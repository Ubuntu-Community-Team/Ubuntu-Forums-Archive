---
title: "Very Strange Problem..."
date: 2011-08-12
forum: Networking &amp; Wireless
---

### Post by lamefox on 2011-08-12
This might take a bit of background to make sense of, so I apologise if it's long and sounds like a life story.

Well, firstly, the actual problem I'm having is that when I start my computer (netbook) up in the morning and try to connect to the router (wirelessly) it just... doesn't work. I've used it before, at full signal strength, and it was completely fine. It never disconnects me or anything - but if I shut down my computer, like I do overnight, when I start it up again often it's hardly getting a signal at all (or so it says) and when it tries to connect it makes the connecting animation and occasionally flashes to a circular thing like firefox's loading animation. Eventually it just fails.

I try restarting my computer, but it doesn't seem to help. The last time, I had to wait until the signal looked "full" again, then *delete the settings in "edit connections" for that router* and only then would it let me log in again, even though I was using the same password from the same computer (even in the same place). That only seems to help when the connection looks "full" though, and even then, not always.



Normally I'd try resetting the router, but I can't because it's locked in the next room (I rent a room here and the guy with the key is rarely around) but honestly I don't think the router is causing this, for a few reasons:

one, because it's locked in a room nobody is entering. Nobody has done anything to it now, nor had they when this problem occurred and later corrected itself before. There have been no cuts to the power or anything else, either.

two, because it never disconnects me, nor does the signal strength ever seem to drop when I'm already connected. And if I ever get connected to it again, I think I'll just leave this on, always, because of that.

three, because I've had this exact problem in other places, usually coffee shops and the like with free wi-fi. In those cases I at first assumed it was their routers acting up, but even then I sometimes noticed restarting, or disabling and re-enabling "networking" and/or "wireless" could fix it. But, not always.

Anyway, it really seems like the common factor in all this is my computer. Besides keeping it up to date, which I do, I really can't think of anything else to do to fix it...

---

### Post by nickleboyblue on 2011-08-12
It will help to let us know what kind of netbook you have and what version of Ubuntu you are using.  If you are using 11.04, I would suggest you move back to 10.04, as that's the LTS version and 11.04 still has a lot of aspects that should not have been allowed out of development yet, and since they don't have a huge testing team, they released them anyway in an attempt to find those things that don't work so well.

Sometimes, wireless networks get finicky if they have too many people connected to them.  If you and the guy you pay for the connection are the only people who use the network, that will very likely not be the problem, but if it's the only wireless network in the complex, you should seriously consider getting your own network.  Also, sometimes wireless networks seem to favor PC's over LB's (Linux Boxes), as Windows 7 likes to make a little bit more noise on the network to keep connections alive.  If your network guy added someone else to the network, there's a chance that that is the source of your problems.

---

### Post by FormatSeize on 2011-08-12
In the dialogue box where you edit your connections, make sure the "Connect Automatically" checkbox is checked.

---

### Post by lamefox on 2011-08-12
The netbook is made by samsung but I don't really know anything else about it. I am pretty sure I have 11.04 because it's just what was there when I went to the download page, so I assumed it would be the proper one to use. I don't think there's anyone else on the network, however.

Is there some way to change to 10.04 without losing my files, bookmarks and such? Or would I need to find some way to back those up separately?



Regarding connect automatically, it appears to set itself that way already.

---

### Post by pdc on 2011-08-12
what about some facts?

if you copy and paste

lspci -nn
uname -rm
sudo iwlist scan
lshw -C Network
sudo lshw -C network
iwconfig
rfkill list all
lsmod

---

### Post by lamefox on 2011-08-12
I really wish ctrl-v worked in the terminal...

