---
title: "Wireless card drivers"
date: 2011-07-10
forum: Networking &amp; Wireless
---

### Post by GaryReggae on 2011-07-10
Hi folks, sorry if this seems to be a bit of a 'noob' question, however, I am stuck with getting my new media centre PC up and running. I have been using Ubuntu on my laptop for ages but am still puzzled by the more technical aspects.

I have installed LTS Ubuntu from a LiveCD and it's up and running nicely, however, I can't get the WiFi to work. It has an EdiMax EW-7711in PCI card in it and I think that is the problem. 

When I click on the network settings icon on the top bar next to the date, it only says about adding VPN connections...my laptop shows a list of available Wifi networks and also has an option at the bottom to add a new wireless network. 

If this was Windows (and fortunately it isn't!) then I could go into the Device Manager and see a list of all the hardware, including devices with problems. I don't seem to be able to find any kind of equivalent in Ubuntu.

A bit of research on Google tells me that I need to download DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217, which I have done but I have no idea what I am supposed to do with it!

In the archive file there are folders called chips, common, include, os, sta, tools and files called iwpriv_usage.txt, Makefile, README_STA.pci, RT2860STA.dat, RT2860STACard.dat and sta_ate_iwpriv_usage.txt. Yes, I have looked at the readme and I am still none the wiser; if anything, it has confused me even more.

Could somebody please let me know what I need to do to install these drivers or is there an easier way of getting things working?

Thanks,

Gary

---

### Post by Bucky Ball on 2011-07-10
Plug in an ethernet cable, get updates, check System>Administration>Additional Drivers (or Hardware Drivers depending on release). If that doesn't get you up and running ...

In a terminal, run:

```
sudo lshw -C network
```Post the result back here, please. That will give us your wireless chip (the Edimax probably uses Realtek chip).

You can also run:

```
lspci
```Look for the 'Network Controller' line and that also gives your wireless chip.

---

### Post by GaryReggae on 2011-07-11
Thanks for the reply. I have now downloaded all the updates suggested in the Update Manager and rebooted but it still doesn't seem to recognise the wireless card.

I've gone into Hardware Drivers as suggested but it only comes up with ATI/AMD proprietary FGLRX graphics driver - and I'm pretty sure that is not relevant.

I have ran both the terminal commands you suggested and the results are below:

```
garyreggae@garyreggae-mediacentre:~$ sudo lshw -C network
[sudo] password for garyreggae:
  *-network          	 
   	description: Ethernet interface
   	product: RTL8111/8168B PCI Express Gigabit Ethernet controller
   	vendor: Realtek Semiconductor Co., Ltd.
   	physical id: 0
   	bus info: pci@0000:02:00.0
   	logical name: eth0
   	version: 06
   	serial: d0:27:88:1f:90:09
   	size: 100MB/s
   	capacity: 1GB/s
   	width: 64 bits
   	clock: 33MHz
   	capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
   	configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.5 latency=0 link=yes multicast=yes port=MII speed=100MB/s
   	resources: irq:25 ioport:e800(size=256) memory:fdeff000-fdefffff(prefetchable) memory:fdef8000-fdefbfff(prefetchable)
  *-network UNCLAIMED
   	description: Network controller
   	product: RaLink
   	vendor: RaLink
   	physical id: 5
   	bus info: pci@0000:03:05.0
   	version: 00
   	width: 32 bits
   	clock: 33MHz
   	capabilities: pm bus_master cap_list
   	configuration: latency=64 maxlatency=4 mingnt=2
   	resources: memory:febf0000-febfffff
garyreggae@garyreggae-mediacentre:~$
```

```
garyreggae@garyreggae-mediacentre:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc 760G [Radeon 3000]
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
03:05.0 Network controller: RaLink Device 3060
03:06.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
03:06.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
garyreggae@garyreggae-mediacentre:~$
```

Any suggestions would be much appreciated! Thanks again.

---

### Post by GaryReggae on 2011-07-11
It appears that the device in question is the Ralink 3060. It said 'Unclaimed' in the terminal window. I have looked this up and the suggestion is to use install the Windows Wireless Drivers app. I have done this but it needs an INF file to be able to get that working but I cannot find one.  The CD that came with it just has CABs (which won't open) and various EXEs. I have tried downloading the Windows driver off the Ralink website but that is also an EXE so won't open.

---

### Post by Bucky Ball on 2011-07-11
> successful on 10.04, lspci show Ralink Device 3060. Downloaded  ´´RT3062PCI/mPCI/CB/PCIe(RT3060/RT3062/RT3562/RT2860/RT2760/RT2890/RT2790)´´  from [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2) , extracted and followed their README_STA. ... from:

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink)

**RaLink Device 3060** (from the result of your 'lspci') is the device you are looking for and that chipset is also used in the D-Link DWA-525 according to the above link.

* Update: To avoid confusion, this is the link directly to the driver you want:

[RT3062PCI/mPCI/CB/PCIe(RT3060/RT3062/RT3562/RT3592)]("http://www.ralinktech.com/license_us.php?n=2&p=0&t=U0wyRnpjMlYwY3k4eU1ERXdMekV5THpFM0wyUnZkMjVzYjJGa09USXlNek15TlRReE9TNTBaM285UFQxRVVFOWZVbFF6TlRZeVh6TTFPVEpmTXpBMk1sOU1hVzUxZUZOVVFWOVdNaTQwTGpFdU1WOHlNREV3TVRJeE53PT1D")

Just fill in details and your download should start. Check the readme file for instructions on how to go about installing. Let us know how it goes. ;)

