---
title: "University wireless networking"
date: 2006-06-18
forum: Networking &amp; Wireless
---

### Post by naught101 on 2006-06-18
newbie alert. I recently got the BCM43xx driver working, to some extent, and can connect to an unsecured network at my friends' place and browse the net. it's great, it tends to drop out a bit, but that's probably a network problem.

what I really need, though is help getting on to the wireless network at Newcastle Uni, Aus. it uses the Eduroam system, which I think a lot of Universities use. in their own words:
*"The network has a high degree of security and utilises the latest in encryption and authentication mechanisms. It uses IEEE 802.1x authentication with dynamic WEP keys and supports several EAP types."*

there's a relatively simple setup procedure for windows XP or mac, which is most easily understood by checking out one of the instructions pages here: [http://www.newcastle.edu.au/service/library/aic/laptop.html#su](http://www.newcastle.edu.au/service/library/aic/laptop.html#su)
(the rtfs are big files, cause of pictures, the XP wireless one is the smallest, at 5Mb, and the important text part is copied below)

what I cant figure out is the authentication. is there any way to accept dynamic WEP keys from the server in linux/kubuntu?

on XP, I'd log on the UNCLE domain, using EAP, I haven't seen any options for this in the wireless, I'm guessing I need wpa_supplicant ([http://hostap.epitest.fi/wpa_supplicant/)](http://hostap.epitest.fi/wpa_supplicant/)), right?

has anyone else done this before, are there any tutorials availiable, or can anyone give me some pointers?

I'm running kubuntu 6.06, and have a basic understanding of commandline stuff...

cheers
ned

-------------
WIRELESS XP at NEWCASTLE UNIVERSITY

For Windows XP
1.	Click > Start
2.	Click > Control Panel
3.	Click > Network and Internet Connections 
4.	Click > Network Connections
5.	Double-click > Wireless Network Connection
6.	The Wireless Network Connection box opens. net.newcastle.edu.au should be listed. Highlight this and click on the Properties button.
7.	The Wireless Network Connection Properties box opens. 
8.	net.newcastle.edu.au should be listed in Available Networks. Click on net.newcastle.edu.au to highlight it and then click on the Configure button to open the Properties screen.
9.	The Wireless Network Properties box opens.
10.	Click on the Authentication tab – the Authentication tab will be displayed.
11.	Tick the box next to Enable IEEE 802.1x  authentication for this network, and un-tick all other ticked boxes.
12.	In the drop-down box below this, select Protected EAP (PEAP).
13.	Click on the Properties button
14.	The Protected EAP Properties box opens.
15.	 UNTICK:   Validate Server Certificate.
16.	From the drop-down box near the bottom Select Secured password (EAP-MSCHAP v2)
17.	Tick the box next to Enable fast reconnect
18.	Click the Configure button
19.	The EAP MSCHAPv2 Properties box opens.
20.	Un-tick the box next to Automatically use my windows logon name and password (and domain if any)
21.	 Click on OK on each box that is displayed until you are returned to the Wireless Network Connection Properties Box. Close this box. 

The laptop will now attempt to connect to the network.
If successful you will be presented with a login box.
Enter your Internet Access username and Password, and in the Login Domain box enter UNCLE as the domain.
If your username and password are correct, you will be connected to the network.

---

### Post by trubblemaker on 2006-06-19
check the howto's in my signature for help and if you do some searching of the forums I'm sure you could setup a script in you pre-up command in /etc/networking/interfaces, to detect the network that your around and then use the assigned key.  I'm not familar with the encryption method you talked about, but hope that howto's point you in the right direction

---

### Post by naught101 on 2006-06-19
it's working for normal wep stuff, it's just the dynamic wep stuff that I don't know how to do.

I think I have to set up wpa_supplicant somehow, but I don't know.

I don't really want to set up a pre-ip command in /etc/networking/interfaces, as there are more networks I want to use that just the Uni one.

cheers for the pointers

---

### Post by trubblemaker on 2006-06-19
yeah that's why I use a script, there's my school, work and home, (all with different settings) and if it doesn't find those it assumes I"m at a cafe and uses any availble.(unencrypted.) anyways good luck

---

### Post by Smeggy on 2006-06-22
hi naught101,
I go to utas in tasmania and we also use a 802.1x system, what I use is is xsupplicant (not wpa_suppplicant...although that might work too)... available at [http://open1x.sourceforge.net/](http://open1x.sourceforge.net/)

---

### Post by chubbyjia on 2006-08-10
Hi Smeggy

I am current studying in Utas as well.
I am strying to get xsupplicant to work as well.

Mind sharing what's behind the trick ..,.. i have spent a long time doing it .

My contact is [email]sendtojia@hotmail.com[/email]

Thank you

---

### Post by closey on 2006-11-01
I've connected to the net.newcastle.edu.au network by using NetworkManager (install package network-manager-gnome). After installing it correctly click on the icon in the notification area and choose 'Connect to other wireless network' (note that you must do this and not use the entry that already exists). Next choose 'WPA Enterprise' as the encryption type, PEAP and Dynamic WEP are also in the settings. For the username, use UNCLE\c1234567 and your password.

---

