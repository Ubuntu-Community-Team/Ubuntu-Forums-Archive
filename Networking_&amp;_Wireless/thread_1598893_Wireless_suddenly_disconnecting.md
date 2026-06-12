---
title: "Wireless suddenly disconnecting"
date: 2010-10-17
forum: Networking &amp; Wireless
---

### Post by allandk78 on 2010-10-17
The problem is the wireless connection suddenly disappearing after it has been used for a while - it could be after an hour of after 10 minutes of usage. I have experienced this on both 10.04 and on the current 10.10 installation of Ubuntu Desktop on my Dell Vostro 3700 laptop. 

I have a netbook Asus 901 with Ubuntu 9.04 which is stable as a rock. No issues of this kind. On another laptop I have 10.10 remix, which also works very well. 

The wireless hardware on the Dell Vostro 3700 is the following:

> 12:00.0 Network controller [0280]: Broadcom Corporation BCM43224 802.11a/b/g/n [14e4:4353] (rev 01)

I'm using an additional driver for it: "Broadcom STA Wireless Driver"

> 
uname -a
Linux allan-laptop 2.6.35-22-generic #34-Ubuntu SMP Sun Oct 10 09:26:05 UTC 2010 x86_64 GNU/Linux


The system log is attached as a txt file. Here is a snip of when it fails - but why is the good question:

> Oct 17 10:41:52 allan-laptop wpa_supplicant[1050]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Oct 17 10:41:52 allan-laptop NetworkManager[1010]: <info> (eth1): supplicant connection state:  completed -> disconnected
Oct 17 10:41:52 allan-laptop NetworkManager[1010]: <info> (eth1): supplicant connection state:  disconnected -> scanning
Oct 17 10:42:01 allan-laptop wpa_supplicant[1050]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Oct 17 10:42:01 allan-laptop NetworkManager[1010]: <info> (eth1): supplicant connection state:  scanning -> disconnected
Oct 17 10:42:04 allan-laptop NetworkManager[1010]: <info> (eth1): supplicant connection state:  disconnected -> scanning
Oct 17 10:42:08 allan-laptop NetworkManager[1010]: <info> (eth1): device state change: 8 -> 3 (reason 11)
Oct 17 10:42:08 allan-laptop NetworkManager[1010]: <info> (eth1): deactivating device (reason: 11).
Oct 17 10:42:08 allan-laptop NetworkManager[1010]: <info> (eth1): canceled DHCP transaction, DHCP client pid 2041
Oct 17 10:42:08 allan-laptop avahi-daemon[1009]: Withdrawing address record for 192.168.1.7 on eth1.
Oct 17 10:42:08 allan-laptop avahi-daemon[1009]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.7.
Oct 17 10:42:08 allan-laptop avahi-daemon[1009]: Interface eth1.IPv4 no longer relevant for mDNS.


When searching for the wireless network on startup sometimes it doesn't show a start, but all the other networks in the neighborhood does. I have to connect manually to a "hidden wireless network" to make it work.

Please Help and let me know if you need more information to crack this nut.

Thanks.

---

### Post by Quan-Time on 2010-10-17
I just upgraded 4 days ago from 10.04 x64 to 10.10 x64 and my wifi is giving me huge grief.
My wifi was rock solid, NEVER gave me issues, now i experience constant drop outs, and sometimes it wont even work.  Only a reboot will fix it.


```

:~$ uname -a
Linux allenkey 2.6.35-22-generic #34-Ubuntu SMP Sun Oct 10 09:26:05 UTC 2010 x86_64 GNU/Linux

```
```


:~$ lspci
00:00.0 Host bridge: nVidia Corporation MCP79 Host Bridge (rev b1)
00:00.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.0 ISA bridge: nVidia Corporation MCP79 LPC Bridge (rev b2)
00:03.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.2 SMBus: nVidia Corporation MCP79 SMBus (rev b1)
00:03.3 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.5 Co-processor: nVidia Corporation MCP79 Co-processor (rev b1)
00:04.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:04.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
00:09.0 PCI bridge: nVidia Corporation MCP79 PCI Bridge (rev b1)
00:0b.0 SATA controller: nVidia Corporation MCP79 AHCI Controller (rev b1)
00:0c.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:15.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:16.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
02:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9600M GT] (rev a1)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
04:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

```

