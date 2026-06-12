---
title: "Wireless connected but no internet"
date: 2011-05-09
forum: Networking &amp; Wireless
---

### Post by Roastrain on 2011-05-09
Hey

I have a dell studio 1555 and i'm trying to access the net...
The problem is that I am able to connect to my router, but im not able to access the internet from firefox or synaptic or anything else..

A little working around in the wireless ipv4 setting got me to not display the 'server not found' but its loading forever...

Thanks in advance :)

---

### Post by matt_symes on 2011-05-09
Hi

Please post the output of these command from a terminal (copy and paste them into a terminal and copy and paste the results back).

```
sudo lshw -C network
```

Enter your password it will not be echoed to the screen. That is normal.

```
route -n
```

```
ping -c3 8.8.8.8
```

These will do for a start.

Kind regards

---

### Post by Roastrain on 2011-05-09
Ive got the results but the problem is that im accessing the net from a different computer, as i said the internet on the ubuntu machine isnt working...
 
But one thing, it is not able to ping 8.8.8.8
 
I think i can try to post pictures of the what the screen says:
 
[http://imageshack.us/photo/my-images/10/09052011688.jpg/](http://imageshack.us/photo/my-images/10/09052011688.jpg/)

---

### Post by matt_symes on 2011-05-09
Hi

The first command was

```
sudo lshw -C network
```and not 

```
sudo -C network
```That is why you got that error.

The results of the route command show that your PC can see your router as, unless you have set up a static route, DHCP is giving you a default gateway.

You can confirm this by typing

```
ping -c3 192.168.1.1
```I would expect you to get a response.

I would suggest you check all your cabling from your router to your network point. Change the cables if you can and ensure your ISP connection is up. Check the settings on your router as well.

What is your current topology ? What make and model of router are you using ?

Kind regards

---

### Post by Roastrain on 2011-05-09
Hi

It is getting very late where I live, i will put those commands and will revert back tomorrow

Thanks a ton

---

### Post by Roastrain on 2011-05-09
BTW
Im on a dual boot between win7 and ubuntu. the internet works on win7 and not on ubuntu.

my other laptop is being used by someone now, that is why i cant go back to ubuntu and try the commands and revert...

---

