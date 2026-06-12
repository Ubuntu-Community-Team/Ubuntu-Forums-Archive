---
title: "Recommended Wireless NIC?? HELP!!"
date: 2005-12-23
forum: Networking &amp; Wireless
---

### Post by Hangetsu on 2005-12-23
I've tried without success to get either a Microsoft MN510 or NetGear WG111T (both USB wireless cards) to work under Ubuntu.  I know the Microsoft card CAN work, as SUSE 10 picks it up on install;  however, I'm planning to move from 802.11b to 802.11g over the Christmas holiday.

Anyway, I'm going to go ahead an purchase an internal card, and I wanted to know if anyone had a suggestion on a card that works right away, i.e. Ubuntu picks it up and installs all of the drivers during the OS installation.

I really want to go with Ubuntu (particularly since I want to put edubuntu on my daughter's PC), so any suggestions would be GREATLY appreciated.

Thanks!

---

### Post by Lambert on 2005-12-23
the mn510 uses the linux-wlan-ng driver which is not installed by default I believe it's on the disk or if you have access it's in the repositories. 

You can also find it here.

[http://packages.ubuntu.com/breezy/admin/linux-wlan-ng](http://packages.ubuntu.com/breezy/admin/linux-wlan-ng)

After installing it run

```
sudo depmod -a
```

make sure the card is installed and run

```
sudo pcimodules
```

Look for the module in the list then run this to see if driver loaded

```
sudo lsmod  | less
```

if not then 

```
sudo modprobe <driver>
```

replace <driver> with name of driver and no <> are in the command

If it's not working with above try a reboot.

There is also a known bug reported by azz about this driver. NOt sure if it affects you as I don't know much about it but you can look for posts by him as he's linked to his comments a few times.

There's a wireless trouble shooting guide link in my signature see if that helps any.

And last, if you want to buy a new card, I have very little experience witha  mini pci card but I personally like devices with the atheros chipset. 

[http://madwifi.org/wiki/Compatibility](http://madwifi.org/wiki/Compatibility)

---

### Post by Hangetsu on 2005-12-23
I'm trying to ease my way into the world of Linux, so I'm trying to find something that Ubuntu would recognize and load "out-of-the-box", so to speak.  SUSE 10 found my usb wireless NIC during load and I had internet access immediately when I first logged in.  I don't know if that's possible with Ubuntu, but given the raves I've seen with its ease of use I'd almost assume it would have similar functionality.

---

### Post by Hangetsu on 2005-12-23
Oh, and Lambert -- Thanks in advance for your help thus far (on this and my other thread).  I know I'll get Ubuntu working, its just a matter of the learning curve.  I appreciate the help!

---

### Post by noigeaR on 2005-12-23
a wireless solution that works "out of the box" for all operating systems without installing any drivers at all is a **wireless ethernet bridge**. i use a linksys wet54g with ubuntu and it works great. you just connect the computer to the bridge with via ethernet. from the point of view of your computer it's like you're directly connected to the access point via ethernet. the wireless connection is transparent. set-up and configuration is done with a web frontend.
a very nice thing is, if you connect the wireless bridge to a hub or switch, then all computers connected to this hub/switch will automatically have wireless access. this even works for ethernet printers or game consoles with ethernet port. the only drawback is that wireless ethernet bridges are more expensive than a wireless usb adapter (and they're a bit bigger too).
some examples of wireless ethernet bridges are *linksys wet54g*, *linksys wet54gs5* (with built-in 5 port switch), *netgear wge101* or *zyxel g-405*.

---

### Post by Hangetsu on 2005-12-23
Update:

I bought a Netgear WG311v3, and using ndiswrapper have it working perfectly, THANK YOU!

I do have a question on how WPA is used once I upgrade to an 802.11g router, but I'll make a new thread for that (I only saw a WEP option for the NIC).

---

### Post by Lambert on 2005-12-23
If you're using ndiswrapper and want wpa support look at this. Not sure of your question but hope this helps.

[https://wiki.ubuntu.com/forum/hardware/ndiswrapperWithWPA](https://wiki.ubuntu.com/forum/hardware/ndiswrapperWithWPA)

---

### Post by WildTangent on 2005-12-23
My MSI card (with Ralink 2500 chipset) works out of the box, no fuss at all.

-Wild

---

### Post by Piney Woods on 2005-12-27
[QUOTE=noigeaR]a wireless solution that works "out of the box" for all operating systems without installing any drivers at all is a **wireless ethernet bridge**. i use a linksys wet54g with ubuntu and it works great. you just connect the computer to the bridge with via ethernet. from the point of view of your computer it's like you're directly connected to the access point via ethernet. the wireless connection is transparent. set-up and configuration is done with a web frontend.
a very nice thing is, if you connect the wireless bridge to a hub or switch, then all computers connected to this hub/switch will automatically have wireless access. this even works for ethernet printers or game consoles with ethernet port. the only drawback is that wireless ethernet bridges are more expensive than a wireless usb adapter (and they're a bit bigger too).
some examples of wireless ethernet bridges are *linksys wet54g*, *linksys wet54gs5* (with built-in 5 port switch), *netgear wge101* or *zyxel g-405*.[/QUOTE]


I have tried this solution for a desktop computer running ubuntu 5.10 and cannot get it to work.  Firefox will not load the webpage.  I have gone in and manually configured the ip address to the default settings and that did not work. The bridge (wet54g) is about 90 ft from the linksys router(wrt54g) I use and I was told by linksys tech support that that is too far for the bridge to work.  I don't believe that is the case though.  All of the lights on the bridge are working but the "wireless G" light flashes continuously.

Now, before this, I tried setting it up on an XP machine and was able to configure it successfully and so I thought all I had to do was to unplug from the XP machine and simply plug it into ubuntu but no go.  I have gone in and manually set the ip address and gateway but still cannot get online with the bridge.  Could it be that the range is too far?  I have a linksys expander that is in the same room and it works fine for the windows machines.

Thanks,
Piney Woods

---

### Post by noigeaR on 2005-12-27
If the same setup works for Windows XP then it can't be the range. The range is determined by the hardware, not by the operating system on your computer.
Can you connect to the webinterface of the bridge under linux? Type the IP address 192.168.1.226 into the address-bar in firefox and you should be asked for the password for the bridge. When you're on the webinterface, there's a site survey button where you can see what networks the bridge can connect to. If you can see your wireless router there, then the bridge can connect to it.
You can ping your wireless router from a terminal to see if you have a connection from your computer to the wireless router.
On a terminal type
```
ping 192.168.1.1 -c4
```
That's only if your linksys router uses the default IP of 192.168.1.1 of course. 
Your problem probably is, that you don't receive an IP address from your wireless router. Do you use DHCP or fixed IPs?

---

### Post by Piney Woods on 2005-12-27
[QUOTE=Piney Woods]I have tried this solution for a desktop computer running ubuntu 5.10 and cannot get it to work.  Firefox will not load the webpage.  I have gone in and manually configured the ip address to the default settings and that did not work. The bridge (wet54g) is about 90 ft from the linksys router(wrt54g) I use and I was told by linksys tech support that that is too far for the bridge to work.  I don't believe that is the case though.  All of the lights on the bridge are working but the "wireless G" light flashes continuously.

Now, before this, I tried setting it up on an XP machine and was able to configure it successfully and so I thought all I had to do was to unplug from the XP machine and simply plug it into ubuntu but no go.  I have gone in and manually set the ip address and gateway but still cannot get online with the bridge.  Could it be that the range is too far?  I have a linksys expander that is in the same room and it works fine for the windows machines.

Thanks,
Piney Woods[/QUOTE]
I have tried several times to connect to the web interface under linux with no success.  The router does have dhcp working and the ip address you gave above is the correct one.  Yes I do use dhcp from the router to send out ip addresses.

I tried the ping test as you mentioned above and all four packets were lost "Destination Host Unreachable".

---

### Post by xtacocorex on 2005-12-27
I have a Netgear WG511 which works out of the box, but if you buy one, make sure that it's made in Taiwan as the ones made in China don't work with Linux.

I was going to send you to [http://prism54.org](http://prism54.org), but it appears they changed their site and don't have the list of supported chipsets/cards completely moved over.

---

### Post by noigeaR on 2005-12-27
[QUOTE=Piney Woods]I have tried several times to connect to the web interface under linux with no success.[/QUOTE]

Sounds like your ethernet adapter isn't recognized under linux. what interfaces are listed if you type```
netstat -i
```is there an interface called eth0?

---

### Post by Piney Woods on 2005-12-27
I don't know why my earlier post never showed up.....

Anyway, I tried the command to no avail.  All four packets were lost.  I do use dhcp for ip addresses.  I am unable to load the ip address for the bridge under linux using Firefox.    What else do you suggest?

PW

---

### Post by Piney Woods on 2005-12-27
Yes, linux does recognize my lan port as eth0 and it is active.

---

### Post by Piney Woods on 2005-12-28
UPDATE:

I started completely from scratch and reinstalled on my XP machine.  I made sure it was configured with DHCP and that the ssid was correctly typed in.  One mistake I had made was forgetting it was CASE SENSITIVE.  Instead of having it in all lower caps...I had the first letter in capitals.  I changed that and it seems to be working now.  I finished configuring all the settings and clicked on save.  When I tried going to google it loaded with no problems so I knew the bridge was working.

I then unplugged it from the XP machine and then to my Ubuntu desktop, clicked into the Network properties, set it as DHCP, etc....and it WORKED!  I am now able to access the internet, email, download all the updates for Ubuntu and add a few more repositories.  

Thanks to all who helped, posted suggestions and solutions for this problem. 

PW

---

### Post by linuxfanatic1024 on 2005-12-31
I've had very good luck with my Atheros and Ralink-based cards. I bought a Belkin USB card at Best Buy that has a Ralink chipset, which is well-supported on Linux. 

PLEASE try to avoid cards that work only with ndiswrapper or DriverLoader! I prefer to use ndiswrapper ONLY when I can't afford to replace a card that is Linux-hostile. Why?

1. It can encourage hardware manufacturers to continue making proprietary WiFi hardware. By buying their products, you are be supporting these companies that produce secret hardware.
2. Native support is usually more stable.
3. Native drivers are usually under the GPL. The Atheros driver is under the GPL and BSD licenses except for the HAL (contrary to what some think, the HAL is binary-only ONLY because of the FCC and other countries' laws, not because Atheros wants to keep their hardware a secret)
4. The "big three" Linux-friendly chipset manufacturers--Atheros, Ralink, and Intel--have provided a lot of assistance to Linux driver programmers (or written Linux drivers themselves).
5. By buying hardware that doesn't have Linux drivers, you are also indirectly telling them that Windows-only support is OK.

Native Linux driver support is important to me. When there are many cards out there that do have native Linux support, there is not much of an excuse NOT to get one.

I would recommend a Belkin or Linksys PCMCIA/PCI/USB card--both have Ralink chipsets (and have native Linux support).

Ralink drivers can be found at [http://www.ralinktech.com/supp-1.htm]("http://www.ralinktech.com/supp-1.htm"). Atheros and Intel drivers are bundled with Ubuntu and installed by default.

Cards to AVOID:
- Netgear WG111 -- this popular USB card uses a TI chipset and is NOT very well supported natively. When my girlfriend and I tested this card on Linux, we got it to work using ndiswrapper, and she tested it on Windows (she uses both OSes, and I use Ubuntu only). Even after getting it to work with ndiswrapper, the card has problems maintaining a connection, and the range is really bad (the signal gets weak quickly). She also had these connection problems on Windows, believe it or not...
- Any other card with a TI ACX100 or TI ACX111 chipset--same issues as the Netgear WG111.
- Any card with a Broadcom chipset. Broadcom doesn't support Linux users. Unfortunately, Broadcom chipsets are very common because they're cheap. Broadcom chipsets can be found in many laptops, especially those from Dell. If you're ordering a Dell and want to use Ubuntu on it, make sure you get one of the Intel WiFi 
- D-Link wireless cards. D-Link likes to play a game called "Let's change the chipset but keep the model number the same!" They used to offer Linux-friendly hardware, but they switched to Broadcom chipsets because they are cheaper. Don't support this! (D-Link Ethernet cards are OK, though, because they use Linux-friendly Realtek 8139 hardware.)

For more information, check out [http://users.linpro.no/janl/hardware/wifi.html]("http://users.linpro.no/janl/hardware/wifi.html")

Sorry my post was so long, but I really want to help as many users as possible avoid the use of ndiswrapper and secret WiFi hardware. Good luck.

---

