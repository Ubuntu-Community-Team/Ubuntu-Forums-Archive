---
title: "Watch TV/Watch DVD - Audio ok, but Video is a rainbow of colors"
date: 2007-10-25
forum: Mythbuntu
---

### Post by dmfrey on 2007-10-25
After I updated my mythbuntu through the Update Manager after the final release of mythbuntu, I am now seeing a rainbow of colors when I try to watch live tv on pvr 150 or a dvd. The audio appears to be playing correctly.  Live Tv works fine over firewire from DCT-6200.

Has anyone else experienced this?  Have you been able to resolve it?

Thanks,
Dan

---

### Post by the Goat on 2007-10-25
I am getting the same error when I try to watch recordings on my gusty frontend (connecting to Feisty backend)

If I reboot the frontend recordings play fine for a while.  But after some time if I try to play any recording the audio will be fine but the screen will show a still image of random rainbow colors.

This does not seem to be related to any settings in the setup:playback menu in mythfrontend (deinterlacing on/off no change etc.).  I have the same problem for SDTV PVR-500 recordings and HDTV HDhomerun recordings.

I'm guessing this is related to the nvidia binary driver.

---

### Post by dmfrey on 2007-10-26
I started looking through the mythtvfrontend.log file and found no errors there.

I am at a loss as to why this is happening.

---

### Post by superm1 on 2007-10-26
Can one of you guys post a camera picture of this 'rainbow' so we can see a little better what is happening and assess its cause?

---

### Post by dmfrey on 2007-10-26
I am at work now, but I will try to post one sometime this evening.

---

### Post by dmfrey on 2007-10-26
I was able to run home a lunch and take these.

The first picture is attempting to watch live tv from the pvr-150.  The second is a commercial from live tv over firewire from a dct-6200.  DVDs play in the same manner as watching live tv on the pvr-150.  You can here audio without issue, but you get the rainbow screen.



Dan

---

### Post by jmatienzo on 2007-10-26
I had the same problem, I could watch livetv or a few recording but than all of the sudden it would lock the pc in a full pink screen or I would get the rainbow screen. I would have to reboot to get it working again until it would happen again. The only way I was able to fix it was to intall the [COLOR="Red"]nvidia-glx[/COLOR] drivers instead of the [COLOR="Red"]nvidia-glx-new[/COLOR]. Let me know if you need more info.

---

### Post by superm1 on 2007-10-26
Can you do a test capture from /dev/videoX (where X is 0,1,2 depending on the device number you have) and see if its just in that particular recording?  If so, you may just happen to have a dying tuner :(

```
mplayer /dev/video0
```

or

```
mplayer /dev/video1
```

will let you try.

---

### Post by the Goat on 2007-10-26
> **dmfrey said:**
> I was able to run home a lunch and take these.

Dan
I can confirm that the first picture looks very similar to what I am seeing.

Dan when you get this failure does the rainbow image move at all or is it static?  Have you tried running mythfrontend directly after a reboot?  (I get no error directly after a reboot.  it only shows up after some time has passed)

Also please give a short summary of your hardware.

My hardware:
Intel Pentium D 3Ghz
asus motherboard (with nvidia nforce 3 or 4 chipset not sure which)
2xnvidia 7800GT GPU's connected in SLI (though I have never configured any SLI settings in linux)
samsung 1920x1200 LCD display driven at native resolution over DVI cable

This error is seen on my desktop machine which runs mythfrontend and connects to a separate backend (which is running feisty 7.04).
Mythfrontend ran fine on this machine when feisty 7.04 was installed.  I reformatted the harddrive and did a fresh install of Gusty 7.10, so this is not an upgrade problem.

---

### Post by the Goat on 2007-10-26
> **superm1 said:**
> Can you do a test capture from /dev/videoX (where X is 0,1,2 depending on the device number you have) and see if its just in that particular recording?  If so, you may just happen to have a dying tuner :(

```
mplayer /dev/video0
```

or

```
mplayer /dev/video1
```

will let you try.
I know 100% that my problem is not a tuner issue.  I am testing with recordings that I can watch perfectly fine on other frontend machines.

---

### Post by the Goat on 2007-10-26
> **jmatienzo said:**
> I had the same problem, I could watch livetv or a few recording but than all of the sudden it would lock the pc in a full pink screen or I would get the rainbow screen. I would have to reboot to get it working again until it would happen again. The only way I was able to fix it was to intall the [COLOR="Red"]nvidia-glx[/COLOR] drivers instead of the [COLOR="Red"]nvidia-glx-new[/COLOR]. Let me know if you need more info.

Could you give some detail on how to make this change?  Should I disable the nividia driver in the restricted drivers panel then install nvidia-glx using apt-get?

---

### Post by jmatienzo on 2007-10-26
Try installing the NVIDIA-GLX drivers, I mess with this problem for 3-4 days this week. Everything was fixed once I installed the old drivers. If you Google "pink lockup screen" you will see that the new Nvidia drivers have a bug that it's causing the problem.

---

### Post by jmatienzo on 2007-10-26
These are the steps I did:

1. apt-get remove nvidia-glx-new
2. rm  /lib/linux-restricted-modules/.nvidia_new_installed
3. apt-get install nvidia-glx

you may have to edit your xorg.conf file, I didn't have to.

By the way this is my setup:

FE1
7.10
Celeron D3.3ghz  1gb
gf6200

FE2
7.04
amd3200 1gb
gf6600

FE3
7.04
p4 2.4ghz 512mb
gf5200

BE
7.04
p42.8 512mb
7.04
2xpvr150
1xa180hd

---

### Post by dmfrey on 2007-10-26
Goat,

Here are my specs:

MythTV
Motherboard: MSI MS-7125
CPU: AMD Athlon(tm) 64 Processor 3200+ (2009.457 MHz, 512 KB cache)
RAM: 1 GB
Video Card: Asus Extreme GeForce 6200 TurboCache (256MB, PCI-E)
Hard Drive: Barracuda 7200.8 - ST3250823A 250 GB
DVD-ROM: LITE-ON DVD SOHD-16P9S

Only difference is that my dvd-rom has been replaced by a dvd-rw and I now have a pvr-150 in there as well.

When I get some time later tonight, I will see if I can get mplayer to capture from the /dev/video0.  I guess I have to kill mythfrontend when I do that, correct?  I will also see about changing from nvidia-glx-new to nvidia-glx.  Do I disable the nvidia driver in the Restricted Driver Manager?

Thanks,
Dan

---

### Post by jmatienzo on 2007-10-26
I didn't disable it in the driver manager, I just went ahead and removed it  from the command line, I believe it does the same as disabling it in the manager, plus I think just disabling it leaves the installed flag file behind. [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/106217]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/106217")

---

