---
title: "SB Audigy &amp; Nvidia Chipset"
date: 2006-06-15
forum: Multimedia &amp; Video
---

### Post by foneroot on 2006-06-15
I just installed ubuntu for the first time and it's detecting my on-board nvidia chipset sound over my SB Audigy card. How can I enable this card/update drivers for it? Thanks all.

---

### Post by Sutekh on 2006-06-15
Does it detect your SB card?  Use this command to list your soundcards.  You should see both.
```
cat /proc/asound/cards
``` Can you also check that the proper sound modules are loaded?  Find your SB card from the [ALSA Soundcard Matrix]("http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Creative_Labs#matrix") and look for the command in the instructions; **modprobe snd_**xxxx.  For an Audigy it quite likely to be the **snd_emu10k1** module.

Check that those modules are apparent in the output from this command
```
lsmod | grep snd
``` 

Then you can try one of several things to use the SB card over your onboard card.

 - First, you could disable the onboard sound in your BIOS. I wouldn't do this; you never know when a second sound card could come in handy.

 - Secondly, if you use GNOME, go to the Sound preferences in the System -> Preferences menu, and change the default sound card.

 - Or thirdly you can create a sound configuration ile that should let you use the SB card in applications over the onboard card. This command will open an editor.
```
gedit ~/.asoundrc
``` Then paste in
```
 pcm.[B]<card_name>
[/B]{
     type hw
     card **<card_number>**
}

ctl.**<card_name>** 
{
     type hw
     card **<card_number>**
} 
``` Where <card_name> can be replaced by a short decriptive name for the SB card, and <card_number> must be replaced with the corresponding number for the SB card, which you get from the very first command I gave you.

Then you should be able to choose to use the SB card in your applications, via the preferences that can be set in those applicaions.

---

### Post by foneroot on 2006-06-15
got it working - thank you! :)

---

### Post by Sutekh on 2006-06-15
Great! Glad to help out :)

---

### Post by foneroot on 2006-06-15
Things seem to be working but my sound quality isn't pretty bad... would an update fix this or something?

---

### Post by Sutekh on 2006-06-15
What's the problem?  Sound is a bit distorted?  I get this with my SB card.  

Try reducing the volume level to below 70% using the alsamixer
```
alsamixer
```
Use the arrow keys to change channels and volume.

---

### Post by foneroot on 2006-06-15
It sounds better in Windows for some reason... it doesn't sound very "clear" I guess. It's almost sounds a bit muffled together. Almost like the "OMMF" isn't there.

---

### Post by foneroot on 2006-06-16
Ha.. you know what. I was using Banshee to play music and I switched to Rhythmbox and my music sounds a LOT better! :D

---

