---
title: "Trouble with static ip"
date: 2011-02-28
forum: Networking &amp; Wireless
---

### Post by tailwhipm on 2011-02-28
[SIZE=2]Hello, I am new to the ubuntu forums and somewhat of a noob to unix. To start off, I've been trying to setup up a static ip address on my server. (Im running Ubuntu 10.10 btw) So I've followed countless forums and their tutorials on how to setup a static ip with no luck. Heres the thing im confused about, when i type in ```
ifconfig -a
``` the ip for eth0 shows up with my local ip. example: 192.168.1.102. I dont understand how to find the public address for my server as that is important to put the information in for static address and so people can access the server, right? Can someone please help me!!:confused:[/SIZE]

---

### Post by Hakunka-Matata on 2011-02-28
Static IP (never changes) from your ISP?  Is that what you're asking?  So anybody in the cloud can get straight to your server?

---

### Post by Hakunka-Matata on 2011-02-28
> I dont understand how to find the public address for my server as that is important to put the information in for static address and so people can access the server, right?

You don't set that address, you have to talk with your ISP about that, and they give you a static address, if you're willing to pay for it.  It's not cheap.  If that's what you are talking about.

Normally if we have Internet access, our public ip address is done via dhcp.  If you don't reboot your router/modem, often the dhcp'ed public IP address will remain the same for days on end.  But it can change at any time.  If you're running a LAN router between your Internet Modem/Router and your LAN computers, then it's a web administered device which you can access to change settings for your local area network, right?.  From the example you gave, 192.168.1.102, it's probable your LAN router (if you have one), is administered via 192.168.1.1, with a password of Admin, or Administrator, or some other very common password.  The password and default IP addresses are stamped on a label on all modern routers, like Linksys, or Netgear.  Look at that address with a browser and you'll find your current public IP address, given out by your local ISP's dhcp server.  Normally you cannot access the ISP router to administer it, they have it locked down.

---

### Post by tailwhipm on 2011-02-28
Thank you for the quick reply i appreciate it!! and i see what your saying the Public Ip is the address for my entire network not for each computer on my LAN. So how would i go about running my server using my Ip adress to reach the public?

---

### Post by Hakunka-Matata on 2011-02-28
You want people anywhere on the net to be able to access your server?

---

### Post by Hakunka-Matata on 2011-02-28
It's late right now and I'm signing off in a minute or two, but if that's what you mean you have to find your internet IP address.

try this URL [http://whatismyipaddress.com/ip-lookup]("http://whatismyipaddress.com/ip-lookup")

---

### Post by tailwhipm on 2011-02-28
Yes. I know what my internet Ip, is the question is I have 2 different computers on my lan and the server. How do i set it up where that ip reaches only the server. for instance im starting a minecraft server, when someone enters my Internet Ip i want them to access my server to the game.

---

### Post by mimor on 2011-03-01
You probably have this setup:
Internet (ISP modem)  --> Router --> server
                                 --> computer1
                                 --> computer2

If so:
You'll have to access the web-interface of your router and search for port-forwarding.
There you can say eg for minecraft: 
[Minecraftwiki]("http://www.minecraftwiki.net/wiki/Tutorials/Setting_up_a_server#Setting_up_Port_Mapping")
To find out how to set portforwarding on your router:
[Portforward.com]("http://portforward.com/")

---

### Post by mimor on 2011-03-01
Oh, and if you get a dynamic IP adress from your ISP, you might want to set up a [dyndns account]("http://www.dyndns.com/") + some way to update it.

---

### Post by tailwhipm on 2011-03-01
Thanks for all your help i got it!! much appreciated!:)

---

### Post by Hakunka-Matata on 2011-03-01
Please mark your Thread [Solved] when finished.

---

