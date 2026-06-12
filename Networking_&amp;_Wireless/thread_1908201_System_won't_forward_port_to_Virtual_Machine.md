---
title: "System won't forward port to Virtual Machine"
date: 2012-01-12
forum: Networking &amp; Wireless
---

### Post by ArcherB on 2012-01-12
I installed a Virtual Machine that I was successfully connecting to using RDP.  The system is a Windows Server and RDP simply works better than VNC for my needs.

I wanted an easy way to transfer files back and forth from the VM my Ubunutu 11.10 machine.  First I tried to get SMB working.  This required me to try and set up a TUN/TAP interface.  Well, that looked way to complicated for simple file transfer.  I also realized that I could simply use an actual drive on my system as one of the VM drives.

All is well, right?  No.  Now I can't connect to my VM using RDP.  I know the QEMU script is right because it worked before I started messing with the settings.

So, in tryin to fix this, I started messing with my /etc/interfaces file and ended up with something like this:
```
auto lo
iface lo inet loopback

auto br0
iface br0 inet static
        address 192.168.1.69
        network 192.168.1.0
        netmask 255.255.255.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
        bridge_ports eth0
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off
```

Well, for whatever reason, I lost the ability to access the Internet.  LAN access was fine.  I was able to see stuff locally on the network, but nothing beyond my routher.  This was "fixed" by eliminating all the extra stuff from this file and ended up with this:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
```
Plain, simple and it worked.  I was able to access the web.  

However, I am still unable to access my VM's via RDP.  I've tried setting them up with aqemu, VMM, and now VirtualBox.  None of them work, so I don't think it's a problem with my settings and like I said, they all worked before.  Here is one of my VM's command lines:
```
#!/bin/sh
# This script created by AQEMU
/usr/bin/qemu-system-x86_64  -smp 2 -soundhw es1370 -enable-kvm -m 4096 -localtime -cdrom "/media/300/MS/en_sql_server_2008_r2_developer_x86_x64_ia64_dvd_522665.iso" -hda "/home/bryan/.aqemu/4GBWin2008R264_bit_HDA" -hdb "/home/bryan/.aqemu/Win2008R264_bit_HDB" -boot once=c,menu=off -net nic,vlan=0 -net user,vlan=0 -redir tcp:3389::3389 -name "4GBWin2008R264-bit" -vnc :3 -enable-kvm $*
```

Any help is most appreciated.  If you need any other files or settings, let me know.

Thanx!

---

### Post by ArcherB on 2012-01-14
OK, how is this.

Is there a way to re set up networking to default values and set up by all the applications that modified it?

And...

What packages do I need to reconfigure?

I'm thinking this may be a firewall issue.  I am able to connect to this machine via VNC from within my LAN.  From outside my LAN, the connection is rejected.  Also, my VNC dies whenever I try to run something in X as root.  For example, "gksu synaptic" kills the VNC session.  Don't know if that's related.

I've set ALL:  ALL in my host.allow file.  No effect.  I've scoured the /etc/ folder for anything that may be causing the problem.  I don't know what else I can do.

---

### Post by SeijiSensei on 2012-01-14
How about setting up an [OpenVPN]("http://openvpn.net/") tunnel with the VM as the client and your Ubuntu box as the server?  When the VM boots it will try connecting to your Ubuntu machine to set up the tunnel.  Once it's up and running you should have no problems moving data between the two systems.

I use [shared static keys]("http://openvpn.net/index.php/open-source/documentation/miscellaneous/78-static-key-mini-howto.html") for OpenVPN tunnels since they're so easy to set up.

---

### Post by ArcherB on 2012-01-17
OK, here's what I did to fix it:

I did a complete removal of libvirt and all dependent files and reinstalled.  This allowed me to connect to my VMs and have Internet access.  I am able to access the machines via RDP from both the local machine and remotely through port forwarding.

I was able to get access to the rest of my system using VirtualBox's SMB share settings.  I simply set one of my secondary drives (/media/DriveName) to be shared through VirtualBox and the drive magically appeared as a mapped drive in the VM.  I went ahead and shared my home directory the same way.  

As a side note, VirtualBox Rocks!  It's easy to configure, has easy to follow documentation on Oracle's site and runs nearly as fast as running natively.  QEMU wasn't bad, but drive throughput was terrible.  Installing Win2008r2 took at least six hours in QEMU.  It took about half an hour under VirtualBox.  I'm impressed.

---

