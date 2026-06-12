---
title: "Networking doesn't exist."
date: 2010-08-29
forum: Networking &amp; Wireless
---

### Post by Zucriy Amsuna on 2010-08-29
I can't figure out how to connect to the Internet. At all. There is no System > Administration > Networking. There is no System > Networking. No such thing exists, and it never had.

Also, the nm-applet is gone, and I can't get it back. But the Network Manager, as it tells me, still exists, but I can't find it anywhere.

Is there another path to Networking or something? How can I fix this? Please help; I need this system to work.

Thanks.

---

### Post by AlexDudko on 2010-08-29
network-manager applet should be on the upper panel just after installation or booting liveCD.
If there isn't one do
> nm-applet 
in terminal.

---

### Post by Zucriy Amsuna on 2010-08-29
There is no nm-applet. It doesn't exist, anymore.

---

### Post by Iowan on 2010-08-29
From Code of Conduct:> Please use color and font properties for highlighting portions of your text, and not for all of the text in your post.

I'm not well-acquainted with Xubuntu, but you can *try* adding a "Notification Area" to the top panel.

---

### Post by Zucriy Amsuna on 2010-08-29
I'm sorry for the font colour; I didn't realise this forum had that policy.

The Notification Area basically says that there is no more Network Manager.

---

### Post by AlexDudko on 2010-08-29
can you show the output of 
> aptitude show network-manager

---

### Post by Zucriy Amsuna on 2010-08-29
It shows that everything is installed except the nm-applet. It cannot be found.

---

### Post by AlexDudko on 2010-08-29
And what about network-manager-gnome? Is it installed?
If they are installed, then the command
> nm-applet 
should bring the applet to the upper panel.

---

### Post by Zucriy Amsuna on 2010-08-29
As I said before, nm-applet doesn't exist. And it says just that. The command doesn't exist. Networking Manager exists, but not nm-applet.

---

### Post by AlexDudko on 2010-08-29
If you have **network-manager-gnome** installed you should have > nm-applet command, because the latter is included in the former package.

---

### Post by Zucriy Amsuna on 2010-08-29
I know. But it's uninstalled for some reason. Is there a way I can connect to the Internet without nm-applet?

---

### Post by AlexDudko on 2010-08-29
What type of connection do you have? You can easily configure your LAN by editing **/etc/network/interfaces**
> man interfaces

---

### Post by Zucriy Amsuna on 2010-08-29
It would be a direct connection, if it would detect that it's plugged in.

And I don't understand this interfaces thing and how I can utilise it. The manual is a bit confusing.

---

### Post by AlexDudko on 2010-08-29
If you have DHCP, then your **/etc/network/interfaces** should contain something like this:
> # The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
allow-hotplug eth0
iface eth0 inet dhcp

Then simply do
> sudo ifconfig eth0 up

---

### Post by Zucriy Amsuna on 2010-08-29
I don't understand what you have in your quote. All I see there is:

if-down.d
if-post-down.d
if-pre-up.d
if-up.d
interfaces

Should I still try that ifconfig command?

---

### Post by AlexDudko on 2010-08-29
First, show the output of 
> ifconfig -a

---

### Post by Zucriy Amsuna on 2010-08-29
The entire output of ifconfig -a is:

> 
lo Link encap:Local Loopback
    inet addr:127.0.0.1 Mask:255.0.0.0
    inet6 addr: ::1/28 Scope:Host
    UP LOOPBACK RUNNING MTU:16436 Metric:1
    RX packets:8 errors:0 dropped:0 overruns:0 frame:0
    TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
    collisions:0 txqueuelen:0
    RX bytes:560 (560.0 B) TX bytes:560 (560.0 B)


---

### Post by AlexDudko on 2010-08-29
What's the output of 
> more /etc/network/interfaces
I think the lines
> allow-hotplug eth0
iface eth0 inet dhcp 
must be missing. Add them and save the file. Then execute 
> ifconfig eth0 up

---

### Post by Zucriy Amsuna on 2010-08-29
The more command yields:

auto lo
iface lo inet loopback

Yes, those two lines were missing. I added them in, saved the file, then executed the command. I get an error:

> eth0: ERROR while getting interface flags: No such device

---

### Post by AlexDudko on 2010-08-29
Run 
> dmesg
and see if the ethernet device is really present in your system.

---

### Post by Zucriy Amsuna on 2010-08-29
What am I looking for in this giant list?

The card is plugged in within the computer, and the cable is plugged into that--as it normally should. But I don't know any names of anything.

---

### Post by AlexDudko on 2010-08-29
You can find there something like this:
> [   18.610956] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Did your ethernet card work before? Is it a new installation?

---

### Post by Zucriy Amsuna on 2010-08-29
I can't find anything like that in the list.

I set this up on an old computer that had a faulty Windows ME on it; I wiped the hard disk because it couldn't boot, and I decided to install Xubuntu on it. It is now officially my first Linux computer, and I know only what a few college courses of computer science taught me--almost nothing about how to use Linux--just basic UNIX.

---

### Post by AlexDudko on 2010-08-29
Provide output of
> lspci -v

---

### Post by Zucriy Amsuna on 2010-08-29
Using ~~~ to replace a lot of irrelevant(?) stuff:
> 
00:00.0 Host bridge: Intel Corporation 82810 GMCH (Graphics Memory Controller Hub) (rev 03)
~~~

00:01.0 VGA compatible controller: Intel Corporation 82810 (CGC) Chipset Graphics Controller (rev 03)
~~~

00:1e.0 PCI bridge: Intel Corporation 82801AA PCI Bridge (rev 02)
~~~

00.1f.0 ISA bridge: Intel Corporation 82801AA ISA Bridge (LPC) (rev 02)
~~~

00:1f.1 IDE interface: Intel Corporation 82801AA IDE Controller (rev 02) (prog-if 80 [Master])
~~~

00:1f.2 USB Controller~~~
~~~

00:1f.5 Multimedia audio controller~~~
~~~

01:0e.0 Communication controller: Agere Systems LY WinModem
~~~

The last one has the capabilities as "<access denied>", if it matters.

---

### Post by AlexDudko on 2010-08-29
It looks like your system doesn't have a working ethernet card or there's no appropriate driver for it.

---

### Post by Zucriy Amsuna on 2010-08-29
Is there a way to fix that without using the Internet on that computer?

Edit: ADMtek AN983B

Apparently, they don't have any Linux drivers. =/ I suppose that's the reason it doesn't work and never will.

---

### Post by AlexDudko on 2010-08-29
I can't help you if your ethernet card doesn't work.

---

### Post by Zucriy Amsuna on 2010-08-29
It's okay. Thank you for your time and help. ^_^

---

