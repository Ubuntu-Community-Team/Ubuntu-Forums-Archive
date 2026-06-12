---
title: "Mobile Broadband help in 9.04"
date: 2009-05-15
forum: Networking &amp; Wireless
---

### Post by 1993cb7 on 2009-05-15
Ok so i have a 8820 Blackberry and id like to tether it. I see there is options for this under Mobile broadband in the network options section. When i select Tmobile and enter in the settings it never shows up anywhere to select it. The phone is plugged in so im not sure what im missing here. 

Also i found a program named Barry that is suppose to allow you to tether and do all sorts of things with Blackberries. Is it worth it? 

Help:D

---

### Post by 1993cb7 on 2009-05-15
anyone?

Is their a trick to getting responses?

---

### Post by 1993cb7 on 2009-05-15
Ok so i figured out barry and i get it to connect but i get this after a few seconds....

the phone restarts and terminal says:

exception in IPmodem: Datareadthread:exception caught in main():Error in USB_bulk_write script/usr/sbin/pppob finished (pid 18747), status =0x1

Modem hangup 

connect time 0.5 minutes. 
sent 4274 bytes, recieved 7524 bytes
script /etc/ppp/ip-down started (pid 18898 )
connection terminated 
waiting for 1 child processes........
script/etc/ppp/ip-down,(pid 18898 ), 
status =0x0


?????

---

### Post by 1993cb7 on 2009-05-15
20 views and no replys?

---

### Post by 1993cb7 on 2009-05-17
.

---

### Post by meeples on 2009-05-17
im not sure about blackberries but to get my phone to work under mobile broadband, i had to enable the phone to be a modem in the phone itself and then it would automatically connect when i plugged it in to the computer. maybe theres a setting like that in blackberry?


just a guess...

---

### Post by Greyfox_75 on 2009-05-17
Same here. Under Verizon with my windows mobile phone I had to get an app on the phone to enable "Internet Connection Sharing" In linux the phone just shows up as eth1 and the phone/linux software takes care of the rest.

---

### Post by Chiapo on 2009-05-17
I have had absolutely zero success in getting Jaunty to recognize my built in 3G Mobile Broadband modem! (Qualcomm 9121)
I have all the ppp settings correctly entered into Network Manager, yet no device is shown.
Same with all attempts at "tethering" my mobile phone, which works in Windoze.
3G is my only method of connection, due to remote geographic location.
Any advice would be greatly appreciated.
I am seriously considering fdisking the entire hdd and doing a clean install, but if I can't get this netbook online with Ubuntu, doing so is out of the question.

---

### Post by 1993cb7 on 2009-05-18
I get it working but it only lasts about 20 seconds or long enough to load one page, then the phone restarts and i lose connection. 

There is no option in Blackberries to use as a modem so thats out of the question.

---

### Post by danakadan on 2009-05-19
I'm new to linux, new to Ubuntu, fascinated but getting way frustrated with this connection manager that allows me to select ALLTEL from a list and doesnt do anything.  I've searched and searched found program called Barry:  installed it and all what 5 files it needed...   wow my phone can now charge... but no modem.   

There is a program called xmblackberry but I dont understand compiling or taring or sudoing.. oh and xmblackberry needs motif whatever the hell that is...spents hours trying to make that thing download.   

so im stuck screaming and praying for some 9 year old linux wizard from netherlands to make me a nice little pink debian package for blackberry/ ALLtel connections.    *please* 
or links with full explanations and not these post like yeah man I just sudoed compiled it and stuck it in /us/oooo/01010 with the -h trigger after i edited my autorobocop.cfg and backstreet.orh after i divieded by the coefficient logirythem of saturns moons.      

*help!

---

### Post by alan k on 2009-05-19
i recently got a acer netbook one. took xp of cos its crap and stuck ubuntu  9.04 yay!!!

so much better....getting to my point...i stuck my vodaphone mobile broadband in and it installed right away...set it up and all works fine....it however i can't find any software that can show me data usage etc.... can anyone help? 

thanks 
alan

---

### Post by timcredible on 2009-05-19
> **Chiapo said:**
> I have had absolutely zero success in getting Jaunty to recognize my built in 3G Mobile Broadband modem! (Qualcomm 9121)
I have all the ppp settings correctly entered into Network Manager, yet no device is shown.
Same with all attempts at "tethering" my mobile phone, which works in Windoze.
3G is my only method of connection, due to remote geographic location.
Any advice would be greatly appreciated.
I am seriously considering fdisking the entire hdd and doing a clean install, but if I can't get this netbook online with Ubuntu, doing so is out of the question.

well, with a usb-connected mobile broadband modem, 9.04 automatically sees it, all you need to do is click on network manager icon, choose the mobile broadband connection, and 15 seconds later you're on the network, no ppp configuration should be needed.  you do need to activate the card in windows once, however.  if it's built-in, and they didn't use a usb connection for it, then i don't know.

---

