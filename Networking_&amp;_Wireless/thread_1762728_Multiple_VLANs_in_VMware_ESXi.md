---
title: "Multiple VLANs in VMware ESXi"
date: 2011-05-19
forum: Networking &amp; Wireless
---

### Post by sean.kiong on 2011-05-19
Hi there,

I had setup a Multi VLANs in VMware ESXi with HP Procurve Networking Switch.

The following is the /etc/network/interfaces summary of the network server which connect all the Virtual Machine.

all my servers is running on ubuntu server 10.04.

vlan5 = network server
addr 192.168.5.5
subnet 255.255.255.0

vlan6 = WAN
addr 192.168.6.5
subnet 255.255.255.240
gateway 192.168.6.1 which is the internet modem ip.

vlan10 = VLANs allow internet access
addr 192.168.10.5
subnet 255.255.255.0
gateway 192.168.5.5

vlan11 = VLANs no internet access
addr 192.168.11.5
subnet 255.255.255.0
gateway 192.168.5.5

I use ip forwarding in /etc/ufw/before.rules to forward vlan5 and vlan10 segmant to vlan6.
-POSTROUTING -0 192.168.5.0/24 -o vlan6 -MASQUERADE
-POSTROUTING -0 192.168.10.0/24 -o vlan6 -MASQUERADE

something like that, the configuration was working fine. vlan10 and vlan11 can access to the servers in vlan5.
vlan5 and vlan10 can access to the internet.
vlan11 do not have any internet access.

My question is whenever the internet is down or vlan6 is disconnected, the entire network will be down. vlan10 and vlan11 can not reach vlan5.

I do notice that vlan11 will try to goto the DNS to search for an internal ip which is vlan5.

Please guide me how can I correct this ugly setting.

Many thanks

---

### Post by tdiy on 2011-08-05
Hi Sean,

Did you ever get a solution for you problem?

I see that you appear to have Ubuntu 10.04 working with VLAN suppoort on VMWare ESXi. You seem to have made more progress than me. I am having trouble getting the VLANs to actually work in our VM environment. I hope you can give me some pointers as to what you needed to do to get the basics up and running. 

I have VLANs working on a normal server but if I try with a virtualised server setup it fails. 
If I remove the vlan tagging from /etc/network/interfaces and enable VLAN tagging on the ESXi vSwitch it will work. But trying to get vlans set up using /etc/network/interface fails. Any advice on what I need to do?

Theo

---

### Post by sean.kiong on 2011-08-05
Hi Theo,

This is what I did on the VMware site, I created the list of vlans below under the (Configuration -> Networking) :-
vlan00 - Accept all vlan
vlan5  - Accept vlan 5  (server vlans)
vlan10 - Accept vlan 10 (internet accessible vlan)
vlan11 - Accept vlan 11 (intranet vlan)

Ubuntu Servers site:-
Network Server (assign the network adapter to vlan00), so that, it can work as a gateway to talk to each vlans. "I am not sure if this is the correct way but it works"
I configure individual vlan adapter in this server with the IPs subnet. (192.168.5.0, 192.168.10.0, 192.168.11.0, .etc)
I learn from this link on ubuntu server vlan [https://wiki.ubuntu.com/vlan](https://wiki.ubuntu.com/vlan)

What I have done so far the only problem that I am facing is the internet routing, somehow the intranet vlan traffics will go to the internet and come back even the user from the intranet vlan can access the internet.

I hope you find this helpful.

---

### Post by tdiy on 2011-08-10
Hi Sean,

So are you actually setting up the VLANs within your Ubuntu server in /etc/network/interfaces or are you setting them up on the switch in the VMware ESXi interface?

When I enable VLANs in /etc/network/interfaces like so
```

auto lo
iface lo inet loopback

auto vlan100
iface vlan100 inet static
 address 10.1.31.54
 netmask 255.255.255.0
vlan-raw-device eth0

```

I cannot ping other machines in the network with VLAN 100 setup.

If however I just set up the  /etc/network/interfaces like so
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
 address 10.1.31.54
 netmask 255.255.255.0

```
and set up VLAN100 on the vSwitch in the EXSi it does work. 

What I really need to do is get the VLAN working from within Ubuntu.

Is that similar to your situation?
Thanks
Theo

---

### Post by tdiy on 2011-08-10
LOL,

Actually I finally figured out why the Ubuntu server installed in ESXi where acting differently to the Ubuntu server installed directly into hardware.

If you are setting up VLANs within Ubuntu (or any other OS for that manner) running on ESXi you need to use Virtual Machine Guest Tagging (VGT) Mode. 

This doc has information on that but its out of date for ESXi v4.1
[http://www.vmware.com/pdf/esx_vlan.pdf](http://www.vmware.com/pdf/esx_vlan.pdf)

This link
[http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1004252](http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1004252)

pretty much tells that by setting the VLAN ID to 4095 you [FONT=Arial][SIZE=2][FONT=Arial][SIZE=2] enable trunk mode [/SIZE][/FONT][/SIZE][/FONT]

Configuration of VirtualSwitch (vSwitch)

To set vSwitch in trunk mode:

    • Edit host networking via the Virtual infrastructure Client.
    • Click Host > Network > vSwitch_Properties.
    • Click Ports > Portgroup > Edit.
    • Click the General tab.
    • Set the VLAN ID to 4095. VLAN ID 4095 stands for Trunk mode in ESX 3.x.
    • Click OK.

Not sure if this info is any use to you Sean but hopefully it is.
Thanks for you earlier pointers
Tom

---

### Post by sean.kiong on 2011-12-22
Hi Tidy,

The VMware ESXi configuration was okay from my side. This part already kill me for few weeks.
And you were right, you need to configure in the vSwitch.

The problem now is that whenever the VLAN6 or internet connection down. The entire networks will be down.

sigh.

---

