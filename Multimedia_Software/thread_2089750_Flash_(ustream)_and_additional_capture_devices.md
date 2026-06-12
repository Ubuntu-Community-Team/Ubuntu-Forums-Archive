---
title: "Flash (ustream) and additional capture devices"
date: 2012-11-30
forum: Multimedia Software
---

### Post by beauchampy on 2012-11-30
Hello all, first time poster here.

I am building a machine that will ultimately be a Ustream / multiple webcam host for a school radio station.

I'm running webcamstudio. The way it works is it recognises multiple webcams and allows you to switch between them. The output from webcamstudio is as a virtual capture device. In my case, /dev/video2

At the moment I am just testing with one camera connected.

Everything before flash seems to be working ok. I am previewing the camera fine, I can open /dev/video2 in VLC and all is working fine.

The problem is that when I choose my capture device in Ustream, the only capture device it see's is /dev/video0. Even right clicking on flash, going into settings, the only camera listed in the drop down menu is the camera I have connected (/dev/video0) rather than the ouput from webcamstudio which is dev/video2.

I"m testing this with the latest version of Chrome on Ubuntu 10.04 (had mad problems trying to get webcamstudio to even install on ubuntu 12). Firefox + flash doesnt seem to work at all. Flash just crashes.. Despite both being the latest versions.

Any help greatly appreciated.

---

### Post by dannyboy79 on 2012-12-01
have you checked their forums for help? im actually compiling the latest webcam studio as we speak following this tutorial. [http://www.ws4gl.org/download/compiling](http://www.ws4gl.org/download/compiling)

did you install version in the repo or did you compile? i am also using 10.04.4. i'll let you know how it goes. How come you it's /dev/video2 and not video0? do you have other /dev/video devices?

---

### Post by beauchampy on 2012-12-03
Hi there!

No, didn't compile, just installed the latest release. I think its /dev/video2 because theres a capture card in this machine... I'll play around and see what I can muster.

---

