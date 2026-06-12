---
title: "Problems With Networking configuration"
date: 2009-12-23
forum: Networking &amp; Wireless
---

### Post by existente on 2009-12-23
Hi! Iam using ubuntu 9.10 and i am trying to configure the network in order to make possible a modem conection but when i open the Networking window,  all the options appear disabled except the Close button an the help button. I can`t unblok anything. What can i do???:confused::confused::confused:

---

### Post by labinnsw on 2009-12-24
Could you take a screenshot of the window, upload it, and post the link?
What type of modem are you attempting to connect to.(USB, DSL, ADSL etc.? Include brand and model if possible.)
Are you trying to establish a wired or wireless connection?

---

### Post by existente on 2009-12-24
Thanks for your aswer. The picture is attached. 
I have the same problem in two computers while trying to make a conection by telefone.
The models of the modems of theese machines are the following:

Motorola SM56 Data Fax Modem
Smart Link 56K Modem

---

### Post by Iowan on 2009-12-24
Does that machine have other networking devices (ethernet, wireless)? **lshw -C network** will show devices. 
I remember a previous version had dropped out-of-the-box dial-up (Jaunty?).
(I also remember there were How-To's to set it up)

---

### Post by labinnsw on 2009-12-24
[Here is your link]("https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer")

Look for gnome-ppp

That might be a bit heavy.

Install gnome-ppp from Synaptic
Then to configure it, go to Applications >> Internet >> gnome-ppp.
(The application should start up, but if it doesn't, open a terminal and type "sudo gnome-ppp")

Enter your username, password, and the phone number and click connect.

or

click set up
configure the application and close the set up window
click connect.

---

### Post by existente on 2009-12-24
Iowan: Yes, both machines have ethernet and one of them has wireless. How can I find the how to that you mention?

---

### Post by existente on 2009-12-24
labinnsw: Thanks, I'll try it.

---

### Post by aprigiosimoes on 2009-12-24
#/etc/init.d/network-manager stop
#update-rc.d -f network-manager remove 
#vi /etc/network/interfaces
  
   auto eth0
   iface eth0 inet dhcp

#/etc/init.d/networking restart
#ifconfig -a

---

