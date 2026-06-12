---
title: "Networking Ubuntu and Windows"
date: 2010-10-23
forum: Networking &amp; Wireless
---

### Post by DaGeek247 on 2010-10-23
I have one computer, one running Ubuntu 10.04. My brother has a windows XP desktop instead of Ubuntu. Neither of them have internet, or a router/switch of any kind. All I have is an ethernet cord, and a two serial cords. How would I get them to have a one-to-one network?

I would like to have a network between them to have a coop game of [Assault Cube]("http://assault.cubers.net") and a coop edit with the [Platinumarts Sandbox Gamemaker]("http://www.sandboxgamemaker.com"). How would I connect these two computers to do that? I have only touched networking before, and need full details on how to do what.

   Thankz,
     DaGeek247

---

### Post by DaGeek247 on 2010-10-29
bump.

---

### Post by tommy_t_xupa on 2010-10-29
I just got the new Ubuntu 10.10(Maverick Meerkat) in my laptop dell inspiron 1545 with a wireless make:[ BCM4312 ] and a chipset: [ 4e4:4315 ] and it work just fine for the exception of the internet that just dont work
I have tried almost everything but it just doest work
in the terminal they dont recognize iw and dont allow me to do it
and if you have the answer for my problem please reply 
:confused::confused::confused:

---

### Post by SeijiSensei on 2010-10-29
If both machines have an Ethernet port, you need either a small [switch]("http://www.newegg.com/Store/SubCategory.aspx?SubCategory=30&name=Switches"), or something called an "[Ethernet crossover]("http://www.newegg.com/Product/Product.aspx?Item=N82E16812270243")" cable.  That cable connects the transmit pins on one machine to the receive pins on the other, and vice versa.  If you buy a switch you just plug regular Ethernet cables from each machine into the device. 

Then you need to assign each machine a static IP address, say 192.168.1.1 and 192.168.1.2.  You should then be up and running.

---

### Post by DaGeek247 on 2010-10-29
Is there a way to do it without a switch or a crossover cable?

---

### Post by SeijiSensei on 2010-10-31
No.  You need a "crossover" connection of some kind.  There are also crossover serial cables; you don't happen to have one of those do you?  (I doubt it unless you bought one intentionally.)

If you just use a regular Ethernet cable, the transmit pins on each computer will be connected together as will the receive pins. The computers won't be "listening" for traffic from the other device.  (Same holds true for serial cables.)  Crossover cables wire the transmit pins on one end to the receive pins on the other.  So when one computer "talks" the other computer can "hear" it. 

If you discover you have a serial crossover cable, you could use PPP to connect the computers together.  That's a subject that's way beyond a forum discussion.  I'd start with the [PPP HOWTO]("http://tldp.org/HOWTO/PPP-HOWTO/") in that case.

For the money ($8+shipping at Newegg), I'd buy a five-port switch.  You can network five machines together and "daisy-chain" the device to another switch later on if your needs change.  

(I wondered if there were a USB-USB solution; there is, but again you need to buy a [special "bridged" cable]("http://www.hardwaresecrets.com/article/Connecting-Two-PCs-Using-a-USB-USB-Cable/248").  The linked article warns that using a regular USB cable can fry either or both machines ports or even their power supplies.)

For speed and flexibility, nothing beats Ethernet.

---

### Post by DaGeek247 on 2010-10-31
I have two 2x9 serial cables, would they work?

---

### Post by spiky001 on 2010-10-31
Here is a way to make your own cross over ethernet cable [http://www.duxcw.com/digest/Howto/network/cable/cable5.htm](http://www.duxcw.com/digest/Howto/network/cable/cable5.htm)  a normal serial cable will not work

---

### Post by SeijiSensei on 2010-10-31
> **DaGeek247 said:**
> I have two 2x9 serial cables, would they work?

Not unless it's labelled as a crossover cable.  Wiring your own crossover Ethernet cable only makes sense to me if you have absolutely no money and assign no monetary value to your time.  Or if you like to tinker with electrical stuff.

---

### Post by DaGeek247 on 2010-11-23
So, If I got the crossover cable, and plugged it inbetween the two computers, where would i go from there? full detailes for both machines, I still very little knowledge of newtworking between the two.

---

### Post by cariboo on 2010-11-23
There isn't enough psce here to give you a complete networking course, but essentially you have to give each system an ip address in the same netblock eg:

[LIST]
[*]xp system 192.168.0.1
[*]ubuntu system 192.168.0.2
[/LIST]

Then because Windows isn't compatible with other operating systems, you would have to set up samba on you Ubuntu system. If the Windows system has sharing setup properly, you shouldn't have to add anything to the Ubuntu system in order for it to access the Windows system. Here are some resources to help you

[How to set a static ip address in windows]("http://www.tech-faq.com/how-to-set-a-static-ip-address-in-windows.html")

To set a static ip address in Ubuntu using Network-Manager, double click on the network icon in the top panel, and select **Edit Connections**, next select eth0

[IMG]http://i.imgur.com/l62oo.png[/IMG]

and click **Edit**, next, click the IPv4 tab in the editing window

[IMG]http://i.imgur.com/XuOCD.png[/IMG]

Set the Method to Manual

[IMG]http://i.imgur.com/CPcdJ.png[/IMG]

The next thing to do is enter the ip address, the netmask and gateway:

[LIST=1]
[*]enter ip address - 192.168.0.2 - press enter
[*]enter netmask - 255.255.255.0 - press enter
[*]enter gateway 192.168.0.2 - press enter
[/LIST]

For DNS servers, just enter 192.168.0.2, then click Apply, you'll be asked for your password, and you should be done.

For a Samba howto have a look [here]("http://ubuntuforums.org/showthread.php?t=202605").

Good luck

---

### Post by DaGeek247 on 2010-12-30
perfect. i Just eeded to get a cheap working router. thanks for helping out.

---

