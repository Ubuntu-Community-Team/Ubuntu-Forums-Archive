---
title: "Speed Link Pure Voice SL-8708 USB Microphone not working"
date: 2008-07-08
forum: Multimedia Software
---

### Post by samuraiche on 2008-07-08
Hi,
I have to microphones: one integrated in my laptop and another,new usb microphone.Capturing with the integrated mic works fine,no prob. But I cant get my USB mic to work.Trying to get this microphone to work I've done many things,but still no result.
This is a short summary to show what i've already tried.

First of all to see if the snd_usb_audio I ran:**lsmod |grep snd**
```

snd_hda_intel         344728  2 
snd_seq_dummy           4868  0 
snd_usb_audio          83936  2 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  3 snd_hda_intel,snd_usb_audio,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_usb_lib            18432  1 snd_usb_audio
snd_seq_oss            35584  0 
snd_hwdep              10500  2 snd_hda_intel,snd_usb_audio
snd_seq_midi            9376  0 
snd_rawmidi            25760  2 snd_usb_lib,snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56996  21 snd_hda_intel,snd_seq_dummy,snd_usb_audio,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_usb_lib,snd_seq_oss,snd_hwdep,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
usbcore               146028  9 r5u870,usbcam,uvcvideo,**snd_usb_audio,snd_usb_lib**,usbhid,ehci_hcd,uhci_hcd

```

snd_usb_audio,snd_usb_lib are loaded,so it's all right :)

Then to see if the usb mic was recognized:**cat /proc/asound/cards**

 ```
0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xd8240000 irq 22
 1 [default        ]: USB-Audio - C-Media USB Headphone Set  
                      C-Media USB Headphone Set   at usb-0000:00:1d.0-2, full speed
```
So,it's ok too.

Now wanna see which device number has been given to the usb mic:
**arecord --list-devices **
```
**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: default [C-Media USB Headphone Set  ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

and **cat /proc/asound/pcm**:

```
01-00: USB Audio : USB Audio : playback 1 : capture 1
00-01: Conexant Digital : Conexant Digital : playback 1
00-00: CONEXANT Analog : CONEXANT Analog : playback 1 : capture 1

```


**amixer -c 1** gives:

```
elephant@africa:~$ amixer -c 1
Simple mixer control 'Mic',0
  Capabilities: pvolume pvolume-joined cvolume pswitch pswitch-joined cswitch cswitch-joined
  Playback channels: Mono
  Capture channels: Mono
  Limits: Playback 0 - 32 Capture 0 - 16
  Mono: Playback 31 [97%] [46.50dB] [on] Capture 15 [94%] [22.50dB] [on]
Simple mixer control 'Auto Gain Control',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Speaker',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 151
  Mono:
  Front Left: Playback 150 [99%] [-1.37dB] [on]
  Front Right: Playback 150 [99%] [-1.37dB] [on]
```

But when trying to record smthng with **arecord -f cd -D [COLOR="Red"]hw:1,0 [/COLOR]-d 5 test.wav **
Get this message:
> Recording WAVE 'test.wav' : Signed 16 bit Little Endian, Rate 44100 Hz, Stereo
arecord: set_params:906: Channels count non available

But if I change the card to my intel then it runs: **arecord -f cd -D [COLOR="Red"]hw:0,0[/COLOR] -d 20 test.wav**

I also tried to change default capture device in System>Preferences>Sound,
but if I set it to USB Audio and click on "Test" I get:
```
gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Could not open audio device for recording.
```

I tried everything I could,so may be there is someone who had the same issue and could solve it?

Thanx :)

Update:

I have noticed that when I run **arecord -f cd -D "hw:1,0" -c1 -d 20 test.wav** with my usb mic turned off and during the record turn it on, i get my voice recorded for about a second.

---

### Post by samuraiche on 2008-07-13
somebody?

---

