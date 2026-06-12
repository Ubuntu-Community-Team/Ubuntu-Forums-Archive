---
title: "No sound only on YouTube"
date: 2011-08-20
forum: Multimedia Software
---

### Post by Oldhacker on 2011-08-20
Running Ubuntu 10.04 64 bit with Firefox 6.0

The sound level in YouTube had been lower than normal, but as of today there is **no** sound in YouTube.

The picture comes in fine, and the sound is normal on videos embedded in the news channels.

---

### Post by Oldhacker on 2011-08-21
Not having been overwhelmed with responses to my post about no sound in YouTube, I did find a crude workaround that I am now using.

I installed the following add-ons:
Flashblock 1.5.15.1
FlashVideoReplacer 2.1.14

They allow me to hear normal sound in YouTube at the inconvenience of slower loading of clips and some stuttering.

Then, I disable both of them when I want to hear the flash clips on all of the news channels.
Bothersome, but it is better than nothing.

Hopefully, this may help anyone with a similar problem.

---

### Post by .... on 2011-08-22
You probably have no sound from ALSA apps in general (since Flash is an ALSA app). Make sure you have the following: 
- libasound2-plugins package installed.
- The bolded line in /usr/share/alsa/alsa.conf
```
@hooks [
        {
                func load
                files [
                        **"/usr/share/alsa/pulse.conf"**
                        "/etc/asound.conf"
                        "~/.asoundrc"
                ]
                errors false

```If it still doesn't work, see: [http://ubuntuforums.org/showthread.php?t=1455816](http://ubuntuforums.org/showthread.php?t=1455816)
EDIT: Note that if you have to alter/create a .conf file the change won't occur until you restart at least the alsa service or the entire system.

---

### Post by Oldhacker on 2011-08-22
Thank you for your detailed response.
I DO have the libasound2-plugins package installed and The bolded line in /usr/share/alsa/alsa.conf is there as well.

Next I shall follow the thread that you gave and will report back what I find there.

---

### Post by Oldhacker on 2011-08-22
I followed the thread, put the following lines of code into /etc/asound.conf 

Code:

pcm.pulse { type pulse }
ctl.pulse { type pulse }
pcm.!default { type pulse }
ctl.!default { type pulse }

Then, I rebooted and tried YouTube:
result: no sound
Continuing with the thread, I put the same lines of code into creating a new file (which was non-existent) ~/.asoundrc
Rebooted and tried YouTube again.
Result: still no sound
I'll have to keep searching for some other avenue which may be at fault, but thank you again for your efforts.

---

### Post by Oldhacker on 2011-08-24
After making countless attempts at getting the sound in YouTube to work normally, I got a "brilliant" idea: Try going back to an earlier kernel! I went into my GRUB configuration and must have made an error before I saved the alteration. 
Then, I was unable to boot into Ubuntu at all. That left me with only one alternative:
Re-install Ubuntu 10.04 from my DVD. After I did this, I put back all of my data from my backup file on another drive and also put back some of the extra applications that I use for LightScribe, etc. Now, I am using the stock Firefox 3.6.20 instead of the Firefox 5.0 and 6.0 that I was experimenting with. They could have been the source of the conflicts. For the foreseeable future, I shall stick to Ubuntu's own upgrades. ;-)

---

### Post by 1ain on 2011-09-14
I know this may seem obvious, but I was using my 10.04 laptop for the first time in weeks and after I did the necessary updates I went to youtube and there was no sound, all other audio was working ok. What had happened was the volume control at the bottom of the youtube screen had defaulted to mute with a small *x* next to the speaker symbol! Maybe this isn't the problem in your case but it's certainly worth a check first. :lolflag:

---

