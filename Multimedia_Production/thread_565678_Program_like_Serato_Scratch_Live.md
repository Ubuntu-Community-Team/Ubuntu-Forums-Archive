---
title: "Program like Serato Scratch Live"
date: 2007-10-02
forum: Multimedia Production
---

### Post by cet.junior on 2007-10-02
Hi Folks!:)

My problem, I think, it's very simple. I'm looking for a program like Serato Scratch Live for Ubuntu Feisty/Debain...by the time I'm looking for, it's very hard to find...

Looking the web, I found only one program that lookalike...it's Final Scratch (an old version)...today, I found XWAX, another program, but I don't have the opportunity to test. So, I'd like many opinions as popssible from you guys...

Sorry about my english...:lolflag:...and thank you anyway!:)

---

### Post by Stochastic on 2007-10-03
Well I looked into this software area a while ago (about 6-9 months) and found that the only thing that could work on Linux was Final Scratch 1.0 or Mixxx. DON'T GET FINAL SCRATCH!!!! It requires an old (built five years ago) barebones pervertedly altered version of Debian to run - maybe it's possible to hack their system onto Ubuntu, but it was WAAAYYYY beyond my skill.  Furthermore the soundcard they use has absolutely NO BASS - that is nearly the whole reason for DJing in the first place.

I've never heard of XWAX before, it looks like it's on the right track and I may just pick up a couple vinyls to try it out.  I'd recommend either MIXXX or XWAX.

---

### Post by kayosiii on 2007-10-04
TerminatorX ???

---

