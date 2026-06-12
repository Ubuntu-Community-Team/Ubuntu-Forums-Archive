---
title: "help with Playing VCD"
date: 2009-08-25
forum: Multimedia Software
---

### Post by lordbux on 2009-08-25
dear friend

i had been trying to playa vcd on  Mplayer 
but i am getting this error.

```
$ mplayer -cdrom-device /media/NEW/ vcd://2
MPlayer 1.0rc2-4.2.4 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Celeron(R) CPU 2.53GHz (Family: 15, Model: 4, Stepping: 1)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing vcd://2.
read CDROM toc header: Inappropriate ioctl for device
Failed to get cd toc
Failed to open vcd://2.


Exiting... (End of file)

```:confused:

i tried replacing VCD://2 with vcd://1

the vcd is in /media/NEW/

please help..no luck with xine( says no plugin) vlc( no plugin)
although i installe dall plugins i could find
totem too sayn no plugin
please help frinds
:confused:

thanks in advance:guitar:

---

### Post by stinger30au on 2009-08-25
i thought vlc would play vcd media


to install it do this

applications

accessories

terminal

now copy and paste this

sudo apt-get install vlc

then play the cd with vlc

u will find vlc in 

applications
sound & video

let us know

---

### Post by andrew.46 on 2009-08-25
Hi lordbux,

> **lordbux said:**
> i had been trying to play a vcd on  Mplayer 

```
$ mplayer -cdrom-device /media/NEW/ vcd://2
```


I have limited experience playing vcds in this manner but I note the suggested vcd syntax in the [html documentation]("http://www.mplayerhq.hu/DOCS/HTML/en/vcd.html") differs *a little* from your own syntax:

```
mplayer vcd://<track> [-cdrom-device <device>]
```

It may then make little difference but perhaps you could follow this syntax exactly and try:

```
mplayer vcd://2 -cdrom-device /media/NEW
```

and my apologies if this small reorganisation of your commandline makes absolutely no difference at all :-).

Andrew

---

### Post by lordbux on 2009-08-28
sorry 
for the late reply.had some exams......
and 
sorry frnd
nothing seem to work

i get a seek failed error

---

### Post by stinger30au on 2009-08-30
> **lordbux said:**
> sorry 
for the late reply.had some exams......
and 
sorry frnd
nothing seem to work

i get a seek failed error


could well be a crook drive

do you have a spare you can try? or a friends pc you can borrow one from to test and see what goes on?

---

### Post by lordbux on 2009-08-31
> **stinger30au said:**
> could well be a crook drive

do you have a spare you can try? or a friends pc you can borrow one from to test and see what goes on?



i tried changing the cd drive... same trouble

---

### Post by robenroute on 2010-01-07
> **lordbux said:**
> i tried changing the cd drive... same trouble

It's probably not the drive. My multi-boot laptop plays VCDs just perfectly using Windows. Ubuntu (9.04, 8.10, 8.04) and Sidux (also Debian-based) plainly refuse to do anything with a VCD. Now, from the command line "totem vcd://" works, but only for the first track on the disc; the other tracks are still not playable. All in all very frustrating as it used to work without any hiccups..o0O

I'm not sure, but the problem might have to do with gstreamer. Anyone?

---

