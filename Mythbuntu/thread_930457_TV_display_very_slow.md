---
title: "TV display very slow"
date: 2008-09-26
forum: Mythbuntu
---

### Post by WeeGraeme on 2008-09-26
I've just installed Mythbuntu, from the desktop CD.  There are a few issues I need to sort out.  The main one is that the TV display is very slow.  This is setup to receive DVB-T transmissions.  On a HD channel, each frame takes somewhere between 5 and 10 seconds to update.  On SD, it takes probably just over a second per frame.

I previously tried Knoppmyth.  I gave up on that, because I found fine tuning it very difficult.  Live TV did display at normal speed though, so I know it's not a case of the hardware being incompatible.

Despite having made attempts in the past to run Linux, I'm really still brand new to Linux and to Mythtv, so I really don't know enough to fault find.  I'm hoping someone here could point me in the right direction.

Thanks.

---

### Post by volkswagner on 2008-09-26
You will need to provide your log files and hardware description.

Logs are located /var/log/mythtv/mythfrontend.log, and /var/log/mythtv/mythbackend.log

You can also try different playback profiles (cpu-, cpu--, etc).  From mythtv frontend interface

Utilities/setup>Setup>Media Settings>Tv playback

---

### Post by DrMega on 2008-09-26
I guess it depends to some extent on the spec of your hardware.

Are you using open source display drivers or proprietary ones? Do you know if hardware acceleration is active?

What happens if you run this command in the terminal:

```

glxgears

```

And what is the output of:

```

glxinfo | grep rendering

```

---

### Post by WeeGraeme on 2008-09-26
> **volkswagner said:**
> You will need to provide your log files and hardware description.

Logs are located /var/log/mythtv/mythfrontend.log, and /var/log/mythtv/mythbackend.log

You can also try different playback profiles (cpu-, cpu--, etc).  From mythtv frontend interface

Utilities/setup>Setup>Media Settings>Tv playback

Thanks for the reply.  I think I've uploaded my files as an attachment as the front end file is 55k and the backend file is 389k.  I hope the file opens.  I haven't yet learned how to run archiving programs in Linux, so it was made using PowerZip on a Windows machine.  It's supposed to be a tar.bz2 file according to the programme.

I have:

Asus M3N78-VM AM2+ GF8200 5200MT DDR2 PCIEx16 RAID GbLAN mATX motherboard
AMD Athlon&#8482;64 X2 4850e AM2 45w Energy Efficient CPU
Dvico Fusion Dual 4 Dual Express Hybrid Digital PCI express
2 gigs Kingston DDR2
Asus EN9600GT 1GB DDR3 PCIE2.0 HDTV 2xDVI-I HDMI HDCP

---

### Post by WeeGraeme on 2008-09-26
> **DrMega said:**
> I guess it depends to some extent on the spec of your hardware.

Are you using open source display drivers or proprietary ones? Do you know if hardware acceleration is active?

What happens if you run this command in the terminal:

```

glxgears

```

And what is the output of:

```

glxinfo | grep rendering

```

Hi

glxgears produced:

4018 frames in 5.0 seconds = 801.685 FPS
4220 frames in 5.0 seconds = 840.583 FPS
4220 frames in 5.0 seconds = 841.355 FPS
4220 frames in 5.0 seconds = 842.704 FPS
4220 frames in 5.0 seconds = 843.246 FPS
4220 frames in 5.0 seconds = 843.403 FPS
4220 frames in 5.0 seconds = 843.402 FPS
4206 frames in 5.0 seconds = 840.092 FPS
4220 frames in 5.0 seconds = 843.449 FPS
4220 frames in 5.0 seconds = 843.418 FPS
4220 frames in 5.0 seconds = 843.470 FPS
4220 frames in 5.0 seconds = 841.334 FPS
4220 frames in 5.0 seconds = 843.128 FPS
4220 frames in 5.0 seconds = 843.396 FPS
4220 frames in 5.0 seconds = 843.503 FPS
4227 frames in 5.0 seconds = 843.455 FPS
4220 frames in 5.0 seconds = 843.492 FPS
4220 frames in 5.0 seconds = 843.432 FPS
4220 frames in 5.0 seconds = 843.466 FPS
4220 frames in 5.0 seconds = 843.362 FPS
4220 frames in 5.0 seconds = 843.535 FPS
4220 frames in 5.0 seconds = 843.298 FPS
4218 frames in 5.0 seconds = 842.918 FPS
4220 frames in 5.0 seconds = 842.915 FPS

