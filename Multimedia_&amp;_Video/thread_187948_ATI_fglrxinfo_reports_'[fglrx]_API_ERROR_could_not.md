---
title: "ATI fglrxinfo reports '[fglrx] API ERROR: could not register entrypoint for....&quot;"
date: 2006-06-03
forum: Multimedia &amp; Video
---

### Post by nxumdon on 2006-06-03
Hello
So I've attempted to install the fglrx ati drivers as described in method 1 on the following link;

[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

rebooted as reqested and when i run 'fglrxinfo' it just shows a bunch of lines stating;

nxumdon@nxumdon-desktop:/usr/X11R6/lib$ fglrxinfo
[fglrx] API ERROR: could not register entrypoint for SelectTextureSGIS
[fglrx] API ERROR: could not register entrypoint for SelectTextureTransformSGIS
[fglrx] API ERROR: could not register entrypoint for ClientActiveVertexStreamATI
[fglrx] API ERROR: could not register entrypoint for VertexBlendEnviATI
[fglrx] API ERROR: could not register entrypoint for VertexBlendEnvfATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2sATI


Can anyone provide any guidance on how to get this driver working properly.  I've got an ATI 9000Pro running on an GeForce2 motherboard 1.8Ghz AMD CPU.  

I've searched through many pages of help and nothing i've read provides a solution to this problem, although it seems like many others are experiencing it.  

Thanks for any help.

nxumdon

---

### Post by Wild_Coyote on 2006-06-03
I've got that error too :-?

---

### Post by nxumdon on 2006-06-03
just fixed my problem!!!!  dont know why this post didn't show up in the search results..but it works...just download the link to the libGL.so.1.2 and copy to /usr/lib then run fglrxinfo again, and bingo!!! it works!!!

[http://www.ubuntuforums.org/showthread.php?t=185033](http://www.ubuntuforums.org/showthread.php?t=185033)


Thanks...sorry for wasting space on the forums.... :)

---

