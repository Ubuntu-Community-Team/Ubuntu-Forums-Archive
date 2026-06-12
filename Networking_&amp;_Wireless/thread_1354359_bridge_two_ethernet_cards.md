---
title: "bridge two ethernet cards ?"
date: 2009-12-13
forum: Networking &amp; Wireless
---

### Post by ApEkV2 on 2009-12-13
Hello, I have a computer with two ethernet cards. 
How can I bridge them so one is connected to my router, and the other goes to another computer?

I've tried some bridge-utils tuts, but ultimately couldn't get it to work.

Can someone tell me how to do this, or point me towards a good tutorial?

---

### Post by ApEkV2 on 2009-12-14
bump ?

---

### Post by fibercode on 2009-12-14
If you just want to bridge the two nic's you can use the brctl command. Before you can use it you need to install the bridge-utils package:

sudo apt-get install bridge-utils

From your post it looks like you might already have tried this.

I have not used brctl before, but I have set up a gateway on my computer many times. A gateway will forward network traffic from one nic to the other. You can then "sniff" all the traffic going through. 

If this is all you need then you can use Firestarter:

sudo apt-get install firestarter

You can look at Step 7 of this tutorial. Just substitute wlan0 and eth0 with your interfaces:

[http://dimitar.me/?p=277](http://dimitar.me/?p=277)

I hope this helps :)

---

### Post by Yoann Juet on 2009-12-14
> How can I bridge them so one is connected to my router, and the other goes to another computer?

```

brctl addbr MYBG
brctl addif MYBG ethX
brctl addif MYBG ethY
ifconfig MYBRIDGE up
```

Where MYBG is the name given to your bridge and ethX, ethY the two bridged interfaces.

---

### Post by MaindotC on 2009-12-14
I don't understand why anyone is mentioning anything like bridge utils or anything other than ifconfig.  All you have to do is set an ip address and appropriate mask on the interface connected to the other computer.

For example, I suggest you assign an ip address to the NIC's on your two machines in the 10.1.1.x range.  Once you assign it that ip, it will forward all requests regarding that ip to that NIC, which should be to the other machine that has a 10.1.1.x ip address.

---

### Post by fibercode on 2009-12-14
@strAlan

I am not sure I understand what you are suggesting. Bridging is done on Level 2 of the OSI, therefore it knows nothing about IP addresses, just physical addresses (MAC).

It looks like he is trying to turn his computer into a simple switch device for whatever reason.

If he implements your suggestion, then his computer will be able to communicate with the two networks (connected to each NIC) but any request coming from a computer on network1 (through NIC1) will not be magically forwarded to newtork2(through NIC2) and vice versa.

Again, I might have not read your post correctly, but I would be very curious to find out how to do this without bridging or a gateway.

I think that Yoann Juet's is very close. But I think you need to zero out the IP addresses of the 2 NIC's first:

ifconfig ethX 0.0.0.0
ifconfig ethY 0.0.0.0

and then do:

brctl addbr MYBG
brctl addif MYBG ethX
brctl addif MYBG ethY
ifconfig MYBRIDGE up

---

### Post by ApEkV2 on 2009-12-14
```
sudo ifconfig eth0 0.0.0.0 promisc up
sudo ifconfig eth1 0.0.0.0 promisc up

sudo brctl addbr brg0
sudo brctl addif brg0 eth0
sudo brctl addif brg0 eth1

sudo ifconfig brg0 192.168.1.105 netmask 255.255.255.0 up
sudo route add default gw 192.168.1.1 dev brg0
```


this does not work, and i have already tried it.
the problem i get with that is i can connect to the router, but not the internet.

---

### Post by MaindotC on 2009-12-14
He's not talking about bridging in the OSI sense and I know what he's doing and why, and you don't need any of the things you mentioned.  Just do as I suggested and you'll be fine.  The ifconfig setting will not be permanent - it will wipe out after a reboot - but we can address that if need be.

---

### Post by MaindotC on 2009-12-14
> **ApEkV2 said:**
> ```
sudo ifconfig eth0 0.0.0.0 promisc up
sudo ifconfig eth1 0.0.0.0 promisc up

sudo brctl addbr brg0
sudo brctl addif brg0 eth0
sudo brctl addif brg0 eth1
sudo ifconfig brg0 192.168.1.105 netmask 255.255.255.0 up
```

this does not work, and i have already tried it.
the problem i get with that is i can connect to the router, but not the internet.

Ok look I'll give you the commands you need.  What is the IP address range for the nic connected to the other computer?  The nic connecting to your access point is being assigned an address via dhcp from the access point correct?

---

### Post by ApEkV2 on 2009-12-14
the router assigns ip's via dhcp - 192.168.1.100 ++
i assumed the other nic should be 192.168.0.100 ++ like in firestarter

---

### Post by MaindotC on 2009-12-14
No, you need to assign it an ip from a different subnet range.  I don't know if this brctrl stuff has messed up your connection but if not the following will work.  Assuming the NIC connecting to the other machine is eth1:
```

sudo ifconfig eth1 10.1.1.1

```
Assign the ip address 10.1.1.2 to the other machine.  After that's done, you should be able to put a cat5  cable right between them and any requests for 10.1.1.2 will automatically go out the eth1 interface.

---

### Post by ApEkV2 on 2009-12-14
didn't work. sounded to easy,

it's amazing that windows can do this in four mouse clicks

---

### Post by MaindotC on 2009-12-14
Then you did something wrong or that brctrl stuff he had you install screwed up your network settings.  Post the output of ifconfig.

---

