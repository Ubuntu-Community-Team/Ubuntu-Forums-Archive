---
title: "I need help seeting up internet via a wired connection"
date: 2011-02-28
forum: Networking &amp; Wireless
---

### Post by raz_atoth on 2011-02-28
Greetings friends,
 As the title says,i need your advices on setting up my internet access.I have a small home network with one router and two computers.One of the computers runs Windows 7 and connects to internet just fine.The other one runs Ubuntu 10.10
I tried at first editing file /etc/network/interfaces to enable access with dhcp
[PHP]
auto eth0
iface eth0 dhcp
[/PHP]
I got this error message wheni issued /etc/init.d/networking restart

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


Then,i tried assigning a static IP address:
[PHP]
auto eth0
iface eth0 static
address 192.168.0.101
netmask 255.255.255.0
gateway 192.168.0.1
[/PHP]
After /etc/init.d/networking restart the network became visible(the other PC started responding to ping),but there is still no internet access.

Am i missing something obvious here?Any help would be appreciated! :)

Thank you.

---

### Post by chili555 on 2011-02-28
> Then,i tried assigning a static IP address:
```
auto eth0
iface eth0 static
address 192.168.0.101
netmask 255.255.255.0
gateway 192.168.0.1 
```
After /etc/init.d/networking restart the network became visible(the other PC started responding to ping),but there is still no internet access.
If you supply a static IP address and network, et al, then you are responsible to supply DNS nameservers. Please edit /etc/resolv.conf to add:```
nameserver 192.168.0.1
```Is Network Manager running on this system? Usually, NM will interfere with manual methods making connection difficult to impossible.

---

### Post by raz_atoth on 2011-02-28
I tried editing /etc/resolv.conf,still no joy i'm afraid :(
And yes,NM is running.How exactly do i stop it?I tried killing the NetworkManager process,but it was simply restarting(restarted).

On a side note,how does the network manager works?I tried setting up from Preferences->Network Connections a connection with the same details as above (address:192.168.0.101;gateway:192.168.0.1) and set the DNS servers field to 192.168.0.1,while keeping the Connect automatically checkbox marked.I also modified file interfaces to:
[PHP]auto eth0
iface eth0 manual
[/PHP]  
It didn't seem to do anything,as,after a restart,the output of ifconfig eth0 revealed the eth0 interface was unconfigured?

---

### Post by chili555 on 2011-02-28
NM is set up too *ignore* any interfaces listed in /etc/network/interfaces, except loopback, of course. The trouble is, it doesn't work too well with mixed manual and automatic methods, as you've found. I'd suggest you eliminate everything in System > Preferences > Network Connections and remove the eth0 lines in /etc/network/interfaces and reboot, in order to restart networking, NM and your ethernet driver reliably. Then click the NM icon and ask the wired interface to connect.

If you are working with a desktop computer that is not ever going to be hauled down to the coffee shop/library/etc., I'd suggest you remove NM entirely and set up your details as above. None of my desktop computers run NM.> I tried editing /etc/resolv.conf,still no joy i'm afraid Can you still ping the other computer? The router?

---

### Post by raz_atoth on 2011-02-28
It's actually a laptop,so i'd prefer to keep NM :)
One odd thing i noticed is the router doesn't respond to ping when i set file interfaces to:
[PHP]auto eth0
iface eth0 static
address 192.168.0.101
netmask 255.255.255.0
gateway 192.168.0.1[/PHP]
The other computer from the network does (and it's shared files can be accessed using samba)

Now,as i said above,this is a laptop.The router is actually a wireless router.If i have the wireless connection enabled on the laptop everything works fine.Both the router and the second PC respond to ping,the internet works. If i try to connect using the wired connection(after i turned down the wireless and wired the laptop) the router doesn't respond to ping, no internet.The other computer does reply to ping,though.Any ideas why?

Thanks.

---

### Post by chili555 on 2011-02-28
> The other computer does reply to ping,though.What tha...?

Do you mean that, from this computer, you can get ping returns:```
ping -c3 192.168.0.theother
```That's weird. 

When you eliminate all manual settings, doesn't it connect with ethernet through NM?

---

### Post by raz_atoth on 2011-02-28
That's correct.
If i issue something like ifconfig eth0 192.168.0.101 netmask 255.255.255.0
i get a ping response [as in ping 192.168.0.100 -which is the desktop,the other pc from the network].If i ping the router [ ping 192.168.0.1],nothing.

And no,if i eliminate all manual settings (i assume you mean by this reverting file interfaces to:
[PHP]auto eth0
iface eth0 manual[/PHP] ?),NM doesn't connect by itself.

---

### Post by chili555 on 2011-02-28
> if i eliminate all manual settings (i assume you mean by this reverting file interfaces to:I mean by eliminating all, every and any manual settings so that *interfaces* reverts to:```
auto lo
iface lo inet loopback
```Then restart networking and NM:```
sudo /etc/init.d/networking restart
sudo /etc/init.d/network-manager restart
```Now click the NM icon and direct it to connect to the wired network. Does it?

---

### Post by raz_atoth on 2011-02-28
I finally figured it out.Here's what went wrong.I configured the router to allow access to network based on MAC filtering.I had two MACs on my white-list.The mac of my desktop and the mac corresponding to my laptops's _wireless_ interface.Nonetheless,i tried to connect using the wired interface which,obviously has a different mac.As soon as i added it to the allowed list in my router's configuration,it worked like a charm.

All this,though,brings an interesting question.As i told you,i was able to ping and see the shared files of the desktop even though the Mac wasn't on the allowed list,thus,theoretically it shouldn't been considered part of the network.How was that possible?Some bug in the router's firmware?

---

### Post by raz_atoth on 2011-02-28
Btw,thanks chili555 for all your assistance!Much appreciated. :popcorn:

---

