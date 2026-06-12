---
title: "Soundblaster 5.1 VX installation not working"
date: 2012-04-04
forum: Multimedia Software
---

### Post by Trevor Burton on 2012-04-04
Hi All,

I have tried to follow all the guides, but so far have not got anywhere.  I have a fairly old PC running Lucid and a while ago, the onboard sound started hissing.  Speakers were perfectly OK, so I suspected a hardware fault - I bought a cheap soundblaster card and installed it today but can't get it working (it DOES work in Windows).  I've already disabled the onboard sound, reinstalled alsa several times.  Here's my diagnostics below - it seems that somethings "see" my card and others don't?

```

trevor@Thingol:~$ lspci -nn | grep '\[04[80][13]\]'
00:0a.0 Multimedia audio controller [0401]: Creative Labs CA0106 Soundblaster [1102:0007]


trevor@Thingol:~$ speaker-test

speaker-test 1.0.24.2

Playback device is default
Stream parameters are 48000Hz, S16_LE, 1 channels
Using 16 octaves of pink noise
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'
ALSA lib conf.c:4184:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:4184:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:4184:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:4663:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM default
Playback open error: -2,No such file or directory

trevor@Thingol:~$ aplay -l
aplay: device_list:240: no soundcards found...

trevor@Thingol:~$ sudo aplay -l
[sudo] password for trevor: 
aplay: device_list:240: no soundcards found...

trevor@Thingol:~$ echo "Sound cards recognized by the system:"; lspci -nn | grep --color=none '\[04[80][13]\]'; echo "Sound cards recognized by ALSA:"; lspci -nn | grep '\[04[80][13]\]' | while read line; do lspci -nnk | grep -A 3 '\[04[80][13]\]' | grep -e 'Kernel modules: ..*' -e '\[04[80][13]\]' | grep --color=none -F "$line"; done; echo "Sound cards recognized by ALSA, and activated:"; lspci -nn | grep '\[04[80][13]\]' | while read line; do lspci -nnk | grep -A 3 '\[04[80][13]\]' | grep -e 'Kernel drivers in use: ..*' -e '\[04[80][13]\]' | grep --color=none -F "$line"; done

Sound cards recognized by the system:
00:0a.0 Multimedia audio controller [0401]: Creative Labs CA0106 Soundblaster [1102:0007]
Sound cards recognized by ALSA:
00:0a.0 Multimedia audio controller [0401]: Creative Labs CA0106 Soundblaster [1102:0007]
Sound cards recognized by ALSA, and activated:
00:0a.0 Multimedia audio controller [0401]: Creative Labs CA0106 Soundblaster [1102:0007]

trevor@Thingol:~$ wget -O alsa-info.sh http://www.alsa-project.org/alsa-info.sh && chmod +x ./alsa-info.sh && ./alsa-info.sh
--2012-04-04 19:40:05--  http://www.alsa-project.org/alsa-info.sh
Resolving www.alsa-project.org... 77.48.224.243
Connecting to www.alsa-project.org|77.48.224.243|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh [following]
--2012-04-04 19:40:05--  http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh
Resolving git.alsa-project.org... 77.48.224.243
Reusing existing connection to www.alsa-project.org:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/plain]
Saving to: `alsa-info.sh'

    [  <=>                                                                                                                                   ] 27,247       127K/s   in 0.2s    

2012-04-04 19:40:06 (127 KB/s) - `alsa-info.sh' saved [27247]

ALSA Information Script v 0.4.60
--------------------------------

This script visits the following commands/files to collect diagnostic
information about your ALSA installation and sound related hardware.

  dmesg
  lspci
  lsmod
  aplay
  amixer
  alsactl
  /proc/asound/
  /sys/class/sound/
  ~/.asoundrc (etc.)

See './alsa-info.sh --help' for command line options.

cat: /proc/asound/version: No such file or directory
grep: /proc/asound/cards: No such file or directory
cat: /proc/asound/cards: No such file or directory
cat: /proc/asound/modules: No such file or directory
ls: cannot access /dev/snd/*: No such file or directory
grep: /proc/asound/cards: No such file or directory
/sbin/alsactl: save_state:1519: No soundcards found...
cat: /tmp/alsa-info.uKWqd06lxV/alsactl.tmp: No such file or directory
Automatically upload ALSA information to www.alsa-project.org? [y/N] : n


Your ALSA information is in /tmp/alsa-info.txt.UntXBeINue

```

If I run the alsamixergui program, it gives the error "alsamixer: function snd_ctl_open failed for default: No such file or directory".

I found a thread like that in the forums and followed the instructions, but no joy.

Any ideas?

Thanks, Trevor

---

### Post by Trevor Burton on 2012-04-06
bump?

---

### Post by Trevor Burton on 2012-04-07
Anybody have any ideas please?

---

### Post by bolognese on 2012-04-17
Hi Trevor,

Two weeks ago I bought this 5.1 vx card. 
My soundblaster live turned out to have become defect, as the machine did no longer want to boot with the card plugged in. Seem too have played and plugged a bit too much getting everything work.
The machine contains asus a7v333 mainboard, which is about 12 years old now. My machine did not recognize the network card for quite some time.
Maybe you should start from scratch, resetting you bios and start without anything plugged in, beside the nessecary parts.

I could make it, so you will be able too.

Good luck.

Edit: I am enjoying music from all speakers now, which is the first time running Linux and all I had to do was select the appropriate device under sound, after install and update 11.10.

Jos

---

