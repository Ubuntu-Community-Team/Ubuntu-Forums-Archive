---
title: "Broadcom BCM4311: Network works but fails"
date: 2013-03-04
forum: Networking &amp; Wireless
---

### Post by LoopTown on 2013-03-04
Hy, my problem in general is about network _almost_ working.

I'm using 12.10 ubuntu (installed on a new HDD after using 12.04 wich didn't work too well) on Dell Latitude D620.

All problems start with Software Updater wich shows me 40 new updates waiting to be installed. After pressing install now I get a error "system error". Pressing report error it gives me another one something like "ubuntu experienced a software error", after pressing report error it gives me yet another one telling that program crashed unexpectedly. After clicking leave closed it askes me about a minute later my password to report a problem. In this time software updater just hangs there - not responding, not crashing - just chillin'.

Also software center doesn't allow me to install anything - clicking install it just doesn't do anything whatsoever.

Only thing that let's me do anything in matter of sofware is synaptic package manager.

Also my transmission (BitTorrent client) downloads everything for about a minute or so and then gradually closes all connections (wihtout any warning or anything). Both for uploading and dowloading. New connection is possible but those as well get disconnected in about a minute or so. Restarting transmission gives me another minute of up/downloading.

Problem keep coming - sometimes my wireless connection decides to just go away - it does not disconnect connection, it just goes away. The icon shows no connection but clicking on the icon tell me i'm connected. After closing connection thru pressing a button on my laptop and then switching it on again the wireless network comes back.

Thing that is problably not the problem with network but someone might find it useful for me to mention is that I can't backup my system - namely because backup keeps asking me the encryption password (not saying it's wrong but asks me for the password - starts the process of prepearing for backup - asks me for the password again and starts the process again and so on and so on). Password is correct - I know that much.

