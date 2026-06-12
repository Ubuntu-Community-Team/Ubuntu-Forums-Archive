---
title: "Wifi fails with kernel 2.6.28-13, OK with 2.6.28-11"
date: 2009-06-18
forum: Networking &amp; Wireless
---

### Post by Cacadril on 2009-06-18
I just updated my laptop, and got a new kernel. After reboot, the wifi was able to see the networks in the neighborhood, but I repeatedly go a popup "need to authenticate". The password etc was present and correct, but it failed to establish the connection aprox. 6 times. Then I rebooted into the previous kernel, and the connection came up right away.

Some data:

Ubuntu 9.04 jaunty, amd64, acerAspire 5112 WLMi
lspci:
06:02.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)

Related unusual messages in /var/log/kern.log

Jun 18 21:54:07 alabast kernel: [   76.208042] ath5k phy0: gain calibration timeout (2412MHz)
Jun 18 21:54:07 alabast kernel: [   76.208047] ath5k phy0: can't reset hardware (-11)
Jun 18 21:54:07 alabast kernel: [   76.208050] phy0: failed to restore operational channel after scan
Jun 18 21:54:07 alabast kernel: [   76.212896] ath5k phy0: gain calibration timeout (2462MHz)
Jun 18 21:54:07 alabast kernel: [   76.212902] ath5k phy0: can't reset hardware (-11)
Jun 18 21:54:07 alabast kernel: [   76.253204] ath5k phy0: noise floor calibration failed (2462MHz)
Jun 18 21:54:07 alabast kernel: [   76.281072] ath5k phy0: noise floor calibration failed (2412MHz)
Jun 18 21:54:07 alabast kernel: [   76.365198] ath5k phy0: noise floor calibration failed (2412MHz)
Jun 18 21:54:07 alabast kernel: [   76.648656] ath5k phy0: gain calibration timeout (2417MHz)
Jun 18 21:54:07 alabast kernel: [   76.648662] ath5k phy0: can't reset hardware (-11)
Jun 18 21:54:07 alabast kernel: [   76.648665] phy0: failed to set freq to 2417 MHz for scan
Jun 18 21:54:07 alabast kernel: [   76.952428] ath5k phy0: gain calibration timeout (2422MHz)
Jun 18 21:54:07 alabast kernel: [   76.952431] phy0: failed to set freq to 2422 MHz for scan
Jun 18 21:54:08 alabast kernel: [   77.255838] phy0: failed to set freq to 2427 MHz for scan
Jun 18 21:54:08 alabast kernel: [   77.559421] phy0: failed to set freq to 2432 MHz for scan

Thanks

---

### Post by uncle pennybags on 2009-06-19
I have a similar problem. I use WICD instead of Network Manager, and I have NO activity on my wireless card.
 
When I roll back to the older kernel everything works fine. :guitar:

any further ideas?

---

### Post by Cacadril on 2009-06-20
I rebooted today just to see if it made any difference, and the wifi connection came up right away. Other than perhaps the new hal, I cannot see what could have triggered the change. Some transient card malfunction? But seeing all the remote networks.. there are a number of posts around reporting just that, only a bit too sparse, mostly with some different detail.. Anyway, I thought the error had to be at some protocol level or a driver error. Now if people seeing similar problems would only post more technical details. Nobody will find out anything until some bloke chances to post something that gives some developer a deja-vu. The previous post here, uncle pennybags: "no activity" -- how do you know there is no activity? where do you look, what do you see? A small green light not blinking? Did you inspect some logfiles? If so, which ones? It's about giving developers something to go on, and since we are ignorant about all the innards, just striving for some pedantic precision and detail is our best hope to set something in motion.

