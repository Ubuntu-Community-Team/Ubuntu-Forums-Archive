---
title: "having issues connecting with ethernet :("
date: 2009-02-11
forum: Networking &amp; Wireless
---

### Post by sleve on 2009-02-11
Lo all, 

        So sorry to bug you all but i am having a terrible time trying to connect to my router via Ethernet or Usb cable.. i am brand new to linux/ubuntu ( literally just installed a few hours ago) and i am running into a slight issue connecting to my router, i am currently using a Netgear cg814w router. i have gone through the walk through on the desktop and i dont seem to have system>admin>network.. i do have network tools but that doesnt seem to get me to what i want to do... if anyone could help me out it would be much appreciated :D

---

### Post by Fire_Chief on 2009-02-11
Your network card configuration would normally be found under
System -> Preferences -> Network Configuration

If your router is serving DHCP to the LAN, then as long as Ubuntu recognizes the network card, it should pick up an address and work automatically.

If you are not sure whether Ubuntu sees your network card, then try running System -> Administration -> Hardware Testing. It will run through several different device detections and tests to verify the components (sound card, NIC, etc.).

Cheers!

---

### Post by odium1 on 2009-02-11
what kernel are you running? and what version of ubuntu?

---

### Post by sleve on 2009-02-11
hmm well it doesnt recognize my network card : / 

but i do have 27 updates to install so hopefully its something in there.

after ive finished installing all my updates i will attempt to connect via ethernet and if that doesnt work ill be back :cool:

---

### Post by sleve on 2009-02-11
> **odium1 said:**
> what kernel are you running? and what version of ubuntu?

Ubuntu 8.10 dunno what kernel linux ? haha

sorry im very new to this. i have a wow friend helping me but hes asleep atm and im very impatient. ill probably end up figuring it out soon enough or just running around in circles until he wakes up... OR hopefully getting some answers from your ubuntu vets :D

---

