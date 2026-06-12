---
title: "Hardy... No Audio in Games (e.g. OpenArena)"
date: 2008-04-26
forum: Multimedia Software
---

### Post by T_W on 2008-04-26
I just installed a bunch of games under hardy (via "Add/Remove Programs...").

I don't seem to get any sound in any games.

I have tried Supertuxkart, Frozen-Bubble, OpenArena, SuperTux2, Planet Penguin Racer.

Ryhtymbox and system sounds work fine.

Any ideas?

---

### Post by T_W on 2008-04-26
Some progress....

For OpenAL games, the solution seems to be documented here:

[URL="http://wiki.archlinux.org/index.php/PulseAudio#Configuration_of_OpenAL_for_PulseAudio"]
http://wiki.archlinux.org/index.php/PulseAudio#Configuration_of_OpenAL_for_PulseAudio[/URL]

Games that uses OpenAL can use PulseAudio directly writing this line in ~/.openalrc:

```
(define devices '(esd))
```


For some games, I am still seeing the error:

```
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave

```

Seems like ALSA-based games are still a problem.

---

### Post by thePowerworks on 2008-05-23
First time poster, I read here often however and actually had this same problem.

I had the same problem and just by luck I fixed it.

I installed OpenArena through the package manager and realized it was outdated. I went into sound properties and set from high to low, and magically sound started working. Going back to high crashed the program. I was just about to uninstall and install the newer version when I decided to run it through terminal (not really sure why).

I simply opened up a terminal and typed openarena.

Loaded with sound. I was amazed, I ran it again and it worked.

I ran it through the applications menu, no sound.

So I figured it must be the flags attached to the shortcut in the applications menu.

I copied the shortcut to the desktop and double clicked it.

Loaded with sound.

Tried it again with applications menu, no sound.

THIS IS DRIVING ME INSANE! What could possibly be the difference?

---

### Post by genepool on 2008-06-22
[BUMP] 
Having the same problem with the Applications menu and games.  No audio when launched from the menu, normal audio when launched from the terminal.  Checked the shortcut command and they are the same.  No problem with any other software, just 3d games (alien-arena, scorched3d, openarena...)  No useful log entries or errors.  WHY????

UbuntuStudio 8.04 64-bit

---

### Post by Mr.Pickels on 2008-10-25
I have this same trouble

Ubuntu Hardy AMD64
USB Logitech z-10 audio

I have tried a few variations of the .openalrc fix, but it makes no difference

Edit:
Running lbreakout2 from terminal returns:
LBreakout2 2.5.2
Copyright 2001-2005 Michael Speck
Published under GNU GPL
---
Looking up data in: /usr/share/games/lbreakout2
Looking up custom levels in: /home/###/.lgames/lbreakout2-levels
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM default
No available audio device

---

### Post by wolterh on 2009-12-17
I think you have to install the SDL library compiled with ALSA. It worked for me. Its called [libsdl1.2debian-alsa].

---

### Post by grajea on 2010-01-24
Working for me on Karmic after this ...

sudo aptitude install libsdl1.2debian-pulseaudio

---

### Post by bloozguy on 2010-09-25
I had this problem with 10.4 LTS.

I turned the OpenAL option [FONT="Arial Black"]Off[/FONT] in the SOUND menu whereupon there was .... SOUND!

---

