---
title: "Mixed home network Ubuntu/Windows"
date: 2010-09-11
forum: Networking &amp; Wireless
---

### Post by selvaswami on 2010-09-11
Hi;

I have 4 PC's happily running on a D-link wired router.
Our ISP is Carolina RoadRunner.
Two boxes are my Ubuntu 10.04 boxes, completely up to date.
Two boxes are Windows XP (only until Christmas).

I need to add wireless to this lot for a Windows XP laptop, so I checked the Approved Hardware List for routers that 'work right out of the box' with Ubuntu -- and selected the good ol' Linksys WRT54G, which has four wired ports and wireless as well.

Well, it doesn't wish to speak to the Internet, either from Ubuntu or after running the Windows setup CD per instructions.

I put the D-Link back to do some research and post this.

The only advice Roadrunner gives for Ubuntu is that MTU should be set to 1500, which I had not tried.

Before I try again tomorrow night, has anyone else already been through this, and have some tips?

I do not want to invent the wheel all over again . . .

Thanks for any help;

Selvaswami

---

### Post by chili555 on 2010-09-11
Many people here, including me, have used the WRT54G without any problem. I suggest you shut down all computers. Detach the power cable from your D-link router and then detach the ethernet cable from Carolina Roadrunner.

Install the Linksys router by detaching the power cable; attach the ethernet cable from Carolina Roadrunner. Be sure it is inserted in the port marked for WAN. Plug in the wired ethernet cables from your computers to the LAN ports. Plug in the power cable to the Linksys router and let all the flashing LEDs settle down. Power up any of the computers and see if you can access the internet. If not, from one of the Ubuntu computers, please open a terminal and do:```
ping -c3 192.168.1.1
ping -c3 74.125.67.147
ping -c3 www.google.com
```Copy down the output from each command and post it here. The results will help us know how to proceed next.

---

### Post by CharlesA on 2010-09-11
So you replaced the dlink router with the linksys, right?

You would need to power off the modem and hook up the router to it, then power on the router then the modem.

I've never had to change the MTU on any OS.

---

### Post by kevinatkins on 2010-09-11
Given that you can't connect to the internet, that would suggest a problem with the internet settings on the new Linksys router. I'd double-check that the settings on the new router are identical to those on your older D-Link unit.

If all else fails, you could always simply use the new Linksys unit as a simple wireless bridge - I've done that before with spare wireless routers.

---

### Post by selvaswami on 2010-09-11
Hi, guys;

* Yeah, I looked at getting the DWL-810 from D-Link to do a wireless bridge, but the Linksys router with mixed wired plus wireless was half the price. And I bought it already, so I'm committed to making it go.

* Roadrunner's website gives the 'MTU=1500' setting specifically for Linux setups, so I will add it in tonight.

* Note that powering down the cable modem amounts to unplugging it for 30 seconds, until all the front panel lights go off, then plugging it in again. (It has an internal battery to prevent further powering off than that in less than a hour or so).

Should I leave it off for an hour? Or reset it via the Reset button? The TimeWarner tech told me once that hitting the manual reset button on the back of the cable modem is called 'flushing' it because it dumps all the account settings so that it has to read them again from the home office --and it fails to do this sometimes, requiring a service call to restore them. Meaning, don't do it.


Thanks to everyone for your help. I will try the new router again in a bit, and post the ping results if it fails to connect.

---

### Post by CharlesA on 2010-09-11
You should be able to remove the battery as well. It sounds like the modem might still be "locked on" to the MAC of the DLink router.

With the linksys router hooked up, is anything listed under "status" for WAN or internet?

---

### Post by selvaswami on 2010-09-11
The cable modem Time Warner installed is an ARRIS TM402G/110 which is a VOIP modem.

The User Guide for it says resetting it is done by holding the Reset button in back down until all the front panel lights go out, then releasing. It says it takes about five minutes to get itself back in operation.

I'll try the Reset button first tonight.

---

### Post by CharlesA on 2010-09-11
Good luck. :)

---

### Post by linuxusr50 on 2010-09-12
Just a thought!

DLink uses 192.168.0.X addresses on its LAN side to your computers.  Did you by chance statically program your computers for this range?

The Linksys router will give addresses in the 192.168.1.X range from its LAN side to you computers.  If you statically programmed you IP addresses on your computers you will need to change them to accommodate the Linksys router.

Also as suggested below.  You will need to check your router to make sure you are configured properly to your ISP settings if you are using a bridged broadband modem.

---

### Post by selvaswami on 2010-09-12
No, these computers all get DHCP off the router which is, of course, getting a single IP address off the cable modem.

The D-Link worked out of the box, just plugged it in and done.

---

### Post by CharlesA on 2010-09-12
Did it work with the linksys after resetting the modem?

I'm puzzled. I've tried a few different router on my connection - Dlink, Belkin, Linksys - and all I've had to do is power cycle the modem. I'm using an "aftermarket" modem though - a Linksys, since I didn't feel like renting one from the ISP.

However, I know that my friend has one of those fancy VoIP modems from TCW and it was a major pain to get it to see the router. I believe we had to remove the battery from it and then let it sit for a while.

Anyway, check the WAN settings once you hook everything up and see if it's getting the information from the ISP.

---

### Post by linuxusr50 on 2010-09-12
Check to see if you are getting an IP address from the DLink on you computer with

Linux
```
ifconfig
```

Windows
```
ipconfig
```

If you are try pinging first the router LAN IP and if that works try pinging the ISP IP and gateway.  This will help isolate where the issue is occurring.

---

### Post by selvaswami on 2010-09-12
Hitting the Reset button on the cable modem gave instant results, although the power button never actually went off. The front panel lights went blank, then all lit up, then went down to just Power and Telephone 1.

On booting each PC, web came up without further ado.

Wireless came up, and I tweaked Wireless security without problems.

All is working well.

Thanks again for the advice, everyone!

Selvaswami

---

