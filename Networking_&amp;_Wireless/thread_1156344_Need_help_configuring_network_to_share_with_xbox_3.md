---
title: "Need help configuring network to share with xbox 360"
date: 2009-05-11
forum: Networking &amp; Wireless
---

### Post by AgateElite on 2009-05-11
Hello.  First off I would like to state that I am a new user to Kubuntu so I'm trying to figure things out.  Alright here is my issue.  I have a internet connection coming in through wlan0.  I have my xbox 360 hooked up to eth0 and would like to share the connection coming from wlan0 with eth0.  Right now when the xbox is turned on it will still say the network is disconnected.  

I have firestarter, but when i activate the firewall it says that eth0 is not ready and fails to start the fire wall.  Any suggestions?  Also, I'm using the newest version of Kubuntu.

Thanks,
-=AgateElite=-

---

### Post by AgateElite on 2009-05-11
I hate to bump but...bump

---

### Post by draperdt on 2009-05-11
so I am guessing you have a router in that set up right?

---

### Post by AgateElite on 2009-05-12
Yes, I do have a router. When I run windows it works fine.  I know it works, I just dont know how to configure it on Kubuntu.

---

### Post by AgateElite on 2009-05-17
I know its a simple thing but I'm really not able to find a solution, google hasn't been a help.

---

### Post by bregale on 2009-05-17
just been reading a post in the tutorials and tips section that may help you.

---

### Post by Joeagain on 2009-05-17
Post number one of this thread worked for me:

[http://ubuntuforums.org/showthread.php?t=508145&highlight=xbox+360](http://ubuntuforums.org/showthread.php?t=508145&highlight=xbox+360)

```

http://ubuntuforums.org/showthread.php?t=508145&highlight=xbox+360

```

I didn't even have to go past the setting up of the DNS.  It worked right after that, took about 4 minutes total, (on 8.10).

Joe.


Edit:  Though I don't know if gedit is loaded on Kubuntu, perhaps it's kedit instead?  Any text editor will do though.

---

### Post by AgateElite on 2009-05-18
Unfortunately that one didn't work either.  I saw that a few days ago but it failed.  I have no idea why.  The xbox wont even get the IP.  Also I find it weird the wired network connection always says Not Connected even when it is clearly connected. 

Could the fact I'm using 9.04 have anything to do with this?

---

### Post by Joeagain on 2009-05-19
For some reason that I can't understand, the ip for eth0, (the ubuntu ethernet card, the one that connects to the xbox), will drop and I have to enter it manually, every time the xbox checks for an ip.  (See this post:)

[http://ubuntuforums.org/showthread.php?p=7297276#post7297276](http://ubuntuforums.org/showthread.php?p=7297276#post7297276)
```
http://ubuntuforums.org/showthread.php?p=7297276#post7297276
```

So I'd suggest checking whether that ip address is assigned by typing:

```
ifconfig
```

before you run the xboxLive connection test, and if you don't have an ip number there, try typing:

```

sudo ifconfig eth0 down 192.168.2.1
sudo ifconfig eth0 up

```

That is, of course, assuming that you are using 192.168.2.1.  Use whatever number you have decided on.

Just make sure you have that ip address in eth0 before you run the xbox live test, (even after a failed test -- mine always fails the first test upon powering on).  It's something of an annoyance to do every time, but once the xbox is running it's not necessary to do until the next time you power on.  If the xbox Live test fails, then check ifconfig again to see if that number is assigned, and then assign it and run the xbox Live test again.

Ubuntu version shouldn't matter at all.


Joe.

---

### Post by AgateElite on 2009-05-19
I finally got it to connect.  Thank you everyone for your help.   Now just to figure out how to open my NAT...ideas?

---

