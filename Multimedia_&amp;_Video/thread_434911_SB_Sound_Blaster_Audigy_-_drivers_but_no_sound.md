---
title: "SB Sound Blaster Audigy - drivers but no sound"
date: 2007-05-06
forum: Multimedia &amp; Video
---

### Post by lebe0024 on 2007-05-06
I'm new to ubuntu and linux in general.  I can't get sound to come out of my speakers, but it seems thedevice shows when I go to the system -> preferences -> sound -> Device:

I have:
Sound playback : Autodetect.
Music and Movies: Autodetect
Audio Conferencing: Autodetect.
Capture: ALSA
Device: Audigy 1

When I click on any of the "Test" buttons, the progress bar only gets two bar segments and it stops.

Any help would be appreciated.

---

### Post by nuser101 on 2007-05-06
On the upper right of the feisty desktop, you should see a speaker icon. Right click on it, and select "Open Volume Control" from the drop down menu that appears. The alsa mixer will appear. Select the "Switches" tab. It defaults to digital output, and you probably don't want that. Deselect it.

At this point, you should have stereo sound through two speakers. Now click on the "Playback" tab. You may have to deselect the "mute" button for the playback channel you want. Now close the volume control panel.

If you have more than two speakers, right click on the taskbar speaker icon as before, but this time, select "preferences". A scroll down menu will appear, scroll down it until you see the "surround" option. Select it, and close the control panel. For some reason, your sound volume level  will reset to zero after doing this. Select the same speaker icon, but this time with a left click, and you will see a volume slider. Slide it to the default setting of 80%. 

Nearly every feature of my audixgy platinum ex (admittedly an old card) works after implementing these changes.

---

### Post by masonfoley on 2007-05-06
I have an Audigy 2 ZS (PCI) card.  I'd like to build a MythTV server using Ubuntu 7.04 Feisty but I'm hoping to get confirmation that this specific card is supported.

---

### Post by coho1202 on 2007-05-06
I have an Audigy 4 card and was having intermittent sound issues until I checked my bios. I still had the on board audio enabled. After I disabled it I havent had any more issues.

---

### Post by lebe0024 on 2007-05-08
Thanks!  That worked.  If I were ubuntu, I would make two changes here:

1) I would not enable digital audio by default.  I would think the vast majority of users use analog speakers.  The windows driver also does not enable digital by default.

2) I would provide this switch in the system->preferences->sound panel.

Is there a place to make suggestions?

---

### Post by anachreon_ on 2007-05-08
masonfoley, do you mean PCMCIA for a notebook?  IF so, I can tell you that it works fine, I use it on my Dell Inspiron Laptop.  However, you have to tell ubuntu to use the PCMCIA card instead of your onboard card, which can be a little tricky, at least using KDE.  The only way I found to do this reliably is to create a file called "sound" in /etc/modprobe.d/, with the following two lines in it 

```

options snd-emu10k1 index=0
options snd-intel8x0 index=1
```

where the index=0 card is the card you want to load first, and the index=1 card is your onboard sound - for me, the intel8x0

---

### Post by chewjoel on 2007-05-11
I have the same problem, and when I right click on that speaker icon on the top right corner, there's an error message: No volume control GStream Plugins and / or devices found.

What should I do with this?

Thanks.

---

### Post by peebly on 2007-05-11
> **masonfoley said:**
> I have an Audigy 2 ZS (PCI) card.  I'd like to build a MythTV server using Ubuntu 7.04 Feisty but I'm hoping to get confirmation that this specific card is supported.

I have this sound card, has always worked with ubuntu.

---

### Post by xbubbax on 2007-05-14
i just hads this same issue but my audigy would work sometimes, then after a reboot it would not work. went into the bios and shut off the onboard sound and now it is coming up all the time. no issues thanks guys.

---

### Post by masonfoley on 2007-05-21
> **anachreon_ said:**
> masonfoley, do you mean PCMCIA for a notebook?  IF so, I can tell you that it works fine, I use it on my Dell Inspiron Laptop.  However, you have to tell ubuntu to use the PCMCIA card instead of your onboard card, which can be a little tricky, at least using KDE.  The only way I found to do this reliably is to create a file called "sound" in /etc/modprobe.d/, with the following two lines in it 

```

options snd-emu10k1 index=0
options snd-intel8x0 index=1
```

where the index=0 card is the card you want to load first, and the index=1 card is your onboard sound - for me, the intel8x0

Anachreon, thanks for the reply.  I should have been more specific.  I actually have the Audigy 2 ZS Gamer PCI card (not PCMCIA).  I think the Gamer part of the name simply means they bundled some games (retail package) with the Audigy 2 ZS based card.  I was thinking of upgrading the sound card in my Windows box and transfer the Audigy 2 ZS over the box that I'm converting from XP Pro to 7.04 Feisty (permanently I'm hoping).  It would be nice to hear if someone was successful with this card.  ***EDIT:  I just saw Peebly's reply.  Thanks for that.***

I have disabled the onboard multimedia controller in that box but I've made a note of the modprobe.d config you cited above as that would help to ensure that the boot up is loading the card I intend for it to.

Thanks again.

Cheers

---

### Post by vs292 on 2007-05-22
> **anachreon_ said:**
> masonfoley, do you mean PCMCIA for a notebook?  IF so, I can tell you that it works fine, I use it on my Dell Inspiron Laptop.  However, you have to tell ubuntu to use the PCMCIA card instead of your onboard card, which can be a little tricky, at least using KDE.  The only way I found to do this reliably is to create a file called "sound" in /etc/modprobe.d/, with the following two lines in it 

```

options snd-emu10k1 index=0
options snd-intel8x0 index=1
```

where the index=0 card is the card you want to load first, and the index=1 card is your onboard sound - for me, the intel8x0

Hey there,

Did you have to do anything else? I'm about to install that card on Kubuntu from scratch in the next day or so (my previous attempts have failed and I don't quite understand ALSA...!) Any help will be much appreciated!:D

---

### Post by da Wookiee on 2008-03-20
Trying this now seeing if it works.

---

### Post by da Wookiee on 2008-03-20
Disabled card in bios, and everything worked like a charm.  I should have tried that earlier.

---

