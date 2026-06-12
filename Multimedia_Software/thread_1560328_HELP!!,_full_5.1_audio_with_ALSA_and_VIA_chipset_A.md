---
title: "HELP!!, full 5.1 audio with ALSA and VIA chipset AC97 codec"
date: 2010-08-24
forum: Multimedia Software
---

### Post by LarsUb on 2010-08-24
Hi folks,
I'm just a little newbie with ubuntu, i just left windoze.. hehe, i   set up all the programs and hardware i need, but i still having an  issue  with SOUND. This is the stage.

I have a Mobo MSI K8 series, with integrated sound VIA 3059 chip Realtek  ALC655 using codec AC97 (this integrated audio  has 3 audio connectors:  blue, green and  pink), im running Ubuntu Lucid 10.04, and i'm using a  Logitech X530  5.1 audio system (this system has 3 audio connectors:  black, green and orange) - i  just replaced my old pair of simple 2004  speakers :sad:

The issues is: When i installed ubuntu I was running Pulseaudio mixer   with an OLD pair of speakers and everything was working OK. Then, i   connected the new X530 speakers (with its corresponding plugs/connection   and colors), and i could hear a very improved sound but with a **very   annoying little noise** like a tinny buzz or vibration, not so   perceptible at begginig but in 5 minutes my ears were hurted, so i   though those noise was going to turn me deaf.

Well, i thought the speakers were damaged, so i switched to windoze to   try them with the audio drivers and  codecs there, and amazingly the  speakers sounded like heaven, so i  discarded a damage.  Then, i just  came back to Ubuntu, and tried with  other mixers and found that just  with Pulseaudio the annoying noise was  present, and since Pulseaudio was  the default mixer used by all  applications like VLC, MeTV and others,  they had the annoying noise as  well. At that point i decided to remove  Pulseaudio and reinstall, but  that didn't work.

So i removed Pulseaudio again and re-setup ALSA  mixer instead of. So now  im using ALSA  and the annoying noise has gone from all applications :smile: the audio  now sounds good in any application but.... **i just can hear sound  from 3 speakers, the  Front-left, Front-right and Subwoofer**.  If i  try to set the  Output-plugin setting to Surround5.1 in the Audacious audio preferences  it just give me this error:[INDENT]ALSA error, snd_pcm_hw_params_set_rate failed:  Invalid  argument  :sad:
[/INDENT]I've tried to adjust some basic settings with the Alsamixer  gui applet  but nothing makes a reference to my 5.1 sound system. I've  been googling  for a solution but without specific results, i read  something like Alsa cannot do  multichannel but i'm not sure. Therefore my question is:

**How can i correctly setup my 5.1 speakers system with ALSA mixer and  my mobo-integrated sound VIA  with realtek ALC655 and AC97 codec??**,  in order to make sound all  my 6 speakers (2front, 2rear, 1central,  1subw).

Some output commands for workaround from my ub are:
    $ uname -a[INDENT][SIZE=1]Linux hellhound  2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11  07:54:58 UTC 2010 i686  GNU/Linux[/SIZE]
