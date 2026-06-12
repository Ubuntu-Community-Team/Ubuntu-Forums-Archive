---
title: "What have I done to my sound?"
date: 2006-09-30
forum: Multimedia &amp; Video
---

### Post by namelessone on 2006-09-30
Recently I installed a bunch of extra gstreamer plugins (bad, ugly, etc.), but then decided that I didn't need them, so I apt-get remove'd them. I turned on my computer this morning, and the little volume control thingy gave me the following message:
> No volume control GStreamer plugins and/or devices found. So I tried following the Comprehensive Sound Problem Solutions Guide. I got through the part where I identify what module I need for my soundcard and I added it to /etc/modules, (on a side note, there are two other modules in /etc/modules that say snd: snd-pcm-oss, and snd-seq. do I need these?) but when I tried to open alsamixer, I got the following error essage. > alsamixer: function snd_ctl_open failed for default: No such device


Why did removing those gstreamer plugins mess up my sound? And, more importantly, how do I fix my sound?

---

### Post by Kateikyoushi on 2006-10-01
It is not the first time I see this happen. I am also curious about it I might try to uninstall them to see what breaks.

Those two modules are for alsa OSS emulation
Did you reboot after adding the module to etc/modules or did you load it with modprobe ?

What is the output of this command ?

> aplay -l

---

### Post by namelessone on 2006-10-01
I initially loaded the module with modprobe.

The output of aplay -l is > **** List of PLAYBACK Hardware Devices ****


---

### Post by Kateikyoushi on 2006-10-02
That's all ?
It should list your soundcards under that line.

---

### Post by namelessone on 2006-10-02
> That's all ?
It should list your soundcards under that line. Yes, I realize that, but it doesn't. That's all it says. It does list my sound card when I use lspci, though. So I know it's there...
```

0000:00:0c.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)

```

---

### Post by Kateikyoushi on 2006-10-02
Do you get sound if you try this ?

```
sudo modprobe snd-cmipci;modprobe snd-pcm-oss;modprobe snd-mixer-oss;modprobe snd-seq-oss
```

---

### Post by namelessone on 2006-10-02
There is still no sound. I clicked on an ogg file and it said > Totem could not startup. Could not establish connection to sound server

---

### Post by namelessone on 2006-10-06
Well, I took things into my own hands and just went and reinstalled ubuntu. Now everything is working.

---

### Post by al_sharpe on 2006-11-27
> **namelessone said:**
> Well, I took things into my own hands and just went and reinstalled ubuntu. Now everything is working.

Rather drastic namelessone;

I am having the same problem.
turned on machine and no multimedia files will open all the apps say 
something like 
[B]Totem could not startup.
Could not open resource for writing.[/B]
I am just trying to watch a movie not copy it!!!
or
[B]Error playing CD.
Reason: Could not open resource for writing.[/B]
Again just trying to listen to a cd, not copy it!!!
I cannot believe there are not more people with this problem.
As yet have not a clue as to what caused, it. everything seems installed
ok - a complete mystery

Al Sharpe

---

### Post by namelessone on 2006-11-27
> Rather drastic namelessone;

I am having the same problem.
turned on machine and no multimedia files will open all the apps say
something like
Totem could not startup.
Could not open resource for writing.
I am just trying to watch a movie not copy it!!!
or
Error playing CD.
Reason: Could not open resource for writing.
Again just trying to listen to a cd, not copy it!!!
I cannot believe there are not more people with this problem.
As yet have not a clue as to what caused, it. everything seems installed

It seems to me that your problem might be a sound daemon problem. Do you have jack running/not running? (Jack can give you a lot of trouble) Is esd running? If it isn't, turn it on (click on "sound " in "preferences") if it is, try turning it off.

I can't guarantee this will work, but it might...

---

### Post by al_sharpe on 2006-11-27
Hello namelessone:

I don't know what was wrong, but I found a solution I am quite 
happy with.
I reinstalled Totem, and that made no difference, changed from gstreamer
to **Xine** and everything works perfectly.
Can even view DVD-RAM which with gStreamer no-way
Probably with Feisty Fawn Ubuntu should switch to Xine.

Al Sharpe

---

### Post by cmichaelboyd on 2006-11-28
Has anyone tried simply re-installing gstreamer?  This should generate new config files for it, and may solve these errors......

---

### Post by obryant on 2007-02-03
I just had the same problem: "Could not open resource for writing" on a fresh Edgy install. Also using a C-Media sound card (coincidence?), but I got the error not through Gstreamer but through the System -> Preferences -> Sound -> Test button. (Same error message when trying to play a Belinda Carlisle CD.)

My problem was fixed by changing "Auto detect" to "C-Media" in the Sound preferences window.

---

