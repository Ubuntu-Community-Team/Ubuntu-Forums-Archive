---
title: "no network device available"
date: 2009-10-10
forum: Networking &amp; Wireless
---

### Post by deskuda on 2009-10-10
I bought a new pc a few weeks ago and had my old sitting to the side, recently i found a cheap monitor and figured i'd use it again for a second machine.

So, I boot her up and it can't connect to the internet, and on the top right it says 'no network device available'. The network/connection icon, it says 'no network connection', there's also another option that says VPN, but I have no clue on what that is.

Through frustration, I re-installed Ubuntu and it still says the same thing!
I know it's not the cable because I ran it to my other computer + my xbox360 and it went online

Could my network be fried in the old computer and need a new one?

Don't know if this is useful, but I'm using Ubuntu 9.04

---

### Post by mikewhatever on 2009-10-10
You should provide more info on the problem, like your hardware and network setup. Otherwise, helping you is pretty much guesswork.

---

### Post by deskuda on 2009-10-10
This is a tough one, All I really know is, I'm using an ethernet cable hooked to a wired 4-port router. I have all 4 ports in use, they all work, but its just this one computer that won't connect. Or should I say 'no network device available'.

---

### Post by viper250 on 2009-10-10
log in as root open your control center and select hardware see if it detects your network hardware 

look at your network properties make sure it is set to dhcp 
vpn is virtual private networking and is used to securely network to a remote network system example connecting from home to workplace

---

### Post by deskuda on 2009-10-10
I re-installed Ubuntu for the 3rd time and now the internet is working. /shrugs 

That was a strange problem...

---

### Post by ipina on 2009-10-11
Hi my problem is like the one by deskuda. I have a Mac Pro 8-core a couple of days bought, ATI Radeon HD 4870 graphics card and LED Cinema Display. I'm trying to install Ubuntu 9.04 on an internal drive with 250 GB (obviously different from the drive with Mac OS X). I run, in safe graphics mode, a live session user in order to check whether all is ok, and the only bug I find is that related to 'no network devices available'. 
   $ ifconfig shows only parameters for lo, so no ethernet in spite of the fact that I have attached an ethernet connection on OS X.
   $ lspci shows however an ethernet controller Intel Corporation Device 10f6.
Any help would be greatly appreciated.

---

### Post by mikewhatever on 2009-10-11
Can you both post the output of the following command:

sudo lshw -C network

It should show what hardware we are dealing with.

---

### Post by ipina on 2009-10-11
Thank you for your quick reply. Answering you from a MacBook Pro (where Ubuntu run ok) so writing you no a complete output of the command you suggest. 
*-network unclaimed, description: ethernet controller, product: Intel Corporation, physical id: 0, bus info: pci@0000:09:00.0, version: 00, width: 32 bits, clock: 33 MHz, capabilities: pm msi pciexpress msix bus_master cap_list, configuration: latency=0 (there is another message like this one except that bus info is pci@0000:0a:00.0, guess it corresponds to the second ethernet card)
*-network unclaimed, description: ethernet interface, psysical id: 1, logical name: pan0, serial: ba:a4:63:80:d7:90, capabilities: ethernet physical, configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
Thanks once more.

---

