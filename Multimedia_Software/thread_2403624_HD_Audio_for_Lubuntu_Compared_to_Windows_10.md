---
title: "HD Audio for Lubuntu Compared to Windows 10"
date: 2018-10-14
forum: Multimedia Software
---

### Post by kksilvery on 2018-10-14
I have recently moved from Windows 7 64bit to Lubuntu 18.4 64bit. 

The Audio is not up to mark, and it sounds more like AC97. My mother supports ALC883 and the specifications are, 

**Motherboard**: Intel G945DCCR
**Audio**: Realtek ALC883 HD Audio
**RAM**: 2GB
**Processor**: E2180 2.0 GHz

It does have [IMG]https://ibb.co/jZvQ8p[/IMG]in-built and it recognizes the Audio chipset. But, the Audio is no where near to the Windows 7 HD Audio manager. 

How to get HD Audio from Lubuntu Bionic Beaver?

-------------------------_UPDATE------------------------

My Problem: Realtek Windows Audio codec produce HD sound with high volume. I get 30% of the volume in Lubuntu compared to the Realtek Windows Audio codec and the sound quality is no where near Realtek HD Audio codec.

2nd Problem: I like the equalizer, but I don't mind having it on Lubuntu as an add-on. 

I want Realtek HD Audio Windows codec like performance on Lubuntu.

I am also using PulseAudio volume control, but the sound output is not good at all.

Audio Information: [http://www.alsa-project.org/db/?f=4d32e4280a906aab60574efe3b70684012baeac8](http://www.alsa-project.org/db/?f=4d32e4280a906aab60574efe3b70684012baeac8)

---

### Post by Autodave on 2018-10-14
Not sure what exactly you are looking /asking for.  Is it a graphic equalizer that you are seeking?  If so, there are several listed in the Software Center.

---

### Post by franny01 on 2018-10-14
You should be ok with your ALC883. Have you tried playing around with the settings or even tried alternative software in the packages especially the non-free and 3rd party There just might be what you need there. I have my AC97 disabled in bios as I shelled out for an Audigy 5/rx card to give me that Audiofile quality I needed. Ubuntu fully configure the card on installation and was up and running, however I had to set my speakers to Digital S/dpif instead of Analouge Sterio. Why it has my line out as Digital baffles me however the sound quality is spot on so I'm happy. Have a snoop around in the forums of Mint too as they are Ubuntu based also. Have found plenty of useful info there myself. I personally dual boot with Win10pro. Win10 on 1st SSD and Ubuntu on 2nd SSD. That way I can easily switch between both just by rebooting.

---

### Post by Yellow Pasque on 2018-10-15
> **Autodave said:**
> Not sure what exactly you are looking /asking for.  Is it a graphic equalizer that you are seeking?
+1
Audio quality should be the same unless you were using some kind of special DSP/enhancement in Windows. IIRC, the Windows Realtek driver control panel doesn't do anything like this except the surround effects it lets you play with.

Maybe look at alsa info just to make sure mixer settings are okay: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by kksilvery on 2018-10-16
The sound volume is very low. For example, if the Realtek Windows driver can produce output of 100%, then I am getting 30% of the volume in Lubuntu 18.04. You can check the question, I have updated it.

---

### Post by kksilvery on 2018-10-16
> **franny01 said:**
> You should be ok with your ALC883. Have you tried playing around with the settings or even tried alternative software in the packages especially the non-free and 3rd party There just might be what you need there. I have my AC97 disabled in bios as I shelled out for an Audigy 5/rx card to give me that Audiofile quality I needed. Ubuntu fully configure the card on installation and was up and running, however I had to set my speakers to Digital S/dpif instead of Analouge Sterio. Why it has my line out as Digital baffles me however the sound quality is spot on so I'm happy. Have a snoop around in the forums of Mint too as they are Ubuntu based also. Have found plenty of useful info there myself. I personally dual boot with Win10pro. Win10 on 1st SSD and Ubuntu on 2nd SSD. That way I can easily switch between both just by rebooting.

Thank you for the insights and suggestions. I am using default audio that came with the Lubuntu. I have updated the question, so make sure to read it.

---

### Post by kksilvery on 2018-10-16
> **Temüjin said:**
> +1
Audio quality should be the same unless you were using some kind of special DSP/enhancement in Windows. IIRC, the Windows Realtek driver control panel doesn't do anything like this except the surround effects it lets you play with.

Maybe look at alsa info just to make sure mixer settings are okay: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)


I think this report will help you understand my problem, and I have updated the question as well, so make sure to read it. [http://www.alsa-project.org/db/?f=4d32e4280a906aab60574efe3b70684012baeac8](http://www.alsa-project.org/db/?f=4d32e4280a906aab60574efe3b70684012baeac8)

---

