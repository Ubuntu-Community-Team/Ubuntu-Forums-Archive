---
title: "Pls help: Netgear WN511TA_pcmcia"
date: 2010-01-28
forum: Networking &amp; Wireless
---

### Post by iClouseau88 on 2010-01-28
Hi,
Toshiba Satellite pro 4600 laptop with Dual boot XP Pro-Karmic Ubuntu.  Wireless N is fine under Windows with Netgear WN-511TA PCMCIA card.  I recently used the graphical method to install ndiswrapper and the Windows driver into Karmic Ubuntu. The window shows the hardware is present (NMW14X: yes), implying that the INF file is installed.  I even blacklisted the Orinoco driver of the existing Orinoco wireless B card in my laptop. However when I click on the button to configure network the screen says it cannot find a network to configure. When I try to connect wirelessly via Network Manager, I cannot see WPA2 Personal passphrase, only WEP and other authentications.

Could you help me set up wireless connection?  Thank you.

---

### Post by iClouseau88 on 2010-01-28
Oh by the way, the card lits up but I still cannot connect wirelessly.
Up until last year, I used madwifi driver to connect a DLink WNA-2330 PCMCIA card adn everything was fine.  I just used Synaptic Manager to remove "madwifi tools" which is the only term I can find under "Search".

---

### Post by iClouseau88 on 2010-01-28
Hi everyone!  Here's what the terminal shows after I enter iwconfig:

~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Sensitivity=-200 dBm  
          RTS thr=2346 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth1      IEEE 802.11b  ESSID:""  Nickname:"HERMES I"
          Mode:Managed  Frequency:2.412 GHz  Access Point: None   
          Bit Rate:2 Mb/s   Sensitivity:1/3  
          Retry limit:4   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/92  Signal level=-122 dBm  Noise level=-122 dBm
          Rx invalid nwid:0  Rx invalid crypt:10  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

How do I get rid of eth1 (legacy Origano wireless B) and wlan0 (legacy DLink WNA-2330 wireless G) and replace them with the Netgear driver for wireless N?

Thanks a lot for your help.

---

### Post by iClouseau88 on 2010-01-28
Anyone at all? I am getting frustrated!

---

### Post by iClouseau88 on 2010-01-28
Additional info:

~$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/nvidia-kernel-nkc, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ipw3945, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/aliases, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
netmw14x : driver installed
	device (11AB:2A02) present

~$ iwconfig wlan0
wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Sensitivity=-200 dBm  
          RTS thr=2346 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
~$ lspci
00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 11)
00:01.0 PCI bridge: Intel Corporation 82815 815 Chipset AGP Bridge (rev 11)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801BAM ISA Bridge (LPC) (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801BAM IDE U100 Controller (rev 03)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 03)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801BA/BAM AC'97 Modem Controller (rev 03)
01:00.0 VGA compatible controller: Trident Microsystems CyberBlade/XP (rev 63)
02:08.0 Ethernet controller: Intel Corporation 82801BA/BAM/CA/CAM Ethernet Controller (rev 03)
02:0c.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 01)
02:0d.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 31)
02:0d.1 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 31)
07:00.0 Ethernet controller: Marvell Technology Group Ltd. 88W8361 [TopDog] 802.11n Wireless (rev 03)

Any suggestion would be much appreciated!!!

---

### Post by iClouseau88 on 2010-01-29
Bump!

---

### Post by Kixtosh on 2010-01-29
I'm going to suggest something silly (as a new user myself) but in Karmic Koala, I just clicked on the cell tower icon in the top right panel and was immediately able to see my network SSID, and just clicked on it to start it up. It connected flawlessly on the two ancient laptops in my signature, and the "Link" light on my ancient Netgear card came on instantly. Everything has worked ever since from start-up.
 
You seem to have some experience with Ubuntu already (certainly more than me) so maybe this is ridiculous, and maybe you've already done all that, but maybe not (I don't know if 9.04 has equivalent wireless functionality 9.10) I had no need of ndiswrapper or anything else, other than the basic installation. In fact, everything worked out of the box from the Live CD.
 
Perhaps you could try the Live CD of Karmic Koala and see how your card works with that? It might help figure things out, at least. I'm guessing that if it works with the Karmic Koala Live CD that it'll just be a matter of figuring out how to get your installation updated with the necessary stuff.
 
Best of luck, and don't pull your hair out!

---

### Post by iClouseau88 on 2010-01-29
Kixtosh, 

I have already done what you suggested.  I just found out from launchpad.net that a bug in Karmic Koala results in the same symptom for another card (Airlink 101 AWLL6080 USB), i.e. Network Manager sees the device and available networks but when it tries to connect to the access point the WEP password box keeps popping up and connection is never made.
I may have to uninstall Network Manager and give WICD a try.

Thank you for your suggestion anyway.

---

### Post by iClouseau88 on 2010-01-29
Ok, I will shortly post another thread with slightly different topic title so that I can present the info in a more organized way, as suggested in "How to post a wireless issue" at the start of this sub-forum.

---

