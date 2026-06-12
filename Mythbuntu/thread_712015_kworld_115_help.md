---
title: "kworld 115 help"
date: 2008-03-01
forum: Mythbuntu
---

### Post by 4dognight on 2008-03-01
I installed a kworld 115 tuner , and have it finally recoginized in  myth, by reading various posts, as a DVB card type.. 

When I go to have it scan for channels , it never picks any up. I have tried QAM64,128,256. I tried both coax inputs on the card too.

Can someone tell me what they used to get it to pick up channels, for the channel scan.

Im using cable, not atsc. And I would like it to pick up the analog channels too.

---

### Post by lionsnob on 2008-03-01
I had the same issue.  You have to follow the instructions [here]("http://mythtv.org/wiki/index.php/Kworld_ATSC_110").  Note that the instructions for the 110 and 115 are nearly identical. but there are certain portions that differ between the 110 and 115.

---

### Post by thecoolcat on 2008-03-01
Getting NTSC to work on this card using mythtv is pretty involving. Is it first working using tvtime? If you are also trying to get ATSC, try it out using mplayer first.
You can use this thread to help you:
[http://ubuntuforums.org/showthread.php?t=643415](http://ubuntuforums.org/showthread.php?t=643415)

---

### Post by 4dognight on 2008-03-01
> **lionsnob said:**
> I had the same issue.  You have to follow the instructions [here]("http://mythtv.org/wiki/index.php/Kworld_ATSC_110").  Note that the instructions for the 110 and 115 are nearly identical. but there are certain portions that differ between the 110 and 115.

That is the site I used to get it Mythtv to identify the card. I have Myth recognizing the card. It just doesnt pick up any channels., when I am configuring it in the backend. 

I would like to know what others used in the config to get it to scan for channels correctly.

---

### Post by 4dognight on 2008-03-01
> **thecoolcat said:**
> Getting NTSC to work on this card using mythtv is pretty involving. Is it first working using tvtime? If you are also trying to get ATSC, try it out using mplayer first.
You can use this thread to help you:
[http://ubuntuforums.org/showthread.php?t=643415](http://ubuntuforums.org/showthread.php?t=643415)

I can get it to work in tvtime. Although it only goes up to channel 125, even though i selected 'cable + channel 100+'. n]No QAM channels :-(

---

### Post by newlinux on 2008-03-01
You setup the card type right in your /etc/modules correct? And you are doing a full scan with a cable frequency table (not high or low) and letting it complete? If not, tell us all of the scan settings you have tried.

I don't think tvtime won't tune digital channels.
The way to test it outside of myth is to use dvb-utils

---

### Post by 4dognight on 2008-03-01
Here is my /etc/modules
fuse
lp
saa7134-dvb
saa7134-alsa

And my /etc/modprobe.conf
alias char-major-81 videodev
alias char-major-81-0 saa7134
options saa7134 card=90 disable_ir=1

OK, I dont know why, but now I got it to tune in the QAM channels. There were so many diferent variables, I might have missed one. What I ended up with was 
Scan type=full
frequency table=cable hrc
atsc modulation=cable QAM 256

BUT!  I have NO sound!  Argggg!

I tried setting these as stated in the tutorial

 v4lctl -c /dev/video0 setattr automute off
 v4lctl -c /dev/video0 volume mute off

I do see this in the log,
2008-03-01 18:38:13.233 NVP: Disabling Audio, params(-1,2,44100)

Any ideas?

---

### Post by 4dognight on 2008-03-01
I also noticed these messages from dmesg.

[   18.748000] nxt2004: Firmware upload complete
[   20.868000] saa7134_alsa: disagrees about version of symbol snd_ctl_add
[   20.868000] saa7134_alsa: Unknown symbol snd_ctl_add
[   20.868000] saa7134_alsa: disagrees about version of symbol snd_pcm_new
[   20.868000] saa7134_alsa: Unknown symbol snd_pcm_new
[   20.868000] saa7134_alsa: disagrees about version of symbol snd_card_register
[   20.868000] saa7134_alsa: Unknown symbol snd_card_register
[   20.868000] saa7134_alsa: disagrees about version of symbol snd_card_free
[   20.868000] saa7134_alsa: Unknown symbol snd_card_free
[   20.868000] saa7134_alsa: disagrees about version of symbol snd_pcm_stop
[   20.868000] saa7134_alsa: Unknown symbol snd_pcm_stop
[   20.868000] saa7134_alsa: disagrees about version of symbol snd_ctl_new1
[   20.868000] saa7134_alsa: Unknown symbol snd_ctl_new1
[   20.872000] saa7134_alsa: disagrees about version of symbol snd_card_new
[   20.872000] saa7134_alsa: Unknown symbol snd_card_new
[   20.872000] saa7134_alsa: disagrees about version of symbol snd_pcm_lib_ioctl
[   20.872000] saa7134_alsa: Unknown symbol snd_pcm_lib_ioctl
[   20.872000] saa7134_alsa: disagrees about version of symbol snd_pcm_set_ops
[   20.872000] saa7134_alsa: Unknown symbol snd_pcm_set_ops
[   20.872000] saa7134_alsa: disagrees about version of symbol snd_pcm_hw_constraint_integer

---

### Post by 4dognight on 2008-03-01
ok, now i feel stupid. my speakers were turned all the way down!  I do still have those messages that i posted though. not sure if they mean anything bad. 

So , is it worth getting the analog tuner to work on this tuner? If both cant be active at the same time, Im thinking its not worth it.  I still have my pvr500 anyway. I will just use this tuner for the HD local channels.

---

### Post by 4dognight on 2008-03-05
OK, Now that I have recovered from my embarasment of having my speakers tuned off. I need to figure out how to get these channels on this tuner in the EPG to have some useful meaning.

My tuners all show up as 'UNKNOWN 105#1' for example.
Plus they have no schedules. This kind of makes it useless for recording and searching. How do I get schedules for these channels from this tuner?

I have a schedules direct account and  have tried all the possible lineups, to no avail.:confused:

---

### Post by newlinux on 2008-03-05
What I do is into the  channel editor (in mythtv-setup, mythweb, or in the frontend channel editor), and enter the actual XMLTVID for each of these channels (for instance, if 105#1 is actual your local NBC affiliate, I'd put in the XMLTVID for your local NBC affiliate - you can get that from schedules direct). 
Pick a lineup that has all the channels you get via QAM in schedules direct. Then run 
```

mythfilldatabase --do-channel-updates

```

Which will update the channel call sign and number to match what is in schedules direct, and then you will get guide data that makes sense.

---

### Post by dsbw on 2008-03-28
There was no "Broadcast" lineup for your area?

---

