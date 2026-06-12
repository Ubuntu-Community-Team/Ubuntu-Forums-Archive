---
title: "Sound Blaster Audigy SE problems..."
date: 2007-04-27
forum: Multimedia &amp; Video
---

### Post by 3p1ph4ny on 2007-04-27
Hi,

I'm using kubuntu 6.10. I recently purchased this card to drive my 7.1 speaker system.

So, here's my issue:

I was previously using my motherboard's (a Gigabyte GA-K8U-939) onboard sound card. When I got the card, I disabled the onboard sound in the BIOS, and popped in the new card.

I restarted, and tried to install the drivers for the card following loosely [this](https://help.ubuntu.com/community/HowToConfigureSoundBlasterAudigySEinBreezy) guide. Basically, I ran these three commands:

```
sudo apt-get install alsa-source
sudo dpkg-reconfigure alsa-source
sudo module-assistant auto-install alsa-source
```
When I got done, I fired up Amarok to see if all of the speakers were being driven (previously only the right and left speakers were), but no dice.

I decided to restart again, and now I can't see the card any more. For instance $cat /proc/asound/cards says: --no soundcards--

Any thoughts? If you need more info, let me know. Thanks in advance!

---

### Post by raffytaffy on 2007-07-11
i bought the same card and only 2 speakers work. did u ever fix it? and if so how?>

---

### Post by razi3l on 2007-10-12
to fix surround 5.1 with the Audigy SE here is a fix




replace your .asoundrc file (under Home folder, then choose show hidden files) with this script:



################################################## #######
#This is the standard setting (see: "!default")
#This profile, the default loaded, upmixes stereo sound to 5.1.

pcm.!default {
type plug
slave.pcm "surround51"
slave.channels 6
route_policy duplicate
}
################################################## ######
#This is the normal spdif output profile (optical, toslink).

pcm.!spdif {
type plug
slave.pcm "hw:0,1"
}

################################################## #####
#This is what one could call the "factory default setting", in other words, it only plays the actual channels. so if you fx want to watch a 5.1 movie, on the analog output, this is the option you want.


pcm.analog {
type plug
slave analog_slave;
}

pcm_slave.analog_slave {
pcm surround51;
format S32_LE;
}


save it, then log out (ctrl-alt-backspace), log back in and you should be good to go!

---

### Post by felipe1982 on 2007-10-30
Why doesn't ubuntu do this automatically after auto-detecting new hardware?
Why do we have to do these arcane changes to config files?
I don't want to set the sound up for 'just' my user. I want it to be system-wide. Any ideas?

(not mad or bitter --- only curious =)

I'm going to try this when i get home. Fingers crossed!

---

### Post by Joshica on 2007-11-14
That worked perfectly and it was SO easy!! Thank you it's exactly what i wanted! I don't know why it didn't do this, last time I installed it worked perfectly, but this fixed it for me now. Thanks!!:KS:KS:KS

Down with Windows!

---

