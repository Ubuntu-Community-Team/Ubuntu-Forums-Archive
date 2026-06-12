---
title: "Lenovo P500 poor/unreliable wifi signal NO connection hard wired"
date: 2012-12-11
forum: Networking &amp; Wireless
---

### Post by xinemae on 2012-12-11
I apologize ahead of time, I am SO new to Ubuntu that I am only just learning how to navigate the system.

Here's my issue. This machine came with windows 8. I wasn't happy with that OS so at the suggestion of friends we installed Ubuntu 12.04. I thought the wireless issue was caused my the windows 8 program and thus, thought it would be solved by removed said OS and installing ubuntu.

It didn't fix the problem. Lenovo cannot help much, I knew more about Ubuntu than the service guy on the phone. He told me the problem was most likely driver related. 

Here's where I may embarrass myself, but I guess we all have to start somewhere... He wanted me to try and locate d: ... I couldn't. I did think it was wiped out when we installed this OS. He also wanted me to find the device manager so we could trouble shoot the lan drivers. I wasn't able to find those anywhere.

Wired connection does not work, the wireless fluctuates between slow, really slow and not there. Any suggestions?

Thanks in advance!
Cecilia

---

### Post by memilanuk on 2012-12-11
Did you do a complete wipe and install Ubuntu only, or did you set up for dual boot so you could go back to Windows 8 in the event Linux didn't suit you?

Did you make a system recovery CD / DVD set from Windows before you started messing with the operating system and boot loader?

---

### Post by xinemae on 2012-12-11
> **memilanuk said:**
> Did you do a complete wipe and install Ubuntu only, or did you set up for dual boot so you could go back to Windows 8 in the event Linux didn't suit you?

Did you make a system recovery CD / DVD set from Windows before you started messing with the operating system and boot loader?

Dual booting isn't possible with Windows 8 home edition, so yes, it was wiped clean. No I do not believe he made a recovery set from windows before doing so. I won't ever be going back to windows lol so I think that sorta dictated his actions.

---

### Post by memilanuk on 2012-12-11
> **xinemae said:**
> Dual booting isn't possible with Windows 8 home edition, so yes, it was wiped clean. 

Interesting... given that a search on Google for 'linux windows 8 dual boot' returns oodles of pages detailing exactly that.

> No I do not believe he made a recovery set from windows before doing so.  I won't ever be going back to windows lol so I think that sorta dictated his actions.

So you didn't make a recovery set first and you obviously didn't try it out with a Live CD to see if you had any potential hardware issues, and its not even your machine that you were gambling with.

Beautiful.

Lenovo has support forums, including one specifically for Linux.  Maybe they can help you.

---

### Post by chili555 on 2012-12-11
I'll be glad to help you. First, let's find out what wireless and ethernet devices you have. Please open a terminal and run and post:```
lspci -nn | grep -e 0200 -e 0280
```The pipe symbol | is on the right side of my US keyboard on the same key with \.

I have two Lenovos running 12.10 perfectly, so I'm fairly confident we can get you going.

---

### Post by xinemae on 2012-12-11
> **memilanuk said:**
> Interesting... given that a search on Google for 'linux windows 8 dual boot' returns oodles of pages detailing exactly that.
I'm not entirely sure what I did to make you take such a negative turn. If my wording was the cause, then understand that wasn't the intent. I fully admitted to being new to this, and your response presents itself with gobs of ridicule. I came for help, not chastisement, no matter how thinly veiled. 

I did try dual booting and when we encountered errors our searches turned up that you couldn't dual boot with windows 8 edition because one is not allow access to change group permissions or something of that sort and UEFI issues. We were even told by Lenovo support that dual booting windows 8 home edition wasn't possible. 


> **memilanuk said:**
> So you didn't make a recovery set first and you obviously didn't try it out with a Live CD to see if you had any potential hardware issues, and its not even your machine that you were gambling with.

Beautiful.

Lenovo has support forums, including one specifically for Linux.  Maybe they can help you.

If my issue happens with Windows 8 and Ubuntu, my initial thought WAS hardware problems, but I was told it was probably a driver issue.  It IS my machine... just purchased.

So, tell me please, how is a newbie, such as myself supposed to differentiate? This is frustrating enough without the negativity.

---

### Post by xinemae on 2012-12-11
> **chili555 said:**
> I'll be glad to help you. First, let's find out what wireless and ethernet devices you have. Please open a terminal and run and post:```
lspci -nn | grep -e 0200 -e 0280
```The pipe symbol | is on the right side of my US keyboard on the same key with \.