> 00:00.0 Host bridge [0600]: Intel Corporation N10 Family DMI Bridge [8086:a010] (rev 02) 
 00:02.0 VGA compatible controller [0300]: Intel Corporation N10 Family Integrated Graphics Controller [8086:a011] (rev 02) 
 00:02.1 Display controller [0380]: Intel Corporation N10 Family Integrated Graphics Controller [8086:a012] (rev 02) 
 00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02) 
 00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02) 
 00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 02) 
 00:1c.2 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 3 [8086:27d4] (rev 02) 
 00:1c.3 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 4 [8086:27d6] (rev 02) 
 00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 [8086:27c8] (rev 02) 
 00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02) 
 00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02) 
 00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02) 
 00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02) 
 00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2) 
 00:1f.0 ISA bridge [0601]: Intel Corporation NM10 Family LPC Controller [8086:27bc] (rev 02) 
 00:1f.2 SATA controller [0106]: Intel Corporation N10/ICH7 Family SATA AHCI Controller [8086:27c1] (rev 02) 
 00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02) 
 05:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01) 
 09:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354] 
 

 

 

 2.6.38-10-generic i686 
 

 

 

 lo        Interface doesn't support scanning. 
  
 eth0      Interface doesn't support scanning. 
  
 eth1      Scan completed : 
           Cell 01 - Address: 00:1C:F0:55:F0:EF 
                     ESSID:"dlink" 
                     Mode:Managed 
                     Frequency:2.412 GHz (Channel 1) 
                     Quality:1/5  Signal level:-89 dBm  Noise level:-92 dBm 
                     Encryption key:off 
                     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s 
                               12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s 
                               48 Mb/s; 54 Mb/s 
           Cell 02 - Address: 00:22:B0:B6:65:19 
                     ESSID:"dlink" 
                     Mode:Managed 
                     Frequency:2.427 GHz (Channel 4) 
                     Quality:5/5  Signal level:-36 dBm  Noise level:-93 dBm 
                     IE: IEEE 802.11i/WPA2 Version 1 
                         Group Cipher : TKIP 
                         Pairwise Ciphers (1) : TKIP 
                         Authentication Suites (1) : PSK 
                     IE: Unknown: DD7B0050F204104A00011010440001021041000100103B00010310470010565AA94967C14C0EAA8FF349E6F5931110210006442D4C696E6B1023000D442D4C696E6B20526F75746572102400074449522D363135104200046E6F6E651054000800060050F204000110110006442D4C696E6B100800020084103C000101 
                     IE: WPA Version 1 
                         Group Cipher : TKIP 
                         Pairwise Ciphers (1) : TKIP 
                         Authentication Suites (1) : PSK 
                     Encryption key:on 
                     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s 
                               9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s 
                               48 Mb/s; 54 Mb/s 
           Cell 03 - Address: 00:13:46:FA:68:7A 
                     ESSID:"dlink" 
                     Mode:Managed 
                     Frequency:2.437 GHz (Channel 6) 
                     Quality:2/5  Signal level:-78 dBm  Noise level:-96 dBm 
                     IE: IEEE 802.11i/WPA2 Version 1 
                         Group Cipher : TKIP 
                         Pairwise Ciphers (1) : TKIP 
                         Authentication Suites (1) : PSK 
                     Encryption key:on 
                     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s 
                               11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s 
                               48 Mb/s; 54 Mb/s 
 

 

 

 WARNING: you should run this program as super-user. 
   *-network                
        description: Wireless interface 
        product: BCM4313 802.11b/g/n Wireless LAN Controller 
        vendor: Broadcom Corporation 
        physical id: 0 
        bus info: pci@0000:05:00.0 
        logical name: eth1 
        version: 01 
        serial: 4c:ed:de:a0:a6:10 
        width: 64 bits 
        clock: 33MHz 
        capabilities: bus_master cap_list ethernet physical wireless 
        configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 ip=192.168.0.103 latency=0 multicast=yes wireless=IEEE 802.11 
        resources: irq:16 memory:f0100000-f0103fff 
   *-network 
        description: Ethernet interface 
        product: 88E8040 PCI-E Fast Ethernet Controller 
        vendor: Marvell Technology Group Ltd. 
        physical id: 0 
        bus info: pci@0000:09:00.0 
        logical name: eth0 
        version: 00 
        serial: e8:11:32:2e:63:98 
        capacity: 100Mbit/s 
        width: 64 bits 
        clock: 33MHz 
        capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
        configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 firmware=N/A latency=0 multicast=yes port=twisted pair 
        resources: irq:44 memory:f0200000-f0203fff ioport:2000(size=256) 
 WARNING: output may be incomplete or inaccurate, you should run this program as super-user. 
 

 

 

   *-network                
        description: Wireless interface 
        product: BCM4313 802.11b/g/n Wireless LAN Controller 
        vendor: Broadcom Corporation 
        physical id: 0 
        bus info: pci@0000:05:00.0 
        logical name: eth1 
        version: 01 
        serial: 4c:ed:de:a0:a6:10 
        width: 64 bits 
        clock: 33MHz 
        capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless 
        configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 ip=192.168.0.103 latency=0 multicast=yes wireless=IEEE 802.11 
        resources: irq:16 memory:f0100000-f0103fff 
   *-network 
        description: Ethernet interface 
        product: 88E8040 PCI-E Fast Ethernet Controller 
        vendor: Marvell Technology Group Ltd. 
        physical id: 0 
        bus info: pci@0000:09:00.0 
        logical name: eth0 
        version: 00 
        serial: e8:11:32:2e:63:98 
        capacity: 100Mbit/s 
        width: 64 bits 
        clock: 33MHz 
        capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
        configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 firmware=N/A latency=0 link=no multicast=yes port=twisted pair 
        resources: irq:44 memory:f0200000-f0203fff ioport:2000(size=256) 
 

 

 

 lo        no wireless extensions. 
  
 eth0      no wireless extensions. 
  
 eth1      IEEE 802.11  Access Point: Not-Associated    
           Link Quality:1  Signal level:171  Noise level:167 
           Rx invalid nwid:0  invalid crypt:0  invalid misc:0 
 

 

 

 0: brcmwl-0: Wireless LAN 
     Soft blocked: no 
     Hard blocked: no 
 1: hci0: Bluetooth 
     Soft blocked: no 
     Hard blocked: no 
 

 

 

 Module                  Size  Used by 
 binfmt_misc            13213  1  
 parport_pc             32111  0  
 ppdev                  12849  0  
 snd_hda_codec_realtek   255882  1  
 rfcomm                 38125  8  
 sco                    17827  2  
 bnep                   17785  2  
 snd_hda_intel          24140  4  
 l2cap                  48656  16 rfcomm,bnep 
 snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel 
 snd_hwdep              13274  1 snd_hda_codec 
 i915                  450934  3  
 snd_pcm                80042  3 snd_hda_intel,snd_hda_codec 
 snd_seq_midi           13132  0  
 snd_rawmidi            25269  1 snd_seq_midi 
 uvcvideo               66851  0  
 snd_seq_midi_event     14475  1 snd_seq_midi 
 btusb                  18160  2  
 videodev               75143  1 uvcvideo 
 snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event 
 lib80211_crypt_tkip    17203  0  
 bluetooth              65493  9 rfcomm,sco,bnep,l2cap,btusb 
 psmouse                73312  0  
 wl                   2642531  0  
 snd_timer              28659  2 snd_pcm,snd_seq 
 snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq 
 drm_kms_helper         40745  1 i915 
 serio_raw              12990  0  
 snd                    55295  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
 drm                   180037  4 i915,drm_kms_helper 
 soundcore              12600  1 snd 
 lib80211               14570  2 lib80211_crypt_tkip,wl 
 snd_page_alloc         14073  2 snd_hda_intel,snd_pcm 
 i2c_algo_bit           13184  1 i915 
 video                  18951  1 i915 
 lp                     13349  0  
 parport                36746  3 parport_pc,ppdev,lp 
 ahci                   21591  2  
 libahci                25548  1 ahci 
 sky2                   49172  0  
 

