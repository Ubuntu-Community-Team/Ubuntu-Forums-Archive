---
title: "webcam-server / dyndns etc."
date: 2009-04-13
forum: Networking &amp; Wireless
---

### Post by weirdbeardmt on 2009-04-13
Hi

I'm running Ubuntu 8.10, with Apache2, java6 and webcam-server.

Everything is set up for internal viewing - using the included applet, apache2 is listening on 81 so, if I go to 192.168.1.5:81/webcam/webcam.html on any of my computers on the local network then it works fine - webcam-server is still running on 192.168.1.5:8888 so I tweaked the url parameter to point to that address.

That's all fine. The problem I've got is external viewing... my router (Netgear 834) is set up to use Dynamic Dns and port forwarding, so, if i go to my hostname on port 81, then, yes - I see the default "It works" Apache2 screen - no worries at all. 

BUT (you guessed it) [http://myhostname.dyndns.org:81/webcam/webcam.html](http://myhostname.dyndns.org:81/webcam/webcam.html) - I just see the black "connecting, please wait" screen - i.e., for some reason, it won't forward the video through... or something.

Any ideas what I need to tweak to get this to work? Sorry if this is a n00b question... I only installed ubuntu and started doing this today...

:)

---

### Post by antikristian on 2009-04-13
While connected to the the box on your local network, run a netstat -n | grep ESTABLISHED and see what other ports you are communicating with it on. Then you might want to add those to the nat, or better still, set up a vpn connection to the network from the outside if you want better security.

---

### Post by weirdbeardmt on 2009-04-20
I got this working, although I'd be interested to hear about any security implications.

Basically, the webcam-server was running on 8888, so I opened up that port on my router which allows you to see a static image.

I then pointed the webcam.html file to the dyndns address on 8888 and it works.

Thoughts on this setup?

---

### Post by antikristian on 2009-04-21
If this is a service that only you are supposed to use, than a ssh tunnel would be a whole lot more secure. Than you would only open port 22 on the router (or even better, set up ssh to use a non standard port like 2244) and tunnel everything through the ssh tunnel which is encrypted.

Then you would do a 
```
ssh -L 8888:127.0.0.1:8888 username@mydomain.dyndns.org -p 2244

``` (the -p 2244 only applies if you changed the default port on ssh)
Point a webbrowser to 127.0.0.1.8888 to get to the webcam server

If you go this route, be sure to change some of the standard options in /etc/ssh/sshd_config to harden the security, and use a strong password

---

### Post by weirdbeardmt on 2009-04-21
Hi AK

Many thanks for your reply and your code/hitns. That's certainly a nice looking thing. I'm still getting up to speed on the likes of ssh etc so will give that a play at some point.

As for your original question - actually, this wouldn't just be for my use, obviously I'd like to be able to let certain people see the webcam if I tell them about it, without having to set up ssh tunnels and such like.

Obviously the first thing I need to do is put some directory security on the web folders.

Is there anything else I should do?

---

### Post by antikristian on 2009-04-23
Well, hosting web pages really isn't my table, but if this setup is a php service of some kind with a configuration page meant for initial setup, than many of those services recommend removing some of those pages to prevent people hijacking your site. 

You should look into the recommendations for your software.

There might be a forum or a webpage for the specific webcam server you are using that could give you an answer:)

---

### Post by weirdbeardmt on 2009-05-12
> **antikristian said:**
> If this is a service that only you are supposed to use, than a ssh tunnel would be a whole lot more secure. Than you would only open port 22 on the router (or even better, set up ssh to use a non standard port like 2244) and tunnel everything through the ssh tunnel which is encrypted.

Then you would do a 
```
ssh -L 8888:127.0.0.1:8888 username@mydomain.dyndns.org -p 2244

``` (the -p 2244 only applies if you changed the default port on ssh)
Point a webbrowser to 127.0.0.1.8888 to get to the webcam server

If you go this route, be sure to change some of the standard options in /etc/ssh/sshd_config to harden the security, and use a strong password

How do you go this route but using a public webbrowser? Also bear in mind that I guess some firewalls may block outgoing traffic on non-standard ports (that's why getting it running on 80 would be great.)

---

### Post by antikristian on 2009-05-13
If you want access from a public webserver, it would probably be best to just opun the ports. A vpn or an ssh tunnel is probably best if you only want to be able to connect from your private computer.

---

