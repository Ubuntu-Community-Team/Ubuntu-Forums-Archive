---
title: "connecting to wireless networks"
date: 2010-10-18
forum: Networking &amp; Wireless
---

### Post by RasterBurn on 2010-10-18
hey im not sure about this, but is there a way i can setup my computer so i can connect to my wireless network without the use of an admin password? i personally feel that it wouldn't be a security risk of any sort to not require a password to connect to an ecrypted wireless connection, it kinda irritates me first thing in the morning so if anyone could help me with this, that would be great thanks :)

---

### Post by SteveDee on 2010-10-18
You computer should connect automatically to your wireless access point if it is correctly setup. Can you describe what happens when you start up?

---

### Post by Setzdich on 2010-10-18
While the subject has been raised, I'm having difficulty in making any connection at all, whilst on an earlier version of Ubuntu there was no problem whatever.

I've entered a password into wireless networking, have selected 'Infrastructure' - as I always did in a former OS, using the same point of presence - and have entered the SSID and password.

It's WPA so I selected the option with WPA in it (I know about the new exploit and have ordered a replacement). Also wireless networking is marked for auto connect.

I've left it on Automatic/DHCP.

When I click on the networking applet I notice that my network name is greyed out, and although the system frequently informs me that I am connected but cannot connect to the net.

I'd appreciate some advice as I'm beginning to feel a bit goddamn tetchy. The problem seems to have originated with Ubuntu 10.10. An Ubuntu 10.4 USB stick won't boot up, so installing it is not an option, even though it worked on the previous notebook.

---

### Post by SteveDee on 2010-10-18
> **Setzdich said:**
> While the subject has been raised, I'm having difficulty in making any connection at all....


In a terminal type:-

```

iwconfig

```

...and post the output.

Then type:-
```

sudo iwlist scanning

```
...and post this output.

---

### Post by Setzdich on 2010-10-18
Thanks for the response. OK, please remember that I can't screen dump because I'm typing what's on another screen. The iwconfig comand returns (adding a hyphen to cut out the smileys following the "thr" string didn't get rid of them, so I hope you can tolerate them):

lo no wireless extensions

eth0 no wireless extensions

wlan0      Ralink STA ESSID:"" Nickname:"RT2870STA"
           Mode:Auto Frequency=2.412 GHz Access Point: Not-Associated
           Bit Rate:1Mb/s
           RTS thr:off  Fragment thr:off
(Or:            RTS thr off  Fragment thr off
with the colon removed)

           Link Quality=10/100 Signal level:0dBm Noise level:-115 dBm
           Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
           Tx excessive retries:0 Invalid misc:0 Missed beacon:0

following the sudo command (I've always wanted good reason to type one!) I get this:

l0 Interface doesn't support scanning

eth0 Interface doesn't support scanning

wlan0 No scan results

My response to the latter stuff is that I need to install some drivers. ?

Again, thank you for the response.

---

### Post by RasterBurn on 2010-10-18
ok so when i go to connect to my wireless it askes me to unlock the keyring the application is called "/usr/bin/nm-applet" its the network manager applet

like i said in my initial post, i dont see a reason to have to unlock the keyring in order to connect to my wireless though if i deny access to the keyring it will ask for the WPA / WPA2 password for the connection and then ask to unlock the keyring again, if i deny it the second time i will still connect so how do i set it to not require the keyring to be unlocked?

---

### Post by SteveDee on 2010-10-19
> **Setzdich said:**
> 

wlan0 No scan results

My response to the latter stuff is that I need to install some drivers.....

...yep, not much happening there, so type:-
```

lspci

```

...and post (as best you can) the Network Controller info.

---

### Post by SteveDee on 2010-10-19
> **RasterBurn said:**
> ok so when i go to connect to my wireless it askes me to unlock the keyring...

You may have already done this, but first try this with wifi enabled:-
 - Right click on wireless icon in panel and select Edit Connections...
 - Select Wireless tab
 - Select Edit... for you connection (password required)
 - Check/enable "Connect Automatically" and "Available To All Users"

---

### Post by RasterBurn on 2010-10-19
thank you SteveDee, I didnt see the "Available to all users" check box on the bottom, I think that has sorted things out, i will find out when i boot up the computer next, but for now, i will un-hook my wired connection, if all goes well that will free up 1 port on my router for another machine :)

---

### Post by Setzdich on 2010-10-19
Ooh, that was interesting. I pasted it into an editor, saved it and transferred the file to this machine:

00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

Perhaps this is wrong, I see no sign of the Wi-Fi hardware.

---

### Post by SteveDee on 2010-10-19
> **Setzdich said:**
> 
...Perhaps this is wrong, I see no sign of the Wi-Fi hardware.

Nor do I. Are you using a USB wifi stick?

Try:-
```

lsusb

```

This will probably show your device as a RT2870STA since this is the nickname returned by iwconfig.

If so I suggest your next move is to do a search for "RT2870STA" in these forums.