[/INDENT]$ cat /proc/asound/version[INDENT][SIZE=1]Advanced  Linux Sound Architecture Driver Version 1.0.21.[/SIZE]
[/INDENT]$ head -l /proc/asound/card0/codec97#0/ac97#0-0[INDENT][SIZE=1]0-0/0: Realtek ALC655 rev 0
PCI Subsys Vendor: 0x1462
PCI Subsys Device: 0x0080
Flags: 0
Revision         : 0x00
Compat. Class    : 0x00
Subsys. Vendor ID: 0xffff
Subsys. ID       : 0xffff[/SIZE]
[/INDENT]$ lspci | grep audio[INDENT][SIZE=1]00:11.5 Multimedia audio  controller: VIA Technologies, Inc.  VT8233/A/8235/8237 AC97 Audio  Controller (rev 60)[/SIZE]
[/INDENT]$ aplay -l[INDENT][SIZE=1]**** List of PLAYBACK  Hardware Devices ****
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
[/INDENT]$ lsmod | grep snd[INDENT][SIZE=1]snd_via82xx             20058  2 
gameport                9089  1 snd_via82xx
snd_ac97_codec        100646  1 snd_via82xx
ac97_bus                1002  1 snd_ac97_codec
snd_usb_audio          75765  0 
snd_pcm_oss            35308  1 
snd_usb_lib            15801  1 snd_usb_audio
snd_hwdep               5412  1 snd_usb_audio
snd_mixer_oss          13746  2 snd_pcm_oss
snd_seq_dummy           1338  0 
snd_pcm                70662  4   snd_via82xx,snd_ac97_codec,snd_usb_audio,snd_pcm_o  ss
snd_page_alloc          7076  2 snd_via82xx,snd_pcm
snd_mpu401_uart         5617  1 snd_via82xx
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  3 snd_usb_lib,snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6   snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_mid  i_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5   snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi  ,snd_seq
snd                    54148  13   snd_via82xx,snd_ac97_codec,snd_usb_audio,snd_pcm_o   ss,snd_hwdep,snd_mixer_oss,snd_pcm,snd_mpu401_uart   ,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq  _device
soundcore               6620  3 snd[/SIZE]
[/INDENT]$ speaker-test -D surround51 -c 6[INDENT][SIZE=1]speaker-test  1.0.22
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
[/INDENT]From this last Speakertest, all my 6 speakers are passing  the test since  i can hear them one by one, but as i said, now with VLC  or Audacious, trying with many output plugins and settings but i only can hear the Front-left, Front-right and  Subwoof (the rear  speakers and the central are not sounding or just a  mini bit almost  nothing if i put the speaker on my ear). 
I'm thinking on upgrading to Alsa 1.0.23  but this not makes me the real  sense.

I hope you guys from community can help me :wink:
Regards.


++++++++ UPDATE

Since im discarding the alsa upgrade, i was googling and reading this guide  [http://alsa.opensrc.org/SurroundSound ]("http://alsa.opensrc.org/SurroundSound")
Then i tried to build an  .asoundrc  file in /home/MyUser, this would override settings for alsa in all audio apps.

To verify more info about your soundcard's PCM capabilities look at    /proc/asound/pcm/*
Note:  V8237 is my chipset and using AC97 codec in realtek ALC655, well, im not sure why?, but Audacious is using IEC958 as the Mixer element when it works with its output plugins (which cant perform full surround5.1 - as i initially posted), so i used this name to build my asoundrc file like this:

> # 5.1 upmixing, dmixing, asoundrc
pcm.V8237 {
    type hw
    card 0
    }

# 6 channel dmix
pcm.iec958 {
    type dmix
    ipc_key 1024
        ipc_key_add_uid false
        ipc_perm 0660
    slave {
        pcm V8237
        rate 48000
        channels 6
        period_time 0
                period_size 1024
                buffer_time 0
                buffer_size 1000
        }
    }
# upmixing
pcm.surround51 {
    type route
    slave.pcm iec958
    slave.channels 6
    ttable.0.0 1
    ttable.1.1 1
    ttable.0.2 1
    ttable.1.3 1
    ttable.0.5 0.5
    ttable.1.5 0.5
    }

I restarted alsa and Audacious, but now Audacious send this error:
    ALSA error: "No suitable mixer element found"

I'm almost sure this is due to a detail regarding the mixer in my .asounrc file, but i cant find out the mistake o the missing part. Im also sure that Audacious is getting the Alsa output plugin preferences from the  $ aplay -L  command, and this info is taken from the /proc/asound/* files. This works by default when the  .asoundrc file is not present (although is not needed in recent Alsa versions according the alsa website). 
Therefore i think i have to fix something with /proc/asound/*files, or write a better .asoundrc  alsa config file.

In the meanwhile, to still having sound (at least with Front-left-rignt and Subw), i removed the .asoundrc file and reloaded Audacious, i spent 3 hours reading and trying, im tired.. so maybe later i'll still trying..

Your help or directions would be greatly appreciated guys.

---

### Post by lidex on 2010-08-28
This, maybe?
[http://alsa.opensrc.org/index.php/AlsaTips#Enabling_5.2B1_outputs_on_cards_with_line-out.2C_mic-in_and_line-in_jacks](http://alsa.opensrc.org/index.php/AlsaTips#Enabling_5.2B1_outputs_on_cards_with_line-out.2C_mic-in_and_line-in_jacks)

---

### Post by jean noel on 2011-02-27
I don't know if this may help, as I am a bit late. I have the same chipset, and I found out that if go into sound, then hardware then settings for selected  devices. then profile them 4.1 analog output, as I have a 4.1 system, I can have all my speakers working.
Try it.
Regards
Jean Noel

---

