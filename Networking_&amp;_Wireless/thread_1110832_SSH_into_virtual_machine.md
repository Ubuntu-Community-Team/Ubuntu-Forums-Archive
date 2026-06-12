---
title: "SSH into virtual machine"
date: 2009-03-30
forum: Networking &amp; Wireless
---

### Post by blazemore on 2009-03-30
I would like to use SSH to access virtual machines running on a headless server.
I only need to get to them from LAN, not the Internet.
How can I do this?

---

### Post by BkkBonanza on 2009-03-30
Make sure sshd is installed and running on the vm.
Find out what ip connects you with the vm from your lan.
Type,

ssh user@the_ip

If you have a hostname for the vm then you can use that too.

---

### Post by blazemore on 2009-03-30
How do I find the IP of the VM, and ensure it remains static? Can I set up a "virtual" network with just the VMs on the server, as I don't have control over the router that assigns IPs (University dorm room).

---

### Post by BkkBonanza on 2009-03-30
If you are using VMWare then I don't know. Maybe similar to below.

On Virtualbox they have a virtual network mode you select for the vm and then all your vms can be on a virtual network and talk to each other. 

But in Virtualbox NAT mode (default) each vm has it's own ip on it's own seperate network and to get to it from outside (your LAN) you have to add a couple custom commands (from what I recall when I did it). 

In my case I added a couple iptables commands in my host machine to forward ports 80 and 443 to the vm (because the vm could not have ports < 1024 due to not being run as root). Then the ports were accessible. In your case you would want to use something suitable for ssh. The default is 22 but often people like to use some less known port. An example iptables command like I used is below in case it helps. I added this to my /etc/rc.local so it was present on booting. 

iptables -t nat -A OUTPUT -o lo -p tcp --dport 80 -j REDIRECT --to-port 8080

I also had some commands in my VM config (but they are added using VBoxManage, see manual)

<ExtraDataItem name="VBoxInternal/Devices/pcnet/0/LUN#0/Config/guestssh/Protocol" value="TCP"/>
<ExtraDataItem name="VBoxInternal/Devices/pcnet/0/LUN#0/Config/guestssh/GuestPort" value="22"/>
<ExtraDataItem name="VBoxInternal/Devices/pcnet/0/LUN#0/Config/guestssh/HostPort" value="2233"/>

This forwarded port 22 on my VM to port 2233 on my host machine where it can be reached from the LAN.

Hope that gets you started.

---

