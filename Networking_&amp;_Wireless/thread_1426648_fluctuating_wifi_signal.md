---
title: "fluctuating wifi signal"
date: 2010-03-10
forum: Networking &amp; Wireless
---

### Post by Thasaidon on 2010-03-10
Hi all.

I'm running Ubuntu 9.10 (Gnome)
on a Dell Latitude D510 laptop with built-in Intel Pro Wifi.

When I installed Ubuntu all was fine, but lately I've noticed my wifi signal strength is fluctuating like crazy.

It varies from a full signal bar to no connection (using NetworkManager Applet 0.7.996)
When I look at the iwconfig, I also see the "Link quality" is fluctuating, but the "Signal level" and "Noise level" do not vary much.
Link Quality=15/100  Signal level=-32 dBm  Noise level=-71 dBm

On my windows XP machine (also wireless) the signal is constant and good.
I am the only one on channel 9 in my neighborhood
and there are no other devices interfering on my wifi (phone etc).

Does anyone have any idea why the signal is fluctuating only in Ubuntu?

---

### Post by jpl888 on 2010-03-10
In a nutshell it's probably the driver that is the problem. Especially if it works properly in Windows.

I had a Intel 3945 in my old laptop and that seemed to work quite well with the in kernel driver.

You can probably still use the older (not as open source) drivers with a bit of work or you could try changing to channel 11. For some reason that channel always works better wherever I setup a wireless network (and we aren't just talking about Linux).

Hope this helps.

---

### Post by Thasaidon on 2010-03-11
Thanx for the reply.

Just to make things clear, I am NOT running Windows on the same laptop! I have another system running XP connecting to the same wireless router and I have no problems there. So it's not the router.

As for changing to channel 11, that's not an option since most of the AP's are running on that channel. I choose channel 9 because 8 and 10 are also not in use in my neighborhood, so I should have the least interference there.

I figured it was a driver problem since both the Network Manager and iwconfig show the same behavior.
But I'm not that familiar with Linux and drivers (hence my choice for Ubuntu ;-))
Personally I think some update might be the cause for this problem, because it's fairly recent, and I've been running Ubuntu on the laptop for quite some time now without problems.

So maybe reverting back to the original install (and kernel) should do the trick?

---

### Post by inobe on 2010-03-11
try releasing all the connections and re-enter your credentials.


in the connection properties delete the wireless and restart.

a shot in the dark but........

---

### Post by Thasaidon on 2010-03-11
I installed Wifi Radar to check if I was still the only one on channel 9 and I was.

What I did notice however, is that the "signal bar" indicating the signal strength did not fluctuate in Wifi Radar, whilst my "NetworkManager" bar was still going up and down like a yo-yo.

However, I'm not sure if this bar in Wifi Radar is as dynamic as the one in my Network manager.

I already tried disconnecting and reconnecting, but that didn't work. Also deleting my wifi settings and re-entering them didn't solve the problem.

I'll reinstall Ubuntu and see what happens then.
Are there any logs/settings I need to backup for reference?

Thanx for the help so far.

---

### Post by jpl888 on 2010-03-11
Re: going back to old install and kernel.

Sure if it worked before for you I don't see any reason why it wouldn't work now.

Could you post the output of ```
lspci
``` and ```
lsusb
```

If we know the exact chipset there might be some obvious fixes available that we could point you in the direction of.

---

### Post by inobe on 2010-03-11
when the signal fluctuates are you getting the same bandwidth ?

could just be a fluke especially if it's not affecting anything.

personally i prefer using traditional ifup, it's faster and i don't have to look at some ridiculous signal icon.

---

### Post by Thasaidon on 2010-03-11
> **jpl888 said:**
> Re: going back to old install and kernel.

Sure if it worked before for you I don't see any reason why it wouldn't work now.

Could you post the output of ```
lspci
``` and ```
lsusb
```

If we know the exact chipset there might be some obvious fixes available that we could point you in the direction of.
I don't have access to the laptop right now, so I will post the output later today.

As for things working before... I installed Ubuntu from a cd. But over time, there were some kernel and other updates I installed. So maybe one of these could be the cause for this problem?
Is there a way to check what the last updates were?

[QUOTE=inobe]when the signal fluctuates are you getting the same bandwidth ?[/QUOTE]Nope, when everything indicates the signal strength is 0 (or low) I actually have a very bad connection or none at all. When everything indicates the signal is good, I have a normal connection.

---

### Post by Thasaidon on 2010-03-11
Here are the requested outputs...
```
thasaidon@Chimera:~$ sudo lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:01.0 CardBus bridge: Texas Instruments PCI6515 Cardbus Controller
02:01.2 FireWire (IEEE 1394): Texas Instruments Device 8037
02:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
```
So the wireless is the Last one, **Intel PRO/Wireless 2200BG Calexico2**

and
```
thasaidon@Chimera:~$ sudo lsusb
Bus 003 Device 002: ID 413c:8103 Dell Computer Corp. Wireless 350 Bluetooth
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```
The Bleutooth automatically starts with Ubuntu, but I disable it manually when I'm in the GUI.

As for reinstalling from the original install DVD.
I can also just run the DVD as a live DVD :P and see what happens.
I'll let you know after testing.

---

### Post by Thasaidon on 2010-03-11
Well, I answered some questions but I also raised some more...
here's the deal.

I booted the laptop with the Ubuntu 9.10 live dvd, and the wireless had the same problem.
Then I booted the laptop with Backtrack3 from USB and again, the wifi had the same problem.

So I booted Ubuntu from HD again but this time with a Netgear WG511T PCMCIA wifi card in it.
I connected to my wireless via this "new" interface, and the signal strength seemed to be ok and constant.

So I figured it must be the hardware in my laptop which is old and might be failing.

Then I decided to boot my Windows XP machine and check it's wifi connection to my router. This was again ok and steady.
Then I did a scan on all the wifi networks around and here is the strange thing...

On Ubuntu in Wifi Radar channels 8, 9 and 10 were not used except for my connection on channel 9.

But when I checked for wifi networks on my Windows XP machine in a wifi scanner, it showed two other networks on channel 9!
If I look for these two networks in Wifi Radar on Ubuntu, they are shown on channel 11.

So I changed my channel to 13, because according to both Wifi Radar and my windows tool, channel 12 and 13 are free.
Now my signal is better and seems more stable (for now).

So the flaky connection problem seems fixed now by having changed the channel.

Now the questions are,...
why is Wifi Radar showing two networks on channel 11 whilst the windows tool shows them on channel 9 (which seems to be the most accurate)??????

And why does one wifi interface go banana's because of interference, whilst another wifi interface on the same system/OS/channel seems to stay stable and keeps it's connection?

---

### Post by Netnai on 2010-05-25
I have a Dell Latitude D510 and since a week, i have the same issue with the wireless. I assumed that maybe it is the age of the machine.

---

### Post by Thasaidon on 2010-05-25
> **Netnai said:**
> I have a Dell Latitude D510 and since a week, i have the same issue with the wireless. I assumed that maybe it is the age of the machine.

Well, I solved my problem by changing my Wifi to another channel.
But as of late, the problem seems to be back again...
This time, there is no other wifi on my channel.
So I guess the hardware **is** getting old...

---

### Post by guibon on 2010-05-25
I have the same problem with Ubuntu 10.04, but it does NOT seem to be a hardware problem. I dual boot Win XP and Ubuntu: with XP I have a stable and strong signal, while with Ubuntu I have to almost be sitting on the router to have a continuous, but still strongly fluctuating signal.

---

### Post by RobEdM on 2011-04-04
I realize this thread is a year old and mat not be viewed, but I am having a similarly weird situation and maybe someone may be able to explain a little more in depth. I consider myself to be a somewhat advanced Tech, I troubleshoot ISP's and networks for a living. I am running Ubuntu 10.04 on dell 710m with Intel M765 1.7GHz centrino, my wireless is an Intel Pro Wireless 2915 chipset, which offers 802.11a, b and g. I have configured a dual boot win Win7. This is my 3rd Linux build but first with Ubuntu. Now to get the reason for the post, I run my home network starting with a Docsis3.0 modem that provides a 1Gb conn. to a D-Link Dir-655 Rev B (Ipv6 support), the D-link is my router and Subnet host wired to a Netgear WNDR 3300 running DD-wrt broadcasting a 2.4Ghz Bridge to my Office for printers and office PC, I receive that connection with another WNDR3300 flashed with DD-wrt, both of the Netgears Broadcast a 5Ghz wireless that I use for Laptops leaving my wife,guests and gaming systems on 2.4Ghz. Only when I run Ubuntu do I have a problem, my wireless signal is good and steady to every AP but the D-Link, it seems to catch 21-36% with drops down to 0-5% sitting in the room with the AP, when I run the exact same computer in Win7 mode I have a constant 54g when I run my ASUS gaming laptop which also runs a/b/g/n in 2.4Ghz connected to D-Link I seem to have a constant 150Mbs connection. This has absolutely got me stumped, I do quite a bit of installations and trouble shooting so I have the privilege of having two 655's rev.B and one rev.A on hand yet only the Rev.B's have the fluctuations and only in Linux and yet it doesn't seem to affect the bandwidth or speed. This is only bothering me because I depend on knowledge to pay my bills and I'm always looking for a new challenge. I guess my easiest solution is ignore it and keep on about my business, but then I'll have the one I couldn't fix being in my own network and that's not cool.

---

