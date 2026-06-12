---
title: "Is playback supposed to be this difficult on the CPU?"
date: 2008-07-01
forum: Mythbuntu
---

### Post by Mr_Chapendi on 2008-07-01
Th box I'm running Mythbuntu on has 2 Hauppage PVR-150 tuner cards, a 2.53 Pentium 4 processor that's been overclocked to a 2.6, and an nVidia Geforce 6600 GT as the video card/TV out.  My impression was that a 2.6 GHz processor and a solid video card like the one I have were overkill for Mythbuntu without telling it to do anything extreme - especially as far as playback was concerned.  Oddly enough, however, my system seems to spend very little resources on recording, while the CPU maxes out at 100% during playback (until mythfrontend crashes after 20 to 30 minutes.)  I think I may be trying to decode using only the CPU and somehow ignoring the video card's muscle, and/or simply using bizarre playback settings.  Could I get some advice on the playback settings I should be using for my set up (or any other settings you think might be strange - it's very likely something unrelated) that I could tweak incrementally from to find the ideal playback settings for my box?

Thanks for your time, and let me know any other information you might require (logs, etc.) and I will gladly share them.


MythTV Version -  Installed: 0.21.0+fixes16838-0ubuntu3.1

---

### Post by ian dobson on 2008-07-01
Hi,

Sounds as if your using a generic/opensource driver and not using the NVIDIA video driver. Try going into the Mythubuntu setup/configuration program and enable the NVIDIA driver.

For info. My frontend is an Underclocked (800MHz) Core2Duo and a Nvidia 7300GT graphic card and when playing SD (PAL) recordigs the CPU load is only about 30-40%.

Regards
Ian Dobson

---

### Post by Mr_Chapendi on 2008-07-01
Good idea ian, but unfortunately I'm already using the nVidia drivers.  (Double-checked to make sure - wish it would be that easy!)  I'm playing around with the various playback settings, and it seems to run best under 'Slim.'  I still think my machine should be able to handle 'Normal' or even 'High Quality' though - any ideas?

---

### Post by superm1 on 2008-07-01
Make sure you do your kernel updates.  The -16 kernel that shipped with Mythbuntu 8.04 and Ubuntu 8.04 has issues with this...

They're fixed in -17 (and consequently -18,-19,-20...)

---

### Post by Mr_Chapendi on 2008-07-01
The kernel isn't -17.  Other thoughts?

```
theblob5@theblob5:~$ uname -r
2.6.24-19-generic

```

---

### Post by danbodoh on 2008-07-01
Try looking at 'top' output.  Which processes are using the CPU?  Mythfrontend? X? MythBackEnd?

Dan Bodoh

---

### Post by nigel502 on 2008-07-02
I'm experiencing the same issues on a P4 PVR-150 with a Geforce 6600. The maximum resolution I can have is 640x480. Mythbuntu 8.04

My system doesn't view any avaiable updates.

How do I view "top" output to make sure I'm on the right page.

---

### Post by Mr_Chapendi on 2008-07-02
Playing around with some of the settings, I've managed to get usage down to 67% (I switched playback settings to XvMC.)  I still think i can get a better picture out of it though.

top output while running.

```

 5614 root      20   0 74912  47m  23m R 59.9  2.3 113:49.27 Xorg                                           
11172 theblob5  20   0  291m 132m  42m S 25.3  6.5   0:25.41 mythfrontend.re                                
 6614 theblob5  20   0 42580  21m  12m S  6.7  1.1  83:42.87 gnome-system-mo                                
 5123 mythtv    20   0  222m  25m   9m S  5.3  1.2   5:40.21 mythbackend                                    
 6225 theblob5  20   0 49176  27m 7388 S  0.7  1.4  12:12.78 compiz.real                                    
11215 theblob5  20   0  2308 1140  852 R  0.7  0.1   0:00.10 top                                            
    1 root      20   0  2844 1692  544 S  0.0  0.1   0:01.26 init        

```

---

### Post by Mr_Chapendi on 2008-07-02
nigel502, to run top you just literally type in 'top' on the command line.  It'll give you a real-time display of processes and they're corresponding CPU usage (among other things.)  Hit control-c or q(?) to quit.

---

### Post by Mr_Chapendi on 2008-07-02
Eek.  Well, it doesn't like XvMC terribly much after all - it just crashed again.

