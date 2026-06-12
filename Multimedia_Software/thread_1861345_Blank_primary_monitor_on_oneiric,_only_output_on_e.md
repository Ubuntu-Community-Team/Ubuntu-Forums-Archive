---
title: "Blank primary monitor on oneiric, only output on external monitor. (NVIDIA 8400M GS)"
date: 2011-10-15
forum: Multimedia Software
---

### Post by Jarige on 2011-10-15
And such I require the community's help once more.

My problem is that after the upgrade to Oneiric my primary monitor on my laptop doesn't get detected. Even the BIOS screen appears on my second monitor.(!) In other words, I have to plug in a secondary monitor to even use Ubuntu. I tried to 'Detect Displays' in the nvidia-settings program (and the usual Gnome display program) but it doesn't show my monitor. Even when I reboot into Vista (yes, I use Vista for gaming, I'm too lazy to upgrade it to 7) the output remains on my secondary screen.
My primary screen doesn't get detected in Vista either. (not by using the Nvidia Control Panel and not by using the default Display manager in Windows)

I should note that I had this problem before in 11.04 when I killed Xorg too frequently. The reason I killed Xorg so many times was because Unity wasn't responding in a dual-monitor setup. I Still don't know exactly how I fixed the problem back then, but it solved itself somehow. After that, it happened to me multiple times in 11.04 when Unity crashed using Dual-Monitor setup. Sometimes booting in Vista revived the primary monitor, sometimes removing the battery out of my laptop solved the problem. But this time, none of these things work, and I'm out of options. Somehow the video-card thinks it only has the VGA output, which is of course not the case.

And now, this problem appears in Oneiric every single boot. (upgraded just a few hours ago, rebooted numerous times.).

Is there anything I can do about this problem? It's driving me quite nuts right now, since I had other things to do but got hooked up trying to find a solution anywhere. I'm happy to provide extra information if required!

---

### Post by BicyclerBoy on 2011-10-15
You can try forcing the output on with this in /etc/X11/xorg.conf:
Option "ConnectedMonitor" "string"
where "string" is likely "DFP-0"

and adding
Option "ModeDebug" "True"

But first post your /var/log/Xorg.0.log

and the output of:
xrandr --prop

---

### Post by Jarige on 2011-10-15
Well I just turned on my laptop (wake on lan), SSH'ed into my laptop, executed xrandr --prop and saw it said VGA disconnected.
So I ran upstairs, and behold! The laptop monitor was on, showing the new nice login screen!
I still haven't got a clue on why it got fixed. My expectation is that it will break again though, because it used to break in 11.04 too.

Hm, it appears that I can't executy xrandr using SSH, because it shows my netbook resolution.

Is there any use for posting the outpuut of xrandr --prop and my xorg.conf now that it's solved? I will if you ask again, but for now, my problem is solved.

---

### Post by BicyclerBoy on 2011-10-15
I'll have a look anyway out of curiosity..
The Xorg log file is of most use:
/var/log/Xorg.0.log

Have you run
sudo nvidia-xconfig
on this new install ?

Maybe you have some old cruft ...does not explain windows not working correctly, it normally does very well with multiple displays.
Taking the battery out would force a cold reset.

---

### Post by Jarige on 2011-10-15
Well this is the output of xrandr --prop:

```

Screen 0: minimum 320 x 175, current 1440 x 900, maximum 1440 x 900
default connected 1440x900+0+0 0mm x 0mm
   1440x900       50.0* 
   1360x768       51.0     52.0  
   1152x864       53.0  
   1024x768       54.0     55.0     56.0     57.0     58.0  
   960x600        59.0  
   960x540        60.0  
   840x525        61.0     62.0     63.0     64.0  
   832x624        65.0  
   800x600        66.0     67.0     68.0     69.0     70.0     71.0     72.0     73.0  
   800x512        74.0  
   720x450        75.0  
   720x400        76.0  
   700x525        77.0     78.0     79.0     80.0  
   680x384        81.0     82.0  
   640x512        83.0     84.0     85.0  
   640x480        86.0     87.0     88.0     89.0     90.0     91.0  
   640x400        92.0  
   640x350        93.0  
   576x432        94.0     95.0     96.0     97.0     98.0     99.0    100.0  
   512x384       101.0    102.0    103.0    104.0    105.0  
   416x312       106.0  
   400x300       107.0    108.0    109.0    110.0    111.0  
   360x200       112.0  
   320x240       113.0    114.0    115.0    116.0  
   320x200       117.0  
   320x175       118.0  

```

Xorg.0.log is attached as odt, just remove the .odt part cause it's actually a txt file. Appearantly there's a very small size limit for .txt files and I was too lazy to make a zip file, so I just renamed it.
Sorry for the confusing extension :P And thank you for looking in to this!

---

### Post by Jarige on 2011-10-15
Oh, and yes, I did execute nvidia-xconfig during the time that the primary monitor wasn't working. It showed no output and didn't seem to have any directly visible effects. It might have changed xorg.conf without my knowledge though, I didn't check.

---

### Post by BicyclerBoy on 2011-10-15
Your internal LCD is AUO 1440x900 LVDS DFP-0.

You could re-post both file outputs with the 2nd monitor attached.

You should probably run:
**sudo** nvidia-xconfig
to tidy up the new upgrade/install.

---

### Post by Jarige on 2011-10-15
Well at this point I connected my external monitor, these are the new lines in Xorg.0.log:

```

[  3937.271] (II) NVIDIA(GPU-0): Display (DELL 1905FP (CRT-0)) does not support NVIDIA 3D
[  3937.271] (II) NVIDIA(GPU-0):     Vision stereo.
[  3947.739] (II) NVIDIA(0): Setting mode
[  3947.739] (II) NVIDIA(0):     "DFP-0:nvidia-auto-select@1440x900+0+124,CRT-0:nvidia-auto-select@1280x1024+1440+0"
[  3948.884] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
[  3980.126] (II) XKB: reuse xkmfile /var/lib/xkb/server-9389017F38731CFD9F87AD9C54F6A7054409E867.xkm
[  3998.129] (II) NVIDIA(0): Setting mode
[  3998.129] (II) NVIDIA(0):     "DFP-0:nvidia-auto-select@1440x900+0+124,CRT-0:nvidia-auto-select@1280x1024+1440+0"
```

This is xrandr --prop:
```

xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 175, current 2720 x 1024, maximum 2720 x 1024
default connected 2720x1024+0+0 0mm x 0mm
   1440x900       50.0    119.0  
   1360x768       51.0     52.0  
   1152x864       53.0  
   1024x768       54.0     55.0     56.0     57.0     58.0  
   960x600        59.0  
   960x540        60.0  
   840x525        61.0     62.0     63.0     64.0  
   832x624        65.0  
   800x600        66.0     67.0     68.0     69.0     70.0     71.0     72.0     73.0  
   800x512        74.0  
   720x450        75.0  
   720x400        76.0  
   700x525        77.0     78.0     79.0     80.0  
   680x384        81.0     82.0  
   640x512        83.0     84.0     85.0  
   640x480        86.0     87.0     88.0     89.0     90.0     91.0  
   640x400        92.0  
   640x350        93.0  
   576x432        94.0     95.0     96.0     97.0     98.0     99.0    100.0  
   512x384       101.0    102.0    103.0    104.0    105.0  
   416x312       106.0  
   400x300       107.0    108.0    109.0    110.0    111.0  
   360x200       112.0  
   320x240       113.0    114.0    115.0    116.0  
   320x200       117.0  
   320x175       118.0  
   2720x1024     119.0* 

```

I must note that I seem to suffer from this bug: [https://bugs.launchpad.net/ubuntu/+source/unity/+bug/813343](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/813343)
So the secondary screen is scrambled and weird-looking, but it shows output. I think that bug is unrelated to what I had before though.

---

### Post by BicyclerBoy on 2011-10-15
I'm surprised your xrandr output does not show the 2nd screen, even if disconnected...maybe it is confused by twinview.

It is also very odd that windows has problems with the internal screen.
Maybe there is a h/w problem..

Twinview & unity/compiz do not seem to work well together.
You could try good old separate X screens but this is not "windows" like..

---

### Post by Jarige on 2011-10-15
Yeah I was surprised by that too, but as long as the Nvidia Settings thing sees it, I'm happy :P
Yes, hardware problem is what I was thinking of too. I have had this laptop for a pretty long time now (4 or 5 years) but as long as it works, I'm not buying a new one. But somehow it repaired itself after it was powered down for an hour or something.

I might try separate X servers tomorrow (it's late now) but I think one of the reasons why I didn't use that is because it never actually worked for me. But it's a long time since I've tried. Could be just me though, in that time I didn't know what an X server actually was :)

So I could in theory be able to run KDE on one screen and Unity on the other? Or Gnome 3?
I suppose the default would be two Unity desktops?

Or am I making wrong assumptions here? I sometimes have multiple X servers running, so I know a bit of what it does, but I've never run them on separate screens.
(May I assume that the mouse will still go from one screen to another like in TwinView?)
Hm I'm absolutely going to try separate X servers, it actually sounds like fun :P

---

### Post by BicyclerBoy on 2011-10-15
If it ain't broken you haven't tried fixing it enough!

AFAIK. The nVidia driver only supports one X server per GPU; multiple X screens not X servers. So same desktop manager.
Don't know what unity looks like on 2 screens.

You can not place icons on 2nd screen (not since 8.04), can not drag items between screens. Can move the mouse.

Can force apps to launch on either screen:
DISPLAY=":0.1" vlc
will launch vlc on 2nd X screen

---

### Post by Jarige on 2011-10-16
Well today I hardly booted Ubuntu, but all went well today. There was one point where I accidentally booted Ubuntu instead of Vista, at that point the screen was at the secondary monitor. But after rebooting the screen was back to the primary laptop monitor.

It feels kind of random as to when it happens, but it seems to happen most after Unity crashes (or X crashes), very weird.

---

