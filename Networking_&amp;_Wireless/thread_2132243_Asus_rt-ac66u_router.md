---
title: "Asus rt-ac66u router"
date: 2013-04-04
forum: Networking &amp; Wireless
---

### Post by cutSn8 on 2013-04-04
Hi,
 got a new router which seems to work fine with my TV, ipad, windows machines but I can't log on via wifi from my ubuntu 12.04 amd64.
The router supports b/g/n standards (as well as ac draft), and is supposed to play nice with linux out of the box.
Has anyone had any experience with this or any advice to offer?  

The ubuntu machine is a dell inspiron n5010; the device drivers etc are all standard and previously it worked well with my ageing g router.
When I 'enable wireless' the system just keeps trying unsuccessfully to connect and periodically throwing up an 'authentication required' prompt (I've checked the details I supplied - SSID and password - and these are correct).  This is annoying so for now I've just turned off the wireless and plugged in via cat 6.

Thanks

---

### Post by chili555 on 2013-04-04
Many Linux drivers currently are troubled by 802.11N. Although I don't know which driver you are using, I suggest, as an experiment, that you temporarily turn off N speeds in the router. Now can you connect?

Some routers have a mixed WPA and WPA2 mode which also is troublesome to some Linux drivers. If yours uses such a mode, I suggest WPA2 only. 

Finally, some drivers have a few parameters allowing tweaks to the hardware to driver interface. We can explore that if you'll tell us what driver you are using. Find out from the terminal with:```
sudo lshw -C network
```This takes a few moments, so please be patient.

Find your wireless device and see its driver like this example from my machine:> *-network
       **description: Wireless interface**
       product: Centrino Advanced-N 6200
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 35
       serial: 99:94:6b:99:55:99
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes [COLOR="#FF0000"]driver=iwlwifi[/COLOR] driverversion=3.5.0-26-generic firmware=9.221.4.1 build 25532 ip=192.168.1.120 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
Tell us what the driver is and we'll proceed.

---

### Post by cutSn8 on 2013-04-04
Thanks chili555
- I couldn't see how to turn off wireless n speeds on the router.  (The wireless tab under 'advance settings' has a 'wireless mode' box - the menu includes auto (default), N only, and legacy; I tried 'legacy' without success - this just seems to restrict the channel bandwidth to 20 MHz; there is a 'b/g protection' box ticked by default - I haven't played with that).
- As far as I can tell the security is set to WPA2-personal only.
- The wireless driver reported is this: driver=brcmsmac driverversion=3.5.0-26-generic firmware=N/A

Thanks again

---

### Post by chili555 on 2013-04-05
> The wireless driver reported is this: driver=brcmsmac Uh, oh......

I can't think of a device where *brcmsmac* is the optimum driver. Yours may be one, I just haven't seen one myself. Let's learn more about your device:```
lspci -nn -d 14e4:
```Thanks.

---

### Post by cutSn8 on 2013-04-05
Hi chili555

results are:
12:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)

If you can recommend a better driver that would be great, though the wireless seems to be working now.  Not sure exactly what the problem was, just tried rebooting again and entering all the ssid/login afresh.

thanks

---

### Post by chili555 on 2013-04-05
> the wireless seems to be working now.Then I wouldn't do anything now. Post back if it acts up again.

---

