---
title: "Can't record sound in Edgy"
date: 2007-01-04
forum: Multimedia &amp; Video
---

### Post by Verdegris on 2007-01-04
Hi all - first post...

I'm running Edgy on a 1.4g Athlon box, 2 hard drives (1 for OS, 1 200gig for storage) SBLive card, 1.5 gig RAM. Kernel is 2.6.17 unmodded.
The problem: Sound will go into the computer from either the mic or line inputs and can be heard just fine. Volume can be controlled from ALSA mixer app. Capture is turned on in ALSA mixer. However, I cannot record any sound at all from any source, using either the Ubuntu sound recorder or Ardour w/JACK. Tried Audacity as well. Uninstalled, reinstalled, tweaked, tweaked, tweaked. Nothing. Followed every web page's advice, including the excellent Comprehensive sound solutions guide here. Uninstalled ALSA with --purge option, then reinstalled. The only thing I can think of at this point is that the SBLive has gone south in some way - it's pretty old. New driver?
Here's the output from aadebug:


Kernel ----------------------------------------------------
Linux nyabinghi 2.6.17-10-generic #2 SMP Tue Dec 5 22:28:26 UTC 2006 i686 GNU/Linux

Loaded Modules --------------------------------------------
snd_emu10k1_synth       8960  0 
snd_emux_synth         39296  1 snd_emu10k1_synth
snd_seq_virmidi         8576  1 snd_emux_synth
snd_seq_midi_emul       8192  1 snd_emux_synth
snd_seq_dummy           4996  0 
snd_seq_oss            36480  0 
snd_seq_midi            9984  0 
snd_seq_midi_event      8960  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                59120  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_via82xx            30360  0 
snd_emu10k1           128288  3 snd_emu10k1_synth
snd_util_mem            6016  2 snd_emux_synth,snd_emu10k1
snd_hwdep              10756  2 snd_emux_synth,snd_emu10k1
snd_ac97_codec         97696  2 snd_via82xx,snd_emu10k1
snd_ac97_bus            3456  1 snd_ac97_codec
snd_pcm_oss            47360  0 
snd_mixer_oss          19584  1 snd_pcm_oss
snd_pcm                84612  4 snd_via82xx,snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_timer              25348  3 snd_seq,snd_emu10k1,snd_pcm
snd_page_alloc         11400  3 snd_via82xx,snd_emu10k1,snd_pcm
snd_mpu401_uart        10240  1 snd_via82xx
snd_rawmidi            27264  4 snd_seq_virmidi,snd_seq_midi,snd_emu10k1,snd_mpu401_uart
snd_seq_device          9868  8 snd_emu10k1_synth,snd_emux_synth,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_emu10k1,snd_rawmidi
snd                    58372  19 snd_emux_synth,snd_seq_virmidi,snd_seq_oss,snd_seq,snd_via82xx,snd_emu10k1,snd_hwdep,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device

Modprobe Conf ---------------------------------------------
alias char-major-116    snd

Proc Asound -----------------------------------------------
cat: /proc/asound/{version,cards,devices,hwdep,pcm,seq/clients}: No such file or directory

Dev Snd ---------------------------------------------------
controlC0  hwC0D0  midiC0D0  midiC0D2  pcmC0D0p  pcmC0D2c  pcmC0D3p  pcmC1D0p  seq
controlC1  hwC0D2  midiC0D1  pcmC0D0c  pcmC0D1c  pcmC0D2p  pcmC1D0c  pcmC1D1p  timer

CPU -------------------------------------------------------
model name      : AMD Athlon(tm) Processor
cpu MHz         : 1100.222

RAM -------------------------------------------------------
MemTotal:      1295772 kB
SwapTotal:      433712 kB

Hardware --------------------------------------------------
00:00.0 Host bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333]
00:06.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 03)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 40)

Hoping someone here can help...

---

### Post by armadill0 on 2007-02-12
I am having similar issues.  

First, ubuntu is a great distro, thanks for you hard work.  However...    :)

I can hear my voice in the speakers, but I can't seem to get KRec, skype, or anything else so far to "hear" my voice. 

To the best of my memory, sound recording worked correctly under 5.10.  Also, on a previous install of 6.10 on the same machine, KRec would lock up when I hit record.  On my present install, KRec will start to record, but it won't hear my mic sound.  Again, I can hear my voice in the speakers.  I've tried playing with alsamix, kmix, etc and haven't gotten it working.

This seems to be a fairly common problem with ubuntu, I've been pretty surprised how little has been done about it given the otherwise great support.  Hopefully this can be resolved.  Thanks for your help!

I use:

Kubuntu 6.10
uname -a : Linux dolphin 2.6.17-11-386 #2 Thu Feb 1 19:50:13 UTC 2007 i686 GNU/Linux
Chipset: VIA 8237
Mobo: VIA K8T800

