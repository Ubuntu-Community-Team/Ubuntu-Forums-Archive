---
title: "Ubuntu vs Xubuntu/Lubuntu: Wireless works on one but not the others"
date: 2010-05-13
forum: Networking &amp; Wireless
---

### Post by Xendric on 2010-05-13
So, I tried reviving my old windows laptop by installing Ubuntu on it, but it turned out to be too heavy for it, so i turned towards Lubuntu and Xubuntu.

Now, for the couple of days I used Ubuntu, until i decided it's moving too slow and I should go for a lighter version, my USB wireless adapter (and the touchpad, but that's a subject for another subforum) worked fine.
When I installed Lubuntu and Xubuntu, it stopped working. I tried using network-manager and wicd to make my adapter scan for wireless networks, but it's like the USB isn't even there. When I pulled it out and stuck it on my main PC (that is running Ubuntu), it was discovered immediately and connected to my router. But I can't do it on either Xubuntu or Lubuntu.

Please help me.

PS: If anyone has a quick hint about why my touchpad is working during the installation of Xubuntu, but not after it's complete and loads the desktop, please let me know, or I'll make a new post in the relevent section. A USB mouse works fine everywhere, but a touchpad isn't moving the pointer.

---

### Post by Xendric on 2010-05-16
Anyone, please?

---

### Post by cgroza on 2010-05-16
Try installing ubuntu on it and then install lxde or xfce desktop enviroment...

---

### Post by -humanaut- on 2010-05-16
On Xubuntu and Lubuntu a quick sudo apt-get install wicd should solve your wireless problems.

---

### Post by Xendric on 2010-05-17
I tried installing wicd as well as network-manager, but it didnt work.
It's not even detected when I plug it in.

Installing Ubuntu is what I thought about doing as well, but it's my last resort really, because I dont wanna do yet another wipe/install :(

Any other option before I resort to that please?

---

### Post by EdwardR on 2010-05-17
It sounds like you have a wired connection to the internet?  Try this.  With your computer connected to the internet with a wired connections, run Hardware Drivers under Preferences.  If this is the first time you have run it, it should update it's database of available drivers.  Then plug in your wireless device and run Hardware Drivers again.  If it finds a driver, click the button to activate the driver.  Hopefully your wireless will work then.  That's basically the procedure I use to get my PCMCIA wireless card to work on various *buntu installations.

---

### Post by eekrazyk on 2010-06-17
I'm having a similar problem.  I have an old Sony Vaio laptop from about 2001 with a pcmcia RoamAbout 802.11 DS WiFi card.

An Ubuntu live cd detects the wireless card just fine and had no trouble at all.  However, various of the "lighter weight" Ubuntu derivatives (e.g., lubuntu, mint, peppermint) don't appear to detect the pcmcia card at all.

Here's what I've found so far.

```
sudo lshw -C network
*-network
description: RoamAbout 802.11 DS
product: Version 01.01
vendor: Cabletron
physical id: 0
slot: Socket 0[/QUOTE]
```

Here's a snippet of the pertinent parts from Ubuntu live CD:

```
$ lsmod
orinoco_cs  8782  1  orinoco_cs
pcmcia  33024  1  orinoco_cs
pcmcia_core  32964  4  orinoco_cs,pcmcia,yenta_socket,rsrc_nonstatic

```

Now, here's the same from Lubuntu:

```
$ lsmod
pcmcia_core  32964  2  yenta_socket,rsrc_nonstatic
```

Interesting.  What does that mean, exactly?  It appears that it's not even detecting the pcmcia bridge.  Does that sound right?


Does anyone else have any ideas on this?

---

### Post by freddiespagheti on 2010-06-18
I'm having the same issue here. I'm using a pcmcia wireless card on an old laptop and it works fine in Ubuntu. It's been a lot more troublesome on Lubuntu though.

First I had to use a wired connection to manually install pcmcia-utils because the install cd didn't come with it (why that is when the iso is only ~550MB is a mystery to me).

Then after rebooting the card was up and running and could detect networks but would get refused every time I would try and connect.

I tried Wicd but it's not working either. It fails to connect saying 'bad password' but I know that it's correct. 

Anyone else have input?

---

### Post by eekrazyk on 2010-06-19
Good call Freddie.

I installed pcmciautils and my card is detected and up now.  I can scan and see available networks, but I'm still having trouble getting connected to mine.

One note:  I had installed wicd so both NM and wicd were running and I couldn't get the wifi card to start up until I completely removed wicd:

```
$ sudo aptitude remove wicd
$ sudo aptitude purge wicd
```

I also had to change the 'managed' setting to 'true' in /etc/NetworkManager/nm-system-settings.conf to get NM to bring the card up.  However, I think that caused another weird problem. After restarting NM, it tried connecting to my wifi and produced a pop-up asking for the authentication passphrase and had a dropdown menu that was greyed out.  Huh.  When I right-click on the nm-applet to check the settings, I see my original wifi connection and also a new one called "ifupdown (eth1)".  It won't allow me to edit the setting under that one...

```
$ nm-tool

NetworkManager Tool

State: connected

- Device: eth1 --------------------------------------------------      
  Type:              802.11 WiFi
  Driver:            orinoco_cs
  State:             disconnected
  Default:           no
  HW Address:        00:01:F4:ED:B4:1C

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes

  Wireless Access Points 
    linksys:         Infra, 00:0F:66:0B:93:AB, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    Belkin_G_Wireless_BEDCCB: Infra, 00:1C:DF:BE:DC:CB, Freq 2437 MHz, Rate 36 Mb/s, Strength 50 WEP
    BLAH Network:  Infra, 00:1E:2A:71:BF:82, Freq 2412 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2

```

