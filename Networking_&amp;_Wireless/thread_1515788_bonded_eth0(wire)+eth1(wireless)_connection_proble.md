---
title: "bonded eth0(wire)+eth1(wireless) connection problems"
date: 2010-06-22
forum: Networking &amp; Wireless
---

### Post by pyro42 on 2010-06-22
(newbie disclaimer here)

so what i have is a fresh install (10.04 LTS) of the latest ubuntu install on my laptop, i have followed directions [here]("https://help.ubuntu.com/community/LinkAggregation?highlight=%28%28UbuntuBonding%29%29") and [here ]("http://blog.brightbox.co.uk/posts/howto-do-ethernet-bonding-on-ubuntu-properly")to try and set up network bonding.  I have more or less succeeded, more so on the 'less' side.

the problem i am having is getting the wireless to connect/lease.  i have set it up for DHCP as static IP's get a bit bleh when you travel with your laptop.

i followed the directions [here]("https://help.ubuntu.com/community/LinkAggregation?highlight=%28%28UbuntuBonding%29%29") for setting up, however i used the /etc/network/interfaces from [here]("http://blog.brightbox.co.uk/posts/howto-do-ethernet-bonding-on-ubuntu-properly")  (didn't touch loopback section)
 

```
auto bond0
iface bond0 inet dhcp
  slaves all
  bond-mode 0
  bond-miimon 100
```at this point, i rebooted for good measure.

since i had removed network manager, i used the guide at [this]("http://www.stoltenow.com/archives/2006/12/ubuntu_configur.html") site to try and configure the wireless connection (eth1).  

```
Sudo iwconfig 
```confirms eht1 is IEEE 802.11bg

```
sudo iwlist eth1 scanning
```scans and shows several AP, including the one i want to connect to: ARKVIORDWAYWEST

```
sudo iwconfig eth1 essid ARKVIORDWAYWEST
```returns no errors

```
sudo iwconfig
```shows eth1 being associated to ARKVIORDWAY, AP's MAC address, link quality, noise levels etc etc

```
sudo dhclient eth1
```works.. sometimes.  nearest i can tell, it works only when the ethernet cable is unplugged.

sudo dhclient eht0 / sudo dhclient bond0 both work to obtain a lease for the wired connection, but not the wirelss.

my suspicions are either that my wireless (eth1) is somehow not bonding correctly, or more likely, the fact that i am not trying to connect both interfaces to the same router.  the hardline goes to my router, which is plugged to a rooftop antenna connecting to ARKVIORDWAYWEST.  my wifi card however, i want to connect directly to the providers AP, not my router. 

The provider caps their service at 2 mbps and quite honestly, has horrible connection quality.  (anywhere from 7%-14% packet loss from pingtest.net) however they do allow simultaneous connections at 2mbps each.  So my hope was to bond together a couple connections on my primary computer, and get a little better speed and fault tolerance. 

and yes, i would LOVE to just get a different provider, but they really are the best in the area.  centurytel DSL maxes out at 1.5mbps. SECOM advertises 6mbps but their site survey revealed 1.3mbps, maybe 1.5+ if i trimmed a tree, hugesnet.. just LOL.. $100 a month for 2mbps with a 500mb daily cap?  i've asked around and i don't there is even a cable TV provider for the area.  :confused:

a bone, can someone throw me one?

---

### Post by pyro42 on 2010-06-22
ok, so i found the example files with ifenslave, and i came across this

```
-----8<----------8<----------8<----------8<----------8<-----

auto bond0
iface bond0 inet dhcp
    bond-slaves none
    bond-mode 1
    bond-miimon 100

auto eth0
iface eth0 inet manual
    bond-master bond0
    bond-primary eth0 wlan0

auto wlan0
iface wlan0 inet manual
    bond-master bond0
    bond-mode 1
    bond-miimon 100
    bond-give-a-chance 10
    wpa-bridge bond0
    wpa-key-mgmt WPA-PSK
    wpa-proto WPA
    wpa-group CCMP
    wpa-ssid my-ssid
    wpa-psk "my-secret-password"

-----8<----------8<----------8<----------8<----------8<-----

You do not need an "iface eth0" stanza.

The "auto bond0" stanza is required, else bond0 won't bring up.

The "wpa-bridge bond0" stanza is required to informe wpa_supplicant that wifi link-level packets will arrive on bond0, not on wlan0.
The "bond-give-a-chance 10" stanza is required to give a chance for wifi authentication to succeed.
```

which sounds like what i need, however the access point is an open AP, so what do i put in place of the wpa sections?

---

### Post by pyro42 on 2010-06-23
also bought a wireless adapter for my desktop for once i get this all figured out.  
so.. um.. bump?:p

---

### Post by idef1x on 2011-05-21
Just starting to look at this too....anyone with a working configuration?

---