My aadebug output:
ALSA Audio Debug v0.1.0 - Mon Feb 12 11:42:31 AKST 2007
[http://alsa.opensrc.org/aadebug](http://alsa.opensrc.org/aadebug)
[http://www.gnu.org/licenses/gpl.txt](http://www.gnu.org/licenses/gpl.txt)

Kernel ----------------------------------------------------
Linux dolphin 2.6.17-11-386 #2 Thu Feb 1 19:50:13 UTC 2007 i686 GNU/Linux

Loaded Modules --------------------------------------------
snd_seq_dummy           4100  0
snd_seq_oss            34304  0
snd_seq_midi            9088  0
snd_seq_midi_event      7808  2 snd_seq_oss,snd_seq_midi
snd_seq                53360  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_via82xx            28696  7
snd_ac97_codec         96672  1 snd_via82xx
snd_ac97_bus            2432  1 snd_ac97_codec
snd_bt87x              15524  3
snd_pcm_oss            46080  0
snd_mixer_oss          18560  3 snd_pcm_oss
snd_pcm                80520  5 snd_via82xx,snd_ac97_codec,snd_bt87x,snd_pcm_oss
snd_timer              23172  2 snd_seq,snd_pcm
snd_mpu401_uart         8704  1 snd_via82xx
snd_rawmidi            25600  2 snd_seq_midi,snd_mpu401_uart
snd_seq_device          8972  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
snd                    55428  27 snd_seq_oss,snd_seq,snd_via82xx,snd_ac97_codec,snd_bt87x,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
snd_page_alloc         10504  3 snd_via82xx,snd_bt87x,snd_pcm

Modprobe Conf ---------------------------------------------
Warning: module config file does not exist
This means any kernel modules will not be auto loaded
See your linux distro docs on how to create this file

Proc Asound -----------------------------------------------
cat: /proc/asound/{version,cards,devices,hwdep,pcm,seq/clients}: No such file or directory

Dev Snd ---------------------------------------------------
controlC0  controlC1  pcmC0D0c  pcmC0D0p  pcmC0D1c  pcmC0D1p  pcmC1D0c  pcmC1D1c  seq  timer

CPU -------------------------------------------------------
model name      : AMD Athlon(tm) 64 Processor 3200+
cpu MHz         : 2000.449

RAM -------------------------------------------------------
MemTotal:      1035848 kB
SwapTotal:     3028212 kB

Hardware --------------------------------------------------
00:00.0 Host bridge: VIA Technologies, Inc. VT8385 [K8T800 AGP] Host Bridge (rev 01)
00:08.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 02)
00:08.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 02)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control

---

### Post by Admiral-Cyclops on 2007-02-15
I have the exact same issues.

Using SB Live! card.  I know it hasn't gone south because windows uses it fine.

---

### Post by Admiral-Cyclops on 2007-02-15
I've used OSS as the record source as well, no go there.

---

### Post by armadill0 on 2007-02-15
Admiral-Cyclops, could you post some system info, audio chipset, and aadebug output?  That might help us track down the commonality here.  Thanks.

---

### Post by Admiral-Cyclops on 2007-02-17
I certainly would, but I finally fixed it, I am logging in today to post the solution, as I have found it...

First off, its a Sound Blaster Live! card, I think it uses a SigmaTel STAC9721.23 chipset, but I could be wrong, I've also heard it uses a emu10k1.

At any rate, here is how I fixed it...

This is directly from my tech blog (where I post all my solutions, URL is:
[http://solvancy.blogspot.com/](http://solvancy.blogspot.com/)

So, for the last several days I've been trying to do something very simple with no success. I've been trying to accept sound from the microphone into the computer for recording. Using an SB Live! Value card (same as Platinum just different Windows software package bundled with it). At any rate...

The first problem in making this work was that the speakers would play back whatever they heard via the Microphone, while this proved that it functioned properly did not help with recording.

The next problem was actually finding the capture settings that would allow for capture from the microphone to take place, under Linux ALSA there are tons of capture lines that seem to be absolutely useless for the most part. Finally, via several web sites, I found a mixer command...

alsamixer

Its console, so no GUI really, just a minor text GUI.

I won't go through every step, but, I found that the AC97 line has to be turned all the way down in playback as well as the Microphone and Line In volumes in playback. If you don't do this, you'll get feedback.

Next, Press F4 to get to the capture settings. Turn everything off and 0 every out. If its not muted, mute it, if its not a 0, make it to 0.

Finally, find the Microphone setting, press Space until a red L and R appear with CAPTUR appears above the name of the control. Then, find Capture and press space here as well, same thing, red L and R above the word CAPTUR. Then max it out. Find AC97, same there.

This should enable capture from the Microphone. I found that the built in mixer to Gnome was absolutely useless in this capacity.

Oh, in addition, if you want your bass/treble controls to work, in the playback section, unmute Tone. Then, in your capture section, adjust the Bass/Treble

---

### Post by garybrlow on 2007-04-06
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/80531](https://bugs.launchpad.net/ubuntu/+bug/80531) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Its a long standing ALSA bug mainly in feisty but the same version might have been applied via updates in edgy/dapper so its related. I myself have no mic/sound capture/recording capabilities as of the moment. Sound capture(mic input etc.) and sound recording features should be working right out of the box like before with no tweaking applied.

Please Read, Review, Confirm the bug and related info here
[https://bugs.launchpad.net/ubuntu/+bug/80531](https://bugs.launchpad.net/ubuntu/+bug/80531). Don't forget to register at launchpad.net if you already haven't done so to post/confirm bugs there and help Ubuntu become better.

Cheers!!!


GaryBrlow :biggrin:

---

