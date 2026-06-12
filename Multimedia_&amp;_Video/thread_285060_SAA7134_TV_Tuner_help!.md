---
title: "SAA7134 TV Tuner help!"
date: 2006-10-26
forum: Multimedia &amp; Video
---

### Post by The Warlock on 2006-10-26
So I got a [cheap TV tuner](http://www.sinovideo.com.cn/en/p/1/) so I could play Gamecube games on my laptop. It uses the SAA7134 chipset and a Phillips TDA8275 tuner. It works under dscaler in Windows (an open source program), so I figure there mist be a linux driver somewhere. How do I get it to work? TVTime just shows a black screen. Kaffeine says that it can't find a DVB device.

---

### Post by josesanders on 2006-11-29
Just came across this, so I hope you are still around.  I have a similar cheap ebay card, and here's how I got mine to work:

There are many cards with the saa7134, so in order for Ubuntu to open the card, it needs to know which card number you have.  Decent cards have an eeprom chip that identifies the card number.  My card did not have an eeprom, so when I did:
[PHP]dmesg[/PHP]
I got an error message about how my card couldn't be identified, and it gave me a list of about 100 different options.  Since my card is generic, I couldn't figure out which card I have, so I just used the following:
[PHP]rmmod saa7134-alsa.ko
rmmod saa7134.ko
insmod saa7134.ko card=<card number>
insmod saa7134-alsa.ko[/PHP]
In place of <card number>, I tried each card number individually, then opened TVTime for each one to see if I could see television.  It was very tedious, but I found that several card numbers actually worked for my generic card.  Only one worked for sound output, but I'm still working on the sound issue.
After I found a number that worked, in order to get it to bootup with the right number, I edited /etc/modprobe.d/options with the following
[PHP]options saa7134 card=<card number>[/PHP]

I don't have the numbers with me right now, but on the slim chance that you have the same card, I can post the card numbers that worked for me if you want.  I hope this helps.

---

### Post by The Warlock on 2006-12-01
Just out of curiousity, what card number worked with sound?

---

### Post by josesanders on 2006-12-01
Card number 3 was the only one that worked for sound in TVTime, but none so far have worked for sound in MythTV.  I am still working on it, so when I get it to work totally, I'll be sure to post what I did.  Exactly what card do you have?

---

### Post by The Warlock on 2006-12-02
> **josesanders said:**
> Card number 3 was the only one that worked for sound in TVTime, but none so far have worked for sound in MythTV.  I am still working on it, so when I get it to work totally, I'll be sure to post what I did.  Exactly what card do you have?

I linked to it above. It's a SinoVideo Smart-TV PCMCIA (little laptop card). I got it from eBay for cheap. I don't have sound working, but right now I'm just running my Wii into it, and for that I just run the sound outputs into my sound card's line-in and it works fine. It would be nice to have sound for TV shows, though.

---

### Post by josesanders on 2006-12-04
If you aren't interested in recording sound, you can try this:

$ v4lctl -c /dev/video0 volume mute off

In order to execute the command, you need to have xawtv installed, so if you don't, then do this first:

$ sudo apt-get install xawtv

That works to output whatever sound is coming in through the card.  MythTV doesn't pick it up, so it's useless to me, though, but if you are just playing games or watching TV, it should work.

---

### Post by podfish on 2007-01-19
Didn't work to fix my problem, but if you want an easy way to add and remove the driver for each of the card options, check out this script.  You have to run it as root, or with sudo.

```

#!/bin/bash
CARD_NUMBER="1"
while [ $CARD_NUMBER -lt 100 ]
do
rmmod saa7134_alsa
rmmod saa7134
modprobe saa7134 card=$CARD_NUMBER
echo "CARD NUMBER "$CARD_NUMBER
tvtime
CARD_NUMBER=$[CARD_NUMBER+1]
done

```
Each iteration unloads the saa7134 driver and the alsa driver, restarts the driver with the next number, spawns tvtime, and should continue once tvtime has been closed.  Then it increases the card number by one, and kills/reloads the drivers, etc. etc.  Hope this helps someone--my sound is still borked.  I've got it plugged in to the line-in on my audigy card.

Driver worked perfectly under my previous OS, gentoo, but then, it was hard-coded into my kernel, and didn't try to load the alsa module for it, either.   Now, I can't even figure out which mixer device is supposed to run my line in, because it's different every time ubuntu boots, and it wants to load a driver for my onboard sound, which is disabled in the bios...one of the mo' better, yet occasionally annoying features of linux is the ability to completely ignore the bios.

Anyhow, hope someone else has some ideas here.  I'd like to think it's just a kernel/driver issue, but I'm not sure.  If I can't get it to work, I will go back to a "harder to use" distro.

Steve-O  ](*,)

---

### Post by podfish on 2007-01-19
Check this thread out...  Maybe it will help, fixed me just fine.  Nothing wrong with the driver, just what the mixer settings were.  Bring analog-mix and analog-capture online, and you're good to go.  If you were jacking around with the driver, try a reboot, and you should be in good shape.

[http://ubuntuforums.org/showthread.php?p=2034043#post2034043](http://ubuntuforums.org/showthread.php?p=2034043#post2034043)

---

### Post by cblanquer on 2007-01-19
I could finally enable **SAA7134 sound under tvtime** .
I did not find anything solving it with "alsamixer" so I tried "volume control".

Actually the solution was:
[LIST]
[*]enable analog sound (OSS) in "File">"Change device"
[*]set "line-1" to maximum (or at least higher than zero)
[/LIST]

Be careful and ensure your master volume is loud enough to hear the sound when activated.
See my screenshot - the TV image does not figure out but it is working :D .

=======================
By the way 8-) , if you mess around a little too much with alsamixer or the volume control and **lost any sound under Ubuntu**, a way to restablish the sound that worked for me (after some headaches tring to figure out what happened ](*,)  ) was to :
[LIST]
[*]open alsamixer
[*]disable all devices (volume to zero, then mute)
[*]enable one per one starting by "Master" until you get sound back, do not enable them all systematically !
[/LIST]

---

