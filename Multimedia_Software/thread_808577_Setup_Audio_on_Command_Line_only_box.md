---
title: "Setup Audio on Command Line only box"
date: 2008-05-26
forum: Multimedia Software
---

### Post by n1wil on 2008-05-26
Hello,

I'm trying to setup audio playback on a command line only box.  I do not want to install the graphical desktop in my specific application.  I've already got the base system installed and ALSA and associated packages are installed but I still am not able to hear audio.  What is the best method to go about enabling audio in a command line only environment?  What packages should be installed?  I can run the command alsamixer and I see the command line mixer and can change the settings but no audio no matter what the setting.

The detected sound hardware shows as:
Card: Ensoniq AudioPCI
Chip: Cirrus Logic CS4297A rev 4

The installed base OS is Ubuntu 8.04.

I also have VLC installed and I call an internet radio stream such as: 

vlc -vvv [http://208.122.59.30:7794](http://208.122.59.30:7794)  The box seems to pull in the stream but no audio.

What gives?  

Any help would be MOST GREATLY appreciated.

[EDIT]: BTW, if a graphical desktop is installed, there is sound.  So obviously the graphical environment installs a certain package that gets the sound working.  


Thanks,

John Rogers

---

### Post by ibutho on 2008-05-26
Install alsa-utils if its not already installed. After that configure your card using alsaconf and then set the volumes using alsamixer.

---

### Post by n1wil on 2008-05-26
hello, thanks for your reply.  

alsa-utils is already installed.  When I try to run alsaconf I get the following message:

-bash: alsa-conf: command not found

Am I doing something wrong?  I can run alsamixer and adjust settings and all.  Just no sound.

---

### Post by ibutho on 2008-05-26
The command is alsaconf and not alsa-conf. ;) 

Edit: Apparently alsaconf is not available in Ubuntu. Try running alsamixer and unmute some volumes levels e.g. front and pcm.

---

### Post by n1wil on 2008-05-26
Mistake noted, and yes I confirm that alsaconf is not available as it is no longer featured in Ubuntu.  

I have also confirmed that all volumes are set at 75% and unmuted.  Still no audio.  Is there another way to go about this?

Thanks,

John

---

### Post by Gunman1982 on 2008-05-26
Did you try to play just one file with aplay to check if its an driver issue or missing packages.

---

### Post by n1wil on 2008-05-26
no but the sound card is detected and a driver seems to be loaded for it.  I ran lspci to take a look at what's present:

root@d-2400:~# lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
**01:04.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 09)**
01:09.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)

in BOLD

and lsmod returns:

snd_ens1371            27168  2
gameport               16008  1 snd_ens1371
snd_ac97_codec        101028  1 snd_ens1371
ac97_bus                3072  1 snd_ac97_codec
snd_pcm_oss            42144  0
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  4 snd_ens1371,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4868  0
snd_seq_oss            35584  0
snd_seq_midi            9376  0
snd_rawmidi            25760  2 snd_ens1371,snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  3 snd_pcm,snd_seq
psmouse                40336  0
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
serio_raw               7940  0
snd                    56996  13 snd_ens1371,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  1 snd_pcm
button                  9232  0
i2c_i810                5636  0


I will try aplay but I doubt it will have any bearing on the matter.  My application does require VLC to be the program of choice though.  

Thanks.

---

### Post by n1wil on 2008-05-26
No sound output when playing a single file from aplay.

There has got to be a way to get this working.

---

### Post by Gunman1982 on 2008-05-26
Can you show the ouput of the command 'cat /dev/sndstat'?

---

### Post by n1wil on 2008-05-26
root@d-2400:~# cat /dev/sndstat
Sound Driver:3.8.1a-980706 (ALSA v1.0.16 emulation code)
Kernel: Linux d-2400 2.6.24-17-generic #1 SMP Thu May 1 14:31:33 UTC 2008 i686
Config options: 0

Installed drivers:
Type 10: ALSA emulation

Card config:
Ensoniq AudioPCI ENS1371 at 0xdf40, irq 16

Audio devices:
0: ES1371 DAC2/ADC (DUPLEX)

Synth devices: NOT ENABLED IN CONFIG

Midi devices:
0: ES1371

Timers:
7: system timer

Mixers:
0: Cirrus Logic CS4297A rev 4

---

### Post by Gunman1982 on 2008-05-26
Mhh and the command 'lsof | grep snd'? (shows you which applications access the soundcard atm)

---

### Post by n1wil on 2008-05-26
root@d-2400:~# lsof | grep snd
alsamixer 6525       john    3u      CHR      116,0              10220 /dev/snd/controlC0

alsamixer is open on another terminal.  

When alsamixer closed, the command returns nothing.

---

### Post by Gunman1982 on 2008-05-26
Try the aplay with one file again and do the lsof | grep snd on another console to check which card its trying to access

---

### Post by n1wil on 2008-05-26
root@d-2400:~# lsof | grep snd
alsamixer 6529       john    3u      CHR      116,0              10220 /dev/snd/controlC0
aplay     6531       john  mem       CHR     116,16              10194 /dev/snd/pcmC0D0p
aplay     6531       john    3r      CHR     116,33              10080 /dev/snd/timer
aplay     6531       john    4u      CHR     116,16              10194 /dev/snd/pcmC0D0p

---

### Post by n1wil on 2008-05-26
OH MY GOD!!!!  ok....   I WON the IDIOT OF THE YEAR AWARD!

I looked on the back of the tower again (not easily accessible) and found another sound interface...   plugged into that... and whoa!  god said "Let there be sound!" and so it was!

Thanks gentlemen for all your help...   I hope I did not waste anybody's time.  

Though I WILL say, I learned a some extra diagnostics - so i thank you all for the added knowledge - it wasn't a *complete* waste!

lol  geez, can't believe I did that!!!!

---

### Post by boreddrone on 2008-10-12
I too spent a couple of hours on this problem (today) and found the solution.

You must use alsamixer and increase the master volume with the up-arrow keys **_AND press "M" on the master selection to un-mute it_**.

It's in the second paragraph of the "Playback" heading of the "SoundcardTesting" on alsa-project.org.

[http://www.alsa-project.org/main/index.php/SoundcardTesting](http://www.alsa-project.org/main/index.php/SoundcardTesting)

If you're compiling MPlayer I will try and save you some time by identifying *libalsa-ocaml-dev* as the package you'll need to install to get libasound required for MPlayer to recognize ALSA on your system.

---

