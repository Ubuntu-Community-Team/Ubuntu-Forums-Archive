---
title: "Help to enable mythtv service on ethernet"
date: 2009-12-10
forum: Mythbuntu
---

### Post by gwagchunks on 2009-12-10
Hi Everyone

When I setup my box (a combined backend/frontend), I did not select the tick box for enabling mythtv on the ethernet interface and the machine is setup with no "real IP address", just the default 127.0.0.1. I would like to try adding a remote frontend, so I think I need to give my box a static IP, but I'm not sure on how to set this up and don't know if it messes up the database / SQL connections? Has anyone else tried this/got any pointers please?

Thanks

---

### Post by klc5555 on 2009-12-10
> **gwagchunks said:**
> Hi Everyone

When I setup my box (a combined backend/frontend), I did not select the tick box for enabling mythtv on the ethernet interface and the machine is setup with no "real IP address", just the default 127.0.0.1. I would like to try adding a remote frontend, so I think I need to give my box a static IP, but I'm not sure on how to set this up and don't know if it messes up the database / SQL connections? Has anyone else tried this/got any pointers please?

Thanks

Should be a snap. The only normal nuisance is getting your machine assigned a static address by your home network router (rather than assigning first available address in range by DHCP at bootup). If your home net is already static, then this, of course, is no problem.

If not, you can either render your network static, by disabling the router's DHCP and assigning addresses to all your machines yourself. Or, if you only want your master backend server static, while having the rest of the machines on your network continue to use DHCP-assigned addresses, you can do this as well.

If you want only your master backend server to be static, then the "correct" way is to log into your home router and set the address leased to your master backend as a permanent lease, so that the router always assigns this particular address to that particular machine and to no others. The steps to do this will vary from router to router.

The very lazy and not approved way, on a very small home network, would be to simply go into Network Mangler on your Mythbuntu desktop and set up a static address that is outside the range of addresses your home router would be expected to assign.

This works as follows. Most of the time, a home router by default is set to run a private network from the address 192.168.0.1 . The netmask, which is what the router uses to distinguish a packet from inside the network from one outside the network, will normally be 255.255.255.0  .(You will want to check this by running the command "ifconfig" from a prompt, which will tell you this and much else besides.) The first machine that boots on the network will usually get leased at 192.168.0.2, the second at 192.168.0.3, etc. If your network has, say, only six machines, you could simply assign the Mythbuntu master server a fixed address (using Network Manager) at, say, 192.168.0.19 (netmask 255.255.255.0) and have it sit there permanently with reasonable confidence that your other machines will be able to boot and do their usual DHCP stuff with no ip address conflicts. Whatever the private address is of your router (in our example 192.168.0.1) this will be be used in your Network Manager static setup as the "gateway". For DNS resolution of internet addresses, you can either type these DNS server addresses yourself into Network Manager (if you know some valid ones) or, if you have some valid DNS addresses set into your router, you can use the router's address for your DNS (e.g. 192.168.0.1)

I personally keep my whole home network static (except for a subnet that has my wireless laptops). I don't need DHCP to keep track of less than ten machines.

Having set up your master backend machine on a static ip, you set this address in the two spots in the "General" page of the backend setup, set the PIN to 0000, enable the "mysql service" in the "services" tab of MCC, set all frontends (and slave backends) to the new "real" ip, and restart the backend process. Voila! (Usually...).

As always, make a backup of mythconverg before hooking up a new slave backend to your master backend. 

Cheers!

---

### Post by gwagchunks on 2009-12-10
> **klc5555 said:**
> Should be a snap. The only normal nuisance is getting your machine assigned a static address by your home network router (rather than assigning first available address in range by DHCP at bootup). If your home net is already static, then this, of course, is no problem.

If not, you can either render your network static, by disabling the router's DHCP and assigning addresses to all your machines yourself. Or, if you only want your master backend server static, while having the rest of the machines on your network continue to use DHCP-assigned addresses, you can do this as well.

If you want only your master backend server to be static, then the "correct" way is to log into your home router and set the address leased to your master backend as a permanent lease, so that the router always assigns this particular address to that particular machine and to no others. The steps to do this will vary from router to router.

