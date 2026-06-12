---
title: "Fed up to the point of hugging Bill Gates &gt;_&lt;"
date: 2009-03-02
forum: Multimedia Software
---

### Post by Vastakaiun on 2009-03-02
Help!!!

After testing out Kubuntu for a while, I decided to reinstall Ubuntu, since I prefered GNOME to KDE. Everything is working fine, apart from the age old problem: SOUND!

I have been through tons of forums and spent hours trying to fix my sound as it wasn't playing Flash in Firefox. Eventually it has ended up with me having no sound at all, not even for music or computer sounds.

My usual jack socket at the front of my laptop is broken, so I invested in a cheep jack-usb connection. I think this is where the complications lay.

My computer is a Fujitsu-Siemens Amilo Li1718 laptop, I have an Atheros.... something soundcard.

Can someone please help me by talking me through some solutions. I can paste more technical info if requested.

I really want to get this fixed so I don't have to go back to Windows (dual-booting at the minute). Any help is greatly appreciated!

---

### Post by khelben1979 on 2009-03-02
You can grab the source from [the Alsa Project Page]("http://www.alsa-project.org/main/index.php/Main_Page") and start to configure and compile up from source. But before you go this route, try with the alsaconf command first. Select your soundcard/soundchip from the list and then adjust the volume with alsamixser. Restart the machine to see if it helps. If it doesn't, well.. then you can go the long path by compiling source code.. :-)

```
sudo alsaconf
```

```
sudo alsamixer
```
then restart the system.

---

### Post by cariboo on 2009-03-02
Go to System-->Preferences-->Sound and set your usb device to be the output source. Check lsusb to see what the device number is and check for the same thing in the sound settings.

Jim

---

### Post by markbuntu on 2009-03-03
Just read this


[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

---

### Post by 5oh on 2009-03-03
Try disabling the onboard sound.

---

