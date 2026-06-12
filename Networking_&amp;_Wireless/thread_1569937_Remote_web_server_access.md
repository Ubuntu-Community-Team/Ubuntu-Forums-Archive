---
title: "Remote web server access"
date: 2010-09-07
forum: Networking &amp; Wireless
---

### Post by bb6600 on 2010-09-07
Hello there!

I have installed Ubuntu Server (lamp+openssh) on a laptop in order to use it as a testing web server for my projects. After configuring it I've also installed the GUI to make things easier as I'm not very proficient using just the command line.

I'm using the wireless connection on the laptop to communicate with the router and my main desktop (Windows). I've assigned it a static local IP (192.168.1.99) in order to be able to access the sites on my web server from my desktop, and everything works fine.

Now comes my problem: I need to be able to access those local sites from a remote location (outside of my local network) as well. How can I do that?

---

### Post by wesleybailey on 2010-09-07
Do you want to be able to view the pages _only_ from a remote location?

Or do you want to view and edit the files from a remote location.

I have my personal website on a laptop with a local static ip. I then mapped port 80, to that ip. So that the website is available remotely.

If you connect to the internet with a dynamic ip then you will need to know your WAN ip ahead of time, or setup dynamic dns.


Latest Tutorial: [.uif to iso ]("http://wesleybailey.com/articles/uif-to-iso-converter")

---

### Post by bb6600 on 2010-09-07
@wesleybailey: 
Viewing-only from the remote location should be fine so I guess it's pretty much similar to your own setup. 

How do I map the port to my local IP?

---

### Post by bb6600 on 2010-09-07
Never mind, I figured it out that port mapping is done from the router interface :)
Seems to be working now.

Any special security issues I should be aware of?

---

### Post by Strategist01 on 2010-09-07
> **bb6600 said:**
> Never mind, I figured it out that port mapping is done from the router interface :)
Seems to be working now.

Any special security issues I should be aware of?

Security issues - not much but if you want to have your local network protected I suggest that you use 12 character long passwords - they have been shown to be the hardest to crack. Use the passwds on all PCs. You also might want to make sure you can SSH into your laptop - this is a really secure way of connecting.

Other users will give more/better advice, but that will set you on the right track :)

---

