---
title: "Video 'stuttering'"
date: 2010-10-25
forum: Multimedia Software
---

### Post by Ampi on 2010-10-25
Lately all videos I play, whether it´s .avi, .mkv, .vob or a DVD, it keeps stuttering during the whole duration of it. Sometimes worse, sometimes better. 
Now when I watch a video Im just waiting for it to go start enoying me. I do not know why.
I use the movie player and VLC. I tried it on a friend's Window's computer and no problem. How can I fix this?
I tried to keep my drivers and such updated but I don't get it fixed and to be quit honest I just don't know anymore what to look for.

Any ideas? And what more information do I need to give?
The graphics card is in my signature and I don't have any 3D things installed because in previous versions that didnt work well.

---

### Post by bluekarasu on 2010-10-25
In VLC, be sure to enable the checkbox "accelerated output(overlay)" in the video preferences.

If you have a nvidia card (8xxx or newer) and the proprietary driver, you can try to install libva1 and activate the "GPU acceleration" in VLC (under codec)

Finally, try to disable the compiz effects.

---

### Post by lidex on 2010-10-25
There have been issues with this plugin:
```
gstreamer0.10-pulseaudio
```
Try uninstalling it.

---

### Post by bluekarasu on 2010-10-26
> **lidex said:**
> There have been issues with this plugin:
```
gstreamer0.10-pulseaudio
```
Try uninstalling it.

I don't recomend to do that, it as nothing to do with VLC.

---

### Post by Ampi on 2010-10-27
Okay, let me see.

First I will nog yet do the gstreamer plugin because we apparently don't agree.. :)

Second. I don't have Compiz installed, in my Appearences my Visual Effects are on 'Normal'. Should be okay right? Or do I need to disable them entirely?

Third. I have an ATI card, I don't know exactly which one, I think a Radeon HD 3200 Graphics. The *ATI/AMD proprietary FGLRX graphics driver* is not installed because in previous installations of Ubuntu it gave horizontal lines on my screen. So I guess the problem is here? Should I maybe activate it?
For this reason I haven't checked the box with GPU acceleration just yet.

Fourth. The accelerated output (overlay) was already checked.

Hopefully we get a bit closer to a solution..

---

### Post by lidex on 2010-10-27
I should have read more closely as vlc does not use gstreamer. So it would appear to be a more system-wide issue. You're probably on the right track with the video driver. Does the audio stutter as well as the video?
What is the output of these commands:
```
sudo lshw -C display
uname -a
```

---

### Post by juky on 2010-10-29
Hello,

I have the same issue while playing all multimedia, such as flash on website, mp3 locally, avi locally etc....

My output:


> belina@belina-laptop-UBUNTU:~$ sudo lshw -C display
[sudo] password for belina: 
PCI (sysfs)  
  *-display:0             
       description: VGA compatible controller
       product: 82852/855GM Integrated Graphics Device
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:11 memory:d8000000-dfffffff memory:d0000000-d007ffff ioport:1800(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: 82852/855GM Integrated Graphics Device
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=0
       resources: memory:e0000000-e7ffffff memory:d0080000-d00fffff

> belina@belina-laptop-UBUNTU:~$ uname -a
Linux belina-laptop-UBUNTU 2.6.35-22-generic #35-Ubuntu SMP Sat Oct 16 20:36:48 UTC 2010 i686 GNU/Linux

Ideas?

---

### Post by lidex on 2010-10-30
> **juky said:**
> Hello,

I have the same issue while playing all multimedia, such as flash on website, mp3 locally, avi locally etc....

My output:
Ideas?
Try starting your program in a terminal and see if any errors are shown there.

---

### Post by Ampi on 2010-11-01
Apart from the output there is another thing. I had some problems with my videos on youtube and vimeo suddenly. As in they were on double speed and with no sound. I solved this by removing the .pulse folder. I do now have an audio problem on the vlc and movie player. Sooo Im not quite sure what to do.. One solution seems to feed another problem.. 

EDIT: sounds on vlc and movie player suddenly works...

This is my lshw -C display output

```

 *-display               
       description: VGA compatible controller
       product: Radeon HD 3200 Graphics
       vendor: ATI Technologies Inc
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:18 memory:d0000000-dfffffff ioport:ee00(size=256) memory:fdfe0000-fdfeffff memory:fde00000-fdefffff

```

And this is my kernel

```
Linux amparo-desktop 2.6.35-22-generic #35-Ubuntu SMP Sat Oct 16 20:45:36 UTC 2010 x86_64 GNU/Linux
```

---

### Post by lidex on 2010-11-02
> **Ampi said:**
> Apart from the output there is another thing. I had some problems with my videos on youtube and vimeo suddenly. As in they were on double speed and with no sound. I solved this by removing the .pulse folder. I do now have an audio problem on the vlc and movie player. Sooo Im not quite sure what to do.. One solution seems to feed another problem.. 

EDIT: sounds on vlc and movie player suddenly works...

This is my lshw -C display output

```

 *-display               
       description: VGA compatible controller
       product: Radeon HD 3200 Graphics
       vendor: ATI Technologies Inc
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:18 memory:d0000000-dfffffff ioport:ee00(size=256) memory:fdfe0000-fdfeffff memory:fde00000-fdefffff

```

And this is my kernel

```
Linux amparo-desktop 2.6.35-22-generic #35-Ubuntu SMP Sat Oct 16 20:45:36 UTC 2010 x86_64 GNU/Linux
```
Does the video still stutter?

---

### Post by Ampi on 2010-11-03
VLC yes :(
Movie Player yes :(
VLC player with actual DVD: yes :(
Movie player with actual DVD: seems to be less stuttering..

---

### Post by a-user on 2010-11-03
> **Ampi said:**
> 
Second. I don't have Compiz installed, in my Appearences my Visual Effects are on 'Normal'. Should be okay right? Or do I need to disable them entirely?

wrong. any option but the first one enable compiz using.

if you want to be sure you doulc disable the compiz extension in your xorg.conf file.

---

### Post by Z06Gal on 2010-11-03
I have stuttering on chrome only in live streaming video.  I have to use ff for that.  


Robin

---

### Post by Z06Gal on 2010-11-03
I don't know if this will help you but I just installed the 2.6.36 rc8 kernel and it resolved my video issues or it seems to have I should say.  No stuttering and it runs in full screen perfectly.  If you choose to upgrade your kernel, this is what I used.  It really is "painless" as long as you install them in the order recommended here:

[http://forums.linuxmint.com/viewtopic.php?f=42&t=40185&hilit=+kernel+how+to](http://forums.linuxmint.com/viewtopic.php?f=42&t=40185&hilit=+kernel+how+to)

Good luck and I hope this will help you. :)

Robin

---

### Post by Ampi on 2010-11-04
Ok let me see.
I got rid of compiz entirely, as in I put the effects on none and deinstalled any last bit through Synaptic and rebooted.
Now
VLC: no video stuttering :)
Movie Player: still video stuttering
VLC with actual DVD: loads of stuttering.. :(
Movie Player with actual DVD: still some minor stuttering

Soo... Im confused.. 

The whole kernel thing. I guess I have to take a moment for that. Could things go horribly wrong with that? I mean, I should not do that in between jobs, right? :)
And even if it wouldn't work for the sound, if it still a good idea to keep or should I then go back. 
I just installed the 10.10 shouldn't my kernel already be up-to-date?

P.S. When the video stutters the sounds stutters in the same way.. I dont know if I mentioned this or if it is important...

---

### Post by lidex on 2010-11-04
> **Ampi said:**
> Ok let me see.
I got rid of compiz entirely, as in I put the effects on none and deinstalled any last bit through Synaptic and rebooted.
Now
VLC: no video stuttering :)
Movie Player: still video stuttering
VLC with actual DVD: loads of stuttering.. :(
Movie Player with actual DVD: still some minor stuttering

Soo... Im confused.. 

The whole kernel thing. I guess I have to take a moment for that. Could things go horribly wrong with that? I mean, I should not do that in between jobs, right? :)
And even if it wouldn't work for the sound, if it still a good idea to keep or should I then go back. 
I just installed the 10.10 shouldn't my kernel already be up-to-date?

P.S. When the video stutters the sounds stutters in the same way.. I dont know if I mentioned this or if it is important...
Before you change kernels, try this fix:
[http://ubuntu-ky.ubuntuforums.org/showpost.php?p=9961868&postcount=29](http://ubuntu-ky.ubuntuforums.org/showpost.php?p=9961868&postcount=29)

---

### Post by Ampi on 2010-11-05
Ok I did it, these are the results..

VLC: **no** video stuttering 
Movie Player: **no** video stuttering
VLC with actual DVD: **no** video stuttering 
Movie Player with actual DVD: **no** video stuttering

:D:D:D:D:D:D
Finally! 

So what exactly is the tsched=0? Im guessing tsched=time schedule but I don't know what it does.. But Im kind of curious what the cause was..

EDIT: does this mean that the last fix was the 100% fix? If I would want compiz back for example or update the third party 3d acceleration driver (for  now I dont) would that mess up again?

---

### Post by lidex on 2010-11-05
> **Ampi said:**
> Ok I did it, these are the results..

VLC: **no** video stuttering 
Movie Player: **no** video stuttering
VLC with actual DVD: **no** video stuttering 
Movie Player with actual DVD: **no** video stuttering

:D:D:D:D:D:D
Finally! 

So what exactly is the tsched=0? Im guessing tsched=time schedule but I don't know what it does.. But Im kind of curious what the cause was..

EDIT: does this mean that the last fix was the 100% fix? If I would want compiz back for example or update the third party 3d acceleration driver (for  now I dont) would that mess up again?

You should be OK to use compiz and change drivers.

---

### Post by Closrapexa on 2010-11-05
I'm still having a problem with this. I don't know what information I should provide, but I installed 10.10 a few days ago on my Thinkpad r50e, and there seems to be a lag in the mouse movement, and a severe stutter in video. When I play only music, it's a little better, but still very noticeable.

I thought gstreamer-properties would help, and I switched from pulse to alsa, played with the video options, and I also tried the tsched=0 option, but to no avail. The video stutters in Youtube and other video sites as well as VLC.

The output of lspci in terms of graphics is 

00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)

I don't know if I have given enough information, but I would be glad of any help, especially since I had to skip a version, and used 9.10 until now, since I had the dreaded Black Screen of Death problem with 10.4, and could not fix it, as all the solutions I found online didn't help.

When I try to play a song on VLC through the terminal, I get an error every time the sound "jumps".

VLC media player 1.1.4 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0x978dd6c] dummy interface: using the dummy interface module...
Blocked: call to setenv("_PX_CONFIG_ORDER", "", 1)
Blocked: call to setenv("_PX_CONFIG_ORDER", "", 1)
[0x9796644] main input error: ES_OUT_SET_(GROUP_)PCR  is called too late (pts_delay increased to 300 ms)
[0x9796644] main input error: ES_OUT_SET_(GROUP_)PCR  is called too late (pts_delay increased to 344 ms)

I suspect it could be a graphics problem, as when i try to enable desktop effects, I get an error message, saying they can't be enabled

---

### Post by no2498 on 2010-11-07
you may need to restart the computer to use this fix

it comes from the cheese help faq's

The video is sluggish/has a slow response. What can I do?


      You may have set "ximagesink" ("X Window System (No Xv)") as video-output.
      This means, that your cpu is doing all the work. Change it to "xvimagesink"
      ("X Window System (X11/XShm/Xv)") in order to let your graphics card do the work.
    


      To change the settings, run "gstreamer-properties", click the Video tab
      and change the appropriate settings.
    

lovinglinux says this does NOT help flash

but im good with what i get for doing it

---

### Post by Closrapexa on 2010-11-07
Thanks for your reply

I just tried what you said, but when I change the setting and try to test it, I get the error message

X Window System (X11/XShm/Xv): Could not initialise Xv output

Other than that, there is no change :(

---

### Post by no2498 on 2010-11-07
look in the package manager and see if you have 

gstreamer good,bad,ugly,and 10 installed

---

### Post by Closrapexa on 2010-11-07
Yes I do. I'll try checking it with a livecd and see if the problem persists.

---

### Post by Closrapexa on 2010-11-07
Actually, the problem is a little less with the live cd, but still exists. Also, I noticed that the glitches aren't just visual, as when I tried to move something from a usb to the hard drive, it fails as well, when the glitches occur.

Also, if I play a song through the terminal (ctrl f1) it has the same glitches

---

### Post by lidex on 2010-11-07
What kernel version are you using:
```
uname -a
```
Try booting into an older kernel.

---

### Post by Closrapexa on 2010-11-07
This is my kernel 

Linux mozes 2.6.35-22-generic #35-Ubuntu SMP Sat Oct 16 20:36:48 UTC 2010 i686 GNU/Linux

---

### Post by lidex on 2010-11-07
Did you try a different kernel? I've seen also 2.6.35.23 out there.
Try this:
```
sudo apt-get update
sudo apt-get upgrade
sudo update-grub
```
Reboot and post this output please:
```
cat /var/log/Xorg.0.log
```

---

### Post by prognosticon on 2011-10-23
hi 
i tried al the versions in your posts but nothing helps.
Now i tried to log in with ubuntu 2d and play a hd movie with totem video player and its way better but not the best you can get.
What does that mean?
Thanks bye.

---

### Post by Closrapexa on 2011-10-23
prognosticon, try using vlc player, I find it's better. But to tell the truth, I haven't had any problems with 11.10, it just worked out of the box, video-wise. Of course, I'm using unity 2d, but I'm looking into going back to gnome, so that's not much of an issue

plus, I could never get HD movies to work on my machine, they always stutter. But with the size of my screen, and it's age, I just accepted it and only watch regular quality movies on it

---

### Post by prognosticon on 2011-10-23
no i get the best results with totem i tried the other players but totem works best.
I use my laptop as a multimedia center and watched al my movies in hd on my tv but with WIN7.
Now i want to switch to ubuntu, unity is not important it could be any Desktop but it should play hd Movies.

---

### Post by BicyclerBoy on 2011-10-23
This is/was a really old thread & the current problem may not be related to earlier posts...

Unity/compiz/composite could be the problem.
You can not get rid of unity from 11.04 11.10 without replacing the desktop manager e.g. Gnome 3 or Xfce

You can't turn composite off in ubuntu 11.10..no classic login (11.04) & unity 2d still has compiz.

What video h/w is in the laptop ?
Try this terminal:
glxinfo | grep OpenGL

---

### Post by prognosticon on 2011-10-24
> **BicyclerBoy said:**
> This is/was a really old thread & the current problem may not be related to earlier posts...

Unity/compiz/composite could be the problem.
You can not get rid of unity from 11.04 11.10 without replacing the desktop manager e.g. Gnome 3 or Xfce

You can't turn composite off in ubuntu 11.10..no classic login (11.04) & unity 2d still has compiz.

What video h/w is in the laptop ?
Try this terminal:
glxinfo | grep OpenGL

hi sorry i forgot to check the date on this thread  i found it with the search function.
I use ubuntu 11.10 on a Sony vgn fw21e with a ATI mobility radeon hd 3470.
FGLRX is installed with CCC 11.8
 I tried glxinfo but it says it is not installed.
Thx

---

