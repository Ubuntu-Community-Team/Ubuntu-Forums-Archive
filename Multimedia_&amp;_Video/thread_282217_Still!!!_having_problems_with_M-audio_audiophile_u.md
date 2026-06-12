---
title: "Still!!! having problems with M-audio audiophile usb alsa &amp; jack"
date: 2006-10-22
forum: Multimedia &amp; Video
---

### Post by CapnWhizBang on 2006-10-22
I have been doing battle with this for weeks now. I've read and re-read, tried and re-tried everything I can find in the Ubuntu forums regarding the Audiophile USB and ALSA and Jack.
Everything still works if I point it at the onboard Intel audio device. (my only problem with that is my laptop only has a mic (Mono) input and I need to capture stereo.

At the moment I am at a point where I can select the Audiophile USB from System/Preferences/Sound. (although no sound comes out)

When I try to launch jack configured for the Audiophile USB I get:

jackd 0.100.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
11:31:16.063 Could not connect to JACK server as client. Please check the messages window for more info.
loading driver ..
apparent rate = 48000
creating alsa driver ... hw:1|hw:1|64|2|48000|0|0|nomon|swmeter|-|16bit
control device hw:1
configuring for 48000Hz, period = 64 frames, buffer = 2 periods
Note: audio device hw:1 doesn't support a 16bit sample format so JACK will try a 24bit format instead
Note: audio device hw:1 doesn't support a 24bit sample format so JACK will try a 32bit format instead
Sorry. The audio interface "hw:1" doesn't support any of the hardware sample formats that JACK's alsa-driver can use.
ALSA: cannot configure capture channel
cannot load driver module alsa
could not attach as JACK client (server has exited)
11:31:16.316 JACK was stopped successfully.

Like I said, I have been at this for weeks! I don't know what to do. At one point I had it so that it would play .mp3 files (by selecting it in system/preferences/sound) and running rhythmbox so I KNOW the thing works. However, even when that worked, I still go the same messages from jack as above. Is ANYONE using the Audiophile USB with alsa and jack? Can you PLEASE please help me?

---

### Post by Codeman007 on 2006-10-24
The problem seems to be that the USB-Stack of the M-Audio Audiophile USB is not like the specification.

There is a little endian/big endian problem with this adapter. In jackd-0.102.* this seems to be fixed but I have also trouble with the newest jackd.

On the jacd-devel-maillist someone told me to buy another adapter (Terratec, Edirol).

Hm - this is what I found out.

Regards, Code

---

### Post by CapnWhizBang on 2006-10-25
Here's a question....
I added Systems|Preferences|Multimedia System Selector to my menu.
I have ALSA theoretically installed and configured for the internal intel8x0 chip and for usb-audio.
In System|Preferences|Sound I have selected the Intel 82801DB-ICH4 and ESD and System Sounds.
I can use Rhythmbox Music Player to play my mp3s and it works very nicely. (sound from the laptop speakers or the headphones.)
I can also launch jackd (using qjackctl configured to use the intel chip) and ardour and get stuff in ardor to play. (again, my big problem is that I only have a mono mic input for recording otherwise I'd just use this and forget about the usb-audio interface).
So, how come when I open System|Preferences|Multimedia System Selector and choose ALSA for the output and click the "Test" button I get an error: ALSA - Advanced Linux Sound Architecture: Could not open resource for writing. ???

The ones that work are "Autodetect", "OSS" and "Custom" (wich is just OSS again). :confused:

---

### Post by Codeman007 on 2006-11-01
Now I got much information from some guys on jack-devel mailinglist. Here is what I have done and what works:

Thanks to Thibault Le Meur!!!

If you have trouble, here is some information what I have done:

- use the newest ALSA stack (I have testet with version 1.0.13 on Debian etch)
- use a newer jackd than Debian etch use (I tried JACK 0.102.20)
- In Debian etch the drum-sequencer hydrogen is build against an older jack-libray. The best will be if install the newer jackd and then make a soft link from /usr/lib/libjack.so to /usr/lib/libjack-0.100.0.so.0. After that run ldconfig or the softlinks for your jack-library point to the old one!

Next use this instructions from Thibault to load jack (I have printed them out iin _B_I_G_ letters and put them in my studio).

- check the index that has been taken by ALSA at initialization time (or enforce it)
- check that you keep the audiophile turned off while booting, then de-register snd-usb-audio and re-register it with the correct device_setup info.

I personally do this with this small script:

  modprobe -r snd-usb-audio
  modprobe snd-usb-audio index=1 device_setup=0x09

If you habe trouble with the device_setup parameter, take a look at
  /usr/src/modules/alsa-driver/alsa-kernel/Documentation/Audiophile-Usb.txt

- then, and only then, turn on the device.

And other hints:
- If you cant to change the bit-depdth you have to turn-off the device and go back from the de-regsiter step.
- Also check that you are using hw:x,0 as analog output and not hw:x,1 (digital output).

Hope That helps. If not try to contact me.

Code

---

### Post by CapnWhizBang on 2006-11-05
Thank you again for all your help. I think I am getting closer but I am still not there.

I have looked but I haven't found the jack-devel mailing list. Where should I look?

what do you mean by this?
- check the index that has been taken by ALSA at initialization time (or enforce it)
how do I do that? 

I have installed the latest jackd (0.102.20). 
I "think" I have installed the latest ALSA (1.0.13). I'm not sure how to verify that. 
I used the instructions on [this page]("http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Midiman%2FMAudio&card=Audiophile+USB.&chip=&module=usb-audio") to install alsa. I followed the instructions exactly. I'm not sure if I was supposed to change any of the values that were to be pasted into files due to the fact that I need to allow alsa to work for the onboard intel sound chip as well as the usb-audio interface. It's not clear what is being referenced in the code if you have two devices. In some places the first is referenced as 0 and the second as 1 and in other places the first is referenced as 1 and the second as 2. So I am very confused as to what is pointing to or referencing what. Sheesh!

I used this line to begin the alsa install.

sudo ./configure  --with-kernel=/usr/src/linux-headers-$(uname -r) --with-cards="intel8x0 usb-audio" --with-oss=yes --with-sequencer=yes


I get this from aadebug: (am I missing something? see proc/asound reference)

./aadebug
ALSA Audio Debug v0.1.0 - Sun Nov  5 11:09:32 EST 2006
[http://alsa.opensrc.org/index.php?page=aadebug](http://alsa.opensrc.org/index.php?page=aadebug)
[http://www.gnu.org/licenses/gpl.txt](http://www.gnu.org/licenses/gpl.txt)

Kernel ----------------------------------------------------
Linux kstoshiba3 2.6.17-10-386 #2 Fri Oct 13 18:41:40 UTC 2006 i686 GNU/Linux

Loaded Modules --------------------------------------------
snd_seq_midi            9088  0 
snd_seq_midi_event      7808  1 snd_seq_midi
snd_usb_audio          81632  0 
snd_usb_lib            17792  1 snd_usb_audio
snd_rawmidi            25344  2 snd_seq_midi,snd_usb_lib
snd_hwdep               9732  1 snd_usb_audio
snd_seq                53744  2 snd_seq_midi,snd_seq_midi_event
snd_seq_device          8972  3 snd_seq_midi,snd_rawmidi,snd_seq
snd_intel8x0           33820  0 
snd_ac97_codec        101668  1 snd_intel8x0
snd_ac97_bus            2432  1 snd_ac97_codec
snd_pcm                81032  3 snd_usb_audio,snd_intel8x0,snd_ac97_codec
snd_timer              22788  2 snd_seq,snd_pcm
snd                    57604  10 snd_usb_audio,snd_usb_lib,snd_rawmidi,snd_hwdep,snd_seq,snd_seq_device,snd_intel8x0,snd_ac97_codec,snd_pcm,snd_timer
snd_page_alloc         10760  2 snd_intel8x0,snd_pcm

Modprobe Conf ---------------------------------------------
alias char-major-116 snd
alias snd-card-0 snd-usb-audio
options snd-usb-audio index=1 device_setup=0x01
alias char-major-14 soundcore
alias sound-slot-0 snd-card-0
alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss

Proc Asound -----------------------------------------------
cat: /proc/asound/{version,cards,devices,hwdep,pcm,seq/clients}: No such file or directory

Dev Snd ---------------------------------------------------
controlC0  midiC1D0  pcmC0D0p  pcmC0D2c  pcmC0D4p  pcmC1D0p  pcmC1D1p  seq
controlC1  pcmC0D0c  pcmC0D1c  pcmC0D3c  pcmC1D0c  pcmC1D1c  pcmC1D2p  timer

CPU -------------------------------------------------------
model name      : Mobile Intel(R) Pentium(R) 4 - M CPU 2.20GHz
cpu MHz         : 1200.000

RAM -------------------------------------------------------
MemTotal:       758792 kB
SwapTotal:           0 kB

Hardware --------------------------------------------------
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)

Here is output when launching jackd:

jackd -R -v -dalsa -Phw:1,0 -r44100 -p128 -n2 -D -Chw:1,1
getting driver descriptor from /usr/lib/jack/jack_alsa.so
getting driver descriptor from /usr/lib/jack/jack_dummy.so
getting driver descriptor from /usr/lib/jack/jack_oss.so
jackd 0.102.20
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
server `default' registered
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:1,0|hw:1,1|128|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:1
configuring for 44100Hz, period = 128 frames, buffer = 2 periods
ALSA: final selected sample format for capture: 24bit big-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 24bit big-endian
ALSA: use 2 periods for playback
registered builtin port type 32 bit float mono audio
registered builtin port type 8 bit raw midi
clock source = system clock via gettimeofday
new client: alsa_pcm, id = 1 type 1 @ 0x805a780 fd = -1
new buffer size 128
registered port alsa_pcm:capture_1, offset = 512
registered port alsa_pcm:capture_2, offset = 1024
registered port alsa_pcm:playback_1, offset = 0
registered port alsa_pcm:playback_2, offset = 0
++ jack_rechain_graph():
client alsa_pcm: internal client, execution_order=0.
-- jack_rechain_graph()
11200 waiting for signals
load = 0.1551 max usecs: 9.000, spare = 2893.000
load = 0.4566 max usecs: 22.000, spare = 2880.000
load = 0.5729 max usecs: 20.000, spare = 2882.000
load = 0.6138 max usecs: 19.000, spare = 2883.000
load = 0.4620 max usecs: 9.000, spare = 2893.000
load = 0.4205 max usecs: 11.000, spare = 2891.000
load = 0.3825 max usecs: 10.000, spare = 2892.000
load = 0.5186 max usecs: 19.000, spare = 2883.000
load = 0.5867 max usecs: 19.000, spare = 2883.000
load = 0.4484 max usecs: 9.000, spare = 2893.000
load = 0.3793 max usecs: 9.000, spare = 2893.000
load = 0.6893 max usecs: 29.000, spare = 2873.000
load = 0.6548 max usecs: 18.000, spare = 2884.000
load = 0.7409 max usecs: 24.000, spare = 2878.000
load = 0.8012 max usecs: 25.000, spare = 2877.000


**** alsa_pcm: xrun of at least 0.018 msecs



**** alsa_pcm: xrun of at least 0.017 msecs



**** alsa_pcm: xrun of at least 0.016 msecs

load = 0.5557 max usecs: 9.000, spare = 2893.000

Jack appears to be running but when I try to start alsa I get a message about "JACK is not running" or "JACK is running as another user (possibly root)" or "There is already another client called 'ardour'".

When Jack is not running, if I go into "Sound Preferences" and select USB Audio and Test, a tone will come out of the USB Interface. If I select Autodetect, ALSA or Intel then sound comes out of the laptop speakers.

---

### Post by Codeman007 on 2006-11-08
> **CapnWhizBang said:**
> Thank you again for all your help. I think I am getting closer but I am still not there.

I have looked but I haven't found the jack-devel mailing list. Where should I look?


Look there: [http://jackaudio.org/email](http://jackaudio.org/email)

> 
what do you mean by this?
- check the index that has been taken by ALSA at initialization time (or enforce it)
how do I do that? 


When you load the module (with modprobe) you only need to append "index=1" or whatever your soundcard should have. On my thinkpad there is the intel-soundchip at index=0.

> 
I have installed the latest jackd (0.102.20). 
I "think" I have installed the latest ALSA (1.0.13). I'm not sure how to verify that. 


I download the sources from [http://www.alsa-project.org](http://www.alsa-project.org) and compile and install them by myself - so I know what version I have. Perhaps "older" version will work also but I haven't tested this.

> 
I used the instructions on [this page]("http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Midiman%2FMAudio&card=Audiophile+USB.&chip=&module=usb-audio") to install alsa. I followed the instructions exactly. I'm not sure if I was supposed to change any of the values that were to be pasted into files due to the fact that I need to allow alsa to work for the onboard intel sound chip as well as the usb-audio interface. It's not clear what is being referenced in the code if you have two devices. In some places the first is referenced as 0 and the second as 1 and in other places the first is referenced as 1 and the second as 2. So I am very confused as to what is pointing to or referencing what. Sheesh!

I used this line to begin the alsa install.

sudo ./configure  --with-kernel=/usr/src/linux-headers-$(uname -r) --with-cards="intel8x0 usb-audio" --with-oss=yes --with-sequencer=yes


I get this from aadebug: (am I missing something? see proc/asound reference)

./aadebug
ALSA Audio Debug v0.1.0 - Sun Nov  5 11:09:32 EST 2006
[http://alsa.opensrc.org/index.php?page=aadebug](http://alsa.opensrc.org/index.php?page=aadebug)
[http://www.gnu.org/licenses/gpl.txt](http://www.gnu.org/licenses/gpl.txt)

Kernel ----------------------------------------------------
Linux kstoshiba3 2.6.17-10-386 #2 Fri Oct 13 18:41:40 UTC 2006 i686 GNU/Linux

Loaded Modules --------------------------------------------
snd_seq_midi            9088  0 
snd_seq_midi_event      7808  1 snd_seq_midi
snd_usb_audio          81632  0 
snd_usb_lib            17792  1 snd_usb_audio
snd_rawmidi            25344  2 snd_seq_midi,snd_usb_lib
snd_hwdep               9732  1 snd_usb_audio
snd_seq                53744  2 snd_seq_midi,snd_seq_midi_event
snd_seq_device          8972  3 snd_seq_midi,snd_rawmidi,snd_seq
snd_intel8x0           33820  0 
snd_ac97_codec        101668  1 snd_intel8x0
snd_ac97_bus            2432  1 snd_ac97_codec
snd_pcm                81032  3 snd_usb_audio,snd_intel8x0,snd_ac97_codec
snd_timer              22788  2 snd_seq,snd_pcm
snd                    57604  10 snd_usb_audio,snd_usb_lib,snd_rawmidi,snd_hwdep,snd_seq,snd_seq_device,snd_intel8x0,snd_ac97_codec,snd_pcm,snd_timer
snd_page_alloc         10760  2 snd_intel8x0,snd_pcm

Modprobe Conf ---------------------------------------------
alias char-major-116 snd
alias snd-card-0 snd-usb-audio
options snd-usb-audio index=1 device_setup=0x01
alias char-major-14 soundcore
alias sound-slot-0 snd-card-0
alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss

Proc Asound -----------------------------------------------
cat: /proc/asound/{version,cards,devices,hwdep,pcm,seq/clients}: No such file or directory

Dev Snd ---------------------------------------------------
controlC0  midiC1D0  pcmC0D0p  pcmC0D2c  pcmC0D4p  pcmC1D0p  pcmC1D1p  seq
controlC1  pcmC0D0c  pcmC0D1c  pcmC0D3c  pcmC1D0c  pcmC1D1c  pcmC1D2p  timer

CPU -------------------------------------------------------
model name      : Mobile Intel(R) Pentium(R) 4 - M CPU 2.20GHz
cpu MHz         : 1200.000

RAM -------------------------------------------------------
MemTotal:       758792 kB
SwapTotal:           0 kB

Hardware --------------------------------------------------
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)

Here is output when launching jackd:

jackd -R -v -dalsa -Phw:1,0 -r44100 -p128 -n2 -D -Chw:1,1
getting driver descriptor from /usr/lib/jack/jack_alsa.so
getting driver descriptor from /usr/lib/jack/jack_dummy.so
getting driver descriptor from /usr/lib/jack/jack_oss.so
jackd 0.102.20
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
server `default' registered
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:1,0|hw:1,1|128|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:1
configuring for 44100Hz, period = 128 frames, buffer = 2 periods
ALSA: final selected sample format for capture: 24bit big-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 24bit big-endian
ALSA: use 2 periods for playback
registered builtin port type 32 bit float mono audio
registered builtin port type 8 bit raw midi
clock source = system clock via gettimeofday
new client: alsa_pcm, id = 1 type 1 @ 0x805a780 fd = -1
new buffer size 128
registered port alsa_pcm:capture_1, offset = 512
registered port alsa_pcm:capture_2, offset = 1024
registered port alsa_pcm:playback_1, offset = 0
registered port alsa_pcm:playback_2, offset = 0
++ jack_rechain_graph():
client alsa_pcm: internal client, execution_order=0.
-- jack_rechain_graph()
11200 waiting for signals
load = 0.1551 max usecs: 9.000, spare = 2893.000
load = 0.4566 max usecs: 22.000, spare = 2880.000
load = 0.5729 max usecs: 20.000, spare = 2882.000
load = 0.6138 max usecs: 19.000, spare = 2883.000
load = 0.4620 max usecs: 9.000, spare = 2893.000
load = 0.4205 max usecs: 11.000, spare = 2891.000
load = 0.3825 max usecs: 10.000, spare = 2892.000
load = 0.5186 max usecs: 19.000, spare = 2883.000
load = 0.5867 max usecs: 19.000, spare = 2883.000
load = 0.4484 max usecs: 9.000, spare = 2893.000
load = 0.3793 max usecs: 9.000, spare = 2893.000
load = 0.6893 max usecs: 29.000, spare = 2873.000
load = 0.6548 max usecs: 18.000, spare = 2884.000
load = 0.7409 max usecs: 24.000, spare = 2878.000
load = 0.8012 max usecs: 25.000, spare = 2877.000


**** alsa_pcm: xrun of at least 0.018 msecs



**** alsa_pcm: xrun of at least 0.017 msecs



**** alsa_pcm: xrun of at least 0.016 msecs

load = 0.5557 max usecs: 9.000, spare = 2893.000

Jack appears to be running but when I try to start alsa I get a message about "JACK is not running" or "JACK is running as another user (possibly root)" or "There is already another client called 'ardour'".


Hmmmm. You must run jack as the same user as your client should run. I use "qjackctl" for starting and tuning jack. Perhaps try this one as a normal user?

Maybe you cannot get realtime because only root can use this... as far as I know...

I use 48 kHz sampling frq. I don't know if 44.1 kHz is supported by the M-Audio - and 24 bits resolution. That's working for device_setuip=0x09.

One _B_I_G_ thing you should look for:
- Power off the M-Audio
- unload snd-usb-audio
- load snd-usb-audio with ypur parameters
- NOW TURN ON THE M-AUDIO!!!!

If you do not you hear NOTHING!

> 
When Jack is not running, if I go into "Sound Preferences" and select USB Audio and Test, a tone will come out of the USB Interface. If I select Autodetect, ALSA or Intel then sound comes out of the laptop speakers.

I think you are playing trough the ALSA-Device if jack is not running. From this point of view everything is fine...

One thing to check out:
I have (Debian) in /usr/libs a direktory jack-100-0 (or something else) and a directory jack. Inside the dirs there are some I/O-libryries for jack. You must rename jack-100-0 and symlink this name to jack. Perhaps this will help?

Holger

---

### Post by CapnWhizBang on 2006-11-11
What does your /etc/modules.conf file look like?
Can you post it?

What does your .asoundrc file look like?
Can you post it too?

Thanks

---

