---
title: "ATI 3D Acceleration"
date: 2006-05-30
forum: Multimedia &amp; Video
---

### Post by ejos on 2006-05-30
Did the ati drivers(not fglrx) just get 3D acceleration? I just did a default install through espresso and I'm using the ati driver. I just ran glxgears and it actually runs perfectly fine. I'm getting 3000+ fps and I know those rates suck but hey, it's accelerated. I'm really confused right now because it used to run *extremely* slow.

---

### Post by slavik on 2006-05-30
post the output of the following command

```
glxinfo | grep direct
```

---

### Post by ejos on 2006-05-30
eric@eric-desktop:~$ glxinfo | grep direct
*********************************WARN_ONCE*********************************
File r300_state.c function r300Enable line 456
TODO - double side stencil !
***************************************************************************
No ctx->FragmentProgram._Current!!
direct rendering: Yes

---

### Post by slavik on 2006-05-30
looks like you got accelaration. :D

what card is that? you should read the binary drivers wiki page to see if you want to install the new drivers and look at the ati's latest driver's notes to see if your card is there (if it is, I would install the drivers).

---

### Post by ejos on 2006-05-30
Oh ya I know, I get 20,000 fps with fglrx 8.25, but my point being there is **OPENSOURCE 3D ACCELERATION FOR ATI WTFBBQ**!?
BTW: X800 XT

---

### Post by ejos on 2006-05-30
Ahhhh!!!! I don't think anybody really understands what this means!!!!!!!!!!!! I get higher fps in tremulous than with fglrx. THIS IS ABSURD!:cool: :cool: :cool:

---

### Post by souled on 2006-05-31
Interesting stuff... I just tried glxinfo | grep direct and I got this output: ```
direct rendering: Yes
``` Also using ati drivers. However, I'm getting about 10 FPS from glxgears with a Radeon 9200. Something just doesn't seem right.

Edit: With a reboot I get about 1600 FPS.

---

### Post by francescob on 2006-05-31
[QUOTE=souled]Interesting stuff... I just tried glxinfo | grep direct and I got this output: ```
direct rendering: Yes
``` Also using ati drivers. However, I'm getting about 10 FPS from glxgears with a Radeon 9200. Something just doesn't seem right.

Edit: With a reboot I get about 1600 FPS.[/QUOTE]

with xpress 200m i have:
 glxinfo | grep direct
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect

---

### Post by st4rdr1ft3r on 2006-05-31
I just had a thought.
```
ls -al /usr/lib | grep dri
```
Whats the output of that?

---

### Post by francescob on 2006-05-31
[QUOTE=st4rdr1ft3r]I just had a thought.
```
ls -al /usr/lib | grep dri
```
Whats the output of that?[/QUOTE]

fra@francesco:~$ ls -al /usr/lib | grep dri
drwxr-xr-x   2 root root     4096 2006-05-30 15:07 dri

---

### Post by st4rdr1ft3r on 2006-05-31
ok, and now ```
ls /usr/lib/dri
```

---

### Post by francescob on 2006-05-31
[QUOTE=st4rdr1ft3r]ok, and now ```
ls /usr/lib/dri
```[/QUOTE]


```
fra@francesco:~$ ls /usr/lib/dri/
ffb_dri.so   mach64_dri.so  r200_dri.so    s3v_dri.so     tdfx_dri.so
i810_dri.so  mga_dri.so     r300_dri.so    savage_dri.so  trident_dri.so
i915_dri.so  r128_dri.so    radeon_dri.so  sis_dri.so     unichrome_dri.so
```

---

### Post by MadMan2k on 2006-05-31
[QUOTE=ejos]Oh ya I know, I get 20,000 fps with fglrx 8.25, but my point being there is **OPENSOURCE 3D ACCELERATION FOR ATI WTFBBQ**!?
BTW: X800 XT[/QUOTE]
yes there is - the r300 reverse engeneering project was included in Xorg7, but its still quite buggy (hangs my r9800) and does not support everything yet that fglrx supports

---

### Post by no1wantdthisname on 2006-05-31
I think 3d acceleration via the opensource drivers has been around for a long time.  At least this is true for my radeon 9600pro.  Performance seems to be alright, but opengl games show strange colors.  It got distracting after a while so I just went back to using fglrx.

---

### Post by ejos on 2006-05-31
I always knew about that r200 project that was seperate from the ati driver. But now there appears to be a new file, r300_state.c, in the ati drivers. I'm quite sure r300 acceleration is a new thing. Extending my excitement is the fact that it's accelerating my **r400** card!

---

