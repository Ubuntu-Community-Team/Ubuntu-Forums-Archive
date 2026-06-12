---
title: "It is possible full Audio 5.1 with ALSA for VIA - AC97 ???"
date: 2010-08-20
forum: Multimedia Software
---

### Post by LarsUb on 2010-08-20
Hi folks,
I'm just a little newbie with ubuntu, i just left windoze.. hehe, i have  set up all the programs and hardware i need, but i still having an issue  with SOUND. This is the stage.

I have a Mobo MSI K8 series, with integrated sound VIA 3059 chip Realtek  ALC655 using codec AC97 (this integrated audio has 3 audio connectors:  blue, green and pink), im running Ubuntu Lucid 10.04, and i'm using a  Logitech X530 5.1 audio system (this system has 3 audio connectors:  black, green and orange) - i just replaced my old pair of simple 2004  speakers :(

The issues is: When i installed ubuntu I was running Pulseaudio mixer  with an OLD pair of speakers and everything was working OK. Then, i  connected the new X530 speakers (with its corresponding plugs/connection  and colors), and i could hear a very improved sound but with a **very  annoying little noise** like a tinny buzz or vibration, not so  perceptible at begginig but in 5 minutes my ears were hurted, so i  though those noise was going to turn me deaf.

Well, i thought the speakers were damaged, so i switched to windoze to  try them with the audio drivers and codecs there, and amazingly the  speakers sounded like heaven, so i discarded a damage.  Then, i just  came back to Ubuntu, and tried with other mixers and found that just  with Pulseaudio the annoying noise was present, and since Pulseaudio was  the default mixer used by all applications like VLC, MeTV and others,  they had the annoying noise as well. At that point i decided to remove  Pulseaudio and reinstall, but that didn't work.

So i removed Pulseaudio again and re-setup ALSA mixer instead of. So now  im using ALSA and the annoying noise has gone from all applications :) the audio now sounds good in any application but.... **i just can hear sound from 3 speakers, the  Front-left, Front-right and Subwoofer**.  If i try to set the  Output-plugin setting to Surround5.1 in the Audacious audio preferences  it just give me this error:[INDENT]ALSA error, snd_pcm_hw_params_set_rate failed: Invalid  argument  :(
[/INDENT]I've tried to adjust some basic settings with the Alsamixer gui applet  but nothing makes a reference to my 5.1 sound system. I've been googling  for a solution but without specific results, i read something like Alsa cannot do multichannel but i'm not sure. Therefore my question is:

**How can i correctly setup my 5.1 speakers system with ALSA mixer and  my mobo-integrated sound VIA with realtek ALC655 and AC97 codec??**,  in order to make sound all my 6 speakers (2front, 2rear, 1central,  1subw).

Some output commands for workaround from my ub are:
    $ uname -a[INDENT][SIZE=1]Linux hellhound 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11  07:54:58 UTC 2010 i686 GNU/Linux[/SIZE]
[/INDENT]$ cat /proc/asound/version[INDENT][SIZE=1]Advanced Linux Sound Architecture Driver Version 1.0.21.[/SIZE]
[/INDENT]$ head -l /proc/asound/card0/codec97#0/ac97#0-0[INDENT][SIZE=1]0-0/0: Realtek ALC655 rev 0
PCI Subsys Vendor: 0x1462
PCI Subsys Device: 0x0080
Flags: 0
Revision         : 0x00
Compat. Class    : 0x00
Subsys. Vendor ID: 0xffff
Subsys. ID       : 0xffff[/SIZE]
[/INDENT]$ lspci | grep audio[INDENT][SIZE=1]00:11.5 Multimedia audio controller: VIA Technologies, Inc.  VT8233/A/8235/8237 AC97 Audio Controller (rev 60)[/SIZE]
[/INDENT]$ aplay -l[INDENT][SIZE=1]**** List of PLAYBACK Hardware Devices ****
card 0: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 3/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0[/SIZE]
[/INDENT]$ aplay -L[INDENT][SIZE=1]null
    Discard all samples (playback) or generate zero samples (capture)
default:CARD=V8237
    VIA 8237, VIA 8237
    Default Audio Device
front:CARD=V8237,DEV=0
    VIA 8237, VIA 8237
    Front speakers
surround40:CARD=V8237,DEV=0
    VIA 8237, VIA 8237
    4.0 Surround output to Front and Rear speakers
surround41:CARD=V8237,DEV=0
    VIA 8237, VIA 8237
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=V8237,DEV=0
    VIA 8237, VIA 8237
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=V8237,DEV=0
    VIA 8237, VIA 8237
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
iec958:CARD=V8237,DEV=0
    VIA 8237, VIA 8237
    IEC958 (S/PDIF) Digital Audio Output[/SIZE]
[/INDENT]$ lsmod | grep snd[INDENT][SIZE=1]snd_via82xx            20058  2 
gameport                9089  1 snd_via82xx
snd_ac97_codec        100646  1 snd_via82xx
ac97_bus                1002  1 snd_ac97_codec
snd_usb_audio          75765  0 
snd_pcm_oss            35308  1 
snd_usb_lib            15801  1 snd_usb_audio
snd_hwdep               5412  1 snd_usb_audio
snd_mixer_oss          13746  2 snd_pcm_oss
snd_seq_dummy           1338  0 
snd_pcm                70662  4  snd_via82xx,snd_ac97_codec,snd_usb_audio,snd_pcm_oss
snd_page_alloc          7076  2 snd_via82xx,snd_pcm
snd_mpu401_uart         5617  1 snd_via82xx
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  3 snd_usb_lib,snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6  snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5  snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54148  13  snd_via82xx,snd_ac97_codec,snd_usb_audio,snd_pcm_oss,snd_hwdep,snd_mixer_oss,snd_pcm,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               6620  3 snd[/SIZE]
[/INDENT]$ speaker-test -D surround51 -c 6[INDENT][SIZE=1]speaker-test 1.0.22
Playback device is surround51
Stream parameters are 48000Hz, S16_LE, 6 channels
Using 16 octaves of pink noise
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 6 to 5461
Period size range from 3 to 2730
Using max buffer size 5460
Periods = 4
was set period_size = 1365
was set buffer_size = 5460
 0 - Front Left
 4 - Center
 1 - Front Right
 3 - Rear Right
 2 - Rear Left
 5 - LFE
Time per period = 17.799935[/SIZE]
[/INDENT]From this last Speakertest, all my 6 speakers are passing the test since  i can hear them one by one, but as i said, now with VLC or Audacious, i  simply just can hear the Front-left, Front-right and Subwoof (the rear  speakers and the central are not sounding or just a mini bit almost  nothing if i put the speaker on my ear). 
I'm thinking on upgrading to Alsa 1.0.23 but this not makes me the real  sense.

I hope you guys from community can help me ;)
Regards.

---

