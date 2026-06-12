---
title: "Can you play kunm.org sound?"
date: 2008-08-27
forum: Multimedia Software
---

### Post by R_Lopez on 2008-08-27
I have gone through many sets of instructions using different players and codex trying to listen to kunm.org ([http://kunm.org/listen](http://kunm.org/listen)).

The players I have tried all connect to [http://kunm.org/listen/kunm128k.mov](http://kunm.org/listen/kunm128k.mov) and start something (never any sound) and then stop (for example MPlayer will say stopped just below logo).

Can anyone connect to that site and successfully hear it?  Thank you.

Linux rlopez 2.6.24-19-generic #1 SMP Fri Jul 11 23:41:49 UTC 2008 i686 GNU/Linux

Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1

MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) D CPU 2.80GHz (Family: 15, Model: 4, Stepping: 7)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.

---

### Post by malspa on 2008-11-22
Had any luck with this?  Just gave it a quick shot in Debian Etch, MPlayer simply stopped before playing anything.

---

### Post by andrew.46 on 2008-11-22
Hi,

I have not had much luck but strings has revealed the actual address:

```
andrew@skamandros~/Desktop$ strings kunm128k.mov 
 ftypqt   
qt  
Jmoov
lmvhd
trak
\tkhd
$edts
elst
rmdia
 mdhd
5hdlr
mhlrstrmappl
stream media handler
minf
 gmhd
gmin
9hdlr
dhlralisappl
Apple Alias Data Handler
$dinf
dref
alis
stbl
,stsd
rtsp
stts
stsc
stsz
stco
udta
Broadcast by Sorenson Broadcaster
 1.1 (Build 053)
KUNM Stream
2006
KUNM Radio
info@kunm.org ; stream@msdesign.org
!udta
	play
WLOC
free
free
wide
9mdat
wide
mdat**[COLOR="Red"]rtsp://129.24.35.149/kunm128k.sdp[/COLOR]**

```

But I had no luck trying to open this address :confused:.

  Andrew

---

### Post by malspa on 2008-11-22
Is it a Quicktime issue?  Will it work with Windows or Mac?

---

### Post by malspa on 2008-11-22
With MPlayer, plugging in the actual address, I get:

Unnamed
Totem could not play 'rtsp://129.24.35.149/kunm128k.sdp'
There is no input plugin to handle the location of this movie

---

### Post by R_Lopez on 2008-11-25
Thank you everyone who tried to see if you could connect to KUNM. It has been streaming for many years. The people there have no idea how their system works. There were a few persons from an engineering school who talked them into streaming and helped them set it up. They have moved on. So the system as it is just has not been touched. It works on XP Home and Pro for IE, Firefox, and Opera with the correct Quicktime 4 or 5 plugins.

---

### Post by malspa on 2008-11-29
A friend of mine had no problems listening in on his Mac.  My email to the station about getting a stream that will work in Linux has gone unanswered.

---

### Post by R_Lopez on 2008-12-01
Is the fact it works on a MAC just further confirmation that KUNM streams successfully or is it to establish that there is some software that runs on both MAC and Ubuntu that is able to work on MAC?

---

### Post by binbash on 2008-12-01
No sound here  under firefox 3.1b , mozilla vlc plugin

---

### Post by malspa on 2008-12-02
> **R_Lopez said:**
> Is the fact it works on a MAC just further confirmation that KUNM streams successfully or is it to establish that there is some software that runs on both MAC and Ubuntu that is able to work on MAC?

I guess it was just confirmation (for me) that it streams successfully.  At the time, I wasn't sure, so I asked a friend to check it out.

---

### Post by MonkeeSage on 2008-12-02
> **andrew.46 said:**
> Hi,

I have not had much luck but strings has revealed the actual address:

```
andrew@skamandros~/Desktop$ strings kunm128k.mov 
 ftypqt   
qt  
Jmoov
lmvhd
trak
\tkhd
$edts
elst
rmdia
 mdhd
5hdlr
mhlrstrmappl
stream media handler
minf
 gmhd
gmin
9hdlr
dhlralisappl
Apple Alias Data Handler
$dinf
dref
alis
stbl
,stsd
rtsp
stts
stsc
stsz
stco
udta
Broadcast by Sorenson Broadcaster
 1.1 (Build 053)
KUNM Stream
2006
KUNM Radio
info@kunm.org ; stream@msdesign.org
!udta
	play
WLOC
free
free
wide
9mdat
wide
mdat**[COLOR="Red"]rtsp://129.24.35.149/kunm128k.sdp[/COLOR]**

```

But I had no luck trying to open this address :confused:.

  Andrew

Same here. MPlayer just times out (actually, seems to wait for infinity):

```

[Tue 07:26 AM] ~ $ mplayer rtsp://129.24.35.149/kunm128k.sdp
...
Playing rtsp://129.24.35.149/kunm128k.sdp.
Connecting to server 129.24.35.149[129.24.35.149]: 554...
// waiting forever
...

```

---

### Post by R_Lopez on 2008-12-02
Thank you for your time and effort.

---

