---
title: "Installing from live CD but not connected to the internet"
date: 2012-04-28
forum: Networking &amp; Wireless
---

### Post by Internaltheory on 2012-04-28
Ok, I am completely new to linux. Please bear with me if I post or do anything wrong. I have a Dell Dimension XPS t700r and I am trying to install Lubuntu 12.04 from a live CD that I burned. I am able to get Lubuntu to load from the CD and I want to install it to my hard drive. What is happening is that it is not connection to the internet and I want to get it all connected before I install to the hard drive so it can update and whatnot. I have NO clue where to even start with this. I have tried to search and just can't seem to find what I need to do. 

Here is what I am working with:
Setting up a wired Ethernet connection. Did [code] lspci. Told me Ethernet controller is: ADMtek NC100 Network Everywhere Fast Ethernet 10/10.
I am connecting to a Belkin N150 router. 
I use a DSL cable modem through my internet provider which is Charter.

I don't know if this is of any importance but I have another computer that is connected to the router as well that is running Windows 7 64bit. It connects just fine to the internet.

Where do I start? Please be very specific if you're telling me to click on something, I have never used linux before. I know how to get to the terminal. I also tried to add a  wired network connection, method: manual Address: 192.168.2.4 Netmask: 225.225.225.0 Gateway: 192.168.2.1 DNS server: 192.168.2.1 says it's wired network connection is active but still no internet.

---

### Post by marinara on 2012-04-29
I'm not sure, but you might need special drivers for your laptop.
Do you live somewhere with a local linux user group?
also you might try posting in the beginners forum.

---

