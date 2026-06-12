---
title: "i810_audio soundcard not identified"
date: 2005-10-15
forum: Multimedia &amp; Video
---

### Post by JensenDK on 2005-10-15
Hi,

(fyi: this is a repost of a post in the laptop forum that gave no results, hoping this forum might yeild better results)

I've just installed breezy on my Dell Latitude C640 (app. 3 years old) and everything seems to be working out of the box except the sound. It seems that breezy does not recognise the sound hardware on this machine. 

Under the volume control it states that no sound hardware was found and everywhere else I am getting "no default soundcard found". (I think thats it, im running a danish version of breezy so the english text might be different. 

Lspci is giving me the following output:

```

0000:00:00.0 Host bridge: Intel Corp. 82845 845 (Brookdale) Chipset Host Bridge (rev 04)
0000:00:01.0 PCI bridge: Intel Corp. 82845 845 (Brookdale) Chipset AGP Bridge (rev 04)
0000:00:1d.0 USB Controller: Intel Corp. 82801CA/CAM USB (Hub #1) (rev 02)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 42)
0000:00:1f.0 ISA bridge: Intel Corp. 82801CAM ISA Bridge (LPC) (rev 02)
0000:00:1f.1 IDE interface: Intel Corp. 82801CAM IDE U100 (rev 02)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
0000:02:00.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
0000:02:01.0 CardBus bridge: Texas Instruments PCI1420
0000:02:01.1 CardBus bridge: Texas Instruments PCI1420

```

I've gotten the information from linux-on-laptops.com that we are looking at a: 

 # Sound (i810_audio module in 2.4 kernels)
Multimedia audio controller: Intel Corp. AC'97 Audio Controller (rev 02)

And furthermore from this page from a guy that runs debian on his the following description on how to get it working ([http://comcap.free.fr/c640.html](http://comcap.free.fr/c640.html))

```

With a 2.4 kernel, add
alias sound-slot-0 i810_audio
to /etc/modutils/aliases and run update-modules afterwards. You should
chmod go+rw /dev/dsp; chmod go+rw /dev/mixer
if you want normal users to be able to play sounds.

```

The above did not work for me (probably because it was on a different system). 

I've read the following description from another running it on debian woody:

```

You can get sound working by putting a line saying "i810_audio" in /etc/modules. You could also try the utility 'sndconfig', though this is not necessary. The sound device /dev/dsp is owned root.audio, so ensure that all non-root users that need to access the device are in the 'audio' group. Use the 'usermod' command.

```

That did not work either. In both instances it was pretty obvious the commands/method must be a bit different on ubuntu. 

Now to my question:

- How do I make breezy recognise my i810_audio driver compatible soundcard - I think I understand the basic principle from both of the above posts - but how do I do that on breezy.

Thanks for any suggestions

Regards

/Martin

---

