---
title: "Remote Desktop in a Web-page."
date: 2011-10-10
forum: Networking &amp; Wireless
---

### Post by stewi1014 on 2011-10-10
Hello,
i have an apache HTTP server running on Ubuntu and a few other game servers and i have found that remote desktop is extremely useful for administrating it. but i was wondering if there was some way of making a web-page that you could type on a browser on any computer and you could then remotely control the desktop of the host computer (preferably with a password). i am using HTML for my web-pages.

---

### Post by haqking on 2011-10-10
> **stewi1014 said:**
> Hello,
i have an apache HTTP server running on Ubuntu and a few other game servers and i have found that remote desktop is extremely useful for administrating it. but i was wondering if there was some way of making a web-page that you could type on a browser on any computer and you could then remotely control the desktop of the host computer (preferably with a password). i am using HTML for my web-pages.

RDP is inherently insecure. you can web browser to it with  [http://myhost:5900](http://myhost:5900) where your myhost is your dns

use ssh or ssh -X if you need gui

you could also look at webex and teamviewer but stop using RDP ;-)

---

### Post by stewi1014 on 2011-10-10
hmmmm,
i am confused, i understand that screen sharing is a security threat.
i would just like to make a web-page on my website that will enable me to control the mouse and keyboard once i have typed in a password.
if i can get that to work then i wouldn't need to have RDP? :confused:

---

### Post by haqking on 2011-10-10
> **stewi1014 said:**
> hmmmm,
i am confused, i understand that screen sharing is a security threat.
i would just like to make a web-page on my website that will enable me to control the mouse and keyboard once i have typed in a password.
if i can get that to work then i wouldn't need to have RDP? :confused:

RDP is not the same as in Windows, in Linux it uses VNC [http://www.stuartellis.eu/articles/vnc-on-linux/](http://www.stuartellis.eu/articles/vnc-on-linux/)

and is insecure.

and you cant just connect to and control a desktop using HTTP.

---

### Post by stewi1014 on 2011-10-10
sigh...

---

### Post by haqking on 2011-10-10
> **stewi1014 said:**
> sigh...

There are plenty of solutions [http://www.mynitor.com/2010/02/07/15-remote-desktop-solutions-for-linux/](http://www.mynitor.com/2010/02/07/15-remote-desktop-solutions-for-linux/)

not all great

a server should not have a GUI running on it and ssh has always been and for good reason the preferred way to administer a server.

ssh- X if you need X

---

### Post by stewi1014 on 2011-10-10
oh well.
i have set up a ftp server that lets me manipulate files and i can just type vnc://stewi-******.******.***:5900 and control the server, so i think that that is good enugh to administrate it when i am not at my house. i just have to have my computer to do so. i did see a website that showed a live stream of a developers computer, anyone know how to do something like that?

---

### Post by Dangertux on 2011-10-11
> **stewi1014 said:**
> oh well.
i have set up a ftp server that lets me manipulate files and i can just type vnc://stewi-******.******.***:5900 and control the server, so i think that that is good enugh to administrate it when i am not at my house. i just have to have my computer to do so. i did see a website that showed a live stream of a developers computer, anyone know how to do something like that?

I can not emphasize enough how insecure your set up is. I'm not trying to be mean or pick on you but the way you are running right now will get you owned. It's not a matter of if, but when.

A VNC password is EXTREMELY easy to crack, we're talking less than 24 hours on a terrible connection with 5 year old hardware. 

If you absolutely need a Desktop Environment to administer your server I would recommend as haqking said using X forwarding over SSH. Which brings me around to the FTP bit, while FTP is not nearly as much of a security risk as VNC being openly exposed it is a security risk. I would recommend replacing it with SSH which would actually do two things for you.

Cut you down from 2 services to only one, this is good from a security perspective as you're only securing one application as opposed to two. 

Replace two relatively easily compromised applications with one not so easily compromised application, if you put the right measures in place, Public Key Authentication and denyhosts/fail2ban it is relatively difficult to compromise SSH and mostly passed over for easier targets, like poorly configured FTP servers and VNC service. 

Again I'm not trying to pick on you but as it stands now there is a very good chance you're already owned and just don't know it yet. Please reconsider.

Best of luck.

---

### Post by stewi1014 on 2011-10-11
ok, thanks.
ill set up ssh on the server and take down the vnc and ftp servers (if i can figure out how to use ssh).

---

### Post by Dangertux on 2011-10-11
> **stewi1014 said:**
> ok, thanks.
ill set up ssh on the server and take down the vnc and ftp servers (if i can figure out how to use ssh).

Great choice! :-)

If you need any help with SSH or anything like that make sure you post, there are many knowledgeable people who can help you. You may wish to make a seperate thread if necessary to get maximum support, although there have also been many of SSH X forwarding threads in the past so search them to see if that information is useful too :-)

Good luck

---

### Post by stewi1014 on 2011-10-11
I have set up ssh and it works brilliantly!
however when i connect to it with remote desktop viewer i just get the terminal. i think that is meant to happen, but i like controlling th GUI. however if that is just the way it is then i am still happy, i need to get better at terminal.

---

### Post by Dangertux on 2011-10-12
> **stewi1014 said:**
> I have set up ssh and it works brilliantly!
however when i connect to it with remote desktop viewer i just get the terminal. i think that is meant to happen, but i like controlling th GUI. however if that is just the way it is then i am still happy, i need to get better at terminal.

Well it's important to understand that X11 will forward one application at a time, so in your terminal for instance if you type 

```

$xclock &

```

You will see the X clock. Of course that's a little useless, so here is something more useful to get you started

```

$dbus-launch gedit &

```

or 

```

$dbus-launch nautilus &

```

So you get the idea, not quite the same as VNC, but definitely more secure.

Hope that helps oh and this one is just fun

```

$xeyes &

```

:-)

---

### Post by stewi1014 on 2011-10-12
thanks, i have unplugged everything except Ethernet cable and power supply from the server, so now i have to ssh into it to do anything on it at all because a different computer needed a display, mouse etc... . i think ill get used to ssh soon enough. also can windows connect to ssh or do u need a Linux box?

---

### Post by haqking on 2011-10-12
> **stewi1014 said:**
> thanks, i have unplugged everything except Ethernet cable and power supply from the server, so now i have to ssh into it to do anything on it at all because a different computer needed a display, mouse etc... . i think ill get used to ssh soon enough. also can windows connect to ssh or do u need a Linux box?

Yes you can ssh with Windows, PuTTY is the most popular ssh client for Windows

[http://www.putty.org/](http://www.putty.org/)

---

### Post by stewi1014 on 2011-10-16
> **Dangertux said:**
> Well it's important to understand that X11 will forward one application at a time, so in your terminal for instance if you type 

```

$xclock &

```You will see the X clock. Of course that's a little useless, so here is something more useful to get you started

```

$dbus-launch gedit &

```or 

```

$dbus-launch nautilus &

```So you get the idea, not quite the same as VNC, but definitely more secure.

Hope that helps oh and this one is just fun

```

$xeyes &

```:-)

when i type "$dbus-launch gedit &" in i get "No command -launch found"
and the same for nautilus, however the clock works!

---

