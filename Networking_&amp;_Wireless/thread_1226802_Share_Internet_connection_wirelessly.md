---
title: "Share Internet connection wirelessly?"
date: 2009-07-29
forum: Networking &amp; Wireless
---

### Post by ShinHadoken on 2009-07-29
Running Ubuntu 9.04 on my laptop, and here's the deal. In the science building where I go to class, there's no Wi-Fi. So, what I do is I tether to my cell phone via a bluetooth usb dongle and use the DUN profile, and use it as a dial-up modem. This works. However, I have a friend who sits behind me who can't tether because he has an iPhone, and we take turns with my phone. This is inconvenient. Is there a way that I can tether to my phone on my laptop, and then share this connection with my friend, who's running Windows XP,  behind me over my Wireless card?

---

### Post by superprash2003 on 2009-07-30
yes , you could do ICS .. you could either do it via firestarter which has the ICS feature , or manually this way [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

---

### Post by ShinHadoken on 2009-07-30
Alright, so on that page I followed this [link]("https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless") and it looked to be exactly what I'm looking for! Just one question: to do this, you have to edit the /etc/network/interfaces file. I only need to use this configuration for a couple of hours a day, is there a way that I can comment out those lines when I'm not using them or something? If so, what comment character do I use, '#'?

---

### Post by Iowan on 2009-07-30
> **ShinHadoken said:**
> If so, what comment character do I use, '#'? That should work!

---

### Post by ShinHadoken on 2009-08-06
Ok, question: at that wiki page I cited, it says that you can protect your connection using a hex WEP key. First of all, how do I generate one (what about text key?), and secondly, can I use WPA here? It would be preferred.

---

### Post by ShinHadoken on 2009-08-11
Bump

---

### Post by bear24rw on 2009-08-11
idk if it will work with tethering but it works for me with ethernet. to set up your laptop as a router click the network manager icon and select make new connection and then give it a name and some security if you want, let it finish and thats it, your friend should be able to see your computer as a wireless ad hoc network

---

### Post by ShinHadoken on 2009-08-11
The question is no longer is this possible, but it is the following:


> **ShinHadoken said:**
> Ok, question: at that wiki page I cited, it says that you can protect your connection using a hex WEP key. First of all, how do I generate one (what about text key?), and secondly, can I use WPA here? It would be preferred.

---

### Post by ShinHadoken on 2009-08-12
Bump

---

### Post by bear24rw on 2009-08-12
it gives me the option of wep and wpa, for web key if it needs hex just use numbers and letter a-f

---

### Post by ShinHadoken on 2009-08-12
Where does it give you this WEP/WPA option? In the /etc/network/interfaces file? Or in some other program you are using?

---

### Post by bear24rw on 2009-08-12
> **ShinHadoken said:**
> Where does it give you this WEP/WPA option? In the /etc/network/interfaces file? Or in some other program you are using?

when i left click network manager icon in toolbar > create network connection > Enter name & choose security

---

### Post by ShinHadoken on 2009-08-12
That's for adding a new network connection for Ubuntu to use, not for sharing an existing connection over a wireless interface, which is my goal here. I know it's possible through /etc/network/interfaces, as mentioned [here]("https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless#Configuring%20the%20SERVER"), but I want to know if I can encrypt that connection using WPA instead of WEP.

---

### Post by bear24rw on 2009-08-12
> **ShinHadoken said:**
> That's for adding a new network connection for Ubuntu to use, not for sharing an existing connection over a wireless interface, which is my goal here. I know it's possible through /etc/network/interfaces, as mentioned [here]("https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless#Configuring%20the%20SERVER"), but I want to know if I can encrypt that connection using WPA instead of WEP.

Have you tried it? I did it that way like two days ago, i connected a windows XP laptop to my linux laptop wirelessly using the method i described above..

---

### Post by ShinHadoken on 2009-08-13
Hmm, my apologies sir! (or madam?) There's some problems, however: When I picked the security, I chose WPA and it wouldn't let me create the connection. Does anyone know why this is? Secondly, I just went with WEP 128b passphrase for testing purposes, and gave the password as "asdf", a dummy value. My laptop, which  now saw the wireless connection it just created, tried to connect to it (this is the Ubuntu laptop, sharing an ethernet connection for testing purposes) Network Manager reported zero signal on the new connection, and kept asking me for the WEP phrase. Did I make the phrase too short? Can I not connect to my laptop with the same laptop (because of ad-hoc mode, perhaps?) Do I still need to go through Firestarter and share the ethernet connection (a step I skipped due to time, and curiosity of how much of the work Ubuntu would do for me) And once again: why no WPA? Must the WPA passphrase meet a minimun length as well?

---

### Post by ShinHadoken on 2009-08-14
Bump

---

### Post by ShinHadoken on 2009-08-14
BumpP? (Bring up my post, please)

---

### Post by ShinHadoken on 2009-08-15
> **ShinHadoken said:**
> Hmm, my apologies sir! (or madam?) There's some problems, however: When I picked the security, I chose WPA and it wouldn't let me create the connection. Does anyone know why this is? Secondly, I just went with WEP 128b passphrase for testing purposes, and gave the password as "asdf", a dummy value. My laptop, which  now saw the wireless connection it just created, tried to connect to it (this is the Ubuntu laptop, sharing an ethernet connection for testing purposes) Network Manager reported zero signal on the new connection, and kept asking me for the WEP phrase. Did I make the phrase too short? Can I not connect to my laptop with the same laptop (because of ad-hoc mode, perhaps?) Do I still need to go through Firestarter and share the ethernet connection (a step I skipped due to time, and curiosity of how much of the work Ubuntu would do for me) And once again: why no WPA? Must the WPA passphrase meet a minimun length as well?

Sorry guys, don't mean to be pushy, but it's important to me that I can get this to work, and answers to any of the above questions would be a big help!

---

### Post by ShinHadoken on 2009-08-16
Come on guys, please don't leave me high and dry! =(

---

### Post by ShinHadoken on 2009-08-17
I hereby declare this thread shipwrecked. Makes me sad, I really needed this to work. ;(

PLEASE input if you can, this thread is NOT solved.

---

