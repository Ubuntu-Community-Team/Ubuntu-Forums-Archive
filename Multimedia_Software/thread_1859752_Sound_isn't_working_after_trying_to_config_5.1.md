---
title: "Sound isn't working after trying to config 5.1"
date: 2011-10-14
forum: Multimedia Software
---

### Post by Arachan on 2011-10-14
Hello,

I know there are many threads out there about sound not working in Ubuntu. I have tried some of the suggestions people have made but I still cannot get my sound working again.

I have 5.1 surround sound speakers, and previously I had sound working, but only stereo, so only 2 channels were being sent to my 5.1 speakers. I was fiddling around with pulse audio and alsa, and I somehow managed to completely break my sound. Under the hardware tab in sound I see nothing at all now. 

Output of some recommended commands:

```

lspci -v
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
    Subsystem: ASUSTeK Computer Inc. P5KPL-CM Motherboard
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at fe9fc000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
``````


aplay -l
aplay: device_list:240: no soundcards found...
```

At the moment just having sound would be great, even if it was just 2 channels. However I would love to be able to use my 5.1 speakers in Ubuntu, I have never managed to get them working (been trying since 9.10).

Thanks in advance for any help,
arachan.

---

### Post by BicyclerBoy on 2011-10-14
When you say 5.1 surround speakers do you mean:
analogue connected passive speakers, connected by 3 x 3.5mm stereo jacks into the rear i/o panel of mobo ?

What have you been trying so far ?
Have you been experimenting with /etc/modprobe.d/alsa-base.conf modprobe options ?

There is possibly a specific modprobe option for the correct output jack-stack of this mobo..
These a possible candidates...but should try to get working with** no** options .
options snd-hda-intel model=auto
options snd-hda-intel model=6stack-digout

There is a alsa info dump script that is linked in posts by user "Lidex".
Would be useful to see the script output..

What does this show:
dmesg | grep HDA

---

### Post by Arachan on 2011-10-14
Hello,

I think the first thing I need to get straight is which alsa and pulse packages should I have installed, and which not? I found the script you mentioned (alsa-info.sh) and when I ran it I got the following:

[http://www.alsa-project.org/db/?f=737548878c5e128661b91ac1b0f7bfa257040bba](http://www.alsa-project.org/db/?f=737548878c5e128661b91ac1b0f7bfa257040bba)

Seems to be not recognising my audio chip?

And yes, my 5.1 surround is plugged in with 3 3.5mm audio jacks.

Also, dmesg | grep HDA outputs nothing. 

Thanks,
arachan.

---

### Post by BicyclerBoy on 2011-10-14
You do not seem to have any alsa kernel driver ??
You must have tried to compile the alsa kernel driver..

I would comment out these (2) lines from /etc/modprobe.d/alsa-base.conf
snd-hda-intel: model=auto
snd-hda-intel: model=6stack-digout

Then I suggest you use synaptic package manager & reinstall "linux-generic"..

This should re-instate the alsa driver & update your boot image.

Reboot & then rerun the alsa script..

---

### Post by pommie on 2011-10-15
Once you have your sound sorted, try having a look in bios to see if you need to turn 5.1 on, I found mine in 'Onboard Devices Configuration' and for some reason "HDAudio" was turned off, the default on my board is supposed to be "on" :confused:

Cheers David

---

### Post by Arachan on 2011-10-15
Hello,

BicyclerBoy: I did as you instructed and now my Ubuntu won't boot. I select it in grub as usual and it shows a bunch of output (it didn't before) and hangs there. I can ctrl+alt+f1 to login to another session, but X doesn't seem to load. I tried running "startx" but it returned an error. Any thoughts on what I could do?

pommie: My 5.1 does work, because I use it in Windows 7 (where I am now, ugh). Thanks for the suggestion though.

Thanks,
arachan.

---

### Post by BicyclerBoy on 2011-10-15
Do you have a self-compiled video driver ?

DIY compiled/installed kernel drivers of any type ??

Could try reinstall linux-image-generic linux-headers-generic.

To start gdm/X server
sudo service gdm restart

You can check/post the 
/var/log/Xorg.0.log

and look in the output from:
dmseg

---

### Post by Arachan on 2011-10-15
Hello,

I tried to update, upgrade and reinstall the packages you mentioned. However aptitude failed to connect to any of the servers. Hmm. I'm thinking that I will just download the 11.10 iso and do a clean install. Would probably be easiest at this point. 

Thanks for your help,
arachan.

---

### Post by BicyclerBoy on 2011-10-15
Sorry to hear that, sounds serious..
You must have some custom tweaks buried in there..

The log files will reveal what's going wrong for networking & X server..

---

### Post by Arachan on 2011-10-25
Hello,

Well, I did a fresh install of 11.10. Surround sound seems to work 'out-of-the-box' which is lovely. For me the last 4 versions of Ubuntu did not. I don't like Unity, so I switched to XFCE, but that's a different story.

Thanks for your help,
arachan.

---

