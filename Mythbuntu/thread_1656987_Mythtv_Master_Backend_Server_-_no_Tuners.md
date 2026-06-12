---
title: "Mythtv Master Backend Server - no Tuners"
date: 2010-12-31
forum: Mythbuntu
---

### Post by hundred1906 on 2010-12-31
Thinking of using some old hardware to configure an always-on server tucked away in a remote corner. I would want to store music, pictures and recorded TV so it could always be accessed by a separate front end.

For recording TV I have another desk-top with tuner cards installed in PCI-e slots. For various reasons I don't want this to be always-on, just for recording and other desktop stuff only as a secondary backend.

Question - is it a valid configuration for MythTV to have a tuner-less master backend plus a secondary back-end with tuners? Has anyone tried this as a setup?

---

### Post by ian dobson on 2010-12-31
Hi,

I can't see why not, I think the backend could even support wake on lan/sending the slave backend to sleep until it's required.

I've never done it myself, my 3 installations are only simple All in one or split Single Backend/frontend.

Regards
Ian Dobson

---

### Post by williammanda on 2010-12-31
I had a slave backend with a tuner card and it worked fine.

---

### Post by newlinux on 2010-12-31
> **hundred1906 said:**
> Thinking of using some old hardware to configure an always-on server tucked away in a remote corner. I would want to store music, pictures and recorded TV so it could always be accessed by a separate front end.

For recording TV I have another desk-top with tuner cards installed in PCI-e slots. For various reasons I don't want this to be always-on, just for recording and other desktop stuff only as a secondary backend.

Question - is it a valid configuration for MythTV to have a tuner-less master backend plus a secondary back-end with tuners? Has anyone tried this as a setup?

My current master backend has no tuners, and neither does one of my slaves (but three of my slaves do). I've done this for years - as it allows me to have  backends that aren't recording or often used to playback info to help with job processing.

You should be able to do what you want no problems. It will complain when you do the setup that you have no tuners, but you can ignore that.

---

### Post by tgm4883 on 2010-12-31
> **newlinux said:**
> My current master backend has no tuners, and neither does one of my slaves (but three of my slaves do). I've done this for years - as it allows me to have  backends that aren't recording or often used to playback info to help with job processing.

You should be able to do what you want no problems. **It will complain when you do the setup that you have no tuners, but you can ignore that.**

This is not the case with 0.24, you are required to have a tuner configured. However you can set up a dummy tuner that points to a video file.

---

### Post by newlinux on 2010-12-31
> **tgm4883 said:**
> This is not the case with 0.24, you are required to have a tuner configured. However you can set up a dummy tuner that points to a video file.

I'm running .24 - the release note say that, but it hasn't stopped me from doing it. I've noticed a couple of other things incorrect in the release notes as well.

Has it stopped you or are you going by the release notes?

---

### Post by hundred1906 on 2011-01-01
Thanks for the guidance. Any views on the best way to start: Ubuntu Server (+DHCP and LVM) with Myth added; or Mythbuntu?

---

### Post by newlinux on 2011-01-01
It depends on what else you plan to do with the machine. For me, I always start off with ubuntu server or desktop and then add on as I need. I've never actually used mythbuntu proper. With storage groups I have no need for LVM

---

### Post by tgm4883 on 2011-01-02
> **newlinux said:**
> I'm running .24 - the release note say that, but it hasn't stopped me from doing it. I've noticed a couple of other things incorrect in the release notes as well.

Has it stopped you or are you going by the release notes?

I've seen users not able to start the backend without that. It's odd that you can though. Maybe something in your setup, or maybe it just requires a tuner somewhere in your backend.

---

### Post by newlinux on 2011-01-02
> **tgm4883 said:**
> I've seen users not able to start the backend without that. It's odd that you can though. Maybe something in your setup, or maybe it just requires a tuner somewhere in your backend.

You've seen users not be able to start a backend when there are no tuners in the system (on any backend) or not be able to start a backend (secondary or master) when that particular secondary or master doesn't have a tuner but other backend that already exist do? I've helped other users setup tunerless backends, but only when there are tuners available in another backend on the same system. I believe it only won't work when there are no tuners in any backend now.

I don't know what would be special about my setup.

In any event if the OP has problems then adding a dummy tuner should fix it. He may be forced to create a tuner in the master until he can create the secondary with tuners anyway.

---

### Post by tgm4883 on 2011-01-02
> **newlinux said:**
> You've seen users not be able to start a backend when there are no tuners in the system (on any backend) or not be able to start a backend (secondary or master) when that particular secondary or master doesn't have a tuner but other backend that already exist do? I've helped other users setup tunerless backends, but only when there are tuners available in another backend on the same system. I believe it only won't work when there are no tuners in any backend now.

I don't know what would be special about my setup.

In any event if the OP has problems then adding a dummy tuner should fix it. He may be forced to create a tuner in the master until he can create the secondary with tuners anyway.

