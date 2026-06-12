---
title: "cant connect throgh wireless"
date: 2009-11-01
forum: Networking &amp; Wireless
---

### Post by amiryaiar on 2009-11-01
Hello, 

I am a newer instaling ubuntu yesterday succesfully. 
Usin Thinkpad t 60 an a [Linksys ]("http://www.linksysbycisco.com/US/en/products/WAP54G")router. 

trying connect through "sudo pppoeconf" I am finally getting:

Sorry, I scanned 3 interfaces but the excxes concetretor of your providor did not respond, please check your network and modem cables. Another reason for the scan failor may also be another running pppoe process witch control the modem

Can somebody please give a hand here? 

Thank you

---

### Post by coffeeaddict22 on 2009-11-02
Hi amiryaiar,
Sounds complex.  
First, where are you doing the pppoeconf?  There are a few potential sites for problems.  
Linux needs to be recognising your network card- are you wired or wireless?
The network card then has to connect to the router
Finally, your router needs to be connected to the internet via a local connection.
The pppoeconf sounds like you're in the router settings; these shouldn't have needed to be changed no matter what Operating system you're running on your PC.  Have you changed all your hardware?

If you're in Ubuntu, use the network manager.  It should be an item on the top bar; it's also in System/Preferences/Network Connections.  If not, what are you running?  Kubuntu?  Xubuntu?  Mint?

---

### Post by amiryaiar on 2009-11-02
> **coffeeaddict22 said:**
> Hi amiryaiar,
Sounds complex.  
First, where are you doing the pppoeconf?  There are a few potential sites for problems.  
Linux needs to be recognising your network card- are you wired or wireless?
The network card then has to connect to the router
Finally, your router needs to be connected to the internet via a local connection.
The pppoeconf sounds like you're in the router settings; these shouldn't have needed to be changed no matter what Operating system you're running on your PC.  Have you changed all your hardware?

If you're in Ubuntu, use the network manager.  It should be an item on the top bar; it's also in System/Preferences/Network Connections.  If not, what are you running?  Kubuntu?  Xubuntu?  Mint?

Yes, wirless connection. I am with Ubuntu
I have entered the network connections there under the wirless tab I have nothing. 
Clicking the ADD leed me to options I have no idea what to do with them.

---

### Post by coffeeaddict22 on 2009-11-03
Can you open a terminal (Applications/Accessories/Terminal), and type in the following two commands.  Post the output back; it'll give us somewhere to start from.
```
lshw -C network
nm-tool

```

---

