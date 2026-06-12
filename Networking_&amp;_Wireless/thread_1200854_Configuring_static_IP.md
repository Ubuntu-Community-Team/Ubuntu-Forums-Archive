---
title: "Configuring static IP"
date: 2009-06-30
forum: Networking &amp; Wireless
---

### Post by Chetan26 on 2009-06-30
Hi ,
     Iam trying to configure staticIP on UBuntu 8.1 .
     Iam using the following   changes in /etc/network/interfaces

   auto lo eth0
   iface lo inet loopback
   iface eth0 inet static
   address 81.142.10.xxx
   netmask 255.255.255.0
   gateway 192.168.1.150



When I restart the networking Iam not able to connect to the internet.
We are using Router initially for dynamic IP  but now iam unable to connect to the internet.
 

Do I need to make any changes to the router setup?

Please provide some guidance.

Thanks
Chetan

---

### Post by Bucky Ball on 2009-06-30
Probably. You need to stop your router from attempting to serve you an IP. The DHCP server is probably doing that so you have the router sending you one and you attempting to send a different one back and ... crash.

Make sure you have the appropriate IP for the router and gateway at your end on the Ubuntu box. Make sure you have the IP address of the router noted down if it is unusual BEFORE switching off the DHCP server on it as if there are problems you will need to get back into the router config to tweak it.

* There is a GUI in System->Admin->Network if you prefer ...

---

### Post by Chetan26 on 2009-06-30
Hi ,
      Thanks I have got a static Ip for the router as well.
      How can I configure it ?


Thanks
chetan

---

### Post by Bucky Ball on 2009-06-30
Open your browser (firefox or whatever) and type the IP into the address bar (you might need to use 'http://192.168.xxx.xxx or whatever your IP is rather than just the number but from memory both work). Might be an idea to grab the manual for the router at this point.

---

### Post by chili555 on 2009-06-30
I think it is highly doubtful that your router will give you an 84.142.x address. Unless you have done some fancy footwork, I even doubt that the gateway is 192.168.1.150. I suggest you set the *interfaces* file back to DHCP:```
auto lo 
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
```Then restart networking:```
sudo /etc/init.d/networking restart
```See what address the router gives you. You can also verify the address of the router, i.e., the gateway. Here is an example:```
DHCPOFFER of 192.168.1.105 from 192.168.1.254
DHCPREQUEST of 192.168.1.105 on eth1 to 255.255.255.255 port 67
DHCPACK of 192.168.1.105 from [COLOR="Red"]192.168.1.254[/COLOR]
bound to 192.168.1.105 -- renewal in 41358 seconds.
```I am quite sure it is going to be in the 192.168.1.xx range.

You will have to get into the administration pages of the router to see what the range of IP addresses the router hands out. If, for example, the DHCP server in the router is set for 20 addresses starting at 192.168.1.100, then you can safely set a static IP address in *interfaces* of 192.168.1.130.

---

### Post by limar on 2009-07-02
When I change the network settings in the GUI everything works fine and the static ip is given to me. No problem there.

But why doesn´t it change the interfaces file? I should say that the GUI changes the the interface file. But instead it only says:

auto lo
iface lo inet loopback

Nothing about the ip-adres, gateway or whatsoever I entered in the GUI.
Why is that? Do they work seperately?
Can somebody explain?

---

### Post by chili555 on 2009-07-02
I suspect the GUI you are changinging is Network Manager. NM keeps its own set of configuration details and does not depend on */etc/network/interfaces.* If your static IP is working well for you, there is no need to change anything.

If you have a desktop computer that has no need to select from different networks like, for example, the coffee shop or University, then you may safely remove NM through Synaptic and set up */etc/network/interfaces* something like this:```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.108
netmask 255.255.255.0
gateway 192.168.1.254
```Please post back if you need more help.

---

