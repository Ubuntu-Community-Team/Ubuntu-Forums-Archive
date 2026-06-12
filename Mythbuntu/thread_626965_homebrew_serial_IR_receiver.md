---
title: "homebrew serial IR receiver"
date: 2007-11-29
forum: Mythbuntu
---

### Post by mbrocketry on 2007-11-29
Hi I have two homebrew serial receivers (I made) and two Motorola remotes that I use for my fedora based mythtv box. This box is my main frontend and backend unit and I want to add a frontend for a TV in another room using a wireless card and the second serial IR receiver and remote. I am trying out Mythbuntu and the only thing I am having trouble with (besides the frontend only install) getting my serial IR receiver and remote to work. I have the working lircd.conf and lircrc files (works with fedora box) and I have copied them into the correct places. The lircd.conf is in the /etc/lirc folder and the lircrc in in the /home/user/.mythtv folder. So my question is how do I set the serial port in Mythbuntu  and setup/start lirc through the Mythbuntu config center? Or do II do it a different way? I looked at the install manual (chap 10)l but it did not make much sense.

---

### Post by twkisner on 2007-11-29
I don't use my homebrew serial reciever anymore, but my understanding is even with Mythbuntu you still need to disable the kernel serial support so that LIRC can take it over.

You can't do this in the Mythbuntu control center :(

 I took a quick look at the intructions on the PDF for IR transmitter.  It looks like the same thing I did on the Fiesty package to get my reciever to work.  Even though it says it is for transmitter it what you do for a reciever too.

---

### Post by mbrocketry on 2007-11-29
Thanks I will give that a try. Before I do that I want to try using another serial device and replace the lircd.conf and lircrc files and see what happens.

---

### Post by mbrocketry on 2007-11-29
well I have tried both with no luck. Lircd is not running. Mode2 returns an error opening /dev/lirc : no such file or directory. I did verify that I had a lircd.conf in the /etc/lirc folder and the lircrc in the .mythtv folder of my home directory. I can't remember what it takes to write the dev file.

---

### Post by OffAxis on 2007-11-30
what version of lirc are you using?
the 0.8.2 version for serial is busted.
```
lircd -v
```
To get the latest working version go here:
[http://lirc.org/cvs.html]("http://lirc.org/cvs.html")

and just follow the instructions.

After you get that installed you need to disable the kernel serial support and do a few other things. There's a quality write-up here:
[https://help.ubuntu.com/community/Install_Lirc_Gutsy]("https://help.ubuntu.com/community/Install_Lirc_Gutsy")

most of the serial stuff is under 'IR Transmitting', but is pertinent to receiving as well.

also, your device might come up as /dev/lirc0.

---

### Post by barney_1 on 2007-11-30
I have gone through compiling the CVS version of lirc but when I run:
```
lircd -v
```
It still comes up as 0.8.2

Any idea what I can do differently to compile this properly? I notice that there seems to be a pre-release package of 0.8.3 available for Ubuntu but don't know how to install it:

[https://bugs.launchpad.net/ubuntu/+source/lirc/0.8.3~pre1-0ubuntu1]("https://bugs.launchpad.net/ubuntu/+source/lirc/0.8.3~pre1-0ubuntu1")

---

### Post by OffAxis on 2007-11-30
interesting.

If there's an error popping up during the 'make' you might have missed it (like a missing .config for the kernel)

Could be a version conflict; lirc build versus kernel.

to use that launchpad file just download it, untar it, and run the ./setup. Or download the debian package directly:

```
sudo wget http://launchpadlibrarian.net/10229062/lirc_0.8.3%7Epre1-0ubuntu1_i386.deb
```

and then install with a 
```
sudo dpkg -i lirc_0.8.3~pre1-0ubuntu1_i386.deb
```

Here's the page if you need to reference it directly.
[https://launchpad.net/ubuntu/hardy/i386/lirc/0.8.3~pre1-0ubuntu1]("https://launchpad.net/ubuntu/hardy/i386/lirc/0.8.3~pre1-0ubuntu1")

---

