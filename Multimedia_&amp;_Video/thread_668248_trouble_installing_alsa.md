---
title: "trouble installing alsa"
date: 2008-01-15
forum: Multimedia &amp; Video
---

### Post by Shum on 2008-01-15
G'day y'all.

I'm fairly new to linux and am more or less stumbling in the dark.
just installed gutsy on my new lappy but couldnt get sound.
my laptop is a toshiba A200 with an intel 82801 sound card.
After looking into this i found that gusty comes with alsa version 1.0.14 but i need at least version 1.0.15 to support my sound card.

so i read a bunch of tutorials on how to update/install alsa and from there did the following.

i went to the alsa website, downloaded the latest source for driver, firmware, lib and utils.
untared.
went into each directory and ran make and make install, making the drivers and libraries first.

now when i run
 cat /proc/asound/version
it says i have version 1.0.15

i ran alsaconf, it detected my card:
 hda-intel   Intel Corporation 82801G (ICH7 Family)
finish configuring

then says
 Now ALSA is ready to use.
 For adjustment of volumes, use your favorite mixer.

 Have a lot of fun!

mk so it seems to work.

But then all my programs say that there is no sound card and when i run
 cat /proc/asound/cards
i get
--- no soundcards ---

So alsa claims to have detected and configured a sound card, but then i dont have a sound card.

I've tried reading the troubleshooting guide on the alsa website
[http://alsa.opensrc.org/index.php/TroubleShooting](http://alsa.opensrc.org/index.php/TroubleShooting)
but don't follow most of it.

I did however run the aadebug script:
[http://alsa.opensrc.org/index.php/Aadebug](http://alsa.opensrc.org/index.php/Aadebug)
and the output is printed below.

any pointers in the right direction would massively appreciated, just tell me what to google even.

Thanks in advance for your patience and advice.


ALSA Audio Debug v0.1.0 - Tue Jan 15 22:43:53 WST 2008
[http://alsa.opensrc.org/aadebug](http://alsa.opensrc.org/aadebug)
[http://www.gnu.org/licenses/gpl.txt](http://www.gnu.org/licenses/gpl.txt)

Kernel ----------------------------------------------------
Linux shumzor 2.6.22-14-generic #1 SMP Tue Dec 18 05:28:27 UTC 2007 x86_64 GNU/Linux

Loaded Modules --------------------------------------------
snd_pcm_oss            48128  0 
snd_mixer_oss          20352  1 snd_pcm_oss
snd_pcm                94600  1 snd_pcm_oss
snd_seq_dummy           5892  0 
snd_seq_oss            39040  0 
snd_seq_midi           11264  0 
snd_rawmidi            30336  1 snd_seq_midi
snd_seq_midi_event     10240  2 snd_seq_oss,snd_seq_midi
snd_seq                63776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              27784  2 snd_pcm,snd_seq
snd_seq_device         10772  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    71720  9 snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_page_alloc         13584  1 snd_pcm

Modprobe Conf ---------------------------------------------
Warning: module config file does not exist
This means any kernel modules will not be auto loaded
See your linux distro docs on how to create this file

Proc Asound -----------------------------------------------
Advanced Linux Sound Architecture Driver Version 1.0.15.
Compiled on Nov 20 2007 for kernel 2.6.22-14-generic (SMP).
--- no soundcards ---
  1:        : sequencer
 33:        : timer
Client info
  cur  clients : 3
  peak clients : 3
  max  clients : 192

Client   0 : "System" [Kernel]
  Port   0 : "Timer" (Rwe-)
  Port   1 : "Announce" (R-e-)
    Connecting To: 15:0
Client  14 : "Midi Through" [Kernel]
  Port   0 : "Midi Through Port-0" (RWe-)
Client  15 : "OSS sequencer" [Kernel]
  Port   0 : "Receiver" (-we-)
    Connected From: 0:1

Dev Snd ---------------------------------------------------
seq  timer

CPU -------------------------------------------------------
model name	: Intel(R) Core(TM)2 CPU         T5300  @ 1.73GHz
cpu MHz		: 800.000
model name	: Intel(R) Core(TM)2 CPU         T5300  @ 1.73GHz
cpu MHz		: 800.000

RAM -------------------------------------------------------
MemTotal:      2062116 kB
SwapTotal:      787144 kB

Hardware --------------------------------------------------
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
07:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

---

### Post by balaknair on 2008-01-15
try entering this ina terminal
sudo modprobe snd-hda-intel

and check sound again

---

### Post by Shum on 2008-01-16
thanks for the reply man.

that gives me

FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)


i then ran dmesg.
I got a huge output so i wont post it all, but seems to start having a problem here:

...
...
[   37.343777] snd_hda_intel: disagrees about version of symbol snd_ctl_add
[   37.343783] snd_hda_intel: Unknown symbol snd_ctl_add
[   37.343820] snd_hda_intel: disagrees about version of symbol snd_pcm_new
[   37.343822] snd_hda_intel: Unknown symbol snd_pcm_new
[   37.343859] snd_hda_intel: disagrees about version of symbol snd_pcm_limit_hw_rates
[   37.343861] snd_hda_intel: Unknown symbol snd_pcm_limit_hw_rates
and etc for lots more symbols...
...


thanks again

---

### Post by balaknair on 2008-01-16
This is more or less what I got when I tried using ALSA 1.0.15
It stopped detecting my card. Most fixes I tried made no difference.
In the end I did a clean install of Ubuntu, and just edited modprobe.d/alsa-base to add my card model to options without changing ALSA 1.0.14, and this seemed to work.
ALSA 1.0.15 works just fine with Mandriva on this same system, but maybe something about the Gutsy kernel doesn't click with the 1.0.15 package.

Could you try purging alsa 1.0.15 and reinstalling alsa 1.0.14 from the ubuntu repositories and then running modprobe? This worked for a friend's Acer laptop Intel ICH7 card. It *might* work for you, but I'm not too hopeful.
Worst case scenario- you might have to reinstall the Linux kernel(either just the kernel(not sure how but howto-s available on forums) or a total reinstall of Ubuntu)

All the best(hope it doesn't come to the worst case scenario)

---

