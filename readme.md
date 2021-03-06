# FoRTE-Research's Fuzzing Benchmarks

This repository contains a collection of benchmarks and seed inputs to make fuzzing research more readily comparable and reproducable. For instructions on installing and running a given benchmark, refer to the `readme` file in its respective directory. 

**We welcome any suggestions for improving this fuzzing benchmark corpus!** Our only criteria for additional benchmarks is that they are compatible with **AFL-Clang**, **AFL-QEMU**, and **AFL-Dyninst** tracing (as all 8 below are). 

<table>
  <tr>
    <td align=center colspan="2"><div><b>Presented in our paper</b> <a href="https://arxiv.org/abs/1812.11875"><i>Full-speed Fuzzing: Reducing Fuzzing Overhead through Coverage-guided Tracing</i></a><br>(to appear in the 2019 IEEE Symposium on Security and Privacy).</td>
  </tr>
  <tr>
    <td><b>Citing this repository:</b></td>
    <td>
      <code class="rich-diff-level-one">@inproceedings{nagy:fullspeedfuzzing,</code><br>
      <code class="rich-diff-level-one">title = {Full-speed Fuzzing: Reducing Fuzzing Overhead through Coverage-guided Tracing},</code><br>
      <code class="rich-diff-level-one">author = {Stefan Nagy and Matthew Hicks},</code><br>
      <code class="rich-diff-level-one">booktitle = {{IEEE} Symposium on Security and Privacy (Oakland)},</code><br>
      <code class="rich-diff-level-one">year = {2019},}</code>
    </td>
  </tr>
  <tr>
    <td><b>Developers:</b></td>
    <td>Stefan Nagy (<a href="mailto:snagy2@vt.edu">snagy2@vt.edu</a>) and Matthew Hicks (<a href="mailto:mdhicks2@vt.edu">mdhicks2@vt.edu</a>)</td>
  </tr>
  <tr>
    <td><b>License:</b></td>
    <td><a href="/FoRTE-Research/UnTracer-AFL/blob/master/LICENSE">MIT License</a></td>
  </tr>
  <tr>
    <td><b>Disclaimer:</b></td>
    <td><i>This software is strictly a research prototype.</i></td>
  </tr>
</table>

## BENCHMARK STATISTICS
We utilized [Dyninst](https://dyninst.org/) to compute the following bechmark statistics for the 8 binaries evaluated in our paper. Note that we compiled all with Clang/Clang++.

benchname | libname | type | basic blocks | basic block edges
--- | --- | --- | --- | ---
bsdtar		|libarchive |dev 	|31379	|43390	
cert-basic	|libksba	|crypto |9958	|14120	
cjson 		|cjson		|web 	|1447	|2038 	
djpeg		|libjpeg	|img 	|4844	|6776	
pdftohtml	|poppler	|doc 	|54596	|71945 	
readelf		|binutils	|dev 	|21249	|31086 	
sfconvert	|audiofile	|audio	|5603	|7403 	
tcpdump		|tcpdump	|net	|33743	|48791	

For our paper, we collected statistics on the 24hr fuzzing testcase corpora for each benchmark. Note that these numbers reflect corpora generated using [AFL](http://lcamtuf.coredump.cx/afl/) with QEMU-based tracing.

benchname | libname | type | 24hr corpus size | testcases/24hr | 100ms timeouts
--- | --- | --- | --- | --- | ---
bsdtar		|libarchive |dev 	| 90.9G | 25.6M | 4 
cert-basic	|libksba	|crypto | 7.5G 	| 10.7M | 6 
cjson 		|cjson		|web 	| 4.5G 	| 14.5M | 221K 	
djpeg		|libjpeg	|img 	| 30.1G | 21.0M | 656
pdftohtml	|poppler	|doc 	| 0.2G 	| 1.2M 	| 107 	
readelf		|binutils	|dev 	| 3.8G 	| 14.9M | 7 
sfconvert	|audiofile	|audio	| 3.7G 	| 10.1M | 373K 	
tcpdump		|tcpdump	|net	| 2.7G 	| 27.1M | 5 	


## BUILDING BENCHMARKS
We provide the script `buildAll.sh` to compile all benchmarks from source. 
Edit the following parameters to reflect the desired C and C++ compilers, and any assembler parameters:
```
compiler=""
compilerXX=""
passToAS=""
```

## COLLECTING BENCHMARKS
We also provide the script `collectAll.py` to copy all compiled benchmark binaries to the current directory and append them with a use-specific (as specified on the command line) postfix:

You must supply the path to your local copy of the `FoRTE-FuzzBench` repository in the parameter `basePath`:
```
basePath="/path/to/FoRTE-FuzzBench/"
```

Then, run as follows:
```
python /path/to/FoRTE-FuzzBench/collectAll.py [postfix type] 
```

All benchmarks will be copied and appended to the current directory and appended the specified postfix (leave blank if none).

#
<p align=center> <a href="https://www.cs.vt.edu"><img border="0" src="http://people.cs.vt.edu/snagy2/img/vt_inline_computer_science.png" width="60%" height="60%">
</a> </p>
