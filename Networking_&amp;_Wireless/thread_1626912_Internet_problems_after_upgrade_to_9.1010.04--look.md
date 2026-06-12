---
title: "Internet problems after upgrade to 9.10/10.04--looking into router issues"
date: 2010-11-20
forum: Networking &amp; Wireless
---

### Post by TracyO on 2010-11-20
I upgraded to 9.10 and then 10.04 a few weeks ago.  Since then, I've been having trouble viewing content on certain websites in both Chrome and Firefox.  I thought it might be Java or Flash, but no one can figure it out.  Now I'm looking at what my router might have to do with it.  

Gmail and Hulu work fine for the most part.  I have trouble when I try to interact with content (ie. log in, watch a video) on YouTube, Daily Show, etc.  Yes, those sites aren't terribly important, but the bigger issue is that I have the same problem logging into sites where I need to pay bills.

I have a Netgear WGR 614v9 router.  I took a look at the log while attempting to go to the above sites (those that work and those that don't), and for all the sites it says "[DoS attack: IP Spoof] attack packets in last 20 sec from ip (lists address)"  I've never checked the logs before.  Does this mean anything?

Does anyone have other ideas (router-related or not) on this problem?  In Chrome, the most common error is "Err 101" which says the connection was reset.

Thanks.

---

### Post by uncaspi on 2010-11-20
Try to disable the firewall in the router.

---

### Post by TracyO on 2010-11-21
I did that, and I got the same behavior from websites, and the same information in the router log.  

Sometimes, I can get a website to work through Shift+Reload if that's any indication.

I've cleared my cache multiple times, and if it helps at all, it's temporary.

---

### Post by uncaspi on 2010-11-21
Are there something in the router called IP-Spoof? You could try to hardware reset the router.

---

### Post by TracyO on 2010-11-21
I don't see anything called IP Spoof, but I also don't know where I should be looking.  

I did a hard reset of the router last night, and it didn't change anything before or after.

Why am I getting a Connection Reset error in my internet browser?  Is there something else with the router that it could be?  Is there another reason?  

It seemed like there were a lot of funky internet issues when people upgraded to 9.10 and/or 10.04.  It seemed like it was Flash and people's routers, but those solutions haven't worked for me.  It's been about a month now, and I'm getting more frustrated that no one (including me) can figure this out.  It's a general frustration--not at anyone in particular.

I absolutely appreciate everyone who's been taking a stab at it along the way.  If nothing else, explain to me why this issue stumps you (or anyone else).  My knowledge is not much and anything I can get a better understanding of, the better.

---

### Post by uncaspi on 2010-11-21
I've googled spoofing IP and that means that intruders are attempting to get access to your host. So turn on the router firewall. To find out if you've been hacked and the intruder have placed a small code that connects to the intruders computer, sending info, monitor the traffic through your card when all applications is turned off.

sudo tcpdump -i eth0   where eth0 should be replaced with your card.

---

### Post by TracyO on 2010-11-21
How do I find the name of my card?

---

### Post by TracyO on 2010-11-21
PS - Can you do me a favor and look at your router's log?  Ideally, what should it report when things are fine?

I turned my firewall back on this morning as soon as I determined that disabling it was no help.  Figuring out how to leave it disabled (if it worked) and still be secure was going to be a pretty big question.


Update:  I talked to a friend's husband who's a programmer to get a better sense of what the Spoof attack is all about.  He explained it as "A DoS attack is a denial of service attack, which often means flooding or trying to overload a system to make it stop working.  
If your router is what is logging this DoS, it is either someone targeting your network, or it is mistakenly thinking your computer is the cause. "

I took his recommendations for upping my security, but I think under the circumstances, I'm willing to bet it thinks there's something wrong with my computer, and whatever it is is the crux of this issue.

Here's some other stuff I tried earlier today that might provide more information for someone who knows more than me.  Ubuntu community docs for wireless troubleshooting.  
[https://help.ubuntu.com/10.04/internet/C/troubleshooting-wireless.html](https://help.ubuntu.com/10.04/internet/C/troubleshooting-wireless.html)

When I looked for /etc/modprobe.d/aliases, to see if it could be an IPv6 issue, I found that there's no file named aliases in that directory.

I also came upon [http://www.linux-tips-and-tricks.de/index.php/collectNWData.sh/collectNWData-Uberblick-/-Overview.html#English](http://www.linux-tips-and-tricks.de/index.php/collectNWData.sh/collectNWData-Uberblick-/-Overview.html#English) to look at Linux networking problems.
I downloaded the script, I can see it on my desktop, and chmod 700 would not run.

---

### Post by uncaspi on 2010-11-21
Name of the card:  sudo ifconfig or sudo iwconfig
or perhaps if these doesn't work try these.

sudo /sbin/iwconfig
sudo /sbin/ifconfig

---

### Post by uncaspi on 2010-11-21
I have no logs on my router. Perhaps others in the forum can help you.

---

### Post by TracyO on 2010-11-22
Thanks again for your advice.  I'm not completely sure what I'm looking for to find my card name--is it something other than wlan0?  I'm better when given examples.  Here's what I have been able to do:


 /sbin/iwconfig:


tracy@tracy-laptop:~$ sudo /sbin/iwconfig


lo        no wireless extensions.
eth0      no wireless extensions.
wlan0     IEEE 802.11abg  ESSID:"@@@"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1F:33:CD:AF:0E   
          Bit Rate=1 Mb/s   Tx-Power=14 dBm   


          Retry  long limit:7   RTS thr:off   Fragment thr:off


          Encryption key:AF69-7983-E8


          Power Management:off


          Link Quality=70/70  Signal level=-24 dBm  


          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0


          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by TracyO on 2010-11-22
I couldn't get this all in post...




Also, I finally got Collectnwdata, and below are the results.  I don't know what I'm looking for.  If anyone sees anything (or it looks fine) please let me know.


--- NWEliza is analyzing the system for common network configuration errors ...


!!! CND0510W: Channel 11 used by your accesspoint interferes with 1 adjacent access points


!!! CND0450W: WLAN key masquerading is not fully tested on this distribution. Please check output file collectNWData.txt for visible WLAN keys and masquerade them manually






--- Go to [http://www.linux-tips-and-tricks.de/CND#English](http://www.linux-tips-and-tricks.de/CND#English) to get more detailed instructions 


--- about the error/warning messages and how to fix the problems on your own.






--- If you are unsuccessful then place the contents of file collectNWData.txt in the net


--- (see [http://www.linux-tips-and-tricks.de/CND_UPL#English](http://www.linux-tips-and-tricks.de/CND_UPL#English) for links) 


--- and then paste the nopaste link on your favorite Linux forum.






==================================================================================================================


===== cat /etc/*[-_]release || cat /etc/*[-_]version =============================================================


/etc/lsb-release


DISTRIB_ID=Ubuntu


DISTRIB_RELEASE=10.04


DISTRIB_CODENAME=lucid


DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"


===== uname -a ===================================================================================================


Linux tracy-laptop 2.6.32-25-generic #45-Ubuntu SMP Sat Oct 16 19:48:22 UTC 2010 i686 GNU/Linux


===== lspci ======================================================================================================


09:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354] (rev 12)


Kernel driver in use: sky2


Kernel modules: sky2


0b:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)


Kernel driver in use: iwl3945


Kernel modules: iwl3945


===== lsusb | grep -v "root hub" =================================================================================


Bus 001 Device 002: ID 05a9:2640 OmniVision Technologies, Inc. OV2640 Webcam


===== lshw -C network (filtered) =================================================================================


       product: 88E8040 PCI-E Fast Ethernet Controller


       vendor: Marvell Technology Group Ltd.


       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation


       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.25 firmware=N/A latency=0 link=no multicast=yes port=twisted pair


       product: PRO/Wireless 3945ABG [Golan] Network Connection


       vendor: Intel Corporation


       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless


       configuration: broadcast=yes driver=iwl3945 ip=192.168.1.2 latency=0 multicast=yes wireless=IEEE 802.11abg


===== lsmod (filtered) ===========================================================================================


| aes_generic     | aes_i586        | ahci            | arc4            | binfmt_misc      |


| bitblit         | cfg80211        | dcdbas          | dell_laptop     | dell_wmi         |


| drm             | drm_kms_helper  | fbcon           | font            | i2c_algo_bit     |


| i915            | ieee1394        | isofs           | iwl3945         | iwlcore          |


| led_class       | lp              | mac80211        | ohci1394        | output           |


| ppdev           | ricoh_mmc       | sbp2            | sdhci           | sdhci_pci        |


| serio_raw       | sky2            | softcursor      | tileblit        | udf              |


| v4l1_compat     | vga16fb         | vgastate        |


===== ls /lib/firmware/* =========================================================================================


| 2.6.24-27-generic       | 2.6.27-17-generic       | 2.6.28-19-generic       | 2.6.31-22-generic        |


| 2.6.32-25-generic       | 3com                    | acenic                  | adaptec                  |


| advansys                | agere_ap_fw.bin         | agere_sta_fw.bin        | aic94xx-seq.fw           |


| ar9170-1.fw             | ar9170-2.fw             | ar9170.fw               | asihpi                   |


| ath3k-1.fw              | atmel_at76c502_3com.bin | atmel_at76c502.bin      | atmel_at76c502d.bin      |


| atmel_at76c502e.bin     | atmel_at76c504_2958.bin | atmel_at76c504a_2958.bin| atmel_at76c504.bin       |


| atmel_at76c506.bin      | atmsar11.fw             | av7110                  | bcm2033-fw.bin           |


| bcm2033-md.hex          | bcm70012fw.bin          | bcm70015fw.bin          | bnx2                     |


| bnx2x-e1-4.8.53.0.fw    | bnx2x-e1-5.2.7.0.fw     | bnx2x-e1h-4.8.53.0.fw   | bnx2x-e1h-5.2.7.0.fw     |


| cis                     | cpia2                   | cxgb3                   | dabusb                   |


| dsp56k                  | dvb-cx18-mpc718-mt352.fw| dvb-dibusb-5.0.0.11.fw  | dvb-fe-cx24116.fw        |


| dvb-fe-nxt2004.fw       | dvb-fe-or51132-qam.fw   | dvb-fe-or51132-vsb.fw   | dvb-fe-or51211.fw        |


| dvb-fe-tda10046.fw      | dvb-fe-tda10048-1.0.fw  | dvb-fe-xc5000-1.6.114.fw| dvb-ttpci-01.fw          |


| dvb-ttusb-dec-2000t.fw  | dvb-ttusb-dec-2540t.fw  | dvb-ttusb-dec-3000s.fw  | dvb-usb-af9015.fw        |


| dvb-usb-avertv-a800-02.fw| dvb-usb-bluebird-01.fw  | dvb-usb-dib0700-1.10.fw | dvb-usb-dib0700-1.20.fw  |


| dvb-usb-dibusb-5.0.0.11.fw| dvb-usb-dibusb-6.0.0.8.fw| dvb-usb-dtt200u-01.fw   | dvb-usb-tvwalkert.fw     |


| dvb-usb-umt-010-02.fw   | dvb-usb-vp702x-01.fw    | dvb-usb-vp7045-01.fw    | dvb-usb-wt220u-02.fw     |


| dvb-usb-wt220u-fc03.fw  | dvb-usb-wt220u-zl0353-01.fw| e100                    | ea                       |


| edgeport                | emi26                   | emi62                   | ess                      |


| i2400m-fw-usb-1.3.sbcf  | i2400m-fw-usb-1.4.sbcf  | intelliport2.bin        | ipw2100-1.3.fw           |


| ipw2100-1.3-i.fw        | ipw2100-1.3-p.fw        | ipw2200-bss.fw          | ipw2200-ibss.fw          |


| ipw2200-sniffer.fw      | isl3877                 | isl3886pci              | isl3886usb               |


| isl3887usb              | isl3890                 | iwlwifi-1000-3.ucode    | iwlwifi-3945-2.ucode     |


| iwlwifi-4965-2.ucode    | iwlwifi-5000-1.ucode    | iwlwifi-5000-2.ucode    | iwlwifi-5150-2.ucode     |


| iwlwifi-6000-4.ucode    | kaweth                  | keyspan                 | keyspan_pda              |


| korg                    | libertas                | matrox                  | mts_cdma.fw              |


| mts_edge.fw             | mts_gsm.fw              | mwl8k                   | myricom                  |


| ngene_15.fw             | ngene_17.fw             | NPE-B                   | NPE-C                    |


| ositech                 | ql2100_fw.bin           | ql2200_fw.bin           | ql2300_fw.bin            |


| ql2322_fw.bin           | ql2400_fw.bin           | ql2500_fw.bin           | qlogic                   |


| r128                    | radeon                  | rt2561.bin              | rt2561s.bin              |


| rt2661.bin              | rt2860.bin              | rt2870.bin              | rt3070.bin               |


| rt3071.bin              | rt73.bin                | RTL8192E                | RTL8192SE                |


| sb16                    | scripts                 | slicoss                 | sun                      |


| sxg                     | tehuti                  | ti_3410.fw              | ti_5052.fw               |


| tigon                   | tr_smctr.bin            | ttusb-budget            | usbdux                   |


| usbduxfast_firmware.bin | usbdux_firmware.bin     | v4l-cx231xx-avcore-01.fw| v4l-cx23418-apu.fw       |


| v4l-cx23418-cpu.fw      | v4l-cx23418-dig.fw      | v4l-cx2341x-dec.fw      | v4l-cx2341x-enc.fw       |


| v4l-cx2341x-init.mpg    | v4l-cx23885-avcore-01.fw| v4l-cx23885-enc.fw      | v4l-cx25840.fw           |


| v4l-pvrusb2-24xxx-01.fw | v4l-pvrusb2-29xxx-01.fw | vicam                   | whiteheat.fw             |


| whiteheat_loader.fw     | xc3028-v27.fw           | yam                     | yamaha                   |


| zd1201-ap.fw            | zd1201.fw               | zd1211                  |


===== ifconfig (filtered for eth|wlan|ra|ath|dsl) ================================================================


eth0      Link encap:Ethernet  HWaddr ##:##:##:##:##:#1  


          UP BROADCAST MULTICAST  MTU:1500  Metric:1


          RX packets:0 errors:0 dropped:0 overruns:0 frame:0


          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0


          collisions:0 txqueuelen:1000 


          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


          Interrupt:16 


wlan0     Link encap:Ethernet  HWaddr ##:##:##:##:##:#2  


          inet addr:@@@  Bcast:@@@  Mask:255.255.255.0


          inet6 addr: fe80::21f:3cff:fe22:e241/64 Scope:Link


          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1


          RX packets:68603 errors:0 dropped:0 overruns:0 frame:0


          TX packets:67953 errors:0 dropped:0 overruns:0 carrier:0


          collisions:0 txqueuelen:1000 


          RX bytes:36415078 (36.4 MB)  TX bytes:10966366 (10.9 MB)


===== iwconfig ===================================================================================================


lo        no wireless extensions.


eth0      no wireless extensions.


wlan0     IEEE 802.11abg  ESSID:"§§§§§§§§2"  


          Mode:Managed  Frequency:2.462 GHz  Access Point: ##:##:##:##:##:#3   


          Bit Rate=54 Mb/s   Tx-Power=14 dBm   


          Retry  long limit:7   RTS thr:off   Fragment thr:off


          Encryption key:@@ @@@-@@@@-@@@@-@@@@-@@@@-@@@@@@@


          Power Management:off


          Link Quality=70/70  Signal level=-21 dBm  


          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0


          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


===== cat /etc/network/interfaces | grep -v "=''" ================================================================


--- /etc/network/interfaces


auto lo


iface lo inet loopback


===== iwlist scanning ============================================================================================


                    Channel:11


                    Quality=70/70  Signal level=-21 dBm  


                    Encryption key:on


                    ESSID:"§§§§§§§§2"


                    Channel:8


                    Quality=55/70  Signal level=-55 dBm  


                    Encryption key:on


                    ESSID:"§§§§§§§§3"


                    Channel:4


                    Quality=34/70  Signal level=-76 dBm  


                    Encryption key:on


                    ESSID:"§§§§§§§§4"


                    Channel:6


                    Quality=29/70  Signal level=-81 dBm  


                    Encryption key:on


                    ESSID:"§§§§§§§§5"


                    IE: IEEE 802.11i/WPA2 Version 1


                    Channel:8


                    Quality=24/70  Signal level=-86 dBm  


                    Encryption key:on


                    ESSID:"§§§§§§§§6"


===== ndiswrapper -l =============================================================================================


No ndiswrapper module loaded


===== Active processes ===========================================================================================


wpa_supplicant:YES knetworkmanager:NO nm-applet:YES


===== ping tests =================================================================================================


Ping of 195.135.220.3 OK


Ping of [www.suse.de](www.suse.de) OK


===== cat /etc/resolv | grep -i "nameserver" =====================================================================


nameserver 192.168.1.1


===== cat /etc/hosts =============================================================================================


127.0.0.1 localhost


127.0.1.1 tracy-laptop


===== route -n | egrep "(eth|ath|ra|wlan|dsl)" ===================================================================


192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0


169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0


0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0


===== Actual date for bias of following greps ====================================================================


16:22:57 2010-11-21


===== grep -i radio /var/log/messages* | tail -n 5 ===============================================================


/var/log/messages.1:Nov 18 18:05:40 tracy-laptop kernel: [22385.547339] Registered led device: iwl-phy0::radio


/var/log/messages.1:Nov 18 19:14:15 tracy-laptop kernel: [22566.550190] Registered led device: iwl-phy0::radio


/var/log/messages.1:Nov 18 23:52:57 tracy-laptop kernel: [   19.333804] Registered led device: iwl-phy0::radio


/var/log/messages.1:Nov 19 07:32:21 tracy-laptop kernel: [   19.775249] Registered led device: iwl-phy0::radio


/var/log/messages.1:Nov 19 18:11:38 tracy-laptop kernel: [  810.873913] Registered led device: iwl-phy0::radio


/var/log/messages.1:Nov 20 07:37:49 tracy-laptop kernel: [   19.782828] Registered led device: iwl-phy0::radio


/var/log/messages.1:Nov 20 15:53:09 tracy-laptop kernel: [   20.025892] Registered led device: iwl-phy0::radio


/var/log/messages.1:Nov 20 19:15:57 tracy-laptop kernel: [   29.939497] Registered led device: iwl-phy0::radio


/var/log/messages.1:Nov 20 19:27:36 tracy-laptop kernel: [   29.950603] Registered led device: iwl-phy0::radio


/var/log/messages.1:Nov 21 08:48:20 tracy-laptop kernel: [   30.123684] Registered led device: iwl-phy0::radio


===== dmesg | grep -i radio | tail -n 5 ==========================================================================


[   29.242170] Registered led device: iwl-phy0::radio


===== tail -n 300 /var/log/messages* | /bin/grep -i firmware | tail -n 10 ========================================


Nov 21 09:36:50 tracy-laptop kernel: [   29.134125] iwl3945 0000:0b:00.0: firmware: requesting iwlwifi-3945-2.ucode


Nov 21 09:36:50 tracy-laptop kernel: [   29.167059] iwl3945 0000:0b:00.0: loaded firmware version 15.32.2.9


Nov 21 08:48:19 tracy-laptop kernel: [   30.006659] iwl3945 0000:0b:00.0: firmware: requesting iwlwifi-3945-2.ucode


Nov 21 08:48:19 tracy-laptop kernel: [   30.050073] iwl3945 0000:0b:00.0: loaded firmware version 15.32.2.9


===== egrep 'eth|ath|wlan|ra' /etc/udev/rules.d/*net_persistent* /etc/udev/rules.d/*persistent-net* ==============


/etc/udev/rules.d/70-persistent-net.rules:SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="##:##:##:##:##:#1", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


/etc/udev/rules.d/70-persistent-net.rules:SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="##:##:##:##:##:#2", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


===== egrep -r 'eth[0-10]|ath[0-10]|wlan[0-10]|ra[0-10]' /etc/modprobe.*|egrep -v -i '#|backlist' ================


==================================================================================================================


*** NWElizaStates V0.6.5.1-5


IF:eth0 IM:1 IF:wlan0 IM:2 DI:2 AP:1 FALON:1 NIC:0 cNiC:2:0 NI:0 cNI:0 PNG:0 DNS:0 MTU:0 NISS:0 IP6:0 WLW:0 RTDT:debian 


[/code]

---

### Post by uncaspi on 2010-11-22
You should close down all applications running and issue

sudo tcpdump -i wlan0

and see if there is any traffic through your card while no applications are running. If you get a lot of printouts you probably have been hacked. If not everything is fine.

---

### Post by TracyO on 2010-11-22
Fabulous.  I had a load of responses from your command, so I changed my IP address.  Sites seem to be back to normal.

Thank you so much--I'm extremely happy to know what the heck happened.

I'm looking into security threads, but any advice on what to do (or what I might have done wrong in the first place?)?  Could the hacker have had access to anything on my laptop or just internet?

Thank you so much for your help.  You are a rock star.

---

### Post by uncaspi on 2010-11-22
They usually don't get root access unless you run applications such as firefox as root.
Glad I could help. Remember to put [SOLVED] on the thread so others could see it.:D

---