---

### Post by ratcheer on 2011-07-11
Here are some instructions for getting your driver installed. I have an ralink 3562 and this worked for me.

1) Put the downloaded file into some directory by itself. Extract it with Archive Manager.

2) cd to the subdirectory where the archive was extracted.

3) sudo make

4) Copy file RTA2860STA.DAT to directory /etc/Wireless/RT2860STA. You will have to create the directory, first.

5) Still in the  subdirectory where the archive was extracted, run: sudo make install

6) sudo modprobe rt3060sta

If the module name in the last statement is correct (it is hard to be sure), your wireless connection should start. It will probably bring up a dialog in which to enter your WPA2 passphrase. If that didn't get you going, reboot and see if the connection starts.

As a final check, run: sudo lspci -v

Tim

---

### Post by initialx on 2011-07-12
I did what you said on your reply and so far no luck.  I dont kno if its just me but i also lost my enable wireless tick on the network connections on the top right corner.  Is there anything else i can do to get my internet to work???

---

### Post by ratcheer on 2011-07-12
> **initialx said:**
> I did what you said on your reply and so far no luck.  I dont kno if its just me but i also lost my enable wireless tick on the network connections on the top right corner.  Is there anything else i can do to get my internet to work???

initialx, please open your own problem thread and we will help you there. It gets very confusing trying to solve two people's problems at once.

Thanks,
Tim

---

### Post by Bucky Ball on 2011-07-12
> **ratcheer said:**
> initialx, please open your own problem thread and we will help you there. It gets very confusing trying to solve two people's problems at once.

Thanks,
Tim

+1. You will get better help. Use a descriptive thread title.

---

### Post by GaryReggae on 2011-07-12
Thanks for your reply, the instructions you gave me for installing the driver were easy to follow unlike the readme.

Anyway, all went well until I got to the last step, the modprobe command. When I run that, I get:

```

garyreggae@garyreggae-mediacentre:~/Downloads/RALink$ sudo modprobe rt2860sta
FATAL: Error inserting rt2860sta (/lib/modules/2.6.32-32-generic/kernel/drivers/staging/rt2860/rt2860sta.ko): Device or resource busy
```

Now, one of those make commands created two dat files - RT2860STA.dat and RT2860STACard.dat. I have tried running your procedure for the one with the card prefix as well (perhaps the card one is for actual cards like mine while the other one is for onboard chips?). The modprobe for that one comes up with 'Module rt2860stacard not found'. I have tried capitalising that the same as the dat file but it seems to make no difference.

I think the folder structure is correct. In /etc there is a Wireless folder now. This contains a folder for RT2860STA and RT2860STACard and also both dat files in the root of Wireless. Both of the folders contains the correct (according to the filename anyway) dat file.

So, here's the contents of another test (I have snipped out the section about the Ethernet driver to save posting that again):


```
garyreggae@garyreggae-mediacentre:~/Downloads/RALink$ sudo lshw -C network

  *-network
       description: Network controller
       product: RaLink
       vendor: RaLink
       physical id: 5
       bus info: pci@0000:03:05.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=rt2860 latency=64 maxlatency=4 mingnt=2
       resources: irq:20 memory:febf0000-febfffff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: ra0
       serial: 00:1f:1f:a6:79:93
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=RALINK WLAN driverversion=2.4.1.1 multicast=yes wireless=Ralink STA
```