Here is the output of...
```
/var/log$ grep -E 'ath5|phy0|wlan|06:02' kern.log | tail -17
Jun 20 20:25:09 alabast kernel: [161402.076642] ath5k phy0: noise floor calibration timeout (2437MHz)
Jun 20 20:29:09 alabast kernel: [161642.141106] ath5k phy0: noise floor calibration timeout (2437MHz)
Jun 20 20:57:09 alabast kernel: [163322.104297] ath5k phy0: noise floor calibration timeout (2437MHz)
Jun 20 22:09:15 alabast kernel: [167647.289162] wlan0: disassociating by local choice (reason=3)
Jun 20 22:10:10 alabast kernel: [    0.603661] pci 0000:06:02.0: reg 10 32bit mmio: [0xc0200000-0xc020ffff]
Jun 20 22:10:10 alabast kernel: [   15.396361] ath5k_pci 0000:06:02.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Jun 20 22:10:10 alabast kernel: [   15.396459] ath5k_pci 0000:06:02.0: registered as 'phy0'
Jun 20 22:10:10 alabast kernel: [   15.484097] phy0: Selected rate control algorithm 'pid'
Jun 20 22:10:10 alabast kernel: [   15.603599] ath5k phy0: Atheros AR2413 chip found (MAC: 0x78, PHY: 0x45)
Jun 20 22:10:20 alabast kernel: [   30.239743] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun 20 22:11:19 alabast kernel: [   89.504175] wlan0: authenticate with AP 00:21:29:bd:bd:d5
Jun 20 22:11:19 alabast kernel: [   89.505619] wlan0: authenticated
Jun 20 22:11:19 alabast kernel: [   89.505623] wlan0: associate with AP 00:21:29:bd:bd:d5
Jun 20 22:11:19 alabast kernel: [   89.507917] wlan0: RX AssocResp from 00:21:29:bd:bd:d5 (capab=0x411 status=0 aid=2)
Jun 20 22:11:19 alabast kernel: [   89.507920] wlan0: associated
Jun 20 22:11:19 alabast kernel: [   89.508547] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Jun 20 22:11:33 alabast kernel: [  100.108064] wlan0: no IPv6 routers present
```Before the reboot I did another aptitude update / aptitude full-upgrade. The packages affected were
(I checked the file manually first, no other packages were installed/removed):

```
/var/log$ grep 2009-06-20 dpkg.log | grep upgrade
2009-06-20 21:58:40 upgrade tzdata-java 2009f-0ubuntu1 2009j-0ubuntu0.9.04
2009-06-20 21:58:40 upgrade tzdata 2009f-0ubuntu1 2009j-0ubuntu0.9.04
2009-06-20 21:58:46 upgrade file 4.26-2ubuntu3 4.26-2ubuntu4
2009-06-20 21:58:46 upgrade libmagic1 4.26-2ubuntu3 4.26-2ubuntu4
2009-06-20 21:58:47 upgrade dvipdfmx 1:20080607-1 1:20080607-1ubuntu1
2009-06-20 21:58:47 upgrade libhal1 0.5.12~rc1+git20090403-0ubuntu2 0.5.12~rc1+git20090403-0ubuntu3
2009-06-20 21:58:47 upgrade libhal-storage1 0.5.12~rc1+git20090403-0ubuntu2 0.5.12~rc1+git20090403-0ubuntu3
2009-06-20 21:58:48 upgrade hal 0.5.12~rc1+git20090403-0ubuntu2 0.5.12~rc1+git20090403-0ubuntu3
2009-06-20 21:58:51 upgrade python-cupshelpers 1.1.3+git20090218-0ubuntu19.1 1.1.3+git20090218-0ubuntu19.2
2009-06-20 21:58:53 upgrade system-config-printer-common 1.1.3+git20090218-0ubuntu19.1 1.1.3+git20090218-0ubuntu19.2
2009-06-20 21:58:54 upgrade system-config-printer-gnome 1.1.3+git20090218-0ubuntu19.1 1.1.3+git20090218-0ubuntu19.2
```Thanks

---

### Post by CrazyMike on 2009-06-21
I've got the same problem on one of my machines (the other is on the wired network).  Wireless works fine on 2.6.28-11-generic but on 2.6.28-13-generic it 'sees' but cannot connect to my WPA wireless router.  

I'm surprised there aren't more complaints about this out there by now...

System info:

OS:Ubuntu 9.04
MB:Asus A7N8X-Deluxe
Processor:Athlon 2500XP
Wireless:  ENCORE ENLWI-N PCI adapter autoconfigured using Jaunty (connects at 54MB - not sure how to get to 802.11n speeds)

---

### Post by dBuster on 2009-06-21
If you are like me who uses MADWIFI for the Atheros chipset every time you get a kernel update you must re-make the package to get the wifi working again.

Follow the steps in this post for what to do after a kernel update

