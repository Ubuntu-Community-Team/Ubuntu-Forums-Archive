---
title: "RME Babyface setup"
date: 2013-02-19
forum: Multimedia Software
---

### Post by e3p0 on 2013-02-19
I am a BRAND NEW user of ubuntu.  I just installed lubuntu 12.10 on an OLD Dell Dimension e520 for my son.  It has been pretty straight forward so far.

I am trying to get an audio interface recognized.  It is the RME Babyface which has the new drivers and is "class compliant".  

I cannot seem to get anywhere with it though as the system doesn't recognize it.

Can you help a Linux NOOB?

Where do I begin?
Thanks!!
-e

---

### Post by TheFu on 2013-02-19
Googling for "ubuntu sound trouble"
found this: [https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems)
and
[https://help.ubuntu.com/community/Sound](https://help.ubuntu.com/community/Sound)

For someone really new to Ubuntu and using old equipment, I'd strongly suggest running 12.04 which is a "long term release", LTS, supported distro, unlike 12.10 which is useful if you **need** new capabilities or like "new" over "stable."

---

### Post by e3p0 on 2013-02-19
Thanks for the reply.  I am not having any luck with those tutorials.  The first link it seems is regarding the internal sound issues, and I am OK in that respect.  

The second link, I have no idea where to begin.  As far as OSS, it seems as RME is not supported.  It should work as a generic USB card though in class compliant mode.

Thanks for the help.  I will keep plugging away.

I like your signature : linux user since 93/ lover since 96 implying there IS some learning curve.  I am OK with that.

-e

---

### Post by e3p0 on 2013-02-19
when I type 
```
cat /proc/asound/cards
```I only see :  
```
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xdfddc000 irq 44
```I assume this is my internal soundcard.  Can anybody suggest a next step for diagnosing or fixing my issue? 
Thanks!
-e

---

### Post by e3p0 on 2013-02-19
I found this info but cannot make sense of it.  A bit over my head.  Could anyone demystify it?

> @igny: yes, the Babyface basically works in Linux.
You have to patch the ALSA driver like described here: 
[http://sergey.vlasov.me/2012/09/using-f … linux.html]("http://sergey.vlasov.me/2012/09/using-focusrite-scarlett-18i6-in-linux.html")
Unfortunately the patch disables the mixer and any other controls.
Don't know what mixer features would be available via the class compliant mode though.
In qjackctl you can access all 10 ins and 12 outs and midi.
Mic gain and out level of main and headphone out can be adjusted via the Babyface itself.
Due to the lack of the (matrix-)mixer zero-latency monitoring is not possible at the moment

THANKS!!
-e

---

### Post by TheFu on 2013-02-20
> **e3p0 said:**
> I found this info but cannot make sense of it.  A bit over my head.  Could anyone demystify it?

He is telling you that you need to 

[LIST=1]
[*]get the C source code for a specific sound driver
[*]get the kernel code for any dependencies
[*]modify the driver code successfully
[*]compile it
[*]install it into your kernel
[*]load it so it extends your kernel with that specific, modified, driver
[*]select the new driver through some GUI to make use of it
[/LIST]
BTW, I have never heard "class compliant" before you wrote it. I have no idea what that means, if anything.  It sounds like a basic level of generic functions are included, but I don't know.



So, you'll be a Linux kernel driver hacker when/if you get this working.  I would probably return the card and find one that is already well supported by Linux to avoid all sorts of headaches going forward.  



If you are new to programming or new to Linux, then this is asking a lot, IMHO.  None of the steps are hard, but since every system is a little different and our backgrounds are different, it is hard to provide exactly the correct, fewest steps for a successful result to you.  Heck, I'd probably have to do trial and error for 30 minutes to get it working and I was a UNIX/Linux C programmer for about a decade.



Headaches?  Every time there is a new kernel released, you will potentially need to redo these steps again. New kernels happen a few times a month for new OS releases, but that tappers off over time to about 4 a year for 2 yr old kernels. How many there are depends on things outside all our control.  I've seen 2 kernels released the same day.

---

### Post by e3p0 on 2013-02-20
O.K. I figured as much.  I have had no problem with my system recognizing any other device. 

 As far as class compliant, the device originally had only Mac and PC support, but the firmware now supports iOS devices and claims to work with generic USB audio drivers too.  

I am just amazed at how this old computer FAR out performs my newer windows machine, and I got excited to attempt to go full linux.

The RME Babyface is here to stay, and I am fairly confidant there will be a suitably easy workaround soon.  There is a large community of RME users, the manufacturers however don't want to be open source.  I will poke around their forum as there is a linux section there.


I will invest in a cheapo interface that plays nicely with linux to learn the recording software.

Thanks!
-e

---

### Post by jacid on 2014-02-16
hello to all 
I come to you to see if there were new for the babyface 
I have not been able to follow the advice of sergey

---

### Post by Ryan_Miller on 2014-03-06
Hi!

The latest firmware for the babyface allows it to go in to what RME calls "class compliant" mode. You get there by holding the two buttons as you power up the babyface (by plugging in the USB cable or external power supply). Once you're in 'class compliant' mode, all babyface I/O should become available as a USB audio device in alsa!

I'm running #!(crunchbang) Waldorf, which is debian based, and didn't have to do anything special to get the babyface working with Ardour!

Good luck!

---

### Post by jacid on 2014-06-10
hi!
my card is not recognized in the parameters 
how can I remedy to this

i'm on ubuntu studio (debian too)
... iI'll try with another cable (2usb ->1)

---

### Post by jacid on 2014-06-10
i will test Waldorf on another DD ^^
thk

---

