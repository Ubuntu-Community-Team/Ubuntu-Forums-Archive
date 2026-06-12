---
title: "Realtek HD Audio... again."
date: 2010-06-12
forum: Multimedia Software
---

### Post by Newb4Life1 on 2010-06-12
Completed manual install of Realtek HD Audio codecs/drivers +util +lib +plugins

Sound is not working.

alsamixer shows no problems.

I remember this happened to me once before and all it took was one line of code.

Any Ideas?

EDIT: I am positive that they are the correct drivers.

---

### Post by khelben1979 on 2010-06-12
This driver should be part of your Linux kernel, and using modprobe [module name] should just load it and it get's accessible by your Ubuntu system.

So, are you saying you have installed RealTek driver package and it does not give you any sound? What packages did you install? And how did you do that? Version of Ubuntu is also good to know.

---

### Post by Newb4Life1 on 2010-06-12
[http://152.104.125.41/downloads/downloadsCheck.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false](http://152.104.125.41/downloads/downloadsCheck.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false)

I compiled and ran it.

I am using the newest K-Ubuntu

---

### Post by khelben1979 on 2010-06-12
> **Newb4Life1 said:**
> [http://152.104.125.41/downloads/downloadsCheck.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false](http://152.104.125.41/downloads/downloadsCheck.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false)

I compiled and ran it.

I am using the newest K-Ubuntu

I think those drivers are not for Linux, so that won't help you. On [ALSA SoundCard Matrix]("http://www.alsa-project.org/main/index.php/Matrix:Main") you see what is supported for Linux.

I'm not sure what the module name is for your realtek sound chip, but it should be supported without any compiling of anything.

---

### Post by Newb4Life1 on 2010-06-12
The linux drivers are on the bottom of the next page.....

and they are the right ones.  I am 100% sure.


Edit:

What does it mean "Mute = 1"?

```
Node 0x22 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 10
     0x18 0x19 0x1a 0x1b 0x1d 0x14 0x15 0x16 0x0b 0x12
Node 0x23 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 10
     0x18 0x19 0x1a 0x1b 0x1d 0x14 0x15 0x16 0x0b 0x13

```


Heres the codec info:
```
newb4life@newb4life-linux:~$ cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC272

```

---

### Post by khelben1979 on 2010-06-12
Did you do something [like this]("http://ubuntuforums.org/showpost.php?p=9203173&postcount=7") to get it working?

You were right about the Realtek driver on that page.

---

### Post by Newb4Life1 on 2010-06-12
Yep.  Those come directly from the readme that came with the package.

---

### Post by OdinOrion on 2010-06-12
I am curious as to which Realtek HD you have.  I downloaded and installed those drivers directly from the Realtek website.  They work, except I can't seem to get the SPDIF coax out to work.  I does not seem to have anything to do with the gnome-alsa mixer or any other mixer.  But otherwise, sound seems to work for analog.  I have not had the ability to check HDMI sound output as I am using DVI w/o sound.
 
I have the ALC892 HD.

---

### Post by Newb4Life1 on 2010-06-12
I am using the Realtek ALC272

I had to reinstall the OS after my Video driver failed...

HDA is reportedly installed and working properly.

Thanks for the help.

---

### Post by lidex on 2010-06-13
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