glxinfo | grep rendering returned:

direct rendering:  No (If you want to find out why, try setting LIBGL_DEBUG=verbose)

I don't even know what or where glxinfo is, let alone how to set that option.

---

### Post by DrMega on 2008-09-26
> **WeeGraeme said:**
> glxinfo | grep rendering returned:

direct rendering:  No (If you want to find out why, try setting LIBGL_DEBUG=verbose)

I don't even know what or where glxinfo is, let alone how to set that option.

Ok. That explains your slow page rendering. This means that the the CPU is having to do all the work without any assistance from your graphics card.

If you are using the open source graphics driver, then direct rendering is not supported in some. In which case the solution is to use the proprietary driver. I don't know about Mythbuntu, but in ordinary Ubuntu from version 8.04 (or maybe before, not sure) there is an applet that detects your hardware and offers to configure the proprietary driver. If this isn't the case you can configure it manually with little effort, but the downside is that depending on your graphics hardware you might have a chew on getting the TV-out configured.

If you open your xorg.conf you can see what driver is in use from there. From the terminal, follow these steps and tell us what you get:

1. Open xorg.conf
```

gedit /etc/X11/xorg.conf

```

2. look for a line in the display adapter section that says something like:

```

driver = nv

```

or

```

driver = ati (or vesa or fglrx etc)

```

What does "driver" = in your case?

---

### Post by WeeGraeme on 2008-09-26
> **DrMega said:**
> Ok. That explains your slow page rendering. This means that the the CPU is having to do all the work without any assistance from your graphics card.

If you are using the open source graphics driver, then direct rendering is not supported in some. In which case the solution is to use the proprietary driver. I don't know about Mythbuntu, but in ordinary Ubuntu from version 8.04 (or maybe before, not sure) there is an applet that detects your hardware and offers to configure the proprietary driver. If this isn't the case you can configure it manually with little effort, but the downside is that depending on your graphics hardware you might have a chew on getting the TV-out configured.

If you open your xorg.conf you can see what driver is in use from there. From the terminal, follow these steps and tell us what you get:

1. Open xorg.conf
```

gedit /etc/X11/xorg.conf

```

2. look for a line in the display adapter section that says something like:

```

driver = nv

```

or

```

driver = ati (or vesa or fglrx etc)

```

What does "driver" = in your case?

It actually has neither at the moment.  I didn't realise I hadn't mentioned eaerlier that it's an Nvidia based card.  I'm in the process of installing drivers now.  It was just using the default video before.

---

### Post by DrMega on 2008-09-26
> **WeeGraeme said:**
> It actually has neither at the moment.  I didn't realise I hadn't mentioned eaerlier that it's an Nvidia based card.  I'm in the process of installing drivers now.  It was just using the default video before.

I forgot to mention, I hope its not too late, make sure you backup your xorg.conf before you do anything driver or display related.

To back it up, just do:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup*YYYYMMDD*
```

(where YYYYMMDD is the date in order of Year, month then day.

---

### Post by WeeGraeme on 2008-09-30
Thanks for the suggestion.  Unfortunatley for me, I didn't read your suggestion until after I'd made the changes.  Now when I select Watch TV, it just returns to the same menu.  It is also trying to display everything at about twice the size it should be.  My knowledge of Mythbuntu / Ubuntu is insufficient for me to rectify the problem as I don't know how to navigate around the system.

I'll start again and follow your suggestions.  At least I did think to backup the firmware for my TV card, so that's one less thing I've got to find.

---

