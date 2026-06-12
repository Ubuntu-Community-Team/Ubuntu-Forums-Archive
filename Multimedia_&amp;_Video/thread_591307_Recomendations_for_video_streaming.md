---
title: "Recomendations for video streaming"
date: 2007-10-25
forum: Multimedia &amp; Video
---

### Post by whein on 2007-10-25
I need to take an MPEG4 encoded video, stream it over wired ethernet and then display it on an Ubuntu system.  My hardware setup is:
NTSC video -> [video capture board]("http://advantech.com/products/MPEG-1-2-4-Video-ecoder-module-with-Audio(RoHS)/mod_1-239YYU.aspx") --USB--> [single board computer]("http://www.phytec.com/products/sbc/ARM-XScale/phyCORE-XScale-PXA255.html") --ethernet--> [mini-itx computer]("http://www.via.com.tw/en/products/mainboards/motherboards.jsp?motherboard_id=81") -> [video card]("http://www2.pny.com/FX-5200-256MB-PCI-P1732C16.aspx")

Up through the ethernet connection has already been completed by someone else.  I've got Ubuntu 7.04 running nicely on the mini-itx computer.  But I'm not sure what to use to display the video stream.  MPlayer seems to only take input from stdin or the internet (http or ftp) if I'm reading the documentation on streaming correctly.  VLC can take a UDP stream in, but it needs to be in the VLC or VLS output format, whatever that is.  Can one of these be made to work or is there another video playback package that would better suit me?  Ideally I'd like to be able to launch some program, pass it an IP address and a port number, and just have it go to town.  I don't care about a GUI (would actually prefer it not to have one visible).  Any advice?
-Will

---

