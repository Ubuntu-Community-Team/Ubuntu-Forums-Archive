---
title: "Possibly a rookie problem, but no internet connectivity with home WiFi network"
date: 2011-02-13
forum: Networking &amp; Wireless
---

### Post by abedayyad on 2011-02-13
Salutations, 

I've been using Kubuntu on/off for a couple of years, although I've only had it as my main OS for my home PC for a couple of months now. In other words, I am a complete novice. I have Kubuntu 8.10 (if I'm not mistaken). 

I noticed today that I have not been able to connect to my home network while using Kubuntu, but can do so perfectly well on the Windows partition on the same PC (in fact what I am using now). I get a DSL connection through a cable (connecting through the cable alone also does not work) and then use a D-Link 150 router to run the signal throughout the apartment. 

Basically, I am supposed to connect to the Wifi network using a WEP key I set up while I was using Kubuntu, and then provide further login information once my browser loads. 

I have been able to connect to the WiFi network, as KDE shows the signal strength as good with the heart for active (I have Arabised my KDE so I'm not sure what the English equivalent is ...but the point is the same: the network is shown to be active). 

Yet, there is absolutely nothing on my browser when I fire up either Firefox or Konqueror. I also followed the advice here: 

[http://www.kubuntu.org/doc/7.10/network/C/connect-wifi.html](http://www.kubuntu.org/doc/7.10/network/C/connect-wifi.html) 

and it pings perfectly well. 

I am now even more confused as I can get a pretty decent connection at a local cafe. In short: there is something very specifically wrong with my own home network and Kubuntu. 

Is this a hardware issue? Is there some kind of regular maintenance I need to perform on my Linux partition to clean up the history or something and then be able to use my network? I ask because it seems strange that I can not use some hardware which I used only 24 hours ago ...

---

### Post by grahammechanical on 2011-02-13
They say there are no stupid questions. That is true but there can be stupid answers. Here is one: are your web browsers in off-line mode? Here is another one: have your user permissions been altered to prevent you from accessing the Internet? These are just some things to check.

Regards.

---

### Post by abedayyad on 2011-02-13
> **grahammechanical said:**
> They say there are no stupid questions. That is true but there can be stupid answers. Here is one: are your web browsers in off-line mode? Here is another one: have your user permissions been altered to prevent you from accessing the Internet? These are just some things to check.

Regards.
Hey Graham, 

Thanks really for your help. 

My browsers are not in offline mode; I did check this at the first instance. 

I also doubt it is a permissions issue, as I have given my user profile administrative powers (don't need to use sudo ...). 

Any way, for both of the above, it doesn't explain why I'm able to connect to another network at the local coffee shop, or why I was able to connect only yesterday. 

Thanks again though.

---

### Post by Bucky Ball on 2011-02-13
> **abedayyad said:**
> 

... I have given my user profile administrative powers (don't need to use sudo ...

This is not a good idea. It means you are logging in basically as root and that can be dangerous. One slip can break your install badly. ;)

---

### Post by abedayyad on 2011-02-20
Hi Bucky Ball, thanks for that ... I did of course read up on it, but I have kind of foregone some safety attributes for ease of use, and also I was having trouble installing applications otherwise. I think the thing is to be always vigilant. 

As for my main problem: I have solved it, but I am still none the wiser as to what caused. It involved re-booting my router, and putting up a new network, and now it works, but, again, the reason remains a mystery. 

Thanks to anybody who helped ... or wanted to!!

---

### Post by Bucky Ball on 2011-02-20
For apps you could use a custom app launcher. Right click the top task bar, Add to Panel, choose 'Custom Application Launcher', click 'Add', then, for instance, you could use something like:
> 
gksudo kinoThat would launch the application Kino as root by clicking the custom launcher. ;)

Enjoy your OS! ;)

---

