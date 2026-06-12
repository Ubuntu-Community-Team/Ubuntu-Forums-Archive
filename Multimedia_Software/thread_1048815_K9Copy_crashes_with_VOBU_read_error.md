---
title: "K9Copy crashes with VOBU read error"
date: 2009-01-23
forum: Multimedia Software
---

### Post by prashantjois on 2009-01-23
When I run K9copy while trying to make ISOs from my dvds it crashes.  When run from a terminal I get the follow dump in the console:

```

*** libdvdread: CHECK_VALUE failed in ifo_read.c:1543 ***
*** for info_length % sizeof(cell_adr_t) == 0 ***        


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1678 ***
*** for info_length % sizeof(uint32_t) == 0 ***          


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1543 ***
*** for info_length % sizeof(cell_adr_t) == 0 ***        

libdvdread: Invalid title IFO (VTS_02_0.IFO).

*** libdvdread: CHECK_VALUE failed in ifo_read.c:1543 ***
*** for info_length % sizeof(cell_adr_t) == 0 ***        


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1678 ***
*** for info_length % sizeof(uint32_t) == 0 ***          


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1543 ***
*** for info_length % sizeof(cell_adr_t) == 0 ***

libdvdread: Invalid title IFO (VTS_02_0.IFO).
VOBU : 0 Read Error !!!!  ==>  2248409088    
VOBU : 0 Read Error !!!!  ==>  60            
VOBU : 79 Read Error !!!!                    
VOBU : 161 Read Error !!!!                   
VOBU : 232 Read Error !!!!  ==>  294         
VOBU : 313 Read Error !!!!                   
VOBU : 393 Read Error !!!!                   
VOBU : 470 Read Error !!!!  ==>  527         
VOBU : 546 Read Error !!!!  ==>  603         
VOBU : 622 Read Error !!!!  ==>  684         
VOBU : 703 Read Error !!!!                   
VOBU : 780 Read Error !!!!  ==>  832         
VOBU : 851 Read Error !!!!                   
VOBU : 924 Read Error !!!!  ==>  986

.
.
.

QPainterPath::arcTo: Adding arc where a parameter is NaN, results are undefined
QPainterPath::arcTo: Adding arc where a parameter is NaN, results are undefined
QPainterPath::arcTo: Adding arc where a parameter is NaN, results are undefined
QPainterPath::arcTo: Adding arc where a parameter is NaN, results are undefined

.
.
.
VOBU : 1964 Read Error !!!!                                                    
VOBU : 2121 Read Error !!!!  ==>  2274                                         
VOBU : 2274 Read Error !!!!                                                    
VOBU : 2437 Read Error !!!!  ==>  2598                                         
VOBU : 2598 Read Error !!!!                                                    
VOBU : 2752 Read Error !!!!                                                    
VOBU : 2913 Read Error !!!!  ==>  3076 

.
.
.

VOBU : 342331 Read Error !!!!
VOBU : 342516 Read Error !!!!  ==>  342707
VOBU : 342707 Read Error !!!!
VOBU : 342886 Read Error !!!!  ==>  343084
VOBU : 343084 Read Error !!!!
VOBU : 343298 Read Error !!!!  ==>  343488
VOBU : 343488 Read Error !!!!  ==>  343688
KCrash: Application 'k9copy' crashing...
sock_file=/home/myuser/.kde/socket-myuser/kdeinit4__0
VOBU : 343688 Read Error !!!!
Unable to start Dr. Konqi
```



I've read a couple of forum posts claiming that this is a result of not having ubuntu-restricted-extras and/or libdvdcss2 installed.  I can confirm that I have installed both of these packages (libdvdcss2 as well explicitly via medibuntu repository).  Just to be safe I also installed kubuntu-restricted-extras, no luck though.

---

### Post by amast on 2009-03-28
I still can't find a post that explains why this happens or how to resolve it.  There are plenty of reports.  I'm running Intrepid Ibex (64bit) and get the same thing.

---

### Post by ciampix on 2009-05-29
> **amast said:**
> I still can't find a post that explains why this happens or how to resolve it.  There are plenty of reports.  I'm running Intrepid Ibex (64bit) and get the same thing.

It's a new copy protection technology, I do not know any way to resolve it though...

---

