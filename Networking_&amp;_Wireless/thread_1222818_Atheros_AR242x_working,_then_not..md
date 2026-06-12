---
title: "Atheros AR242x working, then not."
date: 2009-07-25
forum: Networking &amp; Wireless
---

### Post by Samm1 on 2009-07-25
[SIZE=3]I am having a problem with my Atheros Wlan adapter.  I am running Ubuntu 9.04. My HP Atheros AR242x was working fine until today when I turned it on, it would not connect to my wireless network but would see other networks in the Network Applet. So, to see if it would help, I opened System>Administration>Hardware Drivers and enabled the madwifi drivers and rebooted, and I could not see any networks at all. I rebooted into Windows (which I only use for games and occasional internet) and I couldn't see any network, dispite reseting the adapter, and refresh the network list. I rebooted back to ubuntu, disabled the madwifi, rebooted, and I can still see no networks, in neither Windows nor Ubuntu. Is there anything I can do? I DO have temporay internet access via a usb apdapter that connnects via a long cord, but for portablilty reasons, I would much like this issue resolved. 

Thanks in advanced.
[/SIZE]

---

### Post by synapsys on 2009-07-25
If you are having problems with your wireless card in both windows and ubuntu, it sounds like you have a problem with your wireless card. You can try removing and reseating your wireless card. With jaunty, ath5k comes installed by default, which supersedes madwifi, so you should not have to mess with your wireless drivers at all. Now that you have installed madwifi you will need to uninstall and blacklist it.

---

### Post by Samm1 on 2009-07-25
My wireless card is built in, coming with my laptop. Reseting the adapter both physically and through software, e.g. Windows Enable/Disable adapter doesn't fix the problem.

I was having no problems at all until I enabled madwifi, and even after disabling it, it persists, so I believe those drivers put it into a state I can't get it out of. Will blacklisting the madwifi (effectivly putting ath5k back into commission) fix this, or any other problem I'm having? Either way, blacklisting will ensure this doesn't happen again.

Thanks for the fast response.

---

### Post by superprash2003 on 2009-07-26
post output of 
1)lshw -C network
2)sudo iwlist scanning

---

### Post by Samm1 on 2009-07-26
I ran the iwlist scanning command and got nothing yesterday, but today I got the networks in my neighborhood. I guessed it solved itself, odd, I know, sorry to waste your time. :(

How ever, I still can't connect to my network, I have the outputs of both commands here. My network may be a hidden network, but it worked before, AND I have the BSSID of the network plugged in.

```
sam@sam-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: MCP78S [GeForce 8200] Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1d:72:6c:d3:c0
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wmaster0
       version: 01
       serial: 00:22:68:bb:87:5a
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k_pci latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 7e:ed:11:49:4d:05
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

sam@sam-laptop:~$ sudo iwlist scanning
[sudo] password for sam: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:18:01:F9:26:22
                    ESSID:"KTUP4"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=28/100  Signal level:-78 dBm  Noise level=-96 dBm
                    Encryption key:on
                    IE: Unknown: 00054B54555034
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030101
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 200100
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F010100200000
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000021f39e3ea7e
                    Extra: Last beacon: 1688ms ago
          Cell 02 - Address: 00:1F:90:E9:72:5C
                    ESSID:"K07J1"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=12/100  Signal level:-92 dBm  Noise level=-100 dBm
                    Encryption key:on
                    IE: Unknown: 00054B30374A31
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030106
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 200100
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F010100200000
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000026ea605c181
                    Extra: Last beacon: 1856ms ago
          Cell 03 - Address: 00:23:69:16:0B:2D
                    ESSID:"JAS"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=12/100  Signal level:-89 dBm  Noise level=-97 dBm
                    Encryption key:on
                    IE: Unknown: 00034A4153
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018020105
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=00000086e76fa7eb
                    Extra: Last beacon: 1244ms ago
          Cell 04 - Address: 00:18:01:FD:06:14
                    ESSID:"IUYD7"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=17/100  Signal level:-85 dBm  Noise level=-96 dBm
                    Encryption key:on
                    IE: Unknown: 00054955594437
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 03010B
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 200100
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F010100200000
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=000003a905b2799f
                    Extra: Last beacon: 896ms ago
          Cell 05 - Address: 00:13:10:1A:1E:F6
                    ESSID:""
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=37/100  Signal level:-73 dBm  Noise level=-97 dBm
                    Encryption key:on
                    IE: Unknown: 00080000000000000000
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0105
                    IE: Unknown: 2F0105
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018020604
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=0000001c281c998e
                    Extra: Last beacon: 1400ms ago

pan0      Interface doesn't support scanning.


```

Now, to make sure the madwifi don't kick in again, what can I do to blacklist them?

Thanks for the responses!

---

### Post by synapsys on 2009-07-26
This is the contents of my blacklist-ath_pci.conf located in /etc/modprobe.d/

> # For some Atheros 5K RF MACs, the madwifi driver loads buts fails to
# correctly initialize the hardware, leaving it in a state from
# which ath5k cannot recover. To prevent this condition, stop
# madwifi from loading by default. Use Jockey to select one driver
# or the other. (Ubuntu: #315056, #323830)
blacklist ath_pci


---

### Post by superprash2003 on 2009-07-28
hmm.. are you sure you cannot see your wifi networks? i can see 5 wifi networks around you using the sudo iwlist scanning command.. do you get any error from network manager saying "device not managed" ?

---

### Post by LightningCrash on 2009-08-26
If you look in kern.log when this happens you'll likely see entries like the following
```
Aug 26 15:09:56 laptop kernel: [ 5873.739604] wifi0: ath_chan_set: Unable to reset channel 7 (2442 MHz) flags 0xc0 'Hardware didn't respond as expected' (HAL status 3)
```

This is on a fresh install of Jaunty with the trunk Madwifi drivers. The hardware stops responding until you reboot.

I'm going through this issue myself and I will try to update with anything that I find.

---

### Post by theDaveTheRave on 2009-08-27
Sam1.

have you been able to get this card working again?

I had a lot of issues when I upgraded to intrepid, it zapped out my wireless card, and with a lot of playing I eventually got it going again.... but it wasn't a nice experience!

Have a look at this sticky thread

[http://ubuntuforums.org/showthread.php?t=885847]("http://ubuntuforums.org/showthread.php?t=885847")

The guy really seems to know how to get these cards working when the go wrong. with luck you'll find an answer somewhere in the thread (admitedly it is rather long though!).

David

---

### Post by LightningCrash on 2009-09-03
I took the easy way out: I found an Intel 3945ABG card online for $5. 

:D

Works like a champ when you use a real card!

---

