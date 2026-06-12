---
title: "Level One Wireless card (RT2500)"
date: 2006-03-14
forum: Networking &amp; Wireless
---

### Post by tmafcerqueira on 2006-03-14
Hi
I'm new to linux and I wanted to use my wireless card to connect to my router and surf the web. The only problem is that I've bought a LevelOne WNC-301 11g Wireless PCI card and EVEREST Home edition says (in network/Windows Network) that I have this card but in netwok/PCI / PnP Network I have a Ralink RT2500.
I've visited ralink website and aparently the RT2500 is a chipset. My question is: Will the drivers from the RT2500 work on my card? If yes, were can I find them?
Thx for helping out a complete newbie :D

---

### Post by djroadrash on 2006-03-14
hi tmafcerqueira:
your cards chip should be supported in ubuntu and other debian distros, i have used a smc card with this chip and it works out of the box.
check system>admin>networking and see if it comes up there, select if it does and check the properties  now u can enable wep, put the network name and the password. or if no wep just enable dhcp. activate and check if it works
if not do this on terminal.
```
$lspci
```
and 
```
$dmesg
```
this will tell u what hardware u have and help find what drivers u need. post the result here 
this is a good page for more info
[https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards]("https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards")
good luck:)

---

### Post by jml on 2006-03-14
A little more information would be helpful.  First, what version of Ubuntu are you using.  Second if you are running version 5.10, you may already be half way there.  5.10 includes some support for the ralink 2500 chipset.  

If you are running 5.10, try restarting your computer with the wireless card plugged in.  Then open up the network configuration application, supply your password and then look to see if the wireless card is listed.  If it is, then highlight the card, click on properties and type in your information.  Click on OK and then highlight the card again and click on activate.  It can take several minutes for the activation process to complete.  If all went well, you should have a connection.  

As shipped, Ubuntu supports both unencrypted wireless connections and connections encrypted with WEP.  If you need WPA or WPA2 encryption, things get a bit more troublesome.  One would normally use an application called WPA_Supplicant to configure WPA encryption, unfortunately, WPA_Supplicant does not support the rt2500 chipset.  You need to find and install an application called Raconfig.  Theoretically, this will enable support for WPA encryption in Linux with the rt2500 chipset.  To be honest, I was never able to get it to work, but there are other postings on this forum that suggest that it does in fact work.  Hope this helps.

Joe

---

### Post by tmafcerqueira on 2006-03-14
I'm terrebly sorry. I forgot. I'm using version 5.04
I'm going to try the solution you gave me djroadrash.
Thank you both

---

### Post by djroadrash on 2006-03-15
im not sure if 5.4 will recognize your card but it is posible. if not u can always use this guide [https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show&redirect=SetupNdiswrapperHowto]("https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show&redirect=SetupNdiswrapperHowto")
come back with info on what happened
good luck

---

### Post by tmafcerqueira on 2006-03-17
Hi again. This might sound stupid but I haven't even got out of the "easy" part:
How do I copy the NdisWrapper to linux from windows? I've tried a USB pen but linux didn't recognized it like windows does. I tried a floppy disk but it didn't work as well. How can I do it?
Thanks

---

### Post by djroadrash on 2006-03-18
i dont know much about windows i use mac and linux but if u can maybe use a hardwire on your router and download the stuff into ubuntu that way, it would be much easier. did u try the ethernet card on your laptop?. just a thought, since i dont use windows and cant tell u, a burned cd could work as well.

---

### Post by tmafcerqueira on 2006-03-19
I'll try burning a CD. I was just hoping I could do it without "spending" money:D . I'm not sure if I got the right file. It has only 22KB:-k 
I tought this would be a larger file. Can you tell me if I have it right?
Btw, Mac-OS is a great choice. I like it. It's good to see people not depending on Gates's software

---

### Post by djroadrash on 2006-03-19
i understand about the money issue. but it should be free or almost free to get your card running, only work, the good kind:)  maybe if it gets too hard, if u have the chance still to trade your card at the store and get one that is supported for sure. just a thought

---

### Post by tmafcerqueira on 2006-03-24
I can't. But ndiswrapper should do it. Haven't tried it yet(exams](*,) )Do I have the right file? It's only 22kb:-k . Do I have to compile it?

---

### Post by tmafcerqueira on 2006-03-24
Never mind. I got it. I'm going to try it now.
Thanks for helping me out;)

---

