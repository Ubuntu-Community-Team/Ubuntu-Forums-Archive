---
title: "IBM ThinkPad T60 Ubuntu 10.4 LTS Wireless Connections Problem (Tried All)"
date: 2011-01-12
forum: Networking &amp; Wireless
---

### Post by luminati on 2011-01-12
Good Day,
 
I recently installed ubuntu 10.4 LTS on my IBM T60 ThinkPad, (Love Ubuntu! Will Never go back to Windows)
 
But now the problem is as followed.:
 
When i'm at work where they have an open (Non protected) WiFi spot i have no problems connecting at all.
But as soon as i'm at home or with friends which have WEP/WPA/WPA2 encrypted routers it is impossible to connect, to none of them. not Linksys, not Dlink not Thomsom, simply none...
 
For days i've been hunting the internet for information about this problem but it is impossible for me to find the solution.
 
I've read the Wireless troubleshooting manual from Ubuntu and did all the checks and tests and everything seems fine.
 
The card is an Intel 3945ABG, and in the new Linux Kernels its already pre-installed.
 
Can someone please help me...!!!  It's so frustrating not beeing able to use the internet in a proper way.. :(
 
Note:
 
I installed wireshark to experiment at my workplace but its finding nothing at all even though its connected to the internet/LAN
Etherape works fine though.

---

### Post by chili555 on 2011-01-12
As it happens, I am answering this post on my T60 which uses an Intel 3945ABG. Are you using Network Manager? Is your home router set for WPA or WPA2 or the difficult WPA *and* WPA2 mixed mode? The title of your post says "Tried All." What all have you tried? From your home, please run and post:```
sudo iwlist wlan0 scan
```

---

### Post by Chasmo on 2011-01-12
I have a similar problem. I just set up a linksys e1000 and in the setup it is set to the wep wep2 mixed mode. when I try to connect using wicd it says I have a bad password. Any ideas on that one.

---

### Post by chili555 on 2011-01-12
> in the setup it is set to the wep wep2 mixed modeMay I assume you mean WPA and WPA2 mixed mode? Please change the configuration in the router to WPA ***or*** WPA2, not both and I believe you will connect easily.

---

### Post by Cloud_704 on 2011-01-12
Same problem (or at least I think it is the same problem) on a Thinkpad R40. Have had it for months, posted on other threads, no replies.

The network manager applet shows some passphrase-protected wireless networks, but they are notoriously "grayed out". Wifi network (not 'hidden') on college campus doesn't show up at all in the applet.

lshw returns: *-network:0 DISABLED
                description: Wireless interface
                product: Cisco Aironet Wireless 802.11b
                vendor: AIRONET Wireless Communications
                physical id: 2
                bus info: pci@0000:02:02.0
                logical name: eth1

... even when I am connected on an open network at home.

N.B. any solution that involves changing household router is moot to me, because the whole point of picking up the laptop was to use it at school ...

Oh, and ability to connect to wireless networks *is* enabled under user-privileges control panel.

---

### Post by luminati on 2011-01-13
Thank you for your quick reply chili555...

I've tried the following.:

1. Tried all different settings for the router i do have acces to and nothing works,
2. I've read the entire ubuntu wireless troubleshooting guide with no to less result.

I had Ubuntu 10.10 installed but had the same problem, i thought i mite not be a stable one so i installed 10.4 LTS.

I've tried a lot of routers because i travel a lot.

Also i must add the following: I installed Ubuntu 10.4 LTS and everything seemed to work fine so i didn't bother to install any drivers or whatever, this because i thought Ubuntu comes with the drivers build in, if yo have a T60 and running 10.4 did you install any additional drivers?

I typed in the command you asked me to, and the result is below

wlan0     Scan completed :
          Cell 01 - Address: 00:18:E7:D0:75:8C
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=69/70  Signal level=-41 dBm  
                    Encryption key:off
                    ESSID:"Baden Gigant van Breugel"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000a1496dad0e
                    Extra: Last beacon: 16ms ago
                    IE: Unknown: 0018426164656E20476967616E742076616E204272657567656C
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A4E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601051B00000000000000000000000000000000000000
                    IE: Unknown: DD1E00904C336E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401050300000000000000000000000000000000000000

