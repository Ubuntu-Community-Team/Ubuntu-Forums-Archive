---
title: "HP probook  4710s no wireless"
date: 2010-05-11
forum: Networking &amp; Wireless
---

### Post by Arles on 2010-05-11
I recently installed Ubuntu 10.4 x64 on my laptop. It has dual boot with Win7 x64. Everything seems ok except there is no wireless network. When clicking on the icon I can't find any networks.

 I tried entering the data manually but I still can't connect. I had no problems on karmic koala so this really puzzles me. The results from ```
sudo lshw -C network
``` and ```
iwconfig
``` are:

```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
pan0      no wireless extensions.






Hardware Lister (lshw) - B.02.14
usage: lshw [-format] [-options ...]
       lshw -version

	-version        print program version (B.02.14)

format can be
	-html           output hardware tree as HTML
	-xml            output hardware tree as XML
	-short          output hardware paths
	-businfo        output bus information

options can be
	-class CLASS    only show a certain class of hardware
	-C CLASS        same as '-class CLASS'
	-c CLASS        same as '-class CLASS'
	-disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
	-enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
	-quiet          don't display status
	-sanitize       sanitize output (remove sensitive information like serial numbers, etc.)
	-numeric        output numeric IDs (for PCI, USB, etc.)
```

---

### Post by ubunterooster on 2010-05-11
I will ask a mod to move this thread to networking and wireless: [http://ubuntuforums.org/forumdisplay.php?f=336](http://ubuntuforums.org/forumdisplay.php?f=336)

  	 	      		 		 			 				 					 					 					 					 					 					 					 [IMG]http://ubuntuforums.org/images/misc/sticky.gif[/IMG]   				 			 			 			 			**[B]see also the Sticky:**[/B] 			                          			 			[Supported wireless cards list and procedure to  get help.]("http://ubuntuforums.org/showthread.php?t=370108") 			 		
  		  		 			 			 				bapoumba

---

### Post by lisati on 2010-05-11
> **ubunterooster said:**
> I will ask a mod to move this thread to networking and wireless: [http://ubuntuforums.org/forumdisplay.php?f=336](http://ubuntuforums.org/forumdisplay.php?f=336)

  	 	      		 		 			 				 					 					 					 					 					 					 					 [IMG]http://ubuntuforums.org/images/misc/sticky.gif[/IMG]   				 			 			 			 			**[B]see also the Sticky:**[/B] 			                          			 			[Supported wireless cards list and procedure to  get help.]("http://ubuntuforums.org/showthread.php?t=370108") 			 		
  		  		 			 			 				bapoumba

Done.

---

### Post by Arles on 2010-05-13
Tried lots of stuff from sticky but nothing helps. Every time I try to install driver for wireless card or activate some proprietary drivers computer freezes. After connecting via LAN and upgrading the system the new kernel can't boot giving kernel panic. The old kernel boots but computer freezes every 5 seconds. Tried 5 fresh installations but no help.

---

