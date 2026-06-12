---
title: "Network Drops with No Arp Replies from Router"
date: 2012-06-03
forum: Networking &amp; Wireless
---

### Post by SparTacux on 2012-06-03
I've got a laptop connected to 4 port modem router using a static ip address. The laptop connects to the local network ok but loses internet connectivity after a short while and all downloads stop hence I can't update via update manager without the whole thing coming to a stop. 

When the network connectivity on the laptop fails:
Wireshark, on the laptop, shows the laptop doing an ARP request "who has 192.168.0.1" but doesn't get any reply from router. Another computer on the same network, also running wireshark, see's the ARP requests ( for the router ) from the laptop.

If I ping another computer from that laptop the computer see's the ping requests and responds with a ping reply. The laptop doesn't get the ping reply either.
The only thing that corrects the problem is to do a full reboot on the laptop which restores the network connectivity. Things will work fine for a while but then it will go down again,  mainly when using the  internet and sometimes during printing.

I'm not sure what's causing this but maybe I can fix it by using the arp -s command in terminal and setting up static arp entries or doing the same thing in a boot up configuration file.
Anyone got any ideas on what's causing the problem?

---

### Post by SparTacux on 2012-06-03
Ok - the Good news is that manually setting up the LAPTOP Arp entries for the router and other computers on the network did solve the problem. I now need to know how to do this on a permanent basis on boot up so that I don't have to type each ip and mac address for all the computes on the network:

sudo arp -s 192.168.0.1 <mac address of router>
sudo arp -s 192.168.0.2 <mac address of computer 1>
sudo arp -s 192.168.0.3 <mac address of computer 2>

Which boot up files do I edit?

---

### Post by SparTacux on 2012-06-03
Apparently there are two ways of doing it.
One is to edit the /etc/rc.local file and put the arp -s statements in there. This works on boot up and gives permanent arp entries but if you bring the network down then you lose the static arp entires.

The second way is to create a new staticarp script file in /etc/network/if-up.d/ and put your arp entries in that new file. This way works a treat as if you bring the network down and bring it back up again the static arp entries are still there.

/etc/network/if-up.d/staticarp

#!/bin/sh

arp -s 192.168.0.1 00:00:00:00:00:00
arp -s 192.168.0.2 00:00:00:00:00:00

and so on. replace the 00:00:00:00:00:00 with your mac addresses.
Use sudo chmod +x/etc/etc/network/if-up.d/staticarp to make the file executable. Job Done.

This is a work around to my disconnection pronlems. I didn't find out what was causing it in the first place.

---

### Post by Drenriza on 2012-06-03
What is this for a strange problem? :)

#1 > ARP request "who has 192.168.0.1" but doesn't get any reply from router
Okey. Your trying to "talk" with 192.168.0.1. Does 192.168.0.1 have a 255.255.255.0 network mask? What ip address does your laptop have and what network mask does it have?

> Another computer on the same network, also running wireshark, see's the ARP requests ( for the router ) from the laptop.
Makes sense since the ARP request "Who is X" is a broadcast message. So all the devices on the same local network, not divided by a 3'rd layer device should see it. But only the device with the X address will respond. All others will drop the package.

#2 > If I ping another computer from that laptop the computer see's the ping requests and responds with a ping reply. The laptop doesn't get the ping reply either.

I don't get this. If you ping any host on the local network, do you get a successful ping (a reply) or a failed ping (no reply)?

If you don't get a ICMP reply. What is the ip address and network mask for the laptop your pinging from (source), and what is the ip address and network mask for the device your trying to ping (destination).

Edit.
> This is a work around to my disconnection pronlems. I didn't find out what was causing it in the first place.
It's not really a solution if you don't know the cause. From what i have read it does not sound like a Linux issue. So fixing it with a Linux "fix" is a no no in my world. Let me know if you wan't help to find the cause, in your network.

---

