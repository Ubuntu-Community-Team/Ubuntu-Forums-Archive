---
title: "Configure Static IP from gnome desktop ubuntu 11.10"
date: 2012-02-03
forum: Networking &amp; Wireless
---

### Post by LandisTwo on 2012-02-03
just an fyi for those, who like me were ready to throw the system in the street.
I've tried to configure my eth1 (eth0 not used, embedded on motherboard) using, well, what would seem to make sense, the... 
System Settings (in that useless side panel)> Network> Wired (2nd connection)> Configure> IPv4 Settings> Method> Manual... NOPE, would NOT let me 'save'... 

So, I figure like everything else on ubuntu/gnome there is no 'root' or 'su' so I have to do this 'old school', in vi run as sudo from console. NOPE, the file that is supposed to have the interface information in it, Doesn't (/etc/network/interfaces)

So, one would think others have to have this issue or it should be in the Ubuntu 'Official Manual' right? NOPE, the official manual, networking, page 33 says the same thing, edit the /etc/network/interfaces file as follows:
"
1.2.3. Static IP Address Assignment
To configure your system to use a static IP address assignment, add the static method to the inet
address family statement for the appropriate interface in the file /etc/network/interfaces. The
example below assumes you are configuring your first Ethernet interface identified as eth0. Change
the address, netmask, and gateway values to meet the requirements of your network.
auto eth0
iface eth0 inet static
address 10.0.0.100
netmask 255.255.255.0
gateway 10.0.0.1
"
Cool, I even use 10. networks, since 1994... NOPE... 
Forums... NOPE, believe it or not the most useful information I got was from [ CiberCiti.biz ]("http://www.cyberciti.biz/faq/howto-debian-ubutnu-set-default-gateway-ipaddress/") : $ sudo ip route add default via 192.168.1.254 - which is fine but is reset at reboot... hmmm
Oh, it also says: $ sudo vi /etc/network/interfaces and add gateway 10.x

NOPE.... 

Well, I remembered when I first loaded my IBM with openSuSE 12.1 it loaded NetworkManager.. I hated it until I installed 12.1 on a laptop and found it useful for the wireless connections..  So, I thought is it here? YEP.. Upper right corner of gnome desktop... And WOW, I can configure my nic to have static IP... 

All this because I replace my Linux Router. I wanted to try [ Smoothwall Express 3 ]("http://www.smoothwall.org/") a 'pre-made' or packaged router... WOW again, smoothwall Rocks!
Way Easier than centos or SuSE and iptables...
I just might start 'selling' these little compaq/ibm boxes on craigs list.. 

Anyways... I finally have my ONE ubuntu system working... 
~$ route
Kernel IP routing table
Destination  Gateway     Genmask  Flags Metric Ref Use Iface
default    smoothwall-01 0.0.0.0   UG    0      0   0  eth0
blah, blah.... It's actually the first time i've seen linux report a host name 'smoothwall-01' (what i named the router) and not it's ip 10.5.0.1,,, hmm...

So, just incase someone else is the tries too hard type, here's A answer

Landis.

---

### Post by LandisTwo on 2012-02-03
NOPE...
Everything looked fine, acted fine, but... 
After reboot I have NOTHING.
i get 'Waiting for network configuration' then again 'waiting up to 60 secs more...'
-ifconfig -a |more
eth1 No IP assigned (onboard - disabled in BIOS)
lo , well it's local
-then there's this:
rename2 (the interfaces name)  Link encap:Ethernet HWaddr 00:a0:c9:dc:12:9d
- this is my add-on nic, the one I supposedly 'reconfigured' with static ip and that 'saw' my smoothwall-01 router by name and had the right ip and gw... 
Now, after reboot doesn't even know 'it's name'.. 

??? hmmm

/etc/init.d/networking restart - fails says there are blank entries in /etc/network/interfaces

I'm about to give up on gnome and turn this system into a fedora or another openSuSE

Landis...

---

### Post by LandisTwo on 2012-02-03
Question, anyone:

sudo lshw says that network: 0 is my onboard which NetworkManager and ifconfig say is eth1 
-and
network: 1 the add-on nic is an intel and is Disabled??? by What? 
'the lights are on, but nobody's home' i guess....

I've now deleted the add-on nic (intel) from NetworkManager, but I'm afraid that's just a 'connection' like Microsucks Windows and has NOTHING to do with the actual config of the nic... Re-Booting, we'll see.. 

ever watch 'Archer'... pretty funny, it's on in the background.. just asking, don't really care.

This is Not the first nic ubuntu has killed... 9 and 10 both have decided not to use nics before, once in this system (that's why there is an add-on nic) and once before in the system this one replaced...

Rebooted, still no network and eth (intel, add-on) is still named 'rename2' in ifconfig

I'm shutting down, removing inel (add-on) and re-enabling the onboard. IF that doesn't work, you'll only see me back here once more (lucky you), to tell you what I think of gnome!

Landis.

---

### Post by LandisTwo on 2012-02-03
well,,, eth1 (onboard) with static ip set in NetworkManager still has NOTHING assigned when I do ifconfig -a

-and
'rename2' is still there

-and NetworkManager says there is only one connection, eth1 (the onboard)

-and /etc/network/interfaces still has just auto lo, iface lo inet loopback.. 

I'm Done!

Bye.
Landis.

---

### Post by LandisTwo on 2012-02-03
Morning, 
OK, answer me this...
I shut down the system so I didn't throw it and went to bed.
Woke up, coffee, smoke.
While I was sleeping, downloaded fedora KDE and Slackware ISO's.
Burning ISO, meanwhile,
I re-disabled the onboard broadcom ethernet, 
Turned on PC
Ubuntu 11.10 didn't complain about 'waiting for network....'
(remember, add-on intel was deleted last night (this morning) and onboard disabaled)
I went to NetworkManager> Connect Ethernet was there, hmmm..
I opened NM> Add and wow, there is my add-on nic (intel) MAC again???
Added a connection using it, assigning static ip and dns.. 
All looked good in NM and console ifconfig, But it did lastnight too after the First time I added static IP to add-on nic.. 
So, I re-booted just to be safe and before checking anything, I launch FireFox and restored session, 1st tab, WABCRadio.com, Started listening to Rush Limbaugh right away.... 

HMMMMM... ?????

Working! Don't know why and now I have 2 more distro on DVD? 
What to do?
I don't like gnome, but I hate windows 7 too, but I like to have a system around that someone might need 'help' with, even though that is not what I do... You know, people think if you 'work on' computers, you are more than happy to be their 'it guy'... 
Yeah, my acc... LOL

I have NO idea what I did or is it just one of those things that 'fixed themselves' ??

Thanks for listening.
Landis.

---

