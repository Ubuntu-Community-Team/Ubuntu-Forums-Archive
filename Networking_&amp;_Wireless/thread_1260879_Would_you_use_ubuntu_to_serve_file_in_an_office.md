---
title: "Would you use ubuntu to serve file in an office?"
date: 2009-09-08
forum: Networking &amp; Wireless
---

### Post by david90 on 2009-09-08
I have an office with 15 workstations and I would like to know using ubuntu as a file server a good idea? 

Does ubuntu file sharing feature have # of users limitation like XP does?

---

### Post by 3rdalbum on 2009-09-08
> **david90 said:**
> I have an office with 15 workstations and I would like to know using ubuntu as a file server a good idea? 

Does ubuntu file sharing feature have # of users limitation like XP does?

1. Yes
2. No, why would it? Microsoft don't want people to use XP as a file server, because they want to sell you a Server edition of Windows that will cost more. Ubuntu is free and Free, so there's no limitation. The Samba package available on Ubuntu desktop is exactly the same as the one on Ubuntu server.

---

### Post by jamest09 on 2009-09-08
Yes, I do this now.

No, there isn't a limit :)

---

### Post by i.r.id10t on 2009-09-08
Been using both Debian and Ubuntu server for a fileserver for a loooong time...

No limits, other than what your hardware can handle.

---

### Post by david90 on 2009-09-12
cool.

For serving files to 10 workstations, what's the recommended system specs?

---

### Post by zman58 on 2009-09-12
Yes, I would use Ubuntu without a doubt for office. It is incredibly responsive and reliable, and secure. Also you can install and set it up in a blink. Also you can update it very quickly. On top of that it is free to use without limitation. I have a complete server setup documented and maintained. It is the setup I am currently using for my home network. Feel free to use what you want from it. I would be happy to answer questions you have, just email me.

Gatekeeper provides the following:

   1. Powerful multiuser server system which is incredibly flexible and reliable.
   2.Gateway to the internet for all workstations on the subnet.
   3.Highly secure and fully configurable firewall via iptables configuration script.
   4.DHCP (dhcpd) server providing automated IP configuration for all workstations.
   5.DNS caching server (named) providing a local private zone and cached name resolution for the various LAN workstations.
   6.Print server (via both CUPS and samba) providing centralized print services for all Windows and Linux workstations. Provides Windows style and CUPS printing services.
   7.Personal and public file shares (provided via samba) for workstations operating on the subnet. Many gigabytes of hard drive storage.
   8.Automated nightly backups of all important media and system files to an external USB drive.
   9.Caching transparent proxy server provides accelerated web services to local subnet.
  10.Remote configuration via X server and ssh.

If you would like to see a logical diagram of the network using gatekeeper please click the link below.

I have network diagrams, readme.txt, etc on my website...
You can read about it and get all necessary information and configuration files here...

