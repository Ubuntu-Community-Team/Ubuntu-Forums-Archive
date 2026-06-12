---
title: "No Sound In Braid Game"
date: 2010-12-15
forum: Multimedia Software
---

### Post by amtur_poet on 2010-12-15
I just downloaded the game Braid for Linux as part of the Humble Indie Bundle #2, but the main two problems I have with it are that it lags noticeably on my fairly new computer [HP Pavillion dv7], and there is no sound at all. I have the speakers turned up to maximum volume, but I still don't hear anything. I am running Ubuntu 10.10 64-bit.

---

### Post by The Fold on 2010-12-15
I'm getting sound, but it's really messed up...it's the same for all of the games.


Other apps that use sound though (YouTube, Spotify) are working fine.

---

### Post by Rob-e on 2010-12-17
I have the same problem which really sucks since the music in this game rocks and this game was the reason I got the bundle.

---

### Post by Takkak on 2010-12-19
My sound is only not working in Braid. You can faintly hear the soundtrack, but there's a heavy kind of static, burning, or something noise that completely drowns it out.

Kinda sucks because Braid seems the most interesting. I guess I'll just play Revenge of the Titans until I find a fix.

---

### Post by dorathy on 2010-12-20
> **Takkak said:**
> My sound is only not working in Braid. You can faintly hear the soundtrack, but there's a heavy kind of static, burning, or something noise that completely drowns it out.

Kinda sucks because Braid seems the most interesting. I guess I'll just play Revenge of the Titans until I find a fix.

thank you.

---

### Post by Takkak on 2010-12-20
Never mind about that. It's probably just noise - even if I turn the sound settings to mute, the static sound just continues.

---

### Post by carlsonmark on 2010-12-21
I had the same problem using 32-bit Ubuntu 10.10.  I did an strace and noticed that the game was looking in the wrong locations for the sound libraries (it was looking in the current working directory instead of in /usr/lib, for example.)

I think the sound started working after I ran the game like this:

```
# LD_PRELOAD=/usr/lib/libpulse-simple.so.0:/usr/lib/libpulse.so.0:/usr/lib/libpulsecommon-0.9.21.so ./braid
```I'm not sure if all of those libraries were necessary, since it turned out my sound was muted during some of my first attempts at using LD_PRELOAD.

If that doesn't work, you can try setting LD_LIBRARY_PATH so that it points to the path that contains your sound libraries.  (This is when I noticed I had turned mute on at some point... whoops!)

```
# LD_LIBRARY_PATH=/usr/lib ./braid
```Oddly, I did not need to do a LD_PRELOAD or set the LD_LIBRARY_PATH on subsequent runs... just once.

Also, I noticed that my laptop sound buttons did not work in Braid, so if I started Braid with sound muted, I could not unmute it using the buttons on the laptop.

---

### Post by o-bin-lad3n on 2010-12-22
Sadly, the preload-trick did not work for me, still a lot of static/cracking noises. I'm on 10.04 64-Bit btw.

