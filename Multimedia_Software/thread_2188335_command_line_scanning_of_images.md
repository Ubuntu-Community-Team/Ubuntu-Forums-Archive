---
title: "command line scanning of images"
date: 2013-11-16
forum: Multimedia Software
---

### Post by aeronutt on 2013-11-16
I can't find a command line scan tool that has a few basic options like file format, compression strength, etc.
Anyrecommendations other than scanimage or hp-scan?

Here's what I've found so far, and for comparison a few GUI tools I tested:

CL:
-scanimage: 
  20 sec to scan my sample at 300dpi.
  No matter what I do, the files are HUGE, my sample 300dpi in tiff is saved as a 35MB file! Same for JPEG with full compression.
  manpage and -h are confusing stating only outputs available are tiff and pnm, yet it seems to acccept jpeg.

-hp-scan:
  37 sec to scan my sample at 300dpi
  Sample 300dpi in JPEG is 750KB.
  No control of JPEG quality.

GUI: 
-simplescan:
  20 sec to scan my sample at 300dpi. 
  File type/size is JPEG/1.6MB.
  Can't tell from looking at processes what options simplescan is using to scan.

-xsane:
  16 sec to scan my sampel at 300dpi.
  File type/size is JPEG/573KB
  Can't tell from looking at processes what options xsane is using to scan.

---

### Post by aeronutt on 2013-11-17
Anyone? Any command line scan available other than scanimage or hp-scan?

---

