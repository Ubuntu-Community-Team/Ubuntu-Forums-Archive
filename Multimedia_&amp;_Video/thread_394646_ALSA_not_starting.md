---
title: "ALSA not starting"
date: 2007-03-27
forum: Multimedia &amp; Video
---

### Post by peterbengtsson on 2007-03-27
I seem to have f**ed up my alsa somehow. It won't start now. When I restart the computer on the geeky messages before the Ubuntu splash says [Fail] on ALSA. 

```
peterbe@trillian:~ $ sudo /etc/init.d/alsa-utils start 
 * Setting up ALSA...                                                    [ OK ] 
peterbe@trillian:~ $ ps ax  | grep alsa
 9736 pts/0    S+     0:00 grep alsa
peterbe@trillian:~ $ sudo /etc/init.d/alsa-utils restart
 * Shutting down ALSA...                                                 [ OK ] 
 * Setting up ALSA...                                                    [ OK ] 
peterbe@trillian:~ $ ps ax  | grep alsa
 9827 pts/0    R+     0:00 grep alsa
```

I won't start and I'm not getting anything in my syslog (/var/log/messages).

Is it because some sort of module is not loaded? I'm not sure what the name of the sound card is but here's the output of aplay

```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

(attached is the result of lspci -nv)
I downloaded a script called aadebug whose output was this:

```
peterbe@trillian:~/tmp/DebuggingSound $ ./aadebug 
ALSA Audio Debug v0.1.0 - Tue Mar 27 11:44:37 BST 2007
http://alsa.opensrc.org/aadebug
http://www.gnu.org/licenses/gpl.txt

Kernel ----------------------------------------------------
Linux trillian 2.6.20-13-generic #2 SMP Sun Mar 25 00:21:25 UTC 2007 i686 GNU/Linux

Loaded Modules --------------------------------------------
snd_hda_intel          21912  3 
snd_hda_codec         204672  1 snd_hda_intel
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54020  16 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_page_alloc         10888  2 snd_hda_intel,snd_pcm

Modprobe Conf ---------------------------------------------
Warning: module config file does not exist
This means any kernel modules will not be auto loaded
See your linux distro docs on how to create this file

Proc Asound -----------------------------------------------
cat: /proc/asound/{version,cards,devices,hwdep,pcm,seq/clients}: No such file or directory

Dev Snd ---------------------------------------------------
controlC0  pcmC0D0c  pcmC0D0p  pcmC0D1p  seq  timer

CPU -------------------------------------------------------
model name      : Genuine Intel(R) CPU           T2600  @ 2.16GHz
cpu MHz         : 2167.000
model name      : Genuine Intel(R) CPU           T2600  @ 2.16GHz
cpu MHz         : 2167.000

RAM -------------------------------------------------------
MemTotal:      2074948 kB
SwapTotal:     2096440 kB

Hardware --------------------------------------------------
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
```


How do I get ALSA working again? I did look at [Comprehensive Sound Problems Solutions Guide]("http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide") but I didn't understand half of it.

---

### Post by drpaul on 2007-03-27
I am not an expert on this, but the message about modprobe not seeing a config file tells me something may be missing [erased, moved, ????]. 

On my Edgy, that info seems to be in /etc/modprobe.d/

If you have a back up, you could look there.

HTH

Paul

---

### Post by peterbengtsson on 2007-03-27
I have lots of files in /etc/modprobe.d/. One called alsa-base which I've attached.

---

