---
title: "support for Intel GMA 3100"
date: 2007-12-26
forum: Multimedia &amp; Video
---

### Post by redder on 2007-12-26
I just installed Ubuntu on my new machine and it's beautiful! Everything works and I'm glad to make the big move off Windows.

However, Google Earth says that it does not recognize my graphics card (Inbel GMA 3100), and although Google Earth runs, its graphic display is black.  Also, Ubuntu says that my system won't run  desktop effects (Compiz), though according to   [Wikipedia ]("http://en.wikipedia.org/wiki/Compiz") I'd expect it to.

What's the right thing to do? How do I make Ubnutu fully "recognize" my graphics card.

Thanks.

------------------------------------------------------------------------------------------------------

System info: Intel Pearl Creek DG31PR motherboard, Intel GMA  3100 graphics card. 

The system tells me:
```
lspci | grep VGA
[I]00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 02)
[/I]
```

System -> Hardware Information tells me I have
*82G33/G31 Express Integrated Graphics Controller*
and the full info page is attached.

I have found the following commands on a  forum, but I don't want to try them before I understand what I'm doing.
```
apt-get install xserver-xorg-video-intel
sudo dpkg-reconfigure xserver-xorg

```

---

