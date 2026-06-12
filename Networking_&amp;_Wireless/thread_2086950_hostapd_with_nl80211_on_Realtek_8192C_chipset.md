---
title: "hostapd with nl80211 on Realtek 8192C chipset"
date: 2012-11-22
forum: Networking &amp; Wireless
---

### Post by mehta_4v on 2012-11-22
Hi,

   I have Airlink 101 Ultra Mini USB stick which ahs the Realtek 8192 chipset. To make it work I got the driver RTL8188C_8192C_8192D_USB_linux_v3.4.2_3727.20120404. I was able to successfully use the USB stick in STA (Infrastructure) mode. We were also successfully turn it into an access point with hostapd. But while using with hostapd we had to use the driver rtl871xdrv, see the scaled down (minimal) config file below:

```
##################
            hostapd.conf
##################
interface=wlan0
ctrl_interface=/var/run/hostapd
ssid=rtwap
channel=6
driver=rtl871xdrv
```NOTE: This works.
But now I want to use the nl80211 driver in the hostapd for some reasons.
But when I compile the hostapd with the nl80211 and use it the hostapd doesn't start. The driver initialization fails. Putting prints inside the code and libnl debug prints show that on "nl_recvmsgs()" I get ENODEV error. What is this supposed to mean ??

Also further digging shows the nl80211 can be used only with the devices which use softmac and the mac80211 APIs in driver. I dont know whether the driver of rtl8192c is based on the mac80211 framework or not ?!!
Can anybody help me confirm this ????!!!!

When I see whether the 8192c.ko module depends on the mac80211 or not I get the following result:

```
for m in $(lsmod|grep "^rt\|^mac\|^cfg"|awk '{print $1}');do echo -n "$m :";modinfo "$m"|grep depends;done
mac80211 :depends:        cfg80211
cfg80211 :depends:    
```It doesn't. Please help. I need to get this working for my board but first m trying with my PC. Not: AP also works in board.

Some may be useful results:

lsmod 
Module                  Size  Used by
8192cu                493872  0 
mac80211              205402  0 
cfg80211              126144  1 mac80211
binfmt_misc             6587  1 
snd_hda_codec_realtek   203440  1 
fbcon                  35102  71 
...

Please help.

---

### Post by mehta_4v on 2012-11-23
Anybody any idea ?????

---

### Post by mehta_4v on 2012-11-23
Okay now m getting the following error:

Failed to create interface mon.wlan0. 
nl80211 driver initialization failed. 
wlan0: Unable to setup interface. 

I figure out that mon.wlan0 is the monitor interface that hostapd sets up for monitoring the frames. But why the setup fails I can't understand ???

---

