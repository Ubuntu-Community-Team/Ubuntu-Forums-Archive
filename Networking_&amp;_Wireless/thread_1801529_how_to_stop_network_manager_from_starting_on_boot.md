---
title: "how to stop network manager from starting on boot ???"
date: 2011-07-10
forum: Networking &amp; Wireless
---

### Post by josephmills on 2011-07-10
Hi there and thanks for taking the time to read this. YOU ROCK 


I would like to stop network manager from starting up on boot. I have tried moving ```
/etc/init.d/network-manager stop 
```

to rc.local and it did nothing but boot me into the CLI 

I have also tried to put ```
sudo service network-manager stop
``` and that did nothing also. 


Second question 



After I get network manager to stop on boot up. How do I make it so it will not auto connect to networks? My computer keeps on joining a different network on boot up. And I don't like this as some times I go to my banks website and I am on there network with out realizing it (because of the auto connect)  Is there a way to stop this also? 

thanks for you time and Ii look forward to hearing from you thanks again 
Joseph

---

### Post by nm_geo on 2011-07-10
Hey Joseph ..
All the wireless in my neighborhood are locked down tight.. LOL
Perhaps if you disable the auto connections in Network Manager that might solve the issue.
I experimented here with mine and now I have to click on the nm-applet icon to connect to my own network.  If you have others listed delete them or make them no-auto as well.
Don't know if this helps..

Another link
[http://askubuntu.com/questions/3677/disable-wireless-on-startup](http://askubuntu.com/questions/3677/disable-wireless-on-startup)

---

### Post by josephmills on 2011-07-10
thanks nm_geo! I am also looking into /etc/networl interfaces.conf right now going to run some test in vbox brb

---

### Post by josephmills on 2011-07-10
> **nm_geo said:**
> Hey Joseph ..
All the wireless in my neighborhood are locked down tight.. LOL
[/url]

I wish that mine where like that I even tried to talk to a couple of them and they still wont listen to me ohh well when there pi get stolen I will be there for them. with nice told you so. I mad it so It wont auto connect to there networks 

Now to make it stop you know like backtrack does. 

no wireless from the get go 

My girl-friend baby sits some of here friends kids and they use this computer for games and that is it.... I thought but I found a bunch of weird cookies and cache. so I dont want to have to remember a bunch of new pass words and I dont want to make an account for them. So I think that this is the way to go.

---

### Post by josephmills on 2011-07-11
I hate to do this but 8umP

---

### Post by Iowan on 2011-07-11
Have you tried disabling NM in System>Preferences>Startup Applications?
Also, there should be a checkbox for "Connect automatically" that can be unchecked.

---

### Post by jawilljr on 2011-07-11
To stop Network Manager from running on boot... just type these from the terminal:

```
sudo mv /etc/init/network-manager.conf /etc/init/network-manager.conf-disabled
sudo mv /etc/xdg/autostart/nm-applet.desktop /etc/xdg/autostart/nm-applet.desktop.disabled
```

To re-enable Network Manager on boot type these:

```
sudo mv /etc/init/network-manager.conf-disabled /etc/init/network-manager.conf
sudo mv /etc/xdg/autostart/nm-applet.desktop.disabled /etc/xdg/autostart/nm-applet.desktop
```

I got the instructions from [Here](http://www.ubuntugeek.com/connection-manager-connman-managing-internet-connections-in-linux.html#more-11286)

I know you do not want to install connman but disabling Network Manager is the same.

Jerry

---

