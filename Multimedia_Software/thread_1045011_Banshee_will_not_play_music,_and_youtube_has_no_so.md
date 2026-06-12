---
title: "Banshee will not play music, and youtube has no sound"
date: 2009-01-20
forum: Multimedia Software
---

### Post by kerouacbuff on 2009-01-20
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
	Subsystem: Micro-Star International Co., Ltd. Device 7010
	Flags: bus master, medium devsel, latency 32, IRQ 18
	I/O ports at e400 [size=256]
	I/O ports at e800 [size=128]
	Capabilities: <access denied>
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0

Gstreamer plugins are already installed, so that's not the issue. I don't remember what I did for this to happen. I don't think it's alsa drivers either, so I have no idea. All I know is that whenever I try to play anything in Banshee, it says in the top left that it is idle, and it shows an icon next to the song that looks like an orange x, which I only get that if I the file is not on my computer. Youtube on the other hand, it plays but there is no sound. Any ideas? Please help me out. Thank you.

---

### Post by kerouacbuff on 2009-01-20
bump.

---

### Post by kerouacbuff on 2009-01-20
Will it help if I tell you that my Ubuntu version is 8.10? Really, I have no idea what happened for there to be no sound.

---

### Post by kerouacbuff on 2009-01-20
When I try to test sound in Sound Preferences, this message comes up:

```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Could not open audio device for playback. Device is being used by another application.
```

---

### Post by kerouacbuff on 2009-01-20
Ok, so I tried installing Pulseaudio, but that didn't work. And I uninstalled Pulseaudio, but I really don't think that this is a sound mixing issue, but I am getting upset from the lack of replies on here, and I just want this fixed. I am going to attach a picture of my Banshee application because at this point I am getting existential and uneasy, so please help!
 
[http://img155.imageshack.us/my.php?image=bansheeissuewj0.png](http://img155.imageshack.us/my.php?image=bansheeissuewj0.png)

Like I said before, the music files are on my computer, so that is not the issue.

---

### Post by kerouacbuff on 2009-01-20
bump.

---

### Post by JakeWatkins on 2009-02-21
I'm having the same problem =\

---

### Post by Psychocotic on 2009-03-02
I came here because I was having the same problem, then had to restart because firefox bugged out. 

Problem was solved.

May be a no brainer, or these guys may have had a different problem, but try restarting.

Good luck!

---

### Post by miegiel on 2009-03-02
Some stuff to try if you have no sound :

```
lspci
```
Verify that your soundcard is in the list, if it's not either your PC didn't see it during boot or ubuntu has no drivers installed for it.

If it's a card try sticking it in a different slot on your motherboard and verify if there is a linux driver for your card. [http://www.ubuntuhcl.org/](http://www.ubuntuhcl.org/) is a good place to start i assume :)

If your card is listed by lspci, than go to "System > Preferences > Volume control" to see if your sound might be muted. Under "Edit > Preferences" you can select channels that are hidden by default.

---

### Post by racerraul on 2009-04-02
I've noticed that if I have music playing on Banshee or Rhythmbox and I try to watch a video online, that the video wont play.

I have to stop the music player and then the video loads.

But then when i am done with the video, I have to shutdown Firefox in order for Banshee or Rhythmbox to play any music, otherwise they remain idle.

Its as if both programs want exclusive access to the sound HW.

I'm using OpenGEU 8.10 AMD64.

---

### Post by cnelbuendia on 2009-11-27
Try reseting your GStreamer config to default.
To do so, go to a console a type de following:

```

sudo rm -rf ~/.gconf/system/gstreamer
sudo rm -rf ~/.gstreamer-0.10

```

That worked for me, let me know if it does for you.

Cnelbuendia.

---

