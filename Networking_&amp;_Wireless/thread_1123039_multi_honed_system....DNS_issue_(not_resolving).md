---
title: "multi honed system....DNS issue (not resolving)"
date: 2009-04-11
forum: Networking &amp; Wireless
---

### Post by ash_lly on 2009-04-11
hello fellows'
i have a system with a nic that lans with my other home computers. i connect to the internet via a usb stick.

my problem is that when the network cable is hooked up to the box, i cannot surf internet..system uses nics dns settings to resolve ip's not the usb's settings. Disabling eth's also does not work that is why i have to remove the cable from the nic

when i remove the lan cable from the system resolving works.

How do i configure my system to use usb settings for internet and not have to physically remove the cable from my box?

/etc/resolv.conf is correctly pointing to my isp

---

### Post by inobe on 2009-04-11
i noticed your topic and decided to try this, i have two gigabyte nics, i tried setting up ICS, incoming from modem to eth1 and outgoing from eth0...

this failed in kubuntu intrepid' however it works well in ubuntu with minimum configurations..

in fact kubuntu takes some time to acquire an ip at startup, i think knetworkmanager has a lot to do with this.

may want to update kde to 4.2, maybe with your configuration this will resolve some of the issues.

---

### Post by inobe on 2009-04-11
actually rebooting in ubuntu with the above config i need to keep changing the settings only when eth0 is configured with auto dhcp, when it's set to share to all computers the settings stick.......

---

### Post by albinootje on 2009-04-11
> **ash_lly said:**
>  How do i configure my system to use usb settings for internet and not have to physically remove the cable from my box? 

Are you sure it is the /etc/resolv.conf and not the possible other gateway ip address ?

It sounds like your ethX (eth0 or eth1 etc.) gets an ip address via DHCP and overrides the gateway and/or /etc/resolv.conf.
It must be possible to give the NIC a static address in NetworkManager or /etc/network/interfaces (without a gateway).

---

### Post by ash_lly on 2009-04-11
i have already upgraded to kde4.2 inobe

/etc/resolv.conf has the nameserver's that are given out by the USB stick

for my nics i have been recieving addresses via dhcp from my router which only gives out ip's (no dns server ip's)

i will try the static ip on my nic and post results.

---

### Post by ash_lly on 2009-04-11
even with static ip(nic enabled or disabled) on the nic, dig or nslookup does not work, as soon as (without even disconnecting the usb connection) i remove the lan cable from the router, dns resolving starts to work.

Iam out of ideas now. To me, in this case, it seems that dns resolution works in order from all ethxx's then to the pppxx's. That is if eth's are not available then resolution occurs with the ppp's settings.

I would like both to work at the same time. 

Its also suprising as I do not experience this problem with my xubuntu box.

---

### Post by ash_lly on 2009-04-12
> **albinootje said:**
> Are you sure it is the /etc/resolv.conf and not the possible other gateway ip address ?

It sounds like your ethX (eth0 or eth1 etc.) gets an ip address via DHCP and overrides the gateway and/or /etc/resolv.conf.
It must be possible to give the NIC a static address in NetworkManager or /etc/network/interfaces (without a gateway).

I think what albinootje says is what is happening in my case. albinootje do you an idea of what i should do now?

---

### Post by albinootje on 2009-04-13
> **ash_lly said:**
> even with static ip(nic enabled or disabled) on the nic, dig or nslookup does not work

How did you set the static ip address ?
-> NetworkManager -> Manual Configuration -> Wired Connection -> Properties ?
Did you fill in the gateway or not ?
Can you plug in the network cable, and after that post the output of the following :
```

cat /etc/resolv.conf
route -n

```

---