[http://ubuntuforums.org/showthread.php?t=816780]("http://ubuntuforums.org/showthread.php?t=816780")

---

### Post by jsravn on 2009-06-21
I too am seeing issues with the kernel upgrade. My wifi sporadically refuses to connect. Turning it on and off on my laptop through hardware seems to fix it... I'm using the ipw2200 driver.

---

### Post by Dinion on 2009-06-22
It definitely has something to do with security being turned on for the router.
After I disabled the wireless security I had no problem connecting again. 
Obviously this is it's own problem since I don't feel like sharing my connection with the world, but I don't know enough to fix it. Hopefully this bit of info adds something to the discussion.

---

### Post by camason on 2009-06-23
I also have this issue:

Asus Eee 901
Realtek RT2860
Ubuntu 9.04

2.6.28-13-generic cannot connect to WPA (not tried others as only router here is WPA)
2.6.28-11-generic can connect fine


I also switched the wireless hardware on/off via bios, but that has made no difference.

Thanks

---

### Post by chrismx on 2009-06-25
I have the same issue, after the kernel upgrade, I cant connect back to my wireless connection, my laptop is a dell latitude d630, with an Intel chipset.

---

### Post by Cacadril on 2009-06-28
I'm the original poster. I have not seen the problem again. However, I have analyzed the kernel log in an attempt at distinguishing between messages that are, and are not, related.

I have booted into 2.6.28-13 in all four times. The first time I had the problem. After that I booted into 2.6.28-11 a last time, and was immediately connected. Then, as stated above, I tried -13 again, and I was immediately connected. Now I have booted into -13 two more times with no problems.

I have filtered the kern.log* files for messages containing wlan or ath5 or phy0. Then I have run them through a perl script to extract the message part (as opposed to the timestamp), sorted the messages alphabetically, and written them out with annotations: '1' means seen only under 2.6.28-11, '2' means seen only under -13, and '3' means seen under both. Then follows the date and time of the first instance and last instance of the message. If both these times belong in the first run of -13, during which the problem did happen, there are '#' signs in front of the times. Otherwise there are ':' chars.

You may have to scroll to the right to see the codes and times!

I have separated the messages that I have only seen while having the problem:

```
ath5k phy0: can't reset hardware (-11)                                                     2 # 2009-06-18 21:54:07 # 2009-06-18 23:32:52
ath5k phy0: gain calibration timeout (2412MHz)                                             2 # 2009-06-18 21:54:07 # 2009-06-18 23:32:51
ath5k phy0: gain calibration timeout (2417MHz)                                             2 # 2009-06-18 21:54:07 # 2009-06-18 23:32:51
ath5k phy0: gain calibration timeout (2422MHz)                                             2 # 2009-06-18 21:54:07 # 2009-06-18 23:32:51
ath5k phy0: gain calibration timeout (2427MHz)                                             2 # 2009-06-18 21:54:13 # 2009-06-18 23:32:52
ath5k phy0: gain calibration timeout (2432MHz)                                             2 # 2009-06-18 21:54:13 # 2009-06-18 23:32:52
ath5k phy0: gain calibration timeout (2437MHz)                                             2 # 2009-06-18 22:00:01 # 2009-06-18 22:00:01
ath5k phy0: gain calibration timeout (2462MHz)                                             2 # 2009-06-18 21:54:07 # 2009-06-18 21:57:39
ath5k phy0: noise floor calibration failed (2412MHz)                                       2 # 2009-06-18 21:54:07 # 2009-06-18 21:58:43
ath5k phy0: noise floor calibration failed (2417MHz)                                       2 # 2009-06-18 22:12:51 # 2009-06-18 23:32:51
ath5k phy0: noise floor calibration failed (2422MHz)                                       2 # 2009-06-18 22:01:37 # 2009-06-18 22:01:37
ath5k phy0: noise floor calibration failed (2427MHz)                                       2 # 2009-06-18 21:54:26 # 2009-06-18 22:08:31
ath5k phy0: noise floor calibration failed (2462MHz)                                       2 # 2009-06-18 21:54:07 # 2009-06-18 21:57:38
ath5k phy0: noise floor calibration timeout (2432MHz)                                      2 # 2009-06-18 22:06:41 # 2009-06-18 22:07:36
phy0: failed to restore operational channel after scan                                     2 # 2009-06-18 21:54:07 # 2009-06-18 23:32:55
phy0: failed to set freq to 2412 MHz for scan                                              2 # 2009-06-18 21:54:12 # 2009-06-18 23:32:51
phy0: failed to set freq to 2427 MHz for scan                                              2 # 2009-06-18 21:54:08 # 2009-06-18 23:32:52
phy0: failed to set freq to 2432 MHz for scan                                              2 # 2009-06-18 21:54:08 # 2009-06-18 23:32:52
phy0: failed to set freq to 2437 MHz for scan                                              2 # 2009-06-18 21:54:08 # 2009-06-18 23:32:52
phy0: failed to set freq to 2442 MHz for scan                                              2 # 2009-06-18 21:54:08 # 2009-06-18 23:32:53
phy0: failed to set freq to 2447 MHz for scan                                              2 # 2009-06-18 21:54:09 # 2009-06-18 23:32:53
phy0: failed to set freq to 2452 MHz for scan                                              2 # 2009-06-18 21:54:09 # 2009-06-18 23:32:53
phy0: failed to set freq to 2457 MHz for scan                                              2 # 2009-06-18 21:54:09 # 2009-06-18 23:32:54
phy0: failed to set freq to 2462 MHz for scan                                              2 # 2009-06-18 21:54:10 # 2009-06-18 23:32:54
phy0: failed to set freq to 2467 MHz for scan                                              2 # 2009-06-18 21:54:10 # 2009-06-18 23:32:54
phy0: failed to set freq to 2472 MHz for scan                                              2 # 2009-06-18 21:54:10 # 2009-06-18 23:32:54
phy0: failed to set freq to 2484 MHz for scan                                              2 # 2009-06-18 21:54:11 # 2009-06-18 23:32:55
wlan0: Failed to config new SSID to the low-level driver                                   2 # 2009-06-18 21:57:39 # 2009-06-18 21:57:39

```Here come the messages that I have seen (also or only) when I was NOT having the problem:

```
ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready                                         3 : 2009-05-22 22:44:41 : 2009-06-26 13:04:10
ADDRCONF(NETDEV_UP): wlan0: link is not ready                                              3 : 2009-05-22 22:34:54 : 2009-06-26 13:04:09
ath5k phy0: Atheros AR2413 chip found (MAC: 0x78, PHY: 0x45)                               3 : 2009-05-22 22:34:46 : 2009-06-26 13:03:59
ath5k phy0: can't reset hardware (-5)                                                      1 : 2009-05-26 00:20:59 : 2009-05-26 01:32:59
ath5k phy0: failed to warm reset the MAC Chip                                              1 : 2009-05-26 00:20:59 : 2009-05-26 01:32:59
ath5k phy0: noise floor calibration timeout (2412MHz)                                      3 : 2009-05-26 11:14:59 : 2009-06-22 07:28:23
ath5k phy0: noise floor calibration timeout (2417MHz)                                      3 : 2009-05-28 22:23:29 : 2009-06-18 22:22:51
ath5k phy0: noise floor calibration timeout (2422MHz)                                      3 : 2009-05-28 21:59:29 : 2009-06-18 21:55:59
ath5k phy0: noise floor calibration timeout (2437MHz)                                      3 : 2009-06-01 21:52:44 : 2009-06-28 20:58:10
ath5k phy0: noise floor calibration timeout (2442MHz)                                      2 : 2009-06-26 00:22:19 : 2009-06-26 00:22:19
ath5k phy0: noise floor calibration timeout (2462MHz)                                      2 : 2009-06-18 21:55:04 : 2009-06-21 17:36:14
ath5k phy0: noise floor calibration timeout (2484MHz)                                      2 : 2009-06-26 04:12:20 : 2009-06-26 04:12:20
ath5k phy0: unsupported jumbo                                                              3 : 2009-05-25 17:08:08 : 2009-06-28 17:24:40
ath5k_pci 0000:06:02.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22                         3 : 2009-05-22 22:34:46 : 2009-06-26 13:03:59
ath5k_pci 0000:06:02.0: PCI INT A disabled                                                 3 : 2009-06-18 21:31:14 : 2009-06-24 19:57:13
ath5k_pci 0000:06:02.0: registered as 'phy0'                                               3 : 2009-05-22 22:34:46 : 2009-06-26 13:03:59
ath5k_pci 0000:06:02.0: restoring config space at offset 0x3 (was 0x5008, writing 0xa808)  3 : 2009-06-18 21:31:14 : 2009-06-24 19:57:13
device wlan0 entered promiscuous mode                                                      3 : 2009-05-25 21:18:15 : 2009-06-21 17:50:02
device wlan0 left promiscuous mode                                                         3 : 2009-05-25 21:20:32 : 2009-06-21 18:02:54
phy0: Selected rate control algorithm 'pid'                                                3 : 2009-05-22 22:34:46 : 2009-06-26 13:03:59
phy0: failed to set freq to 2417 MHz for scan                                              3 : 2009-05-26 00:20:59 : 2009-06-18 23:32:51
phy0: failed to set freq to 2422 MHz for scan                                              3 : 2009-05-26 01:32:59 : 2009-06-18 23:32:51
wlan0 direct probe responded                                                               3 : 2009-05-24 20:59:52 : 2009-06-26 13:04:10
wlan0: AP denied association (code=17)                                                     1 : 2009-05-22 21:25:47 : 2009-05-24 11:58:40
wlan0: No ProbeResp from current AP 00:21:29:bd:bd:d5 - assume out of range                3 : 2009-05-29 11:10:02 : 2009-06-23 10:04:27
wlan0: RX AssocResp from 00:13:46:7b:03:f3 (capab=0x421 status=0 aid=4)                    1 : 2009-06-05 11:12:08 : 2009-06-05 11:12:08
wlan0: RX AssocResp from 00:13:46:7b:03:f3 (capab=0x421 status=0 aid=5)                    1 : 2009-06-10 10:37:07 : 2009-06-10 10:37:07
wlan0: RX AssocResp from 00:13:46:7b:03:f3 (capab=0x421 status=0 aid=7)                    1 : 2009-06-11 15:07:04 : 2009-06-11 15:07:04
wlan0: RX AssocResp from 00:17:9a:63:23:4b (capab=0x431 status=0 aid=1)                    1 : 2009-05-22 21:25:50 : 2009-05-24 20:59:52
wlan0: RX AssocResp from 00:17:9a:63:23:4b (capab=0x431 status=17 aid=1073)                1 : 2009-05-22 21:25:47 : 2009-05-24 11:58:40
wlan0: RX AssocResp from 00:1c:f0:b7:88:db (capab=0x421 status=0 aid=1)                    1 : 2009-05-25 14:40:37 : 2009-06-07 19:23:12
wlan0: RX AssocResp from 00:1c:f0:b7:88:db (capab=0x421 status=0 aid=4)                    2 : 2009-06-18 21:53:23 : 2009-06-26 13:04:10
wlan0: RX AssocResp from 00:1d:0f:ea:65:94 (capab=0x421 status=0 aid=17)                   1 : 2009-06-18 23:35:39 : 2009-06-18 23:35:39
wlan0: RX AssocResp from 00:21:29:bd:bd:d5 (capab=0x411 status=0 aid=1)                    3 : 2009-05-29 11:19:13 : 2009-06-26 15:28:32
wlan0: RX AssocResp from 00:21:29:bd:bd:d5 (capab=0x411 status=0 aid=2)                    3 : 2009-05-25 14:45:39 : 2009-06-23 21:14:26
wlan0: RX ReassocResp from 00:17:9a:63:23:4b (capab=0x431 status=17 aid=1)                 1 : 2009-05-22 21:25:47 : 2009-05-24 11:58:40
wlan0: RX ReassocResp from 00:21:29:bd:bd:d5 (capab=0x411 status=0 aid=1)                  1 : 2009-05-28 15:47:31 : 2009-05-29 11:27:43
wlan0: RX ReassocResp from 00:21:29:bd:bd:d5 (capab=0x411 status=0 aid=2)                  3 : 2009-06-08 11:54:45 : 2009-06-23 11:37:22
wlan0: associate with AP 00:13:46:7b:03:f3                                                 1 : 2009-06-05 11:12:08 : 2009-06-11 15:07:04
wlan0: associate with AP 00:17:9a:63:23:4b                                                 1 : 2009-05-22 21:25:47 : 2009-05-24 20:59:52
wlan0: associate with AP 00:1c:f0:b7:88:db                                                 3 : 2009-05-25 14:40:37 : 2009-06-26 13:04:10
wlan0: associate with AP 00:1d:0f:ea:65:94                                                 1 : 2009-06-18 23:35:39 : 2009-06-18 23:35:39
wlan0: associate with AP 00:21:29:bd:bd:d5                                                 3 : 2009-05-25 14:45:39 : 2009-06-26 15:28:32
wlan0: associated                                                                          3 : 2009-05-22 21:25:50 : 2009-06-26 15:28:32
wlan0: association with AP 00:17:9a:63:23:4b timed out                                     1 : 2009-05-22 21:25:48 : 2009-05-24 11:58:41
wlan0: authenticate with AP 00:13:46:7b:03:f3                                              1 : 2009-06-05 11:12:08 : 2009-06-11 15:07:04
wlan0: authenticate with AP 00:17:9a:63:23:4b                                              1 : 2009-05-22 21:25:50 : 2009-05-24 20:59:52
wlan0: authenticate with AP 00:1c:f0:b7:88:db                                              3 : 2009-05-25 14:40:37 : 2009-06-26 13:04:10
wlan0: authenticate with AP 00:1d:0f:ea:65:94                                              1 : 2009-06-18 23:35:39 : 2009-06-18 23:35:39
wlan0: authenticate with AP 00:21:29:bd:bd:d5                                              3 : 2009-05-25 14:45:39 : 2009-06-26 15:28:32
wlan0: authenticated                                                                       3 : 2009-05-22 21:25:50 : 2009-06-26 15:28:32
wlan0: authentication with AP 00:21:29:bd:bd:d5 timed out                                  3 : 2009-05-29 11:12:07 : 2009-06-18 21:54:12
wlan0: deauthenticated                                                                     3 : 2009-05-25 14:40:37 : 2009-06-23 11:37:21
wlan0: direct probe to AP 00:13:46:7b:03:f3 timed out                                      1 : 2009-06-18 21:31:17 : 2009-06-18 21:31:17
wlan0: direct probe to AP 00:13:46:7b:03:f3 try 1                                          1 : 2009-06-18 21:31:17 : 2009-06-18 21:31:17
wlan0: direct probe to AP 00:13:46:7b:03:f3 try 2                                          1 : 2009-06-18 21:31:17 : 2009-06-18 21:31:17
wlan0: direct probe to AP 00:13:46:7b:03:f3 try 3                                          1 : 2009-06-18 21:31:17 : 2009-06-18 21:31:17
wlan0: direct probe to AP 00:17:9a:63:23:4b try 1                                          1 : 2009-05-24 20:59:52 : 2009-05-24 20:59:52
wlan0: direct probe to AP 00:1c:f0:b7:88:db timed out                                      1 : 2009-06-08 11:53:18 : 2009-06-08 11:53:18
wlan0: direct probe to AP 00:1c:f0:b7:88:db try 1                                          3 : 2009-05-25 14:40:36 : 2009-06-26 13:04:10
wlan0: direct probe to AP 00:1c:f0:b7:88:db try 2                                          3 : 2009-05-25 14:40:37 : 2009-06-24 19:57:18
wlan0: direct probe to AP 00:1c:f0:b7:88:db try 3                                          3 : 2009-06-08 11:53:18 : 2009-06-24 19:57:18
wlan0: direct probe to AP 00:1d:0f:ea:65:94 try 1                                          1 : 2009-06-18 23:35:39 : 2009-06-18 23:35:39
wlan0: direct probe to AP 00:21:29:bd:bd:d5 timed out                                      3 : 2009-05-29 12:11:51 : 2009-06-23 10:04:29
wlan0: direct probe to AP 00:21:29:bd:bd:d5 try 1                                          3 : 2009-05-28 15:47:31 : 2009-06-23 11:37:22
wlan0: direct probe to AP 00:21:29:bd:bd:d5 try 2                                          3 : 2009-05-29 12:11:50 : 2009-06-23 10:04:29
wlan0: direct probe to AP 00:21:29:bd:bd:d5 try 3                                          3 : 2009-05-29 12:11:51 : 2009-06-23 10:04:29
wlan0: disassociated                                                                       1 : 2009-05-22 21:25:46 : 2009-05-24 11:58:39
wlan0: disassociating by local choice (reason=3)                                           3 : 2009-05-22 22:33:47 : 2009-06-26 13:04:11
wlan0: no IPv6 routers present                                                             3 : 2009-05-22 22:44:51 : 2009-06-26 13:04:21

```

---

### Post by Cacadril on 2009-06-28
If people want to contribute some real technical information, try the following commands in a terminal window, and use cut'n paste to copy the session into this forum. Use the '#' button above the message entry window in the forum, to convert the session into a scrollable code window.

Kernel programmers insert logging instructions in their modules precisely for this purpose, so the users have a way of reporting what is going on. If the programmers find the messages are not helpful, they add more or different logging in the next versions. It does not matter whether you understand the messages.

To find out exactly what kind of wireless cards you have, run this command:

```
$ sudo lspci | grep Ethernet

```On my computer the output is:

```
06:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
06:02.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)

```Notice the leading numbers, you need them to find the associated messages in the kernel log.

There is nothing in this output that tells that the second line is the wireless. You may happen to know that Atheros is a maker of wireless chips. Or you may think that Gigabit sounds like a wired network card, since "gigabit" is a bit much for wireless.

To find out what kernel modules are handling the devices, repeat the command with the option "-k" added. To get info only about the 06:02 device, add "-s 06:02":

```
$ sudo lspci -s 06:02 -k
06:02.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
    Kernel driver in use: ath5k_pci
    Kernel modules: ath_pci, ath5k

```Now, you can scan the kernel log files for messages related to the device or the driver/module.

```
$ sudo zgrep -h -E "06:02|wlan|ath5k|ath_pci|Atheros|Linux version" $(ls -rt /var/log/kern.log*)

```The command sorts the files in order of incrreasing last modification times. This means the messages will show up in order of their timestamps with the newest messages last.

The command picks all messages containing "06:02" anywhere, even in the timestamp. You will have to use common sense to weed out unrelated messages issued some day at 12:06:02.

The command also looks for messages containing the words specified, wlan, ath5k, ath_pci, and Atheros.  I added the "wlan" word because that is what shows up in the output of "ifconfig". Run the command 

$ sudo ifconfig

to get a list of network devices and their names and states. "Network devices" is different from "interface cards". The latter is more hardware-related, the former more software related. 

The command also looks for messages containing the words "Linux version". The kernel logs its version when it starts, and it is handy for programmers to know. Especially if you have upgraded the kernel, this helps distinguish messages issued by the earlier kernel.

If you are concerned about security, you may delete or modify the ethernet addresses and IP adresses that may appear. 00:21:29:bd:bd:d5 is an example ethernet address. However, wireless devices broadcast their ethernet addresses, so attackers see them anyway.

On my computer, the messages since last boot are:

```
Jun 26 13:03:59 alabast kernel: [    0.000000] Linux version 2.6.28-13-generic (buildd@yellow) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #44-Ubuntu SMP Tue Jun 2 07:55:09 UTC 2009 (Ubuntu 2.6.28-13.44-generic)
Jun 26 13:03:59 alabast kernel: [    0.603660] pci 0000:06:02.0: reg 10 32bit mmio: [0xc0200000-0xc020ffff]
Jun 26 13:03:59 alabast kernel: [   15.380970] ath5k_pci 0000:06:02.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Jun 26 13:03:59 alabast kernel: [   15.381096] ath5k_pci 0000:06:02.0: registered as 'phy0'
Jun 26 13:03:59 alabast kernel: [   15.590711] ath5k phy0: Atheros AR2413 chip found (MAC: 0x78, PHY: 0x45)
Jun 26 13:04:09 alabast kernel: [   30.289754] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun 26 13:04:10 alabast kernel: [   32.221671] wlan0: direct probe to AP 00:1c:f0:b7:88:db try 1
Jun 26 13:04:10 alabast kernel: [   32.226619] wlan0 direct probe responded
Jun 26 13:04:10 alabast kernel: [   32.226626] wlan0: authenticate with AP 00:1c:f0:b7:88:db
Jun 26 13:04:10 alabast kernel: [   32.230776] wlan0: authenticated
Jun 26 13:04:10 alabast kernel: [   32.230780] wlan0: associate with AP 00:1c:f0:b7:88:db
Jun 26 13:04:10 alabast kernel: [   32.234595] wlan0: RX AssocResp from 00:1c:f0:b7:88:db (capab=0x421 status=0 aid=4)
Jun 26 13:04:10 alabast kernel: [   32.234600] wlan0: associated
Jun 26 13:04:10 alabast kernel: [   32.235172] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Jun 26 13:04:11 alabast kernel: [   32.275158] wlan0: disassociating by local choice (reason=3)
Jun 26 13:04:21 alabast kernel: [   42.552053] wlan0: no IPv6 routers present
Jun 26 15:28:32 alabast kernel: [ 8693.447126] wlan0: authenticate with AP 00:21:29:bd:bd:d5
Jun 26 15:28:32 alabast kernel: [ 8693.448573] wlan0: authenticated
Jun 26 15:28:32 alabast kernel: [ 8693.448579] wlan0: associate with AP 00:21:29:bd:bd:d5
Jun 26 15:28:32 alabast kernel: [ 8693.450855] wlan0: RX AssocResp from 00:21:29:bd:bd:d5 (capab=0x411 status=0 aid=1)
Jun 26 15:28:32 alabast kernel: [ 8693.450859] wlan0: associated
Jun 27 02:15:08 alabast kernel: [47487.124424] ath5k phy0: unsupported jumbo
Jun 27 09:32:16 alabast kernel: [73714.873334] ath5k phy0: unsupported jumbo
Jun 27 10:25:19 alabast kernel: [76897.363246] ath5k phy0: unsupported jumbo
Jun 27 15:48:47 alabast kernel: [96305.777050] ath5k phy0: unsupported jumbo
Jun 28 10:26:10 alabast kernel: [163349.137416] ath5k phy0: noise floor calibration timeout (2437MHz)
Jun 28 14:09:44 alabast kernel: [176763.253057] ath5k phy0: unsupported jumbo
Jun 28 15:46:56 alabast kernel: [182594.614949] ath5k phy0: unsupported jumbo
Jun 28 17:24:40 alabast kernel: [188458.845174] ath5k phy0: unsupported jumbo
Jun 28 18:00:10 alabast kernel: [190589.140473] ath5k phy0: noise floor calibration timeout (2437MHz)
Jun 28 18:04:10 alabast kernel: [190829.137055] ath5k phy0: noise floor calibration timeout (2437MHz)
Jun 28 18:06:10 alabast kernel: [190949.152488] ath5k phy0: noise floor calibration timeout (2437MHz)
Jun 28 20:56:10 alabast kernel: [201149.134378] ath5k phy0: noise floor calibration timeout (2437MHz)
Jun 28 20:58:10 alabast kernel: [201269.137371] ath5k phy0: noise floor calibration timeout (2437MHz)

```

---

### Post by lvictor on 2009-07-19
Same problems since i fresh installed jaunty... (was using intrepid before and worked fine on the same dell laptop)

I must ifconfig wlan0 down then ifconfig wlan0 up to be able to connect via network manager...

here is a dmesg with >>>> inserts to indicates the commands I typed to unblock the situation... I left the MAC intact so you can lookup manufacturers ids...

my driver is iwl3945

BTW... I'm not sure if ubuntu gurus read this forum or no but in case, I would like to emphasis on the fact that I never had so many regressions with linux than since I run ubuntu... before, one needed to wait for ages to get a driver but once it as working the setup could be trusted... now updates would break your setup all the time... so far I've only be annoyed with wifi and bluetooth, but I'm not sure I would trust updates for a server... not sure I would trust ubuntu for my work laptop... its sad to admint but windows have proven more reliable at work than ubuntu at home... I never thought I'd say something like this... never imagined I would even write it !

here is the dmesg in case it can help to understand what is going on... I don't count on help though...

[   20.625532] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.638124] iwl3945 0000:0c:00.0: firmware: requesting iwlwifi-3945-1.ucode
[   20.823272] Registered led device: iwl-phy0:radio
[   20.823348] Registered led device: iwl-phy0:assoc
[   20.823381] Registered led device: iwl-phy0:RX
[   20.823407] Registered led device: iwl-phy0:TX
[   20.842367] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   22.446499] wlan0: authenticate with AP 2e:4f:a7:16:8f:ca
[   22.450053] wlan0: authenticated
[   22.450056] wlan0: associate with AP 2e:4f:a7:16:8f:ca
[   22.482920] wlan0: RX AssocResp from 2e:4f:a7:16:8f:ca (capab=0x401 status=0 aid=1)
[   22.482923] wlan0: associated
[   22.509141] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   22.556544] wlan0: disassociating by local choice (reason=3)
[   33.248036] wlan0: no IPv6 routers present
[   53.116927] wlan0: deauthenticated
[  179.282732] NVRM: Xid (0001:00): 6, PE0000 0200 07800000 0000fdf4 ffd8cfc7 00000000
>>>> ifconfig wlan0 down
[  246.040549] iwl3945: Can't stop Rx DMA.
>>>> ifconfig wlan0 up
[  262.958638] Registered led device: iwl-phy0:radio
[  262.959099] Registered led device: iwl-phy0:assoc
[  262.960681] Registered led device: iwl-phy0:RX
[  262.960737] Registered led device: iwl-phy0:TX
[  262.979727] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  268.699784] wlan0: authenticate with AP 2e:4f:a7:16:8f:c8
[  268.701894] wlan0: authenticated
[  268.701902] wlan0: associate with AP 2e:4f:a7:16:8f:c8
[  268.709157] wlan0: RX AssocResp from 2e:4f:a7:16:8f:c8 (capab=0x411 status=0 aid=1)
[  268.709164] wlan0: associated
[  268.711886] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  279.196047] wlan0: no IPv6 routers present
[  834.797280] CE: hpet increasing min_delta_ns to 15000 nsec

---

