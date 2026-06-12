---
title: "What am I doing wrong? Ralink USB dongle"
date: 2009-01-05
forum: Networking &amp; Wireless
---

### Post by DaveyR on 2009-01-05
Hey guys, I got a USB dongle called 'Azureware Pro N' and been trying to get it working on ubuntu (currently on ethernet). As soon as I plugged it in, it didnt get recognized and the light won't flash.

Looked around a bit and discovered I had to type in terminal: lsusb to see if ubuntu recognizes that it is plugged in. the entry reads:

**Bus 003 Device 002: ID 148f:2770 Ralink Technology, Corp. **

I've tried looking for the list on the ndiswrapper website for most appropriate driver, but it appears down. I googled '148f:2770' and found this entry here:

[http://www.qbik.ch/usb/devices/showdev.php?id=4477](http://www.qbik.ch/usb/devices/showdev.php?id=4477)

Which suggested I use the 'RT2870' drivers from the supplier. 

From what I understand from the forums is that I need to download ndiswrapper and the GUI (check), find the driver (check) and extract the inf. and .sys files. It is at this point I need help.

I cannot find the appropriate files from the linux driver. cannot crack open the .exe and cannot find the files in windows to bring over to linux.

I also have the cd the first driver came in, and if possible, would rather use this driver then any updated one. I downloaded a new version of it on vista, only to lose my connection and reverted back to the one it came with.

---

### Post by DaveyR on 2009-01-05
quick update: I've just discovered 'wine' and tried to extract the files there. All went well until the installer ask I stick the device in. Seeing as the OS does not play the device as soon as it is plugged, the installer ended (*drats*) before I could hopefully extract the installed driver files.

(PS: could I REALLY download and play any .exe file with wine? that's amazing!)

---

### Post by DaveyR on 2009-01-06
Help anyone?

---

### Post by DaveyR on 2009-01-06
Update: I manage to FIND the sys and inf files afterall! Searched my vista partition from ubuntu! Stupid, stupid me! Loaded the inf file into ndiswrapper. restarted and now when i type:

```
ndiswrapper -l
```

It comes out with this:

```
netr28u : driver installed
	device (148F:2770) present
```

However, wireless still no work? I'm now at me wits end now!

Now, I'm close to giving up. If no one could help me, could anyone at least recommend a good cheap Plug'n'Play usb dongle that will 100% works in xubuntu 64bit, hassle free? Thanks.

---

### Post by grumpymole on 2009-01-22
I have this device as well.  Same problem.  Did you get any further?

Cheers

---

### Post by Gadgetguy on 2009-02-03
You might try the drivers for the TRENDnet TEW-644UB.
That is showing up on my Linux Mint 6.0 ( Ubuntu variant ) with lsusb as:

# lsusb
Bus 005 Device 005: ID 148f:2770 Ralink Technology, Corp. 

The drivers are here.  I'm using the XP driver, but there is a Vista x64 in addition to an x86 version.

The drivers are located here:
[http://trendnet.com/langen/products/proddetail.asp?prod=155_TEW-644UB&cat=66](http://trendnet.com/langen/products/proddetail.asp?prod=155_TEW-644UB&cat=66)

I'm only showing a 54Mb connection, on a 11n device, so it may actually be running as a 11g.  Regardless, it is running.

Good luck,
Gadgetguy

---

