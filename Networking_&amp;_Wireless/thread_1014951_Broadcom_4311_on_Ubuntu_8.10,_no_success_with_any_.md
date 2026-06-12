---
title: "Broadcom 4311 on Ubuntu 8.10, no success with any driver"
date: 2008-12-18
forum: Networking &amp; Wireless
---

### Post by r0t on 2008-12-18
Hello, 

having spend most of the day following every guide I could find on the internet I feel I can start a new thread here. I'm trying to install drivers for a Broadcom 4311 wireless card in a HP Compac nx6310 laptop with a clean Ubuntu 8.10 install. And I already erased Windows, so I really need to make this work...

So far I have gone through this: [http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174) (using some program called  bcm43xx-fwcutter) and this ([https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper)#Step%201%20-%20Remove%20any%20existing%20copies%20of%20ndiswrapper%20that%20you%20may%20have](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper)#Step%201%20-%20Remove%20any%20existing%20copies%20of%20ndiswrapper%20that%20you%20may%20have)) using ndiswrapper with every driver that I found any reference to might be working for my card. I have tried trouble shooting using [http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847), and I have also tried to download the Broadcom drivers from [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php), but it refuses to produce any kernel module (is that the word?)

Any help would be appreciated, just tell me what information I need to supply!

Atm any attempt to connect the computer immediately returns a pop-up-window telling be the connection has been closed.

---

### Post by Ayuthia on 2008-12-18
> **r0t said:**
> Hello, 

having spend most of the day following every guide I could find on the internet I feel I can start a new thread here. I'm trying to install drivers for a Broadcom 4311 wireless card in a HP Compac nx6310 laptop with a clean Ubuntu 8.10 install. And I already erased Windows, so I really need to make this work...

So far I have gone through this: [http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174) (using some program called  bcm43xx-fwcutter) and this ([https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper)#Step%201%20-%20Remove%20any%20existing%20copies%20of%20ndiswrapper%20that%20you%20may%20have](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper)#Step%201%20-%20Remove%20any%20existing%20copies%20of%20ndiswrapper%20that%20you%20may%20have)) using ndiswrapper with every driver that I found any reference to might be working for my card. I have tried trouble shooting using [http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847), and I have also tried to download the Broadcom drivers from [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php), but it refuses to produce any kernel module (is that the word?)

Any help would be appreciated, just tell me what information I need to supply!

Atm any attempt to connect the computer immediately returns a pop-up-window telling be the connection has been closed.

Try this first:
```
sudo modprobe -r b43 ssb ndiswrapper wl
sudo modprobe wl
sudo /etc/init.d/networking restart
sudo iwlist scan
```And see if this works. It will try to use the Broadcom STA module that comes with Ubuntu.  If that does not work, you can try the ndiswrapper route:
```
sudo modprobe -r b43 ssb ndiswrapper wl
sudo modprobe ndiswrapper
sudo /etc/init.d/networking restart
sudo iwlist scan
```

If neither work, please post the following:
```
lsmod|grep -e b43 -e ssb -e ndiswrapper -e wl
ndiswrapper -l
lshw -C network
```
That will help us see which modules are loaded, if ndiswrapper likes the current driver, and the last one provides some info about your card and what module it is trying to use.

If it does work, please let us know which one worked and we can then tell you what you need to add to make the changes permanent.

---

### Post by r0t on 2008-12-19
Thanks for taking your time helping!

The wlan0 interface does actually show up in both cases, but it refuses to connect (and doesn't find any networks)

lsmod|grep -e b43 -e ssb -e ndiswrapper -e wl
gives:
```
ssb           40580   1 b44
ndiswrapper  196380   0
usbcore      148848   6 ndiswrapper,usb_storage,libusual,ehci_hcd,uhci_hcd

```

ndiswrapper -l
gives:
```
bcmwl5 : driver installed
        device (14E4:4311) present (alternate driver: ssb)
```

lshw -C network
gives:
```
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: wlan0
       version: 01
       serial: 00:14:a5:a9:18:b3
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.53+Broadcom,10/12/2006, 4.100. latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: e
       bus info: pci@0000:02:0e.0
       logical name: eth0
       version: 02
       serial: 00:15:60:c3:ac:b3
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=64 module=ssb multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: be:e3:98:66:96:66
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
```

---

### Post by Tweakbl on 2008-12-19
Same card in a Dell C640.
The only thing that did not work out of the box was the Dell True Mobile 1470 802.11 a/b/g Wireless Card.
Blacklist the default driver for not working.
CODE:echo 'blacklist bcm43xx'
Then reboot,
After Reboot,Go to ADD/Remove and Update your package info, then do a hardware scan/update.It grabs the fw cutter module and installs it.
Then left click on the network icon,and use.

---

### Post by JamesLavin on 2009-01-05
> **Ayuthia said:**
> Try this first:
```
sudo modprobe -r b43 ssb ndiswrapper wl
sudo modprobe wl
sudo /etc/init.d/networking restart
sudo iwlist scan
```And see if this works. It will try to use the Broadcom STA module that comes with Ubuntu...

If it does work, please let us know which one worked and we can then tell you what you need to add to make the changes permanent.

Thank you, Ayuthia! That solved my problem. I formerly used ndiswrapper (on a Dell 1420) and should apparently stop using it now.

After I upgraded to 8.10, my wireless continued working fine, but I made some manual changes to access an access point while on vacation and then couldn't re-connect after returning home (even after attempting to revert all changes). This solved my problem.

Advice on making this a permanent change would be much appreciated. I see Insperatus elsewhere ([http://ubuntuforums.org/showthread.php?p=6093691](http://ubuntuforums.org/showthread.php?p=6093691)) wrote "echo -e '#ssb workaround, added `date`\ninstall wl modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install wl $CMDLINE_OPTS; modprobe b44;' | sudo tee -a /etc/modprobe.d/wl". Is it something along these lines?

Cheers,

James Lavin

---

### Post by Ayuthia on 2009-01-05
> **JamesLavin said:**
> Thank you, Ayuthia! That solved my problem. I formerly used ndiswrapper (on a Dell 1420) and should apparently stop using it now.

After I upgraded to 8.10, my wireless continued working fine, but I made some manual changes to access an access point while on vacation and then couldn't re-connect after returning home (even after attempting to revert all changes). This solved my problem.

Advice on making this a permanent change would be much appreciated. I see Insperatus elsewhere ([http://ubuntuforums.org/showthread.php?p=6093691](http://ubuntuforums.org/showthread.php?p=6093691)) wrote "echo -e '#ssb workaround, added `date`\ninstall wl modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install wl $CMDLINE_OPTS; modprobe b44;' | sudo tee -a /etc/modprobe.d/wl". Is it something along these lines?

Cheers,

James Lavin

Yes, you are on the right path.  It looks like you don't need the b44 portion because the commands worked without it.  You can use the command that you found and it won't cause any problems or you can use the following:
```
echo -e '#ssb workaround, added `date`\ninstall wl modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install wl;' | sudo tee -a /etc/modprobe.d/wl
```

---

### Post by JamesLavin on 2009-01-10
> **Ayuthia said:**
> Yes, you are on the right path.  It looks like you don't need the b44 portion because the commands worked without it.  You can use the command that you found and it won't cause any problems or you can use the following:
```
echo -e '#ssb workaround, added `date`\ninstall wl modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install wl;' | sudo tee -a /etc/modprobe.d/wl
```

I still haven't tried this because something else weird is going on, and I wanted to watch my system through several reboots.

Doing the modprobe thing ALONE doesn't solve the problem. I then have to also open up System -> Network Configuration and then VIEW my wireless profile (no changes) and click "OK." Doing modprobe alone is insufficient; opening up the wireless profile alone is insufficient. But when I do BOTH, my wireless network comes right up.

Any idea what could cause this extra wrinkle? Should I just apply the fix above and see what happens?

Here's the ugly output after I apply your solution but before I view Network Configuration:

james@jimmy:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          
wlan0: ERROR while getting interface flags: No such device
ioctl[SIOCGIFFLAGS]: No such device
Could not get interface 'wlan0' flags
ioctl[SIOCSIWPMKSA]: No such device
ioctl[SIOCSIWMODE]: No such device
Could not configure driver to use managed mode
ioctl[SIOCGIWRANGE]: No such device
ioctl[SIOCGIFINDEX]: No such device
ioctl[SIOCSIWENCODEEXT]: No such device
ioctl[SIOCSIWENCODE]: No such device
ioctl[SIOCSIWENCODEEXT]: No such device
ioctl[SIOCSIWENCODE]: No such device
ioctl[SIOCSIWENCODEEXT]: No such device
ioctl[SIOCSIWENCODE]: No such device
ioctl[SIOCSIWENCODEEXT]: No such device
ioctl[SIOCSIWENCODE]: No such device
ioctl[SIOCSIWAP]: No such device
ioctl[SIOCGIFFLAGS]: No such device
wpa_supplicant: /sbin/wpa_supplicant daemon failed to start
run-parts: /etc/network/if-pre-up.d/wpasupplicant exited with return code 1
SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
SIOCSIFNETMASK: No such device
wlan0: ERROR while getting interface flags: No such device
Failed to bring up wlan0.

Thanks (again),

James

---

### Post by Ayuthia on 2009-01-10
You might try and see if it works without the sudo /etc/init.d/networking restart portion.  Network Manager is active and will connect automatically.  It usually just takes a few seconds for it to find that the card is active so I tend to have people restart the network.  There is a chance that Network Manager is fighting with the restart so maybe it will just work without it.

As for adding the workaround script, I would hold off on it until we can confirm this part.

EDIT:  Once your system is able to get connected wirelessly, can you let us know if it is using wlan0, eth1, or something else?  If you are not sure, you can confirm this through lshw -C network.

One other thing, did you add info into /etc/network/interfaces?

---

### Post by JamesLavin on 2009-01-12
> **Ayuthia said:**
> You might try and see if it works without the sudo /etc/init.d/networking restart portion. Network Manager is active and will connect automatically.  It usually just takes a few seconds for it to find that the card is active so I tend to have people restart the network.  There is a chance that Network Manager is fighting with the restart so maybe it will just work without it.

You're right about that. I did the modprobe thing and then tried my wifi. No good (as expected). I then viewed my profile in NetworkManager without running "networking restart," and it did indeed connect after a very brief delay.

> As for adding the workaround script, I would hold off on it until we can confirm this part.

EDIT:  Once your system is able to get connected wirelessly, can you let us know if it is using wlan0, eth1, or something else?  If you are not sure, you can confirm this through lshw -C network.

It's strangely eth2. eth0 appears to be the (currently unused) wired connection. Previously (before I removed ndiswrapper), I connected as wlan0.

> One other thing, did you add info into /etc/network/interfaces?

I use a static IP at home, so I did modify this to get 8.04 working. The uncommented section (which I guess is not being used, so I should probably comment it out) is:

auto wlan0
iface wlan0 inet static
address 192.168.1.127
gateway 192.168.1.1
nameservers xxx.xxx.xxx.xxx xxx.xxx.xxx.xxx
netmask 255.255.255.0
wpa-driver wext
wpa-ssid xxxxx
wpa-ap-scan 1
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk XXXXXXXXXXXXXXXXXXXXXXXXXXX 

I've also commented out lines I used to connect using DHCP while on vacation. The commented out lines include eth1 and eth0, which may (?) explain why NetworkManager is using eth2.

Thanks again!

--James

---

### Post by stchman on 2009-01-12
I have had success with using the ndisgtk(GUI front end for ndiswrapper) package.

```
sudo apt-get install ndisgtk
```

Then point it to the Windows .inf file.

---

### Post by Ayuthia on 2009-01-12
> **JamesLavin said:**
> You're right about that. I did the modprobe thing and then tried my wifi. No good (as expected). I then viewed my profile in NetworkManager without running "networking restart," and it did indeed connect after a very brief delay.



It's strangely eth2. eth0 appears to be the (currently unused) wired connection. Previously (before I removed ndiswrapper), I connected as wlan0.



I use a static IP at home, so I did modify this to get 8.04 working. The uncommented section (which I guess is not being used, so I should probably comment it out) is:

auto wlan0
iface wlan0 inet static
address 192.168.1.127
gateway 192.168.1.1
nameservers xxx.xxx.xxx.xxx xxx.xxx.xxx.xxx
netmask 255.255.255.0
wpa-driver wext
wpa-ssid xxxxx
wpa-ap-scan 1
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk XXXXXXXXXXXXXXXXXXXXXXXXXXX 

I've also commented out lines I used to connect using DHCP while on vacation. The commented out lines include eth1 and eth0, which may (?) explain why NetworkManager is using eth2.

Thanks again!

--James

You should be able to use the workaround script with it.  It looks like the problems are with /etc/network/interfaces.  You have listed wlan0 in the file and the system is not able to find it (that is why you are getting the error messages) because your wireless is now eth2.

---

### Post by JamesLavin on 2009-01-12
> **Ayuthia said:**
> You should be able to use the workaround script with it.  It looks like the problems are with /etc/network/interfaces.  You have listed wlan0 in the file and the system is not able to find it (that is why you are getting the error messages) because your wireless is now eth2.

Since I formerly used /etc/network/interfaces, I assumed NetworkManager would simply use that configuration when I switched over from ndiswrapper. But it obviously didn't. So I'll just comment that all out and then apply the fix to make it permanent.

Thanks so much for all your help!

--James

---

### Post by styven on 2009-01-14
Hi there,
Not sure at what point you are now with this but I do not see anywhere that you tried the System-Administration-Hardware drivers option.

I have the same laptop and this all I do every time I do a fresh install from about version 7-10 on.

You should then get the blue indicator light on.

Sadly however in 8-10 I still can't access my wireless network because network-manager keeps changing my password to a really long one, any ideas anyone on that!

I know my hardware is not the problem because I can access my wireless network when I turn off any security.

Steve.

---

