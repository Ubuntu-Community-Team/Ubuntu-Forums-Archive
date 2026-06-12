---
title: "Problem converting tiff-files and other images to DPX"
date: 2009-01-29
forum: Multimedia Software
---

### Post by anton_foy on 2009-01-29
Hello!
I have two problems actually.

1) If I convert an existing DPX-file(filesize: 8.008mb) to a duplicate (command: convert A001_C001.dpx -define dpx : packing-method=a -define  dpx:bits-per-sample=10 -define dpx:colorspace=rgb -define -depth 10 A001.dpx),
the new DPX will have a  filesize of 8.016mb. Why does it get a bigger filesize? I have tried different packets aswell without success. Since some of the frames from the Dpx-sequence should be modified (overlay text) and still
keep the original dpx-frames they have to match in filesize.

2) When: convert A002_C002.tif -define dpx : packing-method=a -define  dpx:bits-per-sample=10 -define dpx:colorspace=rgb -depth 10 A002.dpx
the DPX looks like it has Posterization effect with about 6 colours. I tried different settings without success here aswell.

Can GM fetch the metadata from the original file and attach to the new file somehow with the DPX-to-DPX? When using identify it only shows: A001_C001.dpx DPX 2048x1024 2048x1024+0+0 10-bit DirectClass 8.008mb
Anyone know how to solve these problems? Thank you in advance!

  /Jonas

---

