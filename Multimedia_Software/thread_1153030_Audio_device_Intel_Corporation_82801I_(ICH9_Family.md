---
title: "Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller sound issue"
date: 2009-05-08
forum: Multimedia Software
---

### Post by nakshathram on 2009-05-08
Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller

is my audio device on a HP pavilion dv4-1120us laptop.

Sound is stuttering very badly, I'm unable to listen to any audio or play any video either in Ubuntu jaunty 9.04
Can someone help?

---

### Post by Hilko on 2009-05-08
Me too. I have the same audio device, Ubuntu 9.04 64bit. After upgrading, sound was choppy and rhythmbox would crash all the time. Today i lost all my sound completely ! I cannot even make a test sound.

I already tried all the different settings in system-> preferences->sound

I really really need help with this.

---

### Post by Yankee_Fan on 2009-05-08
> **nakshathram said:**
> Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller

is my audio device on a HP pavilion dv4-1120us laptop.

Sound is stuttering very badly, I'm unable to listen to any audio or play any video either in Ubuntu jaunty 9.04
Can someone help?

Open a terminal and edit /etc/modprobe.d/alsa-base.conf using nano:

```
sudo nano /etc/modprobe.d/alsa-base.conf
```

and add the following two lines at the end of the file:

```
options snd-hda-intel model=hp-dv5
options snd-hda-intel enable_msi=1
```

---

### Post by Hilko on 2009-05-08
It works again, I don't know how or why. I logged out, suspended, logged back in and now my sound works again.

However now i have a new problem.
The keyboard shortcuts to raise and lower volume don't work anymore. These are the two keyboard shortcuts I use the most.

Whenever I click on the keyboard button to increase or decrease volume, a notification pops up on the top left and i see the bar change lenght. But the sound volume stays exactly the same.
I've tried setting different shortcuts for volume, but that doesn't help. Exactly the same thing happens: the notification area shows a bar changing length, but the sound output level does not change.

The only way i can change the volume now is to left click on the panel and drag the slide using the mouse. That still works, but i don't like using the mouse for that.

Please please help me !

---

### Post by keryil on 2009-06-22
> **Hilko said:**
> 
However now i have a new problem.
The keyboard shortcuts to raise and lower volume don't work anymore. These are the two keyboard shortcuts I use the most.


It might be that the device controlled by the keyboard is not the device/track you use for output. Can you control the volume through volume manager? 

You may want to right click on the volume manager icon in the notification area, click on preferences and try one of the other devices/tracks there. Trying this out separately for speakers and any earphone outputs you might have is also a good idea; some of those command only the earphone volume or only the speaker volume. 

As per the original question, nice neat solution, I must comment.

---

### Post by Th3_uN1Qu3 on 2009-06-22
I have a similar laptop and have gotten sound to work properly by doing this:

```
sudo apt-get remove pulseaudio
sudo apt-get remove alsa
sudo apt-get install alsa

```

Now reboot. Go into System -> Preferences -> Sound and set everything to ALSA. Under Default Mixer Tracks pick your analog soundcard (not digital, not HDMI), mine looks like this: HDA ATI SB (Alsa Mixer). In the box below it select PCM. Click close, now go into the volume control and unmute any sliders that have become muted after reinstalling ALSA. Now your sound should work perfectly and you will also be able to control it with the laptop's media keys.

---

### Post by raboofje on 2009-06-22
I had some (other) issues with this card, and [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) helped greatly.

---