### Post by marinara on 2012-04-29
i found info for your network card: apparently it doesn't require a driver.
[http://www.linuxquestions.org/hcl/showproduct.php/product/4302/cat/all](http://www.linuxquestions.org/hcl/showproduct.php/product/4302/cat/all)

sorry i can't help ya more

---

### Post by chili555 on 2012-04-29
First, so that we know the specific details of the card, open a terminal and run and post:```
lspci -nn | grep 0200
```The pipe symbol | is on the right side of my US keyboard on the same key with \.

Next, let's see if there any clues in the kernel messages:```
dmesg | grep -e tulip -e eth
```Thanks.

---

### Post by Internaltheory on 2012-04-29
> **chili555 said:**
> First, so that we know the specific details of the card, open a terminal and run and post:```
lspci -nn | grep 0200
```The pipe symbol | is on the right side of my US keyboard on the same key with \.

Next, let's see if there any clues in the kernel messages:```
dmesg | grep -e tulip -e eth
```Thanks.


Ok for this is what I got when I ran [FONT=&quot]lubuntu@lubuntu:~$ lspci -nn | grep 0200

00:0e.0 Ethernet controller [0200]: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 [1317:0985] (rev 11)
[/FONT]

And this is what I got when I ran lubuntu@lubuntu:~$ dmesg | grep -e tulip -e eth

[FONT=&quot] [    0.085143] i2c-core: driver [aat2870] using legacy suspend method
[    0.085152] i2c-core: driver [aat2870] using legacy resume method
[   17.197925] tulip: Linux Tulip driver version 1.1.15 (Feb 27, 2007)
[   17.198551] tulip 0000:00:0e.0: PCI INT A -> Link[LNKB] -> GSI 10 (level, low) -> IRQ 10
[   17.198602] tulip: tulip_init_one: Enabled WOL support for AN983B
[   17.198994] tulip0:  MII transceiver #1 config 3000 status 7849 advertising 01e1
[   17.246794] net eth0: ADMtek Comet rev 17 at Port 0x1000, 00:20:78:05:f7:14, IRQ 10
[   17.414884] VGA switcheroo: detected Optimus DSM method \ handle
[   94.548577] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  119.600055] eth0: no IPv6 routers present
[  532.193810] tulip 0000:00:0e.0: eth0: tulip_stop_rxtx() failed (CSR5 0xfc664010 CSR6 0xff972117)
[  532.193836] net eth0: Setting full-duplex based on MII#1 link partner capability of cde1
[  543.616079] eth0: no IPv6 routers present
[  592.632083] eth0: no IPv6 routers present
[  903.360065] eth0: no IPv6 routers present
[  951.600062] eth0: no IPv6 routers present
[  999.496053] eth0: no IPv6 routers present
[ 1047.184062] eth0: no IPv6 routers present
[ 1392.520099] eth0: no IPv6 routers present
[ 1440.680058] eth0: no IPv6 routers present
[ 1488.704082] eth0: no IPv6 routers present
[ 1536.816095] eth0: no IPv6 routers present
[/FONT]

---

### Post by chili555 on 2012-04-29
> [ 94.548577] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 119.600055] eth0: no IPv6 routers present
[ 532.193810] tulip 0000:00:0e.0: eth0: [COLOR="Red"]tulip_stop_rxtx() failed[/COLOR] (CSR5 0xfc664010 CSR6 0xff972117)
[ 532.193836] net eth0: Setting full-duplex based on MII#1 link partner capability of cde1
[ 543.616079] eth0: no IPv6 routers presentIt's trying! I have been Googling the highlighted message with no result.

I also saw this: [http://ubuntuforums.org/archive/index.php/t-858226.html](http://ubuntuforums.org/archive/index.php/t-858226.html) As you can see, I was picking tulips even back then! As suggested, please try:```
sudo modprobe -r tulip
sudo modprobe tulip options=5
```If it helps, we can write a conf file in the final install.

Of course, a newer, better-supported NIC card wouldn't break my heart, either. I will be happy to work with you in any case.

---

### Post by Internaltheory on 2012-04-29
> **chili555 said:**
> It's trying! I have been Googling the highlighted message with no result.

I also saw this: [http://ubuntuforums.org/archive/index.php/t-858226.html](http://ubuntuforums.org/archive/index.php/t-858226.html) As you can see, I was picking tulips even back then! As suggested, please try:```
sudo modprobe -r tulip
sudo modprobe tulip options=5
```If it helps, we can write a conf file in the final install.

Of course, a newer, better-supported NIC card wouldn't break my heart, either. I will be happy to work with you in any case.

I ran that and in the top right hand corner a box popped up with the up and down arrows saying:
"Wired Connection 2 
connection established"
I still get no internet connection. When I did that it stopped access to my windows 7 computer. In windows I right clicked on the network icon in the system tray and selected troubleshoot the problem, it connected again, but I can't remember what it had said it fixed. I accidentally closed it. 


I know I am dealing with dinosaur parts here, :). I do have a Netgear FA311 Rev-B1 ethernet card from another computer I could try. Would that be any better?

---

### Post by chili555 on 2012-04-29
I would certainly try another card if I could.

---

### Post by Internaltheory on 2012-04-29
I switched the network cards and it worked!! I have been messing with this thing for 3 days and that's all it took. :rolleyes: While I can ask, what do you think about running Lubuntu on the machine. 
Specs: 
Dell Dimension XPS t700r
384mb RAM
Pentium III
700mhz
40GB HD

I looked online and I know Lubuntu is super light and it should run without a problem, but I just wanted to run it by an expert user. For now I plan on using it just so I can get some facetime with the OS, you know learn something new. I realize that the computer is older than the hills and might need an upgrade eventually. Any ideas on something cool I can do with it?

---

### Post by chili555 on 2012-04-29
Awesome! Glad it's working!

I'd try the live CD and if it runs acceptably for you, then I say go for it. It will be a bit slow with the limited RAM but I think it will run well enough. I've run on less!

You could use it as a back-up server, a print server or as a machine for guests in your home to be able to check emails and good old Facebook. Most of all, you can learn how to use Ubuntu and you may find, as I have, that it does everything you need to do without paying for Windows. Make no mistake, when you buy a new computer, you pay for Windows.

Have fun!

---

### Post by Internaltheory on 2012-04-29
> **chili555 said:**
> Awesome! Glad it's working!

I'd try the live CD and if it runs acceptably for you, then I say go for it. It will be a bit slow with the limited RAM but I think it will run well enough. I've run on less!

You could use it as a back-up server, a print server or as a machine for guests in your home to be able to check emails and good old Facebook. Most of all, you can learn how to use Ubuntu and you may find, as I have, that it does everything you need to do without paying for Windows. Make no mistake, when you buy a new computer, you pay for Windows.

Have fun!

Thanks for your help and suggestions. I have come across another issue but I am going to post in in the proper thread and mark this as solved. :)

---

### Post by Internaltheory on 2012-04-29
Thanks to everyone who tried to help I appreciate it!

---

