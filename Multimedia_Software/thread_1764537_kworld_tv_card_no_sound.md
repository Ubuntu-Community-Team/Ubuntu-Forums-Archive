---
title: "kworld tv card no sound"
date: 2011-05-21
forum: Multimedia Software
---

### Post by dozycat on 2011-05-21
I am installing an:
pvr-tv 7134se
Thats a tv card of kworld.

It is ubuntu 11.04 64 bits.

I got the video tuner working with tvtime doing the following steps:


sudo gedit /etc/modprobe.d/saa7134   
  
and inside:
  
options saa7134 i2c_scan=1 

And Tvtime gets the image of the channels but no sound.

I followed this:

[http://ubuntuforums.org/showthread.php?t=876719&highlight=kworld](http://ubuntuforums.org/showthread.php?t=876719&highlight=kworld)

lspci | grep SAA
07:01.0 Multimedia controller: Philips Semiconductors SAA7134/SAA7135HL Video Broadcast Decoder (rev 01)

 LANG=C pactl list | grep -A2 alsa
    Name: module-alsa-card
    Argument: device_id="0" name="pci-0000_00_1b.0" card_name="alsa_card.pci-0000_00_1b.0" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1"
    Usage counter: 1
    Properties:
--
    Name: module-alsa-card
    Argument: device_id="1" name="pci-0000_07_01.0" card_name="alsa_card.pci-0000_07_01.0" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1"
    Usage counter: 1
    Properties:
--
    Argument: source=alsa_input.pci-0000_07_01.0.analog-stereo
    Usage counter: n/a
    Properties:
--
    Name: alsa_output.pci-0000_00_1b.0.hdmi-stereo
    Description: Internal Audio Digital Stereo (HDMI)
    Driver: module-alsa-card.c
    Sample Specification: s16le 2ch 44100Hz
    Channel Map: front-left,front-right
--
    Monitor Source: alsa_output.pci-0000_00_1b.0.hdmi-stereo.monitor
    Latency: 59329 usec, configured 66666 usec
    Flags: HARDWARE DECIBEL_VOLUME LATENCY 
--
        alsa.resolution_bits = "16"
        device.api = "alsa"
        device.class = "sound"
        alsa.class = "generic"
        alsa.subclass = "generic-mix"
        alsa.name = "HDMI 0"
        alsa.id = "HDMI 0"
        alsa.subdevice = "0"
        alsa.subdevice_name = "subdevice #0"
        alsa.device = "3"
        alsa.card = "0"
        alsa.card_name = "HDA Intel PCH"
        alsa.long_card_name = "HDA Intel PCH at 0xfe700000 irq 53"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:00:1b.0"
        sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card0"
--
        alsa.mixer_name = "Intel CougarPoint HDMI"
        alsa.components = "HDA:10ec0892,1043841b,00100302 HDA:80862805,80862805,00100000"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
--
    Name: alsa_output.pci-0000_00_1b.0.hdmi-stereo.monitor
    Description: Monitor of Internal Audio Digital Stereo (HDMI)
    Driver: module-alsa-card.c
    Sample Specification: s16le 2ch 44100Hz
    Channel Map: front-left,front-right
--
    Monitor of Sink: alsa_output.pci-0000_00_1b.0.hdmi-stereo
    Latency: 0 usec, configured 1999818 usec
    Flags: DECIBEL_VOLUME LATENCY 
--
        alsa.card = "0"
        alsa.card_name = "HDA Intel PCH"
        alsa.long_card_name = "HDA Intel PCH at 0xfe700000 irq 53"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:00:1b.0"
        sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card0"
--
    Name: alsa_input.pci-0000_07_01.0.analog-stereo
    Description: SAA7134/SAA7135HL Video Broadcast Decoder Analog Stereo
    Driver: module-alsa-card.c
    Sample Specification: s16le 2ch 32000Hz
    Channel Map: front-left,front-right
--
        alsa.resolution_bits = "16"
        device.api = "alsa"
        device.class = "sound"
        alsa.class = "generic"
        alsa.subclass = "generic-mix"
        alsa.name = "SAA7134 PCM"
        alsa.id = "SAA7134 PCM"
        alsa.subdevice = "0"
        alsa.subdevice_name = "subdevice #0"
        alsa.device = "0"
        alsa.card = "1"
        alsa.card_name = "SAA7134"
        alsa.long_card_name = "saa7134[0] at 0xfe400000 irq 16"
        alsa.driver_name = "saa7134"
        device.bus_path = "pci-0000:07:01.0"
        sysfs.path = "/devices/pci0000:00/0000:00:1c.7/0000:06:00.0/0000:07:01.0/sound/card1"
--
        alsa.mixer_name = "SAA7134 Mixer"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
--
    Name: alsa_card.pci-0000_00_1b.0
    Driver: module-alsa-card.c
    Owner Module: 4
    Properties:
        alsa.card = "0"
        alsa.card_name = "HDA Intel PCH"
        alsa.long_card_name = "HDA Intel PCH at 0xfe700000 irq 53"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:00:1b.0"
        sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card0"
--
    Name: alsa_card.pci-0000_07_01.0
    Driver: module-alsa-card.c
    Owner Module: 5
    Properties:
        alsa.card = "1"
        alsa.card_name = "SAA7134"
        alsa.long_card_name = "saa7134[0] at 0xfe400000 irq 16"
        alsa.driver_name = "saa7134"
        device.bus_path = "pci-0000:07:01.0"
        sysfs.path = "/devices/pci0000:00/0000:00:1c.7/0000:06:00.0/0000:07:01.0/sound/card1"

So I added the the following line to the end of [FONT=Lucida Console]/etc/pulse/default.pa:

load-module module-loopback source=alsa_input.pci-0000_07_01.0.analog-stereo

Inside of [/FONT][FONT=Lucida Console]/etc/tvtime/tvtime.xml [/FONT][FONT=Lucida Console]Changed the option:

[/FONT][FONT=Lucida Console]<option name="MixerDevice" value="hw:0/PCM"/>

reboot but no sound.
[/FONT][FONT=Lucida Console]



[/FONT]

---

### Post by dozycat on 2011-05-22
tvtime now works.
The solution was to  open sound preferences in desktop, go to input,:
select sa7134se
unmute
and is ready.

Now I need help choosing software for recording tv from cable, only one channel.

I am trying mythtv but still I can't configure to detect the channels.

---

### Post by dozycat on 2011-05-22
Some advance, maybe some can use it:
   ```
 mplayer tv:// -tv driver=v4l2:norm=NTSC:input=0:amode=1:width=720:height=480
 :outfmt=yuy2:device=/dev/video0:chanlist=us-bcast:channel=3
```

another player of tv

---

### Post by dozycat on 2011-05-22
on mythtv I cannot watch tv, it  starts watch tv option and after sometime exits.

the log of frontend is:

```
tail -f /var/log/mythtv/mythfrontend.log 
2011-05-22 08:23:32.954 Using protocol version 63
2011-05-22 08:23:33.068 Spawning LiveTV Recorder -- begin
2011-05-22 08:23:33.422 Spawning LiveTV Recorder -- end
2011-05-22 08:23:33.426 We have a playbackURL(/var/lib/mythtv/livetv/1003_20110522082333.nuv) & cardtype(DUMMY)
2011-05-22 08:23:33.426 We have a RingBuffer
2011-05-22 08:23:33.427 TV Error: LiveTV not successfully started
2011-05-22 08:23:33.427 ScreenSaverX11Private: DPMS Reactivated 1
2011-05-22 08:23:33.428 ScreenSaverX11Private: DPMS Deactivated 1
2011-05-22 08:27:54.529 Deleting UPnP client...
2011-05-22 08:27:55.429 ScreenSaverX11Private: DPMS Reactivated 1



```the mythtvbackend:

```
2011-05-22 09:27:52.440 adding: lawrence-System-Product-Name as a client (events: 0)
2011-05-22 09:27:52.487 TVRec(1): Changing from None to WatchingLiveTV
2011-05-22 09:27:52.532 TVRec(1): HW Tuner: 1->1
2011-05-22 09:27:52.615 format_to_mode() does not recognize V4L1
2011-05-22 09:27:52.654 LoadFromScheduler(): Error, called from backend.
2011-05-22 09:27:52.656 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2011-05-22 09:27:52.834 TVRec(1): Changing from WatchingLiveTV to None
2011-05-22 09:30:46.412 Expiring 0 MB for 1003 at 2011-05-22T09:27:41 => Unknown
2011-05-22 09:30:46.465 Expiring 0 MB for 1003 at 2011-05-22T09:27:42 => Unknown
2011-05-22 09:30:46.510 Expiring 0 MB for 1003 at 2011-05-22T09:27:52 => Unknown


```I check the directories of myth and they have the right permissions.

---

### Post by dozycat on 2011-05-22
It looks like an error of ubuntu 11.04:

2011-05-22 09:42:45.888 format_to_mode() does not recognize V4L1

there is no support for v4l1

---

### Post by dozycat on 2011-05-22
I checked with mythtv and it says the kernel of ubuntu 11.04 is not yet supported.
Anyone knows what other software to use?

---

### Post by dozycat on 2011-05-22
And know I need help tvtime has long delay for the sound.

---

### Post by dozycat on 2011-05-23
I did research and found two things:

1.	V4L1 is not supported, it has been replaced by V4L2, and mythtv is not yet using V4L2.
2.	Pulseaudio is not working well in 11.04, is beibg replaced. And unlucky for me my card 7134SE works by pulseaudio.

So unless someone has any ideas about how record from this card, is time to go multiboot with xp for a while.

And hope a future mythtv development will work this card.

---

### Post by dozycat on 2011-05-24
success.

If someone is interested I give the solution.

Forget about the solution for sound who goes around about pulse audio.

Do not modify the file /etc/pulse/default.pa. 

Tvline works with:
```

tvtime | arecord -D hw:1,0 -r 32000 -c 2 -f S16_LE | aplay - +

```
And for recording:
```

mencoder tv:// -tv driver=v4l2:norm=NTSC:fps=25:outfmt=yuy2:quality=0:input=0:width=720:height=578:chanlist=us-bcast:volume=80:amode=1:normid=0:audiorate=32000:alsa:adevice=hw.1:channel=3 -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=1500:keyint=25 -oac mp3lame -lameopts cbr:br=128:mode=0 -endpos 00:01:00 -vf pp=hb/vb/dr/al/lb,denoise3d -o videocap.avi

```

---

