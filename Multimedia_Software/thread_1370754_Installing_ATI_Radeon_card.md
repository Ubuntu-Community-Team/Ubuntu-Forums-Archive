---
title: "Installing ATI Radeon card"
date: 2010-01-02
forum: Multimedia Software
---

### Post by peyre on 2010-01-02
A coworker gave me her old laptop, and I've been getting it up and running with Xubuntu.  Xubuntu 9.10 just won't install--the screen goes blank and the computer locks up, with either the regular or the alternate install CD.  I gather that this isn't an unknown issue in 9.10, so I'm installing 9.04 instead and I'll just wait until 10.04 comes out.  Xubuntu 9.04 installs and runs like a charm.

This is an HP Pavilion ze4125, with 768MB of RAM and an ATI Radeon IGP 320M video card.  When I enter "sudo su -c "lspci | grep VGA", it returns "01:05.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility U1".

So what I want to do now is install the best driver I can so I can make the most of the video card.  XP let me use any number of high resolutions, but the Display icon in Xubuntu tops out at 1024x768.  EnvyNG doesn't offer. anything compatible with my video card.  I've tried installing ati-driver-installer-9-3-x86.x86_64 and ati-driver-installer-9-12-x86.x86_64, but both say "Extraction failed" (I was running them with gdm stopped).

So, is there something specific I should be doing to get access to higher resolutions, or a driver I need to install?  This is easy on my main computer, which has an NVidia card, so I can use the NVIDIA X Server Settings utility to adjust the resolution--but obviously this machine doesn't have an NVidia card.

---

### Post by SVEN1 on 2010-01-02
ATI Radeon cards are not the best for Linux,the drivers you can get from AT Radeon don't always work. You have to be happy with 
what the Linux builders have come up with as general drivers.
I running a Radeon X1900XTx video card in my desktop using the drivers supplied by Ubuntu and currently have no issues, it works great, and I play games.

There was a listing somewhere with the Linux compatible video cards. If I find the link I will post it.

---

### Post by SVEN1 on 2010-01-02
[http://www.linuxquestions.org/hcl/showcat.php/cat/182/page/1/sort/1/perpage/15/stype/]("http://www.linuxquestions.org/hcl/showcat.php/cat/182/page/1/sort/1/perpage/15/stype/")

[http://www.ubuntuhcl.org/browse/search+video-cards?category=6]("http://www.ubuntuhcl.org/browse/search+video-cards?category=6")

[http://www.linuxcompatible.org/compatlistcat23-1-1-1.html]("http://www.linuxcompatible.org/compatlistcat23-1-1-1.html")

---

### Post by peyre on 2010-01-02
Thanks Sven.  I'll see what I can do with it.  'Course, if worse comes to worst, I'll just restore from the restore CDs and run it with XP.  Not what I was hoping for, but at least I have options.

---

### Post by peyre on 2010-01-06
Well, whaddaya know?  It seems that I have to change part of my original post: XP *offered* lots of high-resolution settings, but now I come to try any of those fancy-shmancy high-res settings, they don't work right.  I get the resolution all right, but the LCD won't support them, so I'd have to move the viewable area around to see things on it.  No thanks.

And when I install the most recent Windows driver for the video card, it limits me to no higher than 1024x768.

Well, chalk one up to Ubuntu!  This makes it a much easier choice re. what OS I want on this machine.  Now if I can just work out the issues with WiFi on it...

---

