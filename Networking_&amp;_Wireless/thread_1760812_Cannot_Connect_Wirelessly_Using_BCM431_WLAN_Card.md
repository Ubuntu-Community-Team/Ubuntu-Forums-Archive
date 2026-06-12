---
title: "Cannot Connect Wirelessly Using BCM431 WLAN Card"
date: 2011-05-17
forum: Networking &amp; Wireless
---

### Post by scrypt on 2011-05-17
Hello

I upgraded Ubuntu to 11.04 I can NO longer connect wirelessly using my BCM4312 WLAN Card. It connected with no problems before dist upgrade using Ubuntu 10.04.
Im really not sure why I cannot connect.
I cannot even see my router in edit wireless connections settings.
I can however see my neighbours routers who are using WPA2 encryption.
But I cannot see my router.

I have uninstalled and reinstalled The Broadcom STA proprietry wireless driver several times using Additional drivers. This did not fix my issue.

I am connected by ethernet at the moment so I do have internet connection.

Can anybody help me to fix the above problems please ?

I look forward to any help and advice

regards

---

### Post by scrypt on 2011-05-18
BUMP

Im still having trouble with this

---

### Post by schauhan on 2011-05-18
The wireless worked on my laptop with 10.04 but did not work after fresh  install of kubuntu 11.04. 

I just fixed same problem following instructions from here. 

[http://adamsteinert.com/blog/?p=332](http://adamsteinert.com/blog/?p=332)

Commands for kubuntu

sudo apt-get install firmware-b43-installer
sudo apt-get install --*reinstall bcmwl-kernel-source* 

That's it. I think drivers need to be installed separately and there is a simple way to do it, though not easy to find.

---

### Post by scrypt on 2011-05-18
Hello

Thank-you for your reply

i had actually already tried the commands you gave me from and earlier fix i found from another ubuntu user had the same issue.

Unfortunately it did not fix my problem.

Here is my iwconfig output:

~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

As you can see I have NO eth0 WLAN for some reason...

here is my ifconfig output:

~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0



here is my output from nm-tool:


~$ nm-tool

NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             connected
  Default:           yes
  HW Address:        00:22:19:DE:C3:E0

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.100
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1


- Device: eth1 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             disconnected
  Default:           no
  HW Address:        00:24:2B:70:48:B4

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    BTOpenzone:      Infra, 02:1D:68:07:88:84, Freq 2442 MHz, Rate 0 Mb/s, Strength 20
    BTHomeHub-1202:  Infra, 00:1D:68:07:88:83, Freq 2442 MHz, Rate 54 Mb/s, Strength 20 WEP
    virginmedia5774681: Infra, C0:3F:0E:BF:70:20, Freq 2422 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    virginmedia3727269: Infra, 30:46:9A:7F:D1:40, Freq 2422 MHz, Rate 54 Mb/s, Strength 80 WPA WPA2


I cannot see my router access point. but I can see my neighbours WLAN access points they use the same ISP as myself.

I really could use some help fixing this. ive been on it for a couple of days now with no luck

---

### Post by mikewhatever on 2011-05-18
Is it at all possible that something is wrong with your router? The fact that your can see the neighbor's APs clearly indicated that the wireless card is working. Make sure your SSID (AP name) doesn't have any odd characters.

I believe the advice above is incorrect:
[s]
sudo apt-get install firmware-b43-installer
sudo apt-get install --reinstall bcmwl-kernel-source 
[/s]

The first command installs the b43 driver, the second one reinstalls the STA one. Result: you end up with two different drivers which isn't workable.

---

