---
title: "Edimax EW-7728In (Ralink RT2860) drops wireless connection and dies until NM restart"
date: 2009-12-21
forum: Networking &amp; Wireless
---

### Post by paakkon3 on 2009-12-21
Hello, newbie here.

I am having a slight bit of trouble with my Edimax EW-7728In wireless nic. It was one of the few draft-N cards with a supported chipset (Ralink RT2860) that I could find and I was really happy when I found out it was recognized out-of-the-box in both Ubuntu 9.04 and 9.10. 

However, there's a very annoying problem with the card. I can connect just fine to my WLAN, and the connection works flawlessly, until it just completely dies. NetworkManager attempts to automatically reconnect, but fails. Other networks fail as well. Restarting network-manager helps (sudo restart network-manager), but only until the connection dies again after a while, which is when I have to restart network-manager again. The disconnection seems to happen faster if there's a lot of network traffic. The problem was less frequent in 9.04 for some reason, but in 9.10 it has become very, very frequent.

The driver seems to generate quite a bit of whine in my dmesg, even when everything is OK:

<snip>
...
[ 5305.207156] ===>rt_ioctl_giwscan. 9(9) BSS returned, data->length = 1500
[ 5425.205180] ===>rt_ioctl_giwscan. 8(8) BSS returned, data->length = 1343
[ 5545.204461] ===>rt_ioctl_giwscan. 8(8) BSS returned, data->length = 1265
...
</snip>

And upon disconnection, I usually get this:

<snip>
...
[ 4972.934688] ERROR!!! RTMPCancelTimer failed, Timer hasn't been initialize!
...
</snip>

And usually I get this message as well:

<snip>
...
[ 4977.937975] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=3)
...
</snip>

Does anyone have any idea what's happening here? Is this a bug in networkManager, since restarting it helps? A bug in rt2860sta? Or is my hardware busted? All ideas are appreciated. 

Thanks.

---

### Post by hugmenot on 2009-12-21
What do NetwokrManager and wpa_supplicant tell when this happens?
Look in /var/log/daemon.log

---

### Post by paakkon3 on 2009-12-22
> **hugmenot said:**
> What do NetwokrManager and wpa_supplicant tell when this happens?
Look in /var/log/daemon.log

Here's the full log, from a few seconds before disconnection, to networkmanager giving up. The CIFS messages are from my smbfs mount. 'Auto depression' is the name of the connection. Zeromus is the name of the box.

