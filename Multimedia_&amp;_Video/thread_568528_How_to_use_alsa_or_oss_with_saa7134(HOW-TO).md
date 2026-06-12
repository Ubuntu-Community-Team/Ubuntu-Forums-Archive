---
title: "How to use alsa or oss with saa7134(HOW-TO)"
date: 2007-10-05
forum: Multimedia &amp; Video
---

### Post by damir_1105 on 2007-10-05
**[SIZE="2"]How to use alsa or oss with saa7134[/SIZE]**

Starting with kernel 2.6.15, the module saa7134-alsa lets you use ALSA to get sound directly from your capture card. From 2.6.16 you can use this module with more than one capture card.

In kernel 2.6.16, the saa7134-oss module is also separated out, and the two modules are treated in much the same way; you can build both and switch between them, though both cannot be loaded at once.

**[SIZE="2"]Insmod parameters[/SIZE]**

Now that both alsa and oss DMA sound have been separated out as distinct modules, it is no longer necessary (though it is not forbidden) to include the insmod parameter "alsa=1" or "oss=1".

On the other hand, on the 2.6.16 kernel, it's not safe to use the parameter "disable_ir=1" to turn off the infrared system for the remote -- that caused an oops. This is fixed in 2.6.17.

In the case of more than one card, you can use something like this:

```
saa7134 card=2,2,2,2 tuner=43,43,43,43 video_nr=1,2,3,4 vbi_nr=1,2,3,4 radio_nr=1,2,3,4
``` 

In dmesg, you should see this type of content murmuring:

```
input: saa7134 IR (LifeView FlyVIDEO30 as /class/input/input5
tuner 5-0061: chip found @ 0xc2 (saa7133[3])
tuner 5-0061: type set to 43 (Philips NTSC MK3 (FM1236MK3 or FM1236/F))
tuner 5-0063: chip found @ 0xc6 (saa7133[3])
saa7133[3]: i2c eeprom 00: 69 51 38 01 10 28 ff ff ff ff ff ff ff ff ff ff
saa7133[3]: i2c eeprom 10: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
saa7133[3]: i2c eeprom 20: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
saa7133[3]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
saa7133[3]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
saa7133[3]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
saa7133[3]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
saa7133[3]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
saa7133[3]: registered device video4 [v4l2]
saa7133[3]: registered device vbi4
saa7133[3]: registered device radio4
```

To then load the new driver that lets you get sound off the PCI bus via ALSA or OSS, you would normally just issue "sudo modprobe saa7134-alsa" or "sudo modprobe saa7134-oss". You can also deliberately assign the enumeration; for instance, for four cards, do this for alsa:

```
sudo modprobe saa7134-alsa index=1,2,3,4
```

Again, dmesg approves:
```

saa7134 ALSA driver for DMA sound loaded
saa7133[0]/alsa: saa7133[0] at 0xf5006000 irq 19 registered as card 1
saa7133[1]/alsa: saa7133[1] at 0xf5007000 irq 20 registered as card 2
saa7133[2]/alsa: saa7133[2] at 0xf5004000 irq 21 registered as card 3
saa7133[3]/alsa: saa7133[3] at 0xf5005000 irq 22 registered as card 4 
```

If instead you use OSS, issue this to determine enumeration:
```

sudo modprobe saa7134-oss dsp_nr=1,2,3,4 mixer_nr=1,2,3,4
```

You should see this in dmesg:

```
saa7134 OSS driver for DMA sound loaded
saa7133[0]: registered device dsp1
saa7133[0]: registered device mixer1
saa7133[1]: registered device dsp2
saa7133[1]: registered device mixer2
saa7133[2]: registered device dsp3
saa7133[2]: registered device mixer3
saa7133[3]: registered device dsp4
saa7133[3]: registered device mixer4
```

