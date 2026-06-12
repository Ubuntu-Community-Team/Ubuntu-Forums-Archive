---
title: "wireless disconnects periodically (RTL8191SEvB Wireless LAN Controller (rev 10))"
date: 2010-12-12
forum: Networking &amp; Wireless
---

### Post by fwin on 2010-12-12
Hi everybody,

I am having some issues with the network manager. My wireless connection stops working periodically (every 5 or 10 min), I have to reboot my laptop in order to make it work again. I am using ubuntu 10.10 64bit and the following wireless device:

Network controller: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller (rev 10)


I also have windows installed in this laptop and the wireless device works fine there. 

I would appreciate any help you can give me.

---

### Post by pastalavista on 2010-12-12
I was advised to edit /etc/NetworkManager/nm-system-settings.conf and change to ```
[ifupdown]
managed=true
```

Originally, mine said "managed=false" and it was acting like yours. Since I changed it, it still goes out sometimes, but not nearly as often as before.

---

### Post by fwin on 2010-12-12
Hi PASTALAVISTA,

thanks for your  response, yes mine also said  "managed=false", I already changed it to  "managed=true" hopefully this will work!

thanks again!

---

### Post by fwin on 2010-12-12
I have used the wireless device for about 1hr now and it went out about 5 min ago. The proposed modification is helpful,  now it doesn't drop the connection that often.  But I still could not reconnect to the wireless network after it went out (i had to reboot in order to get a connection). 

Does anyone else have any other suggestions?

---

### Post by fwin on 2010-12-13
I just want to mention that I also tried to change the network manager as explained by marcobra, here:

[https://answers.launchpad.net/ubuntu/+source/network-manager/+question/130154](https://answers.launchpad.net/ubuntu/+source/network-manager/+question/130154)


This did not work for me, I have the exact same problem whether I use network-manager or WICD.  :confused:


HELP!!

---

### Post by timekillerj on 2010-12-16
I am having this same problem on my Toshiba Qosmio X505. Haven't found a fix yet, but at least I can save you some reboots:

```
sudo rmmod r8192se_pci && sleep 2 && sudo modprobe r8192se_pci
```

Run that in a terminal and your wireless will come back.

---

### Post by fwin on 2010-12-20
Thanks for the suggestion timekillerj, it did work for me!

I also found this website do you think this is a solution? it looks similar to what you suggested. I just dont know if it is the same problem that we are having.

[http://www.frozentux.net/2010/12/ubuntu-10-10-r8192se_pci-driver-on-the-toshiba-satellite-t130-17e-realtek-rtl8191sevb/](http://www.frozentux.net/2010/12/ubuntu-10-10-r8192se_pci-driver-on-the-toshiba-satellite-t130-17e-realtek-rtl8191sevb/)

---

### Post by Pennoid on 2011-03-02
I'm having very similar issues. I have a Lenovo Thinkpad 410i with a RTL8191SEvB wireless controller. Every 5 minutes or so, I don't technically lose the connection, but I stop sending and receiving information and pages won't load etc. All I do is click on Network Manager and reconnect, for a five minute fix, only for it to happen again in five or ten minutes....

Very Frustrating....

---

### Post by fwin on 2011-03-04
Hi Pennoid, I know it is frustrating did you try this?

sudo rmmod r8192se_pci && sleep 2 && sudo modprobe r8192se_pci

It worked for me for a while but then after an update it stopped working, if I execute those commands it freezes everything and I have to restart. Try it and see what happens.

---

### Post by aman_cc on 2011-04-09
I face the exact problem. Same driver and Ubuntu 10.10

I tried replacing network-manager with wicd - but that doesn't work

I have noticed that whenever you try to access update manager in Ubuntu - problem comes faster on more often !!!

I got this link somewhere, maybe it helps you guys as well

[http://askubuntu.com/questions/26395/wireless-keeps-disabling-or-stays-disconnected-realtek-rtl8191sevb](http://askubuntu.com/questions/26395/wireless-keeps-disabling-or-stays-disconnected-realtek-rtl8191sevb)

I haven't tried it yet myself

---

### Post by juliobahar on 2011-12-04
I found a fix and it seems working great on my Lenovo ThinkPad X100e, with RTL8191SEvB wireless lan controller. I'm running the laptop for more than two hours now on ubuntu 11.10 64-bit on both unity and gnome shell. Here we go:

1-Download and extract the RealTek driver from [here]("http://218.210.127.131/downloads/downloadsView.aspx?Langid=1&PFid=48&Level=5&Conn=4&ProdID=230&DownTypeID=3&GetDown=false&Downloads=true#2262"), choose any of the download sites under the first section namely "Linux driver for kernel 2.6.24 (and later)". This driver is supposedly meant for RTL8188CE/RTL8192CE, RTL8191SE/RTL8192SE, and RTL8192DE

2-Follow the instructions in the README file inside the .tar.gz file, type in terminal the following: 
```

$cd [EXTRACTED_FOLDER]
$sudo make
$sudo make install

```
3- Reboot and you should be fine.

I noticed compiling this driver against your kernel is makes the wifi connection more stable - it never dropped so far, and the download speed is somewhat faster.

Edit 30-12-2011: I found this [link]("http://michael-peeters.blogspot.com/2011/10/fixing-rtl8191se-wifi-under-ubuntu-1110.html") useful

---

### Post by Parksy on 2012-01-10
Wow!  I downloaded and installed the new driver today; worked great all day!  Still drops the odd time but no problem reconnecting.  Before it would sometimes go half an hour without being able to connect to any websites.

---

### Post by aryangor on 2012-05-05
> **juliobahar said:**
> I found a fix and it seems working great on my Lenovo ThinkPad X100e, with RTL8191SEvB wireless lan controller. I'm running the laptop for more than two hours now on ubuntu 11.10 64-bit on both unity and gnome shell. Here we go:

1-Download and extract the RealTek driver from [here]("http://218.210.127.131/downloads/downloadsView.aspx?Langid=1&PFid=48&Level=5&Conn=4&ProdID=230&DownTypeID=3&GetDown=false&Downloads=true#2262"), choose any of the download sites under the first section namely "Linux driver for kernel 2.6.24 (and later)". This driver is supposedly meant for RTL8188CE/RTL8192CE, RTL8191SE/RTL8192SE, and RTL8192DE

2-Follow the instructions in the README file inside the .tar.gz file, type in terminal the following: 
```

$cd [EXTRACTED_FOLDER]
$sudo make
$sudo make install

```
3- Reboot and you should be fine.

I noticed compiling this driver against your kernel is makes the wifi connection more stable - it never dropped so far, and the download speed is somewhat faster.

Edit 30-12-2011: I found this [link]("http://michael-peeters.blogspot.com/2011/10/fixing-rtl8191se-wifi-under-ubuntu-1110.html") useful

Thanks it worked for me!!! :guitar:

---

### Post by hantms on 2012-10-18
Note that compiling didn't work for me.  Got an error: 

base.c:319:6: error: ‘IEEE80211_HW_BEACON_FILTER’ undeclared (first use in this function)  

I went into the base.c file and just commented out that line (319) and after that it did compile.

No clue if this causes problems, but it's worth the risk; network dying all the time is no fun.

---

