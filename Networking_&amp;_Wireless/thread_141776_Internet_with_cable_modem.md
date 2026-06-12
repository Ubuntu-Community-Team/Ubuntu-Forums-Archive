---
title: "Internet with cable modem"
date: 2006-03-09
forum: Networking &amp; Wireless
---

### Post by zina on 2006-03-09
Hello,

I'm not experienced in Linux, I just want it to work. ;) I'm having trouble with connecting to the Internet from home using a cable modem. The modem works fine, that is, it's connected to the server. I called the support of the provider, and they told me that, but they do not support Linux.

When I plug in the cable, I do not receive any IP address. Perhaps, the DHCP client doesn't work with the modem?

I use dhcp-3 client. To tell which modem I use, I'd have to look at home (I inherited it from the previous flat inhabitant, and it's most probably no-name and around 5 years old).

At work, I use DHCP, and it works fine.

Zina

---

### Post by thnogueira on 2006-03-09
It seems you are having problem with the MAC-address. I suppose you have windows installed on this computer? In case this is true, do you know if the MAC is spoofed? You can verify by taking a look at advanced properties of the network adapter in device manager. Look at the field physical address.

---

### Post by zina on 2006-03-09
No, I don't have Windows there. What do you mean by "MAC is spoofed"?

DHCP at work works fine, though...

A colleague davised me to reset the modem, because it might have saved the previous MAC address (from the previous flat inhabitant). I pressed the Reset, rebooted the laptop, but it didn't make any difference.

---

### Post by thnogueira on 2006-03-09
If the modem is getting online, probably the problem is the adapter MAC address.   Some ISPs just assign ip number to the computer if the network MAC is registered on their database. If it's the case, you have two options:

1 - get the mac address of your network adapter ( run *ifconfig* command and take note of the number similar to this one: HWaddr 00:0E:35:3E:F5:A3). Call your ISP and ask them to register this MAC address.

