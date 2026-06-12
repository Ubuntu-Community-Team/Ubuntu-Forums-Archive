---
title: "Wireless problem on Ubuntu 8.04 Server Edition"
date: 2009-02-10
forum: Networking &amp; Wireless
---

### Post by New-in-linux on 2009-02-10
Hi, 
I dual booted my Pc (Wich has Windows Vista on it) with Ubuntu 8.04 Server Edition for learning & stuff, but I can't connect to my home network. When it was installing, it couldn't get the network info itself, So I configured in myself, but when the server was running, there was no connection to internet. I have an Sitecom WL-172 Network stick. I am out of solutions alot of commands from the Sticky: Supported wireless cards list and procedure to get help, didn't gave me much information. 

I tested Ubuntu on VMware before dual booting, but because I used NAT, wireless connection was no problem.

I am new to linux so sorry if I am missing some crucial things.
Thanks for the help anyway!

---

### Post by superprash2003 on 2009-02-10
type iwconfig in the terminal. does it support scanning for any of the interfaces?? if not type **lshw -C network** to see which driver is required

---

### Post by New-in-linux on 2009-02-10
> **superprash2003 said:**
> type iwconfig in the terminal. does it support scanning for any of the interfaces?? if not type **lshw -C network** to see which driver is required
I tried Iwconfig, and it gave me only Wlan0: 
 
Wlan0 : IEEE 802.11g ESSID:""
        Mode: Managed Channel: 0
        Access Point: Not-Associated
        Tx-power = 0 dBm
        Retry limit: 7
        RTS Thr: Off
        Fragment thr: 2346 B 
        Link Quality: 0 
        Signal Level: 0
        Noise Level: 0
        Rx Invalid nwid: 0 
        Rx Invalid Crypt: 0 
        Rx Invalid Frag: 0 
        Tx Excessive retries: 0 
        Invalid misc: 0
        Missed Beacon: 0 

I tried lshw -C network, And there was something I noticed; It said Network DISABLED.

---

### Post by superprash2003 on 2009-02-11
it should show you a name like broadcom or realtek or atheros.. what output does **iwlist scanning **give

---

### Post by New-in-linux on 2009-02-11
Here are the results: 

lo      Interface doesn't support scanning
eth0    Interface doesn't support scanning
wmaster Interface doesn't support scanning
wlan    No scan results

I've looking for wich driver it needs, but I couldn't find it.

---

### Post by superprash2003 on 2009-02-12
hmmmm.. wlan0 says no scan results.. are you sure you have wifi networks around?

---

### Post by New-in-linux on 2009-02-12
Yes, Because I run Windows with a good connection. But I maybe have a possible solution. I went looking for proper drivers and stuff and found a Linux driver for my wireless network stick on Ralink, but can I run the setup from my usb stick in ubuntu ? and if yes, how? Since I am total new to linux commands.

---

