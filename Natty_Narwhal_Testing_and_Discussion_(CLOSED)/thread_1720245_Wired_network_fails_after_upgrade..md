---
title: "Wired network fails after upgrade."
date: 2011-04-03
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by VeeDubb on 2011-04-03
I'm at a complete loss.

I upgrade yesterday, through update-manager -d, from 10.10 to natty beta1 on my desktop.   This is my main home machine.  

The upgrade completed without errors.  

After reboot, I could not get online.  I wasn't worried at first because my on-board NIC has always been iffy.  (software determined MAC, wierd stuff like that)  I tried all of my usual work-a-rounds and none of them helped.  It would try to connect, but never get an IP address.  When I try to set up a static IP, it just won't connect to the router.

Then I caved in and bought a new network card.  Same problem.  I went so far as disabling the onboard NIC, removing the new NIC, deleting all connection profiles from the network manager, rebooting, shutting down to reinstall the new NIC, and trying it all again.  Same results.

So I figured, what the heck?  I used my netbook to download the beta ISO, set up a USB startup disk, and tried to install from that.  Low and behold, same results.  Granted, I didn't actually install because the live image couldn't get online.

I tried different network cables, different ports on the router, attaching other devices to the router with the same cables and ports.  

The router is good.

The cables are good.

It's a brand new NIC suffering the EXACT same symptoms as my old NIC.  

No other peripherals on the PCI bus have had any problems.

Does anybody have a clue for me?

---

### Post by VeeDubb on 2011-04-03
Just for grins and giggles, I tried a THIRD network card that was collecting dust in a closet.  it's old and dusty, but known to be good.  It was in the closet because it's only 10/100, and both my on-board and the new one I bought today are gigabit.

Same exact results.  The live image can't connect to the network.

---

### Post by VeeDubb on 2011-04-03
If it makes any difference (which it shouldn't) the new NIC is a netgear GA311 using the RTL8169 chipset which is well known to be fully supported on Ubuntu since edgy

---

### Post by sddfdds on 2011-04-03
may or may not be related, but im on wireless and cant connect...just sits and tries to connect and asks for my wpa2 password over and over but doesnt actually connect

---

### Post by VeeDubb on 2011-04-03
I'm just shocked that I haven't seen anybody else posting the same exact problem.  3 different network cards, all with the same results even running from the live image.

---

### Post by Lucretius on 2011-04-03
similar issue...

wireless connects, works for 30 seconds, fails and won't reconnect

---

### Post by cariboo on 2011-04-03
Are you sure it isn't a dns problem? Try pinging google by name and ip address.

---

### Post by VeeDubb on 2011-04-03
> **cariboo907 said:**
> Are you sure it isn't a dns problem? Try pinging google by name and ip address.

No response.  I can't even successfully ping my router.  When I run ifconfig eth0 it shows the hardware and MAC, and shows that the interface is up, but it doesn't show an IP address.

---

### Post by callan79 on 2011-04-03
> **VeeDubb said:**
> Same exact results.  The live image can't connect to the network.


Just putting my hand up with similar issues...

LAPTOP:
[LIST]
[*]HP Mini 1001TU
[*]Wireless is Broadcom BCM4312 rev 01 (had to install restricted driver to make it work)
[*]Was running 10.10, did a dist-upgrade, and network failed after it was rebooted
[*]Connected a 3G USB Internet stick, did an update, I can now see wireless services around the place
[*]Curiously, I can't see my own wireless service but I can see others, perhaps that's an issue my side, will investigate
[/LIST]


DESKTOP :
[LIST]
[*]Motherboard Gigabyte GA-MA790X-UD4P
[*]LAN is Realtek RTL8111C/D(L) chip (10/100/1000 Mbit)
[*]Was on 10.10, did a dist-upgrade, lost wired network after reboot
[*]ifconfig does show that I have a connection called eth0
[*]eth0 has no IP Address though
[*]I'll do an update tonight and post the results
[/LIST]

---

### Post by VeeDubb on 2011-04-04
Well, I never found the problem, but I did find a solution for me.

I did a full reset to factory defaults on my router.  I can't imagine why my netbook, which is also running natty, was able to connect to my router with the same cable plugged into the same port, but multiple versions of ubuntu and 3 different network cards on my desktop weren't able to, and the problem only started when I tried to upgrade to natty.

---

### Post by callan79 on 2011-04-04
> **callan79 said:**
> Just putting my hand up with similar issues...

LAPTOP:
[LIST]
[*]HP Mini 1001TU
[*]Was running 10.10, did a dist-upgrade, and network failed after it was rebooted
[*]Curiously, I can't see my own wireless service but I can see others, perhaps that's an issue my side, will investigate
[/LIST]


DESKTOP :
[LIST]
[*]Motherboard Gigabyte GA-MA790X-UD4P
[*]Was on 10.10, did a dist-upgrade, lost wired network after reboot
[/LIST]



Well, for someone that works at an ISP and does troubleshooting with customers every day, how much of an idiot do I feel right now?

May laptop wireless is still busted, I'll keep working on that one.

But my desktop machine - the LAN cable had fallen out of the socket.

The Wired LAN was definitely working before I upgraded, and it was broken after I restarted. Somewhere in the middle there, by pure coincidence, I did a dist-upgrade and the LAN cable fell out at the same time, even though I haven't moved my computer.

Weird.

Anyway, I will post back if I find anything more with the Laptop's wireless.

Have a good chuckle at my expense, folks :)

CD

---