2 - spoof the mac(not sure if it's legal). You can configure your network card to pretend to be another one. you'll need to know a registered card number (of your work one, for example) and edit the file /etc/network/interfaces. Under the line where it is 

iface eth0 inet dhcp

add the line:

hwaddress ether 00:07:BD:1E:42:5B //this number is an example


I hope it works

---

### Post by sdb2028 on 2006-03-09
Who is your ISP?, what modem do you use? do you use a router? and what is your network adapter?
I have Comcast through a Linksys Broadband wireless router accessed through an internal Intel Centrino ipw2200bg wireless adapter. All works great.

---

### Post by zina on 2006-03-09
Provider: ComHem, Sweden

The problem is that I rented the flat with the modem already installed, so formally, I'm not the customer of ComHem, and they refuse (!!) to give me supprot. They do not support Linux, but they wouldn't tell me which MAC address they saved for my modem, for example, and they wouldn't register a new one for me. :(

Well, my configuration is entirely differnet from yours. My next move, I guess, would be to borrow a Windows laptop from somebody and to try whether the Internet works on it. (I don't dare to install Windows onto my laptop, because I heard it might go very wrong, and I have a half-finished presentation on it right now, and need to work on it further...)

---

### Post by thnogueira on 2006-03-09
Beleive me. You need a registered mac adrress number and spoof your adapter's one to seems like the registered. It has nothing to do with your OS.
I'd could tell to how to sniff packages with ethereal but it'd be probably against the law.

Come on, it's Sweden. Is that so expensive?

---

### Post by sdb2028 on 2006-03-09
Is your landlord a customer of ComHem? If so, try to get them to get the info for you. It may be that there is no current subscription to the service. You may need to subscribe and have it turned on.

---

### Post by zina on 2006-03-09
I asked the ISP if they save PC mac addresses. Here is their reply: "We don't register any macadresses from the computer/networkcard itself. The mac adress we register in our system is the one from your cablemodem."

So it really seems to be the problem with the laptop talking to the modem. What do you think?

---

### Post by sdb2028 on 2006-03-09
run "ifconfig" and post the results.

---

### Post by sdb2028 on 2006-03-09
P.S. Are you wired to the modem? or wireless?

---

### Post by zina on 2006-03-09
[QUOTE=sdb2028]Is your landlord a customer of ComHem? If so, try to get them to get the info for you. It may be that there is no current subscription to the service. You may need to subscribe and have it turned on.[/QUOTE]

The subscription continues, as far as I understand. But it's generally a good idea to ask her how and if she is payng for the service.

---

### Post by zina on 2006-03-09
It's a wired connection. ifconfig was looking like this yesterday:

eth1      Link encap:Ethernet  HWaddr 00:0A:E4:2E:6D:00
          inet6 addr: fe80::20a:e4ff:fe2e:6d00/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:57161 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18851 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:21885538 (20.8 MiB)  TX bytes:4280062 (4.0 MiB)

Before you ask: eth1 is the right interface number (or how do you call this). So the entire line with ip address, subnetmask etc. was missing. Now at work I have this:

eth1      Link encap:Ethernet  HWaddr 00:0A:E4:2E:6D:00
          inet addr:130.238.8.162  Bcast:130.238.8.255  Mask:255.255.255.0
          inet6 addr: fe80::20a:e4ff:fe2e:6d00/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:57161 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18851 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:21885538 (20.8 MiB)  TX bytes:4280062 (4.0 MiB)

---

### Post by sdb2028 on 2006-03-09
It looks as if everything (except getting the ip addr from DHCP) is working. Can you find out for SURE that there is a current subscription to the service?

---

### Post by zina on 2006-03-09
Hooray, the support finally parted with some information.

Yes, the subscription is valid, and the service is being paid for automatically.

---

### Post by sdb2028 on 2006-03-09
Go to System-Administration-Networking-Ethernet Connection-Properties, Tell me everything listed in the window.(for your settings at home)

---

### Post by thnogueira on 2006-03-09
What cable modem (cm) are you using? You can try to configure static ip and test the connection between the pc and the cm. For example, I have an motorola cm and the configuration page is
[http://192.168.100.1]("http://192.168.100.1").
So I set my like:
ip: 192.168.100.10
netmask:255.255.255.0
gateway: 192.168.100.1

Then I can access the config page and see if it's everithing ok: Was the boot complete? How is the signal? Did the modem got the correct file? Could it stablish the time of the day? etc...  If it's everithing ok, try to spoof the mac addres of your network card with the job's  number (00:0A:E4:2E:6D:00).

Finaly,
you can try to run some live Dist (knoppix, i. e.) to see how it behavior.

---

### Post by zina on 2006-03-09
How an I find out the address of my configuration page?
Or is it the same for every modem?

(To look which modem, I have first to get home)

---

### Post by thnogueira on 2006-03-09
Each modem model has it's addreess. The common ones are 
[http://192.168.100.1]("http://192.168.100.1")
[http://192.168.1.1]("http://192.168.1.1")
[http://192.168.0.1]("http://192.168.0.1")
[http://192.168.2.1]("http://192.168.2.1")

Depending on the model, it has user/passwd restriction. You can easily find in the internet the dafault for your modem. 

EDIT: to configure it staticaly at home, use the example a gave on my last post, but make sure the third field of ip addess is the same of your modem (and the gateway) If the modem's page is 192.168.1.1, you can set:

p: 192.168.1.10
netmask:255.255.255.0
gateway: 192.168.1.1

---

### Post by sdb2028 on 2006-03-09
Making any progress?

---

### Post by zina on 2006-03-10
Well, not really making progress, but gradually getting more and more information. ;)

Modem:
Scientific Atlanta  EPX 2203
(plugged into the Ethernet, not USB)

Things written under
System-Administration-Networking-Ethernet Connection-Properties:

Device: eth1
[x] Enable this connection
Configuration: DHCP

ifconfig at home:

eth1      Link encap:Ethernet  HWaddr 00:0A:E4:2E:6D:00
          inet6 addr: fe80::20a:e4ff:fe2e:6d00/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1574 errors:7825 dropped:0 overruns:0 frame:7825
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:94478 (92.2 KiB)  TX bytes:2430 (2.3 KiB)

---

### Post by zina on 2006-03-10
[QUOTE=thnogueira]
Depending on the model, it has user/passwd restriction. You can easily find in the internet the dafault for your modem. 
[/QUOTE]

I couldn't do this. I found a data sheet (in Google's cache!)
but no ip address there. I can try out addresses you gave me,
once I'm at home again.

---

### Post by thnogueira on 2006-03-10
Try 192.168.100.1.

Is the same computer you are using on both places (work/home)? Did you spoof the MAC? I've just noted both ifconfig you posted have the same MAC address.
When you leave the work, do you turn of the computer? You can try to configure your home pc, with the same parameters ISP gave you at work.

Did you try using another dist cd? It would test if it's some installation problem.

---

### Post by zina on 2006-03-10
Yes, I only have one computer, which is the laptop provided to me by the university.

I turn it off when I go home.

ISP at work is the university, and ISP at home is a private company. I cannot see the point in configuring the laptop at home like the laptop at work. But perhaps I'm wrong? And anyway, the configuration always remains the same: DHCP.

I'm sorry, but I still don't understand to which mac address I should spoof.

Knoppix is too advanced for me. Let's try and avoid it. Why cannot things just WORK? ;)

---

### Post by sdb2028 on 2006-03-10
Go into your System-Administration-Device Manager, and see if there is any reference to your modem. You may need to find an updated driver or firmware.
I'll look around on the net to see what I can find- I'll post back in a little while and let you  know.

---

### Post by thnogueira on 2006-03-10
I'm sorry zina,

I've just realized it's about 1 pc and 2 isp's. I thought it was the inverse. Don't set your ip as static. Don't try another dist. It's everything ok with your installation. I mean, the problem is not your computer.

There are 2 option:

- The problem in the cable modem. You may try to access the config modem and watch the log, status, etc. Sometimes it seems to be online but it's configured to not allow internet access. There is nothing to do with linux and you might request for tecnhical support. In the last case, try to find an ISP that can give you internet access.

- The ISP is not giving assign you a ip. IMHO there is nothing to do with linux and you might request for tecnhical support. In the last case, try to find an ISP that can give you internet access. (maybe you should try dhcpcd client, and pray a lot)

EDIT:

```
Go into your System-Administration-Device Manager, and see if there is any reference to your modem
```

The modem is not referenced in ANY case. Just the ethernet adapters. For the computer side, cable modem is like LAN.

---

### Post by sdb2028 on 2006-03-10
Ok, didn't want to mislead her, just thought it would be something to check. Trying to find references to that modem on internet, haven't found much.

---

### Post by mips on 2006-03-10
Zina,

Looks like your interface is eth1, do you have a eth0 ? Maybe try eth0.

Substitude you interface number below if you are not using eth1. Alternatively if you have both try both and post output for each one as per instructions below.

1. Please disable IPv6 and reboot:
```
sudo mv /lib/modules/$(uname -r)/kernel/net/ipv6/ipv6.ko /lib/modules/$(uname -r)/kernel/net/ipv6/ipv6.ko.bak
sudo depmod -a
```
2. Please post output of **sudo mii-tool eth1**
3. Please post output of **ifconfig eth1**
4. Please post output of **lspci | grep Eth**
5. Please post output of **route -n**
6. Please post output of **cat /etc/resolv.conf**
7. Please post output of **cat /etc/network/interfaces**
7. Please copy **entire** output of windows **ipconfig /all** command here

Another place to try is [http://forum.directconnect.se/index.php](http://forum.directconnect.se/index.php) as people there could possibly give you more information on ComHem & Linux or do a search. I would have a look but my Swedish is not to hot, although a germanic language the scandinavian versions are to hard to read, especially Icelandic ;)

We know:
ISP- [http://www.comhem.se/publik/www/portal/all](http://www.comhem.se/publik/www/portal/all)
Modem- [http://www.scientificatlanta.com/products/customers/prod_sub_VoIP.htm](http://www.scientificatlanta.com/products/customers/prod_sub_VoIP.htm)

---

### Post by zina on 2006-03-10
Hello,

eth0 is the WLAN card so no point trying. ;)

I cannot speak Swedish either, but nevertheless, I can try and ask them in English, so thanks for the pointers.

Other things would have to wait 1 week, I'm afraid, I won't be here. In any case, if I find _any_ solution, I'll post it here.

Cheers,
Zina

---

### Post by mastergunner on 2006-12-27
I have a Scientific Atlanta USB modem and I cant connect to the interent in Ubuntu. I am a newb and totally lost. It is a WebStar DPX2203. What should I do?

---

### Post by mips on 2006-12-28
You are going to battle with USB.

Use the ethernet port !

---

