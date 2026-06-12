---
title: "TVTime: No XVIDEO port found which supports YUY2 images."
date: 2009-12-14
forum: Multimedia Software
---

### Post by phreakshew on 2009-12-14
Hello all. I've been using TVTime for quite some time in my old computer. I recently upgraded to a newer computer and installed the TV tuner card into it before installing Koala 9.10. Unfortunately, TVTime does not work now.

Computer is a Dell Optiplex 270 with onboard video - Intel Extreme.

lspci shows: 
VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)

Error message from TVTime:

Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/oem/.tvtime/tvtime.xml
xvoutput: No XVIDEO port found which supports YUY2 images.

What should I do now?

Thanks~

---

### Post by phreakshew on 2009-12-16
Well, in place of TVTime, I tried Zapping. It crashed with a segmentation fault when I tried to change a setting. Also tried MythTV, but that one can't scan for channels???  - I have read this is a bug with Ubuntu 9.10 - if someone knows how to get it to work, please let me know.

For now the quick 'n easy solution for me is to switch to Xawtv. Got it working right away, but at first could not get the sound to work properly. What I had to do was open alsamixer in a terminal and raise the Line volume.

The only catch with Xawtv is that there are a bunch of settings that need to be set up in the config file, and I have no idea how to do that. The man pages, like most Linux documentation I have come across, expect the reader to already know how to do certain things. But for now, at least I can watch tv at the desired volume.

:popcorn:

---

### Post by phreakshew on 2009-12-16
I posted this same question over at LinuxQuestions.org and received information on how to make TV Time work. In case anyone's interested, here's the link:
[URL="http://www.linuxquestions.org/questions/linux-software-2/tvtime-no-xvideo-port-found-which-supports-yuy2-images-ubuntu-9.10-775704/"]
http://www.linuxquestions.org/questions/linux-software-2/tvtime-no-xvideo-port-found-which-supports-yuy2-images-ubuntu-9.10-775704/[/URL]

:guitar:

---

### Post by xc3RnbFO8P on 2009-12-16
Read this:
[http://www.linuxquestions.org/questions/linux-software-2/tvtime-problems-xvideo-yuy2-591730/]("http://www.linuxquestions.org/questions/linux-software-2/tvtime-problems-xvideo-yuy2-591730/")

---

