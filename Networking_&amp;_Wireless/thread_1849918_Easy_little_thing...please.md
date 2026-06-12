---
title: "Easy little thing...please?"
date: 2011-09-25
forum: Networking &amp; Wireless
---

### Post by MG&amp;TL on 2011-09-25
Could somebody do me a huge favour?

I'm learning php and LAMP, however I don't have a non-networked computer to test this on. Could somebody visit ***[http://192.168.1.70/whatbrowser.php](http://192.168.1.70/whatbrowser.php)*** to see if it works? It works on my home network, but I just want to test.

I know it's a risk to reveal one's IP, but since it's a test computer, isolated, with a firewall, I don't really care. Although I'd rather you didn't hack it. And there's no viruses on there, promise.

Or if I'm completely missing the point here, can someone explain why? Complete web newb, only ever done what I would call 'real' programming, e.g. programs that take up hard disk on the end-user's machine.

---

### Post by Doug S on 2011-09-25
Sorry, but we can not test that address as it is a reserved IP range for local use only.
You would have to set up port forwarding on your router and then give us your external or WAN IP address to try.
There are a few reserved IP ranges for internal use. 192.168.XXX.XXX is one of them as is 10.XXX.XXX.XXX
 
see also: [http://en.wikipedia.org/wiki/Private_network](http://en.wikipedia.org/wiki/Private_network)

---

### Post by MG&amp;TL on 2011-09-25
:???: Can you point me to a tutorial?

---

### Post by Doug S on 2011-09-25
Tell us more about your network and myself or another forum reader will try to help.
I assume you have a router between your adsl modem or cable modem and the rest of your network. Tell us the brand name and model number of your router. Also, can you access your router setup as the administrator? If someone else administers your router, then you will need to get help from them.

---

### Post by MG&amp;TL on 2011-09-25
I have:

-One bashed-up computer(the LAMP server in question, Linux.) with a USB wireless adapter.
-One laptop(Linux) with a wireless adapter built-in.
-BT Home Hub (broadband, connected to a telephone socket), connected to a Windows 7 pc (my parents') via (telephone?) cable. Big yellow chunky stuff, with a clicker and contacts down one edge.

Do you need anything else?

Very generous of you, btw. :)

---

### Post by MG&amp;TL on 2011-09-25
*ifconfig* from the server pc:

```
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0d:56:5f:31:c0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:356 errors:0 dropped:0 overruns:0 frame:0
          TX packets:356 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:54100 (54.1 KB)  TX bytes:54100 (54.1 KB)

wlan0     Link encap:Ethernet  HWaddr 94:0c:6d:e3:98:0a  
          inet addr:192.168.1.70  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::960c:6dff:fee3:980a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:162957 errors:0 dropped:0 overruns:0 frame:0
          TX packets:91409 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:111223122 (111.2 MB)  TX bytes:10745883 (10.7 MB)

```

---

### Post by Doug S on 2011-09-25
I suspect that your internet connection is via ADSL and that your modem and router are combined into the one unit you referred to as "BT Home Hub (broadband, connected to a telephone socket)".
You need to find the manual for that unit and figure out how to access it as administrator so that you can make changes. You would then want to find the port forwarding area and setup requests on port 80 to be forwarded to your server.
If you provide the exact brand name and model number for your modem router, I will see if I can find an on-line manual to maybe help further.
 
for example, maybe one of the user guides here: [http://bt.custhelp.com/app/answers/detail/a_id/10477/~/user-guides-for-broadband-hardware](http://bt.custhelp.com/app/answers/detail/a_id/10477/~/user-guides-for-broadband-hardware)

---

### Post by MG&amp;TL on 2011-09-25
"BT Home HUB KTQ2"

Several version down from this:

[http://www.productsandservices.bt.com/consumerProducts/displayTopic.do?topicId=25746]("http://www.productsandservices.bt.com/consumerProducts/displayTopic.do?topicId=25746")

Would that harm the internet elsewhere on my home network in any way?

---

### Post by Doug S on 2011-09-25
Returning to your original post: If your web pages work with the windows 7 computer and your liinux LapTop computer, then they should work fine for everyone. So maybe the rest of this thread becomes academic.
 
I have not been able to find out how to do port forwarding on your unit. I think it can be done, because I did find a reference about resetting port forwards. Also, some ISP's block port 80 for dynamic IP addresses. I don't know about BT.>  
Would that harm the internet elsewhere on my home network in any way?
No, it shouldn't. At least as long as your server is the only web server on your network.
 
Try this link: [http://portforward.com/english/routers/port_forwarding/BT/BTHomeHub/default.htm](http://portforward.com/english/routers/port_forwarding/BT/BTHomeHub/default.htm)

---

### Post by MG&amp;TL on 2011-09-25
Their AUR did say something about port forwarding...never mind, I set it up for filesharing, got curious about what I could do.

Well, thanks for the help. If I end up living on my own at any point (housing in UK is *insane* at the moment) ,I'll try the port forwarding. :)

---

