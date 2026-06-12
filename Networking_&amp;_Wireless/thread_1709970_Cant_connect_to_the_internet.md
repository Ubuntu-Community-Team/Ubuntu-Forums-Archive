---
title: "Cant connect to the internet"
date: 2011-03-19
forum: Networking &amp; Wireless
---

### Post by spddheeraj on 2011-03-19
hello,
I'm using HP dv6226 laptop. Installed ubuntu 10.10  inside windows 7, dual boot. My internet works perfectly in windows 7 but doesnt seem to work in ubuntu. I've been searching for a good solution and tried everything I found. These are the outputs for the commands.

$ lspci

02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
05:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller

$ sudo ifup eth0
SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
SIOCSIFNETMASK: No such device
eth0: ERROR while getting interface flags: No such device
Failed to bring up eth0.


$lsmod

e1000e                132956  0 

$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address xxx.xx.xx.xxx
netmask 255.255.xxx.0
gateway xxx.xx.xx.xxx


$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                                                                                        SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
SIOCSIFNETMASK: No such device
eth0: ERROR while getting interface flags: No such device
Failed to bring up eth0.



$ cat /etc/resolv.conf
nameserver 172.31.1.1
nameserver 172.31.1.130



$ mii-tool
SIOCGMIIPHY on 'eth0' failed: Operation not permitted
SIOCGMIIPHY on 'eth1' failed: Operation not permitted
SIOCGMIIPHY on 'eth2' failed: Operation not permitted
SIOCGMIIPHY on 'eth3' failed: Operation not permitted
SIOCGMIIPHY on 'eth4' failed: Operation not permitted
SIOCGMIIPHY on 'eth5' failed: Operation not permitted
SIOCGMIIPHY on 'eth6' failed: Operation not permitted
SIOCGMIIPHY on 'eth7' failed: Operation not permitted
no MII interfaces found

$ sudo mii-tool
no MII interfaces found

$ cat /etc/modules.conf
alias eth0 e1000e


$ cat /etc/modprobe.conf
alias eth0 e1000e

$ lshw
*-serial UNCLAIMED
             description: SMBus
             product: N10/ICH 7 Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:18c0(size=32)


  *-network UNCLAIMED
                description: Ethernet controller
                product: 82573L Gigabit Ethernet Controller
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:05:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: cap_list
                configuration: latency=0
                resources: memory:da000000-da01ffff ioport:4000(size=32)

$ ifconfig

only loopback shows up here.. no eth0 or anything else

Downloaded and installed e1000e manually (after installing ethtool) and then loaded module with sudo modprobe e1000e

but still there seems to be no eth0

then I uninstalled network-manager-gnome and also tried wicd... nothing seems to be working.

any help to get my internet working will be appreciated. Thank you.

---

### Post by mikewhatever on 2011-03-19
Check if you have the wireless module, iwl3945, loaded, and if not, try loading it with "sudo modprobe iwl3945".

---

### Post by spddheeraj on 2011-03-19
Thank you for the reply, yes it is loaded... though I'm trying to connect with wired connection. I do not have a wireless network.

edit: still waiting for some assistance...

---

### Post by spddheeraj on 2011-03-19
hello again... I solved the problem, I just had to reset my network adapter's configuration using preboot in DOS environment. ;)

---

### Post by C.Ganesh on 2011-09-14
i am having the same problem and i am brand new to ubuntu :) so please avoid fancy words... can u explain what u exactly did? thanks in advance

---

### Post by abderazaq on 2012-10-12
> **spddheeraj said:**
> hello again... I solved the problem, I just had to reset my network adapter's configuration using preboot in DOS environment. ;)

hello! how have you configuring your network by using preboot in DOS

---