---

### Post by eekrazyk on 2010-06-19
Quick update.  I just read on [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide) that NM can't manage any interfaces listed in /etc/network/interfaces.  I commented out the info I added to that file for eth1 and restarted NM.  I'm no longer seeing that second wifi connection in the nm-applet.

I'm still having trouble getting it to connect to my router, though.

```
$ less /var/log/syslog
...
Jun 19 10:56:58 vaio wpa_supplicant[734]: Trying to associate with 00:0f:66:0b:93:ab (SSID='linksys' freq=2437 MHz)
Jun 19 10:56:58 vaio NetworkManager: <info>  (eth1): supplicant connection state:  scanning -> associating
Jun 19 10:56:58 vaio wpa_supplicant[734]: Association request to the driver failed
Jun 19 10:56:58 vaio kernel: [ 1928.538296] eth1: Lucent/Agere firmware doesn't support manual roaming
Jun 19 10:57:02 vaio NetworkManager: <info>  Activation (eth1/wireless): association took too long.
Jun 19 10:57:02 vaio NetworkManager: <info>  (eth1): device state change: 5 -> 6 (reason 0)
Jun 19 10:57:02 vaio NetworkManager: <info>  Activation (eth1/wireless): asking for new secrets
Jun 19 10:57:02 vaio NetworkManager: <info>  (eth1): supplicant connection state:  associating -> disconnected
Jun 19 10:57:03 vaio wpa_supplicant[734]: Authentication with 00:00:00:00:00:00 timed out.
Jun 19 10:57:08 vaio NetworkManager: <info>  (eth1): device state change: 6 -> 9 (reason 7)
Jun 19 10:57:08 vaio NetworkManager: <info>  Activation (eth1) failed for access point (linksys)
Jun 19 10:57:08 vaio NetworkManager: <info>  Marking connection 'linksys' invalid.
Jun 19 10:57:08 vaio NetworkManager: <info>  Activation (eth1) failed.
Jun 19 10:57:08 vaio NetworkManager: <info>  (eth1): device state change: 9 -> 3 (reason 0)
Jun 19 10:57:08 vaio NetworkManager: <info>  (eth1): deactivating device (reason: 0).

```

```
$ tail /var/log/messages
....
Jun 19 10:56:53 vaio kernel: [ 1923.387474] eth1: Lucent/Agere firmware doesn't support manual roaming
Jun 19 10:56:58 vaio kernel: [ 1928.538296] eth1: Lucent/Agere firmware doesn't support manual roaming

```

I'm seeing other posts out there that indicate this is probably a driver problem.  

```
$ sudo lshw -C network
...
  *-network
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:01:f4:ed:b4:1c
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco driverversion=0.15 **firmware=Lucent/Agere 9.48** link=no multicast=yes wireless=IEEE 802.11b

```

One post suggests needing an older version (6.04), but that the newer version added WPA capability.  Looking into this now.

---

### Post by eekrazyk on 2010-06-19
Another update.  I manually ejected and inserted the card to get dmesg to update:

```
$ sudo pccardctl eject; sudo pccardctl insert
$ dmesg
....
[ 4089.508425] pcmcia 0.0: pcmcia: registering new device pcmcia0.0
[ 4089.589890] orinoco_cs 0.0: Hardware identity 0001:0001:0004:0002
[ 4089.590015] orinoco_cs 0.0: Station identity  001f:0001:0006:0004
[ 4089.590030] orinoco_cs 0.0: Firmware determined as Lucent/Agere 6.04
[ 4089.619811] orinoco_cs 0.0: firmware: requesting agere_sta_fw.bin
[ 4089.760685] orinoco_cs 0.0: Hardware identity 0001:0001:0004:0002
[ 4089.760821] orinoco_cs 0.0: Station identity  001f:0002:0009:0030
[ 4089.760837] orinoco_cs 0.0: Firmware determined as Lucent/Agere 9.48
[ 4089.760848] orinoco_cs 0.0: Ad-hoc demo mode supported
[ 4089.760858] orinoco_cs 0.0: IEEE standard IBSS ad-hoc mode supported
[ 4089.760868] orinoco_cs 0.0: WEP supported, 104-bit key
[ 4089.760877] orinoco_cs 0.0: WPA-PSK supported
[ 4089.830583] ADDRCONF(NETDEV_UP): eth1: link is not ready

```

Interesting that it starts with version 6.04 then requests the newer version...

---

### Post by eekrazyk on 2010-06-19
I installed wicd again and stopped NM and then was able to connect to my WRT54G with WPA.  Sweet.

---

### Post by freddiespagheti on 2010-06-19
Well, I followed your lead and it worked, but its ridiculous what I have to do in order to connect. I installed Wicd again and once thee computer starts up I have to first *stop* NM from trying to connect. Then I have to unplug and and plug back in my pcmcia wireless card so that Wicd will detect the networks. Then I have Wicd try to connect. It will fail. *Then* I try to connect from NM again and it will succeed.

This is just silly](*,)

---

### Post by eekrazyk on 2010-06-19
Yea, I removed NM so I wouldn't have to do that.

After the next reboot, wicd failed with a "bad password" error.  I checked the WPA key, deleted one character and replaced it with the same character again and it connected.  I have to do that every time I reboot...  I don't get it.

---

### Post by tubunu on 2010-09-11
I also have the same problem, has anyone managed to get a work around to getting PCMCIA card to work on Lubuntu? Thanks.

---

