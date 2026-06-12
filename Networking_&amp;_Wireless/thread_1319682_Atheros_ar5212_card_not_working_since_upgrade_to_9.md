---
title: "Atheros ar5212 card not working since upgrade to 9.10"
date: 2009-11-08
forum: Networking &amp; Wireless
---

### Post by ghenk on 2009-11-08
Hi,

I am relatively new to linux but I did have v. 9.04 limping along on an old thinkpad T60 that I use as a toy. It has to be a toy because I can't go around wasting 3 hours every time something stops working to try to fix it.

Today's 3-hour problem: Upgrading to 9.10 and now my functioning wireless card no longer functions. Yes, I realize it was dumb to upgrade something that was previously working... sigh.

The card is an Atheros AR5212 and I have read probably almost all of the forum threads dealing with problems with atheros cards. The computer still detects the card, that's how I found out what type it was specifically, but the computer doesn't detect any networks and there are at least 10 around here.

Here is what I have done thus far that has not fixed the problem:
1) Removed the blacklist of ath drivers. All of them.
2) Installed wicd. No help.
3) Removed all files relating to madwifi. No help.
4) The computer has an external switch for wifi and I have turned this on and off repeatedly. It only seems to affect bluetooth connectivity, when previously it controlled both bluetooth and wifi. The wifi LED also never lights up.

After any of the changes I mentioned above, I also rebooted and fiddled with settings and hence at least 3 hours have been wasted thusly. 

Any other ideas on how I can figure out why the card doesn't function?

JJ

---

### Post by gnu4vn on 2009-11-09
I'm facing the same problem (on my T60 with AR5212). Ubuntu 9.10 doesn't use madwifi as 9.04. 9.10 uses CRDA (see [http://www.ubuntu.com/getubuntu/releasenotes/910](http://www.ubuntu.com/getubuntu/releasenotes/910)).

ath5k doesn't work.


$ lsmod |grep ath5k
ath5k                 124260  0 
mac80211              181236  1 ath5k
ath                     8060  1 ath5k
cfg80211               93052  3 ath5k,mac80211,ath
led_class               4096  2 ath5k,thinkpad_acpi

$ lspci |grep 5212
03:00.0 Ethernet controller: Atheros Communications Inc. AR5212 802.11abg NIC (rev 01)

$ lspci -n |grep 03:00
03:00.0 0200: 168c:1014 (rev 01)

$ iwconfig wlan0
wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
:mad:
Please help!

---

### Post by ghenk on 2009-11-09
Do you think it's possible to try and use ndiswrapper to get the card working? Everyone seems to suggest that as a last resort so I haven't tried using the windows drivers yet. 

Is there a reason why ath5k doesn't work in the new release? 

I still can't figure out how to get the card working and I have run the same commands as gnu4vn and it returns basically exactly the same response. 

Also, I didn't see anything about ath5k or atheros cards not working in the 9.10 release notes. Did I miss something?

---

### Post by gnu4vn on 2009-11-10
Thank ghenk,

I've tried to install ndiswrapper. But I cannot connect.

$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
netathw : driver installed
	device (168C:1014) present (alternate driver: ath5k)

$ iwconfig wlan0
wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

$ tail messages 
Nov 10 13:41:26 skipper kernel: [ 3836.162126] ndiswrapper (iw_set_ap_address:566): setting AP mac address failed (00010003)
Nov 10 13:41:26 skipper kernel: [ 3836.162149] ndiswrapper (iw_set_auth:1602): invalid cmd 12
Nov 10 13:41:31 skipper kernel: [ 3841.165512] ndiswrapper (iw_set_ap_address:566): setting AP mac address failed (00010003)
Nov 10 13:41:31 skipper kernel: [ 3841.165534] ndiswrapper (iw_set_auth:1602): invalid cmd 12
Nov 10 13:41:36 skipper kernel: [ 3846.171101] ndiswrapper (iw_set_ap_address:566): setting AP mac address failed (00010003)
Nov 10 13:41:36 skipper kernel: [ 3846.171124] ndiswrapper (iw_set_auth:1602): invalid cmd 12
Nov 10 13:41:41 skipper kernel: [ 3851.173521] ndiswrapper (iw_set_ap_address:566): setting AP mac address failed (00010003)
Nov 10 13:41:41 skipper kernel: [ 3851.173544] ndiswrapper (iw_set_auth:1602): invalid cmd 12
Nov 10 13:41:46 skipper kernel: [ 3856.179103] ndiswrapper (iw_set_ap_address:566): setting AP mac address failed (00010003)
Nov 10 13:41:46 skipper kernel: [ 3856.179125] ndiswrapper (iw_set_auth:1602): invalid cmd 12

---

### Post by DarkKitsune on 2009-11-10
Tell me if this helps.

[http://ubuntuforums.org/showpost.php?p=8232629&postcount=3](http://ubuntuforums.org/showpost.php?p=8232629&postcount=3)

---

### Post by gnu4vn on 2009-11-10
@DarkKitsune: NOT WORK EITHER!

---

### Post by ghenk on 2009-11-13
Hi Darkkitsune,

I mentioned in my intial post that I have seen that forum post and I tried doing exactly what was suggested there, although I didn't have a madwifi.conf file so I didn't have to worry about removing the blacklist from that file. I did try removing it from the main ath blacklisting file and rebooting but nothing happened. 

I think between all the different solutions I tried I actually ended up probably breaking something else in the process. Is there a way to sort of re-upgrade to 9.10 or just re-format the wifi section?

---

### Post by Syroth on 2009-11-26
So does anyone have any ideas on this? When I had to troubleshoot my atheros based card a month or two ago i caught up on all atheros related material, and when i initially set the card up about a year ago i scoured the internet then. Also, just now I have perused through everything I can find... to no avail.


I am , obviously, having gthe same issue, i upgraded to 9.10 but now all my settings are wiped ( as expected) but i am told there are not any proprietary drivers in use. ifconfig shows a wlan0 , where it should be ath0. i have tried erasing / modifying config files. 

 I have tried more, but i will spare the details... It really is seeming like there is a unique setting / situatioin i am not able to determine.... which i suppose is a fancy way of saying im missing something...

Any help or further suggestions would be appreciated.... like the OP ( i think ) mentioned, i wish there was some way to re-install the wifi aspect of ubuntu.... so it will auto detect accurately as it did before and reset whatever setting has been changed that is causing this complication. 

  Thanks to anyone and everyone in advance!!

---

### Post by drpjkurian on 2009-11-27
Hi everybody

Why cant you give a try to my thread. Let me know the outcome
[http://ubuntuforums.org/showthread.php?t=1309072](http://ubuntuforums.org/showthread.php?t=1309072)

With regards
Dr Kurian

---

### Post by ghenk on 2009-12-01
Hi guys,

I ended up re-formatting back to version 9.04. I couldn't get any of the options on any of the forums to work, though I did not try drpj's very specific instructions. The card works fine now that I have 9.04 installed and everything works great. I don't think I'm going to venture into the crazy upside-down world of updating the operating system again. Too much risk. What will fail next time I upgrade, the monitor drivers?

---

