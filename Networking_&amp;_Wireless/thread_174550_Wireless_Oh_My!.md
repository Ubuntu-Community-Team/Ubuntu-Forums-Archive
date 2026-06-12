---
title: "Wireless Oh My!"
date: 2006-05-12
forum: Networking &amp; Wireless
---

### Post by Drunken Pirate on 2006-05-12
Hey, I am trying to get my DWL-G132 wireless USB device to work. I tried ndiswrapper to install the drivers that were supplied with my device, but it didn't work. So I tried ndisgtk 0.5, and installed the two inf files that came with the usb device. Now when I type in ndiswrapper -l, this comes up:

```

Installed ndis drivers:
athfmwdl        driver present, hardware present
neta5agu        driver present, hardware present

```

But when I got to my network config, the card dosen't show up.

So I tried modprobe ndiswrapper, and it compeleted, but again, network config shows nothing.

Here's what comes up when I run iwconfig:
```
brent@ragsdale-server-01:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

```


What can I do?

---

### Post by jml on 2006-05-12
Getting wireless working in Linux is always very challenging, and getting USB wireless devices is even harder.  I am not an expert on wireless by any means, but here is a link to Ubuntu's wireless troubleshooting guide.  Hope it helps.

[https://wiki.ubuntu.com/WirelessTroubleshootingGuide](https://wiki.ubuntu.com/WirelessTroubleshootingGuide)

Joe

---

### Post by az on 2006-05-12
[QUOTE=Drunken Pirate]Hey, I am trying to get my DWL-G132 wireless USB device to work. I tried ndiswrapper to install the drivers that were supplied with my device, but it didn't work. [/QUOTE]

I think there is a linux driver for your device that is being loaded at boot.  Did you try without ndiswrapper?  I think your problem is that ndiswrapepr and the native linux driver are both trying to use the same devicea dn that won't work.

---

### Post by Drunken Pirate on 2006-05-13
Oh, I added both of those drivers because they both came with the zip folder. Ill try just one of them at a time and see what I can get.

EDIT: Nope, trying one of them or both of them at a time didn't work.

---

### Post by az on 2006-05-13
[QUOTE=Drunken Pirate]Oh, I added both of those drivers because they both came with the zip folder. Ill try just one of them at a time and see what I can get.

EDIT: Nope, trying one of them or both of them at a time didn't work.[/QUOTE]
Did you try not using ndiswrapper at all?  That's what I mean by a native linux driver.

---

### Post by Drunken Pirate on 2006-05-13
[QUOTE=azz]Did you try not using ndiswrapper at all?  That's what I mean by a native linux driver.[/QUOTE]

Nothing shows up wether I used ndiswrapper or not. There is no native linux driver for my card.

A little news, I got the wireless card to show up in network config by using linuxant's free trial of driverloader, but I cant get it to connect to the internet. (I counldn't get it to work with ndiswrapper at all.)

---

### Post by bt224 on 2006-05-13
I had to disable eth0 and add wlan0, I had the same issues with my Linksys card. Drivers showed there, and card showed there in command line, but not in the GUI Network window. I finally got it to work just a few minutes ago.

---

### Post by az on 2006-05-14
[QUOTE=Drunken Pirate]Nothing shows up wether I used ndiswrapper or not. There is no native linux driver for my card.

A little news, I got the wireless card to show up in network config by using linuxant's free trial of driverloader, but I cant get it to connect to the internet. (I counldn't get it to work with ndiswrapper at all.)[/QUOTE]
Post the output of
dmesg
as an attachment after you boot and then plug in your device (wait ten seconds or so).

---