I have two Lenovos running 12.10 perfectly, so I'm fairly confident we can get you going.

Thank you for your help, I will run and post ;)

---

### Post by xinemae on 2012-12-11
(standard input):01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
grep: 0280: No such file or directory

---

### Post by xinemae on 2012-12-11
(standard input):01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
grep: 0280: No such file or directory

---

### Post by verzx on 2012-12-11
Have you actually tried with updating the drivers in ubuntu, find out what the name of your Wireless adapter is and install the ubuntu supported drivers on the website.

---

### Post by xinemae on 2012-12-11
> **verzx said:**
> Have you actually tried with updating the drivers in ubuntu, find out what the name of your Wireless adapter is and install the ubuntu supported drivers on the website.

Verzx, I didn't know how to find the name of my wireless adapter, but yea that's what I thought I needed to do. I just didn't know how to figure out what I had... I googled for help and was sent to these forms... so I thought I'd ask for help here.

---

### Post by chili555 on 2012-12-11
> **xinemae said:**
> (standard input):01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
grep: 0280: No such file or directory
Please try:```
lspci -nn | grep 0280
```

EDIT: Your ethernet ought to work with the driver r8169. Please hook up the ethernet and post:```
sudo modprobe r8169
nm-tool
dmesg | grep r8169
```

---

### Post by xinemae on 2012-12-11
> **chili555 said:**
> Please try:```
lspci -nn | grep 0280
```

EDIT: Your ethernet ought to work with the driver r8169. Please hook up the ethernet and post:```
sudo modprobe r8169
nm-tool
dmesg | grep r8169
```

Thanks! will try and then post results. Sorry for the delay! I greatly appreciate the help.

---

### Post by xinemae on 2012-12-11
cecilia@cecilia-Lenovo-IdeaPad-P500:~$ sudo modprobe r8169
cecilia@cecilia-Lenovo-IdeaPad-P500:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: wlan0  [Rogers] ------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           yes
  HW Address:        84:A6:C8:A6:28:C7

  Capabilities:
    Speed:           19 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *Rogers:         Infra, 68:7F:74:04:14:B2, Freq 2437 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2
    baragon:         Infra, B2:B2:DC:19:6C:50, Freq 2462 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2

  IPv4 Settings:
    Address:         192.168.1.101
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             74.211.89.200
    DNS:             74.211.89.201
    DNS:             208.67.222.222

  IPv6 Settings:
    Address:         2002:ae32:426a:0:405d:2671:7f1a:c790
    Prefix:          64
    Gateway:         fe80::6a7f:74ff:fe04:14b0

    Address:         2002:ae32:426a:0:59a:207f:201f:2d8c
    Prefix:          64
    Gateway:         fe80::6a7f:74ff:fe04:14b0

    Address:         2002:ae32:426a:0:c582:9aec:40eb:4481
    Prefix:          64
    Gateway:         fe80::6a7f:74ff:fe04:14b0

    Address:         2002:ae32:426a:0:c1c6:9efa:f8c8:4836
    Prefix:          64
    Gateway:         fe80::6a7f:74ff:fe04:14b0

    Address:         2002:ae32:426a:0:4931:2dec:b032:cbbf
    Prefix:          64
    Gateway:         fe80::6a7f:74ff:fe04:14b0

    Address:         2002:ae32:426a:0:25c3:800f:e50d:edf5
    Prefix:          64
    Gateway:         fe80::6a7f:74ff:fe04:14b0

    Address:         2002:ae32:426a:0:86a6:c8ff:fea6:28c7
    Prefix:          64
    Gateway:         fe80::6a7f:74ff:fe04:14b0

    Address:         fe80::86a6:c8ff:fea6:28c7
    Prefix:          64
    Gateway:         fe80::6a7f:74ff:fe04:14b0



- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        B8:88:E3:8F:50:28

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


cecilia@cecilia-Lenovo-IdeaPad-P500:~$ dmesg | grep r8169
[    4.946262] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    4.946281] r8169 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.946311] r8169 0000:01:00.0: setting latency timer to 64
[    4.946379] r8169 0000:01:00.0: irq 42 for MSI/MSI-X
[    4.946734] r8169 0000:01:00.0: eth0: RTL8105e at 0xf841a000, b8:88:e3:8f:50:28, XID 00c00000 IRQ 42
[   23.534040] r8169 0000:01:00.0: eth0: link down

---

