---
title: "Connect ubuntu to internet through Windows XP machine"
date: 2009-07-18
forum: Networking &amp; Wireless
---

### Post by freakyfrog on 2009-07-18
This is the setup I have:
* A Windows XP PC with two ethernet ports - one on-board and one NIC.
* A Lenovo 3000 laptop running Ubuntu 9.04
* The XP PC is connected to the internet by a ADSL modem.

Requirement: I want to connect the ubuntu laptop to the PC via any of the two ethernet ports of the PC and access the internet from the laptop.

I understand that the ideal solution is to have a router to share the Internet connection. I've also gone through some threads in the forums to see whether it'd help me out with this requirement. Can anyone give me a solution?

---

### Post by Riaku on 2009-07-18
Have you set up internet sharing in xp?

---

### Post by freakyfrog on 2009-07-18
Yes, I tried setting it up by checking "Allow other users to connect through this computer's internet connection" in **Connection Properties -> Advanced -> Internet Connection Sharing**

Most of the documentation I read involved connecting two machines to each other via an Ethernet cable. Here, I'm trying to connect an XP PC and an ubuntu laptop to each other and make ubuntu access the Internet through the PC's connection.

---

### Post by Riaku on 2009-07-18
try shutting down the laptop and desktop. boot the desktop up first let it connect, then unplug and replug the eth0 cord from the laptop, boot the laptop up and try it, xp is very finicky with it's sharing

---

### Post by freakyfrog on 2009-07-18
I haven't got the machines to ping each other yet. Essentially I have two NICs on my PC. One connects to the modem and the other should connect the PC and the laptop. How do I configure the other NIC to act as a connection between the PC and the laptop? What are the configurations I need to do at both ends?

---

### Post by Riaku on 2009-07-18
When you went through the network setup wizard you where given choice of your internet connection. Make sure you choose the correct one

---

### Post by SharezLinux on 2010-03-19
There is a simple trick!

use a proxy server (Like Pulsar Proxy Server) on your XP machine! :D

Now, You can easily connect to internet through XP!:p

---