```


:~$ sudo dmesg | grep ath9k
[sudo] password for : 
[   12.064690] ath9k 0000:04:00.0: PCI INT A -> Link[LN4A] -> GSI 18 (level, low) -> IRQ 18
[   12.064698] ath9k 0000:04:00.0: setting latency timer to 64
[   12.784862] phy0: Selected rate control algorithm 'ath9k_rate_control'
[   12.785412] Registered led device: ath9k-phy0::radio
[   12.785431] Registered led device: ath9k-phy0::assoc
[   12.785444] Registered led device: ath9k-phy0::tx
[   12.785459] Registered led device: ath9k-phy0::rx
[ 9151.982390] ath9k 0000:04:00.0: PCI INT A disabled
[ 9153.920435] ath9k 0000:04:00.0: PCI INT A -> Link[LN4A] -> GSI 18 (level, low) -> IRQ 18

```

Im fully aware that the Atheros (ath9k) can cause issues.  The fact it worked fine in lucid, why is it so much of an issue in Maverick ??

---

### Post by Quan-Time on 2010-10-17
one thing ill also mention, my onboard gbit eth0 always gave me grief with 9.10 karmic.  It NEVER went above 10/100, and only transfered at 10meg/sec to my file server.  Karmic instantly fixed this and i was able to get 38mb/s constant (limit of this laptop hdd).

Now 10.10 maverick is back to the old 9.10 karmic problems.  Its not detecting at gbit speeds, only 10/100.

If i could downgrade, i would.  I dont want to do a full re-install just yet, but im VERY tempted to do it just for this networking issues.

---

### Post by SilentSeven on 2010-10-17
I am having a similar problem on 10.10 with a Broadcom based wireless card.  Worked OK on 9.x.  

Problem appears to be at least partially related to load.  I can create disconnects on demand with a large file download, video stream or similar.   I can generally recover by deactivating the wireless network from the GUI and re-activating.

I'll see if I can document the problem in a later post.  Not a hard core unix guy; helpful if someone can list the commands they'd like me to run.  

Thanks!

Jeff

---

### Post by Quan-Time on 2010-10-18
OK.. ill paste my post here to another thread which has a similar thing going on.

