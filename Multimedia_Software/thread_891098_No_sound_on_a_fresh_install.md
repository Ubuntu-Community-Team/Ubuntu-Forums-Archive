---
title: "No sound on a fresh install?"
date: 2008-08-15
forum: Multimedia Software
---

### Post by e2k on 2008-08-15
I haven't used linux since Dapper, so I think I'm a little out of touch. Now I decided to do something about it, and installed a fresh Hardy.. Everything seems to work as it's supposed, except the sound.

I can't manage to get it working at all, even though I've followed the [Comprehensive Sound Problem Solutions Guide](http://ubuntuforums.org/showthread.php?t=205449&highlight=multichannel). I tried the general help without any success. I also got the drivers from a *fresh* kernel, no luck.

What to do now? As I mentioned before, I haven't been fooling around with linux in a while, so I'd be happy if you would point out what you want me to copypaste here! :)

Thanks in advance..

---

### Post by leepesjee on 2008-08-15
Hello,
You really need to supply a little bit more information here. Where did get struck in the Comprehensive Sound Problem Solutions? Any error mesaages? Do you have any special hardware? What exactly have you tried and did not work?
Leo.

---

### Post by e2k on 2008-08-15
> **leepesjee said:**
> Hello,
You really need to supply a little bit more information here. Where did get struck in the Comprehensive Sound Problem Solutions? Any error mesaages? Do you have any special hardware? What exactly have you tried and did not work?
Leo.
You're right, my post was a little flimsy.. :D
Here goes:

*lspci -v* gives (what I think is relative)
```
00:0b.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
	Subsystem: Creative Labs SBLive! 5.1 Model SB0100
	Flags: bus master, medium devsel, latency 32, IRQ 22
	I/O ports at b400 [size=32]
	Capabilities: <access denied>

00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
	Subsystem: Giga-byte Technology GA-7VAX Onboard Audio (Realtek ALC650)
	Flags: medium devsel, IRQ 21
	I/O ports at d400 [size=256]
	Capabilities: <access denied>
```
*aplay -l* gives
```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Live [SB Live 5.1], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 1: Live [SB Live 5.1], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 1: Live [SB Live 5.1], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```
Apparently these two can find my soundcard..
Then I tried *sudo modprobe snd-emu10k1*, doesn't give any output, I recon it does what it should? Still no sound..
I continued to follow the tutorial, going with this:
```
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
sudo apt-get install linux-sound-base alsa-base alsa-utils
sudo apt-get install gdm ubuntu-desktop
```but this didn't help either.. I also fiddled around with alsamixer (unmuting almost everything), but nada. What might I be doing wrong here? :confused:

---

### Post by leepesjee on 2008-08-16
I donno if I can help you out here. At least your sound card it recognized and the driver is in place, so the solution cannot be too far away.
It may be some issue with pulseaudio in the way. To check you can kill the pulseaudio daemon with```
killall pulseaudio
```and try again. Another thing is the onboard audio. If you start alsamixer, you can see which card it uses. If it's your audio card youre ok, otherwise you have look around a little. I've seen threads about issues with multiple cards and/or on-board audio.

---

### Post by Crafty Kisses on 2008-08-16
Post the output of
```
lsusb
```
Have you tried messing with alsa?

---

### Post by e2k on 2008-08-16
> **leepesjee said:**
> I donno if I can help you out here. At least your sound card it recognized and the driver is in place, so the solution cannot be too far away.
It may be some issue with pulseaudio in the way. To check you can kill the pulseaudio daemon with```
killall pulseaudio
```and try again. Another thing is the onboard audio. If you start alsamixer, you can see which card it uses. If it's your audio card youre ok, otherwise you have look around a little. I've seen threads about issues with multiple cards and/or on-board audio.
Apparently I had multiple cards (don't know where the other (via82xx) comes from), and the other one was defaulted. So I made my SB default, which lead to some sounds working (like the drums when logging in). :cool:

After pondering a while, I followed your second advice, killing pulseaudio. This took care of the problem! Now all sounds work.. I put alsa as the default sound system in gnome's sound preferences, which seems to do the trick. Thanks a million for a helpful post! \\:D/

---

### Post by leepesjee on 2008-08-16
You're welcome. Well, we found the cause of your problems. I'm not sure if this works as a permanent solution. You might have a look at this thread:
[http://ubuntuforums.org/showthread.php?t=885437](http://ubuntuforums.org/showthread.php?t=885437)
Or, you can go the other way round and try to fix the pulseaudio issues, see:
[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)
Leo.

---

### Post by cooke77 on 2008-08-18
From what your lspci Code says...you have both the 'on-board'/'add-in' Sound Enabled.
Disable the 'on-board' Sound.
I use a Creative Live! 5.1 (emu1ok1)...in my other Computer.
It works just fine.

---

### Post by markbuntu on 2008-08-18
There is really no need to disable a sound card in bios. I have on-board and a plugin card and I find having them both operating to be very useful to me, and more fun.

---

