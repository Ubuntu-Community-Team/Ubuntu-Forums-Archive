---
title: "Bt878 based video capture card :-( Help me.."
date: 2008-04-04
forum: Multimedia &amp; Video
---

### Post by ann pic on 2008-04-04
previously, i have buy a capture card a.ka PICO2000 video capture card, UNKNOWN/GENERIC type. ( 06:00.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11) 
06:00.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11) like in this web [http://www.zorg.org/homeauto/pico2000.php](http://www.zorg.org/homeauto/pico2000.php). I connect my capture card to analouge camera ( BNC to RCA connector) by using the coaxial cable ( usually used for CCTV). I also did install Digital Video Recorder(DVR) software named Motion ([http://www.lavrsen.dk/twiki/bin/view/Motion/WebHome](http://www.lavrsen.dk/twiki/bin/view/Motion/WebHome)) but when i run i got error say my device doesn't support mmap (I actually not sure what the mmap stand for, maybe memory map??) I also have installed xawtv software that usually work with Motion software to display image snapped. But until now i still cannot solve this problem. Is it because of my hardware or my BTTV driver for my capture card haven't installed properly yet? I am using ubuntu 7.10. In linux kernel 2.6.x it have been mentioned that everything is included already([http://linux.bytesex.org/v4l2/bttv.html](http://linux.bytesex.org/v4l2/bttv.html) and [http://linux.bytesex.org/v4l2/build.html](http://linux.bytesex.org/v4l2/build.html)). But i am very down i been trying very hard, i still cannot display or get any output. Is there i need to change to other DVR software? Help me

---

### Post by xc3RnbFO8P on 2008-04-04
DVR is in Synaptic Package Manager, and there is a newer version here:
[http://www.pierrox.net/dvr/]("http://www.pierrox.net/dvr/")

---

### Post by ann pic on 2008-04-04
i want to find DVR software with source code..

---

### Post by xc3RnbFO8P on 2008-04-04
Download the source from here:
[http://www.pierrox.net/dvr/]("http://www.pierrox.net/dvr/")

---

### Post by ann pic on 2008-04-16
hi ringi..

I already installed DVR software but i does not know how to launch the application. I don't have any GUI application. Am i need to install some modules? Hope to get reply soon.
(!_!)

---

### Post by xc3RnbFO8P on 2008-04-16
Try in Terminal:
> dvr  <return>

---

### Post by ann pic on 2008-04-16
when i run in terminal, got syntax error

ann@ann-desktop:~$ dvr <return>
bash: syntax error near unexpected token `newline'
ann@ann-desktop:~$

---

### Post by xc3RnbFO8P on 2008-04-16
Show ouput **dpkg -l | grep v4l** and **dpkg -l | grep tv** in terminal

---