### Post by chili555 on 2012-12-11
We see your wireless is connected here:> *Rogers: Infra, 68:7F:74:04:14:B2, Freq 2437 MHz, Rate 54 Mb/s, [COLOR="Red"]Strength 39[/COLOR] WPA WPA2Is the router nearby? Is there anything you can do to affect the strength? Let's try a temporary driver parameter to see if it helps:```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi 11n_disable=1
```If it works, we can write one file and make it persistent.> [ [COLOR="Red"]4.946262[/COLOR]] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[ 4.946281] r8169 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 4.946311] r8169 0000:01:00.0: setting latency timer to 64
[ 4.946379] r8169 0000:01:00.0: irq 42 for MSI/MSI-XWe  can see by the timestamp that the ethernet driver loads during boot but seems to go nowhere. I am interested in this:> Wired Properties
[COLOR="Red"]Carrier: off[/COLOR]
Is a known good ethernet cable attached at boot-up? Do the LEDs on the router flicker indicating activity? Other than the carrier, we see nothing remarkable so far.

Please check private messages.

---

### Post by xinemae on 2012-12-11
> **chili555 said:**
> We see your wireless is connected here:Is the router nearby? Is there anything you can do to affect the strength? Let's try a temporary driver parameter to see if it helps:```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi 11n_disable=1
```If it works, we can write one file and make it persistent.

with that bit of code there my wireless was disabled and then re-enabled... was that the goal? :D There are 4 other devices connected wirelessly to this router and have pretty good connections. 

oh... the router is about 6 feet in front of where I sit with this machine.

---

### Post by chili555 on 2012-12-12
> my wireless was disabled and then re-enabled... was that the goal? Exactly so. The hope was that it would be enabled with more stability.

This is a bit troublesome:> IPv6 Settings:
Address: 2002:ae32:426a:0:405d:2671:7f1a:c790
Prefix: 64
Gateway: fe80::6a7f:74ff:fe04:14b0

Address: 2002:ae32:426a:0:59a:207f:201f:2d8c
Prefix: 64
Gateway: fe80::6a7f:74ff:fe04:14b0

Address: 2002:ae32:426a:0:c582:9aec:40eb:4481
Prefix: 64
Gateway: fe80::6a7f:74ff:fe04:14b0

Address: 2002:ae32:426a:0:c1c6:9efa:f8c8:4836
Prefix: 64
Gateway: fe80::6a7f:74ff:fe04:14b0

Address: 2002:ae32:426a:0:4931:2dec:b032:cbbf
Prefix: 64
Gateway: fe80::6a7f:74ff:fe04:14b0

Address: 2002:ae32:426a:0:25c3:800f:e50d:edf5
Prefix: 64
Gateway: fe80::6a7f:74ff:fe04:14b0

Address: 2002:ae32:426a:0:86a6:c8ff:fea6:28c7
Prefix: 64
Gateway: fe80::6a7f:74ff:fe04:14b0

Address: fe80::86a6:c8ff:fea6:28c7
Prefix: 64
Gateway: fe80::6a7f:74ff:fe04:14b0Let's ask Network Manager to ignore IPv6 and see if it helps. Please right-click the Network Manager icon, select Edit Connections, edit Wireless, select the IPv6 tab and set it to Ignore. Please see attached.

Also, since you probably rebooted since your last post, repeat:```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi 11n_disable=1
```Now is it more stable? If not, also try:```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi 11n_disable=1 bt_coex_active=N
```When we find the setting or settings that help your connection remain stable, we'll write a configuration file to make it persistent.

If it is still needed, we'll attack the ethernet after the wireless is returned to health.

---

### Post by xinemae on 2012-12-12
> **chili555 said:**
> Exactly so. The hope was that it would be enabled with more stability.

Let's ask Network Manager to ignore IPv6 and see if it helps. Please right-click the Network Manager icon, select Edit Connections, edit Wireless, select the IPv6 tab and set it to Ignore.

Okie dokie, done. 

> **chili555 said:**
> Also, since you probably rebooted since your last post, repeat:```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi 11n_disable=1
```

I haven't rebooted since last night lol fell asleep early.

> **chili555 said:**
> 
Now is it more stable? If not, also try:
```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi 11n_disable=1 bt_coex_active=N
```

When we find the setting or settings that help your connection remain stable, we'll write a configuration file to make it persistent.

If it is still needed, we'll attack the ethernet after the wireless is returned to health.

Not sure if it's more stable. Should I run the following to check the strength?
```
sudo modprobe r8169
nm-tool
dmesg | grep r8169
```

---

### Post by chili555 on 2012-12-12
> **xinemae said:**
> Not sure if it's more stable. Should I run the following to check the strength?
Just these:```
nm-tool
ping -c3 www.google.com
```

---

### Post by xinemae on 2012-12-12
cecilia@cecilia-Lenovo-IdeaPad-P500:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: wlan0  [Rogers] ------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           yes
  HW Address:        84:A6:C8:A6:28:C7

  Capabilities:
    Speed:           24 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *Rogers:         Infra, 68:7F:74:04:14:B2, Freq 2437 MHz, Rate 54 Mb/s, Strength 45 WPA WPA2
    baragon:         Infra, B2:B2:DC:19:6C:50, Freq 2462 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2

  IPv4 Settings:
    Address:         192.168.1.101
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             74.211.89.200
    DNS:             74.211.89.201
    DNS:             208.67.222.222

  IPv6 Settings:
    Address:         2002:ae32:426a:0:15ca:f7e5:bf18:7c33
    Prefix:          64
    Gateway:         fe80::6a7f:74ff:fe04:14b0

    Address:         2002:ae32:426a:0:51f5:822f:b74b:81f8
    Prefix:          64
    Gateway:         fe80::6a7f:74ff:fe04:14b0

    Address:         2002:ae32:426a:0:4d20:5968:731c:f073
    Prefix:          64
    Gateway:         fe80::6a7f:74ff:fe04:14b0

    Address:         2002:ae32:426a:0:a1f5:cf14:46c6:5156
    Prefix:          64
    Gateway:         fe80::6a7f:74ff:fe04:14b0

    Address:         2002:ae32:426a:0:86a6:c8ff:fea6:28c7
    Prefix:          64
    Gateway:         fe80::6a7f:74ff:fe04:14b0

    Address:         fe80::86a6:c8ff:fea6:28c7
    Prefix:          64
    Gateway:         fe80::6a7f:74ff:fe04:14b0



- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        B8:88:E3:8F:50:28

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


cecilia@cecilia-Lenovo-IdeaPad-P500:~$ ping -c3 [www.google.com](www.google.com)
PING [www.google.com](www.google.com) (74.125.225.208) 56(84) bytes of data.
64 bytes from den03s06-in-f16.1e100.net (74.125.225.208): icmp_req=1 ttl=53 time=40.8 ms
64 bytes from den03s06-in-f16.1e100.net (74.125.225.208): icmp_req=2 ttl=53 time=41.4 ms
64 bytes from den03s06-in-f16.1e100.net (74.125.225.208): icmp_req=3 ttl=53 time=42.5 ms

--- [www.google.com](www.google.com) ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 40.897/41.642/42.556/0.726 ms

---

### Post by chili555 on 2012-12-12
Your ping times look pretty solid! I am still mystified by the IPv6 information. Let's try some fixes. Please open a terminal and do:```
sudo gedit /etc/sysctl.conf
```Add these lines at the end:```
# IPv6
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1

