## Sherpa+OpenLoops



**OpenLoops Installation**:

***

NOTES:  version 1.X.X is recommended, otherwise the patching step may not succeed.



Download OpenLoops from [here](https://openloops.hepforge.org/downloads)

```
> tar -zxvf OpenLoops-1.X.X.tar.gz
> cd OpenLoops-1.X.X
> ./scons

# Then copy openloops.cfg into OpenLoops installation top directory(ie.~/OpenLoops.1.X.X)

# do not install any other OpenLoops process libraries!
> ./openloops libinstall ggww2,ggh2tt,gghtt compile_extra=1
> ./scons -c clean=procs

# change to directory ABOVE OpenLoops top directory, then create a folder(eg.named instructions)
and copy openloops.patch into it.
> patch -p0 < ~/instructions/openloops.patch |& tee openloops.patch.output

> cd OpenLoops
> ./scons auto=ggww2,ggh2tt,gghtt generator=0
```



**LHAPDF Installation:**

***

1. Download [LHAPDF](https://lhapdf.hepforge.org/downloads/)

```
> tar xf LHAPDF-6.X.X.tar.gz
> cd LHAPDF-6.X.X
> ./configure 
> make 
> make install
```





2. Install PDF sets (PDF4LHC15_nlo_mc)

Download from [here](https://lhapdf.hepforge.org/downloads?f=pdfsets/6.2/PDF4LHC15_nlo_mc.tar.gz)

PDF sets (each of which is stored in a filesystem directory) should usually be installed in the `$~/share/LHAPDF/` directory (i.e. the PDF dirs are at the same level as the global `lhapdf.conf` file).

To make use of PDF sets installed in other places, those search paths should be listed in the `LHAPDF_DATA_PATH` environment variable.



```
> export LHAPDF_DATA_PATH=$LHAPDF_DATA_PATH$:/path/to/the/PDFsets/
```





**Sherpa Installation**:

***

Download Sherpa from [here](https://sherpa-team.gitlab.io/changelog.html#changelog)

```
> tar -zxvf SHERPA-MC-2.2.5.tar.gz
> cd SHERPA-MC-2.2.5
> ./configure --enable-lhapdf=/path/to/lhapdf --enable-openloops=/path/to/openloops
> make
> make install
```



