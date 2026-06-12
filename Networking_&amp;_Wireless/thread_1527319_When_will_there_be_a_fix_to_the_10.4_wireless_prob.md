---
title: "When will there be a fix to the 10.4 wireless problem"
date: 2010-07-09
forum: Networking &amp; Wireless
---

### Post by nisbeam on 2010-07-09
Like many others it seems, my wireless has stopped working since a recent upgrade The answer does not lie in analysis of logs, settings etc. but surely with those who did it - they should provide a fix.
I cannot believe everyone expects each individual users to go into their own analysis of why this is no longer working as it is clearly widespread.  I have been using Ubuntu for 18 months without this problem on the same dual-boot laptop, and it still works on Windows as before, only Ubuntu 10.4 has recently stopped my network card from working.
I need to know when this will be fixed.  I have been embarrassed by promoting Ubuntu to many colleagues who now also cannot work at home on their wireless networks.
Seriously disillusioned I may start looking for a more stable alternative to Windows.
:(

---

### Post by TBABill on 2010-07-09
nisbeam, I understand your frustration. Do you use a proprietary driver? If so is it possible to just reinstall the driver and reboot? Obviously this wasn't caused by you but to wait would just frustrate you further. It could simply be a change that can be un-changed once you know what it was. 
 
Also, if it's a proprietary driver, was it from Ubuntu or did you get it from the web? That can cause breakage like this when updates are applied.
 
I'm not assuming anything, just offering thoughts that may be easy checks and fixes. If it is deeper than these I hope it resolves quickly for you and the other users impacted.

---

### Post by nisbeam on 2010-07-09
Thanks for the reply.  No it is not a proprietary driver when I first installed Ubuntu it just worked, and has ever since.  Various other threads discuss reinstalling certain components, but it seems that the network is switched off when I boot up.  So if I knew how to check and Enable it that would be a work around until it gets fixed.  But having tried I have not been able to find how to do this.  Thanks anyway,  Andy.

---

### Post by lelantus on 2010-07-09
Unfortunately, this seems to be a problem that plagues a decent portion of Lucid users. I've spent the last two weeks of my free time doing nothing but writing, reading, editing, and researching various "fixes" for this issue. I'm not sure if this is the case with your problem, but the majority of users (myself included) aren't having trouble with their wireless cards or Lucid's support of them, but instead with Network-Manager. 

With the fresh install, Network-Manager appears to work flawlessly. A day or so after (sometimes less) though, it begins to loose functionality. My workaround was pretty simple: I just installed **Wicd** from the repositories (you can use either Synaptic or apt-get) and things were up and running. 

This is nice for internet use, but seeing as so many of the sleek new programs that make the Distro what it is (i.e. all the IM clients involved with Broadcast) rely solely on Network-Manager, this isn't really a complete fix. I'm a bit disappointed with the Ubuntu team for this, but I'm sure they've got a patch on the way... right? Please... I'd much rather just use the native software if possible.

Hope this helped!

---

### Post by nisbeam on 2010-07-09
Lelantus - thanks for your help.  But I am replying unfortunately using my Vodafone USB connection as Wicd didn't work.  It installed fine, detected my Netgear router, told me it was not secure ( I have removed any security).  It said connecting, then I saw some sort of address which quickly disappeared.  The it says getting IP address which eventually fails.  I have no static IP addresses allocated  - or required in the router, it is all simple DHCP.  I have tried re-booting the router but same result.  Am I doomed to failure ?  Going to give up tonight as it is getting late & I need a drink to calm down.  Any further hep will be gratefully received, I wonder how you got this to work so easily with Wicd?  Thanks again.  Regards, Andy.

---

### Post by lelantus on 2010-07-09
That's unfortunate.. humor me and type

```
lshw -c network
```into Terminal for me, will you? This should give a readout of your network status (both wireless and  wired). Post the readout when you're done.

---

### Post by nisbeam on 2010-07-10
Hi and thanks.  I just tried using a static IP to avoid the DHCP, well it did avoid Wicd using DHCP but still did not connect.  Results of ls below:
 *-network               
       description: Ethernet interface
       product: 88E8055 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 10
       serial: 00:16:36:e1:47:46
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.25 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:27 memory:da000000-da003fff ioport:3000(size=256) memory:d4000000-d401ffff(prefetchable)
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:0d:f0:35:31:ed
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

Thanks again.

---

### Post by lelantus on 2010-07-10
Okay, well, if your network was disabled, you would get a readout saying something like

```
 *-network DISABLED
       description: Wireless interface

```

Since you're not, then it appears that Ubuntu is at least recognizing your card's existence, which is a start.

Try this.

```
cd /var/lib/NetworkManager/
```

and then

```
sudo gedit NetworkManager.state 
```

If it says "WirelessEnabled=false", change it to "WirelessEnabled=true" and reboot. This has apparently worked for some people.

---

### Post by nisbeam on 2010-07-10
Hi - your post must have happened at the same time I just tried something else - and it worked!

System, ShutDown, Hibernate switched on the wireless !!! the light came on then the system hibernated.  When I pressed the power up button to re-start the light came on again and I was able to connect with Wicd :p

I tried this after someone had posted a similar fix but shutting the lid.  This didn't work for me so I tried the Hibernate instead and Hey Presto!

Thanks again for all your help, you have restored my faith in the Ubuntu community - not sure about the developer;) of Network Manager though!!  I would still like a "proper" fix.

