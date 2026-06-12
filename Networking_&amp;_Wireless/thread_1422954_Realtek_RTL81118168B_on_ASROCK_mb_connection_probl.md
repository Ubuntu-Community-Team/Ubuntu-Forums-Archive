---
title: "Realtek RTL8111/8168B on ASROCK mb connection problem"
date: 2010-03-06
forum: Networking &amp; Wireless
---

### Post by rickyrockrat on 2010-03-06
The problem is this: the r8169 as supplied from the 2.6.24-27 kernel doesn't work, and the new driver from RealTek works the first time, *but* does *not* work after an ifdown. <Edit> The -27 driver does work, you just need to set up the interfaces file </Edit>

So here is the fix for that and the full details on getting this beast to work. There are many folks who've downloaded, compiled, and installed the driver and have written info on it, but I've not seen a full writeup on it yet.

First, install the linux headers:
sudo apt-get install linux-headers-2.6.24-27-generic
Get the part after the linux-headers by doing this:
uname -r


Then download the driver [here]("http://218.210.127.131/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false")

This should give you a file called r8168-8.016.00.tar.bz2 (or some similar version). Untar it using:
tar -xjf r8168-8.016.00.tar.bz2
Then cd to the r8168-8.016.00 directory and do:
make modules
sudo make install
sudo depmod

Then blacklist the module supplied with the kernel:
sudo vi /etc/modules.d/blacklist
Add the line:
blacklist r8169

If you get a /lib/modules/xxxx/build: No such file or directory, your link is not setup correctly, which should have happened when the headers were set up.  If not, this should be a link to the /usr/src/linux-headers-2.6.24-27-generic.
cd /lib/modules/2.6.24-27-generic
sudo ln -s /usr/src/linux-headers-2.6.24-27-generic build


Then your card should work when you shut down the machine, unplug the network cable, wait a minute, plug cable in, turn machine on.  I verified my setup by using a switch, and plugging a working linux box in one port and the DUT (device under test) in the other port, then issuing these commands on both:
sudo ifdown eth0
ifconfig eth0 192.168.3.x up
Where x was 1 on the working one and 3 on the DUT. Then use ping:
ping 192.168.3.x 
I first pinged my local if (i.e. if I used 1, then ping one):
ping 192.168.3.1
Then ping the remote
ping 192.168.3.3
Make sure any firewalls are set to ACCEPT during this operation.

If you try to rmmod r8169, then depmod r8168, you will get a "failed with error -22" in dmesg (type dmesg to see this). The only way I found to get around this module r&r problem was to reboot.

If you ever need to ifdown eth0, then ifup eth0, it will not work, *again*. Add this to your /etc/network/interfaces file:
(This is in the iface eth0 section)

pre-up ethtool -s eth0 autoneg off && ethtool -s eth0 autoneg on

Then your ifup/down should work. I've wasted an entire day messing about with this!!  I had to duct-tape&bailing wire a wireless network between the DUT and my laptop (which had a working NIC) to get the updates to work, so I can even build the driver from realtek, and *that* was a PITB to get up.  I've details on how you set a wireless up. Perhaps I'll write that up, too.

Here's the write-up:

[ad-hoc wireless router hack]("http://newyork.ubuntuforums.org/showthread.php?p=8924081")

Cheers!

---

