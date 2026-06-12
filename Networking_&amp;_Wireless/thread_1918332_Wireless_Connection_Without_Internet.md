---
title: "Wireless Connection Without Internet"
date: 2012-01-31
forum: Networking &amp; Wireless
---

### Post by phocus on 2012-01-31
Hello,

I am working on a project and part of the scope is for me to broadcast a local version of a custom website (already written) using a small nettop computer, so that others can connect to the computer and view the website. I am running Ubuntu 11.10 on the nettop computer and I have already followed the instruction on how to set this device up as a server (LAMP, but with PostgreSQL instead of MySQL). I thought that I would just need to set up an ad hoc network, however the difficulty is that the project is to be used in areas where there is no internet signal available (hence the necessity to have a local version broadcast rather than having an individual just connect to the website via the internet). All of the "how to's" and tutorials are explaining how to share an internet connection between computers, which wont work in this situation. So in summary I am trying to figure out a way to get my Ubuntu 11.10 computer to broadcast a website on a non-internet network which other devices can recognize and connect to. If you have any advice or guidance, it would be much appreciated. Thank you!!!

~phocus

---

### Post by shumifan50 on 2012-01-31
I don't know what you mean by 'broadcast the website'. However there is no reason you cant do this with an adhoc network as that will allow connection to your server without internet or routers. Infrastructure networks require routers. If you start the server network first then clients can connect to it - I think it will even be visible in a network scan, although I have not checked this as I normally know the network name I want to connect to.

---

### Post by volkswagner on 2012-01-31
I would suggest using an inexpensive WiFi router and ignore the settings for WAN.  It will be a little more equipment, but less support.  I  believe different Operating Systems handle AdHoc in various ways.  If you get a router capable of running DD-WRT, you can simply setup the redirect in the "HotSpot" settings of the WebConfig on the router.  This will force users to your web server, even if they try a different address at first.

If you decide not to go with the router you will want to search how to setup your own hotspot.  Again you will just ignore the WAN portion.

---

### Post by phocus on 2012-02-05
Thanks Volkswagner, what you describe sounds like a great idea. Question: does it matter which router I purchase, or do all have this functionality? 

I actually just posted a new thread becuasue I am now faced with the difficulty of finding a way to automatically redirect all users to my website instantly when they open up their web browser (once connected to my network of course). The thread is found at [http://ubuntuforums.org/showthread.php?p=11665089&highlight=phocus#post11665089](http://ubuntuforums.org/showthread.php?p=11665089&highlight=phocus#post11665089) Please let me know what you think.

---

### Post by tumutanzi.com on 2012-05-19
How can you get wireless without Internet? for me it sounds a bit strange.

---

