---
title: "Slightly sloooow audio"
date: 2014-02-06
forum: Multimedia Software
---

### Post by motorcity909 on 2014-02-06
Hi all

Bit of a funny one.  Over the past few weeks, I've noticed audio plays ever so slightly slow.  It's almost imperceptible; we're not talking a cassette Walkman with the batteries running out!  It's just very very slight and barely noticable unless you know the song very well.  I mainly noticed it from playing the same songs on CD or my iPod in the car.

This slowness is apparent when playing audio/video files (mp3, avi, mp4, etc), YouTube videos and BBC Iplayer too.  

Does a soundcard have, for want of a better word, a "clock" which has maybe lost a milli-second or two?

I'm just using the integrated sound output from the motherboard.  My graphics cards has a HDMI output but I don't use it.

If it helps, this is the output from ```
lspci -v | grep -A7 -i "audio"
``` - 

00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA)
    Subsystem: ASUSTeK Computer Inc. Device 8445
    Flags: bus master, slow devsel, latency 64, IRQ 16
    Memory at fcff4000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel

00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 LPC host controller
--
01:00.1 Audio device: NVIDIA Corporation GF108 High Definition Audio Controller (rev a1)
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at feaf8000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)
    Subsystem: ASUSTeK Computer Inc. P8P67 and other motherboards


Any help will be very much appreciated
Dave

---

### Post by motorcity909 on 2014-02-07
Quick update.  I changed a setting in /etc/pulse/daemon.conf - I changed default-sample-rate from 44100 to 48000 and I *think* it's worked.  Although now I'm listening to a song and thinking 'is that too fast?'.

This may well drive me mad!!

Any other thoughts will be much appreciated.

Cheers
Dave

---

### Post by tgalati4 on 2014-02-07
Sound chips are controlled by crystal oscillators that tend to slow down over time.  Your 44.1 KHz oscillator is probably slow so going to 48 KHz provides some correction, but now your music is a semitone (or more) higher pitch.  If you have a smartphone, load a guitar tuner app.  Make some 1-minute audio test files in *audacity*.  Use the sine wave generator at 440 Hz (A key).  Play it through your speakers and have the phone app show you the key and frequency.  If it is not exactly 440, then you have a problem.

The music player *audacious* has an effects setting that allows you to make slight corrections to the audio clock.  Play with that so you can see how much you are off from being "in tune".

*speaker-test* will also generate tones on the fly:

tgalati4@Mint14-Extensa ~ $ speaker-test -t sine -f 440

speaker-test 1.0.25

Playback device is default
Stream parameters are 48000Hz, S16_LE, 1 channels
Sine wave rate is 440.0000Hz
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 192 to 2097152
Period size range from 64 to 699051
Using max buffer size 2097152
Periods = 4
was set period_size = 524288
was set buffer_size = 2097152
 0 - Front Left

---

### Post by motorcity909 on 2014-02-07
That is a really helpful post, many many thanks.

I did as you advised and the guitar tuner app showed 439.9.

So would that -0.1 make the almost imperceptible slowness I can feel/hear?

If so, I guess that brings me to the need for a longer term solution.  I'm guessing buying and installing a stand-alone sound card?

---

### Post by Yellow Pasque on 2014-02-07
Try this:
```
echo "options snd-hda-intel enable_msi=1" | sudo tee -a /etc/modprobe.d/alsa-base.conf
```

See if there's a difference in your next boot.

---

### Post by motorcity909 on 2014-02-07
Will do.  What is that meant to do?

Oh, one other thing - between my second post and your first reply (the tuning app idea), I had changed the /etc/pulse/daemon.conf *back* to 48000, so my test with the guitar tuning app was with the 48000 figure restored.

I changed it because I was hearing a slight speed up, which you confirmed was probably a semitone higher pitch.

So, with the 48000 setting back, does that change your suggested command?

Thanks for all your help
Dave

---

### Post by tgalati4 on 2014-02-07
A 440 Hz tone should be 440 Hz regardless of the clock speed.  If not, then there is a problem.  Now .1 Hz may be within tolerance of the crystal oscillator, that you will have to research.  

