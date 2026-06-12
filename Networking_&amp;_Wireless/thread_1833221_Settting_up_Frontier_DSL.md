---
title: "Settting up Frontier DSL"
date: 2011-08-25
forum: Networking &amp; Wireless
---

### Post by Silvertones on 2011-08-25
I've been struggling having to use dial up. Frontier now has DSL available in my area. They provide a setup disc for Windows however Support says I can use Linux. No details how. They provide a wireless router with the setup. Whenever I go to a WiFi spot my computer just connects by magic. Well this is how it's supposed to work.
The question here is has anyone setup DSL for use with Frontier? Is there a guide available.I suppose in reality it will be up to Frontier to provide the guide as I'm sure each provider will be different.
In theory it appears that all I need to do is rt click on the network icon in the top right and choose edit connections. Then click on wireless/add in input the neccessary data provided by Frontier.
Does this sort of sound right.

---

### Post by lmarmisa on 2011-08-25
Sorry. I can not give any specific information about your ISP or a reference to a guide. I will try to give you only a very basic general information.

The DSL routers are normally pre-configured by the ISP and they should work when you install them.

So, plug the phone cable and the AC power adapter. You have to add some filters provided by your ISP to your phones too. That is all in relation with the installation.

Routers offer normally two types of connection:

1) Wired connections. 

You need an [Ethernet cable]("http://en.wikipedia.org/wiki/Category_5_cable"). This cable is normally included in the DSL kit provided by your ISP. Connect the cable from the router to your computer. You should be able to access to the internet then.

2) Wireless connections.

This is the kind of connection used normally by laptops. You need to know two parameters in order to complete your connection:

[INDENT]- [SSID]("http://compnetworking.about.com/cs/wireless/g/bldef_ssid.htm") (Service Set IDentifier): This is the name of your wireless network.

- [Passphrase]("http://compnetworking.about.com/od/wirelesssecurity/g/passphrase.htm"): the passphrase is like a secret password and it guarantees that only authorized computers are connected to your wireless network. 
[/INDENT]
You have to know both parameters if you want to connect to your wifi. Try to find this information in the documents provided to you for your ISP. Look at the bottom of your router and check if there is a label showing these two parameters.

If you know SSID and passphrase, the connection to wifi is very easy. Simply click on the network icon of the upper panel and select your SSID. The system will ask you for your passphrase. If the system proposes to you an additional password for storing your wifi information (keyring), I recommend to leave blank this password.

---

### Post by Silvertones on 2011-08-26
Thanks so much. This is exactly what I needed. The ISP confirmed the same thing. When I sign up I'll will set a user name and pass word. Once I plug into the modem it'll connect and ask for these and that's it. The wired router is also as they said. I forgot to ask about wireless as this is what I'd like to use . You answered that question. The router is setup already with the needed info.
One other question. Can the passphrase be changed? Do you know how? I'm sure with Windows it has some sort of program that comes with it. How about for us Ubuntu users?
Thanks

---

### Post by lmarmisa on 2011-08-26
> **Silvertones said:**
> Thanks so much. This is exactly what I needed. The ISP confirmed the same thing. When I sign up I'll will set a user name and pass word. Once I plug into the modem it'll connect and ask for these and that's it. The wired router is also as they said. I forgot to ask about wireless as this is what I'd like to use . You answered that question. The router is setup already with the needed info.
One other question. Can the passphrase be changed? Do you know how? I'm sure with Windows it has some sort of program that comes with it. How about for us Ubuntu users?
Thanks

I would like to know if you have been able to connect to the internet at the moment.

Yes, not only the passphrase can be changed but also the SSID.

Try to follow this procedure. 

I recommend to use the wired connection for accessing to the router setup menu.

Open a terminal (Applications -> Accessories -> Terminal) and type the command **ifconfig**. You will see a result similar to this:

```

luis@UB1010ENG:~$ **ifconfig**
eth0      Link encap:Ethernet  HWaddr 08:00:27:dc:54:f1  
          inet addr:[COLOR="Blue"]192.168.1.106[/COLOR]  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:27ff:fedc:54f1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:559 errors:0 dropped:0 overruns:0 frame:0
          TX packets:247 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:214692 (214.6 KB)  TX bytes:30255 (30.2 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:38 errors:0 dropped:0 overruns:0 frame:0
          TX packets:38 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4056 (4.0 KB)  TX bytes:4056 (4.0 KB)

luis@UB1010ENG:~$ 


```

I have marked in blue the local IP address of my network interface: [COLOR="Blue"]192.168.1.106[/COLOR]. This data will be similar in your case.

This information is important for accessing to the configuration menus of your router. The general format of this parameter will be [COLOR="Blue"]192.168.X.Y[/COLOR]. In my case the IP address is [COLOR="Blue"]192.168.1.106[/COLOR]. The local IP address of the router will be calculated substituting the last number (in my case [COLOR="Blue"]106[/COLOR]) by [COLOR="blue"]1[/COLOR]. Therefore, the IP address of my router would be [COLOR="blue"]192.168.1.1[/COLOR] (this is the most usual value but it may be different like [COLOR="Blue"]192.168.0.1[/COLOR], [COLOR="blue"]192.168.2.1[/COLOR] and so on).

The next step is to open firefox and the go to [COLOR="blue"]http://192.168.1.1[/COLOR] (use the local IP address of your router).

The router will ask for an user and a password. Try admin / admin (I hope this information would be good; otherwise ask to your ISP).

If the access to the router is successful, go to the wireless menu and change the phassphrase (or SSID) if you wish.

I hope this information will be useful to you.

Best regards,

