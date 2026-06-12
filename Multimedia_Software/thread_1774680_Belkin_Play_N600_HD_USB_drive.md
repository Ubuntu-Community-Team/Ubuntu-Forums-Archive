---
title: "Belkin Play N600 HD USB drive"
date: 2011-06-03
forum: Multimedia Software
---

### Post by gambothell on 2011-06-03
Hi All -

I purchased a Belkin Play N600 HD router, which is a dual band router. This router has two usb ports that you can hook a printer or usb hd to. Belkin states that they do not support Linux (odd since the router runs Linux). I was having a heck of a time trying to connect to the usb hd from my Ubuntu 11.04. I called Belkin tech support and was told curtly that they would not help me because they do not support Linux. Sigh.

After some investigation I got it working. By the way, it runs better under Ubuntu then Windows Vista... This is what you must do:

1.  Make sure you have Samba installed properly. Follow the instructions in:
[http://ubuntuforums.org/showthread.php?t=1169149&highlight=smb+ports](http://ubuntuforums.org/showthread.php?t=1169149&highlight=smb+ports)
2.  Click on Places and Network to open Nautilus.
3.  Click on the menu GO and select Location
4.  Type: smb://ip_addr/hd_name
    Example: In Windows my usb drive is labeled **Seagate_Replica(A1)** and my router address is 192.168.2.1, so the smb is: smb://192.168.2.1/seagate_resplica(a1)

You should now see the usb hd mounted where you can get to your music, pictures etc.:)

Also: when you want to mount the usb hd again, when you click on GO, you will see the smb link in the history at the bottom of the dialog.

---

### Post by nightbeing86 on 2011-07-27
Hey,

thanks very much for the info. I'm considering getting that router and already suspected that beneath Belkin's Windows-only storage tool there's nothing but old SMB/CIFS at work :)

Have you tried setting up a printer? Because I'd really need that functionality as well. And Belkin does of course say that it's Win/Mac only, just like with USB storage.

---

### Post by silvertuna on 2011-07-29
I have the same question. I tried the following string (lifted the name of the printer off a MacBook path that worked), but no luck. 

smb://192.168.2.1/usb://Hewlett-Packard/HP%20LaserJet%201022?serial=JM0154W

---

### Post by nightbeing86 on 2011-08-01
@silvertuna

what happens if you just enter the IP of your router as *host* in the *New Printer* setup wizard and let it search for whatever kind of networked printer it might find?

This worked for me with the old router I might want to replace with the Belkin...

---

### Post by gambothell on 2011-08-01
I have not installed a printer on my router, but for a usb drive, you do not put usb in the location; just enter the ip address/disk-name or printer name.

I have found an issue with the router. As posted earlier, I have a seagate 2tb usb drive connected. When I update data on the drive, sometimes the drive will not reflect the changes unless I unplug the usb and replug it. I do not know if the problem is with Belkin or with Seagate. Anyone else run into this issure with a usb drive on this router?

---

