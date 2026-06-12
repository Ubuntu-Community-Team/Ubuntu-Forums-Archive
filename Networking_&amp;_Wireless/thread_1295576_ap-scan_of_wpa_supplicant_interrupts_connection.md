---
title: "ap-scan of wpa_supplicant interrupts connection"
date: 2009-10-19
forum: Networking &amp; Wireless
---

### Post by cosmotronix on 2009-10-19
Hi!

I have a weird problem with wpa_supplicant (0.6.9) and the latest  Karmic-Release on my Thinkpad T40p (Atheros AR5212 Chipset with ath5k-Driver). I can connect with NM without problems, but every 2 minutes wpa_supplicant scans the AP which takes 5-6 seconds and meanwhile no packages are transferred! There is no packet loss, the transfer is just delayed.

Syslog says:

Oct 19 22:50:26 localhost wpa_supplicant[5935]: Starting AP scan (specific SSID)
Oct 19 22:50:26 localhost wpa_supplicant[5935]: Scan requested (ret=0) - scan timeout 30 seconds
Oct 19 22:50:32 localhost wpa_supplicant[5935]: RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
Oct 19 22:50:32 localhost wpa_supplicant[5935]: RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Oct 19 22:50:32 localhost wpa_supplicant[5935]: Wireless event: cmd=0x8b19 len=8
Oct 19 22:50:32 localhost wpa_supplicant[5935]: Received 2268 bytes of scan results (6 BSSes)
Oct 19 22:50:32 localhost wpa_supplicant[5935]: CTRL-EVENT-SCAN-RESULTS

and ping:

64 bytes from 192.168.1.1: icmp_seq=83 ttl=128 time=15.0 ms
64 bytes from 192.168.1.1: icmp_seq=84 ttl=128 time=6653 ms
64 bytes from 192.168.1.1: icmp_seq=85 ttl=128 time=5666 ms
64 bytes from 192.168.1.1: icmp_seq=86 ttl=128 time=4664 ms
64 bytes from 192.168.1.1: icmp_seq=87 ttl=128 time=3662 ms
64 bytes from 192.168.1.1: icmp_seq=88 ttl=128 time=2661 ms
64 bytes from 192.168.1.1: icmp_seq=89 ttl=128 time=1674 ms
64 bytes from 192.168.1.1: icmp_seq=90 ttl=128 time=673 ms
64 bytes from 192.168.1.1: icmp_seq=91 ttl=128 time=1.05 ms

--- 192.168.1.1 ping statistics ---
99 packets transmitted, 99 received, 0% packet loss, time 98242ms
rtt min/avg/max/mdev = 0.878/276.756/6653.714/1075.783 ms, pipe 7

Any ideas?

Cheers
Holger

---

### Post by kevdog on 2009-10-20
Are you using network manager?

---

### Post by cosmotronix on 2009-10-20
Yes, I use NM, but meanwhile I'm quite sure that the problem is the ath5k driver! I had the same problem with Intrepid and Jaunty, but there I could use the madwifi ath_pci as a workaround. With Karmic and the switch to DeviceKit madwifi is no longer supported. :-?

[Bug #276508]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/276508") and [Bug #439011]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/439011")

---

### Post by kevdog on 2009-10-20
Did you try making a manual connection with wpa_supplicant and various iwconfig ifconfig statements at the command line to verify your assumption that it is the driver and not a network manager problem?  With the wpa_supplicant.conf file you create when setting up manual connection, you can attempt to specify the ap_scan=0 or 1 whether you want to do an AP scan.

---

### Post by cosmotronix on 2009-10-22
I tried to change different settings, especially the ap_scan switch, but without success. My WiFi connection quality isn't the best and I found that the ath5k driver may has problems in this case.

I costs too much time to make further investigations and I guess it's easier to look for another WiFi-Card...

Thanks so far!

---

### Post by kevdog on 2009-10-22
Sorry to rain down on your parade - but if considering a new wireless card (which isn't a bad idea) - you might want to investigate chipsets that work with linux before running out and blindly picking one up.  I have 2 cards -- a bcm4306 that uses the b43 driver and an older cisco card that uses the ath_pci or madwifi drivers.  Both perform great.  I know some newer chipsets that still have poor driver support -- such as the ath5k driver which is still currently a moving target.

---

### Post by cosmotronix on 2009-10-22
I look for a broadcom or intel chipset and the bcm4306 is a good recommendation, thanks! 

Please note that madwifi seems to be no longer supported in Karmic. If it would be there I wouldn't have these problems. The AR5212 worked excellent with ath_pci!

---