Overall I have to do a restart on my computer at least once a day to use Wifi in general (sometimes the switch on the laptop doesn't do anything at all).

On Windows XP (sorry for mentioning it on ubuntu forums) all worked well.

Really don't like to go back on windows a Linux is a great platform to learn Computer Science on and has a lot of extremely useful tools and apps for free. That being said - I really can't use my computer like this also.

Thanks for any help you could give me!

PS! Updateing and upgrading doesn't work thru terminal either.
PPS! Problems I had with 12.04 still remain with 12.10 in network-wise. My unsolved post about 12.04 IM connection problems (still have the same problem in 12.10 [http://ubuntuforums.org/showthread.php?t=2098635](http://ubuntuforums.org/showthread.php?t=2098635) )

---

### Post by chili555 on 2013-03-04
Let's see what kind of wireless card you have. Please open a terminal and do:```
lspci -nn | grep 0280
```The pipe symbol | is on the right side of my US keyboard on the same key with \. If it is a Broadcom, also post:```
lsmod | grep -e b43 -e brcmsmac -e wl
```Thanks.

---

### Post by LoopTown on 2013-03-04
Here they are!

lspci
> 0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)

lsmod
> 
b43                   347311  0 
mac80211              461203  1 b43
cfg80211              175574  2 b43,mac80211
bcma                   34484  1 b43
ssb                    50088  2 b43,ssb_hcd



---

### Post by chili555 on 2013-03-04
A Broadcom; pretty good guess, eh? All looks just fine so far. Let's see a couple of other things:```
dmesg | grep -e wlan -e b43
nm-tool
```

---

### Post by LoopTown on 2013-03-04
Let me guess - broadcom is not the best network hardware around?

dmesg
> 
[   32.145595] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
[   32.573814] Registered led device: b43-phy0::tx
[   32.573843] Registered led device: b43-phy0::rx
[   32.573877] Registered led device: b43-phy0::radio
[   38.848098] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[   38.961139] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   38.961555] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   41.396888] wlan0: authenticate with 08:76:ff:85:80:09
[   41.420264] wlan0: send auth to 08:76:ff:85:80:09 (try 1/3)
[   41.422681] wlan0: authenticated
[   41.428169] wlan0: associate with 08:76:ff:85:80:09 (try 1/3)
[   41.430577] wlan0: RX AssocResp from 08:76:ff:85:80:09 (capab=0x411 status=0 aid=1)
[   41.431048] wlan0: associated
[   41.431273] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready



NM Tool
> 
State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             unavailable
  Default:           no
  HW Address:        00:18:8B:A9:3E:63

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0  [Thomson-08-76-FF-85-80-09] -----------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             connected
  Default:           yes
  HW Address:        00:19:7D:18:44:F1

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    Thomson-08-76-FF-CB-3B-F4: Infra, 08:76:FF:CB:3B:F4, Freq 2462 MHz, Rate 54 Mb/s, Strength 59 WPA WPA2
    Maestro:         Infra, 00:1C:F0:DF:3C:3D, Freq 2437 MHz, Rate 54 Mb/s, Strength 57 WPA
    Thomson-58-98-35-F4-B1-DC: Infra, 58:98:35:F4:B1:DC, Freq 2462 MHz, Rate 54 Mb/s, Strength 54 WPA WPA2
    Air:             Infra, 00:24:36:AC:2F:2B, Freq 2462 MHz, Rate 54 Mb/s, Strength 40 WPA2
    Rasti:           Infra, 64:70:02:CA:3E:3C, Freq 2452 MHz, Rate 54 Mb/s, Strength 32 WPA2
    lisette:         Infra, 00:16:01:C7:16:A7, Freq 2442 MHz, Rate 54 Mb/s, Strength 45 WEP
    *Thomson-08-76-FF-85-80-09: Infra, 08:76:FF:85:80:09, Freq 2462 MHz, Rate 54 Mb/s, Strength 78 WPA WPA2
    Vkos:            Infra, BC:AE:C5:C3:C4:6D, Freq 2412 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2

  IPv4 Settings:
    Address:         192.168.1.68
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254





---

### Post by chili555 on 2013-03-04
> *Thomson-08-76-FF-85-80-09: Infra, 08:76:FF:85:80:09, Freq 2462 MHz, Rate 54 Mb/s, Strength 78 [COLOR="#FF0000"]WPA WPA2[/COLOR]Would you please try setting your router to WPA2 only and not mixed mode WPA and WPA2? Also, is your router set for B, G and N speeds? Will you please try B and G only? Finally, please Edit Connections in Network Manager and set IPv6 to Ignore. Please see attached.

Everything else looks very fine.

---

### Post by LoopTown on 2013-03-04
It's going to take a little time as now I can't connect to the wireless network with any computer in my house ( I've changed all the settings in computers too - encryption and key type and such).

---

### Post by LoopTown on 2013-03-04
It's done, and got my wireless back. Still doesn't update the system.

---

### Post by chili555 on 2013-03-04
Are there any errors or warnings if you do:```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by LoopTown on 2013-03-04
Now it seems like the transmission kills connections a lot faster - within 10 seconds into downloading.

---

### Post by LoopTown on 2013-03-04
On update no but on apt-get install says just ... 36 not upgraded
apt-get upgrade though worked just fine.

---

### Post by LoopTown on 2013-03-04
On upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  linux-headers-generic linux-image-generic
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.


but right now upgraded 34 (i guess) programs (f**k yeah man :D)

---

### Post by LoopTown on 2013-03-04
Transmission says the port is closed. How can I check what ports are open or how to open a port for transmission?

Thank you for your help thus far! (I'm still making animal noises trying to express my happiness about getting at least something upgraded in this system at 01:28 am with my gf trying to sleep).

PS! I'm working on transmission - found a way for handeling ports.

---

### Post by chili555 on 2013-03-04
> Transmission says the port is closed. How can I check what ports are open or how to open a port for transmission?Usually that's in the router. Please see attached from my dd-wrt flashed router.

---

### Post by LoopTown on 2013-03-04
Found it and made all necessary changes but still shows port closed (allows some connection and then closes them). Firewall is not active in router. I'll try to handle it.

Thing that I can't handle myself is why I can't install anything from software center, maybe again something to do with my router or ports perhaps?

---

### Post by chili555 on 2013-03-05
Is the firewall active in the computer?```
sudo ufw status
```You might momentarily de-activate it:```
sudo ufw disable
```> Firewall is not active in router. I recommend you activate it immediately.

---

### Post by LoopTown on 2013-03-06
Status: Inactive

Activated routers firewall (ISP put up the router - interesting guys as I've seen it so far).

---

### Post by chili555 on 2013-03-06
So now what is the result of:```
sudo apt-get update && sudo apt-get -y upgrade
```

---

### Post by LoopTown on 2013-03-06
55 upgraded, 0 newly installed, 0 to be deleted and 2 not upgraded.

Guess it works?

---

### Post by chili555 on 2013-03-06
> **LoopTown said:**
> 55 upgraded, 0 newly installed, 0 to be deleted and 2 not upgraded.

Guess it works?I guess it does. The two not upgraded are probably the kernel and linux-headers. Update Manager will probably want to handle those for you so it, a GUI, can remind you to reboot.

---

### Post by LoopTown on 2013-03-09
Thank You my sir! I was away for a few days dealing with the Estonian local WorldSkills 2013 and where I used their computers. Coming back home everything seems to be just fine, even transmissin is working well. Now it's time to start troubleshooting why software updater crashes every singel time I use it.

But really, Thank You for helping!

---

### Post by chili555 on 2013-03-09
> Estonian local WorldSkills 2013Awesome!> Now it's time to start troubleshooting why software updater crashes every singel time I use it.Is it Updater, Synaptic, apt-get from the terminal or all three?

---

### Post by LoopTown on 2013-03-09
Updater alone. Might have something to do with software center not doing anything when I click install (but still making the button inactive). It's total mystery for me that came with whole network problems as such. Still I think it might have something to do with some files in "to be updated" list. Now when theres oly 14 i can try by trial and error.

---

### Post by chili555 on 2013-03-09
Is Synaptic installed? Can you open it, mark all upgrades, click Apply and get them updated that way? We need to figure out if it's a problem with your software sources or the updater itself. Here is what my software sources look like and what I recommend.

---

### Post by LoopTown on 2013-03-12
As said it in the first post, synaptic is the only thing that seems to work quite perfectly in this computer. But what really get's me confused is that both updater and software center stopped working at the same time. So it shouldn't be purely updaters software issue it has to be something connecting them both. Only thing besides sopurces that comes to ming is network again.

---

### Post by chili555 on 2013-03-12
I suggest opening Synaptic and re-installing update-manager and update-manager-core. Then try again. If Synaptic works, then apt sources seems intact.

---

### Post by LoopTown on 2013-03-14
So, did reinstall and the problems are still here. Update manager changed to software updater and now when hanging (stops working but doesn't believe itself to be crashed) doesn't give any errors.

Update manager/software updater says every time I start it "You've stopped checking for updates, updates are available from last check" witch is strange because I haven't stopped anything.

---

### Post by chili555 on 2013-03-14
> **LoopTown said:**
> So, did reinstall and the problems are still here. Update manager changed to software updater and now when hanging (stops working but doesn't believe itself to be crashed) doesn't give any errors.

Update manager/software updater says every time I start it "You've stopped checking for updates, updates are available from last check" witch is strange because I haven't stopped anything.We're pretty far outside my area of expertise. I suggest you ask over on General Help: [http://ubuntuforums.org/forumdisplay.php?f=331](http://ubuntuforums.org/forumdisplay.php?f=331)

You may get some clues running Update Manager from the terminal:```
sudo update-manager
```When I run it, there are no errors, warnings, smoke or sparks.

---

### Post by LoopTown on 2013-03-14
I'll move myself over to general then - but big thanks to You! I can now at least use my computer.

Thank You!

---