There is a heavy thread here: [http://ubuntuforums.org/showthread.php?t=960642&highlight=RT2870STA](http://ubuntuforums.org/showthread.php?t=960642&highlight=RT2870STA) ...that's been running for 2 years!

---

### Post by Setzdich on 2010-10-19
Hello again. Not I've been cheating a bit, not only grepping the web but also installed Hardinfo. What's this

Intel Corporation 82801 Mobile PCI Bridge (rev e2)

It's not a USB device, probably an integrated one though.

This is the machine itself, bought for working on the road:

[http://preview.tinyurl.com/yc6y9wd](http://preview.tinyurl.com/yc6y9wd)

---

### Post by Setzdich on 2010-10-19
> **SteveDee said:**
> Nor do I. Are you using a USB wifi stick?

Try:-
```

lsusb

```

This will probably show your device as a RT2870STA since this is the nickname returned by iwconfig.

If so I suggest your next move is to do a search for "RT2870STA" in these forums.

There is a heavy thread here: [http://ubuntuforums.org/showthread.php?t=960642&highlight=RT2870STA](http://ubuntuforums.org/showthread.php?t=960642&highlight=RT2870STA) ...that's been running for 2 years!

Whoa! I have just noticed and applied the USB interrogation, and it returned more than just that which you mentioned:

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 148f:3070 Ralink Technology, Corp. RT2870/RT3070 Wireless Adapter
Bus 001 Device 002: ID 0ac8:3343 Z-Star Microelectronics Corp. Sirius USB 2.0 Camera
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

So the RT2870 bit is bang on, but I see RT3070 also, and I have found a clue here: [http://wiki.debian.org/rt2870sta](http://wiki.debian.org/rt2870sta)

Do you think this is what I need?

I realise I face the problem of knowing how to install a driver in Linux. I don't.

---

### Post by SteveDee on 2010-10-19
> **Setzdich said:**
> 
Do you think this is what I need?.

I think you would be better advised to look at the link/thread I mentioned above. From page 22 onward it starts to apply to 10.10 and a similar kernel to yours.
Maybe post you question in that thread.


Sorry Page 21...

---

### Post by Setzdich on 2010-10-19
> **SteveDee said:**
> I think you would be better advised to look at the link/thread I mentioned above. From page 22 onward it starts to apply to 10.10 and a similar kernel to yours.
Maybe post you question in that thread.


Sorry Page 21...

Thank you for your help and advice which are gratefully received.

I'll be on it tomorrow. For the while I'm sick of the sound of so many PSUs, HDs and fans kicking up a din, to say nothing of the heat.

---

### Post by RasterBurn on 2010-10-20
Ok so the settings you mentioned SteveDee worked like a charm, and worked great for a day, unfortunately today it has encountered a new problem, it seems the password for WPA2 is not being accepted...

I open up nm-applet window to edit the wireless settings only to find that the password for connecting is no longer set, and i can go in and set the password over and over again and it doesnt seem to remember the password at all

---

### Post by SteveDee on 2010-10-21
> **RasterBurn said:**
> Ok so the settings you mentioned SteveDee worked like a charm, and worked great for a day, unfortunately today it has encountered a new problem, it seems the password for WPA2 is not being accepted...

I open up nm-applet window to edit the wireless settings only to find that the password for connecting is no longer set, and i can go in and set the password over and over again and it doesnt seem to remember the password at all

OK, use the 2 commands in post #4 of this thread, and post the output.

---

### Post by RasterBurn on 2010-10-21
ok so i have run the command, there are about a dozen wireless signals that my computer picks up on a regular basis including my own (all of them are locked down with encryption)

iwconfig:

```

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  Mode:Managed  Frequency:2.412 GHz  
          Access Point: Not-Associated   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vboxnet0  no wireless extensions.

``````

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 07 - Address: 00:24:01:42:F9:9C
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=59/70  Signal level=-51 dBm  
                    Encryption key:on
                    ESSID:"Michael's Wireless"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000008d880fd180
                    Extra: Last beacon: 830ms ago
                    IE: Unknown: 00124D69636861656C277320576972656C657373
                    IE: Unknown: 010882848B968C129824
                    IE: Unknown: 030101
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 200100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 3204B048606C
                    IE: Unknown: DD180050F2020101030003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401051900000000000000000000000000000000000000
                    IE: Unknown: 3D1601051900000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD7B0050F204104A00011010440001021041000100103B00010310470010565AA94967C14C0EAA8FF349E6F5931110210006442D4C696E6B1023000D442D4C696E6B20526F75746572102400074449522D363135104200046E6F6E651054000800060050F204000110110006442D4C696E6B100800020084103C000101

vboxnet0  Interface doesn't support scanning.


```i have filtered the rest of the signals that have been detected for simplicity

---

### Post by SteveDee on 2010-10-21
RasterBurn, your iwlist output probably confirms what you already know. Your issue seems to be security related.
I have a system running a clean install of Lubuntu 10.10 which boots straight into my account with wifi running, so I haven't seen problems like this on pure Lubuntu.

A few weeks ago I put together a minimal install (Ubuntu Minimal ISO) of 10.04 and then tried to add LXDE. I couldn't connect to my access point so had to install wpa_supplicant and configure it, which fixed the problem. If you have a keyring problem, this will probably work for you also.

So I guess you have (at least) 3 options:-
1) Try to back-track by un-doing recent changes (as it did appear to work for a while)
2) Install/configure wpa_supplicant like this: [http://undiff.com/2008/08/wireless-with-wpa_supplicant-easier-then-you-think/](http://undiff.com/2008/08/wireless-with-wpa_supplicant-easier-then-you-think/)
3) Upgrade to 10.10

I'm sorry I can't be more helpful.

---