Check 880 and 1760 as well.  Higher frequencies will magnify the error and that may be audible.  Concert tuning is typically 441, 442, 443 Hz after an hour of playing.  This is to compensate for the strings and wood instruments stretching during a performance so they stay in tune with the brass (which don't change much).  So I would say a 1 to 2 Hz difference is audible, but a 0.1 Hz is probably not.  Remember, each device has an oscillator and there will be slight differences.  

Create some WAV or mp3 tracks with pure tones 220, 440, 880, 1760.  Burn them to a CD or put them on your ipod and mp3 players and you will see slight differences between them.

More than you want to know about crystal oscillators:  [http://en.wikipedia.org/wiki/Crystal_oscillator_frequencies](http://en.wikipedia.org/wiki/Crystal_oscillator_frequencies)

Typical audio oscillators are run at:  > 45.1584 MHz  Used in CD-DA systems and CD-ROM drives; allows binary division to 44.1 kHz (1024×44.1 kHz), 22.05 kHz, and 11.025 kHz. Also allows integer division to common UART baud rates up to 115200. Available as a TCXO. Frequencies also used are 11.2896 MHz, 16.9344 MHz, 22.5972 MHz and 33.8688 MHz.

---

### Post by motorcity909 on 2014-02-07
Interestingly, using the tuning app on 880 and 1760 files showed them exactly at their respective numbers.  Not even a 0.1 deviation like with 440 file.

I'm wondering if it's all just in my head!!

BTW, what is that command 
```
echo "options snd-hda-intel enable_msi=1" | sudo tee -a /etc/modprobe.d/alsa-base.conf
```

meant to do?

Thanks again
Dave

---

### Post by tgalati4 on 2014-02-07
That is a switch:

tgalati4@Mint14-Extensa ~ $ modinfo snd-hda-intel
filename:       /lib/modules/3.5.0-39-generic/kernel/sound/pci/hda/snd-hda-intel.ko
description:    Intel HDA driver
license:        GPL
srcversion:     56BA5E778974145B901C998
.
.
.
depends:        snd-hda-codec,snd-pcm,snd,snd-page-alloc
intree:         Y
vermagic:       3.5.0-39-generic SMP mod_unload modversions 
parm:           index:Index value for Intel HD audio interface. (array of int)
parm:           id:ID string for Intel HD audio interface. (array of charp)
parm:           enable:Enable Intel HD audio interface. (array of bool)
parm:           model:Use the given board model. (array of charp)
parm:           position_fix:DMA pointer read method.(0 = auto, 1 = LPIB, 2 = POSBUF, 3 = VIACOMBO, 4 = COMBO). (array of int)
parm:           bdl_pos_adj:BDL position adjustment offset. (array of int)
parm:           probe_mask:Bitmask to probe codecs (default = -1). (array of int)
parm:           probe_only:Only probing and no codec initialization. (array of int)
parm:           single_cmd:Use single command to communicate with codecs (for debugging only). (bool)
**parm:           enable_msi:Enable Message Signaled Interrupt (MSI) (bint)**
parm:           patch:Patch file for Intel HD audio interface. (array of charp)
parm:           beep_mode:Select HDA Beep registration mode (0=off, 1=on, 2=mute switch on/off) (default=1). (array of int)
parm:           power_save:Automatic power-saving timeout (in second, 0 = disable). (int)
parm:           power_save_controller:Reset controller in power save mode. (bool)
parm:           align_buffer_size:Force buffer and period sizes to be multiple of 128 bytes. (bint)
parm:           snoop:Enable/disable snooping (bool)

By setting it to "1" the switch enables something called Message Signaled Interrupt.  I have no idea what it does, but you could probably search the web for it.

---

### Post by motorcity909 on 2014-02-07
Okay, thanks again.

Not sure I want to run a command that I'm not sure of what it will do.

I'm now thinking of trying a USB sound card and bypassing the internal sound card altogether.

I may start another thread to ask about recommedations for any particular such soundcard.    Oddly enough, there is a very little out there on the web about good USB cards to use with (X)Ubuntu.  I'm guessing (hoping) that's because they simply work.

Many thanks once again for all your help with this.

Dave

---

### Post by tgalati4 on 2014-02-07
Burn a CD and check your car player with your tuner app.  Check your iPod as well with some reference tone mp3 tracks.  It's possible that your computer is OK and your car CD and iPod are slightly fast.

---

### Post by motorcity909 on 2014-02-07
That is a very good idea.  Might be a day or two before I get to it as out all day tomorrow.

Just want to say thanks again for all your help with this, it's really appreciated.

Dave

---

### Post by motorcity909 on 2014-02-10
Hi again

Tried the three test files on my iPod.  440 and 880 were just 0.1 and 0.3 over, respectively and the 1760 was exact.

I've ordered a USB soundcard from Amazon which should arrive in the next day or two so once I plug that in, I can bypass the onboard sound which is where, I think, this slowness is coming from.

The reviews include good experiences from a few Linux users (Ubuntu, Xubuntu, Mint, Fedora and Debian were all mentioned) so hopefully it will do the trick.

Cheers
Dave

---

### Post by Yellow Pasque on 2014-02-10
So have you tried enable_msi=1 or not?

> Interrupt Handling
~~~~~~~~~~~~~~~~~~
HD-audio driver uses MSI as default (if available) since 2.6.33
kernel as MSI works better on some machines, and in general, it's
better for performance.  However, Nvidia controllers showed bad
regressions with MSI (especially in a combination with AMD chipset),
thus we disabled MSI for them.

There seem also still other devices that don't work with MSI.  If you
see a regression wrt the sound quality (stuttering, etc) or a lock-up
in the recent kernel, try to pass `enable_msi=0` option to disable
MSI.  If it works, you can add the known bad device to the blacklist
defined in hda_intel.c.  In such a case, please report and give the
patch back to the upstream developer. 


---

### Post by motorcity909 on 2014-02-10
No I didn't.  I'll see how I get on with USB soundcard.

Cheers
Dave

---

### Post by tgalati4 on 2014-02-10
I spent the afternoon tuning several electronic keyboards.  I could tell the difference between 440 and 439 or 441, but I couldn't really distinguish 440.5 or 439.5 especially with the warble that exists in most older electronic keyboards.  I find using *gtkguitune* convenient. I plug the line out of a keyboard into the line-in of a laptop and set the appropriate gains.  You can see the variation and the ripple noise from these 20 and 30-year old keyboards.  The timing accuracy of a thinkpad laptop is several times better than the analog circuitry in these old noise makers.

---

### Post by motorcity909 on 2014-02-11
But isn't there something charming in that non-perfectness?  That's why people like Orbital and the Chemical Brothers love the old synths.

---

### Post by Elfy on 2014-02-11
> **motorcity909 said:**
> But isn't there something charming in that non-perfectness?  That's why people like Orbital and the Chemical Brothers love the old synths.and good musicians didn't even have the option of digital ones :p

---

### Post by motorcity909 on 2014-02-13
Well, the USB soundcard arrived and seems to have solved the problem.

No slowness anymore and if anything it's a bit louder too.

For info, it was [this]("http://www.amazon.co.uk/PC-Trading%C2%AE-Virtual-Stereo-External/dp/B005NPK5DE") USB soundcard and it works fine with Xubuntu.  Simply plugged in and it just worked.  No drivers, no reboot.  It appeared as a new analogue device in the Pulse Audio sound settings, select it and that was it, job done.

Nice to read all the reviews from Windows users on Amazon talking about downloading and installing drivers!  

Anyway, particular thanks to Temüjin for all your help.  Learnt a lot about audio from you, mate, so many thanks.

Dave

:guitar:

---

### Post by tgalati4 on 2014-02-14
It's a growing trend.  As folks determine that their on-board audio sucks, they look for other solutions.  For instance, RaspberryPi's have mediocre sound, so Wolfson steps in:
[http://www.element14.com/community/community/raspberry-pi/raspberry-pi-accessories/wolfson_pi](http://www.element14.com/community/community/raspberry-pi/raspberry-pi-accessories/wolfson_pi)

And yes, I do like that analog sound and working analog keyboards command premium prices as a result.  (They are really hard to keep running.)

---

