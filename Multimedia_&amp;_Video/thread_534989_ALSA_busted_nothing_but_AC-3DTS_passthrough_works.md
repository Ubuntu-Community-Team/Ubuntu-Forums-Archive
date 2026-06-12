---
title: "ALSA busted: nothing but AC-3/DTS passthrough works"
date: 2007-08-25
forum: Multimedia &amp; Video
---

### Post by jboehm on 2007-08-25
Hi,

Everything been working great for quite a while.  I use a spdif connection between my htpc and my receiver.  I used dmix-digital as my alsa:default to send out analog tv and digital  AC-3/DTS audio thru the spdif connection.  See the attached asound.conf.

I was playing with xine last night and at one point it popped up some message about not gaining access to the audio channel.  Don't know if that was the cause of the problem but now my analog tv audio out the spdif connection is GONE!!  The digital audio still works (hdtv and dvds AC-3/DTS passthrough.)  But no analog source material works (analog tv recording.) Even the annoying system bell is busted. 

jboehm@catwomen:~$ /usr/bin/aplay -D default /usr/share/sounds/alsa/Front_Center.wav
Playing WAVE '/usr/share/sounds/alsa/Front_Center.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mono
****But no sound comes out!!! ****

I did a test and changed the default from dmix-digital to dmix-analog and the analog tv content made it to the headphone jack. Of course in this test the digital pass thru is garbage.

I did some testing today, I've come to the conclusion that /etc/asound.conf is fine. The system is responding to changes.  I suspect the simple codecs?? have been blown away.  For example the bell doesn't play and *.wav files don't play. Only AC-3/DTS passthrough works.

I noticed that the default xine pass through port was
audio.device.alsa_passthrough_device:iec958:AES0=0x6,AES1=0x82,AES2=0x0,AES3=0x2
I wonder if that hosed something up at a really low level.  I've restarted several times and even shutdown and unplugged the power hoping to reset the problem -- no luck.

I tried to grab the alsa-info script but [www.linux-sound.info](www.linux-sound.info) was down today.  Instead I have posted the output from the Aadebug script.

Thanks for the much appreciated help,
Jon

---

### Post by jboehm on 2007-08-28
I believe it is safe to say the the problem is fixed now.  It turns out that xine corrupted asound.state in memory when it crashed.  On shutdown the corrupted asound.state gets copied to /etc/asound.state.  Then at boot /etc/asound.statef gets copied back into memory.  No matter how many times I deleted /etc/asound.state the corrutped version always came back.  

I had a backup copy of /etc/asound.state.  I back up my important directories every night via rsync. /etc is one of those directories.  When the problem first occurred I had the good sense to turn off auto backups.

I grabbed the backup copy of /etc/asound.state placed it in /etc/asound.state.safe and did the following:

alsactl -f /etc/asound.state.safe restore

rebooted to make sure it stuck and I was good to go.

Thanks for the help,
Jon

PS. bad xine ... bad
FYI.  Since I have a well thought out asound.conf I changed 
audio.device.alsa_passthrough_device:iec958:AES0=0 x6,AES1=0x82,AES2=0x0,AES3=0x2
to
audio.device.alsa_passthrough_device:default
Hopefully this won't happen again

---

### Post by Suk on 2007-11-14
same problem, nearly the same solution, with Gutsy.
I posted my working asound.state here : [http://ubuntuforums.org/showthread.php?t=445536](http://ubuntuforums.org/showthread.php?t=445536)
Notice that, on Gutsy, I found the asound.state in /var/lib/alsa instead of /etc/.

---

