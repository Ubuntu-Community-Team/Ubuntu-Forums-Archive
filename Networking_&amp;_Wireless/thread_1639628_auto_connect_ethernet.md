---
title: "auto connect ethernet"
date: 2010-12-06
forum: Networking &amp; Wireless
---

### Post by nestawasright on 2010-12-06
My issue here is unique. There are times when I need to turn the router off while the computer is on. When I turn the router back on, with the computer still on, I want the machine to sense a connection and connect. This does not happen. I'd have to go to the computer, click about and get it connected. 

What I want is while the computer is on, turn off the router, turn the router back on and have internet connection on the computer without having to touch the machine. 

It's 9.10 on a laptop. Thanks a lot.

---

### Post by squenson on 2010-12-06
I suggest that you install the utility Wicd. Then you can launch the utility and scan the connections, then click 'Automatically connect to this network' in front of your connection name. It works for me!

---

### Post by nestawasright on 2010-12-07
> **squenson said:**
> I suggest that you install the utility Wicd. Then you can launch the utility and scan the connections, then click 'Automatically connect to this network' in front of your connection name. It works for me!

I don't doubt that WICD works, but does it work under the conditions I described for you. To turn off the router while the machine is on, and turn the router back on and have connection at the computer---without having to interact with the machine?

---

### Post by dandnsmith on 2010-12-07
As I understand it, Wicd is a utility for wifi connections, not for ethernet.

If the ethernet interface is still set up as 'auto eth0', then I would expect it to connect (with a possible delay) as soon as the router returns to service - this is the behaviour I get if I remove/insert the network cable (which comes to the same thing).

I think it still works with my home-brewed eth0 connection setup, but haven't tried it recently (as the connection point is not readily to hand at either end). I do believe, now I come to think of it that it always survives  a router reboot.

HTH

---

### Post by squenson on 2010-12-07
> I don't doubt that WICD works, but does it work under the conditions I described for you.
Yes, I often tweak my router parameters from my laptop (WiFi)or my desktop (ethernet) then the router reboots and I get connection automatically.

> As I understand it, Wicd is a utility for wifi connections, not for ethernet.
You are absolutely right, I should have noticed it in the post title.

---

### Post by grahammechanical on 2010-12-08
I have just tried an experiment.

I am connected by ethernet. I have just switched off the router. After a few seconds I received a disconnection message. I then switched the router back on but I did not get a ethernet connection to the router. This was because I did not have the connection set to Automatically Connect.

So, I edited the connection to Automatically Connect and then repeated the experiment. Guess what? It does automatically connect when the router re-establishes its connection to the ISP and starts polling for a connection to a computer. You do need to give the router time to establish a authenticated connection to the ISP before you can reload web pages.

Will this do what you want?

Regards.

---

### Post by nestawasright on 2010-12-27
> **grahammechanical said:**
> I have just tried an experiment.

I am connected by ethernet. I have just switched off the router. After a few seconds I received a disconnection message. I then switched the router back on but I did not get a ethernet connection to the router. This was because I did not have the connection set to Automatically Connect. .

Where do you set the connection to Automatically Connect? On network manager or WICD? 

>  So, I edited the connection to Automatically Connect and then repeated the experiment. Guess what? It does automatically connect when the router re-establishes its connection to the ISP and starts polling for a connection to a computer. You do need to give the router time to establish a authenticated connection to the ISP before you can reload web pages.

Where did you "edit the connection" and how did you do so? This is, yes, what I'm hoping to accomplish. 

Thanks

Will this do what you want?

Regards.[/QUOTE]

---

