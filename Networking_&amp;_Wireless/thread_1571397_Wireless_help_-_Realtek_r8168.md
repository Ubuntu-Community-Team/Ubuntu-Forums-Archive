---
title: "Wireless help - Realtek r8168"
date: 2010-09-09
forum: Networking &amp; Wireless
---

### Post by admac21 on 2010-09-09
Ok, I'm trying set up a new Advent Roma 3001 laptop for my granny, this will be her first computer (perfect time to try Ubuntu) so I want everything set up flawlessly. So, after I received the laptop I set about installing Ubuntu 10.04, after the installation had finished and rebooted everything worked perfectly! Great I thought! It even connected to our wireless network no problem (our network has always been a pain in the *** to connect to anyway) So I set about installing all the latest updates, rebooted and then the problems began... Upon logging in the wireless no longer worked, nor did the sound. I tried various solutions and installed the latest drivers from realtek but to no avail (although the sound magically started working again) So after a whole night not really getting anywhere I decided just to start fresh again and not bother with the updates, next day, fresh install, logged in, nothing... couldn't get it connected with a wired or wireless connection, so tried the realtek drivers again which has fixed the wired connection, but still no wireless, it doesn't detect any networks, not even neighbours. Really stuck here and obviously the wireless is one of the most important things I need to have working.

On a side note, I've only been using Ubuntu since the release of 10.04, so not the most clued up person, I can use terminal fine, but mostly for copy/paste jobbies.

Also, the README file that I got with the realtek driver has further instructions about setting up network related information, but I have no idea how to enter them correctly, and they seem to be related to eth0, which is already working, there is also further instructions for mac addresses, force link status and jumbo frame which is all lost on me, so I have no idea wether that is where the problem is or not. This is the readme for referance:

```
<Linux device driver for Realtek Ethernet controllers>

	This is the Linux device driver released for RealTek RTL8168B/8111B, RTL8168C/8111C, RTL8168CP/8111CP, RTL8168D/8111D, RTL8168DP/8111DP, and RTL8168E/8111E Gigabit Ethernet controllers with PCI-Express interface.

<Requirements>

	- Kernel source tree (supported Linux kernel 2.6.x and 2.4.x)
	- For linux kernel 2.4.x, this driver supports 2.4.20 and latter.
	- Compiler/binutils for kernel compilation

<Quick install with proper kernel settings>
	Unpack the tarball :
		# tar vjxf r8168-8.aaa.bb.tar.bz2

	Change to the directory:
		# cd r8168-8.aaa.bb

	If you are running the target kernel, then you should be able to do :

		# ./autorun.sh	(as root or with sudo)

	You can check whether the driver is loaded by using following commands.

		# lsmod | grep r8168
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

	   If the user is in the path ~/r8168, the link status can be forced 
	   to one of the 5 modes as following command.

		# insmod ./src/r8168.ko speed=SPEED_MODE duplex=DUPLEX_MODE autoneg=NWAY_OPTION

		,where
			SPEED_MODE	= 1000	for 1000Mbps
					= 100	for 100Mbps
					= 10	for 10Mbps
			DUPLEX_MODE	= 0	for half-duplex
					= 1	for full-duplex
			NWAY_OPTION	= 0	for auto-negotiation off (true force)
					= 1	for auto-negotiation on (nway force)
		For example:

			# insmod ./src/r8168.ko speed=100 duplex=0 autoneg=1

		will force PHY to operate in 100Mpbs Half-duplex(nway force).

	2. Force the link status by using ethtool.
		a. Insert the driver first.
		b. Make sure that ethtool exists in /sbin.
		c. Force the link status as the following command.

			# ethtool -s ethX speed SPEED_MODE duplex DUPLEX_MODE autoneg NWAY_OPTION

			,where
				SPEED_MODE	= 1000	for 1000Mbps
						= 100	for 100Mbps
						= 10	for 10Mbps
				DUPLEX_MODE	= half	for half-duplex
						= full	for full-duplex
				NWAY_OPTION	= off	for auto-negotiation off (true force)
						= on	for auto-negotiation on (nway force)

		For example:
		
			# ethtool -s eth0 speed 100 duplex full autoneg on

		will force PHY to operate in 100Mpbs Full-duplex(nway force).

<Jumbo Frame>
	Transmitting Jumbo Frames, whose packet size is bigger than 1500 bytes, please change mtu by the following command.

	# ifconfig ethX mtu MTU

	, where X=0,1,2,..., and MTU is configured by user.

	RTL8168B/8111B supports Jumbo Frame size up to 4 kBytes.
	RTL8168C/8111C and RTL8168CP/8111CP support Jumbo Frame size up to 6 kBytes.
	RTL8168D/8111D supports Jumbo Frame size up to 9 kBytes.
```


And thank you for any help! It will be very much appreciated!!


[B][COLOR="Red"]
EDIT[/COLOR][/B]: Ok, after looking at ''lspci -v'' I have noticed that the wired (ethernet controller) and wireless (network controller) are actually 2 seperate modules/drivers if I am understanding this correctly, in which case, that would explain why the wired connection is working, but the wireless isn't.

The wireless (network controller) is actually Realtek RTL8187SE. I had a look on their website, but only found windows drivers, but in the terminal window it says:

Kernal driver in use: r8180
Kernal modules: rtl8187se

Am I right in thinking that both of those should be rtl8187se, and is so, how would I change it so that it is?

Thanks again!

---