[http://linuxwireless.org/en/users/Download](http://linuxwireless.org/en/users/Download)

I installed those drivers, AND!! changed my wifi channel from 11 to 1 and power cycled my wifi router (both, i have 2, one which handles my local network and DSL2 duties, and another one on my roof, mikrotek rb133, which connects to a local wifi community, and bridged between the 2 networks), and all came good.

Im not too sure which was the issue here.  My network (cable eth0) also works at true gbit speed now when plugged in.  Not sure why but its something to note.

So basically everything for me is working perfectly again.  I hope others get some success soon !!

---

### Post by moore.bryan on 2010-10-21
Known bug ([https://bugs.launchpad.net/linux/+bug/518818]("https://bugs.launchpad.net/linux/+bug/518818")), that is supposedly fixed, but still is affecting me.

---

### Post by indelible on 2010-11-08
Getting weird disconnects on HP Mini 311 after clean install of 10.10. netbook remix.  It seemed to work well for a little while but now it's disconnecting seconds after connecting, and gets stuck in some kind of loop when reconnecting.  Connection is rock solid in XP or 7.  Pretty frustrating issue on a netbook especially since I don't have an extra ethernet cable to use to trouble shoot on the machine itself, I have to unplug my desktop to even get syslogs like the following off it. 

```
Nov  8 15:39:18 311 NetworkManager[987]: <info> Activation (wlan0) starting connection 'Compu-Global-Hyper-Mega-Net'
Nov  8 15:39:18 311 NetworkManager[987]: <info> (wlan0): device state change: 3 -> 4 (reason 0)
Nov  8 15:39:18 311 NetworkManager[987]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Nov  8 15:39:18 311 NetworkManager[987]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Nov  8 15:39:18 311 NetworkManager[987]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Nov  8 15:39:18 311 NetworkManager[987]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Nov  8 15:39:18 311 NetworkManager[987]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Nov  8 15:39:18 311 NetworkManager[987]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Nov  8 15:39:18 311 NetworkManager[987]: <info> Activation (wlan0/wireless): connection 'Compu-Global-Hyper-Mega-Net' has security, and secrets exist.  No new secrets needed.
Nov  8 15:39:18 311 NetworkManager[987]: <info> Config: added 'ssid' value 'Compu-Global-Hyper-Mega-Net'
Nov  8 15:39:18 311 NetworkManager[987]: <info> Config: added 'scan_ssid' value '1'
Nov  8 15:39:18 311 NetworkManager[987]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Nov  8 15:39:18 311 NetworkManager[987]: <info> Config: added 'psk' value '<omitted>'
Nov  8 15:39:18 311 NetworkManager[987]: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Nov  8 15:39:18 311 NetworkManager[987]: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Nov  8 15:39:18 311 NetworkManager[987]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Nov  8 15:39:18 311 NetworkManager[987]: <info> Config: set interface ap_scan to 1
Nov  8 15:39:18 311 NetworkManager[987]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Nov  8 15:40:19 311 NetworkManager[987]: <warn> Activation (wlan0/wireless): association took too long.
Nov  8 15:40:19 311 NetworkManager[987]: <info> (wlan0): device state change: 5 -> 6 (reason 0)
Nov  8 15:40:19 311 NetworkManager[987]: <warn> Activation (wlan0/wireless): asking for new secrets
Nov  8 15:40:19 311 NetworkManager[987]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Nov  8 15:40:19 311 NetworkManager[987]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Nov  8 15:40:19 311 NetworkManager[987]: <info> (wlan0): device state change: 6 -> 4 (reason 0)
Nov  8 15:40:19 311 NetworkManager[987]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Nov  8 15:40:19 311 NetworkManager[987]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Nov  8 15:40:19 311 NetworkManager[987]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Nov  8 15:40:19 311 NetworkManager[987]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Nov  8 15:40:19 311 NetworkManager[987]: <info> Activation (wlan0/wireless): connection 'Compu-Global-Hyper-Mega-Net' has security, and secrets exist.  No new secrets needed.
Nov  8 15:40:19 311 NetworkManager[987]: <info> Config: added 'ssid' value 'Compu-Global-Hyper-Mega-Net'
Nov  8 15:40:19 311 NetworkManager[987]: <info> Config: added 'scan_ssid' value '1'
Nov  8 15:40:19 311 NetworkManager[987]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Nov  8 15:40:19 311 NetworkManager[987]: <info> Config: added 'psk' value '<omitted>'
Nov  8 15:40:19 311 NetworkManager[987]: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Nov  8 15:40:19 311 NetworkManager[987]: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Nov  8 15:40:19 311 NetworkManager[987]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Nov  8 15:40:19 311 NetworkManager[987]: <info> (wlan0): supplicant connection state:  scanning -> disconnected
Nov  8 15:40:19 311 NetworkManager[987]: <info> Config: set interface ap_scan to 1
Nov  8 15:40:21 311 NetworkManager[987]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Nov  8 15:40:34 311 NetworkManager[987]: <warn> (wlan0): link timed out.


```

---

### Post by indelible on 2010-11-08
friend suggested I install "wicd" and that seems to have somehow solved the problem, though my understanding is installing that with aptitude should have disabled the seemingly broken default network manager package, which it did not.  

edit: removed network-manager-gnome and network-manager manually with aptitude, rebooted, wicd is still connecting to wireless fine. What it is that makes wicd "just work" when the default network manager fails in an extremely annoying way I have no idea, but if someone would like some logs or something to help resolve this bug which seems to have been around for a while, let me know what to post.

---

### Post by brocos on 2010-11-21
I have the same problem, my wireless keeps disconnecting all the time after having installed ubuntu 10.10. It would work for a while and then I would need to do a restart to restore the connection. I have tried installing wicd as suggested in the previous entry but it didn't work. There are several fixes suggested but nobody seems to be sure about what is casing this. Does anybody have more information about this issue?

---

### Post by guest5 on 2010-11-21
Same here, soooo ~ I was running ubuntustudio; I reinstalled Ubuntu 32 bit, then installed the metapackages for studio, now it works. And has been for a day now without issue.

---

### Post by .dave on 2010-11-23
I'm getting issues as well.

This seems to be a big problem for people at the moment. It's a real shame as I normally rate Ubuntu highly for people looking for a Windoze alternative. But  I can't recommend it to the 'infirm' if they are going to have constant battles to get their internet working.

Hope to see a fix soon.

--------------------------------------------------------------------------------

Has anyone tried this solution with any success? [http://edtake.wordpress.com/2010/05/10/ubuntu-lucid-lynx-wireless-keep-dropping/](http://edtake.wordpress.com/2010/05/10/ubuntu-lucid-lynx-wireless-keep-dropping/)

> **[ubuntu] Lucid Lynx Wireless Keep Dropping (updated)]("http://edtake.wordpress.com/2010/05/10/ubuntu-lucid-lynx-wireless-keep-dropping/")**

  				 					10 					05 					2010 				 					 				 					After enduring the endless wireless disconnection after  upgrading to Ubuntu 10.04 (Lucid Lynx) I have finally found the  solution!
 The symptoms I was seeing is as such:
 
[LIST=1]
[*]connected
[*]after using for 5 minutes to 10 minutes, the wireless network manager get disconnected
[*]only wireless connection selectable is the last network you connect to
[*]unable to re-connect, even after 10 minutes
[*]you must disable the wireless and enable it before you can try to reconnect&#8230;
[*]then back to step 1
[/LIST]
 The steps below worked for me [IMG]http://s2.wp.com/wp-includes/images/smilies/icon_smile.gif?m=1285254906g[/IMG] 
 
[LIST]
[*] *sudo gedit /etc/NetworkManager/nm-system-settings.conf*
[*] set the &#8220;[ifupdown] managed=false&#8221; to true.
[/LIST]
 Although the above changes reduced the frequency of the wireless  drop, but I am still facing it. After thinking it around a bit more,  it&#8217;s more stable now. Below are what I have done:
 
[LIST]
[*]*sudo gedit /etc/NetworkManager/nm-system-settings.conf*
[/LIST]
 
[LIST]
[*]Changed the file to:
[/LIST]
 [INDENT][main]
plugins=ifupdown,keyfile
 [ifupdown]
managed=true
 [ifdown]
managed=true
 [ifup]
managed=true
[/INDENT] Good luck to you! And have fun with Lucid Lynx. Let me know if this  works or if there are other better fix!
 *Added on June 28, 2010:*
 *With with the fixes above, it has only lessen the problem on my  machine and not totally eliminate it. Thanks for the comments on trying  out wicd, which i did give it a try. BUT although the wireless  connection didn&#8217;t drop at all for the 2 days which i have been using it,  i see a cap on the wireless transmission rate of 60KB/s (even after  trying &#8220;sudo iwconfig wlan0 rate 54M&#8221;, which is not the problem*[I]).  This is not acceptable to me, which is why i sent back to using gnome  network manager, but for those of you who want to try out wicd, below  are the commands:
[/I]
 [INDENT]*sudo apt-get install wicd*
 [I]sudo apt-get remove network-manager
[/I]
[/INDENT] *Drop me a message if you have a solution to the transmission rate cap!*
 				


---

Good luck and hopefully we'll all find a solution eventually.

---

### Post by moore.bryan on 2010-11-23
I've taken to downloading/installing the bleeding-edge [compat-wireless]("http://wireless.kernel.org/en/users/Download#Requirements_for_bleeding_edge"), which makes things better for me.

---

### Post by Dankstar on 2010-12-06
Thanks to this thread I tried installing the package **linux-backports-modules-compat-wireless-2.6.36-2.6.35-23-generic** and so far the disconnection, low speed connection and packet loss nonsense I was having with my ath9k seems to have gone.  It's now 54Mbit and hasn't presented a reconnection message or asked for a password in the last 24 hours.   Hopefully it'll stay this way.  I am using Kubuntu 10.10.

---