### Post by Rackerz on 2006-05-31
How do you get glxgears to output fps? When I run glxgears, it doesn't output FPS.

---

### Post by ejos on 2006-05-31
glxgears -printfps

---

### Post by Rackerz on 2006-05-31
[QUOTE=ejos]glxgears -printfps[/QUOTE]

So simple, thank you :D.

---

### Post by st4rdr1ft3r on 2006-05-31
[QUOTE=francescob]```
fra@francesco:~$ ls /usr/lib/dri/
ffb_dri.so   mach64_dri.so  r200_dri.so    s3v_dri.so     tdfx_dri.so
i810_dri.so  mga_dri.so     r300_dri.so    savage_dri.so  trident_dri.so
i915_dri.so  r128_dri.so    radeon_dri.so  sis_dri.so     unichrome_dri.so
```[/QUOTE]

Hmm the fglrx one isnt there. Thats probably the problem since when I do the same command I get:
```

damien@nebula:~$ ls /usr/lib/dri/
atiogl_a_dri.so  i915_dri.so    r200_dri.so    savage_dri.so   unichrome_dri.so
ffb_dri.so       mach64_dri.so  r300_dri.so    sis_dri.so
fglrx_dri.so     mga_dri.so     radeon_dri.so  tdfx_dri.so
i810_dri.so      r128_dri.so    s3v_dri.so     trident_dri.so
```

Let me have a think about it since I'm not really in the right state to do it right now and i'll let you know.

---

### Post by almahtar on 2006-06-01
francescob: I have the xpress 200m in my laptop, with 128 mb of video ram.  In order to get it to work I had to go into bios and share 128 megs of system ram with the card (UMA+ sideport mode), then download the 8.25.18 drivers from ATI.com, delete all occurrances of fglrx.ko on my system (updatedb && locate fglrx.ko, then delete the files listed), and install the ATI drivers.  Let me know if you have any questions about any of that stuff, I know it was pretty quick'n'dirty.

---

### Post by Jabone on 2006-06-01
I managed to get 3D acceleration to work :) 
I had to prevent fglrx to load by adding fglrx to /etc/default/restricted-modules-common

By boot I tried to load manually fglrx but it gave me message that fglrx.ko doesn't found. Well I reinstalled linux-restricted-modules and fglrx.ko appeared /lib/modules/2.6.15-23-k7/volatile/fglrx.ko and I installed it by "modprobe fglrx" 

I didn't wont to do above stuff all the time to get acceleration to work so I edited restricted-modules-common and removed fglrx. Now lsmod shows fglrx is loaded, but usage count is 0. It should be 12 according when acceleration was working. 

