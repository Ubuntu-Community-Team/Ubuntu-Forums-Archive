---
title: "Static ip on wired/wireless network on ubuntu 9.04"
date: 2009-09-16
forum: Networking &amp; Wireless
---

### Post by SpritBille on 2009-09-16
Hey All.

I'm looking for a way to make my ubuntu 9.04 to use a static ip adress for two reasons. 1. Torrents, 2. remote desktop. I need to do so on two seperate computers.

My quistion is how? I'm using a D-link 524 router, and i'm kind of lost.

Thanks a lot.

Kind regards
Bille

---

### Post by lvlint67 on 2009-09-16
I'm positive this has been posted before.

but to assign the ip through ubuntu

```

sudo nano /etc/network/interfaces

```you should see something like:
> 
auto eth0
iface eth0 inet dhcp
change that to something like:
> 
auto eth0
iface eth0 inet static
        address 192.168.1.100
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
save that.^^

Now.. it might help to statically set the dns servers (i never end up doing this but i'll throw it in in case you want to.

```

sudo nano /etc/resolv.conf

```On the line &#8216;name server xxx.xxx.xxx.xxx&#8217; replace the x with the IP of your name server. (You can do ifconfig /all to find out what they are)

Others also reccomend running: (i never do this either)
```

sudo apt-get remove dhcp-client

```now:
```

sudo /etc/init.d/networking restart

```and you should be good to go
---------------------------------------------------
If you want the router to statically assign the ip... you need to log into the router admin page and feed it the pc mac address...

I don't have specific instructions for this and have had mixed sucesses (it works well wih my zonet but my dynex refuses to assign statics based on mac addresses)

ps: source -http://www.howtogeek.com/howto/ubuntu/change-ubuntu-server-from-dhcp-to-a-static-ip-address/

---

### Post by SpritBille on 2009-09-16
Thanks. I've tried that now. I really don't know if i worked. I still can't connect to my ubuntu with RemoteDesktop, it keeps saying it can only be accessed on the local network. I have given ubuntu a static ip as you told me (i think, the only difference is that it said lo insted of eth0), assigned it a static ip on my router, and forwarded port 5900 to the computer....

I'm lost :(

---

### Post by lvlint67 on 2009-09-16
> **SpritBille said:**
> Thanks. I've tried that now. I really don't know if i worked. I still can't connect to my ubuntu with RemoteDesktop, it keeps saying it can only be accessed on the local network. I have given ubuntu a static ip as you told me (i think, the only difference is that it said lo insted of eth0), assigned it a static ip on my router, and forwarded port 5900 to the computer....

I'm lost :(

the lo is the 'local adapter' it's basically a loop back to the same computer.
leave lo alone in the settings. add settings for eth0 (i'm going to guess that that is the adapter name you want)

and now how are you trying to connect?

client->internet->router->server?
or are you just doing it on a local network.

Either way there is a configuration file somewhere that needs to be set to allow the proper network access to the service.

---

### Post by SpritBille on 2009-09-16
ahh.. I didn't say anything about the eth0, should I write:
"auto lo
 iface lo inet loopback
auto eth0
iface eth0 inet static
        address 192.168.1.100
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1"

I would like to be able to connect to my computer at home, from work and so on. My internet connection at home is connectet to a D-link 524 router (at home it is wireless, but I like to set it up at some other computers when i get it to work, and they are wired).

Thanks.

---

### Post by badger_fruit on 2009-09-16
> **SpritBille said:**
> Thanks. I've tried that now. I really don't know if i worked. I still can't connect to my ubuntu with RemoteDesktop, it keeps saying it can only be accessed on the local network. I have given ubuntu a static ip as you told me (i think, the only difference is that it said lo insted of eth0), assigned it a static ip on my router, and forwarded port 5900 to the computer....

I'm lost :(


VNC typically uses port number 5800 for VNC Viewer and 5900 for web-access (eg through IE or FF).  I suggest you try to port-forward 5800 as well as 5900 to the Ubuntu machine on your router.

---

### Post by SpritBille on 2009-09-16
okay. I have now done what you told me, but when I use the code:
sudo /etc/init.d/networking restart
It says:
*Reconfiguring network interfaces...
Ignoring unknown interface wlan0=wlan0.
SIOCADDRT: No such process
Failed to bring up eth0
[OK]

I might tell you asswell that im trying this of at my home network by using TightVNCViewer on a Windows 7 machine

---

### Post by SpritBille on 2009-09-16
But i forgot that I use a ZyXEL to connect to my internet host, but I i'm not to change anything there right?

---

### Post by badger_fruit on 2009-09-16
> **SpritBille said:**
> But i forgot that I use a ZyXEL to connect to my internet host, but I i'm not to change anything there right?

No, the connection "path" from a remote PC to yours at home would look something like this:-

Remote PC --> Your router (via internet)
Your router --> Local PC to remotely use

On the remote PC you connect to your public internet address
This can be found by browsing to [www.whatismyipaddress.com](www.whatismyipaddress.com) from a machine on your local network.

The router needs to know where to send requests, so configure it using your user-guide or online help here --> [http://portforward.com/](http://portforward.com/) so that it forwards VNC connections (port 5800 or 5900) to the local IP address of the PC you wish to remote-control.

I hope that helps :)

---

### Post by SpritBille on 2009-09-16
okay. But i have done that. But i think the error lies in my ZyZEL (the one connecting to the internet), becaus if i go to spritbille.dyndns.org it goes to my ZyZEL not my router d-link

---

### Post by SpritBille on 2009-09-16
ZyXEL of course

---

