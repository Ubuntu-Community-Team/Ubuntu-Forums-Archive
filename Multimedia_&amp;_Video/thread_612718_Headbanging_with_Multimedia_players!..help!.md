---
title: "Headbanging with Multimedia players!..help!"
date: 2007-11-14
forum: Multimedia &amp; Video
---

### Post by Radiolad on 2007-11-14
Hi, Radiolad here!
I'm having great fun with 7.10 and enjoying it but .....
I still need to sort out the USPLASH bootup screen as at present this is just a blank/black screen, *but *my **biggest **problem is with trying to play 'video' from websites like the BBC and Channel4.
I've attempted to use:-  MIRO,  VLC,  XINE, Totem Xplayer and REALplayer all to no avail.

They either fail to launch properly or just 'stammer/flicker'.  I also could not find where to *_select _*a default player so I had to delete each one in turn in order to allow a different one to run (and fail). :confused:

I've searched through the forums to find the ideal video/media  player,  but so far no joy  :(

Your help would be much appreciated as my head is begining to hurt !!
Cheers, Radiolad.

---

### Post by bingoUV on 2007-11-14
1. Have you used any other linux distribution / ubuntu version in which video players work fine?

2. Give your hardware configuration (including video card)

3. Do you use compiz ( desktop visual effects ) ?

4. Give the output of the following command
```

glxinfo  | grep direct

```

---

### Post by Radiolad on 2007-11-14
Hi, the output from running the code you gave is as follows:-

direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect

What does this mean ??

My  previous failed attempts for playing 'video'/BBC/Channel4 was with DAPPER.
MY Graphics are: 82810E DC-133 (CGC) Chipset Graphics Controller, but how do I gain acces to the 
hardware configuration (including video card) ??
I ran a search in *Synaptic Package Manager*  to find I have 10 items of 'compiz' loaded.

So..... how are things looking ???   :(

NB (although this may not be connected with the problem). I have also attempted to alter the VISUAL EFFECTS  of APPEARANCE PREFERENCES for the desktop but the system does a self- test and reverts back to 'basic' appearence !!    :confused:

Cheers, Radiolad

---

### Post by bingoUV on 2007-11-15
1. Have you used any other linux distribution / ubuntu version in which video players work fine?

3. Do you use compiz ( desktop visual effects ) ?


Seems like pretty old hardware (of the P-3 era). Correct me if I am wrong. If it is indeed P-3 era hardware, direct rendering is a must to play video properly. Graphics support for this video card should have been builtin for ubuntu.

---

### Post by Radiolad on 2007-11-15
> **bingoUV said:**
> 1. Have you used any other linux distribution / ubuntu version in which video players work fine?

3. Do you use compiz ( desktop visual effects ) ?


Seems like pretty old hardware (of the P-3 era). Correct me if I am wrong. If it is indeed P-3 era hardware, direct rendering is a must to play video properly. Graphics support for this video card should have been builtin for ubuntu.

Hi,
1. I'm running DAPPER on a 400Mhz iMac and have no joy in running video/BBC etc.
2. The PC running 7.10 (the one I am on now) is a Gateway 850 Mhz P3.
3. There are 10 Compiz progs shown as loaded on my Synaptic Package Manager on 7.10
 So far, as per my previous message...no joy !   :(
Any suggestions welcome.
Cheers, Radiolad

---

### Post by exoren22 on 2007-11-15
when you installed vlc did you also install the vlc mozilla plugin? It may sound stupid or even insulting, but I have forgotten this step TWICE and been frustrated for days.

---

### Post by Radiolad on 2007-11-15
> **exoren22 said:**
> when you installed vlc did you also install the vlc mozilla plugin? It may sound stupid or even insulting, but I have forgotten this step TWICE and been frustrated for days.
Hi,   All I can remember was accepting all the associated progs that where given, but it might well be worth me re-instaling VLC and taking  more notice of the additional progs it recommends ie.   VLC moilla plugin.

JUST FOR INFO:  I have just been (for the first time)  looking at Video news items and film trailers within  my ISP Tiscali  without ANY problems !!!!!!!   :confused:      ...I have not installed/removed or tweaked anything apart from the Tiscali Preferences  to run  at 1Meg+ .  They run with minimal 'jitter or stammer, in fact very acceptable.

Anyway, thanks for the Moilla plugin advice ....is this just sitting in Synaptic awaiting to be selected ?

Cheers, Radiolad.

---

### Post by Radiolad on 2007-11-15
> **exoren22 said:**
> when you installed vlc did you also install the vlc mozilla plugin? It may sound stupid or even insulting, but I have forgotten this step TWICE and been frustrated for days.

Hi, A quick update: I've just checked in Synaptic...and **Yes** ....I have got Mozilla- plugin-VLC, also VLC-nox   and VLC .
Cheers, Radiolad.  :confused:

---

