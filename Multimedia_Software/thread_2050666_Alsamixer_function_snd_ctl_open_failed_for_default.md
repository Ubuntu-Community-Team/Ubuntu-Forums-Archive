---
title: "Alsamixer: function snd_ctl_open failed for default: No such file or directory!"
date: 2012-08-31
forum: Multimedia Software
---

### Post by greatsirkain on 2012-08-31
Hi, I realise this posts been dead for a while but it's the closest I've been to an answer.
I've been a windows user since 95 and learned to loath microsoft so any response should be as if you're talking to a retarded chipmunk (seriously, I spent a whole day looking for the task manager).

Here's some details:
lspci | grep audio
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)

aplay
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'
ALSA lib conf.c:4184:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:4184:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:4184:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:4663:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM default
aplay: main:660: audio open error: No such file or directory

sudo lshw -C multimedia
*-multimedia UNCLAIMED  
       description: Multimedia audio controller
       product: 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller
       vendor: Intel Corporation
       physical id: 1f.5
       bus info: pci@0000:00:1f.5
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: ioport:ee00(size=256) ioport:edc0(size=64) memory:feb7fa00-feb7fbff memory:feb7f900-feb7f9ff

I tried:
  	 	 	 	 	 	   sudo nano /etc/modprobe.d/alsa-base
and adding this as the last line:
Code:
"options snd-intel8x0 ac97_quirk=3"
  along with various other things like purging ALSA &

sudo modprobe snd- (tab) displays 167 sound card drivers but mine isn't one of them

pulseaudio
E: [pulseaudio] pid.c: Daemon already running.
E: [pulseaudio] main.c: pa_pid_file_create() failed.


wmmixer
wmmixer : Unable to open mixer device /dev/mixer'.

All of this started when I tried to fix the right speaker that wasn't working (which still does using a live ubuntu cd) by updating it, I also downloaded and installed all the latest releases from their site and used psynaptic to get everything alsa related, nothing has worked, if I could afford to buy a new card (or even better a new pc) I would, I know the sound is onboard, it's a Dell optiplex 7...something, slimline version...annoyingn this is I think I still have the soundmax.exe drivers for windows on disk somewhere, sorry for the long post but any help would be appreciated

---

### Post by oldos2er on 2012-08-31
Post moved to its own thread.

---