```
Dec 22 14:25:05 zeromus wpa_supplicant[1297]: CTRL-EVENT-SCAN-RESULTS
Dec 22 14:25:05 zeromus kernel: [  349.720583] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 930
Dec 22 14:25:46 zeromus wpa_supplicant[1297]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Dec 22 14:25:46 zeromus wpa_supplicant[1297]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Dec 22 14:25:46 zeromus NetworkManager: <info>  (ra0): supplicant connection state:  completed -> disconnected
Dec 22 14:25:46 zeromus kernel: [  390.913362] ERROR!!! RTMPCancelTimer failed, Timer hasn't been initialize!
Dec 22 14:25:46 zeromus NetworkManager: <info>  (ra0): supplicant connection state:  disconnected -> scanning
Dec 22 14:25:51 zeromus wpa_supplicant[1297]: CTRL-EVENT-SCAN-RESULTS
Dec 22 14:25:51 zeromus kernel: [  396.022203] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 766
Dec 22 14:25:56 zeromus kernel: [  401.145305]  CIFS VFS: No response to cmd 46 mid 15594
Dec 22 14:25:56 zeromus kernel: [  401.145313]  CIFS VFS: Send error in read = -11
Dec 22 14:26:01 zeromus NetworkManager: <info>  (ra0): device state change: 8 -> 3 (reason 11)
Dec 22 14:26:01 zeromus NetworkManager: <info>  (ra0): deactivating device (reason: 11).
Dec 22 14:26:01 zeromus NetworkManager: <info>  (ra0): canceled DHCP transaction, dhcp client pid 3736
Dec 22 14:26:01 zeromus NetworkManager: <WARN>  check_one_route(): (ra0) error -34 returned from rtnl_route_del(): Sucess#012
Dec 22 14:26:01 zeromus NetworkManager: <info>  Activation (ra0) starting connection 'Auto depression'
Dec 22 14:26:01 zeromus NetworkManager: <info>  (ra0): device state change: 3 -> 4 (reason 0)
Dec 22 14:26:01 zeromus NetworkManager: <info>  Activation (ra0) Stage 1 of 5 (Device Prepare) scheduled...
Dec 22 14:26:01 zeromus NetworkManager: <info>  Activation (ra0) Stage 1 of 5 (Device Prepare) started...
Dec 22 14:26:01 zeromus NetworkManager: <info>  Activation (ra0) Stage 2 of 5 (Device Configure) scheduled...
Dec 22 14:26:01 zeromus NetworkManager: <info>  Activation (ra0) Stage 1 of 5 (Device Prepare) complete.
Dec 22 14:26:01 zeromus NetworkManager: <info>  Activation (ra0) Stage 2 of 5 (Device Configure) starting...
Dec 22 14:26:01 zeromus NetworkManager: <info>  (ra0): device state change: 4 -> 5 (reason 0)
Dec 22 14:26:01 zeromus NetworkManager: <info>  Activation (ra0/wireless): connection 'Auto depression' has security, and secrets exist.  No new secrets needed.
Dec 22 14:26:01 zeromus avahi-daemon[1091]: Withdrawing address record for 10.0.0.100 on ra0.
Dec 22 14:26:01 zeromus avahi-daemon[1091]: Leaving mDNS multicast group on interface ra0.IPv4 with address 10.0.0.100.
Dec 22 14:26:01 zeromus avahi-daemon[1091]: Interface ra0.IPv4 no longer relevant for mDNS.
Dec 22 14:26:01 zeromus NetworkManager: <info>  Config: added 'ssid' value 'depression'
Dec 22 14:26:01 zeromus NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Dec 22 14:26:01 zeromus NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
Dec 22 14:26:01 zeromus NetworkManager: <info>  Config: added 'psk' value '<omitted>'
Dec 22 14:26:01 zeromus NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Dec 22 14:26:01 zeromus NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Dec 22 14:26:01 zeromus NetworkManager: <info>  Activation (ra0) Stage 2 of 5 (Device Configure) complete.
Dec 22 14:26:01 zeromus NetworkManager: <info>  (ra0): supplicant connection state:  scanning -> disconnected
Dec 22 14:26:01 zeromus NetworkManager: <info>  Config: set interface ap_scan to 1
Dec 22 14:26:01 zeromus NetworkManager: <info>  (ra0): supplicant connection state:  disconnected -> scanning
Dec 22 14:26:06 zeromus wpa_supplicant[1297]: CTRL-EVENT-SCAN-RESULTS
Dec 22 14:26:16 zeromus NetworkManager: <info>  ra0: link timed out.
Dec 22 14:26:16 zeromus wpa_supplicant[1297]: CTRL-EVENT-SCAN-RESULTS
Dec 22 14:26:56 zeromus wpa_supplicant[1297]: last message repeated 4 times
Dec 22 14:27:01 zeromus NetworkManager: <info>  Activation (ra0/wireless): association took too long.
Dec 22 14:27:01 zeromus NetworkManager: <info>  (ra0): device state change: 5 -> 6 (reason 0)
Dec 22 14:27:01 zeromus NetworkManager: <info>  Activation (ra0/wireless): asking for new secrets
Dec 22 14:27:01 zeromus NetworkManager: <info>  Activation (ra0) Stage 1 of 5 (Device Prepare) scheduled...
Dec 22 14:27:01 zeromus NetworkManager: <info>  Activation (ra0) Stage 1 of 5 (Device Prepare) started...
Dec 22 14:27:01 zeromus NetworkManager: <info>  (ra0): device state change: 6 -> 4 (reason 0)
Dec 22 14:27:01 zeromus NetworkManager: <info>  Activation (ra0) Stage 2 of 5 (Device Configure) scheduled...
Dec 22 14:27:01 zeromus NetworkManager: <info>  Activation (ra0) Stage 1 of 5 (Device Prepare) complete.
Dec 22 14:27:01 zeromus NetworkManager: <info>  Activation (ra0) Stage 2 of 5 (Device Configure) starting...
Dec 22 14:27:01 zeromus NetworkManager: <info>  (ra0): device state change: 4 -> 5 (reason 0)
Dec 22 14:27:01 zeromus NetworkManager: <info>  Activation (ra0/wireless): access point 'Auto depression' has security, but secrets are required.
Dec 22 14:27:01 zeromus NetworkManager: <info>  (ra0): device state change: 5 -> 6 (reason 0)
Dec 22 14:27:01 zeromus NetworkManager: <info>  Activation (ra0) Stage 2 of 5 (Device Configure) complete.
Dec 22 14:27:01 zeromus NetworkManager: <info>  Activation (ra0) Stage 1 of 5 (Device Prepare) scheduled...
Dec 22 14:27:01 zeromus NetworkManager: <info>  Activation (ra0) Stage 1 of 5 (Device Prepare) started...
Dec 22 14:27:01 zeromus NetworkManager: <info>  (ra0): device state change: 6 -> 4 (reason 0)
Dec 22 14:27:01 zeromus NetworkManager: <info>  Activation (ra0) Stage 2 of 5 (Device Configure) scheduled...
Dec 22 14:27:01 zeromus NetworkManager: <info>  Activation (ra0) Stage 1 of 5 (Device Prepare) complete.
Dec 22 14:27:01 zeromus NetworkManager: <info>  Activation (ra0) Stage 2 of 5 (Device Configure) starting...
Dec 22 14:27:01 zeromus NetworkManager: <info>  (ra0): device state change: 4 -> 5 (reason 0)
Dec 22 14:27:01 zeromus NetworkManager: <info>  Activation (ra0/wireless): access point 'Auto depression' has security, but secrets are required.
Dec 22 14:27:01 zeromus NetworkManager: <info>  (ra0): device state change: 5 -> 6 (reason 0)
Dec 22 14:27:01 zeromus NetworkManager: <info>  Activation (ra0) Stage 2 of 5 (Device Configure) complete.
Dec 22 14:27:01 zeromus NetworkManager: <info>  Activation (ra0) Stage 1 of 5 (Device Prepare) scheduled...
Dec 22 14:27:01 zeromus NetworkManager: <info>  Activation (ra0) Stage 1 of 5 (Device Prepare) started...
Dec 22 14:27:01 zeromus NetworkManager: <info>  (ra0): device state change: 6 -> 4 (reason 0)
Dec 22 14:27:01 zeromus NetworkManager: <info>  Activation (ra0) Stage 2 of 5 (Device Configure) scheduled...
Dec 22 14:27:01 zeromus NetworkManager: <info>  Activation (ra0) Stage 1 of 5 (Device Prepare) complete.
Dec 22 14:27:01 zeromus NetworkManager: <info>  Activation (ra0) Stage 2 of 5 (Device Configure) starting...
Dec 22 14:27:01 zeromus NetworkManager: <info>  (ra0): device state change: 4 -> 5 (reason 0)
Dec 22 14:27:01 zeromus NetworkManager: <info>  Activation (ra0/wireless): access point 'Auto depression' has security, but secrets are required.
Dec 22 14:27:01 zeromus NetworkManager: <info>  (ra0): device state change: 5 -> 9 (reason 7)
Dec 22 14:27:01 zeromus NetworkManager: <info>  Activation (ra0) failed for access point (depression)
Dec 22 14:27:01 zeromus NetworkManager: <info>  Marking connection 'Auto depression' invalid.
Dec 22 14:27:01 zeromus NetworkManager: <info>  Activation (ra0) failed.
Dec 22 14:27:01 zeromus NetworkManager: <info>  Activation (ra0) Stage 2 of 5 (Device Configure) complete.
Dec 22 14:27:01 zeromus NetworkManager: <info>  (ra0): device state change: 9 -> 3 (reason 0)
Dec 22 14:27:01 zeromus NetworkManager: <info>  (ra0): deactivating device (reason: 0).
Dec 22 14:27:06 zeromus wpa_supplicant[1297]: CTRL-EVENT-SCAN-RESULTS

```

