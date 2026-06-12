---
title: "no sound on 12.04"
date: 2012-08-22
forum: Multimedia Software
---

### Post by noconaway on 2012-08-22
EDIT: I was able to change my BIOS options and get the audio working. Thanks for your time!

Hey everyone, any help on this is greatly appreciated. I've worked on solving the problem for a day or two, but i just don't know enough about Ubuntu to be really intelligent about coming up with a solution!

I installed 12.04 a few days ago; at first the sound worked but soon after the install i was unable to get audio to come out of the speakers. I'm not sure where the source of the problem is!

When i look into my sound settings, the only output device is listed as 'dummy output' which obviously doesn't work. I've looked into this issue a fair amount: you can find reports [here]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/994746") and [here]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/908751") , for instance. two popular solutions from those pages are to get rid of pulseaudio or alsa, like so:

```
apt-get purge alsa-dha-dkms
```
or
```
pulseaudio -k
```

neither of which worked for me. i saw [here]("http://ubuntuforums.org/showthread.php?t=1316634") that it might work to totally remove and reinstall puleaudio and alsa, like so:
```
sudo update-grub
sudo apt-get remove --purge alsa-base
sudo apt-get remove --purge pulseaudio
sudo apt-get install alsa-base
sudo apt-get install pulseaudio
sudo alsa force-reload
```

but sadly this did not work either.

i went though [these]("https://help.ubuntu.com/community/SoundTroubleshooting") items, and found that those tips were unhelpful. Here is some information i got from the troubleshooting steps:

To see if Ubuntu recognizes any sound card, i did the following:
```
$ aplay -l
aplay: device_list:252: no soundcards found...
```

apparently the sound modules might be the problem. so, to try to find them, i did:
```
$ find /lib/modules/`uname -r` | grep sn
/lib/modules/3.2.0-29-generic-pae/kernel/net/netfilter/nf_conntrack_snmp.ko
/lib/modules/3.2.0-29-generic-pae/kernel/net/ipv4/netfilter/nf_nat_snmp_basic.ko
/lib/modules/3.2.0-29-generic-pae/kernel/net/bridge/netfilter/ebt_snat.ko
...
...
```

So i had the modules installed. the next step was to see if my PC's hardware was recognizing the soundcard, so i did:
```
$ lspci -v | grep -A7 -i "audio"
```
which returned a new line, like so:
```
$ lspci -v | grep -A7 -i "audio"
$
```

So i took around my BIOS setup, but couldn't find anything that looked particularly relevant. then again, i'm not sure about what i should have been looking for.

any help is appreciated!

---

### Post by jualin on 2012-08-22
Glad that it worked. Please marked your thread as solved to help others in the forum :)

---

