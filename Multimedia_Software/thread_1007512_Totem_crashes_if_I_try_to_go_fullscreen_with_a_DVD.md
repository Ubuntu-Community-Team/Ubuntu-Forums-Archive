---
title: "Totem crashes if I try to go fullscreen with a DVD?"
date: 2008-12-10
forum: Multimedia Software
---

### Post by Lupusceleri on 2008-12-10
Heya,

I followed some guides from the forums to install the DVD codecs for my 64bit Intrepid Ibex Ubuntu (after adding the repos for medibuntu). It seems to work fine, the DVD loads, yet when I try to go fullscreen Totem just.. shuts down. No error messages, no graying out first, it's just gone.

Any idea what's going on, should I provide you with more information first?

Thanks, Lupus.

---

### Post by tech9 on 2008-12-10
Seeing that I am not a huge Totem fan...

install vlc - it works better for playing DVDs

---

### Post by Lupusceleri on 2008-12-10
Okays, will do. I use VLC on my windows as well didn't know there was a Lin version :)

---

### Post by Rupert_s on 2008-12-11
hello
I have exactly the same problem. When I'm trying to play ANY video on fullscreen player exits (Totem) or hangs up (mPlayer, VLC).

I think the problem is with X server, becouse I noticed the same problem with maximizing games under wine. Also when I change video out from xv to x11 it seems to be quite ok.

Any ideas?
thx


---
CORE 2 QUAD q8200, intrepid ibex, 2gb RAM, gf7600gs ;-((

---

### Post by Lupusceleri on 2008-12-12
Installing VLC and uninstalling Totem seemed to work for me...

So no idea what you can do bud. :\

---

### Post by d156156156 on 2009-02-27
> **Rupert_s said:**
> hello
I have exactly the same problem. When I'm trying to play ANY video on fullscreen player exits (Totem) or hangs up (mPlayer, VLC).

I think the problem is with X server, becouse I noticed the same problem with maximizing games under wine. Also when I change video out from xv to x11 it seems to be quite ok.

Any ideas?
thx


---
CORE 2 QUAD q8200, intrepid ibex, 2gb RAM, gf7600gs ;-((

I too have exactly this problem regardless of player, and as it is one of the last 2 things I _need_ to get done to bring my computer up to doing everything I need, I am dying to find a solution.

---

### Post by derekbuc on 2009-04-22
Same problem here, any player exits on fullscreen. A reboot seems to cure it, but that's just a pain. Any ideas?

---

### Post by derekbuc on 2009-04-22
I turned the visual effects settings in the appearance app down to none, and it seemed to have cured it.

---

### Post by VMC on 2009-04-22
Those of you having this issue need to supply video card info.

```
lspci -nn | grep VGA
```

---

### Post by mengqing on 2009-04-24
I am having this issue as well. Tried everything and still getting the same result.

> **VMC said:**
> Those of you having this issue need to supply video card info.

```
lspci -nn | grep VGA
```

01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV770 [Radeon HD 4850] [1002:9442]

---

### Post by nonvolume on 2009-04-24
same problem here when i try fullscreen vlc,mplayer or totem crash and restart pc.how can i fix this :confused:

---

### Post by levicivita on 2009-04-25
> **derekbuc said:**
> I turned the visual effects settings in the appearance app down to none, and it seemed to have cured it.

I had the same problem.  This did it for me.  My guess is that the jiggly-window mode (whatever it is actually code) interacts negatively with streaming media.  I could be wrong though.

---

### Post by lls666 on 2009-06-04
have the same problem... movies either slow the computer down to a crawl or freeze the whole desktop or log me off when I switch to fullscreen...

VGA info:
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics] [1002:9612]

running Jaunty 64 bit

will try switching the effect to None... had switched it to the middle selection but that didn't help...

edit:
switched the settings to None and the problems vanished...
is there a way to have jaunty switching off the visual effects automatically when Movie Player is running and then restart the visual effects? my ubuntu box isn't my main multimedia box but it is still annoying to know that the box has problems with videos...

---

### Post by TunaCanTommy on 2009-06-04
Similar problem here . . . watching a HULU video on-line, went to full-screen and FireFox (ver 3.0.10) crashed.

[PHP]01:00.0 VGA compatible controller [0300]: nVidia Corporation NV44A [GeForce 6200] [10de:0221] (rev a1)[/PHP]

---

### Post by Sillouette on 2009-06-04
Seems I am not alone. Consider this then a bump to this and my thread as well. I am going through the same issues with video playback (mplayer, Vlc, Movie Player, Totem also). 

Rather than re post my thread, here is a [LINK]("http://ubuntuforums.org/showthread.php?t=1177844")

Ive gotten reads on the thread, but like here, not so much on the help.

Sill

---

### Post by Sillouette on 2009-06-05
Looks like the "geniuses" are going for the low hanging fruit...

sad.

---

### Post by Edgar09 on 2009-06-25
Totem has started to be a great solution & now it all just a big mess.!!

But i found a better & more suitable Player..

It's the VLC media player..

It's way better..

Sorry Totem lovers...

But i got a new love...:popcorn:

---

### Post by klikevil on 2010-08-17
VLC did not fix it for me it crashed on full screen or maximize just like totem, SMPlayer (which is my favorite) could maximize without crashing but the video would stop, what fixed it for me was the turn off the visual effects solution, wobbly windows isn't the cause either i had to load metacity to maximize/full screen, somewhat of a nuisance, but doesn't really require a bug fix in my opinion.

---

### Post by nutsy.ben on 2010-08-22
IT IS NOT A PROBLEM OF THE PLAYER.

People get it wrong here. I tried on many players (Totem, Dragon, VlC). All give the same problem. 

I am using Lucid Lynx and the card:

05:00.0 VGA compatible controller [0300]: nVidia Corporation NV36.1 [GeForce FX 5700 Ultra] [10de:0341] (rev a1)

Any idea is welcome.

---

### Post by nutsy.ben on 2010-08-23
All right;

I did not really fix the problem but found a turn around.
For those who use vlc there is a solution:
 1/ Go in preferences (tools/preferences) or Ctrl+P
 2/ Set your video output to 'X11' 
 3/ Restart VLC (maybe also reboot).

And the full screen option is available again ... :D

Nevertheless, it does not really fix the origin of the problem. 
If someone finds the reason ..... 

Ciao Ubunter !!!

---

### Post by Jetro on 2010-08-29
Just want to sign to this. .avi files crashes on both VLC and Totem when trying to load in fullscreen. nutsy.bens workaround works, though. Thanks :)

Using Ubuntu 10.04. Video card details:  nVidia Corporation G71 [GeForce Go 7900 GS] [10de:0298] (rev a1)

---