I removed fglrx "modprobe -r fglrx" and stopped gdm. Started again and lsmod shows fglrx usage count 0 :( 

Is there any way to fix this. Would blacklisting fglrx in udev work? Has anybode tried?

Thanks in advance

Jabone

---

### Post by francescob on 2006-06-01
[QUOTE=almahtar]francescob: I have the xpress 200m in my laptop, with 128 mb of video ram.  In order to get it to work I had to go into bios and share 128 megs of system ram with the card (UMA+ sideport mode), then download the 8.25.18 drivers from ATI.com, delete all occurrances of fglrx.ko on my system (updatedb && locate fglrx.ko, then delete the files listed), and install the ATI drivers.  Let me know if you have any questions about any of that stuff, I know it was pretty quick'n'dirty.[/QUOTE]

i've done the uma+ sideport mode too, now i'll try the 8.25.18 drivers, cause i think i have a older one version. By the way, which version did you get from ati web site? 
RADEON 8500 Series and higher
or
Notebooks with ATI Graphics
?

---

### Post by almahtar on 2006-06-01
Francescob:

I went to (from the very first page at [www.ati.com](www.ati.com))

drivers and software - Linux ->
Linux display drivers and software->
motherboards with ati graphics (under the x86 section)->
ati proprietary blah blah(only option available)->
ati driver installer.

To run that baby you'll need to have a few things installed... off the top of my head you'll need build-essential, fakeroot, dh-make, dmake, and module-assistant.

so apt-get install those and you should be good for running the installer.  Like I said before make sure to delete all the old fglrx.ko files before you run it.  I've had a lot of problems in the past thinking it'd just overwrite them and it didn't.

---

### Post by francescob on 2006-06-01
[QUOTE=almahtar]Francescob:

I went to (from the very first page at [www.ati.com](www.ati.com))

drivers and software - Linux ->
Linux display drivers and software->
motherboards with ati graphics (under the x86 section)->
ati proprietary blah blah(only option available)->
ati driver installer.

To run that baby you'll need to have a few things installed... off the top of my head you'll need build-essential, fakeroot, dh-make, dmake, and module-assistant.

so apt-get install those and you should be good for running the installer.  Like I said before make sure to delete all the old fglrx.ko files before you run it.  I've had a lot of problems in the past thinking it'd just overwrite them and it didn't.[/QUOTE]

yeah i,ve already installed ati proprietary drivers... i was just wondering if is better to get the version for notebook or not... by the way the new version totally messed up my graphics... now almost everything in kde is trasparent (menu, windows etc...) and after a while it hangs..

---

### Post by ejos on 2006-06-01
This thread has derailed, we're talking about the driver called "ati", not "fglrx" which is the proprietary driver from ATI. Does anybody else have 3D acceleration coming from these open source drivers?

---

### Post by almahtar on 2006-06-01
I'm sorry, ejos.  Didn't mean to hijack the thread.  Let me wrap it up real fast: francescob - the 200M is a really generic chipset used for onboard graphics in desktops and laptops both.  The notebook drivers section is just high-end (like Alienware) stuff, and I don't know if there are even Linux versions of those drivers.  PM me with a bit more info about what's going on with the display corruption, please. I'd like to help.


Once again, sorry to hijack the thread.

---

### Post by whatever on 2006-06-02
[QUOTE=ejos]This thread has derailed, we're talking about the driver called "ati", not "fglrx" which is the proprietary driver from ATI. Does anybody else have 3D acceleration coming from these open source drivers?[/QUOTE]
using the kubuntu live-cd it works for me with my radeon 9700. i didn't try the ubuntu cd, but i guess it also works there. glxgears runs at ~2000 fps and ppracer is playable, but [warsow](http://warsow.net/) refuses to start.

however, on my ubuntu dapper installation (which is in fact a warty to hoary to breezy to dapper dist-upgrade ;)) Xorg freezes when i use the "ati" driver and try to load the glx extension. fglrx is working ok here, glxgears runs at about twice the framerate of the open source driver. if only fglrx's 2d acceleration was faster...

edit: when using the live-cd's xorg.conf "ati"+glx also works with my installation :)
edit2: the "AGPFastWrite" option caused the freeze

---

### Post by bosonflux on 2006-06-02
I'm using the "ati" driver. I get about 2050 fps with glxgears using a Radeon 9000 AIW. When fglrx worked, just a few days ago, I got 2500 fps. Currently, Chromium works fine but the GL screensavers all freeze the computer up solid after a few minutes. Despite all the superb help and suggestions, this card simply will not work with fglrx. My installation is a Dapper starting with flight 4, with all upgrades applied since. The dist-upgrade 4 days ago was a disaster for many people with older cards like mine.

---

### Post by whatever on 2006-06-02
[QUOTE=bosonflux]I'm using the "ati" driver. I get about 2050 fps with glxgears using a Radeon 9000 AIW.[/QUOTE]
open source 3d support for r200 hardware has been available for years now (afaik). i think this thread is about r300+ hardware.

---

### Post by bosonflux on 2006-06-02
The original post by ejos only asks about ati drivers. He does not stipulate r200, r300, or even state what card he is using.

---

### Post by linuksamiko on 2006-06-02
How does ist come that acceleration is (or atleast seams to be) activated, according do glrxinfo but every time I try to play a game like nexuiz there is nothing screensavers are slow too.
glxgers is just fine I get quite alot of frames (as much as with the regular ati-drivers)

---

### Post by Robert A. Morin on 2006-09-25
Yeah, that's more or less my problem, atm.  I happen to be running a notebook with an ATI Mobility X300 graphics card (it's a Dell Inspiron 6000, no less, and fear that I may have a dead end card that may not be upgradable).  I was hoping to have the same 3D Acceleration with Ubuntu 6.06 that I do with Win XP Pro SP2, but after all the installation, here's what I got:

```

morinro@morinro-laptop:~$ glxinfo | grep direct
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect
morinro@morinro-laptop:~$ ls -al /usr/lib | grep dri
drwxr-xr-x   2 root root      624 2006-09-25 08:50 dri
morinro@morinro-laptop:~$

```

Doesn't seem like that's gonna do much of anything.  Wonder what the next steps are gonna be...  Here's what I get with fglrxinfo:

```

morinro@morinro-laptop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

```

I knew that I configured the Synaptic Software Manager for the xorg.driver.fglrx package correctly, and it seemed to confirm my card as an ATI card, but no can do on the 3D acceleration.  Plus, since this is a notebook, I'm not so sure that there's any way to swap the graphics card on this bad boy, either.

---

