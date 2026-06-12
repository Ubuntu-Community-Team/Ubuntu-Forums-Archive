---
title: "Really annoying WPA issue"
date: 2010-06-07
forum: Networking &amp; Wireless
---

### Post by Windows Nerd on 2010-06-07
So, I finally have gotten around to addressing what to do with this god darn problem (with just one even more annoying workaround). 

Anyways, so to fill y'all in:

About a month (I think...things have been so darn busy I can't remember :p) ago my router crapped out on me. I think it was because of a power surge, but anyways, it died. So I went and got a replacement one (well actually my dad did, I didn't have time), which is the excact same model as the other one. The new one worked fine for a few days. The only one had worked perfectly fine for almost a year. I set up the new one with the exact same configuration as the old one. 

The problemo is as follows:

After a few days when I brought my computer out of suspend it could not connect to the network. It would just keep trying to connect, every so often asking for confirmation about what the WPA key was. I have autosaved the Key with network manager. I cannot connect by doing anything, I have tried connecting to my neighbour's network, then connecting back to my own, turning the wireless card on/off, disabling/enabling networking/wireless through nm-applet, suspending and resuming the computer, and then restarting it. 

The only current workaround I know of is to go reset the router by unplugging it and waiting a couple seconds then plugging it back in.

If I boot a Windows machine, it tells me that the router is not responding and to go reset it.

If I am on a Mac it just says it cannot connect after trying for about 3 minutes.

So, you may be wondering, why am I asking about another workaround?
1) The router is far away from my computer and I am lazy to walk to it and reset it.
2) I will be downloading something, then forget about, then go reset my router (and blipping out the internet for about 10 seconds in the proccess) and my download fails and I have to restart it.
3) My brother is playing Xbox and gets pissed when his game disconnects, 'specially if he is winning ;)

I have asked my neighbour (who is an absolute Linux guru) and he tried to solve the problem of Network Manager keeping asking for the password while constanly trying to connect by trying to edit /etc/wpa_supplicant/wpa_supplicant.conf and putting the proconfigured password there so it wouldn't have to keep asking what the password is. Except that it doesn't exist on Ubuntu (I have no idea what distro he uses, I only learned what WM he used about a week ago, but it does on his system).

Edit: Pardon me about not providing some information about my hardware/config.

Note: was connected to the network when I ran these commands.

```
scott@scott-laptop:~$ iwconfig
lo        no wireless extensions.

vboxnet0  no wireless extensions.

pan0      no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"home1"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:25:9C:F3:C5:9F   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=44/70  Signal level=-66 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
``````
scott@scott-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:e0:b8:c5:c0:eb  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:803 errors:0 dropped:0 overruns:0 frame:0
          TX packets:803 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:63526 (63.5 KB)  TX bytes:63526 (63.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:c0:a8:de:d7:67  
          inet addr:192.168.0.108  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:a8ff:fede:d767/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16747 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9226 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7467440 (7.4 MB)  TX bytes:1411749 (1.4 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-C0-A8-DE-D7-67-37-36-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
``````
scott@scott-laptop:~$ lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter    #<--this is my wirelss card.
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 046d:c521 Logitech, Inc. MX620 Laser Cordless Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```I will gladly provide any more particular commands if you need them.

/edit

Any help? Does anyone know about another workaround or have a problem similar to this?

Scott

---

### Post by Windows Nerd on 2010-06-08
Bump. 58 views, no replies ;(

---

### Post by PRC09 on 2010-06-08
If as you said "The new one  worked fine for a few days" then it could be a problem with the new router.If you can connect to your neighbors network an d not to your own and also if you get the same connection errors and problems in the other operating systems then I would suspect a problem with the router and not Ubuntu......

---

### Post by Windows Nerd on 2010-06-09
So then what do you suggest I do with the router (besides getting a new one, I have alrready had to replace it once)

---

### Post by randumnumber on 2010-06-09
> **Windows Nerd said:**
> So then what do you suggest I do with the router (besides getting a new one, I have alrready had to replace it once)

If it were me i would hit the reset button on the back of the router, remove all the autoconfigured connection stuff from my machine in NetworkManager and start over. If you named your network the same thing as your old network but it is on a new router this could theoretically cause issues because that network essid looks the same but the bssid is different. so you could try naming the network something different, if you didnt do that already. also go into your router and see if the firmware can be updated if so... update it. if none of this works and the problems persist in all other platforms then youve got a faulty Access point.

---

### Post by sille777 on 2010-06-09
> **PRC09 said:**
> If as you said "The new one  worked fine for a few days" then it could be a problem with the new router.If you can connect to your neighbors network an d not to your own and also if you get the same connection errors and problems in the other operating systems then I would suspect a problem with the router and not Ubuntu......


I Would agree this seems more like a router or even a DSL/Cable modem issue. Esp. if its effecting all connected  devices in your house.  

Might want to contact your ISP to see if there is a way to test or check the modem itself as well


I recently had to replace my DSL modem due to intermittent connectivity issues and first suspected the router and had already it replaced with a new one.  I knew it wasnt just my laptop as all computers and even my netflix blueray player was effected.

---

### Post by Windows Nerd on 2010-06-12
> **sille777 said:**
> I Would agree this seems more like a router or even a DSL/Cable modem issue. Esp. if its effecting all connected  devices in your house.  

Might want to contact your ISP to see if there is a way to test or check the modem itself as well


I recently had to replace my DSL modem due to intermittent connectivity issues and first suspected the router and had already it replaced with a new one.  I knew it wasnt just my laptop as all computers and even my netflix blueray player was effected.
Wired works fine, but it is only wireless that is the problem.

Hitting the reset switch is my current fix, and I can connect to it just fine for anywhere from 3 hours to two days. I don't disconnect at all from the router, it's just when I suspend the computer then re-connect when I turn the computer back on is the problem.

If it may be that though I am using the same configuration for the router but it is a different BSSID, then wouldn't just deleting the connection settings out of Network-Manager for the network, then setting up a new connection, work?

I am going to try that

---

