---
title: "No internet connection on wired LAN"
date: 2009-07-01
forum: Networking &amp; Wireless
---

### Post by zer010 on 2009-07-01
First of all, I have a WIRED LAN, NOT wireless.  My main computer (comp1) is connected to the internet via cable modem, which I recently got the connection working. Comp1 has 2 NICs, one connected to the cable modem, and the other one  connected via crossover to Comp2.  I had been able to (finally) share internet with Windoze so I know my cable/connections are good.  Now that I have ditched Win, and are running Ubuntu 9.04 on both Comps,  I am having trouble getting an internet connection on Comp2.  I have tried to edit the connection mannually, but to no avail. It doesnt help that I am a little under-educated when it comes to the nitty-gritty of the technical underpinnings.  I am still quite new to the shell as well, but do have a natural commonsense ability to follow along with info/advice.  Any help would be greatly appreciated!

---

### Post by t0mppa on 2009-07-01
Not really an expert on wired connections, but since it's summer and the regular helpers appear to be on holidays, here's an idea to get you started.

Run **route** on the terminal of both boxes and check that the routings are correct. You'll want the comp2 to have a default route that has the comp1's second NIC IP as gateway and comp1's NIC's to bridge the traffic from second NIC to the first, when the destinations are outside your local network.

The man command and Google are your friends, if you need to study how standard Linux commands like these work and what they do, so I'll leave the details for better tutorials.

---

### Post by Boondoklife on 2009-07-01
Did you manualy set an ip for both linux boxes on the cards that will be sharing the connection? Can you give a bit more detail on your ip settings for both boxes? can you post the output of ifconfig -a for both boxes

---

### Post by Iowan on 2009-07-01
If you had it working with a Windows box it *should* be as simple (never quite that simple) as setting up a manual address in Network Manager with comp1 as the gateway.  (Oh, DNS servers will need to be referenced in */etc/resolv.conf*)

---

### Post by zer010 on 2009-07-02
First, I only had a LAN working with 2 Win boxes, which only requires to run a Network Wizard.  

Next, using GNOME, I set up my secondary eth on comp1 as : IP 198.168.0.1, Subnet mask 255.255.255.0, Gateway 0.0.0.0.  On comp2 I set it up as: IP 198.168.0.2, Subnet Mask 255.255.255.0, Gateway 198.168.0.1.  The Network Manager says that the connection was established, but apparently not for internet sharing.  Maybe I should look into bridging the two NICs on comp1? I tried to find some info on google, and I found suggestions to use Firestarter as a means to do what I want. I would much rather get this connection going without an interim application.  Im thinking that using a router would also be easier, but as I said, I would rather get a basic connection first before I move on to hardware and software solutions.  Also, for some reason (probably my monkeying around), in the Network Connections, I have a listing for eth0(normal), Auto Ethernet(should be eth1), and another Auto Ethernet(should be eth2). I think I will be reinstalling 9.04 before to long because of my messing around. After I do, i will post the ifconfig data here.  Thanks for the replies and y'alls time!

---

### Post by superprash2003 on 2009-07-02
you should take a look at this [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing) .. before that , establish a connection between comp1 and comp2.. enter ips manually like 192.168.0.1 and 192.168.0.2 .. ensure that they can ping each other first..

---

