---
title: "How I solved my sound problems in Gutsy"
date: 2007-11-03
forum: Multimedia &amp; Video
---

### Post by patis on 2007-11-03
Hello,

After upgrading to Gutsy I found my system with no sound. After some trials I got Rythmbox to work but no sound out of Firefox or the Epiphany browser. I finally got everything to work and I want to share how I did it in the hope that it will help someone else (there's been many posts about sound problems in Gutsy, mine included!).

I tracked down the source of the problem to the kernel in Gutsy loading up the sound drivers in a different order and therefore messing up the configurations I had in Feisty. A drastic solution is to disable the unwanted sound cards (or chipsets) in the BIOS to leave only the one you really want and hope for the alsa configuration files to be pointing to the right card.

I took a soft approach and here's is how I solved my sound problems:

1. Remove any [FONT="Lucida Console"].asound*[/FONT] files you may have in your home directory

```
~$ rm .asound*
```

2. Find which sound cards are detected and active:

```
~$ cat /proc/asound/cards
 1 [default        ]: USB-Audio - PnP Audio Device        
                      PnP Audio Device         at usb-0000:00:13.2-2, full speed
 2 [UART           ]: MPU-401 UART - MPU-401 UART
                      MPU-401 UART at 0x330, irq 5

```

The numbers above in the first column, 1 and 2, are the card numbers.

3. Test that your cards are configurable by ALSA

```
~$ amixer -c1
``` or ```
~$ amixer -c2
```

The output of these commands should be the setting of the different devices in the cards (PCM levels, etc.).

4. Make your preferred card the default card for you system.
[LIST] Global Settings, for all users: I found that the easiest way to set up the default alsa card for all your users is by editing [FONT="Lucida Console"]/etc/environment[/FONT] and adding the line ```
ALSA_PCM_CARD=1
``` (replace 1 with the card number you want). 
[/LIST]
[LIST] Do it only for your personal account in the system: The easiest way is probably using the following commad, ```
asoundconf set-default-card default
``` (Note: "default" in the above line is the name of the card in my system, it is kind of weird since it was not my default card! Yours will likely be different.) This will recreate the .asound* files that you removed in step 1.
[/LIST]

5. Finally, visit the sound preferences menu (System-->Preferences-->Sound) and ensure that your selection reads "autodetect" or "ALSA" everywhere.

The next time you or any of your users login sound should be fine.

I hope this helps.

---

### Post by mrvertigo on 2007-11-03
thanks, I had a similar problem!

---

### Post by strawberryzen on 2007-11-18
This is brilliant! Fixed sound in mplayer and firefox for me. Thanks a bunch!

Anyone trying this out ought be aware that the numbers from the cat command don't always start from 1, in my case they started at 0. Make sure you check before setting that value.

---

### Post by kag on 2007-11-20
Thank you so much. I must have reset my CMOS a while ago because my onboard sound card was enabled. Disabling it corrected my problem immediately.

---

### Post by RSVampire on 2007-11-26
the only problem I've had with this method so far is my soundcard(s) seem to swap between slots 0 and 1 depending on the IRQ levels.

any suggestions?

---

### Post by SuperTim on 2007-11-27
Oh, damn. I've been trying to figure this out for days. Embedded flash audio works like a charm, now! Thank you so much!

---

### Post by A + on 2007-11-27
Thanks I'm not an absolute beginner but not far off and this seems to have done what tons of other angles haven't.  My card started at 0 too.

One issue I'm left with is a high-pitched sound while the CD is playing...I'm messing with the sound settings under System>preferences>sound>devices now to see if there is a combination that will get rid of it.  Anyone know, please let me know.

J

---

### Post by arrizaba on 2007-11-27
Thanks!!

This solved my video/audio problems!

Now I am able to play videos. Before the players were freezing because of the sound. Now they are OK.

---

### Post by dustman on 2007-11-27
Hi!

I tried this but with no effect. I still haven't got any sound :(

---

### Post by RSVampire on 2007-11-27
so how do I choose an audio device from it's name or it's driver from startup?

because I can get sound now whenever it randomly turns off, but it's randomly turning off because the default slot keeps changing back and forth between the integrated audio and the sound blaster card based on the IRQ.

So if I tell it to default to slot 0 in 2 days my sound card will move to slot 1 then I have to re-edit the file and restart the computer... I'd rather tell it "default soundcard.driver.xxx" rather than "default IRQ slot x" so it can dynamically change when the system changes.

can anybody help me with that?

---

### Post by krelverehan on 2007-11-27
Wow, thanks... So easy... I had sound only in Totem and Rhythmbox... nothing else (firefox, vlc, etc...). Now it all works, all thanks to :KS**patis***!!!*:KS

---

### Post by CodeDragon on 2007-11-27
This worked like a charm for me.  Thank you very much patis.

---

### Post by rog22 on 2007-11-27
sweet! fixed my flash and dvd sound issues

---

### Post by RSVampire on 2007-11-29
nevermind, I think I fixed my problem with this post...

[http://ubuntuforums.org/showthread.php?t=546793&highlight=sound](http://ubuntuforums.org/showthread.php?t=546793&highlight=sound)

---