Luis

---

### Post by Silvertones on 2011-08-26
That sounds easy enough.
I have dial up at the moment on one computer. I have 3 laptops that are networked via a wireless adhoc network. I want to do away with this and use a router. DSL will be available in my area soon so want to get the router set up first. So I assume that as the wireless cards are already setup I can set the security of the router to match the cards.
My other thoughts to simplify this is my other 2 computers are windows by necessity. I could just use one of them to set up the router couldn't I then the Linux box will just connect I'm sure..

---

### Post by lmarmisa on 2011-08-26
In my case, I like to install in Windows the minimum number of programs. 

So, if you are able to access to your router setup using your browser (firefox or IE), you do not need to install any program.

If you get some problems with my procedure, then install that program. This is my humble recomendation. :)

Best regards,

Luis

---

### Post by walt.smith1960 on 2011-08-26
It depends on the ISP as lmarmisa said.  When I had Verizon DSL, Verizon used a PPPoE login.  I was using a Linksys router and had to go to a status page.  There I found PPPoE login information.  I had to enter the user name & password on that page in order for the router to connect.  This is a router function though, not an operating system function so the ISP should be helpful with this.  

You should also change the default router name & password as a security precaution.  If you lose the user name or password, a hard reset -usually pressing a recessed button for several seconds- will restore factory defaults.  If your router firmware permits it, you could store a configuration file once you get it like you want it.  That way, if you have to do a hard reset you can restore the configuration file rather than have to reenter everything.

---

### Post by Silvertones on 2011-08-26
Yep I get it. I'm really talking two subjects at once:
1. Just setting up a router
2. hooking up to the internet via Frontier's modem.
For #1 it seems simple, ifconfig to acquire the IP address of the router--hooked up wired at first. Then type in that IP address into Firefox and configure the router. Once I do that I should be able to go wireless.
For#2 it'll take me to a login page at Frontier--type in the user name & password I setup when purchasing.

Okay guys one more piece of the puzzle. As  I mentioned at this point I have my 3 laptops networked wireless via an ADHOC net work. ADHOC networks work best when set up to use static IP addresses. I won't need the ADHOC once I get this going so I should revert back and let the router assign the IP addresses?

---

### Post by lmarmisa on 2011-08-26
I recommend to define an automatic configuration with DHCP on your computers when you switch to the router solution.

If you use a manual setup, your communications could not work.

---

### Post by Silvertones on 2011-08-28
So after all the phone calls to Frontier it finally comes down to this," We can't support you if you run Linux. We can not advise you on whether out equipment will work with Linux." etc, etc.
So looks like no DSL for me.

---

### Post by walt.smith1960 on 2011-08-29
> **Silvertones said:**
> So after all the phone calls to Frontier it finally comes down to this," We can't support you if you run Linux. We can not advise you on whether out equipment will work with Linux." etc, etc.
So looks like no DSL for me.

That's a standard disclaimer.  Do you have a Windows install you can use to get set up?  ISP support may only know "Click on Internet Explorer blah, blah, blah" Once you are confident in the the DSL connection, setting up a network with a router in Linux is plain vanilla. The biggest challenge may be getting your wireless network adapter working with Linux.  Many work OOB or with minimal tweaks, a few can be a gold plated PITA.   I wouldn't let "We don't support Linux" discourage you, network protocols are O.S. agnostic.  Besides, does the ISP offer a trial period, 30 days or so?

---

### Post by Silvertones on 2011-08-29
> **walt.smith1960 said:**
> That's a standard disclaimer.  Do you have a Windows install you can use to get set up?  ISP support may only know "Click on Internet Explorer blah, blah, blah" Once you are confident in the the DSL connection, setting up a network with a router in Linux is plain vanilla. The biggest challenge may be getting your wireless network adapter working with Linux.  Many work OOB or with minimal tweaks, a few can be a gold plated PITA.   I wouldn't let "We don't support Linux" discourage you, network protocols are O.S. agnostic.  Besides, does the ISP offer a trial period, 30 days or so?

Yes I finally figured out "don't support" means we can't help you but they do say it'll work. I do have Windows on a partition here so I can do that but first I think, just to be a Linux geek, will try as mentioned above. Plug a cable into the modem and configure everything with Firefox. If I fail I'll go to Windows and do it that way.
I got this from them BTW:

Dear John,  Thank you for contacting the Frontier eCenter.  I have received your  email dated 8/25/11 regarding your DSL requirements.  My name is Angela, and I will be happy to assist you.  I apologize for your inconvenience. After speaking to a Frontier's  Technical Support Department Specialist, I found out that this is Great  News concerning your Linux system!  Yes, it will work and is compatible  with Frontier's High Speed Internet service and no data has no cap on  the amount of the data service.    I hope I have resolved the reason for you emailing us today, if not,  please do not hesitate to contact Frontier's Technical Support  Department at 1-877-462-1105 where a specialist will be more than happy  to further assist you.  Thank you for using the New Frontier. We appreciate your business.  Sincerely,  Angela Service Request Representative - eCenter Frontier Communications 5003 S. Miami Blvd.  Durham, NC 27703 (877) 462-6143 [EMAIL="customersupport.pn@ncnetwork.net"]customersupport.pn@ncnetwork.net[/EMAIL]

---

### Post by walt.smith1960 on 2011-08-29
Good news.  I understand why tech support people don't want to support Linux, they don't want to deal with " are you using KDE, Gnome 2, Gnome Classic, Unity, Gnome Shell, Xubuntu ...... so I know what you're looking at on your screen?"  Web browser administration pages like routers commonly use is a way to get around that.

---