Best wishes.  Andy.

---

### Post by lelantus on 2010-07-10
Glad to hear it!

---

### Post by rogerdg on 2010-07-10
I have a problem with network-manager not logging into my network after a reboot/hibernate/suspend It prompts me for my network key.  It waits until I click CONNECT, then connects.  I tried removing network manager and using WiCD.  WiCD connects correctly, but removing network manager breaks empathy.

I'm currently using Ubuntu Lucid Lynx and would really like to see network manager fixed.  My network is auto-configured and I am using WEP security with a shared key.

---

### Post by lelantus on 2010-07-10
I had this problem too for a while. 

Oddly enough, I uninstalled and then reinstalled network-manager and for the moment it's working just fine. So maybe they came up with a patch to fix the problem.

If not, then you may want to check your network-manager settings and make sure that it's set for automatic connection.

---

### Post by lelantus on 2010-07-11
Aaaaand now it's gone again. 

Using Wicd isn't a particularly large problem, but *rogerdg* is right, without Network-Manager, clients like Empathy and Evolution are difficult (if not impossible) to use it would appear that even if the program is uninstalled/ reinstalled, it still has the same expected lifespan of one or two boots before it breaks. 

This is extremely disheartening, as I know what the problem is. I just have no idea how to fix it. 

Alright, so, just in case any forums staff end up seeing this *cough* *cough* here's the issue (at least as far as I can tell).

When one navigates to ```
/var/lib/NetworkManager/
``` and looks at ```
NetworkManager.state
``` with sudo gedit, you can find the following:

```
[main]
NetworkingEnabled=true
WirelessEnabled=false
WWANEnabled=true
```The readout should be with "WirelessEnabled=true", therefore enabling the wireless communication. Strangely, it keeps returning to "=false" after changing it to "=true", saving, and restarting network-manager.

I have no idea why it keeps reverting to "=false", but this is clearly where the problem lies. I also have no idea how to fix it..

UBUNTU GURUS.. HELP US!

---

### Post by lelantus on 2010-07-18
Bump.

---

### Post by lelantus on 2010-08-11
Bump.

---

### Post by nawir on 2010-08-12
Hai. I've tried to open the NetworkManager.state and the value is true.does anyone know why it happens?

---

### Post by lelantus on 2010-08-12
Well, is your NetworkManager program working?

---