The frontend log - [http://pastebin.ubuntu.com/24547/](http://pastebin.ubuntu.com/24547/)

It crashed around 4:12 or so.
It seems that I don't have XvMC set up, so it just used xv-blit instead.
What should I do from here?  Follow this?  [http://www.mythtv.org/wiki/index.php/XvMC](http://www.mythtv.org/wiki/index.php/XvMC)

Or is XvMC what I should be going for in the first place?

---

### Post by zoiks on 2008-07-02
> **Mr_Chapendi said:**
> 
Or is XvMC what I should be going for in the first place?

You shouldn't need XvMC, you have plenty of horsepower. Something else is wrong. I wouldn't recommend XvMC since it locks you into mpeg2 and only shows a black and white OSD.

Maybe I'll chime in - what are you doing for deinterlacing, and do you have libmpeg2 enabled? Various deinterlace routines will take a lot of CPU, and maybe libmpeg2 does as well, IIRC.

---

### Post by danbodoh on 2008-07-02
Is Xorg the process that eats the CPU?  During playback, it's mythfrontend that is busy doing decoding and such.  So your problem is not decoding, so XvMC isn't going to help.

Can you get a similar top output when not running mythfrontend?  Perhaps by running totem or mplayer?  Maybe it's something with your video driver?

More questions than answers...

Dan Bodoh

---

### Post by Archmage on 2008-07-03
Did you try to reproduce the problem with compiz turned off?

---

### Post by Mr_Chapendi on 2008-07-03
danbodoh, when playing recorded TV through mplayer instead of mythfrontend, cpu usage stays right around 50%, and certainly never crashes or skips.  Is there a way to rule out my video driver more definitively?

Archmage, thank you for pointing copmiz out - I had forgotten it came default with ubuntu-desktop.  Unfortunately, it seems to make little difference in CPU usage and doesn't seem to be the problem (although it probably wasn't helping, either.)

I'm still playing around with various playback settings - I was getting slightly better performance from libmpeg2 with opengl, but then I started to get a *different* weird problem.  Now, if I watch anything in mythfrontend and then back into the menu and then try to watch anything else in mythfrontend I get only sound, no video...

I think I'm going to reinstall to get all of the default settings back (I think I must have just activated something really bizarre) and see what happens.  I'll let you all know if it fixes the problem, and describe what specifically is still going wrong if it doesn't.  (I reinstall all of my operating systems constantly, I'm OCD like that, so this isn't as much of an inconvenience as it may sound.)

I'll keep you posted.

---

### Post by rumblered on 2008-07-03
Don't reinstall!

It's the video driver. I had this problem myself. Turns out the nvidia driver has the rather insane default of running a idle polling loop while waiting for the hardware instead of registering an interrupt. And that works very badly with MythTV.

Add this to your device section in /etc/X11/xorg.conf:
Option "UseEvents" "True"

And Xorg cpu usage will fall to a few percent.

---

### Post by Mr_Chapendi on 2008-07-03
Interesting - will try that now.

---

### Post by Mr_Chapendi on 2008-07-03
rumblered, that seemed to do the trick!  Xorg now averages between 4 and 6 % during playback, with mythfrontend being the most CPU-intensive process.  Thank you for telling me that little fix - it should really be posted prominently in Mythbuntu documentation about nVidia video cards.  (Or maybe I just missed it - very possible.)  

I am still somewhat miffed that I can't play in 'High Quality' without significant stuttering and 100% CPU usage - with my specs, shouldn't I be able to?

---

### Post by mrand on 2008-07-03
> **Mr_Chapendi said:**
> rumblered, that seemed to do the trick!  Xorg now averages between 4 and 6 % during playback, with mythfrontend being the most CPU-intensive process.  Thank you for telling me that little fix - it should really be posted prominently in Mythbuntu documentation about nVidia video cards.  (Or maybe I just missed it - very possible.)  

I am still somewhat miffed that I can't play in 'High Quality' without significant stuttering and 100% CPU usage - with my specs, shouldn't I be able to?Perhaps I'm missing it somewhere, but I don't see where you outlined what playback profile you're using.  That has a fairly big impact on things, and a 2.6 GHz P4 may not do much more than than lowest settings without some assistance.

[INDENT]   Marc[/INDENT]

---

### Post by Mr_Chapendi on 2008-07-04
marc, you're right - I haven't outlined it.  I tend to change it 6 to 7 times a day trying to find the best looking settings - this is severely hampered by the fact that I don't quite understand what I'm changing.  :)  Right now I do believe it's in 'Standard' with every one of the decoding routines as 'Standard' and rendering as 'xv-blit.'

---

