---
title: "Natty-Realtek 8101E/8102E -drops out in seconds"
date: 2011-08-11
forum: Networking &amp; Wireless
---

### Post by Bilou5404 on 2011-08-11
This was my first post. I think "Absolute Beginners" is not the best place for it to get an answer. It might take a while to get moved. Forgive me, but I might loose my borrowed machine at any moment so no connection at all then and I'm in a place where I have no idea how to find a cafe.

I've attached diagnostic output following someones help to a 10.04 user.

Rather than repeat it, here is link:

[http://ubuntuforums.org/showthread.php?t=1822682]("http://ubuntuforums.org/showthread.php?t=1822682")

---

### Post by Bilou5404 on 2011-08-11
I think I'm in way beyond my depth. Sure I can copy/paste, but Ive found links that appear to describe an issue of drivers. Most are old, but others talk of compiling a new driver into the kernel (gulp!)

Realtek have a new driver. 
From: [ftp://WebUser:*****@202.134.71.21/cn/nic/r8101-1.020.00.tar.bz2](ftp://WebUser:*****@202.134.71.21/cn/nic/r8101-1.020.00.tar.bz2)


Other links talk about replacing R8169 with R8168 (aargh! blacklist? rename _old??))

All of this is beyond my ken, but I'll post the links I found in case they are useful to someone who knows a lot more than I ever will:

[http://ubuntuforums.org/showthread.php?t=1811819]("http://ubuntuforums.org/showthread.php?t=1811819")
[http://ubuntuforums.org/showthread.php?t=936379]("http://ubuntuforums.org/showthread.php?t=936379")
[http://ubuntuforums.org/showthread.php?t=1442676]("http://ubuntuforums.org/showthread.php?t=1442676")
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/326891]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/326891")
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/534536]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/534536")
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=7&Level=5&Conn=4&DownTypeID=3&GetDown=false#2]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=7&Level=5&Conn=4&DownTypeID=3&GetDown=false#2")
[http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=7&PFid=7&Level=5&Conn=4&DownTypeID=3&GetDown=false#RTL8100E/RTL8101E/RTL8102E-GR/RTL8103E%28L%29%3Cbr%3ERTL8102E%28L%29/RTL8101E/RTL8103T%3Cbr%3ERTL8401/RTL8401P]("http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=7&PFid=7&Level=5&Conn=4&DownTypeID=3&GetDown=false#RTL8100E/RTL8101E/RTL8102E-GR/RTL8103E%28L%29%3Cbr%3ERTL8102E%28L%29/RTL8101E/RTL8103T%3Cbr%3ERTL8401/RTL8401P")
[http://manpages.ubuntu.com/manpages/oneiric/en/man4/re.4freebsd.html]("http://manpages.ubuntu.com/manpages/oneiric/en/man4/re.4freebsd.html")
[http://ask.debian.net/questions/why-doesn-t-the-realtek-rtl8101e-8102e-adapter-work-on-lenny-installer]("http://ask.debian.net/questions/why-doesn-t-the-realtek-rtl8101e-8102e-adapter-work-on-lenny-installer")

All I need is some electrons coming down the cable in the right order and ending up on my screen.

Everything else on the machine works really well. I don't want to give up now!

---

### Post by Bilou5404 on 2011-08-12
Come on guys, this is a pretty common chip set. 

If the (total) lack of replies says "nobody know the answer" or "err..we do have a big problem here and no-one will admit it" then just say so.

I know Windoze can do it. I just don't like that answer, but perhaps it is the only one. No big deal, I'll just have to live with it, sob!

Can I please have just one guy/gal say "no idea, but it sounds like a pita".

This is just so dumb. WIFI is fine, but no internet lan!!! jesus!

---

### Post by Bilou5404 on 2011-08-13
I'm really new on Linux and not a programmer, so if I appear confused then I am confused!

My Googling comes up with similar workarounds all over, basically downloading the current Linux driver from Realtek (done that), save it on usb, and then compile into a "kernel module" (I think that is the right terminology) according to the readme in Realtek's package. 

A copy of that readme is attached (I haven't found out how to do those nice scrolling boxes people use here for text - /code ??)

I guess A good way to proceed might be to 

a)make a backup of the current boot drive to DVD. I need to save a few GB of downloads, delete them, then backup the OS itself to more DVDs. I'll Google good ways to do that.

b)Then blindly follow the readme and pray - I won't understand what I'm doing, just copy/paste, but I can probably handle directory changes and commands at the terminal. I'll practice first.

Can some kind person warn me if any of that seems lunacy. I won't have any internet access from the machine in question once i start, just this ancient XP laptop I've borrowed. The lady concerned may decide to grab the laptop back at any moment, which is only reasonable.

Is this strategy pretty well bullet-proof, or am I risking jumping into a black hole with no way out? With no internet, I won't be able to get help  or get any missing packages. certianly not from repos as this machine is XP.

Wise counsellings appreciated. I'm not too proud to listen carefully!

Thanks a bunch if you can help a bit.

Guillaume

Hang on a moment, I found this button in advanced for code. Trying for the readme. Fingers crossed.

```

<Linux device driver for Realtek Ethernet controllers>

	This is the Linux device driver released for RealTek RTL8101E, RTL8102E(L) and RTL8103E(L), the Fast Ethernet controller with PCI-Express interface.

<Requirements>

	- kernel source tree (supported Linux kernel 2.6.x and 2.4.x)
	- For linux kernel 2.4.x, this driver supports linux kernel 2.4.20 and latter.
	- compiler/binutils for kernel compilation

<Quick install with proper kernel settings>
	Unpack the tarball :
		# tar vjxf r8101-1.aaa.bb.tar.bz2

	Change to the directory:
		# cd r8101-1.aaa.bb

	If you are running the target kernel, then you should be able to do :

		# ./autorun.sh	(as root or with sudo)

	You can check whether the driver is loaded by using following commands.

		# lsmod | grep r8101
		# ifconfig -a

	If there is a device name, ethX, shown on the monitor, the linux 
	driver is loaded. Then, you can use the following command to activate 
	the ethX.

		# ifconfig ethX up

		,where X=0,1,2,...

<Set the network related information>
	1. Set manually
		a. Set the IP address of your machine.

			# ifconfig ethX "the IP address of your machine" 

		b. Set the IP address of DNS.

		   Insert the following configuration in /etc/resolv.conf.
		
			nameserver "the IP address of DNS"

		c. Set the IP address of gateway.

			# route add default gw "the IP address of gateway"

	2. Set by doing configurations in /etc/sysconfig/network-scripts
	   /ifcfg-ethX for Redhat and Fedora, or /etc/sysconfig/network
	   /ifcfg-ethX for SuSE. There are two examples to set network 
	   configurations.

		a. Fixed IP address:
			DEVICE=eth0
			BOOTPROTO=static
			ONBOOT=yes
			TYPE=ethernet
			NETMASK=255.255.255.0
			IPADDR=192.168.1.1
			GATEWAY=192.168.1.254
			BROADCAST=192.168.1.255

		b. DHCP:
			DEVICE=eth0
			BOOTPROTO=dhcp
			ONBOOT=yes	

<Modify the MAC address>
	There are two ways to modify the MAC address of the NIC.
	1. Use ifconfig:

		# ifconfig ethX hw ether YY:YY:YY:YY:YY:YY

	   ,where X is the device number assigned by Linux kernel, and
		  YY:YY:YY:YY:YY:YY is the MAC address assigned by the user.

	2. Use ip:

		# ip link set ethX address YY:YY:YY:YY:YY:YY

	   ,where X is the device number assigned by Linux kernel, and
		  YY:YY:YY:YY:YY:YY is the MAC address assigned by the user.

<Force Link Status>

	1. Force the link status when insert the driver.

	   If the user is in the path ~/r8101, the link status can be forced 
	   to one of the 4 modes as following command.

		# insmod ./src/r8101.ko speed=SPEED_MODE duplex=DUPLEX_MODE autoneg=NWAY_OPTION

		,where
			SPEED_MODE	= 100	for 100Mbps
					= 10	for 10Mbps
			DUPLEX_MODE	= 0	for half-duplex
					= 1	for full-duplex
			NWAY_OPTION	= 0	for auto-negotiation off (true force)
					= 1	for auto-negotiation on (nway force)
		For example:

			# insmod ./src/r8101.ko speed=100 duplex=0 autoneg=1

		will force PHY to operate in 100Mpbs Half-duplex(nway force).

	2. Force the link status by using ethtool.
		a. Insert the driver first.
		b. Make sure that ethtool exists in /sbin.
		c. Force the link status as the following command.

			# ethtool -s ethX speed SPEED_MODE duplex DUPLEX_MODE autoneg NWAY_OPTION

			,where
				SPEED_MODE	= 100	for 100Mbps
						= 10	for 10Mbps
				DUPLEX_MODE	= half	for half-duplex
						= full	for full-duplex
				NWAY_OPTION	= off	for auto-negotiation off (true force)
						= on	for auto-negotiation on (nway force)

		For example:
		
			# ethtool -s eth0 speed 100 duplex full autoneg on

		will force PHY to operate in 100Mpbs Full-duplex(nway force).

<Jumbo Frame>
	RTL8101E, RTL8102E and RTL8103E do not support Jumbo Frame.

```

Oooh! It worked. I just learned something.

---

### Post by gordintoronto on 2011-08-13
I wish I could say, "yup, that will work," but I have no idea.

Funny, the computer I'm using has a Realtek 8111, but it has never had an Ethernet cable attached to it. My wireless adapter "just works," through dozens of versions/distros.

---

### Post by Bilou5404 on 2011-08-13
> **gordintoronto said:**
> I wish I could say, "yup, that will work," but I have no idea.

Funny, the computer I'm using has a Realtek 8111, but it has never had an Ethernet cable attached to it. My wireless adapter "just works," through dozens of versions/distros.

I had no problems either with my WIFI (Ralink RT3090), except initially it wouldn't connect even under XPsp3. The guest house guy where I was staying back then gave me the bs that it was working fine for the (incredibly ancient) laptop they had. Strange. So I walked up and down the street (in Ho Chi Minh, Vietnam)with my machine carefully cradled in my arms, and got a couple of unprotected WIFIs to connect. Mmmmm, definitely curious. So I looked at the setup the guest house was running. It turned out that it was actually XP running on a cable connection. So I tried that cable on mine (still under XP at the time). It worked. I then disconnected and tried their WIFI. That then worked OK and it continued to work on 3 other networks over a period of 1 month.

Natty connected on the first try. That worked for a month with no problems.

Then moved to the current room. No WIFI, but a cable from a router. That always works, so I didn't give it a second thought, nor, unfortunately, try it. I was looking forward to a nice fast download speed which WIFI, by definition, can't always give us.
Oh well. I'll continue to update this thread when I come across useful stuff. It might help others. There doesn't seem to be a sub-forum for compiling and stuff so I'll keep it here.

---

### Post by Bilou5404 on 2011-08-13
OK, continuing with the compile/blacklist solution.

Ubuntu seems to recommend using Checkinstall rather than a staright "make".

[https://help.ubuntu.com/community/CompilingEasyHowTo]("https://help.ubuntu.com/community/CompilingEasyHowTo")

Unfortunately there is a bug with Checkinstall that has never been fixed. But there is a work-around for that bug (Yikes - I am getting in deep!).

[https://bugs.launchpad.net/ubuntu/+source/checkinstall/+bug/78455]("https://bugs.launchpad.net/ubuntu/+source/checkinstall/+bug/78455")

Anyway, I downloaded the latest checkinstall deb package manually. Also got Ethtool as some people have suggested that can help once you get the correct driver loaded.

Then I might need some other packages it seems, namely:
build-essential, and
gcc (a c compiler I think), and, possibly
automake

That will need a wifi connection. I'll have to try and find one. Or download the live cd onto the xp machine and copy it to my external HD for burning. That means I have to find that utility that can mount ext3 on XP. Aargh!

There must be someone around who has already done this and has the checkinstall deb package for the latest driver!

---

### Post by gordintoronto on 2011-08-14
You can download individual packages from packages.ubuntu.com. Copy them to a flash drive or CD-RW to get them to your networkless machine.

The down side: you have to check for uninstalled "dependencies," and gather them first. I think you will find that gcc is part of a basic Ubuntu installation, but you must get build-essential. Or perhaps build-essential includes gcc.

---

