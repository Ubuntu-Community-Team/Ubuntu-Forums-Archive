---
title: "Switching on and off router's wifi through ethernet"
date: 2012-12-10
forum: Networking &amp; Wireless
---

### Post by FraGarriz on 2012-12-10
Hi everyone!

Is there a way to switch on and off router's wifi by sending a command from an ethernet connected computer?
What i would like to do is automatically switch off the wifi network at, say, 11 p.m. and switch it back on at 6 a.m. so that I could avoid all the radiation during the night (I'm lazy and I don't want to walk all the way to the router :wink: ).
I don't believe it is possible... However i'm waiting for your replies
Thanks.

---

### Post by haqking on 2012-12-10
> **FraGarriz said:**
> Hi everyone!

Is there a way to switch on and off router's wifi by sending a command from an ethernet connected computer?
What i would like to do is automatically switch off the wifi network at, say, 11 p.m. and switch it back on at 6 a.m. so that I could avoid all the radiation during the night (I'm lazy and I don't want to walk all the way to the router :wink: ).
I don't believe it is possible... However i'm waiting for your replies
Thanks.

Plug the router into a timer ;-)

unless you just mean the wireless facility, in which case i suspect it will depend very much on your router

---

### Post by FraGarriz on 2012-12-10
Yes, I still need the ethernet connection. Unfortunately my IPS is Fastweb (Italy) and its routers are sadly known to leave the user very little freedom with settings.
I deduce that there isn't a "magic universal command" that can do what I need... (Some sort of WOL dedicated to router's wifi).

---

### Post by dannyboy79 on 2012-12-10
you should be able to log into your router's config webserver and turn WIFI off right from the computer you're sitting at. I know my dlink DIR-655 has the ability to set when the internet is accessible via time frames but I don't believe that turns off the WIFI, it just limits when you can access the internet or not using it's firewall.

if you didn't want to have to log into the routers webserver config page every night to shut off wifi and then every morning to turn it back on, i would look into one of those timer plugs like haqking suggested. also, do you have a wireless phone at home? you better turn that off also, also, I would stop using you cell phone! LOL

---

### Post by haqking on 2012-12-10
> **FraGarriz said:**
> Yes, I still need the ethernet connection. Unfortunately my IPS is Fastweb (Italy) and its routers are sadly known to leave the user very little freedom with settings.
I deduce that there isn't a "magic universal command" that can do what I need... (Some sort of WOL dedicated to router's wifi).

oh right well cant you just login to the router and disable it then when you need to ?

other than that, I mean im sure you can telnet into it, and the wifi is just a wireless NIC on the router itself so can be disabled via command line once connected to it but then thats n different to logging into the GUI to disable it

Failing that then get yourself a tin-foil night cap ;-)

---

### Post by FraGarriz on 2012-12-10
I cannot use that timer plugs as i still need the internet connection. I just don't want the wifi network. Only ethernet. And no, i don't want to log into the webserber.
Do exist a terminal command such as "192.168.1.0 wifi off/on" or something like that? Just an automatic "switcher". Such a command is to be sent via ethernet.

---

### Post by FraGarriz on 2012-12-10
> **haqking said:**
> 
...
and the wifi is just a wireless NIC on the router itself so can be disabled via command line once connected to it but then thats n different to logging into the GUI to disable it.
...


Ehm, what is a NIC?

---

### Post by haqking on 2012-12-10
> **FraGarriz said:**
> I cannot use that timer plugs as i still need the internet connection. I just don't want the wifi network. Only ethernet. And no, i don't want to log into the webserber.
Do exist a terminal command such as "192.168.1.0 wifi off/on" or something like that? Just an automatic "switcher". Such a command is to be sent via ethernet.

why cant you log into it ?

either way to send a command would require authentication

---

### Post by FraGarriz on 2012-12-10
> **haqking said:**
> why cant you log into it ?

either way to send a command would require authentication

Unfortunately, Fastweb dosn't allow an actual webserver. Only them have the total control of the router via internet (and I hate this situation). I necessarily have to log into their website with a browser to change just a few settings (such as port forwarding and little more).

---

### Post by FraGarriz on 2012-12-10
Actually I forgot to mention this situation earlier...

---

### Post by lisati on 2012-12-10
The router I currently use has what amounts to a physica; on/off switch for its WiFi on its control panel that doesn't affect the wired connections.
> **FraGarriz said:**
> Ehm, what is a NIC?

**N**etwork **I**nterface **C**ard

---

### Post by dannyboy79 on 2012-12-10
if you can't log in to the GUI webserver to change much, then what makes you think you can just send it a command to turn off wifi? I seriously doubt its possible.

---

### Post by ZippyUbu on 2012-12-10
> Unfortunately, Fastweb dosn't allow an actual webserver. Only them have  the total control of the router via internet (and I hate this  situation). I necessarily have to log into their website with a browser  to change just a few settings (such as port forwarding and little more).     Most Routers that you buy now-a-days support a wide range of settings for different ISP's. You might find you can change the router as long as it supports whats required from Fastweb.

Speak with their help desk to see if they allow 3rd party Routers to be installed. If so, you could purchase another Router and maybe install [http://www.dd-wrt.com](http://www.dd-wrt.com) which allows wireless options that you're referring to; of course, you could research and purchase a Router with those options available which might be a better idea ;-)  

--
Zu

---

