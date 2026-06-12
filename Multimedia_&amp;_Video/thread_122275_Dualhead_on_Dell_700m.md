---
title: "Dualhead on Dell 700m"
date: 2006-01-27
forum: Multimedia &amp; Video
---

### Post by blixer on 2006-01-27
I'm trying to get dualhead working on my Dell 700m laptop. It was working OK until I did a fresh install and upgraded from Hoary to Breezy.

Since Ubuntu moved from XF86 to x.org, I wasn't able to my my old config file exactly but what i've got now is fairly close. It is derived from a 700m on linux website 

My current xorg config is attached. It works fine in single head mode but the weirdness starts when I try and run it in dual head mode. The first time it tries to run, it exits with the following output (i've only included what I think is relevant, attachment limitations prevent me from attaching the rest):

```
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/X11R6/lib/modules/linux/libint10.a
(II) I810(0): initializing int10
(WW) I810(0): Bad V_BIOS checksum
(II) I810(0): Primary V_BIOS segment is: 0xc000
(EE) I810(0): vm86() syscall generated signal 11.
(II) I810(0): EAX=0x0000ff01, EBX=0x00064800, ECX=0x0000097e, EDX=0x00200000
(II) I810(0): ESP=0x00005f49, EBP=0x00005f8d, ESI=0x00005f75, EDI=0x00000636
(II) I810(0): CS=0xf000, SS=0x0100, DS=0x0000, ES=0xffff, FS=0x0000, GS=0x0000
(II) I810(0): EIP=0x0000f517, EFLAGS=0x00033046
(II) I810(0): code at 0x000ff517:
 26 8a 26 10 00 38 e0 75 0d f6 16 00 00 26 8a 26
 10 00 86 06 00 00 2a e0 8e c0 58 50 a9 00 02 74
(II) I810(0): VESA BIOS not detected

Fatal server error:
AddScreen/ScreenInit failed for driver 0


Please consult the The X.Org Foundation support 
```

The weird thing is that after I have received this error mesasge, I can no longer start X at all - not even in the previously working single head mode. I get this error:

```
==) I810(0): Default visual is TrueColor
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/X11R6/lib/modules/linux/libint10.a
(II) I810(0): initializing int10
(WW) I810(0): Bad V_BIOS checksum
(II) I810(0): Primary V_BIOS segment is: 0xc000
(EE) I810(0): vm86() syscall generated signal 11.
(II) I810(0): EAX=0x0000ff01, EBX=0x00064800, ECX=0x0000097e, EDX=0x00200000
(II) I810(0): ESP=0x00005f49, EBP=0x00005f8d, ESI=0x00005f75, EDI=0x00000636
(II) I810(0): CS=0xf000, SS=0x0100, DS=0x0000, ES=0xffff, FS=0x0000, GS=0x0000
(II) I810(0): EIP=0x0000f517, EFLAGS=0x00033046
(II) I810(0): code at 0x000ff517:
 26 8a 26 10 00 38 e0 75 0d f6 16 00 00 26 8a 26
 10 00 86 06 00 00 2a e0 8e c0 58 50 a9 00 02 74
(II) I810(0): VESA BIOS not detected
(EE) I810(0): VBE initialization failed.
(II) UnloadModule: "i810"
(II) UnloadModule: "int10"
(II) UnloadModule: "vgahw"
(II) Unloading /usr/X11R6/lib/modules/libvgahw.a
(II) UnloadModule: "vbe"
(II) UnloadModule: "int10"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
```

The only way that i've found to get back into X is to restart the computer and then it works fine. It seems as though the first attempt corrupts the video memory and prevents it from working at all in the future ... bizarre.

Suggestions greatly appreciated!

---

### Post by polpak on 2006-01-27
Are you actually trying for Dual head, or are you trying to clone the display?

I've had some similiar issues in trying to get the display to clone to both the external VGA and the LCD.

I can look at the final version of the xorg.conf I made and compare it to what you have later today.

---

### Post by blixer on 2006-01-27
Yeah, i'd like to get dual head working.
If I use i810switch and enable the CRT, I get a picture on both screens, though the CRT looks terrible, probably because it's trying to run with the same settings as the LCD.

---

### Post by short4lif2 on 2006-01-28
Yeah, I have had this problem before when I was trying to get my dual head working (which I never did)  You probably want to comment out or remove the second section of your xorg.conf that refers to PCI:0:2:0 because it could be causing a conflict.  That is how I fixed my X server.  Just try commenting out all the sections that refer to the secondary card, monitor, and screen.  I am not sure that that will work but it should.  After that comment out the information about your secondary screen in your serverlayout.  That should get X back up and working.  Another thing, ALWAYS have a backup copy of two versions of xorg.conf.  The first backup should be of the xorg.conf right after you installed, which, assuming you did not remove hardware, should always work, and the other backup should be of the latest errorless xorg.conf, which should also work and has all your recent successful changes. I learned all that the hard way

---

### Post by blixer on 2006-01-30
My X server works fine in single mode, i just get trouble when I try and run it in dual head mode. Unless anyone has any more suggestions, i'll take this over to x.org and see if they have any ideas.

Thanks for your help everyone.

---

### Post by mtrichardson on 2006-02-19
Have there been any updates? I would very much like to get this working on my 700m.

---

### Post by tatare99 on 2006-11-11
Same for me... :-( I've been working on this for the last 3 days (actually, for the last 3 nights...) and it still does not work.
I cannot get a 1280x1024 resolution on my external LCD monitor.
The best I had was a cloned 1024x768.
Do you know what to do to make it work ??

I'm kind of desperate !

---

### Post by blixer on 2006-11-11
There is a bug in the video driver.

See this post for the workaround:

[http://www.ubuntuforums.org/showthread.php?t=155762](http://www.ubuntuforums.org/showthread.php?t=155762)

---

### Post by tatare99 on 2006-11-12
I finally managed to get my external monitor working ! (without xinerama) :-) I'm happy !
I have a Dell 700m and an external L1919S.
Here is what I do:
when GRUB shows up, I press Fn+F8, then the output is redirected to my external monitor. The important thing is press Fn+F8 when GRUB shows up.

Then, I just have to change the resolution of the screen by adding in the modes: "1280x1024"
i.e.
Modes		"1280x1024" "1280x800" "1024x768"
And then, it just works !
I have the output on my external LCD monitor (with a 1280x1024 resolution) and nothing on the laptop... exactly what I wanted :-)
And when I restart my laptop without pressing Fn+F8 when GRUB shows up, the display is as usual on my laptop at 1280x800... it's great !

---

