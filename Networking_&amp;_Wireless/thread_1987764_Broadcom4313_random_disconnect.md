---
title: "Broadcom4313 random disconnect"
date: 2012-05-26
forum: Networking &amp; Wireless
---

### Post by biodojo on 2012-05-26
I had an Acer Aspire One 722 with the Atheros Wifi card and it worked  fine on 11.04. So we bought 200 of them for our school. However these  all came with the Broadcom BCM4313 wireless card and there are issues.  It is using the brcmsmac driver and they connect initially. However  after a time (sometimes just a few webpages) some of them lose  connection. However, they still have an IP and network-manager says they  are connected, but no pages load and you can't ping anything on the LAN  or internet. A disconnect/reconnect can fix it, but sometimes a restart  is required. It happens frequently so is a major issue.  Lots of  broadcom drivers are blacklisted: bcm43xx, b43, brcm80211. Any ideas or  experiences with the broadcom4313 card? Please save these computers from  a Windows fate!

---

### Post by chili555 on 2012-05-26
Are you certain that *brcmsmac* is correct for that device? How about we fine tune one of those babies and then you can fix up 199? Please run and post:```
lspci -nn | grep 0280
```

---

### Post by biodojo on 2012-05-29
Thanks for the reply and offer of help!
 
Here is the lspci output

07:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)

I also tried running tail -f /var/log/syslog on a machine that had an issue:
 wpa_supplicant[1029]: Failed to initiate AP scan.
last message repeated 61 times (which repeats every minute)

This message is on both netbooks I have with me that have the issue, and the working ones have very different outputs.

---

### Post by praseodym on 2012-05-29
You need to blacklist the modules **bcma** and **brcmsmac**, too, and install the Broadcom-STA driver from "additional drivers". Reboot after that.

---

### Post by biodojo on 2012-05-29
Thanks for the suggestion.
I will try this other driver, though other posts say that the *brcmsmac *is the one to use and that the STA driver is the bad one :confused: so I guess it might be just try them both and see which one is the most stable on the particular hardware configuration.

