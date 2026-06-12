---
title: "UNE won't pick up my Belkin router"
date: 2010-07-26
forum: Networking &amp; Wireless
---

### Post by Heidious on 2010-07-26
I'm a first time Linux user and have just dual-booted my Advent Milano netbook. I am running XP SP3 as well as Ubuntu Netbook Edition.

After much troubleshooting and enquiring I managed to get the wireless up and running on it. However I can only connect to a nearby unsecured network. Ubuntu simply does not acknowledge my Belkin router. The wireless light is not even on. Yet it works perfectly in XP.

My router is a Belkin Wireless G (F5D7634xx4A-H). Is there any way I can make it work in Ubuntu? I downloaded the .pdf of the manual but it doesn't mention anything about installation/setup for Linux.

Any help is much appreciated .

---

### Post by Montserrat on 2010-07-26
Heidious,

I don't have an answer for you, but a similar problem. I also have a dual install, with Win7 partitioned from 10.04 LTS on a Toshiba laptop. I can connect to the Belkin Wireless G just fine from the Win7 side. On Ubuntu, if I first get online using the wired connection, I can sometimes disconnect the ethernet cable, then be able to surf for a time on automatically connecting to something. I must be inadvertently borrowing a cup of broadband from next door, because it doesn't seem to be the Belkin (that's Model F5D7230-4 v9 by the by). 

Perhaps the two of us can get some attention here.

---

### Post by kerry_s on 2010-07-26
the router shouldn't matter, it's your wireless card in your computer that needs to be working.

both of you give no info there, no specs, make, model, etc...

---

### Post by wojox on 2010-07-26
Did you install the ndiswrapper?

---

### Post by Montserrat on 2010-07-26
Speaking for myself, here's info on the NIC. It's a Realtek RTL8191SE Wireless 802.11n PCI-E. I haven't installed NDISwrapper. Any advice for doing so? 

I see that NDISwrapper's supposed to make drivers for card and router work with Ubuntu. Will it work on Win7 drivers? Or are they the same anyway?

---

### Post by Montserrat on 2010-07-27
wojox,

Thanks, I didn't wait for your advice, but used Synaptic to install NDISwrapper. Now the Belkin wireless works.

Let's see if this works for Heidious.

m

---

### Post by Heidious on 2010-07-27
My wireless hardware is a RaLink RT3090 802.11b/g.

I am having problems installing NDISWrapper. I typed in the command to install it but it's still saying it's not installed.

---

### Post by Montserrat on 2010-07-27
You're ahead of me if you already knew about NDISWrapper. I had no problem installing through Synaptic Package Manager. You can also use Synaptic to check its status. But I should shut up, and let someone more experienced help out.

---

### Post by Heidious on 2010-07-27
Synaptic worked. NDISWrapper is now installed. Cheers for the help :)

---