Thanks so far!  :D

---

### Post by chili555 on 2011-01-13
> **Cloud_704 said:**
> Same problem (or at least I think it is the same problem) on a Thinkpad R40. Have had it for months, posted on other threads, no replies.

The network manager applet shows some passphrase-protected wireless networks, but they are notoriously "grayed out". Wifi network (not 'hidden') on college campus doesn't show up at all in the applet.

lshw returns: *-network:0 DISABLED
                description: Wireless interface
                product: Cisco Aironet Wireless 802.11b
                vendor: AIRONET Wireless Communications
                physical id: 2
                bus info: pci@0000:02:02.0
                logical name: eth1

... even when I am connected on an open network at home.

N.B. any solution that involves changing household router is moot to me, because the whole point of picking up the laptop was to use it at school ...

Oh, and ability to connect to wireless networks *is* enabled under user-privileges control panel.Would you please post a new thread and send me a private message with the link? Yours is neither a T60 nor an Inter 3945ABG.

Is your card disabled by either the hardware switch or the Fn keys?

---

### Post by chili555 on 2011-01-13
> Cell 01 - Address: 00:18:E70:75:8C
Channel:1
Frequency:2.412 GHz (Channel 1)
Quality=69/70 Signal level=-41 dBm
Encryption key:off
ESSID:"Baden Gigant van Breugel"Is this a router for which you have control? Notoriously, our drivers, Network Manager and wpa_supplicant have difficulty with ESSIDs with spaces in the name. Is it possible to change the ESSID to something without a space; for example, vanBreugel?

It looks like it's completely open with no WEP, WPA or any other security. Is that the case? Is this one of the networks to which you are unable to connect?

I did not install any other drivers all the way from when I bought the laptop new and installed 8.04, if I remember. For learning purposes, I have, at times, installed linux-backports-modules-compat-wireless (available in Synaptic) which is supposed to have a newer version of the driver iwl3945; however, I have never noticed the slightest difference.

---

### Post by luminati on 2011-01-13
This is a router at my work which i do have acces to.
The problems starts as soon as the routers are protected.
 
The strange thing is, if i am conected to a unprotected Wifi shouldnt WireShark work? because it isnt.
 
I have tried all different brands of routers but to none i could connect allthough the passwords are 100% correct.
 
People use linux for hacking rite? why so much trouble connecting to a router? haha
Also in an earlier stage i had Dual boot  Ubuntu 10.10/Win XP and on XP it did connect without a problem.
Is this maybe a bug in Ubuntu? Are there similar problems with Kubuntu?

---

### Post by luminati on 2011-01-13
Note: The names of the routers at my home are "Linksys" DD-RW (Thomson)
Sentinel (DLINK) 
 
When i take off the password of my DLink router it does connect :confused:
 
The point off course is to connect to any router, and never work with Windows again.'
Í'm learning Linux and Python for 2 weeks now.
 
Thanks so far Chili555..!!!

---

### Post by chili555 on 2011-01-13
> This is a router at my work which i do have acces to.I assume you have no trouble connecting at all. I had asked for a scan result from home which is, I assume WPA protected. You might also post:```
sudo cat /var/log/syslog | grep wlan
```The log will be quite long (or else check syslog.1) but try to capture the 20 or so lines that illustrate the attempt and failure to connect. Make sure any ethernet cable is detached as you run the test.

---

### Post by luminati on 2011-01-13
As soon as i'm at home i will try the different routers and post the log!  :popcorn:

---

### Post by Chasmo on 2011-01-13
Thanks Chilli
I was able to connect but something is still not quite right. I have to reboot to get the wireless icon at the top of my screen. and trying to start it from wicd still won't work. It tells me I have a bad password. I think with some snooping around I will be able to figure it out. Thanks for your help.

---

