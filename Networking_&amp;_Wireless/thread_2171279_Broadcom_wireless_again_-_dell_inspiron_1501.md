---
title: "Broadcom wireless again - dell inspiron 1501"
date: 2013-08-29
forum: Networking &amp; Wireless
---

### Post by markeee on 2013-08-29
Installed 13.04 on my 1501 earlier and originally i had no wireless/wired connection..managed to get the wired working (downloaded linux-firmware-nonfree) and installed off a USB stick

 which enabled me to run apt-get upgrade after the upgrade was complete ny wireless was working and it shows my network o2wireless in network manager

rebooted the laptop and now no wireless - ive read countless forum posts and I'm a bit stuck now to be honest as ifconfig/iwconfig list the wlan0 and lspci -nn k says its using b43-pci-

mark@ins1501:~$ iwconfig
wlan0     IEEE 802.11bg  ESSID:off/any
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

lo        no wireless extensions.

eth1      no wireless extensions.

mark@ins1501:~$

mark@ins1501:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:19:b9:61:4b:d2
          inet addr:192.168.1.67  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:b9ff:fe61:4bd2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4624 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2776 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:4008659 (4.0 MB)  TX bytes:373286 (373.2 KB)
          Interrupt:21

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:384 errors:0 dropped:0 overruns:0 frame:0
          TX packets:384 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:35639 (35.6 KB)  TX bytes:35639 (35.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:19:7e:47:d2:c5
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

mark@ins1501:~$


mark@ins1501:~$ lspci -nnk | grep -iA2 net
05:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
        Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]
        Kernel driver in use: b43-pci-bridge
08:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
        Subsystem: Dell Device [1028:01f5]
        Kernel driver in use: b44
mark@ins1501:~$


Any suggestions appreciated many thanks

---

### Post by markeee on 2013-08-29
mark@ins1501:~$ dmesg | grep b43
[   11.699495] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
[   11.756714] b43-phy0: Found PHY: Analog 4, Type 2 (G), Revision 8
[   14.136051] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[  429.644590] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
[  429.688061] b43-phy0: Found PHY: Analog 4, Type 2 (G), Revision 8
[  429.924063] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
mark@ins1501:~$

---

### Post by markeee on 2013-08-29
mark@ins1501:~$ dmesg | grep b43
[   11.699495] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
[   11.756714] b43-phy0: Found PHY: Analog 4, Type 2 (G), Revision 8
[   14.136051] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[  429.644590] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
[  429.688061] b43-phy0: Found PHY: Analog 4, Type 2 (G), Revision 8
[  429.924063] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
mark@ins1501:~$

---

### Post by markeee on 2013-08-30
Wasn't sure where to post this..as thereds network/dell specific/general help

it applies to all i think

just STUCK

Installed 13.04 on my 1501 earlier and originally i had no wireless/wired connection..managed to get the wired working (downloaded linux-firmware-nonfree) and installed off a USB stick

which enabled me to run apt-get upgrade after the upgrade was complete ny wireless was working and it shows my network o2wireless in network manager

rebooted the laptop and now no wireless - ive read countless forum posts and I'm a bit stuck now to be honest as ifconfig/iwconfig list the wlan0 and lspci -nn k says its using b43-pci-

mark@ins1501:~$ iwconfig
wlan0 IEEE 802.11bg ESSIDff/any
Mode:Managed Access Point: Not-Associated Tx-Power=20 dBm
Retry long limit:7 RTS thrff Fragment thrff
Power Managementff

lo no wireless extensions.

eth1 no wireless extensions.

mark@ins1501:~$

mark@ins1501:~$ ifconfig
eth1 Link encap:Ethernet HWaddr 00:19:b9:61:4b:d2
inet addr:192.168.1.67 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::219:b9ff:fe61:4bd2/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:4624 errors:0 dropped:0 overruns:0 frame:0
TX packets:2776 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:4008659 (4.0 MB) TX bytes:373286 (373.2 KB)
Interrupt:21

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:65536 Metric:1
RX packets:384 errors:0 dropped:0 overruns:0 frame:0
TX packets:384 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:35639 (35.6 KB) TX bytes:35639 (35.6 KB)

wlan0 Link encap:Ethernet HWaddr 00:19:7e:47:d2:c5
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

mark@ins1501:~$


mark@ins1501:~$ lspci -nnk | grep -iA2 net
05:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]
Kernel driver in use: b43-pci-bridge
08:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
Subsystem: Dell Device [1028:01f5]
Kernel driver in use: b44
mark@ins1501:~$


Any suggestions appreciated many thanks

---

### Post by squakie on 2013-08-30
Let's test something:

sudo modprobe b43

*If* that helps, then do the following:

sudo su

echo b43 >/etc/modules

---

### Post by markeee on 2013-08-30
Thanks for the reply

I tried sudo modprobe b43 and no difference :(

the device is listed as you can see but just wont show any networks!

---

### Post by markeee on 2013-08-30
tempted to reinstall the whole OS..but cant see how that would solve much?

---

### Post by squakie on 2013-08-30
Let me ask a question:  when you had this working prior to the update, did you ever do anything to enable a driver (restricted drivers, modprobe, etc)?

Also, there is a moderator who is quite good with wireless issues - hopefully he will see this thread and can help you.

---

### Post by markeee on 2013-08-30
> **squakie said:**
> Let me ask a question:  when you had this working prior to the update, did you ever do anything to enable a driver (restricted drivers, modprobe, etc)?

Also, there is a moderator who is quite good with wireless issues - hopefully he will see this thread and can help you.

nope 
im not sure how it worked

basically had no eth0 or wlan0 then I downloaded linux0-firmware-nonfree.db and instaleld that off a USB stick
removed bcmwl-kernel-source

and i had wired eth0 then I ran apt-get update which took a while..came home from the gym it had finished and It was showing my wireless network in the network manager when I click it on the top right corner

reboot and I'm back to just having wired and no wireless but it says wlan0 is there and it also says b43 driver is in use?

no idea what to do now:(

---

### Post by mörgæs on 2013-08-30
Please stop multiposting. Threads merged.
With your experience in the fora you should know the rules.

---

### Post by markeee on 2013-08-30
> **mörgæs said:**
> Please stop multiposting. Threads merged.
With your experience in the fora you should know the rules.

sorry

---

### Post by squakie on 2013-08-31
Did you try [this]("http://linuxg.net/how-to-fix-broadcom-bcm4311-wireless-driver-on-ubuntu-and-linux-mint/") thread?

---

### Post by smoothedatol412 on 2013-08-31
I have the same problem on my dell !!! and i cant get it to work eather

---

### Post by varunendra on 2013-08-31
@markeee,

Please follow the "Wireless Script" link in my signature, follow the instructions in the linked post to run the script *(created by Wild Man - the same moderator squakie referred to)*, and post back the report the script creates. Thanks.

@smoothedatol412,
Posted on your original thread, please post back what I've asked there.

---

### Post by squakie on 2013-09-07
Actually, believe it or not, dumb old me wrote the first version of this script up for Wild Man so he wouldn't have to keep writing it out.  He had some others work on it to add a couple of things and to remove the MAC address in the output.  I may have been using a previous userid at the time (anewguy).  Funny how I can be so dang dumb but was at least able to get that going for him.

---

### Post by squakie on 2013-09-08
Everything you need is [here]("http://ubuntuforums.org/showthread.php?t=2077104&highlight=").

---

### Post by wildmanne39 on 2013-09-09
squakie you are still listed as a contributor!

---

### Post by squakie on 2013-09-09
Ah gee - didn't have to do that!  But hey - thanks! ;)

---

