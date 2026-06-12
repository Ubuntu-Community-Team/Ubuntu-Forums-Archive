---
title: "Netopia 3342 USB ADSL modem on static IP"
date: 2009-04-17
forum: Networking &amp; Wireless
---

### Post by sir_nasty on 2009-04-17
So hopefully the title makes it clear but I've been messing around with this and on google for a few hours now and finally decided to post.  I have the netopia 3342 USB pocket ADSL modem, Dell Mini 9, Ubuntu 8.04.  dmesg now shows the modem, when connected to a phone line it shows the dsl line speed etc but I need to get an interface and configure it to work on a Static IP bridged system.  Any ideas or insight? Thanks in advance

---

### Post by sir_nasty on 2009-04-17
On a side not I THINK that I got a new interface after I connected it called sms but I can't figure it out for sure.  Any ideas on how to make this work?

---

### Post by sir_nasty on 2009-04-18
for the sake of documentation, after setting up a usb adsl modem with the proper firmware etc (/lib/firmware is where the file should reside) restart the computer then sudo apt-get install br2684ctl and read man br2684 for directions on how to map the atm interface to a useable network interface.  to verify that your firmware is loading correctly restart the computer and type dmesg, it should show the line active and give you some connection statistics.  Hopefully this is helpfull in the future!

---

### Post by ajaysutton on 2009-05-22
Greetings,

Do I usderstand you used br2684ctl to configure the modem for use with the static IP?  I too have an 3342 that I'd like to be able to use with my netbook (Asus 1000he running 9.04) and when I plugged it in, the modem trained up, but I didn't draw an IP.  I'll restart with the device plugged in and see if that helps, but I'd like to hear more about how you made this work.

Thanks in advance.

---

### Post by sir_nasty on 2010-05-12
In my particular situation I use a public static ip not a DHCP assigned one.  You either need to lookup how to configure PPPoE or PPP depending on what particular protocol your ISP uses. 

If you use a Public Static IP in bridge mode this is what I did to get it working:

Sudo apt-get install br2684ctl

br2684ctl -b -c 0 -a 8.35
(-b run it in the background so it dumps back to a command prompt when done, simply putting '&' at the end won't work)
(-c create interface nas0)
(-a VPI.VCI)

ifconfig nas0 up

ifconfig nas0 [static ip]

route add default gw [gateway ip]

usefull command for my situation:

/proc/net/atm/cxacru:0
(returns information about the connection)

---

