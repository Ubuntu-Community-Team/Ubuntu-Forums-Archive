---
title: "Network card problem"
date: 2010-04-13
forum: Networking &amp; Wireless
---

### Post by m_elbatniji on 2010-04-13
Dear Friends,
I have recently installed Ubuntu 9.10 on my desktop. I am facing a wiered problem with my NIC. The NIC works fine when connecting it to my DSL router. However; when connecting it to a standalone switch i.e. not connected to anything, ubuntu does not recognize the interface as up although the LEDs on both sides of the link show that the link is up. Because of that I cannot make use of the connection between ubuntu and the switch. Can anyone help me troubleshoot this problem? Thanks.

---

### Post by cheffabe on 2010-04-13
You can check you interfaces with "ifconfig". The first two lines of your first network card "eth0" it should look like this:

```

eth0      Link encap:Ethernet  HWaddr 00:0e:a6:97:ea:f0  
          inet addr:192.168.10.8  Bcast:192.168.10.255  Mask:255.255.255.0

```You should get a similar result with your IP address when your connected to your router. You usually get this address via dhcp from the router. If you are just connected to a switch, your card works but has no IP. So you can add a dhcp-server (router) to the switch or set the IP address manually. Hope that helps.

---

### Post by m_elbatniji on 2010-04-13
Dear cheffabe,
Thank you for your reply. I have configured a DHCP server on my standalone switch and now it is working. But I am wondering about two things:
 
- It seems that for ubuntu to bring the interface up, it has to aquire an IP address either statically or via DHCP. Why doesnt it at least show me that the physical link is up and it is trying to aquire an IP address? (Just like windows does)
- One of the things that I havent mentioned is that I have multiple NIC installed and whenever I physically connect one of the interfaces I have to click on the "wired network connection" icon on the right side of the top toolbar and choose the interface and click on connect. Then the interface is activated and it starts aquiring an IP address. How can I configure so that it does all that automatically once the cable is plugged in?
 
 
Once more  I appreciate you help :) I hope I can find answers to the above 2 questions.

---

### Post by dwarfolo on 2010-04-13
Try to check the "Connect automatically" option inside your NetworkManager Applet.

---

### Post by m_elbatniji on 2010-04-13
It is checked... on all of the interfaces. Does it have anything to do with user permissions. During the installation, I was asked to create a username and that is the user I login with. However; when performing some tasks, i have to use the sudo command followed by the command i want to use. the wiered thing is that i have to enter the password of the user that i am already logged in with, which i think is wiered. Could it be that?

---

### Post by doas777 on 2010-04-13
> **m_elbatniji said:**
> It is checked... on all of the interfaces. Does it have anything to do with user permissions. During the installation, I was asked to create a username and that is the user I login with. However; when performing some tasks, i have to use the sudo command followed by the command i want to use. the wiered thing is that i have to enter the password of the user that i am already logged in with, which i think is wiered. Could it be that?

this is standard on ubuntu. instead of running as root, you run as a normal user, but you have the ability to run admin commands via sudo and gksu. limited users cannot use sudo or gksu. basically it is the same as UAC in windows. you as an admin user have only normal user rights unless you specifically tell somthing to run as admin, then you either say "yes, I want to run as admin", or you put in a username/password to confirm that you want to run as admin. 

here is some more info:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

as for your network query, gnome-network-manager does not show a tray icon for each connection, but instead tries to cover all connections. as such it doesn't have an animation telling you that one connection is requesting an IP. in windows, each adapter can have their own icon, so the notifications are adapter-specific.

---

