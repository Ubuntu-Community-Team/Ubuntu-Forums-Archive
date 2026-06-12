---
title: "Problem with ADSL and pppoeconf"
date: 2006-07-11
forum: Networking &amp; Wireless
---

### Post by GnomicGhost on 2006-07-11
Hi all,
I can't get on the internet with Dapper. :(
I have tried with Kubuntu also, aswell as Ubuntu.  Neither of them work, and seem to have the same problem.

I run pppoeconf and go through all the steps.  It seems to be connected (from running 'plog').
But no webpages load, and I can't ping anything.

Dual boot with XP and XP runs internet fine.
Thank you for any help.
:)

As a side note, why did they change the DSL setup to this?  It worked fine before - now it apparently does not.  Many people appear to have the same or similar problems. ](*,)

---

### Post by GnomicGhost on 2006-07-12
/bump
Can anyone help at all please?

---

### Post by mips on 2006-07-13
What is the make and model of your adsl device ?

---

### Post by foots2015 on 2006-07-13
I got the DSL working, these are the steps I took:

**Note:** [I]You may not have to do steps 3 or 4. For step 4 your  MTU might be different.
[/I]
1. Reinstall Ubuntu 6.06

2.


> Originally Posted by manzuk View Post
Well, a friend of mine had a similar problem few months ago. Although we solved it, I don't remember exactly what we did but I'll try to help you.


Just as general information

There are two types of ADSL modems, Ethernet (those which use a cable like telephone's) and USB (which obviously connect through usb)

Ethernet ADSL modems are easier to config. Why? Because we JUST have to find a way to tell the ADSLmodem to establish an internet connection with the ISP. And that's where PPPoE gets into the action (but I'll explain later how)

In the other hand, some USB ADSL modems are not propertly detected when plugged in, and that's because the computer doesn't have the necessary drivers. So we have to find them, compile them, and install them. A real pain, but not the end of the world (I might write a HowTo...)


Your particular problem

If your modem is Ethernet (or if it's USB and you know your computer has detected it fine), then you need these packages:

pppoe & pppoeconf

Where to get them? There's quiet an useful page for this cases [http://packages.ubuntulinux.org](http://packages.ubuntulinux.org)
There you can search and download packages from the official repositories. So go there (under win) and get those packages! And install them under linux (double click, and Gdebi will do the rest)

Check again that your modem is connected to your PC (and if it's USB, remember the "link" or whatever is called led should be on)

Now run from a terminal
Code:

pppoeconf

and cross your fingers...

Lets say everything went fine. Now you have to edit /etc/ppp/peers/dsl-provider
Remember you need SuperUser rights, so you should run:
Code:

gksu gedit /etc/ppp/peers/dsl-provider


Where it says
Code:

#user [email]myusername@myprovider.net[/email]

replace "myusername@myprovider.net" with your actual user, and delete the "#" at the begining.

Now edit /etc/ppp/pap-secrets (here is where your password goes)
Again SuperUser rights needed, so
Code:

gksu gedit /etc/ppp/pap-secrets


At the end it says
Code:

# * password

replace "password" with your real pass, and I think you should delete the "#"

Let's try the connection!!!

From a terminal run:
Code:

pppd call dsl-provider

and go to [www.google.com](www.google.com)
Or if it doesn't work, you can try with
Code:

sudo pppd call dsl-provider


Final comments

I can't remember whether pppoeconf did the username and pass stuff for you or not, so I put it just in case.
I might be forgetting something...
Hope this helps you. (tell me later if it worked)

3. Disabled IPV6

4. Set MTU to 1452

And Viola the internet works

---

### Post by GnomicGhost on 2006-07-15
I write this from Dapper!! :)

My issue was a gateway issue.
I had to set my network manually.  From DHCP to static.
It is now:
192.168.0.115  <-- static IP address
255.255.255.0  <-- Mask
192.168.0.1    <-- Gateway address
I also disabled IPv6.


System -> Admin -> Networking | --> Ethernet Connection -> Properties (set as static)

Hope this helps someone else.

[Edit: I'm connected to a router too, which is connected to modem.  Not directly to ADSL modem]

---

