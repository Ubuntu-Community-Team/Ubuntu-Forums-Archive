---
title: "problems in stalling rmpi, R  ubuntu"
date: 2008-06-07
forum: Michigan Team - US
---

### Post by GreenLinux@R on 2008-06-07
I posted this on another forum, but got no response. so I am trying to get some "local" help and please forgive my double posting. 


I flowed the solution and used CC=mpicc
[COLOR="DarkGreen"]([http://www.mail-archive.com/r-help@stat.math.ethz.ch/msg94158.html](http://www.mail-archive.com/r-help@stat.math.ethz.ch/msg94158.html))[/COLOR]

greenlinux4r@greenlinux4r-desktop:~/R/i486-pc-linux-gnu-library/2.7$ CC=mpicc R CMD INSTALL --clean Rmpi_0.5-4.tar.gz
* Installing to library '/home/greenlinux4r/R/i486-pc-linux-gnu-library/2.7'
* Installing *source* package 'Rmpi' ...
[COLOR="SeaGreen"]checking for gcc... mpicc
checking for C compiler default output file name...
configure: error: C compiler cannot create executables
See `config.log' for more details.
ERROR: configuration failed for package 'Rmpi'[/COLOR]
** Removing '/home/greenlinux4r/R/i486-pc-linux-gnu-library/2.7/Rmpi'
** Restoring previous '/home/greenlinux4r/R/i486-pc-linux-gnu-library/2.7/Rmpi'

any help and comments will be appreciated.

---

