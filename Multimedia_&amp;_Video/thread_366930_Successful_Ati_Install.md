---
title: "Successful Ati Install ?"
date: 2007-02-21
forum: Multimedia &amp; Video
---

### Post by doobydave on 2007-02-21
Ok, breathe, try to stay calm......

I appear to have installed the drivers correctly (using the various methods described at the end of the how-tos) yet the graphics are an utter joke. Much worse in fact than the open-source ones supplied.

My glxinfo show DRI:yes and fglrxinfo shows the fglrx module being used.

Currently using dapper after trying on edgy (same result)

I've read about nforce2 issues but not sure if they are still applicable.
I have also tried the k7 kernel optimisations yet same results (although better monitor detection).

fgl_glxgears give ok (i think) score of >400 but
glxgears -printfps only scores 125

I have an abit nf-7s rev2 board and a gigabyte ati 9600 Pro 256MB

Any thoughts?

Sorry to post on such a prolific topic, but my patience is dwindling. It may very well be time to send my ati card on a one way holiday!
Thanx in advance (he says presumptuously)

---

### Post by r4ik on 2007-02-21
Install the driver from here,

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Good luck !

---

### Post by doobydave on 2007-02-21
Sounds too good to be true - so i shall try it right away!

cheers.

---

### Post by r4ik on 2007-02-21
Let me know if it works will you ?

---

### Post by doobydave on 2007-02-21
Nice program..... but it has not made any difference.

I saw that a new release is available from the ati site. i might give that a go.

cheers.

---

### Post by r4ik on 2007-02-21
Chips it did not work.
hope you get it going.

---

### Post by doobydave on 2007-02-21
Got the latest drivers.
Used ENVY to uninstal then ran the ati installer directly with
 sudo sh ati-driver-installer-8.34.8-x86.x86_64.run

during install, an error occurred (missing file - "atiogl_a_dri.so") but install finished.  Rebooted, tried glxgears again and still 125 fps. very slow.

Just about to give up, and my screensaver (which usually laughs at me for my choice af gpu) cuts in and low and behold its much better.

Dont know if it is the later driver version or the way i installed it. Might try again later.

Still dont know why glxgears is so slow.

---

### Post by NT4usB on 2007-02-21
I'm seeing 450-500 from my 9600 Pro.

ct@wimp:~$ fglrxinfo
display: :0.0 screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 Generic
OpenGL version string: 2.0.6286 (8.33.6)

ct@wimp:~$ glxgears -printfps
2488 frames in 5.0 seconds = 497.506 FPS
10019 frames in 5.0 seconds = 2003.779 FPS*
26047 frames in 5.0 seconds = 5209.367 FPS*
2394 frames in 5.0 seconds = 478.800 FPS
2490 frames in 5.0 seconds = 497.625 FPS
2487 frames in 5.0 seconds = 497.388 FPS
2497 frames in 5.0 seconds = 499.023 FPS
2501 frames in 5.0 seconds = 500.186 FPS
2501 frames in 5.0 seconds = 499.822 FPS
2501 frames in 5.0 seconds = 500.186 FPS
2501 frames in 5.0 seconds = 499.822 FPS
2501 frames in 5.0 seconds = 500.185 FPS
2501 frames in 5.0 seconds = 499.823 FPS

*minimized.

ed: installed using Envy, btw.

---

### Post by theevilsithlord on 2007-02-22
I have the same problem with my Radeon 9700. I just used Envy and it installed newer drivers successfully, but I still get the same poor results. I know glxgears technically is not a benchmark, but desktop performance is seriously lacking as well.

```
fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9700 Generic
OpenGL version string: 2.0.6286 (8.33.6)

```

```
glxgears -printfps
2091 frames in 5.0 seconds = 418.095 FPS
2099 frames in 5.0 seconds = 419.696 FPS
2089 frames in 5.0 seconds = 417.696 FPS
2093 frames in 5.0 seconds = 418.496 FPS
2108 frames in 5.0 seconds = 421.495 FPS

```

---

### Post by doobydave on 2007-02-22
Right.

Back on Edgy after breaking my dapper (described above - with rather good 3d unfortunately).
Good old ghost!

Tried Envy again with same results. Not good.

Why doesn't this subject have its own section. Ther seems to be rather a large overlap between "multimedia and gaming" and "hardware and Laptops"

I could have ordered and received an nvidia card in the time i've spent faffing around. Maybe windows isn't so bad after all ......

---

### Post by doobydave on 2007-02-23
Has anyone got fglrx to work on an nforce 2 motherboard?

---

### Post by doobydave on 2007-02-23
Think this may point to the problem. Anybody know its relevence?

dave@davesbuntu:~$ grep WW /var/log/Xorg.0.log
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
(WW) fglrx: No matching Device section for instance (BusID PCI:2:0:1) found
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(WW) fglrx(0): Option "VendorName" is not used
(WW) fglrx(0): Option "ModelName" is not used

---

