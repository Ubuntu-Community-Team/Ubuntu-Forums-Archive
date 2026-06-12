---
title: "Help with Trident 4DWave DX-1 Sound Card"
date: 2007-02-15
forum: Multimedia &amp; Video
---

### Post by AKM on 2007-02-15
Well, I've spent a couple hours searching the 'net for help... finally feel like I'm at the point where I need to make a post.

I fresh installed Ubuntu 6.10 Edgy on this machine last night from CD. Ran the update download today. I still have no sound. The little speaker icon in the upper right screen is crossbar'd out, and under the System... Preferences... Sound... there is still no Default Sound Card. The whole reason I'm building this PC for Ubuntu is to use it as a music PC (Pandora, MP3s, etc). I'd like to leave the Trident card in it.

I've tried various ALSA things dealing with the trident card. Including what the alsa-project procedure recommended, along with modprobe trident, etc... Still no sound.

Here is the result of an aadebug script:

{Paste}

./aadebug.scr: line 2: ALSA Audio Debug v0.1.0 - Thu Feb 15 23:07:11 CST 2007: command not found
[http://alsa.opensrc.org/aadebug](http://alsa.opensrc.org/aadebug)
[http://www.gnu.org/licenses/gpl.txt](http://www.gnu.org/licenses/gpl.txt)

Kernel ----------------------------------------------------
Linux shop 2.6.17-11-generic #2 SMP Thu Feb 1 19:52:28 UTC 2007 i686 GNU/Linux

Loaded Modules --------------------------------------------
snd_trident            46724  0 
snd_ac97_codec         97696  1 snd_trident
snd_ac97_bus            3456  1 snd_ac97_codec
snd_pcm_oss            47360  0 
snd_mixer_oss          19584  1 snd_pcm_oss
snd_pcm                84612  3 snd_trident,snd_ac97_codec,snd_pcm_oss
snd_timer              25348  1 snd_pcm
snd_page_alloc         11400  2 snd_trident,snd_pcm
snd_util_mem            6016  1 snd_trident
snd_mpu401_uart        10240  1 snd_trident
snd_rawmidi            27264  1 snd_mpu401_uart
snd_seq_device          9868  2 snd_trident,snd_rawmidi
snd                    58372  9 snd_trident,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device

Modprobe Conf ---------------------------------------------
alias char-major-116 snd
alias snd-card-0 snd-trident
alias char-major-14 soundcore
alias sound-slot-0 snd-card-0
alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss

Proc Asound -----------------------------------------------
Advanced Linux Sound Architecture Driver Version 1.0.12rc1 (Thu Jun 22 13:55:50 2006 UTC).
--- no soundcards ---
  2:        : timer
cat: /proc/asound/hwdep: No such file or directory
cat: /proc/asound/seq/clients: No such file or directory

Dev Snd ---------------------------------------------------
timer

CPU -------------------------------------------------------
model name      : AMD Athlon(tm) Processor
cpu MHz         : 598.947

RAM -------------------------------------------------------
MemTotal:       255980 kB
SwapTotal:      746980 kB

Hardware --------------------------------------------------
00:00.0 Host bridge: VIA Technologies, Inc. VT8371 [KX133] (rev 02)
00:07.4 Host bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 30)
00:08.0 Multimedia audio controller: Trident Microsystems 4DWave NX (rev 02)

{End Paste}

an (abridged) lspci yields:

00:08.0 Multimedia audio controller: Trident Microsystems 4DWave NX (rev 02)

So my system is seeing the card... but the drivers aren't loading for some reason.

Can anyone point me in a another direction that I can take with this?

Mucho thanks!

Andrew

---

### Post by mokh_mokh on 2007-04-07
tnxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx

---

### Post by deadgobby on 2007-04-07
If you had sound before the update and no longer. try reinstalling ALSA and see if it works again

Gobby

---

### Post by deadgobby on 2007-04-07
[http://library.pantek.com/Miscellaneous/The%20Linux%20Documentation%20Project/HOWTO/Alsa-sound-3.html](http://library.pantek.com/Miscellaneous/The%20Linux%20Documentation%20Project/HOWTO/Alsa-sound-3.html)

---

