---
title: "Sound On and Off on Startup"
date: 2006-10-19
forum: Multimedia &amp; Video
---

### Post by blueidealist on 2006-10-19
I have an IXP SB400 AC97 Audio Controller.

I tried to tweek alsamixer in all possible ways...
But I nevertheless have this major problems.

On some boots: the sound works.
On other boots: the sound doesn't work.

I have not been able to find any logic.  I may have the computer running.  Boot up - and I'll hear the Ubuntu login music.  Reboot... and it's disappeared (or inversily) without doing a thing.
When it doesn't work, I usually try to tweak alsamixer by moving up and down some knobs and rebooting, but by far this trick may simply be superstition as it certainly doesn't work systematically.

This is annoying...
Anyone can help?

David

---

### Post by ReaderRat on 2006-10-20
I don't know if this will help:
Sound Solutions - Comprehensive Guide
         [http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide)

---

### Post by blueidealist on 2006-10-20
The thing is that my sound card is recognized at all times, whether the sound works or not on startup.

david@David:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: IXP [ATI IXP], device 0: ATI IXP AC97 [ATI IXP AC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Modem [ATI IXP Modem], device 0: ATI IXP MC97 [ATI IXP MC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

So following the thread, I move to alsamixer...
And I've tweaked it as I said in all possible ways and have not been able to find some setting which would make my sound work on every startup.

So I'm still lost.

David

---

### Post by blueidealist on 2006-10-21
I tried comparing aplsy -l and lspci -v terminal command results wen the sound is working and when it isn't working.
No luck: I get the exact same response on all lines:

david@David:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: IXP [ATI IXP], device 0: ATI IXP AC97 [ATI IXP AC97]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 1: Modem [ATI IXP Modem], device 0: ATI IXP MC97 [ATI IXP MC97]
Subdevices: 1/1
Subdevice #0: subdevice #0

david@David:~$ lspci -v
[...]
0000:00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
        Subsystem: Gateway 2000: Unknown device 0301
        Flags: bus master, 66MHz, slow devsel, latency 64, IRQ 209
        Memory at d0503400 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>
[...]

I'm still lost on this prolem...

David

---

### Post by blueidealist on 2006-10-21
In the event that I cannot solve this issue,

is there any way to reset the sound in Ubuntu without having to reboot the computer (a kind of "kill-all sound" kind of thing)?

 This would be gladly appreciated to avoid my many reboot (and crossing fingers) attempts at restarting to have sound.

David

---

### Post by elv on 2006-10-25
Having similar problems myself with Edgy, can anyone shed some light on this

---

### Post by ginkhao on 2006-10-25
Me too, mine works until I touch the volume control, then it dies and I have to reboot if I want sound, even if it can't be fixed I'd like to know how to re-start it without a reboot.

---

### Post by bhtooefr on 2007-06-05
Necroposting, but I've got a similar issue on Feisty. In my case, it'll work, but then, usually when playing a Flash video, it'll start stuttering. At this point, sound will no longer work, period, and I have to reboot.

Also, when playing videos from YouTube after this has happened, the video will stop progressing after two seconds in Opera. Firefox is intermittently affected.

---

### Post by PhoenixBlessings on 2007-12-18
When I start my computer up it sometimes does not have sound, but then if I restart it 1 or 2 times, then one of the times my sound will work. 

Is there anything that would cause this? Also, are there any ways to fix it?

I run Gutsy Gibbon, but the same thing happened when I ran Feisty Fawn.

---