Not sure, never got that far into troubleshooting as I just had them add a dummy tuner. I suspect it's if the master backend doesn't have a tuner (or doesn't know of a tuner in the environment)

---

### Post by hundred1906 on 2011-01-03
Interesting discussion. I have not yet got as far as creating the new master back-end but am in the process of creating a new server install to run it on using Ubuntu Server. Not sure yet whether I am taking the right approach in bothering with a server or whether to just set up a mythbuntu install instead. The advantages of the latter is that Myth is already using its own protocols for chatting across the local network so there appears to be less need for DHCP and name servers and other similar stuff.

Regarding the tuners issue. In my case the Secondary back-end will be the desktop machine I am currently using as a combined back/front end so there will be tuners in the configuration - just not on the Master. Interesting views on whether or not this is a viable configuration.

---

### Post by newlinux on 2011-01-03
> **hundred1906 said:**
> Interesting discussion. I have not yet got as far as creating the new master back-end but am in the process of creating a new server install to run it on using Ubuntu Server. Not sure yet whether I am taking the right approach in bothering with a server or whether to just set up a mythbuntu install instead. The advantages of the latter is that Myth is already using its own protocols for chatting across the local network so there appears to be less need for DHCP and name servers and other similar stuff.

I'm not sure I get what you are saying. Are you planning on having this machine run as a DHCP server and a name server? Or just connecting to an existing router? The fact that myth uses its own protocols for streaming and communication doesn't really have anything to do with whether the machine functions as a DHCP or name server. Myth's protocols operate on top of basic networking protocols which ubuntu or mythbuntu will have regardless of whether it serves as a networking server or not. Mythbuntu doesn't add anything extra in terms of networking that installing mythtv on ubuntu server wouldn't add. In either case, you have to configure your machine to connect to your home LAN, which in most cases is automatic without installing anything special. this would be the same in ubuntu server, desktop, or mythbuntu.

Maybe I'm just completely misunderstanding what you are saying. In any event, no matter which one you start with you can install any ubuntu packages on them so you can get whatever software you need. 

What all do you plan on using this machine for? Will be used as a desktop at all? Do you prefer Gnome, XFCE, KDE? do you want a minimal install with just the packages you want? These are the types of questions that should guide you to which version of ubuntu to install.
> 
Regarding the tuners issue. In my case the Secondary back-end will be the desktop machine I am currently using as a combined back/front end so there will be tuners in the configuration - just not on the Master. Interesting views on whether or not this is a viable configuration.

It is a viable config for me as I have no tuners in my master backend. One question is will it let you start there if the master doesn't know there are other tuners in other backend. As a test, I deleted all my tuners across my slaves and recreated them with no problem.

---

### Post by hundred1906 on 2011-01-03
Good questions especially as I am just feeling my way through this. I think I want the server just to store and then deliver media around the house, by which I mean recordings, pictures, music and everything else myth can do. The whole server idea came out of two problems with my existing set-up. Firstly my desk-top that currently acts as the master and front-end is in a spare bedroom but sometimes that room is used for guests and then I need to be able to shut it down - but still want to get at recordings via a front-end. Secondly I am also configuring a thin client as a front-end and want that to be able to boot it's image from the network that needs static IP addresses so again this leads to thinking about a server config. Finally I have a spare PC and thought it worth a try building a hub/server that I could put out of the way (I have somewhere in mind my wife has not yet discovered). So the hub/server does not need to be a desktop and I would rather it did not have keyboard, mouse, display etc and just a small install size so the need for extra hardware is minimised. Thought this might be just what lots of people need.

Oh, and I do have some extra hardware to play with. I have a spare router so can easily set up a second network just to develop the config on prior to going live. Also (I think) I have a spare network card so I could configure the hub with two network ports if that was to make life any easier.

---

### Post by williammanda on 2011-01-03
Food for thought...I setup all my computers with a static ip address assigned in the router by computer name. I find this helps out if you are going to use something other than mythtv on your system ie NFS.

---

### Post by hundred1906 on 2011-01-04
> **williammanda said:**
> Food for thought...I setup all my computers with a static ip address assigned in the router by computer name. I find this helps out if you are going to use something other than mythtv on your system ie NFS.

Thanks. How do you do that within the router. Mine is a Linksys WR54G and has DHCP enabled. Is it done through the DDNS setting using [www.dyndns.org?](www.dyndns.org?)

---

### Post by newlinux on 2011-01-04
> **hundred1906 said:**
> Thanks. How do you do that within the router. Mine is a Linksys WR54G and has DHCP enabled. Is it done through the DDNS setting using [www.dyndns.org?](www.dyndns.org?)

It's a feature some routers have and some don't. Not sure about the stock WTR54Gs (it wasn't in the stock firmware when I purchased the ones I have, but that was years ago). Certainly with firmware you can flash to it you can (I have WRT54Gs flashed with dd-wrt - there are also other options) and I do assign static IPs by MAC address as well. It's not done with DDNS.

---

### Post by hundred1906 on 2011-01-06
> **newlinux said:**
> It's a feature some routers have and some don't. Not sure about the stock WTR54Gs (it wasn't in the stock firmware when I purchased the ones I have, but that was years ago). Certainly with firmware you can flash to it you can (I have WRT54Gs flashed with dd-wrt - there are also other options) and I do assign static IPs by MAC address as well. It's not done with DDNS.

It is pretty easy to see how you have so many beans. I looked up dd-wrt and see I will need to reserve weekend time for checking out the instructions carefully then going through the procedure for flashing the firmware. Will let the thread know how it goes.

---

