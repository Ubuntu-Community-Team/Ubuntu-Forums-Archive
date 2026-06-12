---
title: "Wireless problem - Belkin n F5d8053"
date: 2010-11-20
forum: Networking &amp; Wireless
---

### Post by joeblurton on 2010-11-20
Hi guys,

A truckload of kudos to anyone who can figure this out! I'm trying to set up my new BT Home Hub under Lucid on my desktop. My laptop is working perfectly but I'm struggling with USB adapters.

I have an Edimax EW-7318Ug which has been playing up for a while - it's very eccentric and sometimes just disappears, although it can connect to the wifi briefly.

To remedy this I bought a Belkin n F5d8053 adaptor, but it's simply not showing the HomeHub signal. It shows Fon and OpenZone, but not the HomeHub. It won't connect to either.

I have tried unencrypting the connection - this makes the Wifi visible but still not connectable. I've tried renaming the hotspot name, everything, and still I can't connect. The HomeHub is set to Automatic b/g/n and works flawlessly on the laptop. When visible, the HomeHub hotspot shows full signal.

Any clues as to how I can fix this and get the desktop connected?

Many thanks,

Joe.

---

### Post by joeblurton on 2010-11-20
Well, I seem to have narrowed the problem down. I hauled out a creaking old Pentium 3 laptop from a cupboard running XP, and downloaded the Belkin drivers for that. I've bridged the connection and now have that laptop acting as a server for the desktop. Seems massively wasteful, but it'll have to do for now.

Does anyone know if using ndiswrapper will conflict with the automatic driver stack in Ubuntu?

---

### Post by joeblurton on 2010-11-20
I managed to fix it (sort of) with the instructions here: [http://ubuntuforums.org/showthread.php?t=1470384]("http://ubuntuforums.org/showthread.php?t=1470384")

It still won't connect to an encrypted network, but it'll do for now.

---

### Post by Sigmarr on 2010-11-22
First thing I am a Ubuntu beginner and there may be a better way of doing this but I have the same Belkin hardware you have and this is how i got mine working.

1. Download the Belkin driver exe for your ver.XXXX (I have a v5000)

2. Download the RAR package for your Archive Manager (search RAR in the Software Center) if you do not have it.

3. Rename the driver file extension from .exe to .rar and open with archive manager

4. Inside the F5D8053vXXXX file you will find a folder named WinXP2K extract this folder to your home directory

I assume you have ndiswrapper installed

5. Go to System -> Administration -> Windows Wireless Drivers

6. Select Install New Driver and select the .inf file in the folder you extracted to your home folder (mine was named net8192u.inf)

7. Now I did all that from the terminal so i am not sure if it sets the driver for the hardware automaticly if not open a terminal and enter
```
lsusb
```you will see something like this
```
Bus 001 Device 002: ID XXXX:XXXX Belkin Components
```you will need the ID XXXX:XXXX for the next step

now enter
```
ndiswrapper -a XXXX:XXXX net8192u
```Note that your driver file name may be different than mine depending on the version of the hardware so replace as needed.

Hope this helps you out!

---

