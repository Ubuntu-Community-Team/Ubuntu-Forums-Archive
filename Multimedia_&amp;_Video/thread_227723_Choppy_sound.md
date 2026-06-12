---
title: "Choppy sound"
date: 2006-08-02
forum: Multimedia &amp; Video
---

### Post by Hyuuga on 2006-08-02
I know this is probably a normal problem. I've searched both the net and this forum without any results.
Whenever i play audio files the sound regularely chops, which is really annoying. When i searched the net and followed a few stepped i've concluded that the DMA/UDMA is all in order, but it might be some sort of hardware/filesystem flaw after upgrading kernel. But i've found absolutely NO help what-so-ever that actually works for me.

What must i do to get it to work? reinstall dapper drake?

---

### Post by SeanHodges on 2006-08-02
One thing I can suggest is try inserting the Live CD and playing the example sound file (found in the "Examples" folder on the desktop). If you needed to do anything to get your sound card working on your installed copy of Ubuntu you'll need to do the same for the livecd beforehand.

This will at least tell you if its a screwey installation, or a problem with the configuration of the sound card...

I'm not good with the details of sound in Linux, but I'll help where I can.

Could you also post the output of lsmod, and dmesg? Put them in CODE tags to make them easier to read...

---

### Post by Hyuuga on 2006-08-02
Sorry, i haven't quite memorised terminal commands yet, what commands do i use to find the output of Ismod and dmesg?
also, the only live cd's i have are of the breezy badger. I used the "upgarde" feature in the system updater to upgrade to 6.06
But it wasn't choppy before that, and it wasn't choppy the first time after that either!

i dunno and doubt it will help but my sound card is a "VT8233/A/8235/8237 AC97 Audio Controller" on an Amilo L7300 laptop.

---

### Post by Hyuuga on 2006-08-02
Sorry, i haven't quite memorised terminal commands yet, what commands do i use to find the output of Ismod and dmesg?
also, the only live cd's i have are of the breezy badger. I used the "upgarde" feature in the system updater to upgrade to 6.06
But it wasn't choppy before that, and it wasn't choppy the first time after that either! So i powerfully doubt it's a screwed up installation.

i dunno and doubt it will help but my sound card is a "VT8233/A/8235/8237 AC97 Audio Controller" on an Amilo L7300 laptop.

---

### Post by SeanHodges on 2006-08-03
LSMod will probably be useful to know here, if you open a terminal and type 

```
lsmod
``` (L, not an I)

You should be able to copy and paste the output of the terminal.

A friend of mine had a similar problem with the same VT8233 AC97 audio controller, he suggests you try:

```
sudo nano /etc/modutils/alsa
```

and add the following lines to the end of the file:

```
# ALSA
alias char-major-116 snd
alias snd-card-0 snd-via82xx

# OSS
alias char-major-14 soundcore
alias sound-slot-0 snd-card-0

alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss
```

Save the file, and update the modules:

```
sudo update-modules
```

Then open the ALSA mixer and make sure that the volume is not turned all the way up to 100% (just under should be ok):

```
alsamixer
```

I cant check that against my machine, as I don't have it here. But would be worth a try...

---