### Post by ApEkV2 on 2009-12-14
```
eth0      Link encap:Ethernet  HWaddr 00:19:5b:c0:89:5f  
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:5bff:fec0:895f/64 Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:78688 errors:0 dropped:0 overruns:0 frame:0
          TX packets:65920 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:87681352 (87.6 MB)  TX bytes:9013787 (9.0 MB)
          Interrupt:19 

eth1      Link encap:Ethernet  HWaddr 00:16:17:8f:e9:9c  
          inet6 addr: fe80::216:17ff:fe8f:e99c/64 Scope:Link
          UP BROADCAST PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:2286 errors:0 dropped:0 overruns:0 frame:0
          TX packets:464 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:168968 (168.9 KB)  TX bytes:32412 (32.4 KB)
          Interrupt:30 Base address:0xc000
```

this is after i
```
sudo ifconfig eth1 0.0.0.0 promisc up
```
because when i did what you said to do, nothing worked

---

### Post by MaindotC on 2009-12-14
Please post your command line output in [code] tags.  As you can see, your eth1 is not showing the assigned ip address of 10.1.1.1 - like I said you did something wrong.  Set it accordingly.

---

### Post by sanemanmad on 2009-12-14
LOL.... I am sorry Stralan, but whatever you are having this fella do is WAY WAY off.

ApEkV2 ~ What are you trying to accomplish?

Please elaborate, I have a very complex setup and may be able to help you replicate what i have if it is what you are looking for.

```
My setup as follows
Internet > Modem > Server (3 NICS)> Internal LAN.

eth0 > gateway to internet
eth1 + eth2 --> bond0 (bonded interface) sends all network/internet requests to eth0 and vice-versa.


```

---

### Post by ApEkV2 on 2009-12-14
I will answer the question, "what am i trying to do" with a picture from windows.

Also this explanation, 
```
eth0 connects to the router, eth1 connects to my xbox
i want both to be able to reach the internet
```

---

### Post by MaindotC on 2009-12-14
> **ApEkV2 said:**
> 
i want both to be able to reach the internet[/code]

This completely changes the situation, and you did not mention this in previous posts.  You can still use the method I suggested but you will need to modify your routing tables using the route command.  All you have to do is tell it to send all traffic from your xbox out the destination NIC - the one connected to your router.

---

### Post by fibercode on 2009-12-14
Ok... here is step by step what you need to do.

When finished you will be able to go on the internet both with your xbox and your computer:

1. Your eth0 interface is connected to the router and has DHCP enabled. It gets its settings from your router's DHCP server. It does not need any changes.

2. Configure your eth1 interface:

Go to System -> Preferences -> Network Connections

Click on the eth1 interface, then hit "Edit". Then hit the IPv4 tab, select &#8220;Manual&#8221; from the &#8220;Method&#8221; dropdown. Hit the &#8220;Add&#8221; button and put 192.168.0.1 for the IP address, 255.255.255.0 for the Netmask and leave the Gateway blank. In the DNS server box put 8.8.8.8 (this is the new google dns server and it is easier just to give you the ip then to have you find your ISP's DNS).
Hit "OK" and your eth1 is configured.

3. You need to configure the NIC on your xbox. Put the following settings:

IP: 192.168.0.2
Subnet Mask: 255.255.255.0
Default Gateway: 192.168.0.1
DNS Server: 8.8.8.8

4. Now you are ready to do the gateway.

Install firestarter if you have not done that yet:

sudo apt-get install firestarter

Go to Internet -> Firestarter

First it will ask you to specify your Internet connected device, so chose eth0 from the dropdown. Click &#8220;Forward&#8221; and in the next screen specify your LAN NIC: eth1, then select the checkbox named &#8220;Enable Internet connection sharing&#8221;. Next click &#8220;Forward&#8221; again, and finally click &#8220;Save&#8221;. This will start the gateway.

You should be good to go.

Now, before I finish... From a network stand point if you are not going to sniff the traffic or implement any kind of firewall on your computer there is no need to do all this. 
You can either connect your xbox directly to your router or if you have no available ports on it you can just buy a very inexpensive switch (you can find them for less then $10) and connect it to the router and then to your xbox and any other equipment you have around your house that you want to put on the network.
Among other things, a big disadvantage of using your computer to provide internet to your xbox is that your computer will have to be up and running every time you want to play online with your xbox. That is a lot of hassle...

Let me know how this turned out for you... :D

---

### Post by ApEkV2 on 2009-12-15
I know how to do this with Firestarter and have done this before, but I am not using Firestarter anymore.

Hopefully there is another way other than Firestarter. (another that works)

---

### Post by ApEkV2 on 2009-12-17
bump. it's been 2 days
I started over, gave eth0 a static ip connected to the internet (external).

I gave eth1 a static ip.....(in the etc/network/interfaces file)```
auto eth1
iface eth1 inet static
    address 192.168.0.1
    network 192.168.0.0
    netmask 255.255.255.0
    broadcast 192.168.0.255
```

Gave the xbox manual settings
192.168.0.107
255.255.255.0
192.168.0.1

Gave it the same DNS addresses the computer uses.
Xbox can't connect to the internet.

Is there a route command anyone is willing to share?

---

### Post by MaindotC on 2009-12-17
You need to configure your xbox to refer to your Ubuntu machine as a gateway. [Ubuntu Internet Connection Sharing](https://help.ubuntu.com/community/Internet/ConnectionSharing).

---

### Post by ApEkV2 on 2009-12-17
I have, I gave the xbox the gateway 192.168.0.1

That guide does not work for me. I did everything right so don't ask

---

### Post by ApEkV2 on 2009-12-20
bump

---

