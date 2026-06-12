---
title: "All I want is a static ip.. Why is this so difficult?"
date: 2009-04-18
forum: Networking &amp; Wireless
---

### Post by reznorio on 2009-04-18
Hi,

So I'm loving K/Ubuntu. I've had it for about 6 months. But one thing drives me absolutely batty. Upon every reboot, my eth1 goes unconfigured and I have to set it up all manually, even adding the gateway again. I read up on a buggy NetworkManager and tried to stop it and turn it off on boot up (error below). I've added the 'exit' word to those two NetworkManager files to no avail either. I try and use the System->Preferences->Network Configuration but as soon as I click Manual IP, the OK button turns off. (WTF!?)

Can someone please tell me how to keep this persistent?? It's so silly that I have to jump through hoops just to get a static ip don't you think?

Thanks in advance!!


#cat /etc/network/interfaces
auto eth1   <---i've tried commenting this out too
iface eth1 inet static
	address 192.168.0.10
	network 192.168.0.0
	netmask 255.255.255.0
	broadcast 192.168.0.255
	gateway 192.168.0.1
auto lo
iface lo inet loopback



Linux version 2.6.27-11-generic (buildd@yellow) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Wed Apr 1 20:53:41 UTC 2009


# chkconfig NetworkManager off
insserv: warning: script 'K10netlock' missing LSB tags and overrides
insserv: warning: script 'S01linux-restricted-modules-common' missing LSB tags and overrides
insserv: warning: script 'K03powernowd.early' missing LSB tags and overrides
insserv: warning: script 'K03udev' missing LSB tags and overrides
insserv: warning: script 'K01gdm' missing LSB tags and overrides
insserv: warning: script 'K03xserver-xorg-input-wacom' missing LSB tags and overrides
insserv: warning: script 'K02loopback' missing LSB tags and overrides
insserv: warning: script 'K02udev-finish' missing LSB tags and overrides
insserv: warning: script 'K03vbesave' missing LSB tags and overrides
insserv: warning: script 'K16acpi-support' missing LSB tags and overrides
insserv: warning: script 'S28NetworkManager' missing LSB tags and overrides
insserv: warning: script 'linux-restricted-modules-common' missing LSB tags and overrides
insserv: warning: script 'NetworkManager' missing LSB tags and overrides
insserv: warning: script 'vbesave' missing LSB tags and overrides
insserv: warning: script 'netlock' missing LSB tags and overrides
insserv: warning: script 'loopback' missing LSB tags and overrides
insserv: warning: script 'powernowd.early' missing LSB tags and overrides
insserv: warning: script 'udev' missing LSB tags and overrides
insserv: warning: script 'acpi-support' missing LSB tags and overrides
insserv: warning: script 'xserver-xorg-input-wacom' missing LSB tags and overrides
insserv: warning: script 'gdm' missing LSB tags and overrides
insserv: warning: script 'udev-finish' missing LSB tags and overrides
insserv: There is a loop between service hwclock and mountall
insserv:  loop involving service mountall at depth 8
insserv:  loop involving service checkfs at depth 7
insserv: There is a loop between service hwclock and mountall
insserv: There is a loop between service hwclock and mountdevsubfs
insserv:  loop involving service mountdevsubfs at depth 5
insserv:  loop involving service udev at depth 4
insserv:  loop involving service nfs-common at depth 2
insserv:  loop involving service hwclock at depth 1
insserv:  loop involving service mysql-ndb at depth 8
insserv:  loop involving service hwclockfirst at depth 8
insserv: exiting without changing boot order!
/sbin/insserv failed, exit code 1

---

### Post by lensman3 on 2009-04-18
I run Fedora Core 10 and I'm not familiar with Ubuntu, but.....

On my system selinux is running for security.  It has options when it is running that can reset config files that were changed.  Kinda of like "Oh, that file has changed, copy the last good config over the top".

Maybe this security is doing it.  

The file to change is /etc/selinux/config.  Change the line to "SELINUX=disabled"

I hope this helps.  

By the way, Redhat Fedora Core 10 suffers with the same problem.  NetworkManager has been disabled on my machine.  You are using the same chkconfig that I did.  You can do the same thing that chkconfig does by going to the /etc/rc3.d, /etc/rc4.d, and /etc/rc5d and deleting the soft linked files that have NetworkManager in them.  The prepending S for start and K for kill are used during each runlevel boot.  rc3.d are the files that are executed when the kernel passes through run-level 3.  Run-level 5 is starts the GUI.  Go to /etc/init.d and delete the script "NetworkManger".  This is the script that is causing all the "evil".

Something on my systems are still trying to stop the network link. I haven.t found it yet.  It tries to remove the lowlevel driver.  "dmesg" shows the driver stopping and starting.

"NetworkManger" is not ready for prime time!!!!

---

### Post by FrankT-Qc on 2009-04-18
It's definitely a NetworkManager problem, I've encountered this many times...

If you're going to use static config, keep your /etc/network/interfaces as it is (the "auto" line has to be there to if you want your interface to go up at boot time) and uninstall NetworkManager

have fun,
Frank

---

### Post by bugslayr on 2009-05-08
Hello!
I am having the same behavior on Kubuntu 9.04 ...
I tracked the issue down to a script in ***/etc/network/if-pre-up.d***

The script ***dhclient3-apparmor***will start the dhcp client for all interfaces except **lo**
Somehow it executes pretty late and overwrites all other settings.

I added an extra line: ***[ "$IFACE" != "eth0" ] || exit 0***
Now the script leaves my interface alone and I can configure my desired settings in either ***/etc/network/interfaces*** or in **NetworkManager**.

Well, this changes helped me ... although it might not be a really clean approach ... maybe it's helpful for others too.

---

