---
title: "Speaker stopped working during a video playback. Headphones are ok."
date: 2015-06-18
forum: Multimedia Software
---

### Post by MajinSaha on 2015-06-18
Hi!
I have Dell Latitude e6440 with Ubuntu on it, 12.05 LTS. I cannot complain about it, it's been great so far.
However, when watching a video on VLC player, the sound just disappeared in a middle of playback,with no action on my part. This is far from the first time I watch a video on VLC on my Ubuntu, so this event was a total surprise. Since then, there has been no sound coming from my speakers at all. Headphones reproduce the sound as usual though.
After googling, I tried 
```
sudo nano /etc/modprobe.d/alsa-base.conf
```
and added a new line in the end of the file
```
options snd-hda-intel model=auto
```
as well as an alternative
```
options snd-hda-intel model=generic
```
Then rebooted. Nothing changed.
I also installed the latest updates for my OS, but also in vain.

The only suspicious thing that happened earlier that day was that my Skype stopped responding after 1 hr long conversation, and I had to kill the Skype process with key -9 in the command line in order to be able to restart it.

Can anybody please help me resolve this strange problem?
Thanks.

---

### Post by kostkon on 2015-06-18
You could probably reverse the changes you've made to alsa-base.conf and just try deleting the .pulse configuration folder (~/.pulse if you are using 12.04, ~/.config/pulse, for 14.04 or later.) and then logout and/or reboot.

Then, test your audio and if needed, try to setup it again in your sound settings.

Hope that helps.

---

### Post by MajinSaha on 2015-06-19
Thanks for the first response.
I tried what you said. After reboot I noticed that .pulse directory again, it just reappeared. No sound whatsoever. Headphones are still fine.

---

### Post by MajinSaha on 2015-06-19
Bump please.

---

### Post by kostkon on 2015-06-20
You could check your hardware volume levels in alsamixer; open a terminal and give:
```
alsamixer
```
then press F5 to view all the volumes, F6 to select a different sound device, if needed. Make sure that everything is at 100% and not muted.

Also, to be on the safe side and be sure it will not happen again in the future, you could disable the *Allow skype to automatically adjust volume levels* option in Skype (under Sound.)

---

### Post by MajinSaha on 2015-06-23
Sorry for not responding earlier. On some occasions these past days, the sound was returning for a few seconds without me doing anything specific. It also worked just when I started typing this answer and then it stopped again. 
It was the right speaker only. The left one still quite. 
I proceeded with your advice and saw
[ATTACH=CONFIG]262825[/ATTACH]
I made everything go up, except that I couldn't do anything with the speaker. It's just down completely. That seems bad, doesn't it?

---

### Post by MajinSaha on 2015-07-02
Anyone else?

---

### Post by monkeybrain20122 on 2015-07-03
Install pulse audio volume control (pavucontrol) and check that Output Devices is set to speaker

---

### Post by MajinSaha on 2015-08-16
monkeybrain20122,
I tried but didn't help.
This is the screenshot.
[ATTACH=CONFIG]263878[/ATTACH]

---

### Post by monkeybrain20122 on 2015-08-17
I don't know. Check the configuration tab. May have to turn off HDMI.

---

