---
title: "bash built in or otherwise command(s) to broadcast packet"
date: 2010-06-03
forum: Networking &amp; Wireless
---

### Post by Crazedpsyc on 2010-06-03
I have a shell script program to capture packets (tcpdump) | filter out the hex data (grep) | replace some data (sed) | add lines between packets (sed), and now I just need it to be broadcast(ed:confused:) to my USB port. so first I think I need to know how to find the hardware port (like the one for the keyboard is generally something like 0x60), and then how to send the packets. so a CLI program to send them there or a pre-existing command. right now I have it >>ed to a file called "packets.txt", but that is just to see if it works, and piping it through another command would be fine.

Thanks for helping! (if you do)

---

### Post by Crazedpsyc on 2010-06-13
Hello? is the ubucommunity dead? What's wrong? need more info??? I've got it

---

### Post by Crazedpsyc on 2010-07-07
Please give me some ideas! I am seriously stuck! Maybe how to make an injector with libpcap?

---

### Post by Crazedpsyc on 2010-10-22
Is there a python module for libpcap, and if so how can I use it to accomplish this?
Bumping
bump
bumped

---

### Post by Crazedpsyc on 2010-10-22
Is there a python module for libpcap, and if so how can I use it to accomplish this?
Bumping
bump
bumped

---

### Post by BkkBonanza on 2010-10-22
How you send it to the USB port is going to depend on what device is receiving it at the other end. Usually a driver is needed to get data correctly to a particular device. If it mimics a serial port then you can likely use some generic serial-usb driver and feed it to that. So what device is the data going to?

---

### Post by Crazedpsyc on 2010-10-22
Just a plain variable frequency antenna that accepts pure binary as far as I know

---

### Post by BkkBonanza on 2010-10-22
I have no idea about that. How does an antenna connect to USB? It doesn't make any sense within my electronics knowledge. You don't mean it's a USB wifi adapter?

---

### Post by Crazedpsyc on 2010-10-23
Yes, but as far as I know It cannot handle anything other than raw packet data. Sorry, I guess that's hex not binary ;P
So it should be as simple as streaming the live data from the packet capture output to the device.

---

### Post by BkkBonanza on 2010-10-23
I've never heard of anything like that at all. If it's a wifi adapter then you need the driver for it. If it's an antenna then there is just no way it can connect directly to USB without some kind of circuit to act as a radio - which is what a wifi adapter is. Can you point me to some information on whatever device you have? Otherwise this is just a dead end.

If you have a wifi adapter you certainly cannot just stream "raw" data to it. You need to install a driver that makes it visible as a ethernet interface, and then you can route packets to that interface.

---

### Post by Crazedpsyc on 2010-10-24
It is basically just a '[cantenna]("http://www.cantenna.com/")', but in an actual plastic case instead of a pringles can ;). but anyway, how do I do this with just a plain internal wifi card with the drivers already installed and working nicely?

---

### Post by BkkBonanza on 2010-10-24
The antenna has to connect to your wifi card, not to USB itself. Depending on the wifi card it will have some small connector(s) for an antenna or the antenna will be "internal" (printed on the circuit board). The two most common antenna connectors are SMA (for USB dongles that have a connector), and MMC (for miniPCIe boards inside notebooks). See this [page]("http://wireless.gumph.org/content/3/7/011-cable-connectors.html") for examples. 

Many wifi adapters do not have antenna connectors and then you would be forced to either mount it inside the cantenna or solder on a wire with a connector. Your best bet in this case is usually to buy a cheap USB dongle off ebay that already has the SMA connector on it. 

I built a cantenna that worked quite well about 2 years ago by making a hole in the can and inserting the USB dongle up into the can about 1.5 cm inside. That wifi adapter had an internal circuit board antenna in it (ZyDas 1211). Later, when I made another one with a N type connector and small wire as antenna it did not work so well.

I've also used an RT8189 from eBay that has an SMA connector. Whatever wifi adapter you use it needs to have it's driver installed and working. In most cases now this happens automatically but there are some adapters that require manually finding and installing the driver. It's best to choose models that have built in support.

---

### Post by Crazedpsyc on 2010-10-25
Ok, Thanks for all the tips there, I actually made (just put the head on) and used one of those cords with my roof-mounted antenna for a substitute cantenna just for fun, but now how about a simpler question. How can I just rebroadcast my collected packets live out say, port 80 to another device on my LAN? I am sure this can be accomplished with libpcap, but I have no idea how. If there is already a program to broadcast packets like this, that would be great too. I prefer python to C, so if there is a python module for libpcap, I would rather use that.

---

### Post by BkkBonanza on 2010-10-25
It depends what you are actually trying to accomplish. You can just use an iptables rule to redirect traffic to a different IP or port. That's probably the easiest way. There are programs like **Tcpreplay** for taking saved packet dumps and replaying them to another machine. You don't need to write a program for this unless you have some special needs regarding data manipulation and even then a lot can be done with tools available.

---

### Post by Crazedpsyc on 2010-10-27
Thanks, that looks like it'll work. I just need to capture, edit, and rebroadcast the packets to another machine, so all of that can be accomplished in a one-line shell script with several pipes now that I have **tcpreplay.**

---

