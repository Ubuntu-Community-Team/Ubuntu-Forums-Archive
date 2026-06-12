---
title: "Troubleshooting a Linksys WRT54G router"
date: 2009-05-17
forum: Networking &amp; Wireless
---

### Post by Old *ix Geek on 2009-05-17
The router I have now is the first one I've ever had, so I have no previous experience!

I recently started having problems with wireless on my HP dv6000 laptop--with the infamous Broadcom BCM43xx issue--but I had just upgraded from 8.10 to 9.04 and assumed it was related to that.

Due to that and other problems I got sick of trying to make Jaunty work, so I wiped it and did a fresh install of 8.10.  Still no wireless.  Hmmmmm... :confused:

Then I realized that a desktop is also no longer connecting wirelessly--most of the time.  At least with it, every once in a while it sees the wireless networks in my area (mine, my neighbors) and even occasionally connects to mine.  But for the most part it's not working either.

The laptop doesn't even see any wireless networks, although its wireless light is blue which indicates that it's working.

I have NO IDEA how to troubleshoot a router.  It's a Linksys WRT54G and I've had it for just under three years.  I've tried resetting it, unplugging it, etc., but to no avail.  I tried using the Linksys site but EVERYTHING assumes you're using windoze or Mac.

Right now I have everything hard-wired to the router but would REALLY like to get back to wireless.  Any advice will be most appreciated.

---

### Post by puppywhacker on 2009-05-17
I have mixed feelings about the wrt54g's buildquality. I experienced wireless connection issues with mine, so I decommisioned it in favor of an wag300n, which was a lot more reliable. (YMMV)

the BCM43xx has new and old drives. which one are you using?
[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

the linksys management page at [http://192.168.1.1/](http://192.168.1.1/) mainly accessible via wired connections.

The command iwconfig and iwlist should help you find, attach and troublehoot your connection. mainly look at the signal strength and dropped packets
```

iwconfig wlan0
tail -50 /var/log/messages

```

---

### Post by superprash2003 on 2009-05-18
have you looked at system->admin->hardware drivers ?

---

### Post by Old *ix Geek on 2009-05-19
> **superprash2003 said:**
> have you looked at system->admin->hardware drivers ?I'm using the correct driver, B43, but even tried STA just to see if that changed anything. It didn't.  I definitely have b43-fwcutter installed and it's the newest version.

iwconfig wlan0 shows:
```
wlan0     IEEE 802.11bg  ESSID:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Tx-Power=27 dBm
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

and /var/log/messages shows:
```
May 19 12:10:02 HPLaptop -- MARK --                                                                                           
May 19 12:30:02 HPLaptop -- MARK --                                                                                           
May 19 12:48:49 HPLaptop kernel: [ 9635.107019] input: b43-phy0 as /devices/virtual/input/input11                             
May 19 12:48:49 HPLaptop kernel: [ 9635.365252] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)             
May 19 12:48:49 HPLaptop kernel: [ 9635.508578] Registered led device: b43-phy0::tx                                           
May 19 12:48:49 HPLaptop kernel: [ 9635.510457] Registered led device: b43-phy0::rx                                           
May 19 12:48:49 HPLaptop kernel: [ 9635.510978] Registered led device: b43-phy0::radio                                        
May 19 12:48:49 HPLaptop kernel: [ 9635.536337] ADDRCONF(NETDEV_UP): wlan0: link is not ready                                 
May 19 12:48:50 HPLaptop kernel: [ 9636.120093] b43-phy0: Radio hardware status changed to DISABLED                           
May 19 12:48:50 HPLaptop kernel: [ 9636.168041] b43-phy0: Radio turned on by software                                         
May 19 12:48:50 HPLaptop kernel: [ 9636.168049] b43-phy0: The hardware RF-kill button still turns the radio physically off. Press the button to turn it on.                                                                                                 
May 19 13:10:02 HPLaptop -- MARK --                                                                                           
May 19 13:30:02 HPLaptop -- MARK --
May 19 13:50:02 HPLaptop -- MARK --
May 19 13:54:26 HPLaptop kernel: [13572.662604] input: b43-phy0 as /devices/virtual/input/input12
May 19 13:54:27 HPLaptop kernel: [13572.932026] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
May 19 13:54:27 HPLaptop kernel: [13573.086128] Registered led device: b43-phy0::tx
May 19 13:54:27 HPLaptop kernel: [13573.086371] Registered led device: b43-phy0::rx
May 19 13:54:27 HPLaptop kernel: [13573.086555] Registered led device: b43-phy0::radio
May 19 13:54:27 HPLaptop kernel: [13573.112369] ADDRCONF(NETDEV_UP): wlan0: link is not ready
May 19 13:54:27 HPLaptop kernel: [13573.684028] b43-phy0: Radio hardware status changed to DISABLED
```

(I have no idea what the references to "radio" are!)

---

### Post by chili555 on 2009-05-19
> The hardware RF-kill button still turns the radio physically off. Press the button to turn it on.That means there is a switch or key combination on your laptop that turns the wireless radio on and off. It has been nudged to off. Nudge it on.> I have mixed feelings about the wrt54g's buildquality. I experienced wireless connection issues with mine, so I decommisioned itMe, too.

---

### Post by Old *ix Geek on 2009-05-19
> **chili555 said:**
> That means there is a switch or key combination on your laptop that turns the wireless radio on and off. It has been nudged to off. Nudge it on.Thanks, but you missed the parts where I said:
```
The laptop doesn't even see any wireless networks, although
**its wireless light is blue which indicates that it's working**.
```
and
```
Then I realized that [b]a desktop is also no longer connecting
wirelessly[/b]--most of the time. At least with it, every once in a
while it sees the wireless networks in my area (mine, my neighbors)
and even occasionally connects to mine. But for the most part it's
not working either.
```

It's not just the laptop, and on the laptop the wireless switch (it's a slider, actually) is definitely in the 'on' position.

---

### Post by chili555 on 2009-05-19
> you missed the parts where I said:Indeed, I did. Sorry.

---

### Post by Old *ix Geek on 2009-05-20
> **chili555 said:**
> Indeed, I did. Sorry.

No problem--and I didn't mean to sound snitty.  It kind of came out that way, but wasn't meant to.

---

