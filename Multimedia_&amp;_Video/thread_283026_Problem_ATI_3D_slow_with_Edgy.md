---
title: "Problem: ATI 3D slow with Edgy"
date: 2006-10-23
forum: Multimedia &amp; Video
---

### Post by stitch on 2006-10-23
Hi, I have an ATI Radeon 9550SE video card. It worked ok on Dapper, but with Edgy everything seems to be slower. I fI issue the classic GLXGEARS command, it works, but gears rotate VERY slow, as they were 'braked' by something.
Is there anyone that had the same problem ?

Obviously, I run an RC Edgy in this moment ;-)

Ciao/Dim

---

### Post by CarpKing on 2006-10-23
What drivers are you using? Default radeon, or proprietary fglrx?

---

### Post by stitch on 2006-10-24
ATI drivers, sorry I forgot to put the information ;)

Thanks for help

Brgds

P.S. Here are the other H/W details:

    PC Pentium IV 2.4 GHz
    RAM 1 Gb

---

### Post by jsully1 on 2006-10-26
I'm having this same issue - it's very noticeable unfortunately.

---

### Post by Melcar on 2006-10-26
Just installed the propietary ATI drivers in Edgy and I'm having the same problem.  fglrx and glxinfo show the correct information (driver name and direct rendering enabled) and glxgears gives me about the same readings as with Dapper (about 2000fps on my 200M) but things like screensavers run noticeably slow.  Going to try installing Beryl and see how it goes.

---

### Post by zvezdogled on 2006-10-27
Under edgy i can't even install fglrx driver](*,) , but everything  worked under dapper just fine.
I have ati radeon mobility 9700...

---

### Post by boban on 2006-10-27
> **zvezdogled said:**
> Under edgy i can't even install fglrx driver](*,) , but everything  worked under dapper just fine.
I have ati radeon mobility 9700...

I don't know if it will help you, but I have radeon 9500 pro and followed this steps to install drivers:

1) instal fglrx
```

sudo aptitude install fglrx-driver

```

2) Changed ati to fglrx in device section of may /etc/X11/xorg.conf. That section looks now like that:

```

Section "Device"
	Identifier	"ATI Technologies, Inc. R300 AD [Radeon 9500 Pro]"
	Driver		"fglrx"
	BusID		"PCI:2:0:0"
EndSection

```

3) Add at the end of xorg.conf following section:

```

Section "Extensions"
	Option "Composite" "disable"
EndSection

```

4) reboot

(5) install xgl :) )

I hope it will help...

---

### Post by Carlos Araujo on 2006-10-27
Edgy: The ATI drivers continues with precarious support.We fail!!

OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

---

### Post by zvezdogled on 2006-10-27
thank you boban
now it works 
problam was with Composite

---

### Post by boban on 2006-10-27
I'm glad I could help :)

---

### Post by sloggerkhan on 2006-10-27
Dude, you're using Mesa... that's not a real driver. 
add this to xorg.conf (or make similar for your card):
[COLOR="Red"]
Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon Mobility X700 (RV410 PCIE)"
	Driver      "fglrx"
	Option	    "UseFBDev" "true"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"

Section "Extensions"
	Option	    "Composite" "0"
EndSection
[/COLOR]

[COLOR="Blue"]$ fglrxinfo[/COLOR]

should give something like: 

[COLOR="Blue"]display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON X700 Generic
OpenGL version string: 2.0.6011 (8.28.8 )[/COLOR]

on a side note, I just notice fglrxinfo for my card says "XFree86-DRI" missing on display ":1.0"
but everything seems to be working... what's up with that?

---

### Post by Melcar on 2006-10-29
Performance is so bad.  Well not that bad, but definately worse than in Dapper.  The drivers are correctly installed (8.29.6) and Direct Rendering is working.  I even got Beryl going and it works fine (just like in Dapper).  However, glxgears gives me half of what I used to get in Dapper (around 3000fps down to 1500fps) and 3D screensavers are incredibly choppy.  Anyone found a fix yet?

---

