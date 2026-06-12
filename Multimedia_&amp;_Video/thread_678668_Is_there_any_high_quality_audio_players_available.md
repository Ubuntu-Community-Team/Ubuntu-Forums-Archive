---
title: "Is there any high quality audio players available?"
date: 2008-01-26
forum: Multimedia &amp; Video
---

### Post by Transwave on 2008-01-26
Hi, im looking for a high quality mp3 playing software for ubuntu 7. Since im having more expensive speakers, the simple/tiny audio playback programs is not enough (they makes my sound system sound poor).

Any audiophiles out there that have any suggestions of appropriate programs?

Thanks in advance!

---

### Post by xeth_delta on 2008-01-26
> **Transwave said:**
> Hi, im looking for a high quality mp3 playing software for ubuntu 7. Since im having more expensive speakers, the simple/tiny audio playback programs is not enough (they makes my sound system sound poor).

Any audiophiles out there that have any suggestions of appropriate programs?

Thanks in advance!

First of all, welcome to the forums!
There is a great array of good players available in Ubuntu, but I doubt the choice of the player will have any direct influence on the quality of the output sound. It will have more to do with the output codec the program might be using and especially the sound system in the operating system, and how it is configured. Feel free to correct me if I'm wrong.

I could quote a number of programs, such as Amarok(library player), Audacious (Winamp-like), Banshee. You will be able to find audio players in the package data-base/repositories. For example open synaptic and look for multimedia programs.

I am not sure I understand the problems you have. Is the sound of bad quality?

Xeth

---

### Post by bufsabre666 on 2008-01-26
well the audio player really makes little differnce

did you go through and turn on your options: like me i have a 5.1 suround set so you right click on the sound option
open volume control
edit->preferences
and enable surround front center side, etc depending on your setup
and turn them on or up

or if thats not what youre referring to cause your question was kinda vague, it could just mean that your sound card/chipset might not be well supported in linux

---

### Post by patrickfromspain on 2008-01-26
amarok rocks! ;)

---

### Post by legatek on 2008-01-26
Audiophiles don't listen to mp3s, they listen to FLAC. Your high end sound system will sound lousy playing back mp3s regardless of the player.

---

### Post by eye208 on 2008-01-26
> **Transwave said:**
> Hi, im looking for a high quality mp3 playing software for ubuntu 7. Since im having more expensive speakers, the simple/tiny audio playback programs is not enough (they makes my sound system sound poor).

Any audiophiles out there that have any suggestions of appropriate programs?
MP3 decoding is a standardized procedure. If your MP3 files sound ugly, it's because they have been encoded

- from low quality sources
- at low bitrates or
- using the wrong encoder (i.e. something other than LAME).

5.1 output will not make MP3 sound better because there is no such thing as multichannel MP3. 2 channels is max.

---

### Post by Vgercke on 2008-01-26
I use Rhythmbox.:guitar:

---

### Post by Transwave on 2008-01-26
Thx for your replies! I am using winamp when running windows, and that's what i am comparing with. I can clearly hear a difference between winamp and VLC for instance, because winamp has equaliser and probably some cool filters. The winamp is not available for any other OS than windows, that's why i am looking for alternatives. 

I have thought about the possibility that the linux driver isn't as good as in windows. I have the ASUS A7N8X motherboard with Realtek AL650 integrated audio chipset. Bying a new sound card is an alternative, if that will result in better audio in linux.

I have a stereo system (two speakers connected to a amplifier), so the surround features are not relevant.

Isn't Amarok made for KDE environment? When i mark the Amarok for installation in synaptic packet manager, it wants to install a whole bunch of KDE stuff (im running gnome), but perhaps it is not a problem?

---

### Post by ron999 on 2008-01-26
> **Transwave said:**
>  When i mark the Amarok for installation in synaptic packet manager, it wants to install a whole bunch of KDE stuff (im running gnome), but perhaps it is not a problem?

Hi
It's OK to use KDE apps in Gnome. But the first time that you install one it will install some KDE stuff so that they will run properly. It's not a problem.

---

### Post by eye208 on 2008-01-26
> **Transwave said:**
> I can clearly hear a difference between winamp and VLC for instance, because winamp has equaliser and probably some cool filters.
If you use EQs and filters to "improve" music playback, then you are by definition NOT an audiophile. [-X

---

### Post by xeth_delta on 2008-01-26
As I said in a previous post, and since you are a WinAmp user in Windows, you could try audacious. Look for it in the repositories and install the extra plug-ins.

---

### Post by srt4play on 2008-01-26
> **eye208 said:**
> If you use EQs and filters to "improve" music playback, then you are by definition NOT an audiophile. [-X

I'm definitely no audiophile but on my laptop, XMMS w/ equalizer sounds really really good and without equalizer sounds like crap.

---

### Post by Transwave on 2008-02-19
xeth_delta, thx for your tip, thats the kind of mp3 playback software i was seraching for.

Unfortuanally, ive reached to the conclusion that the alsa driver is not quite as good as the audio drivers i use in windows (for my hw). So the quest contunues, I'll try wine or vmware later.

---

### Post by xeth_delta on 2008-02-19
There is a real possibility your drivers are not configured properly. Care to elaborate on what sound card you have?
```
sudo lshw -C sound
```

---

### Post by stefansmith on 2008-04-01
I find Ubuntu sounds better out of the box than Windows XP in my system. Ubuntu Studio with the RT Kernel sounds much better. Vista is better sounding than XP, but not as good as Linux IMHO.

For some serious tweaking, see my sigs...

If you are just listening to MP3's, Linux will be perfectly fine. What hardware are you using?

---