### Post by jamesrw on 2007-10-13
XWAX..!
[http://www.xwax.co.uk/](http://www.xwax.co.uk/)

I'm trying to get equipment to check it out. there seems to be good support as well.

---

### Post by Stochastic on 2007-10-15
I've since gone out and bought some rekkids to work with XWAX.  In the development repos there's a Jack supported version so I'm running that and it's pretty freakin' responsive.  I'm quite impressed with it and hope to see it grow alot more.

---

### Post by diizy on 2007-10-19
Here is what you are after:

[http://members.iinet.net.au/~jkburges/xwax/xwax_serato_quickstart.html](http://members.iinet.net.au/~jkburges/xwax/xwax_serato_quickstart.html)

This should aid you to get Serato up & running with linux, i haven't yet tested, but i will try when i get home today.

---

### Post by cet.junior on 2007-11-12
> **diizy said:**
> Here is what you are after:

[http://members.iinet.net.au/~jkburges/xwax/xwax_serato_quickstart.html]("http://members.iinet.net.au/%7Ejkburges/xwax/xwax_serato_quickstart.html")

This should aid you to get Serato up & running with linux, i haven't yet tested, but i will try when i get home today.


[COLOR=Black] Thank you, very much **diizy**!

I'll try this way too...I find another, using a program called [Mixxx]("http://mixxx.sourceforge.net/")...it seems to be very mature and responsive (and seems to use XWAX too), but I haven't tested with the Serato device yet (my notebook is under repair).

ASAP, I'll test with both methods, Mixxx and the Serato/XWAX.

Thank you all for the replies![/COLOR]

---

### Post by Eddy Gordo from Tekken on 2007-11-14
has anyone gotten XWax to work in Ubuntu (Studio)?
My 1st and 2nd attempt at getting the software to launch was a FAIL.  I am going to upgrade to Ubuntu Studio 7.10 and try again.  I have denon 3500s and a delta 1010LT so instead of the Serato amp, i intend to plug right into my soundcard and take advantage (crosses fingers) of ~0 latenency.  Am I going to be the first to try this with XWax?

---

### Post by Stochastic on 2007-11-14
I had it working great in Feisty but haven't had the time to install it / try it yet for Gutsy
that was with my presonus firepod running the jack version of xwax

---

### Post by qfour20 on 2007-11-15
> **Eddy Gordo from Tekken said:**
> has anyone gotten XWax to work in Ubuntu (Studio)?
My 1st and 2nd attempt at getting the software to launch was a FAIL.  I am going to upgrade to Ubuntu Studio 7.10 and try again.  I have denon 3500s and a delta 1010LT so instead of the Serato amp, i intend to plug right into my soundcard and take advantage (crosses fingers) of ~0 latenency.  Am I going to be the first to try this with XWax?

I haven't used Ubuntu Studio before, but I have gotten xwax set up and running just fine in Gusty.  I was using a Gemini PS-02 USB to test.  Due to short-sightedness on Gemini's part in laying out the USB audio in this device, it is only sufficient as a test platform and unsuitable for gig use... more on my attempted solution shortly.

The following packages need to be installed for xwax to function correctly:
mpg123 flac libsdl-ttf2.0-0
The most obvious way to install these is:
sudo apt-get install mpg123 flac libsdl-ttf2.0-0

The mixer that I have only has channel 1 sent directly to the USB audio device.  The other USB audio device only can record master out.  Sending a signal back down the same USB device, I can map the sound to "line 1" or "line 3".  If I send it to line 1, I don't get the output from the timecode record, so playing back audio requires using both channels right now.  I ordered two USB phono preamp [devices]("http://www.artproaudio.com/products.asp?type=90&cat=13&id=128") that will hopefully arrive before the end of the week.  We will see how these work out.

Good luck setting up xwax.  My curiousity has been piqued by mixxx.

-q

---

### Post by Eddy Gordo from Tekken on 2007-11-15
> **Stochastic said:**
> I had it working great in Feisty but haven't had the time to install it / try it yet for Gutsy
that was with my presonus firepod running the jack version of xwax

> **qfour20 said:**
> I haven't used Ubuntu Studio before, but I have gotten xwax set up and running just fine in Gusty.  I was using a Gemini PS-02 USB to test.  Due to short-sightedness on Gemini's part in laying out the USB audio in this device, it is only sufficient as a test platform and unsuitable for gig use... more on my attempted solution shortly.

The following packages need to be installed for xwax to function correctly:
mpg123 flac libsdl-ttf2.0-0
The most obvious way to install these is:
sudo apt-get install mpg123 flac libsdl-ttf2.0-0

Good luck setting up xwax.  My curiousity has been piqued by mixxx.

-q

I'm going to try again tonight after i upgrade to gusty.  on the xwax site there are two download choices x86 and source code. are they different?  is there a separate download for the "jack version". Ubuntu studio comes with Mixxx, but it doesn't support using my turntables...but then again that appears to be the point of Mixxx
:-)

---

### Post by qfour20 on 2007-11-16
> **Eddy Gordo from Tekken said:**
> I'm going to try again tonight after i upgrade to gusty.  on the xwax site there are two download choices x86 and source code. are they different?  is there a separate download for the "jack version". Ubuntu studio comes with Mixxx, but it doesn't support using my turntables...but then again that appears to be the point of Mixxx
:-)

As best I know, you have to use the development version of xwax right now to use JACK.  The 0.2 version up for download on the website does not support JACK.  You can download the source code if you'd like and build it yourself, but the binary version (labeled "x86") is most likely what you want.

Download the file on the website to someplace you know... in my case, I sent it to my home directory, /home/kitchen.  Unpack the file using tar:
```
$ tar -xvzf xwax-0.2_ix86.tar.gz
```

That means that tar (the "tape archiver") will e**x**tract **v**erbose (lets you know what it's doing) un**z**ip a **f**ile.  This will create a directory named xwax-0.2_ix86.  You will want to run xwax as root (normally this is "A Bad Thing", but it's necessary to reduce latency).  To do this:

```
$ sudo bash
```
You will be prompted to enter your password, then be spit back out to a shell logged in as "root".  This is the "super user" account on your system.  It will not question anything you request it to do, and you can damage your installation quite easily, so please be careful what commands you enter in this shell.  You have been warned.

Before we get down to running xwax itself, we want to figure out what audio inputs and outputs we will be using.  To do this, you will use two tools:  lsusb and aplay.  Enter the following commands, your output will likely be very different:

```
root@kitchen:~# lsusb
Bus 004 Device 009: ID 08bb:2902 Texas Instruments Japan 
Bus 004 Device 007: ID 058f:6254 Alcor Micro Corp. 
Bus 004 Device 008: ID 08bb:2902 Texas Instruments Japan 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
root@kitchen:~# aplay -L
front:CARD=I82801DBICH4,DEV=0
    Intel 82801DB-ICH4, Intel 82801DB-ICH4
    Front speakers
surround40:CARD=I82801DBICH4,DEV=0
    Intel 82801DB-ICH4, Intel 82801DB-ICH4
    4.0 Surround output to Front and Rear speakers
surround41:CARD=I82801DBICH4,DEV=0
    Intel 82801DB-ICH4, Intel 82801DB-ICH4
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=I82801DBICH4,DEV=0
    Intel 82801DB-ICH4, Intel 82801DB-ICH4
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=I82801DBICH4,DEV=0
    Intel 82801DB-ICH4, Intel 82801DB-ICH4
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
null
    Discard all samples (playback) or generate zero samples (capture)
front:CARD=default,DEV=0
    USB Audio CODEC , USB Audio
    Front speakers
surround40:CARD=default,DEV=0
    USB Audio CODEC , USB Audio
    4.0 Surround output to Front and Rear speakers
surround41:CARD=default,DEV=0
    USB Audio CODEC , USB Audio
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=default,DEV=0
    USB Audio CODEC , USB Audio
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=default,DEV=0
    USB Audio CODEC , USB Audio
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=default,DEV=0
    USB Audio CODEC , USB Audio
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=default,DEV=0
    USB Audio CODEC , USB Audio
    IEC958 (S/PDIF) Digital Audio Output
front:CARD=default_1,DEV=0
    USB Audio CODEC , USB Audio
    Front speakers
surround40:CARD=default_1,DEV=0
    USB Audio CODEC , USB Audio
    4.0 Surround output to Front and Rear speakers
surround41:CARD=default_1,DEV=0
    USB Audio CODEC , USB Audio
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=default_1,DEV=0
    USB Audio CODEC , USB Audio
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=default_1,DEV=0
    USB Audio CODEC , USB Audio
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=default_1,DEV=0
    USB Audio CODEC , USB Audio
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=default_1,DEV=0
    USB Audio CODEC , USB Audio
    IEC958 (S/PDIF) Digital Audio Output
root@kitchen:~# 
```

Now, what does all this mumbo jumbo mean?  The output of "lsusb" tells me what's on the USB bus.  On my system, the two devices listed as "Texas Instruments Japan" are the USB audio devices.  Looking through the output of "aplay -L", we want the devices named "USB Audio CODEC".  On my system, these two devices appear to be the second and third devices listed.  This means that they will show up as devices /dev/dsp1 and /dev/dsp2.  Remember, these devices are numbered starting at zero, instead of one.

So, to launch xwax for one turntable (in my case), I would issue the following command:

```
root@kitchen:~# cd xwax-0.2_ix86/
root@kitchen:~/xwax-0.2_ix86# ./xwax -l ../music -d /dev/dsp1
```

The "../music" signifies that I have a directory in my home directory named "music" where all my tracks are stored.

Hope this helps.

-Rick

---