---

### Post by westie457 on 2011-08-12
Hi adding my 2 cents here and not wanting to upstage anyone.

To me it looks like an incorrect driver is being used.

Take a look at the first link for the alternative driver.

[http://wireless.kernel.org/en/users/Drivers/b43](http://wireless.kernel.org/en/users/Drivers/b43)

Then go to the second link for instructions to install

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

To remove the unneeded one while Synaptic is open all you do is mark for removal and click apply.

A quick reboot and wait for the dust to settle and you should have fully functioning wireless.

---

### Post by lamefox on 2011-08-12
Hi

those instructions told me my card is "Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)" and that is in the list for "STA driver" compatibility, but when I follow the instructions for installing that, and find it in the package manager, it says the installed version is the same as the latest version.

---

### Post by nm_geo on 2011-08-12
Please add the command 

```
nm-tool
```copy and paste results

Yes your chipset is supported by the STA (wl) driver and that is what is installed.

---

### Post by lamefox on 2011-08-12
.

> NetworkManager Tool

State: connected

- Device: eth1  [Auto dlink] ---------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             connected
  Default:           yes
  HW Address:        4C:ED:DE:A0:A6:10

  Capabilities:
    Speed:           1 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    honeysett:       Infra, 00:26:5A:FE:2F:52, Freq 2427 MHz, Rate 54 Mb/s, Strength 40
    Tooley:          Infra, 98:FC:11:48:35:84, Freq 2462 MHz, Rate 0 Mb/s, Strength 20 WPA WPA2
    arcade:          Infra, 00:26:5A:F9:E6:A4, Freq 2437 MHz, Rate 54 Mb/s, Strength 20 WEP
    *dlink:          Infra, 00:1C:F0:55:F0:EF, Freq 2412 MHz, Rate 54 Mb/s, Strength 20
    dlink:           Infra, 00:22:B0:B6:65:19, Freq 2427 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    dlink:           Infra, 00:13:46:FA:68:7A, Freq 2437 MHz, Rate 0 Mb/s, Strength 20 WPA2
    HPD110a.E3849C:  Ad-Hoc, 02:24:D4:4B:22:4B, Freq 2437 MHz, Rate 54 Mb/s, Strength 40
    BELL973:         Infra, 00:1D:5A:AF:10:81, Freq 2447 MHz, Rate 54 Mb/s, Strength 40 WEP

  IPv4 Settings:
    Address:         192.168.0.103
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            sky2
  State:             unavailable
  Default:           no
  HW Address:        E8:11:32:2E:63:98

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off




---

### Post by westie457 on 2011-08-12
Just to clarify... You are using the STA driver downloaded from the Broadcom web-site. Is that correct? IMHO you should install the bcmwl-kernel-source driver and remove the one you are currently using.

---

### Post by nm_geo on 2011-08-12
When you click left click on the network manager icon ... How many dlink wireless connection do you see?  

I notice in the wireless scan you did earlier 3 different channels all with the dlink ESSID I do not know much about that dlink router.. But I can see that if you were able to connect to the second cell listed it is much stronger. If you do happen to see two or three "dlink" try to connect another one for strength.

That might explain the having to reconnect when the signal strength is strong. I thought you said that you have automatic clicked on in the network manager with ESSID 'dlink'.  Again I am not a dlink specialist but I would recommend you edit your wireless in network manager make it available to everyone and make sure you have connects automatically checked... check both..

---

### Post by nm_geo on 2011-08-12
> **westie457 said:**
> Just to clarify... You are using the STA driver downloaded from the Broadcom web-site. Is that correct? IMHO you should install the bcmwl-kernel-source driver and remove the one you are currently using.

He has the bcmwl-kernel-source driver installed already..

---

### Post by lamefox on 2011-08-12
> **nm_geo said:**
> When you click left click on the network manager icon ... How many dlink wireless connection do you see?  

I notice in the wireless scan you did earlier 3 different channels all with the dlink ESSID I do not know much about that dlink router.. But I can see that if you were able to connect to the second cell listed it is much stronger. If you do happen to see two or three "dlink" try to connect another one for strength.

That might explain the having to reconnect when the signal strength is strong. I thought you said that you have automatic clicked on in the network manager with ESSID 'dlink'.  Again I am not a dlink specialist but I would recommend you edit your wireless in network manager make it available to everyone and make sure you have connects automatically checked... check both..

I'm not quite sure what you mean... the (sometimes) stronger dlink (which is locked) is the one I want to use, but can't, even when it looks like full signal strength. This one I'm on now is further away and quite weak from here, while the one I'm trying to use is only in the next room.

I don't know what the network manager is, or if it's the same as where "connect automatically" is, I don't see any option about availability. Connect Automatically is definitely set to on, though. It seems to default to that with each new connection it makes, ever, including this one.

---

### Post by nm_geo on 2011-08-12
Look at the screen shot that is the Network Manager.. you can right click or left click on it.  It is where you select and setup wireless connections.

---

### Post by lamefox on 2011-08-12
Hm... I can't find anything at all about setting something available to everyone. But connecting automatically is definitely on (and it does this - or tries to, depending on the network it's attempting to connect to).

---

### Post by nm_geo on 2011-08-12
Right Click on wireless icon 
> Edit connections
 > wireless tab
 > Maybe 'auto dlink'
> edit
Password


However when you left click do you see wireless networks?
Do you see signals?
Can you pick the dlink that is strongest?
Do you have the passphase from the owner?

See screen shot

---

### Post by lamefox on 2011-08-12
I see the different signals yes. I can select the strongest dlink and I have the password for it, but all it does it try to connect for a while then give up.

When I open the edit window for that connection, it doesn't ask for the password. I'm not sure why, maybe because I'm not actually connected to it. But I can look at the window in the screenshot.

---

### Post by nm_geo on 2011-08-13
Here is another screen shot make sure you have WPA2 selected in the security tab settings.

Added all the Tabs under edit wireless. Not in order but all there.

---

### Post by lamefox on 2011-08-13
Yeah that setting looks right too. And if I tell it to show the password it's not typed incorrectly or anything like that.

---

