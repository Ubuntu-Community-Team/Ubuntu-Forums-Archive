---
title: "Yet another MCP51 problem thread"
date: 2007-07-12
forum: Multimedia &amp; Video
---

### Post by gaelfx on 2007-07-12
I would like to start by saying that I have scoured these forums for many days awaiting an answer to my particular problem, only to see other people with persistent problems not truly related to mine. I have a Compaq Presario V3000 (V3169AU revision). This was purchased in China, so it lacks some of the features such a laptop is supposed to have, according to the pdfs from Compaq's site (firewire, multimedia card-reader). I easily got my sound working using the stable release of ALSA 1.0.14, however, a problem persists in that I am unable to use the microphone that is built-in to the Conexant sound card. I know it is not safe to assume that the holes above my screen actually contain microphones, but my hardware seems to believe there is a microphone that should be capable of capture, and yet Audacity shows no activity when I turn monitor output on. Can anyone help me with this issue? I will attach my alsa-info output so I don't have to gunk up the forums with all that info. If you need any more information, please post as I will be monitoring this thread closely.

---

### Post by gaelfx on 2007-07-13
As an aside, I am having problems with the 1.4 Skype Beta, which worked when I initially installed it, but now fails on loading all sound devices. Here is term output:

>  ALSA lib ../../src/confmisc.c:1105:(snd_func_refer) Unable to find definition 'defaults.pcm.dmix.device'
ALSA lib ../../src/conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib ../../src/conf.c:3968:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib ../../../src/pcm/pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../src/confmisc.c:1105:(snd_func_refer) Unable to find definition 'defaults.pcm.dmix.device'
ALSA lib ../../src/conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib ../../src/conf.c:3968:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib ../../../src/pcm/pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM default


also **ldd /usr/bin/skype | grep not** returns absolutely nothing. I think it may have something to do with my installing ALSA 1.0.14, because it seems that it stopped working around that time, but it doesn't seem that that should be a problem. Has anyone else experienced this issue? Should I just try installing a non-Beta version? I really need some advice.

---

### Post by gaelfx on 2007-07-13
And more info, if it helps. My ALSA Audio Debug output:
> [QUOTE]ALSA Audio Debug v0.1.0 - Fri Jul 13 13:54:41 CST 2007
[http://alsa.opensrc.org/aadebug](http://alsa.opensrc.org/aadebug)
[http://www.gnu.org/licenses/gpl.txt](http://www.gnu.org/licenses/gpl.txt)

Kernel ----------------------------------------------------
Linux gaelfx-iBook2 2.6.20-16-generic #2 SMP Thu Jun 7 19:00:28 UTC 2007 x86_64 GNU/Linux

Loaded Modules --------------------------------------------
snd_hda_intel         333472  1 
snd_pcm_oss            50176  0 
snd_mixer_oss          20096  1 snd_pcm_oss
snd_pcm                93960  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy           5892  0 
snd_seq_oss            38912  0 
snd_seq_midi           11264  0 
snd_rawmidi            30208  1 snd_seq_midi
snd_seq_midi_event     10240  2 snd_seq_oss,snd_seq_midi
snd_seq                63392  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              27400  2 snd_pcm,snd_seq
snd_seq_device         10900  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    71336  12 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_page_alloc         12944  2 snd_hda_intel,snd_pcm

Modprobe Conf ---------------------------------------------
Warning: module config file does not exist
This means any kernel modules will not be auto loaded
See your linux distro docs on how to create this file

Proc Asound -----------------------------------------------
Advanced Linux Sound Architecture Driver Version 1.0.14.
Compiled on Jul  8 2007 for kernel 2.6.20-16-generic (SMP).
 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xc0000000 irq 18
  0: [ 0]   : control
  1:        : sequencer
 16: [ 0- 0]: digital audio playback
 17: [ 0- 1]: digital audio playback
 24: [ 0- 0]: digital audio capture
 33:        : timer
cat: /proc/asound/hwdep: No such file or directory
00-01: Conexant Digital : Conexant Digital : playback 1
00-00: CONEXANT Analog : CONEXANT Analog : playback 1 : capture 1
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
controlC0  pcmC0D0c  pcmC0D0p  pcmC0D1p  seq  timer

CPU -------------------------------------------------------
model name      : AMD Turion(tm) 64 
cpu MHz         : 800.000

RAM -------------------------------------------------------
MemTotal:       446260 kB
SwapTotal:     1301224 kB

Hardware --------------------------------------------------
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control[/QUOTE]

---

### Post by JustBrowsing on 2007-07-13
I'm starting to really hate my Gateway due to this MCP51 issue, no sound in an Operating System really kills its potential.

I'm trying to sell this dang laptop after just 5 months of ownership mainly due to it's hardware incompatibilities with Linux. Also, next time I'm sticking with Intel processors.

---

### Post by gaelfx on 2007-07-13
I don't think that an AMD processor presents any problems, the issue lies with the fact that most programs are not concerned with supporting 64-bit structures in their code. Granted, most applications probably have no need for 64-bit variables, and multi-threading is still barely used by most software makers. But it's still rather upsets me. Mac's XCode makes it very simple to create 64-bit compatible code, it did so almost at the same time 64-bit processors became available on the mass-consumer market, and now it's very simple to port any code into a "universal binary" that will work on intel processors (which have a completely different structure from PPC)! I wonder why other software development platforms haven't accomplished this as quickly? It seems to me that many in the industry lack of foresight and are war-hawks about backwards compatability. I think VM can solve most of those BC problems, so why are our systems still restrained by ancient pieces of code that may or may not be out there?

At any rate, don't blame AMD for things, the processors work at least as well as Intel's, in my experience. Sure, Java is a pain in the *** to run in AMD64 Ubuntu, but whose fault is it that there is no 64-bit JRE? It's not any Linux distro's job to make sure other people are keeping up with the hardwares that are becoming widely available out there. You would think Sun would get off it's behind and step up to the "challenge" of creating a viable 64-bit plugin, after all, it's in their best interest

---

