---
title: "Graphics Card Upgrade Question"
date: 2006-12-24
forum: Multimedia &amp; Video
---

### Post by Dominicus on 2006-12-24
I'm a Linux new-comer, intend to build a dual-boot system with my current PC:
-Dell Dimension 8100
-Pentium 4 1.5GHz 400FSB
-NVidia GEForce2 MX400 32Mb
-1,280Mb RAM
-LCD Panel Display with native 1680x1050 resolution

My 3D and video playback capabilities really suck with this setup.

I plan to get an extra HDD and Graphics card.  The new HDD will have the Edgy boot.

This leaves the issue of which graphics card to get.  My PC is vintage 2001, and I fear getting a newer card that's overkill for my older CPU, not readily supported by Ubuntu Edgy, or requires more power than what my power supply can handle (I see newer add-on cards come with warnings about power...is this even a consideration?).

If you know of a graphics card supported out-of-box in Ubuntu 6.10 Edgy (i.e. able to set  custom resolution 1680x1050), that is good upgrade to NVidia GEForce2 MX400, and good match to my PC hardware above, I'd appreciate your recommendations.

I really don't want to spend more than $100 in this old clunker, but reality is I need it for couple more years.  If you believe I'm naive thinking I'll notice any difference in 3D or video playback performance by upgrading the graphics card (i.e. because bottleneck is elsewhere), please give me your thoughts too.

Thanks in advance to Ubuntu Community.

---

### Post by cilynx on 2006-12-24
Your machine should be absolutely fine with video and 3d.  Honestly, your MX400 shouldn't be aweful if you're using the nVidia binary drivers.  What's you output for 
```

glxinfo|grep direct

```