[http://home.roadrunner.com/~zahorec/gatekeeper.html](http://home.roadrunner.com/~zahorec/gatekeeper.html)

How about that for service?

---

### Post by david90 on 2009-09-13
> **zman58 said:**
> Yes, I would use Ubuntu without a doubt for office. It is incredibly responsive and reliable, and secure. Also you can install and set it up in a blink. Also you can update it very quickly. On top of that it is free to use without limitation. I have a complete server setup documented and maintained. It is the setup I am currently using for my home network. Feel free to use what you want from it. I would be happy to answer questions you have, just email me.

Gatekeeper provides the following:

   1. Powerful multiuser server system which is incredibly flexible and reliable.
   2.Gateway to the internet for all workstations on the subnet.
   3.Highly secure and fully configurable firewall via iptables configuration script.
   4.DHCP (dhcpd) server providing automated IP configuration for all workstations.
   5.DNS caching server (named) providing a local private zone and cached name resolution for the various LAN workstations.
   6.Print server (via both CUPS and samba) providing centralized print services for all Windows and Linux workstations. Provides Windows style and CUPS printing services.
   7.Personal and public file shares (provided via samba) for workstations operating on the subnet. Many gigabytes of hard drive storage.
   8.Automated nightly backups of all important media and system files to an external USB drive.
   9.Caching transparent proxy server provides accelerated web services to local subnet.
  10.Remote configuration via X server and ssh.

If you would like to see a logical diagram of the network using gatekeeper please click the link below.

I have network diagrams, readme.txt, etc on my website...
You can read about it and get all necessary information and configuration files here...

[http://home.roadrunner.com/~zahorec/gatekeeper.html]("http://home.roadrunner.com/%7Ezahorec/gatekeeper.html")

How about that for service?

Thanks for your detailed documents.  I will definitely read it.

I'm kinda apprehensive about using the a file serving PC as a gateway also because if the PC fails the whole office loses internet.  I think keeping different components of a network separate makes the network less prone to a complete failure.

What do you think?

---

### Post by zman58 on 2009-09-13
> **david90 said:**
> Thanks for your detailed documents.  I will definitely read it.

I'm kinda apprehensive about using the a file serving PC as a gateway also because if the PC fails the whole office loses internet.  I think keeping different components of a network separate makes the network less prone to a complete failure.

What do you think?

Separating components is a good option, however, it does cost more. If you have separate components and the gateway server fails, then you can still have your fileshares up and running on the other system--that is if you still have the required network services. On the downside, you have two or more systems to purchase and maintain $$. You should have a some kind of disaster plan in place that would provide at a minimum the most critical services. You need to decide to what extent your business needs to cover each provided service.

If my gatekeeper system should fail I can easily plug in my wireless/wired WAN router (D-Link DIR-615) and have a network up with fundamental routes in place within a minute or so. So in the normal case gatekeeper provides all and should it fail I can drop my Router in place temporarily. In this case I would not have local DNS and file/print services, but at least everyone would have basic network and a default route to the WAN so could use Internet. This is a 10 second switch over requiring switching two Ethernet cables. The only time I have ever needed to do this is when I am upgrading server hardware and need to bring gatekeeper down for a few hours.

Gatekeeper runs backups nightly on all user and system configuration files to a separate backup drive, so I am covered for backup data to the extent I need to be for our home.

The advantages of one main system that I use provides me with a central point of control and one single system to manage. The logging and flexibility this provides is far beyond what a typical appliance provides. It is extremely cost effective and reliable with Linux.

I would not suggest this approach with Windows because Windows systems degrade over time to the point that they just fail--then there is the security problems also with Windows. Then the continual patch and rebooting, lockups, failures, etc.

It is hard to describe just how reliable this Linux system is. The system has never failed. I have it on a UPS and it literally runs 24-7 non-stop. It is more reliable than the cable modem that it is connected to, more reliable than the wireless router node attached to it, more reliable than the ISP network to which it is connected. It just never fails and it is running on common PC hardware--nothing particularly expensive or special. It serves up music, video, data, files all day long. I just performed software updates on it last night with 150 new package updates which took about 10 minutes and required one single restart--only because the Linux kernel was updated. It was unavailable to the network only during the reboot time which is less than a minute. Athlon 3500 with 2G RAM and a 500 GB hard drive. Just imagine what a business class server could do with the same software stack!

I don't believe there is a problem running one single system, as long as you have a standby device which can provide rudimentary network services in case the one system system should fail. If you are providing remote (Internet) services, such as http website, to the big bad Internet then it is a different story and you would need a DZONE with separate http server and separate routing.

I suggest that you get a very good quality switch. All switches are not created equal. I picked up a 24 port 10/100 buffered switch by D-Link when they recently went on sale because the Gbit switches are out now. It made a huge difference over the little 16 port 10/100 consumer based LinkSys product I had previously. The network runs as smooth with the D-Link business class switch.

At this point in time, and for business purposes, I would recommend a decent 10/100/1000 (Gbit) business class switch. Make sure you get the Gbit port on the LAN side of the server PC also. The Gbit backbone this provides will make a difference if you are serving lots of data to the LAN workstations. If your business workstations are Windows, then it will also make a big difference because of the silly desktop situation with Windows where a sluggish network creates sluggish desktop experience for everyone with mapped drives--this not the case with the Linux desktop.

---