Edit: This is from syslog. Daemon.log has the same bits from wpa_supplicant and networkmanager, but is missing the kernel messages.

---

### Post by hugmenot on 2009-12-22
Maybe it&#8217;s giving up out of depression?

From my uneducated guess the driver is crapping out below NM and wpa_supplicant.

There are two bugs filed that seem relevant:
[https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/344022](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/344022)
[https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/480477](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/480477)

But I didn&#8217;t read them. No idea if there&#8217;s a fix in sight.

EDIT: One of them was a dupe of this bug, which is marked as FIX RELEASED:
[https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/339891](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/339891)

---

### Post by paakkon3 on 2009-12-22
Thanks, changing the SSID made it work! ;)

Seriously though, thanks for digging up those bugs. [https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/480477](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/480477) kind of described my situation, but it still doesn't say anything about needing to restart NetworkManager.

I fiddled around with my AP and found out that the card doesn't appear to do wireless-N after all. When I configured my AP to accept only wireless-N connections, the card does see the network, but cannot connect to it. I also tried disabling the 5GHz band completely (the card is a 2.4GHz one) and pumping up the beacon interval. Neither helped.

Anything else I should try? Or should I just report a new bug for this?

---

### Post by hugmenot on 2009-12-22
If you look at the last bug I cited and expand "view all comments" at the bottom they talk about a fix. Did you see this? I haven&#8217;t read all that for lack of time.

