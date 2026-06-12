---
title: "Alsa not passing S24_3LE"
date: 2011-09-20
forum: Multimedia Software
---

### Post by maxcherry2 on 2011-09-20
[FONT=Calibri][SIZE=3]Hi all, [/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]I am new to Linux in general and new to this Forum. This is my first post so Hi to all.[/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]I am running Ubuntu 11.04 on a small HP server. It is being used to great effect to stream movies via a PS3 and Music using Squeezeplay. [/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]However nothing is ever perfect? [/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]I am trying to play 24/96khz Flac files and they come out all distorted. Flac at 16/44.1 is fine. [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]It is the same result using Squeezplay of VLC player. but if a use [/SIZE][/FONT]
 
```
 
aplay -D hw:1,1 test.wav
Playing WAVE 'test.wav' : Signed 24 bit Little Endian in 3bytes, Rate 96000 Hz, Stereo

```
[FONT=Calibri][SIZE=3]all plays fine. [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]This is my /proc/asound/vard1/stream1 file when using the above and the flac is playing fine.[/SIZE][/FONT]
 
```
 
KingRex technology co.,ltd KingRex UC-192 USB TO Spdif/I2S at usb-0000:00:12.2- : USB Audio #1
 
Playback:
  Status: Running
    Interface = 2
    Altset = 2
    URBs = 3 [ 16 16 16 ]
    Packet Size = 576
    Momentary freq = 96000 Hz (0xc.0000)
  Interface 2
    Altset 1
    Format: S16_LE
    Channels: 2
    Endpoint: 8 OUT (ADAPTIVE)
    Rates: 44100, 48000, 96000, 88200, 176400, 192000
    Data packet interval: 1000 us
  Interface 2
    Altset 2
    Format: S24_3LE
    Channels: 2
    Endpoint: 8 OUT (ADAPTIVE)
    Rates: 44100, 48000, 96000, 88200, 176400, 192000
    Data packet interval: 500 us

```
[FONT=Calibri][SIZE=3]However the same file played using Squeezeplay or VLC player the /proc/asound/vard1/stream1 file looks like this[/SIZE][/FONT]
```
 
KingRex technology co.,ltd KingRex UC-192 USB TO Spdif/I2S at usb-0000:00:12.2- : USB Audio #1
 
Playback:
  Status: Running
    Interface = 2
    Altset = 1
    URBs = 2 [ 5 6 ]
    Packet Size = 768
    Momentary freq = 96000 Hz (0xc.0000)
  Interface 2
    Altset 1
    Format: S16_LE
    Channels: 2
    Endpoint: 8 OUT (ADAPTIVE)
    Rates: 44100, 48000, 96000, 88200, 176400, 192000
    Data packet interval: 1000 us
  Interface 2
    Altset 2
    Format: S24_3LE
    Channels: 2
    Endpoint: 8 OUT (ADAPTIVE)
    Rates: 44100, 48000, 96000, 88200, 176400, 192000
    Data packet interval: 500 us

```
[FONT=Calibri][SIZE=3]So now the file plays ok in VLC and the dac shows 96khz but the output is using Altset 1 and outputting S16_LE [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Under the VLC codec details it shows the output stream as [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Codec: PCM S24LE(araw) [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Channels Stereo [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Sample Rate: 96000 Hz[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Bits per sample: 24 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]And Squeezeplay just sounds wrongs the track is all slow and distorted. [/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]So to recap my usb Spdif works using aplay command but playing same file from a software player the file becomes S16_LE format and not a S24_3LE [/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]At first I thought the problem was Squeezeplay but because it also effects VLC I now think it is Alsa? [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]any help would be very much appreciated, please let me know your thoughts :confused:[/SIZE][/FONT]

---

### Post by BicyclerBoy on 2011-09-21
This is the best guess ..
What happens if you point VLC directly at the hw device

vlc --aout alsa --alsa-audio-device hw:1,1

Maybe the alsa plughw is doing a conversion.

---

### Post by wjamoore on 2011-09-21
Yeah, I'm getting 44.1khz 16 bit output for every file.

Tried various players.  Would like to use decibel, but ti seems it's not the player rather alsa...

Not too happy.  Will be happy if I get a fix.  If Linux cannot do this it will be a showstopper for  my music server,

wjam

---

### Post by wjamoore on 2011-09-21
Hold on!  Breakthrough!!

DeadBeef allows selection of the output plugin and output device.

I chose "Direct Hardware Device without any conversions" on the output device and bingo.  i get the correct sample rate.  However it's saying 32 bit when in fact it's 24...  Not sure if that's just an error or it's doing something to the signal.

Now how do i get Decibel to do this?

wjam

---

### Post by maxcherry2 on 2011-09-21
> **BicyclerBoy said:**
> This is the best guess ..
What happens if you point VLC directly at the hw device
 
vlc --aout alsa --alsa-audio-device hw:1,1
 
Maybe the alsa plughw is doing a conversion.
 
Thanks for your help.
 
I have tried the above and
 
I get this?
 
```
 
 [EMAIL="david@NasBox:~$"]david@NasBox:~$[/EMAIL] vlc --aout alsa --alsa-audio-device hw:1,1
VLC media player 1.1.9 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[[COLOR=lime]0x1383af0[/COLOR]] inhibit interface error:[COLOR=red] Failed to connect to the D-Bus session daemon: //bin/dbus-launch terminated abnormally with the following error: Autolaunch error: X11 initialization failed.[/COLOR]
[[COLOR=lime]0x1383af0[/COLOR]] main interface error: [COLOR=red]no suitable interface module
[/COLOR][[COLOR=lime]0x136a4c0[/COLOR]] main interface error: [COLOR=red]no suitable interface module[/COLOR]
[[COLOR=lime]0x1250120[/COLOR]] main libvlc error: [COLOR=red]interface "globalhotkeys,none" initialization failed
[/COLOR][[COLOR=lime]0x1250120[/COLOR]] main libvlc: [B]Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[/B][[COLOR=lime]0x136a4c0[/COLOR]] qt4 interface error:[COLOR=red] Could not connect to X server[/COLOR]
[[COLOR=lime]0x136a4c0[/COLOR]] skins2 interface error: [COLOR=red]Cannot open display
[/COLOR][[COLOR=lime]0x136a4c0[/COLOR]] skins2 interface error: [COLOR=red]cannot initialize OSFactory
[/COLOR]

```
 
 
Don't know what that means. 
 
Also I have changed my asound.conf file from
 
pmc.! default {
type hw
card 1 
device 1
}
 
to 
 
pmc.! default {
type plughw
card 1
device 1
}
 
[COLOR=black][FONT=Verdana]and that makes no difference. Finally I tried [/FONT][/COLOR]
[COLOR=black][FONT=Verdana][/FONT][/COLOR] 
[COLOR=black][FONT=Verdana][/FONT][/COLOR] 
[COLOR=black][FONT=Verdana][EMAIL="david@NasBox:~/Storage/Squeeze$"][COLOR=black]```
 [/COLOR]
[COLOR=black][FONT=Verdana][/EMAIL][EMAIL="david@NasBox:~/Storage/Squeeze$"][COLOR=black]david@NasBox:~/Storage/Squeeze$[/COLOR][/EMAIL][EMAIL="david@NasBox:~/Storage/Squeeze$"][COLOR=black] aplay -D plughw:1,1 test.wav
Playing WAVE 'test.wav' : Signed 24 bit Little Endian in 3bytes, Rate 96000 Hz, Stereo
[/COLOR][/FONT][/COLOR]
[COLOR=black]
```[/COLOR][/EMAIL]
[COLOR=black][/COLOR] 
[COLOR=black]and the /proc/sound/card1 file looks ok [/COLOR]
 
```
 
KingRex technology co.,ltd KingRex UC-192 USB TO Spdif/I2S at usb-0000:00:12.2- : USB Audio #1
Playback:
  Status: Running
    Interface = 2
    Altset = 2
    URBs = 3 [ 16 16 16 ]
    Packet Size = 576
    Momentary freq = 96000 Hz (0xc.0000)
  Interface 2
    Altset 1
    Format: S16_LE
    Channels: 2
    Endpoint: 8 OUT (ADAPTIVE)
    Rates: 44100, 48000, 96000, 88200, 176400, 192000
    Data packet interval: 1000 us
  Interface 2
    Altset 2
    Format: S24_3LE
    Channels: 2
    Endpoint: 8 OUT (ADAPTIVE)
    Rates: 44100, 48000, 96000, 88200, 176400, 192000
    Data packet interval: 500 us


```
 
which would seem to rule out that plughw is doing any conversion. 
 
What files can I check to see what players uses what output in ALSA is it that easy?
 
I have disabled pulseaudio as that was a requiremnt to get Squzzeplay to work in the first place. 
 
Also is it worth [COLOR=black][FONT=Verdana]mentioning[/FONT][/COLOR] that I am outputting to a USB Spdif which then goes to my Hi-Fi DAC just to be clear that I have no onboard sound device. ):P
 
[/FONT][/COLOR]

---

### Post by BicyclerBoy on 2011-09-21
I do understand your audio arrangements but that's of little help.
You do realize that most mobo audio can support S/PDIF 96KHz 24 bit stereo.
It's the reclocking that is important & that optical/toslink is worse than coaxial.

Your vlc errors looks like X server screen was not active.
Did you run from console terminal login ?

aplay -l

There could be a bug in the alsa code support for your USB codec..
Your conclusions are based on the assumption that the /proc-file-system info is correct.

---

### Post by maxcherry2 on 2011-09-21
> **BicyclerBoy said:**
> I do understand your audio arrangements but that's of little help.
You do realize that most mobo audio can support S/PDIF 96KHz 24 bit stereo.
It's the reclocking that is important & that optical/toslink is worse than coaxial.
 
Your vlc errors looks like X server screen was not active.
Did you run from console terminal login ?
 
aplay -l
 
There could be a bug in the alsa code support for your USB codec..
Your conclusions are based on the assumption that the /proc-file-system info is correct.
 
[FONT=Calibri][SIZE=3]Yes you are right I am assuming a lot. Being new to Linux I am clutching at straws I didn't even know there was a difference running over putty or from the terminal. I do know thanks for that pointer. [/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]Running your command over console terminal produced this[/SIZE][/FONT]
 
```
 
david@NasBox:~$ vlc --aout alsa --alsa-audio-device hw:1,1
VLC media player 1.1.9 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0x153d120] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Blocked: call to setlocale(6, "")
Warning: call to srand(1316686558)
Warning: call to rand()
Blocked: call to setlocale(6, "")
 
(process:4736): Gtk-WARNING **: Locale not supported by C library.
                Using the fallback 'C' locale.
Warning: call to rand()
Warning: call to rand()
Warning: call to rand()
Warning: call to rand()

```
[FONT=Calibri][SIZE=3]VLC did fire [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]up and play the file as before 16/96 not 24/96 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3][/SIZE][/FONT] 
[SIZE=3][FONT=Times New Roman]entering [/FONT][/SIZE][COLOR=black][FONT=Verdana]aplay -l [/FONT][/COLOR][SIZE=3][FONT=Times New Roman]gives[/FONT][/SIZE]
 
 
```

[FONT=Verdana][COLOR=black][COLOR=black][FONT=Verdana]david@NasBox:~$  aplay -l[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]**** List of PLAYBACK Hardware Devices ****[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]card 1: SpdifI2S [KingRex UC-192 USB TO Spdif/I2S], device 0: USB Audio [USB Audio][/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Subdevices: 1/1[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Subdevice #0: subdevice #0[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]card 1: SpdifI2S [KingRex UC-192 USB TO Spdif/I2S], device 1: USB Audio [USB Audio #1][/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Subdevices: 1/1[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Subdevice #0: subdevice #0[/FONT][/COLOR]
 
[/COLOR][/FONT]
```
 
 
Thanks for your advice so far what should I do next.:(

---

### Post by BicyclerBoy on 2011-09-21
Using clementine & card0 mobo S/PDIF:

If I select audio sink (alsa) & iec958, it plays 92KHz/24bit correctly but 192KHz/24bit is silent.

vlc --aout alsa --alsa-audio-device iec958
works correctly with 92KHz/24bit, fails to start with 192KHz/24.

I note that:
VLC 1.0.6 could not play the whole 6 min track..
Clementine was perfect
The functionality matches the input capabilities of the HT amp.
The mobo soundcard is good for 192/24.

Can you try the above VLC cmd ?

Could check out --spdif --aout-rate --no-hq-resampling

---

### Post by BicyclerBoy on 2011-09-21
Take it all back...
Playback of 96KHz/24bit in clementine via iec958

cat /proc/asound/card0/pcm1p/sub0/hw_params
shows output is S16_LE  2 channel 96KHz.

speaker-test -c 2 -r 96000 -D iec958 -F S32_LE
cat /proc/asound/card0/pcm1p/sub0/hw_params
shows output is S32_LE  2 channel 96KHz & pink noise is heard.

speaker-test 1.0.24 does not have the option S24_3LE with my h/w.

VLC 1.0.6  gives 48K/32bit or 96K/16bit from 96K/24bit media.

But with this in /etc/asound.conf the spdif is 32 bit & 96KHz !
```

# force 32 bit spdif
pcm.!iec958 {
  type plug
  slave {
    pcm "hw:0,1"
    format S32_LE
  }
}

```
But is this really 24 bit from the player to the amp or just converted by alsa ?


[http://web.archiveorange.com/archive/v/bFtHWj7CgIYq9AxKTuoh](http://web.archiveorange.com/archive/v/bFtHWj7CgIYq9AxKTuoh)
[http://www.spinics.net/linux/fedora/alsa-user/msg10193.html](http://www.spinics.net/linux/fedora/alsa-user/msg10193.html)

---

### Post by maxcherry2 on 2011-09-22
Hi,

I did  vlc --aout alsa --alsa-audio-device iec958 in console and got this

```
david@NasBox:~/Storage/Squeeze$ vlc --aout alsa --alsa-audio-device iec958
VLC media player 1.1.9 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0x2202120] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Blocked: call to setlocale(6, "")
Warning: call to srand(1316743073)
Warning: call to rand()
Blocked: call to setlocale(6, "")

(process:2206): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.
Warning: call to rand()
Warning: call to rand()
Warning: call to rand()
Warning: call to rand()
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'
ALSA lib conf.c:4184:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:4184:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:4184:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:4663:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM iec958
[0x2a17270] oss audio output error: cannot open audio device (/dev/dsp)
```

No sound.

Then did vlc --spdif --aout-rate --no-hq-resampling


```
david@NasBox:~/Storage/Squeeze$ vlc --spdif --aout-rate --no-hq-resampling
VLC media player 1.1.9 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0x2560120] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Blocked: call to setlocale(6, "")
Warning: call to srand(1316073423)
Warning: call to rand()
Blocked: call to setlocale(6, "")

(process:2317): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.
Warning: call to rand()
Warning: call to rand()
Warning: call to rand()
Warning: call to rand()

```

cat /proc/asound/card0/pcm1p/sub0/hw_params looked like this


```
david@NasBox:~/Storage/Squeeze$ cat /proc/asound/card1/pcm1p/sub0/hw_params
access: RW_INTERLEAVED
format: S16_LE
subformat: STD
channels: 2
rate: 96000 (96000/1)
period_size: 1024
buffer_size: 262144

```

then I tried changing the asound.conf

pcm.!iec958 {   type plug   slave {     pcm "hw:0,1"     format S32_LE   } }
got the same sample rate.

changed to think it might force the right sample rate 
pcm.!iec958 {   type plug   slave {     pcm "hw:0,1"     format S24_3LE   } }

 tried aplay -D hw:1,1 test.wav

and got white noise?

reset the asound.conf back to 

```
pcm.!default {
type hw
card 1
device 1
}
ctl.!default {
type hw
card 1
device 1
}
```

back to  aplay -D hw:1,1 test.wav

cat /proc/asound/card1/pcm1p/sub0/hw_params

```
access: RW_INTERLEAVED
format: S24_3LE
subformat: STD
channels: 2
rate: 96000 (96000/1)
period_size: 12000
buffer_size: 48000

```

played file in VLC still 16bit


so this shows me the hardware supports the Flac format so it must be software. That is my guess.....

Is there anything esle I can try ALSA reinstall?

Or any other system information I could post to work through the problem

Thanks David.

---

### Post by .... on 2011-09-22
Are you running pulseaudio? It seems like whenever you try to play anything without playing directly to the ALSA device, it gets resampled.

Note that 24-bit data might be zero-padded to 32-bit if it makes it easier for the hardware.

---

### Post by maxcherry2 on 2011-09-22
Also just tried
 
[EMAIL="david@NasBox:~/Storage/Squeeze$"][COLOR=black]```
 [/COLOR]
[/EMAIL][EMAIL="david@NasBox:~/Storage/Squeeze$"][COLOR=black]david@NasBox:~/Storage/Squeeze$[/COLOR][/EMAIL][EMAIL="david@NasBox:~/Storage/Squeeze$"][COLOR=black]  aplay  -D hw:1,1 -f S32_LE test.wav
Warning: format has changed to S24_3LE
Playing WAVE 'test.wav' : Signed 24 bit Little Endian in 3bytes, Rate 96000 Hz,         Stereo
[/COLOR]
[COLOR=black] [/COLOR]
[COLOR=black]
```[/COLOR][/EMAIL]
 
and 
[COLOR=black][/COLOR] 
[EMAIL="david@NasBox:~/Storage/Squeeze$"][COLOR=black]```
 [/COLOR]
[/EMAIL][EMAIL="david@NasBox:~/Storage/Squeeze$"][COLOR=black]david@NasBox:~/Storage/Squeeze$[/COLOR][/EMAIL][EMAIL="david@NasBox:~/Storage/Squeeze$"][COLOR=black] aplay -D hw:1,1 -f S16_LE test.wav
Warning: format has changed to S24_3LE
Playing WAVE 'test.wav' : Signed 24 bit Little Endian in 3bytes, Rate 96000 Hz,         Stereo
[/COLOR]
[COLOR=black]
```[/COLOR][/EMAIL]
 
both times format changed to S24_3LE? and confrimed by 
the /proc/asound/card1//pcm1p/sub0/hw_params
 
```
 
access: RW_INTERLEAVED
format: S24_3LE
subformat: STD
channels: 2
rate: 96000 (96000/1)
period_size 12000
buffer_size 48000

```
 
I thought the -f switch would force the bit rate....
 
not sure if any of that helps?

---

### Post by BicyclerBoy on 2011-09-22
I did not mean to imply you should use S32_LE in the asound.conf iec958.
Or on the speaker-test cmd line.

The cmd line options for VLC were just for research not direct copy..

As I said before my h/w driver did not allow S24_3LE.
Your h/w driver does not support 32bit.
AFAIK All 24bit S/PDIF is sent as padded 32bits.

You have tried overwriting iec958 (!iec958) with a new definition with S24_3LE bu tit was pointing at hw:0,1.

speaker-test with S24_3LE works (pink noise).

Don't run GUI VLC in a console or some remote terminal (it's a X screen app), run the ncurses interface.

You should check your /proc/../stream files as previous..I don't have those files.

It makes more sense if you do not redefine iec958 but use a new name like
iec958_24.

With the iec958_24 in place with S24_3LE
```

# force 24 bit spdif
pcm.iec958_24 {
  type plug
  slave {
    pcm "hw:1,1"
    format S24_3LE
  }
} 

```

Then try
speaker-test -c2 -r 96000 -D iec958_24
Check the proc/../pcmXp & streamX files

But after all this, I am still not convinced that 24 bit audio is being passed from player. The player should be checking the capability of the output device but I don't trust the consumer sound media players.
Maybe need to try
[http://www.signalyst.com/consumer.html](http://www.signalyst.com/consumer.html)

The only way I can check for real 24 bit is to build some S/PDIF snooping device or use a digital storage oscilloscope.

---

### Post by maxcherry2 on 2011-09-22
> **.... said:**
> Are you running pulseaudio? It seems like whenever you try to play anything without playing directly to the ALSA device, it gets resampled.
 
Note that 24-bit data might be zero-padded to 32-bit if it makes it easier for the hardware.
 
Hi,
 
pulseaudio is disabled as Squeezeplay wont play with it running.
 
David.

---

### Post by maxcherry2 on 2011-09-22
Not sure what you mean or how to do that.

VLC GUI opens when I enter vlc --aout alsa --alsa-audio-device hw:1,1

Don't run GUI VLC in a console or some remote terminal (it's a X screen app), run the ncurses interface.

Sorry about the confusion from my end. This Linux is a step learning curve!

Ok changed asound.conf to


pcm.iec958_24 {
 type plug   
 slave { 
      pcm "hw:1,1"     
    format S24_3LE 
   } 
}

then did speaker-test -c2 -r 96000 -D iec958_24

```
david@NasBox:~$ speaker-test -c2 -r 96000 -D iec958_24

speaker-test 1.0.24.2

Playback device is iec958_24
Stream parameters are 96000Hz, S16_LE, 2 channels
Using 16 octaves of pink noise
Rate set to 96000Hz (requested 96000Hz)
Buffer size range from 96 to 174762
Period size range from 48 to 87381
Using max buffer size 174760
Periods = 4
was set period_size = 43690
was set buffer_size = 174760
 0 - Front Left
 1 - Front Right

```got white noise.

 /proc/asound/card1/stream1 

```
KingRex technology co.,ltd KingRex UC-192 USB TO Spdif/I2S at usb-0000:00:12.2- : USB Audio #1

Playback:
  Status: Running
    Interface = 2
    Altset = 2
    URBs = 3 [ 16 16 16 ]
    Packet Size = 576
    Momentary freq = 96000 Hz (0xc.0000)
  Interface 2
    Altset 1
    Format: S16_LE
    Channels: 2
    Endpoint: 8 OUT (ADAPTIVE)
    Rates: 44100, 48000, 96000, 88200, 176400, 192000
    Data packet interval: 1000 us
  Interface 2
    Altset 2
    Format: S24_3LE
    Channels: 2
    Endpoint: 8 OUT (ADAPTIVE)
    Rates: 44100, 48000, 96000, 88200, 176400, 192000
    Data packet interval: 500 us

```/proc/asound/card1/pcm1p/sub0/hw_params

```
access: MMAP_INTERLEAVED
format: S24_3LE
subformat: STD
channels: 2
rate: 96000 (96000/1)
period_size: 43690
buffer_size: 174760



```/proc/asound/card1/pcm1p/info

```
card: 1
device: 1
subdevice: 0
stream: PLAYBACK
id: USB Audio
name: USB Audio #1
subname: subdevice #0
class: 0
subclass: 0
subdevices_count: 1
subdevices_avail: 0

```/proc/asound/card1/usbmixer

```
USB Mixer: usb_id=0x040d3410, ctrlif=0, ctlerr=0
Card: KingRex technology co.,ltd KingRex UC-192 USB TO Spdif/I2S at usb-0000:00:12.2-
  Unit: 12
    Control: name="Speaker Playback Volume", index=0
    Info: id=12, control=2, cmask=0x3, channels=2, type="S16"
    Volume: min=-10240, max=0, dBmin=-4000, dBmax=0
  Unit: 12
    Control: name="Speaker Playback Switch", index=0
    Info: id=12, control=1, cmask=0x0, channels=1, type="INV_BOOLEAN"
    Volume: min=0, max=1, dBmin=0, dBmax=0
  Unit: 20
    Control: name="IEC958 In Playback Switch", index=0
    Info: id=20, control=1, cmask=0x0, channels=1, type="INV_BOOLEAN"
    Volume: min=0, max=1, dBmin=0, dBmax=0
```what I don't get is that speaker test shows

Stream parameters are 96000Hz, S16_LE, 2 channels
Using 16 octaves of pink noise
Rate set to 96000Hz (requested 96000Hz)

indicating 16bit  but /proc/asound/card1/stream1

shows   Interface = 2
           Altset = 2

which indicates the steam is 24_3LE is that not 24 bit. 

Am I just not understanding the bit rates being streamed is 24_3LE not 24bit?

Thanks

David.

---

### Post by maxcherry2 on 2011-09-22
ok.
 
Now after checking Squeezeplay It does not stream 
 
I have had to change my asound back 
 
```
 
pcm.usbdac {
type hw;
card 1;
device 1;
}
 
 
ctl.plugusb {
type hw;
card 1;
device 1;
}
pcm.!default usbdac

```
 
for it to play music of any type. Not sure why that is, must be to do with the default output in Squeezeplay Server?
 
The thing with Squeeze is that I can use my Tablet or Andriod phone as a remote so can just run the server headless (well still desktop but no screen or keyboard and hidden away)
 
other players don't offer this....
 
David.

---

### Post by BicyclerBoy on 2011-09-22
I think that speaker-test does not understand/allow S24_3LE.
If you run speaker-test with no options, it lists the allowed formats. I do not have S24_3LE.

Can you craft a asound.conf with
defaults.pcm.rate_converter "samplerate_best"
and
format S24_3LE 
rate 96000
in your pcm.usbdac {--}
You need to install libsample for the alsa rate converter.
This uses the high quality resampler..uses lots of CPU (1/2 core2duo).

You can have all of the definitions (usbdac, iec958_24 etc) together in the asound.conf file, they do not interact except you can not share the hw:1,1 with multiple apps.

usbdac is just an alias for hw:1,1.

---

