---
title: "internet problem"
date: 2009-04-22
forum: Networking &amp; Wireless
---

### Post by demosthenes456 on 2009-04-22
okay so after two days i finally installed my wireless driver using ndiswrapper. now the problem is... when using windows i had to connect to the netwrk and then use a seperate dial up connection to connect to the internet via the wireless network.
My main modem is wireless and set to bridge mode.. so i have to use a dial up to connect to the internet. now it cant be changed back. so my problem is i am connected to my wireless network in linux but i cant create a dial up that connects to the internet

the ips and subnet masks are on dynamic.. i need help creatin a broadband connection that connects via my router. i was on the point to point and changed it to pppoe and typed in my username and password and when i go to modem it only gives me the (etho) option i need help creatin a step by step connection to the internet via my wireless. i am really new to linux so step my step would be nice.. is ther maybe any .deb packages i need to download? and can u maybe provide a link to them and there dependencies

ok in windows i connect to the wireless network. and then in the create a connection option i choose the connect to internet>setup manually>connect to broad band using name and a password> then its finished.. windows automatically connects to the internet throught the wirelesscard i need help doing this in linux ubuntu

---

### Post by ulpiano on 2009-04-22
Check this link [https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html]("https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html")
I've read that the latest version of network manager (0.7 I guess) doesn't allow to set pppoe connections over wireless. That's strange because older versions did.
Sorry,my English is bad.

---

### Post by ulpiano on 2009-04-22
This link can be useful, but it's in Spanish [http://patagonianuser.blogspot.com/2008_05_01_archive.html]("http://patagonianuser.blogspot.com/2008_05_01_archive.html")
Google Tranlation could help you.

---

