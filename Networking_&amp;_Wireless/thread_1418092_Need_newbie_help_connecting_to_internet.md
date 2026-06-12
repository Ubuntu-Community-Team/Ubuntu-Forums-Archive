---
title: "Need newbie help connecting to internet"
date: 2010-02-28
forum: Networking &amp; Wireless
---

### Post by Ballentine10 on 2010-02-28
I just installed Ubuntu 9.10 on my Acer laptop. The installation went smoothly. So now I would like to connect to the internet with it (I have reverted to my other laptop running Windows to get help). 

I tried reading the instructions I have found online and in the OS help section, but they have not helped. 

Here's some background: I have a Broadcom BCM4401-BO 100 base TX ethernet port in the laptop, connected to a DSL cable modem. 

I am using Ubuntu 9.10. I finally found the networking icon in the upper right of the screen (it is transparent).

Can someone please tell me in plain, clear language how to connect to the internet?

Thank you!

---

### Post by chili555 on 2010-02-28
Let's take a systematic approach. First, open Applications -> Accessories -> Terminal and do:```
ifconfig
```Do yoy see an ethernet interface, *eth0* perhaps? If so, then the card and it's appropriate driver have found each other and attached. Does it have an IP address, like this:> eth0      Link encap:Ethernet  HWaddr 99:16:6f:9a:5f:99  
          [COLOR="Red"]inet addr:192.168.1.105[/COLOR]  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:6fff:fe9a:5fdf/64 Scope:LinkIf so, you *are* attached to the internet. Can you open Firefox and navigate to Google?

Does your DSL provider require a user name and password? Is it possible, as it is in my system, to set it (and forget it) in the administration pages of the modem?

If you do not see an ethernet interface, we'll need to find and load the needed driver. If so, please run and then post:```
lspci -nn | grep -i Ethernet
```

---

### Post by Ballentine10 on 2010-03-01
Thank you, Chili555 for your prompt, detailed reply.

I think I am getting warm. 

Here is what I got:
> 
ubuntu@ubuntu:~$ ifconfig

eth0      Link encap:Ethernet  HWaddr 00:16:d4:b1:b7:28  

          inet6 addr: fe80::216:d4ff:feb1:b728/64 Scope:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 B)  TX bytes:2222 (2.2 KB)

          Interrupt:21  

It looks like there is a connection. So the next question is how do I log in?

I have to give a sign on name and password. I tried doing this with Ubuntu, but I don't think it logged on with the ISP.

Can you give me specific instructions on how to do this, please?

Thank you!

---

### Post by chili555 on 2010-03-01
You have an interface, meaning your network card has found a working driver and they have attached. You do not have a connection, meaning that your internet service provider (ISP) has not given you an IP address and therefor access to the network. They are expecting a user name and password, as you know.

I don't know much about this issue, although I actually use it! My DSL modem allows me to set the user name and password in its administration pages. I have also used a router which allows the same. Thereafter, I connect to the DSL modem with no user name and password requirement.

If these methods are not suitable in your case, you might refer to this thread: [http://ubuntuforums.org/showthread.php?t=1308020&highlight=dsl](http://ubuntuforums.org/showthread.php?t=1308020&highlight=dsl)

You might also search this forum for 'pppoeconf.'

You could try the Network Manager method. Right-click the icon at the top right and Edit connections. You will see a tab for DSL. Add a connection and fill in your details. I understand that Network Manager and DSL are a bit buggy right now, but I'd certainly try it first.

---

### Post by velle frak on 2010-03-01
Does your DSL modem has 2 zones, with DHCP running in the private?

If so, run [FONT=Courier New]dhclient[/FONT] in a terminal, and check with [FONT=Courier New]ifconfig[/FONT] if you received an ip-adres.

---

### Post by Ballentine10 on 2010-03-01
I'm not an expert on DSL. My previous abode had a real broadband connection, with a fiber optic (Cat 5?) cable coming out of the wall and going into my laptop. Turn it on, the connection was there (when it was working). 

Here I have a box connected to a telephone jack in the wall by copper wire, with the fiber optic cable coming out of the box and going into the laptop. 

So, I have to turn on the modem when I turn on the computer and log on to the ISP, using my ID sign on, and a password. They shake hands and I'm in business. 

As to IP address, as far as I can tell, I have a floating address, which changes every time I sign on. 

I'm looking at the broadband connection details, with my Windows connection, and it says: 

WAN miniport, (PPPOE)

Device type: PPPOE

Server type: PPP

And I have a Server IP4v address and a Client IP4v address.

It uses TCP/IPv4 and v6

Frankly, all this should be invisible to the user. And it is with Windows, once I set it up. Windows internet connections aren't the easiest for an amateur to set up, either. But it's gotten a bit easier. 

If Linux can make an internet install format that is simpler than Windows, that would be a good lesson for Microsoft. 

What I saw was confusing. If I had already been using Linux/Ubuntu, the terminology might have made some sense. But given that the first thing I'm doing after installing the OS is trying to do an internet setup, the instructions did not mean anything to me. 

On the other hand, perhaps something wasn't working. But I do know my modem and internet connection works, the laptops work, they seem to be getting a connection to the ISP, but the OS is not logging on.

What I think I'm looking for is something to click that sends my ID and password to the ISP. 

FYI, I am in a foreign country teaching. When I got internet installed here, it took four people about four hours to figure out how to connect my laptop. And then only after I finally suggested they turn off the firewall/antivirus program. That was with Windows (in Englishy). Imagine what it would have been like with Ubuntu.  

Hey, thanks for the help. Keep the suggestions coming.

---

