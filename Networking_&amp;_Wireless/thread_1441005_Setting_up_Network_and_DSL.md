---
title: "Setting up Network and DSL"
date: 2010-03-28
forum: Networking &amp; Wireless
---

### Post by Pyorrhea on 2010-03-28
Hi everyone,

So this problem of mine is a general problem for 1st timers to ubuntu. 

I have searched the forums to assist me with this topic, but to no avail, nothing I found seems to help me.

My problem :

I cannot be connected to my network and DSL connection at the same time.

When connecting my computer on a normal windows network, 1st I set the NIC to my network address, netmask and gateway. This secures the connection on my "Home" network. I then set my router to a Bridged connection. Then I would create a dail-up DSL connection where I insert my Username and Pass that I received from my ISP.

End result is that I connect.

For Ubuntu I am not having any joy. 1stly when I open Network Connections, I see that there is a Auto Wired Connection. I tick the dail. It connects with no problem. I setup a DSL connection, with specified address, netmask and gateway. 

When I click on it to connect, I loose connection to the network. 

Which to me is wrong, as I would like to be connected and on the net at the same time.

I have tried the PPPoEConf command in terminal to setup the DSL  connection and I setup my NIC address, netmask and gateway. I used the sudo vi /etc/*/interfaces/ to set this via terminal.

I am not able to connect to the internet at all. And I loose connection to my network when I click on the DSL connection. 

Untunu 9.10

Please help.

Thanks :)

---

### Post by chili555 on 2010-03-28
> I then set my router to a Bridged connection.Maybe I am missing something here; if I am, please help me understand. If you set the router to provide the user name and password to the DSL modem and connect your computer *without* PPPoE, aren't all the computers that are also connected to the router available, as well as the internet? Or, are you trying to have two connections; one to the internet and a second one to a LAN on a separate network/router?

If the latter is the case, it can be done with manual configuration, but I don't believe Network Manager will do so.

Please help me understand your setup better.

In my system, where the router provides the DSL user/password, everybody is connected to the router, everybody (assuming they are not on some DENY list) sees everybody and everybody sees the internet.

---

### Post by Pyorrhea on 2010-03-28
My router is acting like a hub between 2 computers. The router is not setup to always be connected to the internet, it is a bridged setup so me and my m8 can connect to the internet with our individual Internet accounts.

In windows I just create a normal dial-up connection with my DSL username and password, as I am already connected to my router.

Router IP range 10.0.0.0 - 10.0.0.255 Router ip is set to 10.0.0.2

My computer 10.0.0.110


In short. I want to be connected to my network 24/7 without having to connect to it manually. And if I want to connect to the internet I would use the Connect to DSL Connection(Similar to Windows Dail-up connection)

Thanks for the reply.

---

### Post by Pyorrhea on 2010-03-28
So I have played around some more and still nothing. What I have noticed now is, that when I want to setup a static IP for my NIC, that I cannot do so. 

When going to Administration and then going to Networking, then I do not see an option for Networking. 

And it is at networking where I want to assign the Static IP for my NIC. 

Can anyone tell me how to find this in Ubuntu 9.10.

I have tried again to set the Static IP for my NIC with 

sudo vi /etc/networking/interfaces

This however only creates a Wired Connection which I have to click on to connect. 

Please Halp!

---

