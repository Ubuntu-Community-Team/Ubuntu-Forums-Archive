---
title: "Using global proxy"
date: 2011-03-29
forum: Networking &amp; Wireless
---

### Post by shanehm2 on 2011-03-29
Hey there all very first time linux user.

I am trying to get my user name setup properly for linux so i can use it fully throughout linux fully but I can't workout how.

It uses a http:// proxy then I have to authenticate with a username and password. The proxy allows autosave.

So is there a way that it can be done ???

---

### Post by Do_Japan on 2011-03-29
Well, if you are a first time user then you probably shouldn't be using a proxy server.  I'm still not sure what that has to do with your user name being:P fully throughout linux fully.

---

### Post by shanehm2 on 2011-03-29
> **Do_Japan said:**
> Well, if you are a first time user then you probably shouldn't be using a proxy server. I'm still not sure what that has to do with your user name being:P fully throughout linux fully.
 In other words I need to know how to add the connection settings, so I can install packages etc.
 
So I need to know what file I need to edit so I can have internet connectivity using my user name.

---

### Post by Do_Japan on 2011-03-29
You can download packages using the Ubuntu Softare Center under the Applications menu.  Create an internet connection under System > Preferences > Network Connections.  What type of username are you trying to connect with?

---

### Post by shanehm2 on 2011-03-29
> **Do_Japan said:**
> You can download packages using the Ubuntu Softare Center under the Applications menu. Create an internet connection under System > Preferences > Network Connections. What type of username are you trying to connect with?
 My internet connection is based on a proxy.
 
The default settings is:
```

[http://proxy.det.nsw.edu.au:8080](http://proxy.det.nsw.edu.au:8080)
user: xxxxx.xxxxx.xxxxx
pass:xxxxxx

```
 
So there is an active connection at all times but it is a authenticated one and comes in on the eth0 lan connection and I want it configured so any time I launch a program that requires internet connectivity it looks at the http proxy and authenticates.

---

### Post by Do_Japan on 2011-03-29
Goto System > Preferences > Network Proxy, select Manual Proxy Config and Details.  Is that what you are looking for?

---

### Post by shanehm2 on 2011-03-31
> **Do_Japan said:**
> Goto System > Preferences > Network Proxy, select Manual Proxy Config and Details.  Is that what you are looking for?
Yep I can find that in Ubuntu, but I am trying to find it for Xubuntu. :)

---

### Post by patryk77 on 2011-03-31
Hey!

In my /etc/ I have the following:

```
./apt/apt.conf:Acquire::http::proxy "http://localhost:2012/";
./apt/apt.conf:Acquire::https::proxy "https://localhost:2012/";
```

(My proxies are tunneled by SSH)

I guess you would need something similar; read the man page for more info as my entries were generated from Network Manager:
man apt.conf

I think just replacing [http://localhost:2012](http://localhost:2012) with ```
http://user:password@proxy:8080
``` might do the trick, but I have no idea where else you would have to change it.

I know that Chrome opens the Gnome Proxy Settings window under Gnome (regular ubuntu), but I have no idea if XFCE has an equivalent, but it might be worth trying.

---

### Post by shanehm2 on 2011-03-31
> **patryk77 said:**
> Hey!

In my /etc/ I have the following:

```
./apt/apt.conf:Acquire::http::proxy "http://localhost:2012/";
./apt/apt.conf:Acquire::https::proxy "https://localhost:2012/";
```(My proxies are tunneled by SSH)

I guess you would need something similar; read the man page for more info as my entries were generated from Network Manager:
man apt.conf

I think just replacing [http://localhost:2012](http://localhost:2012) with ```
http://user:password@proxy:8080
``` might do the trick, but I have no idea where else you would have to change it.

I know that Chrome opens the Gnome Proxy Settings window under Gnome (regular ubuntu), but I have no idea if XFCE has an equivalent, but it might be worth trying.
thanks I will try having a look at that today :)

---