One of my machines:
```

rcw@esquire:~$ lspci|grep VGA
01:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 440 AGP 8x] (rev a2)
rcw@esquire:~$ cat /proc/cpuinfo |grep MHz
cpu MHz         : 1800.404
rcw@esquire:~$ 

```
That machine is happily (ie smoothly) running xgl / compiz, so you don't need to go far to get what you want.  
We're talking maybe $20 on pricewatch
[http://www.pricewatch.com/video_cards/geforce4_mx_440_8x_agp_64mb.htm](http://www.pricewatch.com/video_cards/geforce4_mx_440_8x_agp_64mb.htm)

Let's troubleshoot what you've got before we throw money at the problem...

---

### Post by Dominicus on 2006-12-24
I got:
```
ubuntu@ubuntu:~$ glxinfo|grep direct
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect
ubuntu@ubuntu:~$ lspci|grep VGA
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)
```

glxgears gives me ~205fps

Now, before folks start troubleshooting my setup, I'll clarify my 3D and video playback suck while running WindowsXP.  In general, video playback from video-editing apps, DVD's, or downloaded HiRes video is choppy, and 3D benchmark testers can't get more than 20-30 fps in 3D simulations.  Have I made wrong extrapolation that this card will also underperform in Linux Ubuntu?

The output above is from Ubuntu Edgy liveCD session, so it may suffer from whatever shortcuts this method causes.

I do not, as of yet, have a permanent Ubuntu installation on this PC (in process of getting extra HDD from this).  However, I've toyed with Ubuntu long enough on an older laptop, that I'm ready for a dual-boot system in my main PC.

Thanks again for recommendations.

---

### Post by cilynx on 2006-12-25
I'd give the binary drivers a shot so long as you enjoy the fiddling.  

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

Even if you buy another card, you're still going to have to run the binary drivers to get the performance boost.  The open source "nv" driver simply doesn't do the cool accelerated stuff.

I advise sticking with nVidia as they have the best support right now.

---

### Post by Dominicus on 2006-12-25
Well, thanks for the tip on how to activate Nvidia driver,  I got the following report now:

```
glxinfo|grep direct
direct rendering: No

ubuntu@ubuntu:~$ glxgears -printfps
4705 frames in 5.0 seconds = 937.123 FPS
```

Fps' went from 200 to 900 using the Nvidia driver...awesome.  The install was quite painless.

I'll restate my original question given the learnings: 

What is your recommendation for an Nvidia graphics card that installed with a Pentium4-1.5GHz CPU system, would ensure CPU speed be the bottleneck of graphics output?
I'm hoping this would still be one of the older Nvidia cards, as my current card & CPU are 6 years old.  If you can include the series or even the model, this is appreciated.

Thanks!

---

### Post by cilynx on 2006-12-25
You should be able to get direct rendering: yes, but if you're looking to replace the card anyway, you should prolly just do than first, then fight with the drivers.

As I mentioned in a previous post, you can get a GeForce4 MX 440 for ~$20 on pricewatch.  That should do all the "normal" things you want to do without outgunning your system.

---

### Post by Dominicus on 2006-12-30
Thank You for the response.  I have opted for an "NVidia GeForce 6200 256Mb AGP".  Got it at a popular web shop for $32 total (after a couple rebates and free 2nd-day shipping).
I'm hoping this one will make a difference in WinXP video playback and support my Ubuntu dual-boot.  I'll be installing in a few days (waiting for more upgrades to arrive before starting the surgery!).

---

### Post by cilynx on 2006-12-30
Sounds like a good upgrade.  Let us know how it works out for you --

---

### Post by Dominicus on 2007-01-10
Well, upgrading to nVidia GeForce 6200 didn't go as smooth as I hoped:

An initial boot into Windows presented problem recognizing my DVI connection.  After much troubleshooting I got the DVI connection to work with WinXP.  This was first time I'd ever been able to operate my LCD in digital mode (as my previous card only had analog output).

I then proceeded to boot Edgy via live CD.  This did not go well at all, as it permanently killed the DVI port after I applied the nVidia binaries.

X would not start again even in analog mode.  I got that blue-red screen warning me of X.org's crash.  Unfortunately it is so dim-lit, I cannot even read what it says.

Booting back into WindowsXP is successful, but the card now only works in Analog mode.

I spent some time on the phone with the card phone support folks until they concluded my DVI port is now non-operative, and I should return the card for warranty work.

Well, I'm not too hot about starting this process all over again with a replaced 6200, so I'm giving serious thoughts about your recommendation of going with the MX440 instead.

Thanks

---

### Post by Dominicus on 2007-01-11
Well, my saga with Ubuntu and nVidia cards continue.

I returned the NVidia GeForce6200 card fried while loading the binary drivers on digital mode in ubuntu Edgy.

I put back my old OEM Nvidia GeForce2 MX400.  I booted Ubuntu using Edgy liveCD, which went well.  I tried glxgears and got 280 fps (a modest improvement over my prior test with this same card, which I attribute to the CPU upgrade I just installed from 1.5GHz to 2.4GHz).

Next, I followed the process to load the Nvidia binaries as shown here:
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia")

When I restarted X [ctrl]-[alt]-[bksp], the process failed.  The error screen lists something about monitor detection.  Since I don't yet have a fully functioning dual-boot system (only liveCD), plus fact the error condition wouldn't kick me out to the command line, I can't transcribe the error message.

I may have to take a digital picture of the screen, as I do get a dump of the x.org log file.

This process did not produce any errors before, and increased my fps into the 900 (prior post).  Any ideas?

NEVERMIND: Just hitting on limitations of testing Edgy with LiveCD-only install.  I ran the Update Manager to apply the newer fixes -PRIOR- to applying the Nvidia binaries and all's good now.  Getting 930 fps out of the old GeForce2 MX400 clunker on glxgears.  I have a GeForce 6200 replacement on the way, and if that doesn't test out, a friend pitched in a Quadro4 700 XGL.

So upgrading from a Pentium4 1.5GHz to 2.4GHz increased video performance by 3% big deal?  Thanks a lot for the help.  Although I don't look forward to opening up my PC yet again, all this troubleshooting has certainly lowered the stress factor on pulling stuff out of my system and playing around.

---

### Post by Dominicus on 2007-01-22
I was testing Ubuntu 6.10 Edgy from LiveCD, curious to see if it would correctly detect a newly installed Nvidia GeForce 6200 video card.

It came up, but not at my LCD monitor's native resolution (1680x1050).  After login, I went straight to this forum to search how to install the binary Nvidia linux driver.

After following the 'how-to', I restarted the X server (Ctrl-Alt-Bksp) and got a black screen.  I could hear the PC working but video was gone.

I rebooted the PC to allow WinXP to start but no video there either:frown: . I disconnected the Digital (DVI) monitor connection and switched to the analog output to get signal back up.

I thought Linux had fried my Video Card's digital port, but after swapping back to my old card in analog mode, other problems continued: Windows could no longer identify my LCD panel and defaulted the driver to "analog monitor".  I had to force Windows to install the manufacturer's drivers (ViewSonic).

After much googling, I've since learned that my monitor's EDID data is now gone.  The symptom being the PC can no longer get any information about the monitor and pretty much operates "in the blind" as to its capabilities.  DVI (digital) connection will not work since EDID data is required for the handshake before the graphics card would even enable the digital signal.

The damage is pretty much irreversible unless you can get your hands on a working LCD panel of exactly the same type and use a special application to copy over EDID again (not my case).  If your video card only has digital output, you'll need to install a digital-to-analog adapter.

---

