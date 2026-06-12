---
title: "pppoe help (raspppoe and pppoeconf)"
date: 2006-02-14
forum: Networking &amp; Wireless
---

### Post by navir on 2006-02-14
Im quite new to ubuntu, still dual-booting with windows xp(which by the way was a breeze to set up in ubuntu).
Anyway, in windows I have this raspppoe client, I dont know exactly what it is, my internet guy set it up on my computer. I type raspppoe in the run option and a little window pops up where i can query the ethernet for services. Over my ethernet connection, there are many different services. ubuntu chooses the first one in that list, hence i cant access the net.

my question is that is there any client for ubuntu that can let me do the same. i tried RP-PPPoE and it just configured the same connection that pppoeconf did, except it took some more time.

please help me get rid of windows!!!!!

thanks
navir

---

### Post by mips on 2006-02-14
Navir,

You might not need rasppoe or pppoe.
What router/modem brand/model do you have ?
Who is your ISP ?

---

### Post by navir on 2006-02-14
thanks for your quick reply,
i dont have a router or any other device. all i got is a LAN cable going in the back of the computer. the LAN is detected properly and configured via DHCP. im in bombay, india, my ISP is exatt net.

thank you

---

### Post by mips on 2006-02-14
If you don't have a router or any other device where does the LAN cable go to ???

---

### Post by navir on 2006-02-14
im sorry, i misunderstood router for an external box. the LAN cable goes into the inbuilt ethernet which is a 
**Marvell Yukon Gigabit Ethernet 10/100/1000Base-T Adapter, Copper RJ-45**

thats what the name is in windows control panel. should i be looking somewhere else?

thanks

---

### Post by mips on 2006-02-14
[QUOTE=navir]im sorry, i misunderstood router for an external box. the LAN cable goes into the inbuilt ethernet which is a 
**Marvell Yukon Gigabit Ethernet 10/100/1000Base-T Adapter, Copper RJ-45**

thats what the name is in windows control panel. should i be looking somewhere else?

thanks[/QUOTE]

One end of the LAN cable plugs into the PC, where does the other end plug into ?

---

### Post by navir on 2006-02-14
The other end goes into a socket in my wall, a normal electric switch socket. I guess to my ISP's server?

---

### Post by mips on 2006-02-14
In that case I don't think it is a LAN cable. You don't perhaps have a internal DSL modem ???

---

### Post by navir on 2006-02-14
i'm quite sure it is a LAN cable, and no i dont have an internal DSL modem. my motherboard is an ASUS K8V-X. both ubuntu and windows see it as eth0 and Local Area Connection respectively, and both configure it via DHCP. I'm sorry if i'm leading you around in circles.

in windows i query it using a PPPoE access concentrator which also tells me that it is a local area connection.

am I missing something?

thanks

---

### Post by mips on 2006-02-14
Unless you have a direct ethernet connection to your ISP which I doubt.

Where/what is the pppoe access concentrator ???

---

### Post by navir on 2006-02-14
i type raspppoe in start-run, and a window pops up that says 'query available services'

my isps website is [www.exatt.net](www.exatt.net)
and the local cable operator from where i get the last mile connection is
worldnet.exatt.com

the drivers for download are on the second site

thanks youve been very patient
navir

---

### Post by mips on 2006-02-14
Have a look at [http://mm.gnu.org.in/pipermail/linuxers/Week-of-Mon-20040719.txt.gz](http://mm.gnu.org.in/pipermail/linuxers/Week-of-Mon-20040719.txt.gz)

The second link worldnet.exatt.com does not work ?

---

### Post by navir on 2006-02-14
thanks man, ill let you know if that works out
navir

---

### Post by linuxfreaks on 2006-06-23
I also have a same kind of problem. My ISP has installed a raspppoe in my computer and a dialup- kind of window where i put in my username n password and get connected to the net.

Now i have installed a dual booting system (XP n Ubuntu).
In Ubuntu:
I installed PP-PPPoE but the program doesn't start!.
What should I do??

---

### Post by mips on 2006-06-25
Give us more info, hardware make & model of the router/modem/ISP etc ?

There is no way your isp is going to install a ras box in your pc, maybe you mean something else ?

---

### Post by Quad Master on 2007-08-25
Me too having the same doubt.

Scenario.

I have a Onboard Nvida based Lan Card where the lan cable comming from my ISP plugs in.

The other end of the Lan cable is connected to a Switch/Hub 8port on the terrace of my bldg.

All i have to do is In start>run> type raspppoe and i am presented with this.

[IMG]http://img341.imageshack.us/img341/4898/raspppoewj0.png[/IMG]

Then i create a dialer , like this

[IMG]http://img502.imageshack.us/img502/4441/dialercz2.png[/IMG]

Here i key in my username and passwd provided by my isp and this is how i get connected online.

My ISP is Tata Indicom Broadband.

---

### Post by Leoric on 2007-10-25
Hi, I'm from Russia, possibly I've had the same problem. I don't know about Bombay, but in my town direct-cable connection to ISP is quite common. So in fact it is PPP over LAN, with just a cable directly plugged into ethernet adapter at the user's end of the line.

Using rp-pppoe I managed to get the connection up. 

Seems to be a problem with DNS, because I can't obtain dynamic IP (even in Windows - but there it works without it).
So I have to manually specify IP and DNS address in Linux. Placed DNS address in /etc/ppp/pppoe.conf. - Reboot is required!

---