---

### Post by paakkon3 on 2009-12-22
> **hugmenot said:**
> If you look at the last bug I cited and expand "view all comments" at the bottom they talk about a fix. Did you see this? I haven’t read all that for lack of time.

Yes, I saw the fix. The ralink driver download link is broken, so I couldn't test the fix. I guess I'll try and hunt down the latest ralink driver and test whether the problem persists with it. Edimax offer an older driver for some reason. Maybe downgrading is an option too. I'll experiment.

---

### Post by paakkon3 on 2009-12-22
All right. Here's an update. Updating the driver to the latest version (2.2.0.0) didn't help with the original problem. However, with the latest driver, wireless-N now works.

In case someone else wants to do the upgrade, here's what I did:


[LIST=1]
[*]Grab the 2.2.0.0 driver from [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)
[*]Grab a patch from [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/396945](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/396945) ([http://launchpadlibrarian.net/32746268/2009_0918_RT2860_Linux_STA_v2.2.0.0-kernel2.6.31-0.patch](http://launchpadlibrarian.net/32746268/2009_0918_RT2860_Linux_STA_v2.2.0.0-kernel2.6.31-0.patch)) - this is needed because the linux kernel in Ubuntu 9.10 is incompatible with the vanilla ralink driver.
[*]Unpack the driver
[*]Apply patch: patch -p1 < 2009_0918_RT2860_Linux_STA_v2.2.0.0-kernel2.6.31-0.patch
[*]Modify os/linux/config.mk to enable wpa_supplicant use: sed -i 's/^HAS_WPA_SUPPLICANT=n/HAS_WPA_SUPPLICANT=y/;s/^HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n/HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y/' os/linux/config.mk
[*]sudo make
[*]sudo make install
[*]sudo ifconfig ra0 down
[*]sudo rmmod rt2860sta
[*]sudo modprobe rt2860sta
[*]sudo ifconfig ra0 up
[*]sudo restart network-manager
[/LIST]
Word of warning: NetworkManager has been acting up even more often after this update. And for some reason I have to bring the ra0 interface up manually after each reboot now.

So anyway, since this didn't help me much in my original problem, I'll try downgrading the driver next.

Edit: I just realized that downgrading to the Edimax suggested version won't do any good. The exact same version (1.8.0.0) comes with Ubuntu. All help would still be very appreciated.

---

### Post by paakkon3 on 2009-12-22
Okay, now this feels like a shameless bump of my own thread, but I ran into different kind of trouble while experimenting. I installed wicd because I still couldn't shake the idea of NetworkManager being buggy and causing all this. Now, wicd appears to be even more useless than NM. It fails to get an IP address from the AP's DHCP, and if I try to set the IP address manually, wicd tells me it cannot establish a connection with the AP. So now I am kind of stuck. Does anyone know how to fix wicd?

---

### Post by finni on 2010-02-01
Has anyone tried the new 2.3.0.0 drivers if they are any better?

[http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)

---

### Post by rusart on 2010-02-03
> **finni said:**
> Has anyone tried the new 2.3.0.0 drivers if they are any better?

[http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)

Yes. It works (just installed), but i don't know what about problem in this thread, yet.

UPD: Looks like fixed for me. Reconnect automaticaly after lost connection.

---

### Post by lvgandhi on 2010-02-11
When I tried to patch for Kubuntu karmic, I get error as follows. 
lvgandhi@lvgvaio:~/Downloads/2010_01_29_RT2860_Linux_STA_v2.3.0.0$ patch -p1 -R < ../2009_0918_RT2860_Linux_STA_v2.2.0.0-kernel2.6.31-0.patch
patching file os/linux/rt_linux.c
Hunk #1 FAILED at 1683.
Hunk #2 succeeded at 1743 with fuzz 2 (offset 11 lines).
1 out of 2 hunks FAILED -- saving rejects to file os/linux/rt_linux.c.rej

Any solution please

---

### Post by Rebelli0us on 2010-08-14
I bought an EDIMAX EW-7728IN because they said here..

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

...that it works in Linux. It only connected once when running the Desktop CD, and now it will not connect at all. It's also flaky in Windows.

So who can we believe? Which wireless adapter really works under Linux?

---

