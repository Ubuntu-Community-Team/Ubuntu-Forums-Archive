---
title: "Help - VLAN's, The NetworkManager way"
date: 2012-09-20
forum: Networking &amp; Wireless
---

### Post by Doc X on 2012-09-20
Hello!

I'm trying to set up VLANs using NetworkManager (now that is supports them natively). I need some help from a NetworkManager guru.

For this example, the computer will be hooked to an ethernet switchport that does not have a 'native' VLAN, so all packets must be tagged. So there ***must*** be a system-wide ethernet configuration.

For the system-wide configuration, I'm creating files in /etc/NetworkManager/system-connections .

I have a wired connection eth0 which is the parent connection for my VLANs. Since there is no native VLAN on the switch, I'm guessing that ipv4 under eth0 should be disabled. I have created a text file named "eth0" in the above directory which looks like:

--->%---
[connection]
id=eth0
uuid=a924d592-f739-48f1-b2d5-6fdda53bab7b
type=802-3-ethernet

[802-3-ethernet]
duplex=full
mac-address=18:03:73:2b:a7:f7

[ipv6]
method=disabled

[ipv4]
method=disabled
--->%---

I get an error from network manager when it tries to load this file, saying:

keyfile: parsing eth0 ... 
keyfile:     error: invalid or missing connection property 'method'

Why am I getting that error?

If I dont include the 'method=disabled', then by default, NetworkManager tries to get an address from DHCP, that is not what I want.

Next, I'll have a couple of tagged VLANs on eth0, VLAN 100 and VLAN 200. On VLAN 100 the computer will have a static address, and on VLAN 200, the computer should use DHCP to get an address.

I created a file called "vlan200" in the above directory, which looks like:

--->%---
[connection]
id=vlan200
uuid=576cf840-88fb-4692-822b-edae81088476
type=vlan
autoconnect=true

[vlan]
parent=eth0
id=200

[ipv6]
method=auto

[ipv4]
method=auto
--->%---

This file appears to work properly, no errors, and I am sending this forum post through VLAN 200.

Now for VLAN 100.  I have created a file "vlan100" in the above directory that looks like this:

--->%---
[connection]
id=vlan100
uuid=7d0710ba-fea5-4a8e-afea-9e4dedf40a4a
type=vlan
autoconnect=true

[vlan]
parent=eth0
id=100

[ipv6]
method=auto

[ipv4]
method=manual
addresses=192.168.100.111;24;192.168.100.1;
--->%---

When NetworkManager loads this file, I get another this error:

keyfile: parsing vlan100 ... 
keyfile:   error: invalid or missing connection property 'addresses'

Why am I getting that error? From the sparse collection of examples I can locate on the internet, I've got it right. The source code is well documented, but not 'well-exampled' so to speak. 

It says I should have an "array of address structures". Each structure has an IP address in network byte order, followed by prefix (1-32), followed by the gateway in network byte order. Maybe I am creating the array improperly?

In short, why the error with the method in 'eth0'? and why the error with the addresses in vlan100?

Some examples I have used for my test are: 

[Add VLAN tagging to NetworkManager]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/353835")

I know how to set up VLANs properly by editing /etc/network/interfaces, but I'm trying to learn NetworkManager.

Thanks for any help.

---

### Post by Doc X on 2012-09-20
As a follow up:

I figured out the static addressing problem with help from this forum post:

[Howto deal with Network Manager completely from the command line.]("http://arstechnica.com/civis/viewtopic.php?f=16&t=1163023")

The file 'vlan100' now looks like:

--->%---
[connection]
id=vlan100
uuid=7d0710ba-fea5-4a8e-afea-9e4dedf40a4a
type=vlan
autoconnect=true

[vlan]
parent=eth0
id=100

[ipv6]
method=auto

[ipv4]
method=manual
addresses1=192.168.100.111;24;192.168.100.1;
--->%---

Works as advertised. Very unintuitive on how to created the array of arrays for "addresses". It looks to me like a different keyname when used like that.

Still looking for the answer for eth0 not liking method=disabled

---

