---
title: "rhythmbox, amarok, lastfm not working"
date: 2008-10-09
forum: Multimedia Software
---

### Post by soumyajit pramanick on 2008-10-09
hi, 
1. i am using lenovo R60 laptop with intel audio.

2. suddenly alsa has stopped working. and as a result rhythmbox, amarok and lastfm are not working.

3. i went to system>preferences>sound and tried all the tests.
getting some strange errors like 
'audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not get/set settings from/on resource.'

4. swithiching the default sound playback from 'autodetect' to 'OSS' makes Rhythmbox work,but amarok and lastfm are still mute.

please help!

---

### Post by Yellow Pasque on 2008-10-09
Did this happen after a kernel update? If so, I would try:
```
sudo sh /etc/init.d/alsa-utils restart
```
If that doesn't work, then: [https://help.ubuntu.com/community/SoundTroubleshooting#Getting%20the%20ALSA%20drivers%20from%20a%20*fresh*%20kernel](https://help.ubuntu.com/community/SoundTroubleshooting#Getting%20the%20ALSA%20drivers%20from%20a%20*fresh*%20kernel)

And, of course, the good ol' build-it-yourself method if those don't work: [http://ubuntuforums.org/showthread.php?t=820959](http://ubuntuforums.org/showthread.php?t=820959)

---

### Post by soumyajit pramanick on 2008-10-09
hi Temüjin,
thank you for your post.

you guessed right..this indeed happened after a karnel update. 

but alsa-utils restart didn't work.

Getting the ALSA drivers from a *fresh* kernel also didn't work.

i'll try your last option if i don't find any other not so technical solution as i am not very comfortable with codes.  :(

please help with any other solutions if possible..

---

