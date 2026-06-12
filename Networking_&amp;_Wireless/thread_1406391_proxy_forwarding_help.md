---
title: "proxy forwarding help"
date: 2010-02-13
forum: Networking &amp; Wireless
---

### Post by Greens on 2010-02-13
I use an application called Proxoid to connect to the internet via my moto Droid using android adb forward.  Turns my cell into a little proxy server or something.

This works great on firefox and in synaptic package manager because they both have options to use a manual proxy.  i just put in localhost 8080

I have a few problems still though:

-How do i make the terminal use the proxy E.g. apt-gets don't work

**-How can i make something specific, EVE Online (mmorpg), connect to the proxy when it doesn't have a built in option, 
      or force all of my connections to go through that port.

I saw something that was explaining how to forward the terminal but i got lost because the only info i have is that its port 8080 i just start the app on my phone, choose the port, and sudo ./adb forward tcp:8080 tcp:8080
so idk im kind of lost beyond downloading files and surfing the web with it...

Also i seemed to have seen a screenshot of a windows application that does exactly what im talking about with a nice GUI, but i need a linux solution.

The game i want to connect to the proxy (EVE) is ran using WINE, if that is relevant.

---

### Post by iamgeniusrnti on 2010-03-19
> **Greens said:**
> I use an application called Proxoid to connect to the internet via my moto Droid using android adb forward. Turns my cell into a little proxy server or something.
 
This works great on firefox and in synaptic package manager because they both have options to use a manual proxy. i just put in localhost 8080
 
I have a few problems still though:
 
-How do i make the terminal use the proxy E.g. apt-gets don't work
 
**-How can i make something specific, EVE Online (mmorpg), connect to the proxy when it doesn't have a built in option, 
or force all of my connections to go through that port.
 
I saw something that was explaining how to forward the terminal but i got lost because the only info i have is that its port 8080 i just start the app on my phone, choose the port, and sudo ./adb forward tcp:8080 tcp:8080
so idk im kind of lost beyond downloading files and surfing the web with it...
 
Also i seemed to have seen a screenshot of a windows application that does exactly what im talking about with a nice GUI, but i need a linux solution.
 
The game i want to connect to the proxy (EVE) is ran using WINE, if that is relevant.
 
I have an SSH and a VNC server running on my Ubuntu box.  I then use my root'd Droid and establish an SSH pipe with forwarding so I can remote control my box using VNC viewer.
 
I am also wanting to frward 8080 but that is so I can get into my router from my phone.
 
I don't understand what you're trying to do.  
 
Typically, if you're using ADB, you are doing it in Ubuntu with the Droid connected to Ubuntu via USB.  ADB enables you to send commands into the Droid's Linux kernel thru your USB connection.
 
Are you trying to TETHER your phone and get internet into your box?  If so, you should be using AziLink on the Droid and OpenVPN... aw hell here: [http://www.humans-enabled.com/2009/12/how-to-tether-your-verizon-droid-as.html](http://www.humans-enabled.com/2009/12/how-to-tether-your-verizon-droid-as.html)
 
I hope this helps.......

---

