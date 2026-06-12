---
title: "Do you have Soundblaster Live and Ubuntu 8.10 Interpid Ibex?"
date: 2008-12-08
forum: Multimedia Software
---

### Post by Truckerpunk on 2008-12-08
Just wondering. Has anyone been able to get their system up and running with a Creative soundblaster Live card? I've been trying for a while now without any luck. If you have your machine running with a Soundblaster Live card (CT4830), PLEASE help me out here. My system freezes when I'm trying to boot with my soundblaster Live card plugged in, but without it everything is smooth(except for sound of cause). I running out of hope and ideas here.

---

### Post by Eddie Wilson on 2008-12-08
I do have a Soundblaster Live audio card and I really haven't had any problems. Now I'm not sure which card it is so I will have to check on that. I will let you know what I come up with.

---

### Post by kostkon on 2008-12-08
> **Truckerpunk said:**
> Just wondering. Has anyone been able to get their system up and running with a Creative soundblaster Live card? I've been trying for a while now without any luck. If you have your machine running with a Soundblaster Live card (CT4830), PLEASE help me out here. My system freezes when I'm trying to boot with my soundblaster Live card plugged in, but without it everything is smooth(except for sound of cause). I running out of hope and ideas here.
That's strange. Maybe it is a hardware issue. Maybe the card is faulty.

You could try to put the card in another PCI slot, for example.

---

### Post by Truckerpunk on 2008-12-08
I have tried two different PCI slots already... But maybe I'm just unlucky. I'll try another one or two, and post thr results here. Thanks for the replies.

---

### Post by Elfy on 2008-12-08
What you could try to do is boot with the card - let it crash - boot the livecd and then access the logs 

You can mount the drive, assume that the drive is /dev/sdxy - get the real number from running sudo fdisk -l

Make a folder and mount the drive, remember to change the number

```
sudo mkdir /media/tmp
sudo mount -t ext3 /dev/sdxy /media/tmp
```

Should be on the desktop now - open that and navigate to /var/log

Have a look at dmesg - at the end should be stuff about the card if it causeing the problem

---

### Post by Truckerpunk on 2008-12-08
I got it working!!! So Sweet!! You encouraged me to give it another try with changing PCI-slots, and it made it not crash!! But then instead there was a loud BIIIP-noise that was even worse that silence. But it turned out the even-though I had disabled the onboard caed in the BIOS it was listed in the volume control(double click volume in the panel) as AC97, and after muting it the BIIIP-sound disappeared, and only the sweet sound of the loud punk-music that was playing it the background came through my speakers!!! Great! So to sum things up, if anyone has a similar problem: Make sure that you disable the onboard-card from the BIOS AND that you mute it in the volume control. (And make sure that your PCI-slots are functional...). Thanks a lot for all the answers, and for finally letting me have the sweet freedom of Ubuntu!! THANKS!! Really appreciate it.

---

### Post by Truckerpunk on 2008-12-11
To fast there.... It isn't working after all. Just one lucky session. So still no sound through my SBLive card. Just seems like it isn't meant to be after all. The last thing to try is a clean crisp reinstall of Ubuntu 8.04 and if I manage to get it working there then avoid upgrading to 8.10.(I dosen't seem like a new release to me anyways... More like a small ad-on to 8.04).

---

### Post by kostkon on 2008-12-12
> **Truckerpunk said:**
> To fast there.... It isn't working after all. Just one lucky session. So still no sound through my SBLive card. Just seems like it isn't meant to be after all. The last thing to try is a clean crisp reinstall of Ubuntu 8.04 and if I manage to get it working there then avoid upgrading to 8.10.(I dosen't seem like a new release to me anyways... More like a small ad-on to 8.04).
At least is your system booting OK now with the soundblaster plugged in? If that's the case, then open a terminal and do a
```
lspci
```
and a
```
aplay -l
```
and post the results here, if you like.

---

### Post by pseudonym on 2008-12-12
> **Truckerpunk said:**
> So to sum things up, if anyone has a similar problem: Make sure that you disable the onboard-card from the BIOS AND that you mute it in the volume control. (And make sure that your PCI-slots are functional...).

If you properly disabled the onboard sound in the BIOS you should not be seeing it in the volume control. You might want to verify that you've actually disabled it.

Once you're sure that you have you can also do this to make sure the SB Live card is detected first -

1. Open a terminal and type gksudo gedit /etc/modprobe.d/alsa-base

2. Go to the bottom of the file and add these lines - 

options snd-emu10k1 index=0
options snd-<onboard sound module> index=1

You need to know the name of the driver for your onboard sound. You can find that out by looking at the file /usr/share/doc/alsa-base/driver/ALSAConfiguration (you'll need to unzip it first). If you're unsure just ask here again.

3. Save the file and reboot.

---

### Post by Truckerpunk on 2008-12-12
Can't boot with the SBLive card anyway. I can't figure this mess out. But the biggest problem for me was that I couldn't listen to music while a java-applet was running with my onboard card... But I found a workaround for that. If I start firefox with "aoss" in the terminal, there's sound from both the java-applet and my music-player. Still would love to have my SBLive working though. I'll probably try again anytime soon, and when that is I'll post the results you asked kostkon. Cheers, and thanks for the help.

Hey pseudonym. I tried to edit the file as you said. But once again a dead end. It just won't work. And I can't verify that it really is disabled, when I can't boot with my SBLive card. I really appreciate that you guy's are taking some time to try and help me out. All signs point to it being a hardware-error now. I really feel that I've tried everything by now. So until I get myself a new sound card I'll just use my stupid onboard card=). When I get myself a new card I'll post here how it worked out.Until then...

---

### Post by javaholic5 on 2009-03-22
My thread here may be able to help:

[LINK]http://ubuntuforums.org/showthread.php?p=6937251#post6937251[/LINK]

---