### Post by sgominator on 2006-10-31
I have the same problem with Edgy on an Apple Powerbook G4 17" (Ati Mobility Radeon 9600 M10) so i can't install fglrx (ppc architecture)
I have SUSE 10.1 on the same machine (Xorg 6.9.0) and 3D works beautyfully (no sound, instead :(
What's been lost between 6.9.0 and 7.1.1 ???

---

### Post by Melcar on 2006-11-01
I just installed the new 8.30 driver and performance seems to be better.  I'm back to 3000fps but things still are rather choppy (horrible performance in screensavers).

---

### Post by timmy-mac on 2006-11-01
Hi all,

Thought I'd jump in with an observation I've made.. 

I've got the same prob as the OP (and a few others).  I have installed the fglrx drivers from the repos and the new ones from the ATI site.  I have had both installed 'correctly' but my performance is still poor (to none-existent).

Here's the evidence that everything *should* be ok:

> 
tim@edgy:~$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9550 Generic
OpenGL version string: 2.0.6119 (8.30.3)


> 
tim@edgy:~$ glxinfo |grep vendor
server glx vendor string: SGI
client glx vendor string: ATI
OpenGL vendor string: ATI Technologies Inc.


I've got Composite disabled in my xorg.conf as well.

Now, I'm aware that 'glxgears-is-not-a-benchmark'..  but that and fgl_glxgears are both getting framerates of less than 300 FPS.

Google Earth works ok.. 

Cedega has some video 'Tests'.  My system passes the one titled 'OpenGL Direct Rendering' but fails on '3D Acceleration'.

*However*, as Cedega runs that first test, it uses glxgears.  In this instance the framerate looks *much* higher.  Unfortunately, there are no numbers to compare..  but I am 100% sure they're spinning at a 'proper' speed.

I just kinda wondered if anyone could diagnose the problem with that info.  Like, does anyone know if Cedega runs a different command to make that test, or what else might be different??

It's all new to me.  First time I've used ATI and Lunix.

:-k 

Tim

---

### Post by pony-tail on 2006-11-01
I too am having problems in edgy with fglrx drivers on 2 machines 1 x32bit 1 x64bit this problem is to do with xorg7.1/aiglx which ships as default on edgy .
Please ! contact ATI (linux driver feedback ) let them know . Maybe (wishful thinking here ) just maybe they will rectify it in the next release if enough people complain.
This problem is not restricted to K/X/Ubuntu SuSE 10.1 / 10.2 both have this issue . Some of the issue is that ATI build their drivers for Redhat (SuSE as an afterthought) and Deadrat uses xorg 6.8.x /7.0 . the info is in ATI's driver release notes . I think their priorities a wrong (I think that there would be more desktop installs on K/X/Ubuntu and SuSE than there are on redhat - but that is conjecture as I do not have figures - distrowatch maybe ? ) But now AMD has bought ATI maybe with a little pressure things can be improved . Dont forget - ATI Linux Driver Feedback - contact them - let them know !

---

### Post by pony-tail on 2006-11-02
here's my fglrxinfo output :-
> root@P4C800:/home/ian# fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 XT Generic
OpenGL version string: 2.0.6119 (8.30.3)

But still no useable 3D
composite is disabled

---

### Post by boban on 2006-11-02
> **pony-tail said:**
> here's my fglrxinfo output :-

But still no useable 3D
composite is disabled

Hmm... It looks ok... Could you post your xorg.conf?

---

### Post by narfg on 2006-11-02
Same problem here. I can't even play Xmoto or Frozen-Bubble. The driver seems to work but much slower than in Dapper.

---

### Post by edgardz on 2006-11-05
Sorry this is not very helpful but I have the exact same problem. I installed   fglrx 8.30 on Edgy 64-bits and the performance are very slow ...  Nothing seem broke:

> display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 Pro Generic
OpenGL version string: 2.0.6119 (8.30.3)

> name of display: :0.0
display: :0  screen: 0
direct rendering: Yes



I notice that the Xorg 7.1 enable aiglx by default so I disable it with the following command:

> Section "ServerFlags"
	Option "AIGLX" 	"off"
EndSection

But ... bad news .. nothing change. My device section are the following:

> Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Thanks !

---

### Post by cchiaruttini on 2007-02-01
My problem with a Radeon 9550SE card is much worse.
Everything is fine with BreezyBadger (5.10). With Dapper and Edgy, the graphic session does not start at all. Neither it works with the latest Feisty.

My hardware is: 
Motherboard: ASUS K8V-X SE
Processor: AMD 64 bits

Does anybidy knows a solution?
Regards
Claudio

---

