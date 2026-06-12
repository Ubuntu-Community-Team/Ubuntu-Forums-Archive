---
title: "Ndiswrapper nuked wireless - How do I restore?"
date: 2010-11-16
forum: Networking &amp; Wireless
---

### Post by Alan|Cvette on 2010-11-16
Hey folks! Got myself in a bit of a pickle here and need some help please :(

Long story short, my Ubuntu wireless is about 1/4th the speed that it is on Windows. The DNS is extremely slow, webpages load slow, max download speed is roughly 20kb. I've been reading up lately and came across a few places that said that the open source drivers are never going to be as fast as the driver from the manufacturer. I couldn't find one they made for Linux - so I installed ndiswrapper and went with the Windows driver.

Currently I am using Ubuntu 10.10 x64 with a Netopia 3D Reach wireless usb, that uses Ralink 7364 drivers. 

What happened is, after installing the driver on ndiswrapper, knocking on wood, and rebooting. My wireless went poof! There is now only a "wired" option on the network icon. So, basically what I would like to do, is restore Ubuntu to it's original wireless setup (which worked). Any help anyone can offer is welcomed :) Cheers!

---

### Post by chili555 on 2010-11-16
I wonder if we couldn't fix your ndiswrapper installation. What does this tell us?```
ndiswrapper -l
dmesg | grep ndis
```Is your Messenger on?

---

### Post by Alan|Cvette on 2010-11-16
> **chili555 said:**
> I wonder if we couldn't fix your ndiswrapper installation. What does this tell us?```
ndiswrapper -l
dmesg | grep ndis
```Is your Messenger on?

Hi there! Thanks for the reply, give me just a few minutes to close out Windows and hop over to Ubuntu. I only have internet access here on Windoze.

---

### Post by Alan|Cvette on 2010-11-16
Here you go!

```
alan@alan-desktop:~$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
netr7364 : driver installed
	device (148F:9021) present (alternate driver: rt73usb

```

```
alan@alan-desktop:~$ dmesg | grep ndis
[   15.213885] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
[   16.482801] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisRetreatNetBufferDataStart'
[   16.482856] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAdvanceNetBufferDataStart'
[   16.482898] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[   16.482948] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[   16.483000] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[   16.483050] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[   16.483098] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[   16.483132] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMResetComplete'
[   16.483166] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[   16.483202] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[   16.483235] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[   16.483273] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[   16.483310] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[   16.483349] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[   16.483385] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[   16.483421] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateNetBuffer'
[   16.483456] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[   16.483492] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[   16.483529] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferList'
[   16.483566] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisFreeNetBuffer'
[   16.483600] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[   16.483637] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferPool'
[   16.483674] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisFreeNetBufferPool'
[   16.483709] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[   16.483746] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[   16.483784] ndiswrapper (import:233): unknown symbol: WDFLDR.SYS:'WdfVersionUnbind'
[   16.483816] ndiswrapper (import:233): unknown symbol: WDFLDR.SYS:'WdfVersionBind'
[   16.483845] ndiswrapper (load_sys_files:206): couldn't prepare driver 'netr7364'
[   16.484219] ndiswrapper (load_wrap_driver:108): couldn't load driver netr7364; check system log for messages from 'loadndisdriver'
[   16.484307] usbcore: registered new interface driver ndiswrapper

```

The log stuff
```
Nov 16 00:58:16 alan-desktop loadndisdriver: loadndisdriver: load_driver(358): couldn't load driver rt73
Nov 16 00:58:16 alan-desktop kernel: [  134.128000] ndiswrapper (check_nt_hdr:141): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
Nov 16 00:58:16 alan-desktop kernel: [  134.128008] ndiswrapper (load_sys_files:206): couldn't prepare driver 'rt73'
Nov 16 00:58:16 alan-desktop kernel: [  134.128508] ndiswrapper (load_wrap_driver:108): couldn't load driver rt73; check system log for messages from 'loadndisdriver'
Nov 16 00:58:16 alan-desktop kernel: [  134.128568] usbcore: registered new interface driver ndiswrapper

```

I noticed, that it says the driver is not 64 bit, yet it is.

---

### Post by chili555 on 2010-11-16
First do:```
sudo su
echo "blacklist rt2x00usb" >> /etc/modprobe.d/blacklist.conf
echo "blacklist rt73usb" >> /etc/modprobe.d/blacklist.conf
echo "blacklist rt2x00lib" >> /etc/modprobe.d/blacklist.conf
mv /etc/modprobe.d/blacklist /etc/modprobe.d/blacklist.conf
exit
```Next, may we see:```
ls /etc/ndiswrapper
```I suspect there are some other failed drivers in there; maybe we need to do some housekeeping.

While I look over your reply, reboot and run these tests again:```
ndiswrapper -l
dmesg | grep ndis
```Thanks.

---

### Post by Alan|Cvette on 2010-11-16
Sorry for the delay, I had to run up to the grocery store.

```
alan@alan-desktop:~$ sudo su
[sudo] password for alan: 
root@alan-desktop:/home/alan# echo "blacklist rt2x00usb" >> /etc/modprobe.d/blacklist.conf
root@alan-desktop:/home/alan# echo "blacklist rt73usb" >> /etc/modprobe.d/blacklist.conf
root@alan-desktop:/home/alan# echo "blacklist rt2x00lib" >> /etc/modprobe.d/blacklist.conf
root@alan-desktop:/home/alan# mv /etc/modprobe.d/blacklist /etc/modprobe.d/blacklist.conf
root@alan-desktop:/home/alan# exit
exit
alan@alan-desktop:~$ ls /etc/ndiswrapper
netr7364

```

```
alan@alan-desktop:~$ ndiswrapper -l
netr7364 : driver installed
	device (148F:9021) present (alternate driver: rt73usb)
alan@alan-desktop:~$ dmesg | grep ndis
alan@alan-desktop:~$ dmesg | grep ndis
(nothing happens here)

```

---

### Post by chili555 on 2010-11-16
> alan@alan-desktop:~$ ndiswrapper -l
netr7364 : driver installed
	device (148F:9021) present ([COLOR="Red"]alternate driver: rt73usb[/COLOR])
Let's just confirm that it's not actually loaded:```
lsmod | grep -e rt73 -e ndis
```Your /etc/ndiswrapper looks very fine.

I am troubled by the 64-bit issue; can you explain where you got the Windows drivers? Were they clearly marked, perhaps in a folder, as 64-bit?

Where in SC if I may ask?

---

### Post by Alan|Cvette on 2010-11-16
> **chili555 said:**
> Let's just confirm that it's not actually loaded:```
lsmod | grep -e rt73 -e ndis
```Your /etc/ndiswrapper looks very fine.

I am troubled by the 64-bit issue; can you explain where you got the Windows drivers? Were they clearly marked, perhaps in a folder, as 64-bit?

Where in SC if I may ask?

We got this card when we signed up for Bellsouth DSL, it is made by Netopia, but uses Ralink drivers. I could not find the right driver on the Ralink website - And I just saw that the one they make for Linux is a build-it-yourself type job. So I went through the Bellsouth website to get the correct Vista 64bit driver for this card.

I will reboot and get you that info.

EDIT: Oh, Mount Pleasant.

---

### Post by chili555 on 2010-11-16
Move the rt73.inf, .sys and .cat files over from your Vista partition.

Let's remove the not-working symbol-error ridden Vista driver:```
sudo ndiswrapper -e netr7364
sudo rm -rf /etc/ndiswrapper/*
```Now install as you did before, the XP driver rt73.inf. It will grab the .sys and, if needed, the .cat file automatically. 

Reboot.

---

### Post by chili555 on 2010-11-16
To restore your original native driver, please do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```If rt73usb is in there, remove it. Proofread, save and close gedit. Now do:```
sudo ndiswrapper -e rt73.inf
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -rf /etc/ndiswrapper/*
sudo modprobe rt73usb
iwconfig
```Any improvement?

Let's do some diagnostics. Please post:```
lsmod | grep -e rt7 -e rt2
```Thanks.

---

### Post by Alan|Cvette on 2010-11-16
HUGE thanks to chili555! This did the trick to restore Ubuntu back to the original configuration.

```
sudo ndiswrapper -e rt73.inf
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -rf /etc/ndiswrapper/*
sudo modprobe rt73usb
iwconfig
```

Cheers mate!!! :)

---

