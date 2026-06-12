---
title: "[SOLVED] USB Midisport 1x1 Help"
date: 2006-08-10
forum: Multimedia &amp; Video
---

### Post by greenlegacy on 2006-08-10
I'm pretty new to Ubuntu and linux for that matter.  I'm pretty comfortable with using Finale on my windows partition, but I'm trying to break free from that.  Are there any good open source Finale-ish programs?

My other question is about my MIDI device.  It's a USB Midisport 1x1.  It didn't mount automagically, so I'm unsure what to do.  Any help would be appreciated.

---

### Post by philipacamaniac on 2006-08-11
Try Rosegarden or NoteEdit. Both pretty decent contenders against Finale's featureset.

Are you sure the USB Midisport isn't recognized? I checked the ALSA website, which says they have a driver for it. Does the output of

```
lsusb
```

mention anything about it?

It won't actually "mount" because it isn't a drive. In fact, you won't notice any indication that you plugged it in. But if you load up a MIDI program, or something like QJackCtl (a JACK/MIDI patchbay), then you would probably see it.

---

### Post by goodmanbrown on 2006-08-12
I agree with the noteedit recommendation.  It is about as intuitive a score editor as you'll see.  (I have not found the same to be true of rosegarden.)

---

### Post by greenlegacy on 2006-08-24
Noteedit seems to be what I'm going for, more so than Rosegarden.

The lsusb command does seem to show that the computer senses the midi to usb device, but its still not really sending or receiving data with it.

---

### Post by capsid on 2006-08-31
Hi!

How are you determining that no data is being sent or received?  Pardon me if you already know this, but you said you were new.  Like philip said, try patching into something to test it.  You could use jackControl like he's talking about, or aconnectgui.  Puredata is good for testing MIDI equipment, among other things.

Could it be this? (from ubuntustudio.com) 

USB MIDI Keyboard/USB Secondary Sound Card Fix

If you use a USB MIDI keyboard or a USB sound card as your secondary device, you may run into issues with it taking priority over your PCI device as your main sound card. This tends to happen if you leave it turned on and plugged in during boot. Here is the solution:

sudo su
if grep -q "snd-usb-audio index" /etc/modprobe.d/alsa-base; \
  then echo && echo "NOTE: snd-usb-audio is already indexed in /etc/modprobe.d/alsa-base, no changes made."; \
  else cp /etc/modprobe.d/alsa-base /etc/modprobe.d/alsa-base_backup_`date +%Y%m%d%H%M` && \
  echo options snd-usb-audio index=1 >> /etc/modprobe.d/alsa-base; \
fi
exit

---

### Post by dolson on 2006-08-31
Try reading this: [http://ubuntustudio.com/wiki/index.php/QjackCtl_Connections](http://ubuntustudio.com/wiki/index.php/QjackCtl_Connections)

You should gain a basic understanding of how to use JACK Control to make MIDI connections, and how to make audio connections with JACK. Simply substitute the Vkeybd for your USB MIDI device, and it should work.

---

### Post by gosh on 2007-01-09
There is a great guide in making your midisport work: [http://www.ubuntuforums.org/showthread.php?t=96506&highlight=midisport+howto](http://www.ubuntuforums.org/showthread.php?t=96506&highlight=midisport+howto)

---

### Post by greenlegacy on 2007-04-14
Oops, I kind forgot about this thread until just now.  I did end up solving my problem a while ago:  I needed the firmware.  Everything works great now!

:D

---

