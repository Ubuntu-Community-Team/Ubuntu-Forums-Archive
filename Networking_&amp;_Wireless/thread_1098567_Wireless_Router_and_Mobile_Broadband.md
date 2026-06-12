---
title: "Wireless Router and Mobile Broadband"
date: 2009-03-17
forum: Networking &amp; Wireless
---

### Post by Danspanner on 2009-03-17
Hi folks, first time poster and newbie Ubuntu convert.

I resisted the switch for years, but recently decided to try Ubuntu 8.10, and it worked a treat. Right off the bat it recognised my Huawei Mobile Broadband modem, I connect and within minutes I'm downloading stuff I'll undoubtedly never use from the repositories.

Unfortunately I decided to throw my old Linksys wireless router into the mix.

You see, I was shafted by Telstra down here in Australia over a misunderstanding about my phone line and its capabilities. So now I rely on my mobile broadband connection for any internet. Under windows, if I connect my wireless router via wired ethernet, my modem continues to provide me with internet access.
In Ubuntu, though, if I connect my wired ethernet and attempt to connect to the net, the connection simply times out and I cannot access web pages.  

On top of that, I can access my router in Ubuntu to change settings, but not the net. I can browse the net in Windows, but for some reason cannot access my router. 

So my question is this-
Has anyone out there got any idea how I can set up my network so that the net comes through my Huawei and the router is just for network traffic in Ubuntu? Any suggestions?

---

### Post by halovivek on 2009-03-17
Welcome to ubuntu fourms. 
please check this [link ]("https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html")it will help you.

---

### Post by ugm6hr on 2009-03-17
To be honest, I don't really understand what your network looks like.  A diagram might help...

But I suspect the problem is Network Manager, which I think only allows one network connection at a time.  Hence, when connected to ethernet, it disconnects the Huwaei modem.

Consider giving Wicd a try.

---

