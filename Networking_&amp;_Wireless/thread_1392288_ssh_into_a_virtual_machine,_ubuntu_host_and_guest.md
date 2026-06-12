---
title: "ssh into a virtual machine, ubuntu host and guest"
date: 2010-01-27
forum: Networking &amp; Wireless
---

### Post by pythonscript on 2010-01-27
I'm trying to ssh into a virtual installation of ubuntu I have, named "ubuntu-x86" but I can't get it to work for some reason. I have two network cards, both assigned to NAT, on the virtual machine, but one has a static IP address, while the other uses DHCP. For some reason, the command:

```
ssh *username*@ubuntu-x86
``` returns an error of 
"ssh: Could not resolve hostname ubuntu-x86: Name or service not known"

and trying ```
ssh *username*@192.168.1.100
``` doesn't work either. It just hangs. This is my /etc/network/interfaces file from the virtual machine:

```

auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp
auto eth0
iface eth0 inet static
address 192.198.1.100
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1

```Can anyone help me figure this out? Thanks for the help!

EDIT:  Also, once this is working, I should be able to start the virtual machine with
```
VBoxHeadless -startvm "Ubuntu-x86"
```
then ssh into it like normal, right? Thanks!

---

### Post by suseendran.rengabashyam on 2010-01-28
Hi,

If the networking mode on the guest machine is NAT and if you want to SSH into that machine you have to do port forwarding.

You can use VBoxManage, a command line management tool bundled with VirtualBox, for setting up port forwarding. Open the terminal and enter the following commands:

```
VBoxManage  setextradata  ubuntu-x86  "VBoxInternal/Devices/pcnet/1/LUN#0/Config/ssh/HostPort"  2222
VBoxManage  setextradata  ubuntu-x86  "VBoxInternal/Devices/pcnet/1/LUN#0/Config/ssh/GuestPort"  22
VBoxManage  setextradata  ubuntu-x86  "VBoxInternal/Devices/pcnet/1/LUN#0/Config/ssh/Protocol"  TCP
```

The above example assumes a PCNet virtual network card; if you have configured the guest to use the Intel PRO/1000, replace "pcnet" with "e1000" in the above commands.

Once you have typed the above commands, you need to shut down the Guest Machine (a reboot won’t be sufficient) and start it and then connect via SSH with:

```
ssh  -l  <user_name_ubuntu_virtual_machine>  -p  2222  <ip_address_ubuntu_host>
```

I guess there is a small typo in your /etc/network/interfaces file the IP address of the eth0 would be 192.168.1.100.

Also make sure that the IP you are assigning statically is in the right range. You can take help from the output of ```
ifconfig eth1
``` to decide the right range of IP addresses that you can use with NAT.

---

### Post by pythonscript on 2010-01-29
The 192.198.1.100 was a typo in my post; the file itself is correct. Is the choice of port 2222 completely arbitrary, or not? I should be able to start the virtual machine with my headless command mentioned above, then just ssh into it, even without the graphical window open, right? Thanks!

---

### Post by Skaperen on 2010-01-29
> **pythonscript said:**
> The 192.198.1.100 was a typo in my post; the file itself is correct. Is the choice of port 2222 completely arbitrary, or not? I should be able to start the virtual machine with my headless command mentioned above, then just ssh into it, even without the graphical window open, right? Thanks!
Yes, 2222 is arbitrary, although common. If you prefer to use a different port, in most cases you can. If you wish to double check your choice, grep the port number against the file /etc/services and see what other service might be expected there. To see what ports your machine is using, the netstat command is useful.
```
grep 2222 /etc/services
``````
netstat -antup | grep :2222
```FYI, I personally change my ssh daemon to another port besides the standard of 22. I won't say what that port number is. If I were to recommend to people to do that, I'd tell them to pick their own port, anyway (so that there does not become a secondary defacto port number for crackers to bang away at).

---

### Post by pythonscript on 2010-01-29
Thanks for all the tips; would my VBoxHeadless command still work? Any time I try this, the ssh command just hangs without any output.

---

### Post by suseendran.rengabashyam on 2010-02-01
Hi,

   Have you tried my port forwarding suggestions? Does SSH connection still hang after setting up port forwarding?

---

### Post by dmizer on 2010-02-01
You will not need to do any forwarding. I SSH into all my virtual machines without having to do any port forwarding.

Have you installed openssh-server on the guest? If so, please post the /etc/ssh/sshd.conf file from the guest.

---

### Post by sn_ahsanali on 2010-02-02
hey,
i need to ssh a ubuntu server (main server of our network ip 192.168.53.1) i know the password for the root but the problem is m not added in hosts.allow but i know an ip (192.168.50.3) which is  present in hosts.allow   . i  have access to the server(192.168.53.211 my default gateway) which connects to the main server (192.168.53.1)
can any one tell me how to ssh 192.168.53.1

---