[https://help.ubuntu.com/community/AspireOne522#Wireless](https://help.ubuntu.com/community/AspireOne522#Wireless)

---

### Post by chili555 on 2012-05-29
As much as I respect my esteemed colleague praseodym, I suggest you try *brcmsmac* first.

---

### Post by biodojo on 2012-05-29
We are currently using brcmsmac In some testing today Ifound that the one netbook running 12.04 and using the brcmsmac didn't disconnect, while the 2 running 11.04 did disconnect (in that very strange way). I will try updating my 3 test machines to 12.04 and see how they behave tomorrow. 
We are using a customized version of Ubuntu called Ubermix and the 12.04 version is still in beta, but it could be the answer to our issue.

---

### Post by praseodym on 2012-05-30
Thats the best idea, brcmsmac improved with kernel 3.2. Unblacklist the driver after that and uninstall the STA driver.

---

### Post by biodojo on 2012-06-01
Running on 12.04 the wifi has connected reliably in testing. There are occasional hangs in connectivity on our school network nut I can't see any messages in dmesg that report an issue. t occurs about 1 every 15 minutes but if I wait a few seconds and reload the page the connection resumes, so it is very usable.

---

### Post by praseodym on 2012-06-01
Which encryption mode is in use? I recommend usinf WPA2-AES (CCMP), if possible.

---

### Post by biodojo on 2012-06-13
We have 200 new Acer Aspire One 722 with the BCM4313 card. There were major connection problems with 11.04, but upgrading to 12.04 on kernel 3.3 has been more reliable. However, there was an issue where the laptops were connecting and then losing the ability to ping. The issue is intermittent, while trying to track it down I ran tail -f /var/log/syslog and see that every 20 seconds or so this message is displayed.

brcms_ops_bss_info_changed: qos enabled: true (implement)

About every 60 seconds this message is also mixed in:

brcms_c_dotxstatus: Intermediate but not AMPDU

These messages are appearing while the laptop is succefully connected and constantly ping testing (I am getting 97% successful ping returns), so they are aren't error messages per se, but I was wondering if they might be a clue to why there are occasional losses of connectivity. Trouble shooting intermittent issues is tough!

---

### Post by biodojo on 2012-06-13
We are using WPA and WPA2 personal. In additional testing we are losing ping ability when we run some network traffic on the netbook (stream a video and run speedtest.net). The network manager reports connectivity and there are no disconnect messages in dmesg, but ping says unknown host for LAN or internet addresses. After about 1 minute connectivity returns. 

So while the brcmsmac driver in 12.04 seems better than in 11.04 it still isn't good enough for actual use. Does anyone have reliable internet with the Broadcom4313 on the Acer Aspire One 722?

---

### Post by chili555 on 2012-06-13
> We are using WPA and WPA2 personal. Will you please try setting your router to WPA2 only, not mixed mode? I think it's actually an issue with wpa_supplicant, not the brcmsmac driver. Many an Ubuntuan has changed drivers again and again when the fault was likely elsewhere.

---

### Post by biodojo on 2012-06-13
This might explain why I don't get any issues when I test these laptops at home but then they have connection issues at our school. I will talk to the folks in charge of our wifi system and see what options they have.

---

### Post by chili555 on 2012-06-13
> **biodojo said:**
> This might explain why I don't get any issues when I test these laptops at home but then they have connection issues at our school. I will talk to the folks in charge of our wifi system and see what options they have.Indeed. I will be interested in your report. My investigation and understanding of brcmsmac, and wpa_supplicant, for that matter, is a work in progress.

---

### Post by AnotherMuggle on 2012-06-13
I have a HP Mini 210 with a Broadcom 4312 which seems to be behaving in a similar fashion.  Internet access seems to mysteriously stop from time to time, usually after a few hours of use.

Network manager thinks I am connected and as far as I can see the system is quite happy, but internet access is gone and pings to the router fail.

Disabling wireless, waiting a moment, then re-enabling fixes the problem every time.

```
02:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)

```

TK

---

### Post by chili555 on 2012-06-13
> **AnotherMuggle said:**
> I have a HP Mini 210 with a Broadcom 4312 which seems to be behaving in a similar fashion.  Internet access seems to mysteriously stop from time to time, usually after a few hours of use.

Network manager thinks I am connected and as far as I can see the system is quite happy, but internet access is gone and pings to the router fail.

Disabling wireless, waiting a moment, then re-enabling fixes the problem every time.

```
02:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)

```

TKSince you don't have a 4313, the subject of this thread, please start a new thread. Include:```
lsmod | grep -e wl -e b43
```Thanks.

---

### Post by biodojo on 2012-06-13
Hi Another Muggle even though it is a slightly different card it is nice to know that someone else has experienced a similar issue. Got the school network to WPA2 only instead of mixed. Will do some testing. It is always tough to test intermittent issues.

---

### Post by CharlesA on 2012-06-13
Threads merged. Please do not create duplicate threads.

---

### Post by biodojo on 2012-06-13
Well I was able to get a network loss even on WPA2 only (though it seemed a bit harder and I only tested for an hour) However I can't reproduce the error on my home network at all. One thing I have noticed is that on the school network dmesg | grep iee is constantly (every 20 seconds) reporting these messages:
brcms_ops_bss_info_changed: qos enabled: true (implement)
brcms_c_dotxstatus: INTERMEDIATE but not AMPDU


This occurs whether wifi is working or not. At home I don't get those  messages. I do know that we use VoIP at school and our routers have qos  features enabled to make sure the voice communications get priority.  Perhaps the brcms driver isn't handling some aspect of the network  prioritization correctly. I am getting better packet transmission percentages at home though I definitely have slower wifi at home than at school when I run speedtest.net

---

### Post by AnotherMuggle on 2012-06-14
> **chili555 said:**
> Since you don't have a 4313, the subject of this thread, please start a new thread. Include:```
lsmod | grep -e wl -e b43
```Thanks.

I was not trying to hijack the thread, I was mearly trying to contribute some potentially useful information.  I figured since the two model numbers are so similar there was a high possibility there could be a common problem.

There's no need for me to create a new thread as I wasn't looking for any answers.

> **biodojo said:**
> Hi Another Muggle even though it is a slightly different card it is nice to know that someone else has experienced a similar issue. Got the school network to WPA2 only instead of mixed. Will do some testing. It is always tough to test intermittent issues.

Agreed, intermittent issues are the worst.  I hope you find an answer and I will be sure to post here if I notice anything else which may be of interest.

TK

---

### Post by biodojo on 2012-06-14
I was able to install the wl driver and have tested a bit on our school network with very good results. Instead of 96% ping success I am getting almost 100% ping success. Also I have not been able to trigger the connectivity freeze with high traffic that the brcmsmac driver had. So things are looking up. I got the instructions for installing the wl driver from Jim Klein the curator of the Ubuntu for school's remix (Ubermix). The instructions might be ubermix specific so you might need to create the file blacklist-ubermix.conf to get ths to work on your devices. I will report back after more testing, but I can breath easy for now. I want to thank everyone who provided advice in the spirit of sharing.

Check it out at [http://www.ubermix.org](http://www.ubermix.org) 

[LIST=1]
[*] Download and extract to user folder [https://docs.google.com/open?id=0B52M_cKAX2ARTTVodktZWkdFT1k](https://docs.google.com/open?id=0B52M_cKAX2ARTTVodktZWkdFT1k)
[*]In terminal, cd bcmwl*
[*]make && sudo make install
[*]sudo depmod -a
[*]sudo sh -c "echo blacklist brcmsmac >>/etc/modprobe.d/blacklist-ubermix.conf"
[*]sudo sh -c "echo blacklist b43 >>/etc/modprobe.d/blacklist-ubermix.conf"
[*]sudo sh -c "echo blacklist bcma >>/etc/modprobe.d/blacklist-ubermix.conf"
[*]sudo sh -c "echo blacklist ssb >>/etc/modprobe.d/blacklist-ubermix.conf"
[*]sudo gedit /etc/rc.local
[*]add "rmmod ssb" above the exit 0 line at the end
[*]add "modprobe wl" below the rmmod ssd line
[*]reboot
[/LIST]

---

### Post by CharlesA on 2012-06-17
Just a note: It is generally unwise to install random tar.gz files.

If you do need to install something like that, get it from sourceforge or github or another reputable site, not google docs.

---

### Post by praseodym on 2012-06-17
Installation for the 2 latest Broadcom-STA drivers (from the Broadcom-website) via dkms:

[http://forum.ubuntuusers.de/topic/w-lan-acer-4820tg-broadcom-installation-schlae/#post-2865859](http://forum.ubuntuusers.de/topic/w-lan-acer-4820tg-broadcom-installation-schlae/#post-2865859)
In German, should be self-explaining, though.

Drivers from here:

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

---

### Post by biodojo on 2012-06-19
> **CharlesA said:**
> Just a note: It is generally unwise to install random tar.gz files.

If you do need to install something like that, get it from sourceforge or github or another reputable site, not google docs.

Very true and thanks for adding that reminder. Since I have spoken personally and worked for almost a tear with Jim Klein at Ubermix.org I trusted the link he provided. But someone encountering the link in a random forum post should exercise more caution. I could ask Jim to provide a more portable set of instructions including a link to the the driver source files from a standard source.

So far the wl driver performed well in a day of testing 5-6 netbooks, but we won't get a full test of all 200 under working conditions until school gets back in session in August.

---

### Post by CharlesA on 2012-06-19
> **biodojo said:**
> I could ask Jim to provide a more portable set of instructions including a link to the the driver source files from a standard source.

That would probably be a good idea. Maybe host it in a PPA on launchpad?

---

### Post by pakezonite on 2012-07-20
Hi!

I have an HP ProBook with the same Broadcom 4313 wireless chip
and have tried both the restricted wl and the open source brcmsmac
drivers on Xubuntu 12.04 -both gave me a very unstable connection.

In the end I seem to have fixed it by removing network-manager
and installing wicd instead (I remembered this trick from an earlier encounter
with another Broadcom wireless chip some years back giving me headache).

When I first installed wicd it didn't show any signs of life, but I noticed
by looking at the output of: 

```
lshw -c network
```that the logical name of my wireless was actually eth1 and not wlan0,
so after changing the wireless interface setting in wicd preferences to
eth1 instead of wlan0 the thing came to life and has been running 
smoothly ever since! No more packet loss when pinging and working
even at lower signal levels etc. :) 

In the working setup I'm using the restricted wl driver and have made
these additions to /etc/modprobe.d/blacklist.conf:

```
blacklist brcmsmac
blacklist bcma
blacklist b43
blacklist ssb

```I hope this is helps someone!

-P-

---

