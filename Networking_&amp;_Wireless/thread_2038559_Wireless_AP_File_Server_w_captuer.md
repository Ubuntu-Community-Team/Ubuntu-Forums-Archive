---
title: "Wireless AP File Server w/ captuer"
date: 2012-08-06
forum: Networking &amp; Wireless
---

### Post by catgrepuniq on 2012-08-06
I am not sure what software is required and thought someone here might have suggestions to point me in the right dirrection. 

I want to make a wireless fileserver that is easy for users. The device will serve files only, probably all static content,  use  nginx or apache, not recive files via upload, and have no internet connection when in opperation. 

I want to use an Atom board with 1 Mini PCI Express wireless card so it is not too expensive. 

This device MUST appear to be an open wirelss access point, and redirrect all browser traffic to itself so non-tech savvy users will find it with their browsers. 

This is not going to have private files on it, so I want no irritating authentication mechanisms whatsoever. Anyone can connect and view content (I will connect via ssh/scp to add files or make changes). 

I don't know how to make a wireless card appear to be an access point or redirrect browser traffic to itself. Anyone have suggestions?

---

### Post by Dylan1473 on 2012-08-06
I've never set up such a server as an access point, but I can tell you a few things that might help you.

First, and really important: be *very* careful in the wireless card you choose. Most don't support master mode. You should look [here]("https://help.ubuntu.com/community/WifiDocs/MasterMode") for an explanation of what I'm talking about plus [this Wikipedia page]("http://en.wikipedia.org/wiki/Comparison_of_open_source_wireless_drivers#Driver_capabilities") for a list of drivers that support master mode. As an alternative you may be able to use a wireless router or access point in conjunction with your actual server. This may be non-ideal though. Otherwise a cursory Google search should reveal an abundance of tutorials for making a Linux access point, most of which will be somewhat dependent on the particular programs you choose to use.

I'd recommend getting the server edition of Ubuntu. Are you comfortable working with the command line? It sounds like it based on what you said. That will be extremely helpful and probably necessary when running a server. For redirecting web traffic to a page of your choice (specifically on your server) I think you'd need some kind of wireless hotspot solution (never done it so not 100% sure, but have looked into it). A cursory search reveals [coova.org]("http://www.coova.org/CoovaChilli"), I'm not sure if it'd be to your specification. There's probably a simpler method to do what you're asking for since you don't need any sort of authentication.

Otherwise it sounds like you pretty much just need an ftp server. I've used [proftpd]("http://www.proftpd.org/") in the past (no major complaints) and heard good things about [vsftpd]("https://security.appspot.com/vsftpd.html") (that aims more toward security though so the former might be best for you). Oh, you might need a DNS also for redirecting traffic to your machine (again, never done this before so maybe you don't if it's just the one server). You'd probably just use bind for that. Also, non-essential to what you're going for but helpful, I'd recommend [webmin]("http://www.webmin.com/") for helping manage it. I find it's a more efficient way of dealing with some things than directly through the command line.

EDIT: I should add that while using a router might cause problems and drain more power, it'll also probably give you better range/signal etc. Routers are designed to be access points after all and wireless adapters often don't handle it as well. You can tweak that, of course. What kind of range are you looking for anyway?

Additionally, I'd just like to clarify that I suggest hotspot solutions like CoovaChilli for the traffic redirecting. That's not strictly the main purpose of them (though what you're going for is kind of in line with what it's for) and you may well be able to do it in another way since you don't need authentication or plan on charging people or anything. That's just the first thing that I can think of for it.

---

### Post by catgrepuniq on 2012-08-06
Thank you for the info and quick reply. Yes, I am comfortable with command line. I currently use a wireless router with an ESSID of "see http://192.168.0.2/" where 192.168.0.2 is a server, but would like an all-in-one solution. I will def look into the master mode thing when i buy hardware and check into webmin. :)

---

### Post by Dylan1473 on 2012-08-06
I should add that the thing from Coova you might need is CoovaChilli. I corrected the link to point to directly that. You probably already realized. Anyway, I also just happened upon [this]("https://help.ubuntu.com/community/WifiDocs/CoovaChilli"), which explains how to set it up. It also notes something rather important: you need *two* network adapters. Now, maybe that's only if you want to use the internet but it's possible it's set up to require that. I was trying to set up something similar on ClearOS a while ago and the option didn't even show up since I only had one network card (this was strictly through the GUI though and I'm not even sure it was using CoovaChilli).

---

### Post by catgrepuniq on 2012-08-07
Thank you, Dylan1473I, you pointed me in the right direction. I have been doing further research. There is a program called hostapd that turns wireless card into an access point. It works my wifi card, which is too new to allow for master mode with iwconfig.  However, I discovered that someone has already started a project to serve files wireless.. I think i can copy a lot of their config files. 

 Here are some links in case anyone finds this or you're interested: 

   [http://wiki.daviddarts.com/PirateBox_DIY](http://wiki.daviddarts.com/PirateBox_DIY) [https://github.com/MaStr/PirateBoxScripts_Webserver](https://github.com/MaStr/PirateBoxScripts_Webserver)   

Supposedly, PirateBox scripts can do the following:     
* Setup WLAN Interface via iw     
* Setup hotspot functionality (hostapd)     
* Setup IP Adresses of wlan interface     
* Can add wlan interface to an existing bridge     
* Sets Up a DHCP Server with redirect to wlan-interface IP     
* Upload landing page  (via iframe droopy)     
* Browse Uploaded files     
* Announce &quot;Internet yes&quot; for iOS     
* ShoutBox     
* Optional small python Forum     
* Optional imageboard     
* Optional Station counter     
* Optional Inihibit starting upload-script   

I don't need all of that stuff, just  most of it

---