The very lazy and not approved way, on a very small home network, would be to simply go into Network Mangler on your Mythbuntu desktop and set up a static address that is outside the range of addresses your home router would be expected to assign.

This works as follows. Most of the time, a home router by default is set to run a private network from the address 192.168.0.1 . The netmask, which is what the router uses to distinguish a packet from inside the network from one outside the network, will normally be 255.255.255.0  .(You will want to check this by running the command "ifconfig" from a prompt, which will tell you this and much else besides.) The first machine that boots on the network will usually get leased at 192.168.0.2, the second at 192.168.0.3, etc. If your network has, say, only six machines, you could simply assign the Mythbuntu master server a fixed address (using Network Manager) at, say, 192.168.0.19 (netmask 255.255.255.0) and have it sit there permanently with reasonable confidence that your other machines will be able to boot and do their usual DHCP stuff with no ip address conflicts. Whatever the private address is of your router (in our example 192.168.0.1) this will be be used in your Network Manager static setup as the "gateway". For DNS resolution of internet addresses, you can either type these DNS server addresses yourself into Network Manager (if you know some valid ones) or, if you have some valid DNS addresses set into your router, you can use the router's address for your DNS (e.g. 192.168.0.1)

I personally keep my whole home network static (except for a subnet that has my wireless laptops). I don't need DHCP to keep track of less than ten machines.

Having set up your master backend machine on a static ip, you set this address in the two spots in the "General" page of the backend setup, set the PIN to 0000, enable the "mysql service" in the "services" tab of MCC, set all frontends (and slave backends) to the new "real" ip, and restart the backend process. Voila! (Usually...).

As always, make a backup of mythconverg before hooking up a new slave backend to your master backend. 

Cheers!

Wow klc555! Thanks for the comprehensive reply, that's fantastic. I had googled around and saw quite a bit of stuff about changing IP address, but the issue of getting this in the myth service and working with mysql I just couldn't find. I'm fairly confident about IP address schemes and changing / shrinking the dhcp range on my router (I did a CCNA course a few years ago). I'll give this a go tomorrow (after reading on how to backup the database!) I was not sure that this post had posted as it looked as though the forums were down earlier today (well they were showing about 10/12 hours behind).

Thanks again! :)

---

### Post by gwagchunks on 2009-12-12
Hi

Just a quick update to let you know that this worked. I changed to a static IP, and have setup a remote frontend. I didn't realise that you could watch TV over it! I thought recordings was the only option. 

The only thing I have noticed that might be worth mentioning is if there is no network cable in the NIC on the backend/frontend, then you get a message about not being able to communicate with the backend server.

Cheers

---

### Post by Beeeerock on 2009-12-17
I'm having a similar problem... I didn't expect to be running a remote front end box and failed to enable the Mythtv service during the back/front end install on the original box.  Can someone point me to an explanation of what settings get changed or set if this box is checked during install?  I can look for IP addresses to change as described above, but I'd like to understand what is actually going on... and if there are any other details I should be fixing to do it all properly.

---

### Post by nickrout on 2009-12-17
> **gwagchunks said:**
> Hi

Just a quick update to let you know that this worked. I changed to a static IP, and have setup a remote frontend. I didn't realise that you could watch TV over it! I thought recordings was the only option. 

The only thing I have noticed that might be worth mentioning is if there is no network cable in the NIC on the backend/frontend, then you get a message about not being able to communicate with the backend server.

Cheers

Well thats because when you pull the cable out the box no longer has an IP address on that interface.

2 solutions:

1. set up networking in /etc/network/interfaces like this:

```
auto eth0
iface eth0 inet static
        address 192.168.1.11 
        netmask 255.255.255.0
        gateway 192.168.1.1
        dns-nameservers 192.168.1.1

```

obviously use your own network addresses, my MBE is 192.168.1.11 and my router/dns server is 192.168.1.1. The interface should then stay up whether or not a cable is present.

Or

2. don't pull the cable out.

---