Network disabled? There is still nothing relating to wireless on the network menu by the clock.

Any further advice would be greatly appreciated! Thanks for your time.

PS: I have also rebooted to no avail!

---

### Post by ratcheer on 2011-07-12
All I can think is that my card is a 3562 and I had it do a modprobe for rt3562sta. However, after doing so, my kernel driver in use is listed as rt2860. So, I wonder if you should modprobe for your actual device name, i.e., rt3060sta?

No reboot was required for me when I did it that way, my wireless connection came up immediately after the modprobe executed.

Also, have you blacklisted rt2800pci and added rt3060sta to your modules list?

I have some more complex instructions that have also worked for me, if you want to try them. But they still depend on using the correct module name, whatever that proves to be. Who knows, I might be using the wrong module name, but it did get my network up and running.

Tim

---

### Post by ratcheer on 2011-07-12
I am sorry, I did all of this about a month ago and I am starting to confuse myself.

My card is a 3060, just like yours. However, when I ran make, the module created was rt3562sta.ko. That is the module I loaded to get my wireless working. I had not noticed the discrepancy until just now, when I was looking everything over to help you.

I wonder if yours will come out the same as mine? The actual module created should be found in the subdirectory ./os/linux down from the DPO..... directory where your driver source was expanded.

Also, did you follow the README_STA_pci instructions about HAS_WPA_SUPPLICANT=y and HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y before running make?

Tim

---

### Post by GaryReggae on 2011-07-13
Hi Tim,

Thanks again for your help with this. I have tried modprobe with different device names and here are the results:

sudo modprobe rt3060sta - FATAL: Module rt3060sta not found.
sudo modprobe rt3562sta - accepts this with no error, just comes back to the standard ~$ prompt.
sudo modprobe rt2860sta - FATAL: error inserting rt2860sta (/lib/modules/2.6.32-32-generic/kernel/drivers/staging/rt2860/rt2860sta.ko): Device or resource busy

There is something in what you said about that .ko file as it appears in that error msg. I have tried modprobe for that filename but it says that module is not found. From the above results, I think the proper module name is probably rt2860sta but it may be rt3562sta. Oddly, the actual card name (3060) is the one that doesn't work.

> Also, have you blacklisted rt2800pci and added rt3060sta to your modules list?

Sorry, I'm not sure how to do that, could you please give me instructions?

> Also, did you follow the README_STA_pci instructions about HAS_WPA_SUPPLICANT=y and HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y before running make?

Again, I'm not quite sure how to do this. I did read the readme but it didn't make a lot of sense. If you could let me know what I need to do then that would be very much appreciated.

Thanks,

Gary

---

### Post by ratcheer on 2011-07-13
Ok, I think we are close.

First, do those settings for HAS_WPA_SUPPLICANT=y and HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y. This is done simply by editing file ./os/linux/config.mk. When I say "./", it just means down from your DPO directory.

Go back to the DPO directory and run "sudo make"

Re-copy file RTA2860STA.DAT to /etc/Wireless/RT2860STA

Edit files (as root or under su) /etc/modprobe.d/blacklist.conf and /etc/initramfs-tools/modules. In the blacklist file, add a line with "blacklist rt2800pci". In the modules file, add a line with "rt3562sta".

Go back to the DPO directory. Run "sudo make install"

Run "sudo modprobe rt3562sta". Your wireless connection should come up. Then, mine gave me a dialog to enter the WPA2 passphrase and I was connected.

Again, if this does not work, I have another method.

Tim

---

### Post by ratcheer on 2011-07-13
I just had to redo this twice, this morning, because I got new kernel updates for both Natty and Oneiric. It worked perfectly as I described it above in both cases.

So, also note that you will have to redo it every time you install a kernel update, as well. Why? Because we are compiling the driver from source and installing it into the Linux kernel. Every time the kernel is replaced with a stock kernel, our change is not in the new one.

Tim

---

### Post by GaryReggae on 2011-07-13
Yes, that worked!!! Thanks you very much indeed.

The modprobe command didn't bring up anything straight away, but after a reboot, the wireless options appear in the network manager menu - and I have successfully connected.

Many thanks,

Gary

---

### Post by Bucky Ball on 2011-07-13
Good news. Enjoy! Please mark thread as 'solved' so it might help others. ;)

---

