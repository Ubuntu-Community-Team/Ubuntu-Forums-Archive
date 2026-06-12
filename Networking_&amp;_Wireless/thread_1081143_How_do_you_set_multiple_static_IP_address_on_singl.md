---
title: "How do you set multiple static IP address on single Ethernet Card?"
date: 2009-02-26
forum: Networking &amp; Wireless
---

### Post by bearslumber on 2009-02-26
Hi'

I currently connect my laptop to the network at work with static IP of 192.168.0.X. for eth0.
  
I also need to connect the same laptop to my ethernet home hub which has a DHCP server that allocates addresses in the range 192.168.1.X.

Can I set eth0 to several IP addresses, and/or a combination of DHCP and Satic IP addresses, so that I can move between the networks seemlessly? If so How.

Any help will be greatly appreciated.

Regards

Bearslumber

---

### Post by albandy on 2009-02-26
you can create profiles in network manager.

also you can assing multiple ip's to one interface but I'm not sure if you can combine dhcp and static.

or you can make an script that detect if exist a dhcp server and use it or asing a static IP.

For example
asing static ip to your interface
then do a ping to gateway
if no ping answer call to dhclient

and you can also asing an ip manually from command line, for example:
ifconfig eth0:0 192.168.0.x/24
route add default gw 192.168.0.1 dev eth0:0

---

### Post by Vishal Agarwal on 2009-02-26
You can do it. I don't remember the actual syntax. But you can install the webmin package and with the help of that you can create virtual LAN card with the required Ip addresses (DHCP os Static) Webmin has other good utilities also.

[Webmin]("http://webmin.com/")

---

### Post by superprash2003 on 2009-02-26
like albandy says , there are network profiles.. configure your settings ( static ip etc ) when you are on wifinetwork1 . .. then when your away from wifinetwork1 and next to wifinetwork2, your ubuntu machine should automatically be able to find wifinetwork2 ( when you click on the network icon ) then it may ask for password.. enter password.. then you would be connected to wifinetwork2.. now when your back to wifinetwork1 , it either will automatically connect to wifinetwork1 or you may have to choose it when you click on the network icon on the top pane of the desktop.. but you dont need to configure ip,gateway etc again

---

### Post by bearslumber on 2009-02-27
Thank you everyone for your quick response. Much appreciated.

Here is what has happenned so far...

I Tried Albandys first suggestion to use "Network Manager". At this point, the ability to have profiles sounded like the best solution. The exact app did not appear in my menu. After a while, I found it in "Applications->Add/Remove" and installed it from there but it still did not appear in my menu. I searched for the same in Synaptec Package Manager, and found it. I looked for the installed files to find the command, and I found > 1. /usr/sbin/NetworkManager
2. /usr/sbin/nm-system-settings
3. /usr/bin/nm-tool

1. Launching NetworkManager from the command line did nothing visibly.
2. Launching nm-system-settings gave me a warning > ** (nm-system-settings:14934): WARNING **: No plugins were specified.
3. Launching nm-tool responded with the status of my current connections. "Basically Not connected".

I decided to try the tools I had already tried and that was "network-admin" launched via System->Admin->Network. This allowed me to set up a pan0 network with roaming enabled. At the top of the dialogue box it gives the option for "Locations" and I guessed this must be the equivalent of "profiles". So I typed in a location name and saved it. This caused the dialogue biox to disapear. Upon relaunch the location I had set was nowhere to be seen and the pan0 network seemed dead. Clearly there is something wrong because the location seemed to be buggy.

I then found a netwrok selector tool which worked with network-admin because it detected pan0 but selecting pan0 did nothing.

I then decided to look at Vishal Agarwals suggestion and install webmin. This looked good, but selecting Network Configuration->Network Interfaces->Add New interface does not give me the option to set up an interface that uses DHCP. I am guessing that this is because I already have 1 static address set up for eth0. Webmin does not allow setting another IP for eth0. So I am stuck.

I read Superprash2003's tutorials but they concentrated on wireless networks which I already have running smoothly, so thanks for the help, but my aim is to get a similar setup on wired networks.

Anty further help would be greatly appreciated.

regards

Bearslumber

---

### Post by kevdog on 2009-02-27
Not sure if this is still relevant, however maybe this will help: [http://ubuntuforums.org/showthread.php?t=683076](http://ubuntuforums.org/showthread.php?t=683076)

---

### Post by freonchill on 2009-03-28
i was playing around with this today,

i want to set eth0 in network manager to have 2 different IP's

IP      192.168.1.2
subnet  255.255.255.0
gateway 192.168.1.1

IP      192.168.2.2
subnet  255.255.255.0
gateway 192.168.2.1

now, i see [http://www.dedoimedo.com/images/computers/ubuntu-8.10-network-1.jpg](http://www.dedoimedo.com/images/computers/ubuntu-8.10-network-1.jpg) you can put in multiple IP addresses for the same piece of hardware. (with their own respective subnet and gateways)

the problem i have is that even though i set it to TWO different IPs it only shows the FIRST on connection information

is there something further i need to setup? (e.g. the routes button, above linked image)

thanks,

---

### Post by freonchill on 2009-04-03
bump

---

### Post by bearslumber on 2009-04-23
Hi,

After banging my head against a wall, and nearly giving up, I contacted the [Network Manager mailing list]("http://projects.gnome.org/NetworkManager/") and I now have a response.

It boils down to the /etc/network/interfaces 

configuration settings. It had an entry for eth0 which was entered (I guess) during installation, which meant running nm-tool on the command line reported eth0 as "unmanaged". 

I removed all entries in /etc/network/interfaces and presto!!!

freonchill:

Hopefully this resolves your issue too. If not I suggest contacting the [Network Manager mailing list]("http://projects.gnome.org/NetworkManager/").

**NOTE:** This solution contradicts the solution in Kevdogs thread.

Everyone; Many thanks for your help.

Regards

Happy Bear, no longer lumbering.
:P

Bearslumber

---

