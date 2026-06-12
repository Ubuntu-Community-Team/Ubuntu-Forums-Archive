---
title: "How to setup TFTP server to work on secondary network card?"
date: 2010-12-14
forum: Networking &amp; Wireless
---

### Post by legendbb on 2010-12-14
a machine with 2+ network cards, need to setup TFTP server on one card and use internet on another.

the tftpd server works on default routing network adaptor with following configuration.

How set the TFTP server on the secondary network adaptor?

Thanks,

TFTP server tftpd by xinetd configuration in: /etc/xinetd.d/tftp
{
protocol = udp
port = 69
socket_type = dgram
wait = yes
user = nobody
server = /usr/bin/in.tftpd
server_args = /tftpboot
disable = no
}

Could not find how to change the post <prefix> I remembered clearly I did before.
Can anyone comment on this please.

Thanks,:biggrin:

---

### Post by legendbb on 2010-12-16
Found solution myself, for note if any one needs:

vim /etc/network/interfaces

  	 	 	 	td p { margin-bottom: 0cm; }p { margin-bottom: 0.21cm; }   	 	 		 			[FONT=Arial][SIZE=2]# The loopback netwrok interface [/SIZE][/FONT]
 			[FONT=Arial][SIZE=2]auto lo [/SIZE][/FONT]
 			[FONT=Arial][SIZE=2]iface lo inet loopback [/SIZE][/FONT]
 			 
 			[FONT=Arial][SIZE=2]# This is a list of hotpluggable network interfaces. [/SIZE][/FONT]
 			[FONT=Arial][SIZE=2]# They will be activated automatically by the hotplug 			subsystem [/SIZE][/FONT]
 			 
 			[FONT=Arial][SIZE=2]# mapping hotplug [/SIZE][/FONT]
 			[FONT=Arial][SIZE=2]# script grep [/SIZE][/FONT]
 			[FONT=Arial][SIZE=2]# map eth0 [/SIZE][/FONT]
 			 
 			[FONT=Arial][SIZE=2]# configuration of eth0 with dhcp [/SIZE][/FONT]
 			[FONT=Arial][SIZE=2]iface eth0 inet dhcp [/SIZE][/FONT]
 			[FONT=Arial][SIZE=2]auto eth0 [/SIZE][/FONT]
 			 
 			[FONT=Arial][SIZE=2]# configuring eth1 device with static settings [/SIZE][/FONT]
 			[FONT=Arial][SIZE=2]iface eth1 inet static [/SIZE][/FONT]
 			[FONT=Arial][SIZE=2]address 192.16.230.1 [/SIZE][/FONT]
 			[FONT=Arial][SIZE=2]netmask 255.255.255.0 [/SIZE][/FONT]
 			[FONT=Arial][SIZE=2]gateway 192.16.230.1 [/SIZE][/FONT]
 			 
 			[FONT=Arial][SIZE=2]# add the route for the secondary interface for specific 			addresses [/SIZE][/FONT]
 			[FONT=Arial][SIZE=2][COLOR=#ff0000]up route add -net 192.16.230.0/24 gw 			192.16.230.1 dev eth1 [/COLOR][/SIZE][/FONT]
 			 
 			[FONT=Arial][SIZE=2]# starts automatically at boot up [/SIZE][/FONT]
 			[FONT=Arial][SIZE=2]auto eth1 [/SIZE][/FONT]
 		 	  
TFTP server works on default route network.
# /etc/init.d/networking restart
you may need reboot the machine.

check $ route to see if the default routing is added for the 2nd NIC.

---