### Post by Fire_Chief on 2009-02-11
If it still doesn't see the card, then open a terminal and type```
lspci
```then copy and paste the results here.

Cheers!

---

### Post by sleve on 2009-02-11
00:00.0 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:0a.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon X1650 Pro (rev 9e)
01:00.1 Display controller: ATI Technologies Inc Radeon X1650 Pro (Secondary) (rev 9e)

---

### Post by odium1 on 2009-02-11
you can check which kernel you're running by typing 
```
uname -a
```
in the terminal. 

i'm just curious to know if you're having a problem related to the latest kernel bug :D

---

### Post by sleve on 2009-02-11
Linux ubuntu 2.6.27-7-generic #1 SMP Fri Oct 24 06:42:44 UTC 2008 i686 GNU/Linux


kernal ^^^


and i dced my wireless adapter using my neighbor/friends atm

and hooked up my chord and got this with the hardware test

ERROR:root:Could not find def gateway info in /proc
Traceback (most recent call last):
  File "/usr/share/hwtest/scripts/internet_test", line 132, in <module>
    sys.exit(main(sys.argv[1:]))
  File "/usr/share/hwtest/scripts/internet_test", line 118, in main
    host = route.get_default_gateway()
  File "/usr/share/hwtest/scripts/internet_test", line 81, in get_default_gateway
    t1 = self._get_default_gateway_from_bin_route()
  File "/usr/share/hwtest/scripts/internet_test", lin

---

### Post by Fire_Chief on 2009-02-11
Ok, so the system sees your wireless card but not the wired one. Can you give us more info on the machine? (Brand/model/type) Or if you know it, what is the brand and model of the wired network card?

---

### Post by sleve on 2009-02-11
> **Fire_Chief said:**
> Ok, so the system sees your wireless card but not the wired one. Can you give us more info on the machine? (Brand/model/type) Or if you know it, what is the brand and model of the wired network card?


pc is custom built the ethernet card is built into the motherboard and ive totally lost the packaging for it. i built it about 1 year and a half ago... i feel i may be stuck in a rut :(

---

### Post by Fire_Chief on 2009-02-11
Nah, not quite yet. What is the make/model of the motherboard?

It should be printed on there somewhere.

---

### Post by sleve on 2009-02-11
ill i got was ecs 15-q22 012002

and p4m800pro m v 2.0

---

### Post by odium1 on 2009-02-11
that's an elitegroup mobo with via chipset (so google tells me)

---

### Post by Fire_Chief on 2009-02-11
So another user mentioned in [this thread]("http://ubuntuforums.org/showthread.php?t=335748") that he updated his BIOS to the latest version. Then there was a switch in the BIOS to enable/disable the onboard NIC and it was working fine in Ubuntu.

The latest available BIOS for your board from ECS is [Here]("http://www.ecsusa.com/ECSWebSite/Downloads/ProductsDetail_Download.aspx?detailid=673&DetailName=Bios&DetailDesc=&CategoryID=1&MenuID=6&LanID=9").

Cheers!

---

### Post by sleve on 2009-02-11
oh ty mates dling atm

what is the zip program for linux by chance?

---

### Post by Fire_Chief on 2009-02-11
it's built-in :guitar:

---

### Post by sleve on 2009-02-11
hmm should i do this on the windows side ?

and do i need to load this onto a disc or can i use mounting software like - daemon tools?

---

### Post by Fire_Chief on 2009-02-11
Best bet is to first boot into the BIOS and see what kind you have already installed. Then go look at the ECS flash utility page [here]("http://www.ecs.com.tw/extra/flashutl/index.html"). If you have Windows installed, you may be able to flash directly from there. Otherwise, you would probably need to make a bootable DOS floppy with the flash utility on it and boot to that. The instructions on the utility page should guide you through it.

If you need files for a bootable DOS floppy, check out [http://www.bootdisk.com]("http://www.bootdisk.com"). Note that the utilties which create these disks work under Windows.

Cheers!

---

### Post by sleve on 2009-02-11
K im back and ive figured out whats going on. i dont have my via compatible fast ethernet drivers dled. ive grabbed this ```
diff -Nura src-orig/rhine_main.c src/rhine_main.c
--- src-orig/rhine_main.c	2007-01-26 08:31:02.000000000 +0800
+++ src/rhine_main.c	2007-01-26 09:17:54.000000000 +0800
@@ -1734,7 +1734,12 @@
 
 #ifdef RHINE_TX_CSUM_SUPPORT
     if ((pInfo->hw.flags & RHINE_FLAGS_TX_CSUM) &&
+
+#if LINUX_VERSION_CODE >= KERNEL_VERSION(2,6,19)
+        (skb->ip_summed == CHECKSUM_PARTIAL)) {
+#else
         (skb->ip_summed == CHECKSUM_HW)) {
+#endif
         struct iphdr* ip=skb->nh.iph;
         if (ip->protocol == IPPROTO_TCP)
             pHeadTD->tdesc1 |= cpu_to_le32(TCR_TCPCK);
```

and when i run the script i see nothing so i dont know if its dled. i still see an orange light on the port im connected to so i dont know whats going on. anyone have any reqs?

also i do have around 200+ megs of updates since this is a fresh linux ug so im wondering if i need to download that. i seem to not be able to download things like world of warcraft or steam so im hoping its me just needing to update. im desperate to run linux on my machine as ive grown so very tired of windows. 

thank you in advance and for all the help ive received so far

---

### Post by odium1 on 2009-02-11
i would definitely do the updates because that *could* clear the entire issue up... i don't want to promise anything, but it definitely wouldn't hurt. i just got my laptop running smoothly again about 20 minutes ago. i've been dealing with this dead eth0/kernel bug for about two weeks now since the 2.6.27-11 kernel update was available.. i updated and rebooted and i couldn't get my wired networking to work. i tried TONS of stuff up until last night i found **kernelcheck** and installed it, it found the latest kernel (2.6.28-4) and installed it for me and viola! my ethernet started working again haha.

---