### Post by SparTacux on 2012-06-03
Hi Drenriza..

I agree this is not the best solution to this problem but it did work. I'm an engineer by trade & nothing to do with IT. My solutions usually involve a bit of oil and grease, turn a few screws , and a bit of a clean up   ;-)

I've had this problem on the one laptop for months and put up with it by rebooting it when I needed to. I don't use it for internet use - it's just there for my syslog from my router and also acts as a print server. When I need to do updates - it goes "down". In the end I tried out wireshark on it to pin point the problem and found it wasn't getting any arp replies from the router ( 192.168.0.1 ) The ip address for the laptop is 192.168.0.220 and subnet mask is 255.255.255.0  It also didn't get any arp replies from any other computers that were trying to print to the printer attached to the laptop. 

Whan i tried pinging other computers on the network the ping request reached those computers but no reply came back to the laptop. When the network is running normally there are no problems with arp replies from the router or ping replies from other other computers. 

My guess is that the source of the problem is either the laptop itself or maybe the router. None of the other computers on my network have any problems. All computers on this network are using static IP's with subnet mask of 255.255.255.0

If you think you know what may be the problem or a better fix then please advise.

---

### Post by Drenriza on 2012-06-03
It just sounds so very strange. Since you only use the ICMP ARP replies and ACK,s to build the MAC table. And then you use the MAC address to communicate on the local LAN.

Without having info about the network and being able to go through it myself it's hard to pinpoint the problem.

I'am so curious that if you set up a team viewer session i'll take a look. Else i would take a closer look at the router / switch your using.

Quick thought.
If you have assigned static ip addresses to all the machines on the network, does any of them have the same ip?

---

### Post by SparTacux on 2012-06-03
> **Drenriza said:**
> It just sounds so very strange. Since you only use the ICMP ARP replies and ACK,s to build the MAC table. And then you use the MAC address to communicate on the local LAN.

Without having info about the network and being able to go through it myself it's hard to pinpoint the problem.

I'am so curious that if you set up a team viewer session i'll take a look. Else i would take a closer look at the router / switch your using.

Quick thought.
If you have assigned static ip addresses to all the machines on the network, does any of them have the same ip?

Yes - it's a weird one. 

I don't know how long the arp entries stay in the arp table before they get refreshed but I did spot the router asking who is 192.168.0.220 quite a lot of times even when the network was running ok. It seemed as if the router wasn't getting a reply or it wasn't keeping hold of the mac details for a long enough period.  In the end I decided to artificially give the laptop all the IP and MAC details using the arp -s command. So far so good- It did a full download of the latest updates without dropping out.

All the computers have different static IP addresses that's for sure. I did change the WAN side mac address of the router ( quite some time ago ) from it's default setting to a MAC that may be on a computer on my local network. I did this to avoid me using a WAN MAC that someone else on the internet may be using. I'm not sure if this could cause a problem or not.

---

### Post by Drenriza on 2012-06-06
"WAN MAC"? On the WAN you don't use MAC addresses to communicate. Based on the technology of your ISP you use a layer 2 based communication, yes. But not MAC addresses, so i would not worry about a device on the WAN having the same MAC address as your gateway / bridge device.

Besides, the MAC address is a 32bit hexadecimal ROM address. With over 4 billion combinations, so in theory could two devices have the same exact MAC address? Yes, but extremely unlikely.

To answer the question if this is the issue, probably not.

And when a firm start to produce products, they get a range of the scope (4 billion addresses). And from this scope they give their devices addresses. So also for two devices to have the same address the firm needs to go through the scope, and start from the beginning of their address range and then two devices will end up with the same MAC address. But by the time the firm has ran through their scope, years have passed. And consumer products have been changed long before that.

Is their a 192.168.0.220 device on your local lan?

Do you have "flapping links" on some of your devices? Link that goes up and down in rapid sessions of each other. This could have a less positive effect on your network.

---

