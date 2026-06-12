---
title: "Sound wont work"
date: 2006-06-03
forum: Multimedia &amp; Video
---

### Post by ViperAFK on 2006-06-03
Ok I have an dell 4600 with integrated Intel ICH5 sound card, this is the first time i have used linux and it seems to have detected my sound card, but i cannot get sound to play out of the speakers at ALL, i have Ubuntu 6.06

---

### Post by ViperAFK on 2006-06-03
bump

---

### Post by nysmo on 2006-06-03
I also have an Intel ICH5 onboard in my pc, and it doesn't play sound.
The strange thing is that after I installed dapper I had sound, just today I opened aMsn and "puff" no more sound. Maybe just a coincidence, maybe not.

Just Solved my problem: run "alsamixer" in the cli and see if Master and PCM are both ON, if not press "m" to turn them on.
Hope this works for you

---

### Post by ViperAFK on 2006-06-03
thanks, nothings muted, but sound still doesnt work

---

### Post by ViperAFK on 2006-06-03
bump

---

### Post by zaroff on 2006-06-03
I'm also having trouble with the ICH5 onboard sound on my Sager 8890 laptop in Dapper.  In Gnome, when any application tries to play sound it just hangs.  I've checked alsamixer and everything is unmuted.  lsmod shows that the snd_intel8x0 module is loaded.  But everytime I try to play sound with xmms, totem, etc., they all just hang and do nothing.  I've tried running gstreamer-properties and changing the default output plugin between alsa and esd, but when I click the 'Test' button and the 'Testing' window comes up, there's no tone.  If I then click 'OK', gstreamer-properties freezes.

Interestingly, in spite of all this, the drum sound does play at the GDM login prompt.  Ideas?

---

### Post by deodatus on 2006-06-04
I found something like this on a Fedora forum.
Open terminal:
#*sudo alsaconf*
follow instructions, then:
#*sudo gst-register-0.8* 
This registers all the GStreamer plug-ins among other things I don't know of.
*reboot*.  It wouldn't work until I rebooted.

---

### Post by zaroff on 2006-06-05
> I found something like this on a Fedora forum.
Open terminal:
#sudo alsaconf
follow instructions, then:
#sudo gst-register-0.8
This registers all the GStreamer plug-ins among other things I don't know of.
reboot. It wouldn't work until I rebooted.

alsaconf is no longer included with alsa-utils in Dapper.  Any other suggestions?

---

### Post by scaltro on 2006-06-05
Same problem, my sound card is recognized,but when a stream is playing,i can't heard nothing?

---

### Post by Zap on 2006-06-10
I've the same card and the same problem :(
It's seems nobody know who can we can sounds :(

---

### Post by ViperAFK on 2006-06-12
has there been any solution to this yet? It seems The ICH5 is supported through the i810+AC97 driver and it should be included inthe kernel. SO WHY WONT SOUND WORK

---

### Post by mandible on 2006-06-13
resolved my issue and it had nothing to do with Ubuntu.

---

### Post by ViperAFK on 2006-06-14
hmmm one of the first things i did was install automatix also, to get the mp3 codecs ect...

---

### Post by zirakzigal on 2006-06-17
I solved my Dell Dimension ICH5 no sound issue on ubuntu 6.06.  I have had this problem on most distros of linux.  No sound coming out of speakers, but headphones worked.  Below works for my system.

Go to the Volume Control (double click speaker icon).  On the Switches tab, check Spread Front to Surround and Center/LFE.

On Playback tab un-mute and bring volume up on Master Surround, PCM and Master.  If you do not see one of these, Edit-Preferences and check them.

This has been driving me nuts for months. I hope this helps others.

---

### Post by zirakzigal on 2006-06-17
Forgot to add this:

Options tab - Set Channel Mode to 6ch.

Hope it works for you all.

---

### Post by jajemera on 2006-07-20
Hello. You might be using a mono speaker, like the ones built in the pcs itself. I have an IBM Thinkcentre A50 and initially the sound isn`t working. What you should do is double click on the speaker icon, then on the preferences, check master mono and increase the volume(it is initially set to zero). That should work. In case you aren`t using a mono speaker, try tweaking the others tracks in the preferences list.:cool:

---

### Post by wenzlicker on 2006-10-06
My sound stopped working after a kernel update. I found the answer on another forum (sorry I lost the link).

In a terminal, type ```
gnome-volume-control
``` and make sure PCM is unmuted.

---

### Post by zaroff on 2007-07-08
ok, I know this is a really old thread but I would just like to post the solution that I recently found for my problem with the sound not working correctly on my Sager 8890. The trick is to add 'irqpoll' as an option to the kernel on boot up. It's a very simple fix and so far I've tested it successfully with Ubuntu Feisty and Knoppix. Just wanted to pass this along in case anyone else is still struggling with a similar problem (it took me over a year to accidentally find this answer).

---