This really kills the experience... :(

---

### Post by carlsonmark on 2010-12-22
> **o-bin-lad3n said:**
> Sadly, the preload-trick did not work for me, still a lot of static/cracking noises. I'm on 10.04 64-Bit btw.

This really kills the experience... :(

You could do an strace and attach the results.  Also, I've never used 64-bit Linux, so I'm not sure if the libraries are in the same place (/usr/lib)

```
# strace ./braid 2> braid.strace
```Then exit braid as quickly as possible.  Make sure there is text in the braid.strace file.  It should start out with something like "execve(".  Attach the braid.strace file to the thread and I can see if there are any other library problems.

---

### Post by o-bin-lad3n on 2010-12-22
Ubuntu has its 64-bit libraries in /usr/lib, /usr/lib64 symlinks to that, and the 32-bit libraries in /usr/lib32.

Seems Braid looks for the libraries in the current directory by default and falls back to /usr/lib.

Btw, I found out that the noise gets a lot better, if I move the libraries Braid ships out of the way, so it has to use the system's... Still cracks every 3-5 seconds, but before it had multiple cracks per second.

Attached strace is with Braids own libraries. Thanks!

---

### Post by carlsonmark on 2010-12-23
Hmm... I didn't see anything out of the ordinary in the strace.

Have you seen this thread, or one of the others like it?

[http://ubuntuforums.org/showthread.php?t=987252](http://ubuntuforums.org/showthread.php?t=987252)

---

### Post by o-bin-lad3n on 2010-12-25
All other audio is working absolutely fine, but thanks ;)

It's actually quite playable with braids own libs removed (Except libCg* of course).

I disabled compiz to make the game run a little smoother and I think that also reduced the cracking noise further. So it also depends on cpu-load...

---

### Post by lidex on 2010-12-25
This may help. No sound or stuttering sound in SDL-based games.

Many games use the SDL library, however, by default, only the ALSA version of SDL is installed. Some games are known to work better if you instead use the PulseAudio version of SDL. This is due to a bug in alsa-plugins.

Diagnosis

Open synaptic and select the package which contains the game. Right-click on the package and select Properties. Go to the tab "dependencies" and select "dependencies" in the combobox. If "libsdl1.2debian" is listed as a dependency, then the game is affected.

Fix / workaround

Install the package libsdl1.2debian-pulseaudio, then restart your game.

---

### Post by o-bin-lad3n on 2010-12-30
Thanks for the suggestion, but 10.04 has the -pulseaudio version installed by default and the alsa version is not.

---

### Post by Emblem Parade on 2011-06-11
Hey, anybody found a solution to this?

I am also on Natty 64bit, and not getting any sound.

---

### Post by antenna on 2011-06-18
Also 11.04 64 bit and no sound.  Framerate issue as well.  Any help appreciated. :(

---

### Post by Emblem Parade on 2011-06-24
I ended up finding the problem on my particular setup. I have sound! Gorgeous sound, too, and am enjoying this really innovative game.

(I'm on 64bit Natty, thought I don't think that matters.)

The issue is that I have on-board audio and also a separate audio card, which each appears as a separate hardware output in Ubuntu's audio settings. (Which are PulseAudio.) The Braid game uses SDL's audio library, which plugs in to PulseAudio. But, somehow SDL's PulseAudio support is special and does not think to use the system defaults. So, even though I have everything else working find with my external audio card, somehow Braid (and only Braid) defaulted to using my internal audio card.

Fixing this wasn't trivial, because Braid is a full-screen game, and so I had no easy access to the audio setting while it was running. But, somehow through a lot screwing around and alt-tabbing I managed to switch to the desktop while Braid continued running in the background, and that's where I could get to audio settings and change the audio output for Braid. Phew!

I blame mostly SDL for this, though I think it would be nice if Braid also had a windowed mode.

Off topic -- you can buy the gorgeous soundtrack for the game off Magnatune:

[http://magnatune.com/artists/albums/braid-soundtrack/](http://magnatune.com/artists/albums/braid-soundtrack/)

---

### Post by Thekla on 2011-06-24
Ryan Gordon ported the game. He posted a list of commandline switches [on his mailing list]("http://icculus.org/pipermail/braid/2010-December/000016.html").

From the man himself: "If you get bad sound, try export SDL_AUDIODRIVER=alsa, and that'll probably solve 90% of the problem cases (but if it's working now and you try this, it may stop working)."

---

### Post by Spydax on 2011-08-14
> export SDL_AUDIODRIVER=alsa
Ran this as a standalone command - still no sound

> Open synaptic and select the package which contains the game. Right-click on the package and select Properties. Go to the tab "dependencies" and select "dependencies" in the combobox. If "libsdl1.2debian" is listed as a dependency, then the game is affected.

Fix / workaround

Install the package libsdl1.2debian-pulseaudio, then restart your game.

I have BOTH packages installed - libsdl1.2debian & libsdl1.2debian-pulseaudio
However libsdl1.2debian is listed as the dependancy in braid, how do I change that?

---

### Post by CaptainPasty on 2011-08-28
Emblem Parade - Any chance you could provide a brief summary of how you did this as it sounds suspiciously like my problem? I'm using Natty and have a second (none-default) soundcard too. Again, no sound. 

Also, how did you manage to Alt-Tab out of Braid as for the life of me I can't get out of it...

Thanks in advance

---

### Post by nimbrant on 2011-08-31
> Also, how did you manage to Alt-Tab out of Braid as for the life of me I can't get out of it...

Braid can be run in a window using the -windowed flag
```
braid -windowed
```

I'm using 64-bit Natty and was getting audio static. I renamed the file libSDL-1.2.so.0 in braid directory so it would use the system one and that seemed to work for me.

---

### Post by CaptainPasty on 2011-09-01
Actually I've sorted it. There might be a much quicker way to do this, but here goes:

I started PulseAudio Volume Control (you might need to install this) and then in the terminal I went to /opt/braid and started the game in windowed mode ( ./braid -windowed) so that I could switch between the game and PulseAaudio Volume Control. 

Next, while the game was running I switched to PVC, went to the Playback tab and turned up the volume on "Braid: Simple DirectMedia Layer". Job done.

Oh and for what it's worth, the sound and music really is nice...  :)

---

