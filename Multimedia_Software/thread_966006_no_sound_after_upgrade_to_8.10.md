---
title: "no sound after upgrade to 8.10"
date: 2008-11-01
forum: Multimedia Software
---

### Post by acegik on 2008-11-01
After I upgrade to 8.10 I lost the sound on my speakers. I have an inboard intel Chip HDA that controls the sound. I have tryed alsamixer command with no results. I have tryed lspci-v and aplay-l and it shows that my sound chip is recognized, but still there is no sound
Can you help me please?

---

### Post by slava_ on 2008-11-01
> **acegik said:**
> After I upgrade to 8.10 I lost the sound on my speakers. I have an inboard intel Chip HDA that controls the sound. I have tryed alsamixer command with no results. I have tryed lspci-v and aplay-l and it shows that my sound chip is recognized, but still there is no sound
Can you help me please?

I had the same problem - everything ok (devices, alsamixer) but no sound.
You should **check the mixer** (from the tray, [Right click] speaker -> open Volume control ). I had the "_Front_ mixer" muted. I activate it, and the sound appeared.

Hope it helps.

---

### Post by acegik on 2008-11-01
Yea i've try that, I even uninstalled and reintalled the alsa files fresh, but still I have no sound at all. Speakers are working i test them already.

---

### Post by gandaran on 2008-11-01
> **acegik said:**
> After I upgrade to 8.10 I lost the sound on my speakers. I have an inboard intel Chip HDA that controls the sound. I have tryed alsamixer command with no results. I have tryed lspci-v and aplay-l and it shows that my sound chip is recognized, but still there is no sound
Can you help me please?
upgrading sometimes breaks thinks, it's best a fresh install

---

### Post by siDDis on 2008-11-01
same problem here, I also have a Intel HDA never had a problem with it before I upgraded.
I'm using spdif for all sound, but I only hear sound when its true digital sound as AC3 or DTS. I managed to get it to work after 2 hours with typing and loud flaming, but it broke again after a reboot :(
I think it have something todo with Pulseaudio but not sure.

---

### Post by matt_is_rockin on 2008-11-01
Had the same problem, same Intel HDA card in my laptop.

Just managed to fix it by downloading the package GNOME ALSA Mixer. The Master was up, but PCM was down. Turning this up was the key in my case.

Hope this helps someone.
Matt

---

### Post by Cod on 2008-11-01
Thanks matt_is_rockin, I had the same problem.  Can't believe I missed it.  I've had major problems with the upgrade so just thought it was one in the long line of hassles I've had.  Fixed now.  Cheers.

---

### Post by acegik on 2008-11-01
> **matt_is_rockin said:**
> Had the same problem, same Intel HDA card in my laptop.

Just managed to fix it by downloading the package GNOME ALSA Mixer. The Master was up, but PCM was down. Turning this up was the key in my case.

Hope this helps someone.
Matt

Yea, I tryed opening the volume control and pumping up all the bars and nothing I don't know what else to do!

---

### Post by ve4cib on 2008-11-01
I was having similar issues after an upgrade from 8.04 --> 8.10 (x86-64), also with an HDA-Intel soundcard.

I *think* I've solved the problem.  The details are in [this](http://ubuntuforums.org/showthread.php?p=6078737#post6078737) thread.  Basically, all I did was reinstall and reconfigure some packages, replaced my libsdl1.2 package to '*-all' (instead of the default '*-pulseaudio'), and set the everything to autodetect in System>Preferences>[Multimedia System Selector|Sound].

Not sure if it'll help you, but it might not hurt to try?

---

### Post by Brown Betty on 2008-11-01
I'm having this trouble also.  I attempted to follow the [Comprehensive Sound Solutions Guide](http://ubuntuforums.org/showthread.php?t=205449)

> $ aplay -l
aplay: device_list:215: no soundcards found...

$ lspci | grep audio
02:03.0 Multimedia audio controller: ESS Technology ES1983S Maestro-3i PCI Audio Accelerator (rev 10)

The third step in the above-linked guide sent me to the alsa documentation to see if the driver exists (I'm sure it does, since I had sound in 8.04) but the site has been reorganized since the guide was written and I couldn't find any list.

I'm not sure where to go from here.

---

### Post by gg234 on 2008-11-01
try this fix menctioned in the article for sound issue [http://www.ubuntugeek.com/common-problems-and-solutions-for-nvidia-restricted-drivers-after-ubuntu-810-intrepid-ibex-upgrade.html](http://www.ubuntugeek.com/common-problems-and-solutions-for-nvidia-restricted-drivers-after-ubuntu-810-intrepid-ibex-upgrade.html)

---

### Post by Mombo on 2008-11-01
Go figure I was have sound problems and I was trying everything I could find and it was just something muted in my mixer the whole time. Thanks for pointing me in such an obvious direction #2

---

### Post by everytimeref on 2008-11-03
> **Mombo said:**
> Go figure I was have sound problems and I was trying everything I could find and it was just something muted in my mixer the whole time. Thanks for pointing me in such an obvious direction #2

Yeah, I laughed at this and thought "what a complete doofus" then I checked and had the same problem:oops::oops::oops::oops:

Well, almost, there was a button that had digital out switched on, I unclicked that and we were back in the groove.

know to work out why intrepid can't see my camera...

---

