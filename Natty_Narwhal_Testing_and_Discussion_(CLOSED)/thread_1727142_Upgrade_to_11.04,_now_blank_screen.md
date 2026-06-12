---
title: "Upgrade to 11.04, now blank screen"
date: 2011-04-12
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by andromedar on 2011-04-12
Hi!

I have this problem:
I upgraded yesterday from 10.10 to 11.04 beta, but now the laptop displays only a black screen with mouse pointer. The pointer moves when i move my mouse. It's the desktop that doesn't show. The resolution of the black screen seems to be fine, as the mouse cursor is the same size as on 10.10. It takes also unusually long time to load to that stage.

What could be wrong?

Thanks
Andrej

---

### Post by coffee412 on 2011-04-12
I had the same problem. I upgraded from 10.10 to 11.04 and stared at a black screen with a mouse. I dont know what the problem is. I have 2 drives in my system sda is my fedora 13 o/s and sdb is my ubuntu. I did notice some other stuff also about 11.04:

1. I didnt get a prompt for where to install the boot loader. Thus, It wiped out my fedora grub boot loader and I had to repair that.

2. I had 2 errors pertaining to ~/.ICEauthority and gconf crashing.

I just wiped my ubuntu disk because I didnt have much on it. I wiill try a new install to it but I would prefer to have the option of where to put the grub bootloader.

coffee

---

### Post by MAFoElffen on 2011-04-12
Please be patient.  Becuase this is a beta1 release, don' be confused when the moderators move this post to the natty dev/discussion area ...

First... What are your video/cards?  Natty is heavily testing changes in the video and in drivers... but there are many fallback video options that you can use on the LiveCD StartP and at Bootime from Grub... but info about your system would help for that.

Second, well... H had a bad experience with this in the past a few years back, so... I usually do a some-what manual partitioning, then "really pay attention" during the install process for the grub and where it goes.  I think a lot of install problems would be avoided if that process was made a little clearer and they put those items in neon colors with explanations and warninggs on what happens if... But instead, we can help you recover from grub problems also.

---

### Post by uRock on 2011-04-12
Moved to Natty Narwhal Testing & Discussion.

---

### Post by andromedar on 2011-04-13
Hello, i am using nvidia GeForce 7200/256MB RAM on a HP dv6000 notebook.

---

### Post by Ron Chaine on 2011-04-16
This affects me too.  Intel 4500MHD graphics card.  It somewhat works with fbdev driver instead of Intel.

When I run startx from terminal, it fills up with

"(EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid Argument"

---

### Post by MAFoElffen on 2011-04-16
> **andromedar said:**
> Hello, i am using nvidia GeForce 7200/256MB RAM on a HP dv6000 notebook.
Do you get a grub menu at start? If not, press shift key to bring it up.  If so try the rescue mode > low graphics... after startup system > administration > additional drivers. 

If you can't bring up low graphics mode, rebbot and get to the grub menu, cursor to the main boot menu item. press "e" > go to the kernel boot line and append " text " to the end of the line.  Press ctrl-x to boot... it will boot into a text console mode. Login as you > install the dirver...
```

sudo apt-get install nvidia-current
sudo nvidia-xconfig
```Tell me happans or how it goes with that.

NOTE: A alternate way that might also help the others with diffrent video cards-- is to try different kernel boot options, using "e" at the grub menu.  Go to the kernel boot line... try these options (one at a time/not together):
```
nomodeset
xforcevesa
i915.modeset=0 xforcevesa
vga=xxx (replacing/using a vesa mode that your card supports, such as 771)
``` These options would be added near the end of the line, after the kernal name,

Another thing you might try is to drop down the the grub CLI (command line interface) via pressing "c" while in the grub menu...  From there you could use
```

GRUB> echo $linux_gfx_mode

```to see what vidoeo mode it is currently set to... It will most likely be set at "keep". If you then 
```
echo $gfxmode
``` it will most likely say "auto' which is the default.

Then use 
```
GRUB> vbeinfo
```to get the video modes as grub sees them on your hardware.

Use "set" and "unset" commands
```
set GFXMODE=680x480

```or to any mode that your video supports.
 
I think you once you found a mode that worked, you would then change /etc/grub.d/00_header file where it says set gfxmode=auto to the mode that worked.

Hope this info helps.

---

### Post by MAFoElffen on 2011-04-16
I do see where some people are using the startup-manager package to resolve a similar problem were this application is changing and updating the grub config file to makechanges in the graphics resolution and color depth... Let me look into what the actual grub changes that are being made / that are actually helping... and see if they would help with these problems.

---

### Post by MAFoElffen on 2011-04-16
Same as mentioned before--

If you use startup-manager, it will make edits to the grub files... For instance, changeing the following setting to:
display resolution 1024x768
color depth 16 bit 

and under the advanced tab:
bootloader 1024x768

Chages to grub file section 00_header, line that says "set gfxmode=auto" to "set  gfxmode-1024x768" and then add/appends vga-758 to the kernel boot line  in 10_linux section...

Same fixes as mentioned above, you just need to finds the resolutions and modes that your graphics card supports and make those changes.  Another good tool for finding graphics modes is to install hwinfo 
```
sudo apt-get install hwinfo
```and use via```
sudo hwinfo --framebuffer
```

---