```After proofreading carefully, save and close gedit. Now do:```
sudo sysctl -p
sudo gedit /etc/modprobe.d/iwlwifi.conf
```Add the following to the new empty file that opens:```
options iwlwifi 11n_disable=1 bt_coex_active=N
```After proofreading carefully, save and close gedit. Now reboot and let us hear your report. Is the wireless stable now?

Is ethernet a priority? Fixing it will be an even bigger task, but we can certainly do so if it's needed. Having a working wireless will make it all a lot more convenient.

---

### Post by xinemae on 2012-12-12
Seems like things are better... it was such a random thing. It is definitely faster than it has ever been, with Windows 8 or Ubuntu. So far, it isn't completely halting, which has me holding my breath LOL

I'm fine with a working wireless, I haven't been "plugged" in with a cable in so long LOL


Thanks so much for your help, you are beyond awesome!

---

### Post by chili555 on 2012-12-12
Please continue to monitor it and post back if we can help you further. Fingers crossed.

Thank you for your kind comments.

---

### Post by xinemae on 2013-09-20
Sooo.... an update.

I was still having issues with the signal strength. If I moved to my dining room, no walls in between the computer and my router I'd lose all connection. After researching for months, I finally found the solution to be a hardware issue... despite Lenovo's statements that it isn't. The network card was wired BACKWARDS! Switched the two wires, even though they appeared to be correct. What's the worse that could happen? I'd lose the little connectivity that I had? LOL Nope... FULL strength signal... I can walk down my driveway with my computer and it doesn't lose connection now. Took me almost 10 months, but finally found the true reason. 

I wanted to put in an update, just in case others were having the same issues. Thanks for ALL the help here, y'all are fantastic :)

Cecilia

---

### Post by chili555 on 2013-09-20
I am very glad it's working. I hope you have brought this to Lenovo's attention. It is, in my opinion, inexcusable.

---

