---
title: "Please please help me vnc through ssh"
date: 2010-09-04
forum: Networking &amp; Wireless
---

### Post by JohnnyLongarms on 2010-09-04
I have read a bajillion tutorials and have gotten nowhere. 
This is my first Linux box, and it has been nothing but headaches. 
i'm pretty handy around computers, I took a Unix class, and I used Dos as a kid, but i'm just having so much trouble with this.

I just want to remotely control my Ubuntu box from my windows laptop over my home network. That's it. I cannot find one comprehensive step-by-step tutorial that will show me how to do this. Everything I find assumes I know at least something about linux, and I don't.

I have Putty, realvnc and tightvnc viewer installed on my laptop.
I have open-ssh and vx11 somethingorotherinstalled on the Ubuntu box. I have also allowed remote connections on Ubuntu from system>preferences.

I am getting very frustrated and would really appreciate someone giving me some help.

So far I HAVE been able to remotely control the box through one method. Through the GUI on ubuntu I went to:

System>Preferences>network connections 

and set the server to static IP, then I was able to use real VNC viewer from my windows machine to connect to the IP I set (192.168.0.11) but I couldn't get there through servername.local or whatever it said. The problem witht his solution is that the Ubuntu box then couldn't connect to the internet (which I need it to do.)

someone please please please direct me to the information I need for this simple task.

I just need to remotely control the desktop, the reason I wanted to use vnc through ssh so that I can leave the ubuntu box headless. Using just VNC I was having problems when the box was rebooted (had to log in before I could remotely control it... something about a security key ring?)

---

### Post by scorp123 on 2010-09-04
Read here:
[http://ubuntuforums.org/showpost.php?p=4527622&postcount=2](http://ubuntuforums.org/showpost.php?p=4527622&postcount=2)

VNC-over-SSH tunnel is explained here:
[http://ubuntuforums.org/showpost.php?p=9420091&postcount=6](http://ubuntuforums.org/showpost.php?p=9420091&postcount=6)


EDIT:

Maybe Teamviewer would be a possible solution for you as well? Read here:
[http://ubuntuforums.org/showpost.php?p=9750486&postcount=2](http://ubuntuforums.org/showpost.php?p=9750486&postcount=2)

I use it with my own systems, e.g. to remotely access my laptop in the office when at home, or vice versa. It has the advantage that it does not require you to fiddle with firewall ports and what not.


EDIT #2:

Teamviewer has a bookmark mechanism: they call it "Partner List". Basically all you have to do is to create a free account with their web site. You can then use that login in the Teamviewer client and then bookmark previously used connections. You can also set the client so it doesn't generate new user ID's and new numbers each time you login (... a slight bit of a security risk IMHO; but then again it should be obvious that you should never ever show or give those numbers to anyone ...). With the bookmarks in the "Partner List" you can easily reconnect to previously connected hosts whenever you need to. In my 'Partner List' I have added my own systems so I don't have to bother memorizing those numerical ID's and passwords ... I just click on one of my systems in the list .... and taaadaaaa ... I'm connected.

---

### Post by JohnnyLongarms on 2010-09-08
Thanks for the reply! Sorry it took me so long to get back, I've been really busy. 
 
Those first two links didn't really help me. It was a little confusing, and I am trying to access a Ubuntu box from my windows laptop.
 
Using [this tutorial]("http://codesnippets.joyent.com/posts/show/319") I was able to get my Ubuntu box to have a static IP, and I was still able to use VNC to connect to it. I think I was messing up the broadcast part before.. Who knows. 
 
Now hopefully I'll have some time in the next week to figure out how to use ssh, and samba.. then I'll be all set!
 
Forgot to check out Teamviewer.. maybe I will tonight! Thank you!

---

### Post by BkkBonanza on 2010-09-08
Since you have VNC working it is pretty easy now to get ssh going as well.

1. Make sure openssh-server is installed on the dekstop system. Check in Synaptic and if not installed then install it.

2. On your laptop you just need to run Putty with settings as a "tunnel". I did a quick google and found this page to tell you what settings to make.

[http://people.hmdc.harvard.edu/~mathpre/vnc/putty/](http://people.hmdc.harvard.edu/~mathpre/vnc/putty/)
(not fancy but has the basic info)

3. Now open VNC and tell it to connect to localhost:0 (NOT your desktop address like before).

How it works? Putty opens a ssh tunnel to your desktop. Then VNC sends data into the tunnel where it is encrypted and pops out the other end to VNC on the desktop.

When you finish VNC, also close Putty so the tunnel is closed.

---

### Post by JohnnyLongarms on 2010-09-08
Thanks for the info, I'll have to try it out when I get home.
The reason I wanted to use SSH is because I saw somewhere that using ssh will allow you to get onto the machien even if it's locked or sleeping.. or whatever linux does =P
As it stands I can't go headless with the desktop because sometimes I can't get into it because I need to enter my password (twice after reboot.) Something about a keyring? Hopefully this works for that..
 
Hopefully I can follow that guide. I don't know why I'm having so much trouble with everything linux. I swear I'm not *that* dumb!
 
So I have heard that using vnc through ssh is supposed to make my server secure. I don't really understand why that is. Can't someone still access my server just using vnc? (I do as of now)
 
Thanks for all the help y'all! Hopefully this will be resolved soon! :)

---

### Post by BkkBonanza on 2010-09-08
VNC over SSH is secure because SSH encrypts all data transferred thru it, and supports more secure key authentication over passwords.

SSH server can start on boot but I think VNC still doesn't start until login. Not sure about that though as I rarely use VNC, and never before login.

That guide I posted is for the Windows side so you should be more comfortable there.

---

### Post by JohnnyLongarms on 2010-09-08
Okay, so it just stops people from intercepting my connection during a vnc session.
 
I guess we'll find out the other part of the question tonight.. hopefully..

---

### Post by JohnnyLongarms on 2010-09-22
Okay, so today my linux box died or something.. so I started over (not that I had it working before.)

I installed Ubuntu, allowed for remote desktop viewing, set up a static IP.

I could vnc to the box by going to 192.168.0.11 
I figured out putty today, so I can ssh to the box
I can ssh to the box, then vnc to localhost, and it works.

Unplug my monitor,keyboard,mouse..

I can ssh to the box, and I get to the CLI, but I can't VNC. 

I just want a headless box.. isn't this what linux is for anyway!? =P

Sorry for bumping an old post.. it wouldn't be old but.. I have been very busy lately. Thanks so much for the help!

---

