---
title: "Help! My wireless is gone!"
date: 2010-03-07
forum: Networking &amp; Wireless
---

### Post by Donny Bahama on 2010-03-07
When I run ifconfig, wlan0 still shows up, but it has no IP address. The (gnome) panel ethernet icon is there, but the wireless icon is gone.

lshw shows:```

   *-network
        description: Wireless interface
        product: PRO/Wireless 4965 AG or AGN Network Connection
        vendor: Intel Corporation
        physical id: 0
        bus info: pci@0000:02:00.0
        logical name: wmaster0
        version: 61
        width: 64 bits
        clock: 33MHz
        capabilities: bus_master cap_list logical ethernet physical wireless
        configuration: broadcast=yes driver=iwl4965 latency=0 module=iwl4965 multicast=yes wireless=IEEE 802.11g
```After running
```
donny@Maui:~$ sudo iwconfig wlan0 essid MaunaLoa commit
Error for wireless request "Commit changes" (8B00) :
    SET failed on device wlan0 ; Operation not supported.

```Then running iwconfig again, I get```

wlan0     IEEE 802.11g  ESSID:"MaunaLoa"  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: <snip>   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```But still no wireless icon in the panel (and no net connectivity).

I should add that everything was working fine until I tried to set up a VirtualBox  (Windows) VM and it had no connectivity. I mucked around like a stupid blind noob trying this and that which I found via this forum and Google. I never did get that to work, and now I've totally broken my wireless.

Please, ***please ***help. :(

---

### Post by chili555 on 2010-03-07
> The (gnome) panel ethernet icon is there, but the wireless icon is gone.Network Manager is designed to prefer the wired ethernet connection to wireless. I can only assume that you are seeing the ethernet symbol because it's connected! If you disconnect the ethernet cable and wait a few moments for NM to recognize a change of state, does the wireless symbol re-appear?

---

### Post by Donny Bahama on 2010-03-07
> **chili555 said:**
> Network Manager is designed to prefer the wired ethernet connection to wireless. I can only assume that you are seeing the ethernet symbol because it's connected! If you disconnect the ethernet cable and wait a few moments for NM to recognize a change of state, does the wireless symbol re-appear?No. The wireless icon was gone long before I plugged in an Ethernet cable. (I only did so because I'd lost my wireless capabilities.)

---

### Post by phischphood on 2010-03-07
I'm having a very similar problem. I have posted in [this]("http://ubuntuforums.org/showthread.php?t=1422520") thread []("http://ubuntuforums.org/showthread.php?t=1422520")

---

### Post by chili555 on 2010-03-07
Can you right-click in the notification area of your panel and add it back? If you don't see it to add, simply add a notification area and then add it.

---

### Post by Donny Bahama on 2010-03-07
> **chili555 said:**
> Can you right-click in the notification area of your panel and add it back? If you don't see it to add, simply add a notification area and then add it.I think the problem is bigger than that. I *do* have a notification area already, and I *do *have nm-applet added to the panel. But nm-applet won't *ever* show the wireless icon (even when I disconnect the ethernet cable), nor will it allow me to connect to any WAPs.

---

### Post by chili555 on 2010-03-07
In iwconfig, do you still have wlan0? What does this tell us?```
sudo iwlist wlan0 scan
cat /etc/network/interfaces
```Thanks.

---

### Post by Donny Bahama on 2010-03-07
> **chili555 said:**
> In iwconfig, do you still have wlan0? What does this tell us?```
sudo iwlist wlan0 scan
cat /etc/network/interfaces
```Thanks.Yes, I do still have wlan0.
```
donny@Maui:~$ sudo iwlist wlan0 scan
[sudo] password for donny: 
wlan0     Scan completed :
          Cell 05 - Address: 00:11:22:33:44:55    <- changed for security reasons
                    ESSID:"MaunaLoa"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=90/100  Signal level=-42 dBm  Noise level=-127 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=000000640ead4144
```
Other cells were found as well, but I deleted them from the listing. MaunaLoa is my AP/wireless router.
```
donny@Maui:~$ cat /etc/network/interfaces
auto wlan0
iface wlan0 inet manual

auto br0
iface br0 inet dhcp
   bridge_ports wlan0 vbox0

# The loopback network interface
auto lo
iface lo inet loopback
```Thanks **so much** for your help!

---

### Post by chili555 on 2010-03-07
Network Manager will not manage any interfaces in *interfaces*. Please do:```
sudo gedit /etc/network/interfaces
```Comment out wlan0:```
[COLOR="Red"]#[/COLOR]auto wlan0
[COLOR="Red"]#[/COLOR]iface wlan0 inet manual

auto br0
iface br0 inet dhcp
   bridge_ports wlan0 vbox0

# The loopback network interface
auto lo
iface lo inet loopback
```Proofread, save and close gedit. Upon reboot, you should see your very healthy wireless in Network Manager.

---

### Post by Donny Bahama on 2010-03-07
> **chili555 said:**
> Network Manager will not manage any interfaces in *interfaces*. Please do:```
sudo gedit /etc/network/interfaces
```Comment out wlan0:```
[COLOR=Red]#[/COLOR]auto wlan0
[COLOR=Red]#[/COLOR]iface wlan0 inet manual

auto br0
iface br0 inet dhcp
   bridge_ports wlan0 vbox0

# The loopback network interface
auto lo
iface lo inet loopback
```Proofread, save and close gedit. Upon reboot, you should see your very healthy wireless in Network Manager.Wow! THANK YOU!!!

I commented out those two lines, saved the file, then tried:
```
donny@Maui:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                      
      Ignoring unknown interface wlan0=wlan0.
```Obviously that didn't work. I'm guessing the restart was mandatory. If so, it will have to wait until I [figure this out]("http://ubuntuforums.org/showthread.php?t=1424109") (or until my rsync completes - whichever comes first.)

---

### Post by chili555 on 2010-03-07
> Ignoring unknown interface wlan0=wlan0.That suggests that wlan0 is still in *interfaces*. Please check your work.

I wouldn't reboot if rsync is going on. As far as I know, if you started rsync within an SSH connection, if you stop SSH, rsync will die. Also, detach the wire when you reboot or NM will connect to ethernet and forget about wireless.

---

### Post by Donny Bahama on 2010-03-07
> **chili555 said:**
> That suggests that wlan0 is still in *interfaces*. Please check your work.I did, and it looks right:
 ```
#auto wlan0
#iface wlan0 inet manual

auto br0
iface br0 inet dhcp
   bridge_ports wlan0 vbox0

# The loopback network interface
auto lo
iface lo inet loopback 

```
I noticed, though, that wlan0 was still referenced in the br0 section. I commented those out (actually I saved the whole thing as interfaces.sav, then deleted all but the loopback section at the bottom) then ran 
```
sudo /etc/init.d/networking restart

```
and now I can see the available wireless networks! I connected to mine, and it seems to have worked, but I can't actually access the internet. At this point, I've inadvertently killed my SSH session, so now I can reboot. I'll let you know how it goes.

Thanks, again, for your help.

---

### Post by Donny Bahama on 2010-03-07
After restarting, my wireless is BACK! Thank you! Thank you! Thank you! Thank you! Thank you! Thank you! ***Thank you!***

---

