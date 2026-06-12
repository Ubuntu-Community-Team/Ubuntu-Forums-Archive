---
title: "Fuzzy Audio through m-Audio Fast Track"
date: 2011-04-27
forum: Multimedia Software
---

### Post by undfined on 2011-04-27
I recently built a machine with a Zotac GeForce 8200-ITX motherboard and a m-Audio Fast Track (not the PRO version).

While this was working on my previous machine flawlessly, now I get a layer of fuzz over my music that doesn't go away.  Sometimes I can play 1 song, sometimes I can get through several before the fuzz starts.  Rebooting is the only thing that fixes it.

I tried 10.10 and just now the 11.04 beta, after resetting my BIOS to the fail-safe defaults.

Any thoughts?

---

### Post by lidex on 2011-04-27
Try resetting your pulse configuration.
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Reboot**

---

### Post by undfined on 2011-04-28
me@Walrus:~$ rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
rm: cannot remove `/home/me/.pulse': No such file or directory
rm: cannot remove `/home/me/.asound*': No such file or directory
rm: cannot remove `/home/me/.pulse-cookie': No such file or directory
me@Walrus:~$ sudo rm /etc/asound.conf
rm: cannot remove `/etc/asound.conf': No such file or directory
me@Walrus:~$

dmesg is attached.

---

### Post by undfined on 2011-04-28
I am trying the new release of 11.04 and will report back.  However, the updates that just came through about an hour ago did not work either.

No luck on 11.04 either.  Sounds great for a little while then gets noisy.  All I'm playing are mp3s.

---

### Post by undfined on 2011-04-28
I've been struggling with this for the better part of a few hours.  PulseAudio hangs and takes Banshee, Flash, and anything multimedia along with it.  I tried disabling PulseAudio through the Startup Applications but that hasn't helped.

I get a dmesg output:  usb_set_interface failed

And that line keeps repeating the longer the system is on.

edit: I am beginning to think it's the motherboard since lsusb -t showed every USB device is on one port with differing speeds.  Is that normal?

I set my BIOS to only use USB 1.1 and am testing.  No problems so far.

---

### Post by lidex on 2011-04-28
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by undfined on 2011-04-29
> **lidex said:**
> Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

[http://www.alsa-project.org/db/?f=da91796a6f9a52e64e02f0340766b328c6cf3991](http://www.alsa-project.org/db/?f=da91796a6f9a52e64e02f0340766b328c6cf3991)

Using 1.1 only didn't work.

---

### Post by undfined on 2011-04-30
lidex -

Thanks for working with me on this.  I got pretty deep into troubleshooting after your post and learning a lot about USB and ALSA.

Long story short, I'm happy to accept a motherboard incompatibility and picked up a PCI-e USB card and plugged the m-Audio into that.  Running for hours without issue.

The Zotac was letting some video noise come through the USB too, which I started noticing after the fuzz started while loading Synaptic and the screen greyed for a password.  Then after staring at a verbose, realtime pulseaudio log I just admitted suckage and got the $40 card.

I am now happily chugging along in 11.04.

---