Note that if you use saa7134-oss in Debian, and build your kernel with ALSA as modules, you may need to add saa7134 to the OSS-module-list to keep your OSS emulation under ALSA (cf. #359851):

```
echo saa7134 >> /usr/share/linux-sound-base/OSS-module-list
```

If OSS emulation is not working, some applications (such as VLC) that expect ALSA sound devices won't be able to find the legacy OSS devices created by saa7134-oss.

If your ALSA is built into the kernel rather than as modules, you won't need to worry about this.

**[SIZE="2"]Insert modules on boot[/SIZE]**

To insert the modules with these parameters on boot, you can create a file called /etc/modprobe.d/saa7134 with the following lines (adjust card and tuner numbers as required):

```
options saa7134 card=2,2,2,2 tuner=43,43,43,43 video_nr=1,2,3,4 vbi_nr=1,2,3,4 radio_nr=1,2,3,4 
install saa7134 /sbin/modprobe --ignore-install saa7134; /sbin/modprobe saa7134-alsa
options saa7134-alsa index=1,2,3,4
```

Your distribution may require you to put these lines into /etc/modprobe.conf; this is not a good idea in Debian, since the files in /etc/modprobe.d will then be ignored.

If instead you use OSS, these lines will load the modules for four cards:

```
options saa7134 card=2,2,2,2 tuner=43,43,43,43 video_nr=1,2,3,4 vbi_nr=1,2,3,4 radio_nr=1,2,3,4 
install saa7134 /sbin/modprobe --ignore-install saa7134; /sbin/modprobe saa7134-oss
options saa7134-oss dsp_nr=1,2,3,4 mixer_nr=1,2,3,4
```

Note that once you've entered this information inside /etc/modprobe.d, your subsequent manual insertions will also make use of this information. Scripts, for instance, need not repeat it.

These instructions are of course specific to kernels 2.6.16 and later, as earlier kernels do not have separate DMA modules.

For kernels before 2.6.16, DMA sound via OSS is activated simply by the insmod parameter "oss=1".

**[SIZE="2"]Set permissions[/SIZE]**

Make sure your users are added to the group "audio" to get access to them -- in Debian, if your user name is "tv", you would use

```
adduser tv audio
```

**[SIZE="2"]List your capture devices[/SIZE]**

To get a list of your alsa capture devices, issue

```
arecord -l
```

You should see your regular sound card and the capture card(s):

```
**** List of CAPTURE Hardware Devices ****
card 0: CK8S [NVidia CK8S], device 0: Intel ICH [NVidia CK8S]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CK8S [NVidia CK8S], device 1: Intel ICH - MIC ADC [NVidia CK8S - MIC ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: SAA7134 [SAA7134], device 0: SAA7134 PCM [SAA7134 PCM]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: SAA7134_1 [SAA7134], device 0: SAA7134 PCM [SAA7134 PCM]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 3: SAA7134_2 [SAA7134], device 0: SAA7134 PCM [SAA7134 PCM]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 4: SAA7134_3 [SAA7134], device 0: SAA7134 PCM [SAA7134 PCM]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

**[SIZE="2"]Configure the cards to record[/SIZE]**

Set the cards to record on channel 1 and max volume, using for instance

```
alsamixergui -c 1
```

for each of the cards.

**[SIZE="2"]Watch with mplayer[/SIZE]**

You should now be ready to watch live tv with mplayer, using something like this:

These are for rf connections:

US broadcast or satellite:

```
mplayer tv://$channel -tv driver=v4l2:device=/dev/video0:chanlist=us-bcast:alsa:\
adevice=hw.1,0:amode=1:audiorate=32000:forceaudio:volume=100:immediatemode=0:norm=NTSC
```

If you're using a satellite box, $channel should probably be set to 3 or 4. If that doesn't work, try the US cable TV setup below. If you're getting your broadcast off the air, you can run the scantv utility to detect stations and set $channel to the local channel for your area.

US cable:

```
mplayer tv://"insert channel" -tv driver=v4l2:device=/dev/video0:chanlist=us-cable:alsa:\
adevice=hw.1,0:amode=1:audiorate=32000:forceaudio:volume=100:immediatemode=0:norm=NTSC
```

Here again you can run the scantv utility to detect the channels available from your provider, or you can use your provider's channel table.

Europe cable:

```
mplayer tv://"insert channel" -tv driver=v4l2:device=/dev/video0:chanlist=europe-west:alsa:\
adevice=hw.1,0:amode=1:audiorate=32000:forceaudio:volume=100:immediatemode=0:norm=PAL
```

Note the norm= and chanlist= parameters. Adjust as required for your location.

If "adevice=hw.1,0" doesn't work, try simply "adevice=hw.1". Some tuners require "adevice=hw.2" -- for instance, on a board with nforce 3 250/gb chipsets. If others experiance this with other boards, please update.

**[SIZE="2"]Record with mencoder[/SIZE]**

It may be simpler to get sound during recording than during playback. I get good sound using this, where $DEV is the number of the device node:

```
mencoder -tv driver=v4l2:device=/dev/video$DEV:fps=30000/1001:chanlist=us-bcast:\
audiorate=32000:alsa:adevice=hw.$DEV:input=0:amode=1:normid=4:width=576:height=432 \
-ovc x264 -x264encopts threads=2:bitrate=500:bframes=2:subq=1:me=1:frameref=4:8x8dct \
-oac mp3lame -lameopts cbr:br=64 -endpos $TIM -o $DIR/$FIL.avi tv:// > /dev/null
```

So the alsa device is simply called hw.1 -- not hw.1,0. The line is taken from the channel script. You may find you need to use hw.2 instead, depending on the audio hardware on your system.

Neither ffmpeg nor transcode as yet have ALSA support.

Because so many applications still appear to have difficulties accessing ALSA's odd device enumeration, the OSS module for DMA sound continues to be useful. You can also use ALSA's OSS emulation with saa7134-alsa to get /dev/dspX devices for OSS-aware applications.

**[SIZE="2"]ALSA audio with other applications[/SIZE]**

To hear the audio through ALSA using tvtime (or other programs that don't support it directly), run the following command after starting tvtime:
```

arecord -D hw:1,0 -r 32000 -c 2 -f S16_LE | aplay -
```

It basically records at 32kHz Stereo from the SAA7134 ALSA source (hw:1,0 or change accordingly), and plays it through your default ALSA output. Look at the options from aplay to change your output.

There might be a delay between the video and the audio. To avoid it, specify a device for aplay (not the 'default' device):

```
arecord -D hw:1,0 -r 32000 -c 2 -f S16_LE | aplay -D surround41
```

In order to get full surround sound from the stereo TV audio output, edit your /etc/asound.conf or ~/.asoundrc file as described in ALSA FAQ028 ([http://alsa.opensrc.org/FAQ028](http://alsa.opensrc.org/FAQ028)) and use this device:

```
arecord -D hw:1,0 -r 32000 -c 2 -f S16_LE | aplay -D ch51dup
```

I don't know how to use ALSA directly with xawtv, motv, kdtv, tvtime, or zapping; if you do, please add it in here!

If using arecord still causes a delay between the video and the audio, try using sox:

```
sox -r 32000 -w -t alsa hw:1,0 -t alsa hw:0,0
```

Sox might get you mono sound, while all the alsa solutions cause delays. A combination has been known to work:

```
arecord -D hw:1,0 -r 32000 -c 2 -f S16_LE | sox -q -c 2 -r 32000 -w -t wav - -t alsa hw:0,0
```

If sox doesn't have alsa support, you can try this instead:

```
arecord -D hw:1,0 -r 32000 -c 2 -f S16_LE | play -q -c 2 -r 32000 -w -t wav -
```

Alternatively you can use alsa's oss-emulation with sox, which seems to result in way better latency then all the above:
```

sox -q -c 2 -s -w -r 32000 -t ossdsp /dev/dsp1 -t ossdsp -w -r 32000 /dev/dsp
```

---

### Post by studo77 on 2007-10-16
thank you for a good 'how to'

But i get problems...

i had tv input working to see channels, but no sound so went through it all one more time. Now tvtime can't find my card, but dmesg seem to be ok. Here is Dmesg about 7134:
[   38.848217] saa7130/34: v4l2 driver version 0.2.14 loaded
[   38.848282] ACPI: PCI Interrupt 0000:04:07.0[A] -> GSI 22 (level, low) -> IRQ 21
[   38.848290] saa7134[0]: found at 0000:04:07.0, rev: 1, irq: 21, latency: 32, mmio: 0xff5ffc00
[   38.848296] saa7134[0]: subsystem: 1131:0000, board: UNKNOWN/GENERIC [card=0,insmod option]
[   38.848304] saa7134[0]: board init: gpio is 80407f
...
[   39.207547] saa7134[0]: registered device video1 [v4l2]
[   39.207570] saa7134[0]: registered device vbi1
[   39.396772] saa7134 ALSA driver for DMA sound loaded
[   39.396803] saa7134[0]/alsa: saa7134[0] at 0xff5ffc00 irq 21 registered as card 1


TvTime says : no device /dev/video0
that seems ok, because my /etc/modprobe.d/options
is:
```
options saa7134 card=0 tuner=9
```
and /etc/modprobe.d/saa7134:
```
options saa7134 card=0 tuner=9 video_nr=1 vbi_nr=1
install saa7134 /sbin/modprobe --ignore-install saa7134; /sbin/modprobe saa7134-alsa
options saa7134-alsa index=1
```

which tells me that it is video1, but when using 
tvtime-scanner --input=1 it still says
videoinput: Cannot open capture device /dev/video0: No such file or directory

with tvtime-scanner --input=1 -d /dev/video1 it says
No tuner found on input 1.  If you have a tuner, please
    select a different input using --input=<num>.

so is it my tuner i need to edit or card? or is there something else wrong,?

Have tried other cards and tuners, but now everything seems to go black.

[edit] In denmark, so PAL is what i need, also getting cable form TDC(tv-signal-supplier), and card is Zolid ZD-TV7134RF

---

### Post by studo77 on 2007-10-16
ok, got picture again, but still no sound

modprobe.d/options
options saa7134 card=59 tuner=9

modprobe.d/saa7134
#options saa7134 card=43 tuner=10 video_nr=1 vbi_nr=1
install saa7134 /sbin/modprobe --ignore-install saa7134; /sbin/modprobe saa7134-alsa
options saa7134-alsa index=1

dmesg
[   41.191420] saa7130/34: v4l2 driver version 0.2.14 loaded
[   41.191486] ACPI: PCI Interrupt 0000:04:07.0[A] -> GSI 22 (level, low) -> IRQ 21
[   41.191494] saa7134[0]: found at 0000:04:07.0, rev: 1, irq: 21, latency: 32, mmio: 0xff5ffc00
[   41.191500] saa7134[0]: subsystem: 1131:0000, board: Kworld/Tevion V-Stream Xpert TV PVR7134 [card=59,insmod option]
[   41.191508] saa7134[0]: board init: gpio is 80407f
[   41.191592] input: saa7134 IR (Kworld/Tevion V-Str as /class/input/input2
[   41.295387] parport: PnPBIOS parport detected.
[   41.295498] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   41.299243] saa7134[0]: Huh, no eeprom present (err=-5)?
[   41.338524] tuner 1-0060: All bytes are equal. It is not a TEA5767
[   41.338529] tuner 1-0060: chip found @ 0xc0 (saa7134[0])
[   41.338570] tuner 1-0060: type set to 9 (Alps HSBH1)
[   41.338573] tuner 1-0060: type set to 9 (Alps HSBH1)
[   41.340746] saa7134[0]: registered device video0 [v4l2]
[   41.340768] saa7134[0]: registered device vbi0
[   41.340789] saa7134[0]: registered device radio0
.....................
[   41.756532] saa7134 ALSA driver for DMA sound loaded
[   41.756560] saa7134[0]/alsa: saa7134[0] at 0xff5ffc00 irq 21 registered as card 1
...........................
[   42.192908] saa7134 IR (Kworld/Tevion V-Str: unknown key: key=0x03 raw=0x03 down=1


Any help is much appreciated. I think i know, that my problem is what you are trying to do, reroute sound from 7134-card to my soundcard.

---

### Post by studo77 on 2007-10-16
Could it be in my .asoundrc that i need to add a setting?

by now it looks like:
```
pcm.dmix51 {
type dmix
ipc_key 1024
slave {
pcm "hw:0,0"
rate 44100
channels 6
period_time 0
period_size 1024
buffer_time 0
buffer_size 4096
}
}

pcm.20to51 {
type route
slave.pcm surround51
slave.channels 6
ttable.0.0 1
ttable.1.1 1
ttable.0.2 1
ttable.1.3 1
ttable.0.4 0.5
ttable.1.4 0.5
ttable.0.5 0.5
ttable.1.5 0.5
}

pcm.duplex {
type asym
playback.pcm "20to51" #muss als pcm.20to51 definiert sein
capture.pcm "dsnooper"
}

pcm.dmix51{
    type dmix
        ipc_key 1024
        slave{
            pcm "hw:0,0"
                rate 48000
                channels 6
                period_time 0
                period_size 1024
                buffer_time 0
                buffer_size 4096
        }
}

pcm.duplicate{
    type plug
    slave.pcm "dmix51"
    slave.channels 6
    route_policy duplicate
}
```

---

### Post by studo77 on 2007-10-16
Last time posting, been spamming this for long enough:)

saa7134:
options saa7134 card=59 tuner=9 video_nr=0 vbi_nr=1 radio_nr=0
install saa7134 /sbin/modprobe --ignore-install saa7134; /sbin/modprobe saa7134-alsa
options saa7134-alsa index=1

options:
options saa7134 card=59 tuner=9

boots ok, and picture is ok, but still no sound.
So i put a jack from 7134-card-out to line-in.

And i hear static, when watching TV.... CRAP.

Going to comment everything out and see what result i then get... probably the same.

Yeeehaaaaa!!!
Never got the passthrough working, but now using a jack connection. Reason for static, was the wrong audio-standard, so uses PAL-BG and everything is fine. a clutty workaround, but it works. The software solution would have been better.

---

### Post by damir_1105 on 2007-10-17
Great if you solved problem. I use direct connection to, but you can use DMA. I have tried booth versions and for me first is better because DMA can produce delay betwean sound and picture and after some time you get lost sync or even sound. I didn't have these problems but others on this forum had this problem when i try to help with using DMA.

you can see: [http://ubuntuforums.org/showthread.php?p=3515058#post3515058]("http://ubuntuforums.org/showthread.php?p=3515058#post3515058")

---

### Post by Turin Turambar on 2007-11-30
So basically, it's not possible to have the sound in Tvtime without messing with arecord line? :confused:

---

### Post by damir_1105 on 2007-12-01
> **Turin Turambar said:**
> So basically, it's not possible to have the sound in Tvtime without messing with arecord line? :confused:

you have 2 solutions.

1. using card with DMA (arecord, aplay)
2. direct cable connection from tv card to sound card ( same cable witch connect cdrom and soundcard )

---

### Post by Turin Turambar on 2007-12-02
Hvala! :)
I tried mplayer, mythtv, VLC... but I'll stick to tvtime. The easiest  TV program to configure.

This site is also very useful:
[http://gentoo-wiki.com/HARDWARE_saa7134](http://gentoo-wiki.com/HARDWARE_saa7134)

---

### Post by Computer_kid on 2008-01-12
Thanks, this helped a lot.

I found that the mplayer command worked without too much work.

---

### Post by giaka92 on 2008-03-13
Hi, excuse me for my bad english:(

On gusty my pinnacle 300i goes with this comand:
```
tvtime | arecord -D hw:1,0 -r 32000 -c 2 -f S16_LE | sox -q -c 2 -r 32000 -w -t wav - -t alsa hw:0,0

```

But on hardy doesn't go! Where's the problem???
Thanks!:KS

---

### Post by digge on 2008-04-02
Hi

I have  Pinnacle PCTV 300i wich uses this chip. I have been able to get the sound working at all with the help from this thread however always out of sync. So i thought id connect the soundcable between videocard and soundcard and sure enough works good with out tweaking however still out of sync. Problem is the sound is before the video so i was thinking, is there any way at all to have the sound buffer a certain amount of time and have them sync that way? I mean there must be some sort of mixer or somthing able to do that?

My guess is that all this happens as the sound is realtime and the video use an mpeg2 software encoder as far as im aware on these cards, they don't have a hardware encoder. Since you dont want choppy video the encoder probably buffers some and creates the problem.

OT:
Another odity ive noticed is that mythtv in my case doesnt shut of the grabbing from the card so sound continues even if i stop watching tv. But i guess that problem is for another thread.

---

