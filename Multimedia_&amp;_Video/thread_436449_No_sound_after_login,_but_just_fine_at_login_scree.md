---
title: "No sound after login, but just fine at login screen"
date: 2007-05-07
forum: Multimedia &amp; Video
---

### Post by Natume on 2007-05-07
I have a bit of a predicament... nothing super-critical, but more than marginally annoying.

I just finished installing a new kernel (though the old 2.6.17.11-generic is still there and for the most part working fine ; see below for the only part that isn't), to solve some issues with timer resolution and such, so now I have both 2.6.17.11-generic and a specially compiled 2.6.21.1 on my system, both of which boot up just fine.  To get sound on the latter kernel, seeing as I didn't compile ALSA or OSS in, I compiled ALSA from the latest source (1.0.14rc4) from the ALSA page (just the driver, libraries, utilities, and oss packages).  I would have used 1.0.13, or even lower (and I did try .13, .12, and .11 prior to .14rc4), but none of them made it through the 'make' after configuration, no matter what the configuration settings were.  1.0.14rc4 installed just fine though, and I loaded the snd_pcm_oss, snd_mixer_oss, snd_seq_oss, snd_emu10k1, and snd_intel8x0 modules as well as put them in /etc/modules so that they load on rebooting (which I've done several times since).  Both my built in Intel card and external PCMCIA Soundblaster Audigy card were recognized just fine, and show up in the utilities that list them.

The problem is that, despite getting sound at the login screen and the regular pops of the speakers on startup and shutdown, as soon as I actually log in, the sound shuts off.  Alsamixer works fine, as do gui utilities for adjusting sound levels, and give no errors, however, no sound comes out of either my desk or laptop speakers in any application, no matter whether I'm using the Intel or Creative sound cards.

I do, however, get a consistent set of (error) messages whenever I open up an external utility (even gedit) from the terminal.  They're as follows (and they never really change, nor do I ever get different messages) :

ALSA lib confmisc.c:1286:(snd_func_refer) Unable to find definition 'defaults.pcm.dmix.device'
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3982:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2144:(snd_pcm_open_noupdate) Unknown PCM default

Not exactly sure what these entail, other than something's screwed up.  However, there were no errors given during the configure, make, or make install of any of the ALSA stuff.  I'd like to get sound working soonish, and anything that anybody knows or a direction somebody could point me in would be much appreciated.  I've also attached the text of the output of aadebug (a script given on the ALSA troubleshooting part of the wiki there), which may be useful ; some of the data seems rather human-readable.

**************************************************

ALSA Audio Debug v0.1.0 - Mon May  7 20:31:32 EDT 2007
[http://alsa.opensrc.org/aadebug](http://alsa.opensrc.org/aadebug)
[http://www.gnu.org/licenses/gpl.txt](http://www.gnu.org/licenses/gpl.txt)

Kernel ----------------------------------------------------
Linux natume-laptop 2.6.21.1-rt #1 SMP PREEMPT Mon May 7 17:18:30 EDT 2007 i686 GNU/Linux

Loaded Modules --------------------------------------------
snd_intel8x0           36892  0 
snd_emu10k1_synth       9088  0 
snd_emux_synth         40576  1 snd_emu10k1_synth
snd_seq_virmidi         9600  1 snd_emux_synth
snd_seq_midi_emul       8320  1 snd_emux_synth
snd_seq_dummy           5252  0 
snd_seq_oss            39296  0 
snd_seq_midi           10272  0 
snd_seq_midi_event      9344  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                60752  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_emu10k1           145856  1 snd_emu10k1_synth
snd_rawmidi            27424  3 snd_seq_virmidi,snd_seq_midi,snd_emu10k1
snd_ac97_codec        108196  2 snd_intel8x0,snd_emu10k1
snd_seq_device         10252  8 snd_emu10k1_synth,snd_emux_synth,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_emu10k1,snd_rawmidi
snd_util_mem            6272  2 snd_emux_synth,snd_emu10k1
snd_hwdep              11652  2 snd_emux_synth,snd_emu10k1
snd_hda_intel         256408  1 
snd_pcm_oss            47904  0 
snd_mixer_oss          19200  1 snd_pcm_oss
snd_pcm                87300  5 snd_intel8x0,snd_emu10k1,snd_ac97_codec,snd_hda_intel,snd_pcm_oss
snd_timer              26244  3 snd_seq,snd_emu10k1,snd_pcm
snd                    61540  18 snd_intel8x0,snd_emux_synth,snd_seq_virmidi,snd_seq_dummy,snd_seq_oss,snd_seq,snd_emu10k1,snd_rawmidi,snd_ac97_codec,snd_seq_device,snd_hwdep,snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
snd_page_alloc         12040  4 snd_intel8x0,snd_emu10k1,snd_hda_intel,snd_pcm

Proc Config -----------------------------------------------
CONFIG_SOUND=y
# CONFIG_SND is not set
# CONFIG_SOUND_PRIME is not set

Modprobe Conf ---------------------------------------------
Warning: module config file does not exist
This means any kernel modules will not be auto loaded
See your linux distro docs on how to create this file

Proc Asound -----------------------------------------------
cat: /proc/asound/{version,cards,devices,hwdep,pcm,seq/clients}: No such file or directory

Dev Snd ---------------------------------------------------
controlC0  hwC1D2    midiC1D2  pcmC0D0p  pcmC0D6p  pcmC1D1c  pcmC1D3p
controlC1  midiC1D0  midiC1D3  pcmC0D2c  pcmC1D0c  pcmC1D2c  seq
hwC1D0	   midiC1D1  pcmC0D0c  pcmC0D6c  pcmC1D0p  pcmC1D2p  timer

CPU -------------------------------------------------------
model name	: Intel(R) Pentium(R) 4 CPU 3.00GHz
cpu MHz		: 2992.732
model name	: Intel(R) Pentium(R) 4 CPU 3.00GHz
cpu MHz		: 2992.732

RAM -------------------------------------------------------
MemTotal:      2040976 kB
SwapTotal:     1381580 kB

Hardware --------------------------------------------------
00:00.0 Host bridge: Intel Corporation 915G/P/GV/GL/PL/910GL Express Memory Controller Hub (rev 04)
0b:00.0 Multimedia audio controller: Creative Labs SB0400 Audigy2 Value

---

### Post by gilkyboy on 2007-05-11
I have the exact same problem, any luck on solving it yet?

---

### Post by gilkyboy on 2007-05-12
I managed to fix my sound by finding a pretty basic error.  My user wasn't part of the audio group.  Before beating yourself over the head, try that :)

---

### Post by Natume on 2007-05-14
Ah, thanks for the tip.  I'll have to try that after ... uh... I reinstall the kernel again.  {chuckles} Linux kinda died on me when I went to uninstall the 1.0.14rc(whatever the number is) drivers etc. in 2.6.17-11.  I'm assuming it's an issue because I installed them while in 2.6.21.1.  In any case, when I work up the courage (and find the free time in case I need to reinstall Linux again ; only took 7 hours or so last time) to try the new kernel again, I'll see how modifying the user groups works.

---

