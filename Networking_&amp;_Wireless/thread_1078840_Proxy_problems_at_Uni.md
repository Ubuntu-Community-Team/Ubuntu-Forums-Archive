---
title: "Proxy problems at Uni"
date: 2009-02-23
forum: Networking &amp; Wireless
---

### Post by Ampersand. on 2009-02-23
So i only just managed to finally get my wireless to work thanks to Pytheas22 and now i have another problem.

This time im having trouble connecting to the wireless at Uni. First of all they have a complicated Proxy system which took a while to make it allow Firefox to even access the internet.

The actual problem for me is that in order to connect and view other websites (than just the UWS home page) i have to enter my student account and password. The site then attempts to load and install a program called NetDirect (hopefully someone has heard of it) and about halfway through the normal setup routine it asks for my root password.
Now i assume this is my sudo password that i use in terminal or anywhere else but this doesnt work for NetDirect. It tells me that i have entered the incorrect root password and it shuts down leaving the browser open and me still logged in to the uni website.

Things i did:
-Changed the proxy settings using Network Proxy under systey>preferences (and made exceptions)
-Changed proxy settings in Firefox (3 i might add) under edit>preferences (and made exceptions)
-Created an exception that allowed the site to store cookies
-Called the help desk and they were unsure of why the root password wouldnt work. they suggested that maybe NetDirect wasnt configured for Linux. (the tech dude seemed to know a bit about Linux and asked what distro and whatnot so they arent useless)

Im really hoping this isnt the case because it would be really frustrating not to be able to use the wlan (and their huge bandwidth) while im at school.
Im wondering if my normal account isnt setup to be a root user, if this is the case how would i change it/find this out?
Anyway, thanks in advance

---

### Post by dmizer on 2009-02-23
I would suggest talking to the help desk guys again and learning more about this "netdirect" software. What is it, and why do you have to install it in order to use the internet? Is there an alternative that could be used in your situation?

For example, it may just be a pppoe dialer, preprogrammed with your schools settings. All you may need is to configure your pppoe dialer manually.

I would be extremely leery of being forced to install anything on my computer unless I knew what it was beforehand. ESPECIALLY if it requires root access.

---

### Post by Ampersand. on 2009-02-24
Im pretty sure it is some kind of VPN unless that sounds silly.
The java applet didnt initialise properly one time so i checked the details and it is made by Nortel Systems. I checked out their website but it is pretty useless from what i can see. 
I had used it on this computer when i was using vista and it didnt really seem to do much besides allow me to connect properly. Not sure if it is a checkpoint or a necessary program.
Ill call the guys tomorrow and see what work arounds they could think of, im not sure if they will let me do anything because they are pretty tight with their connection. Every time you go to a new website you have to retype your user name and password (however i see i can get around that using terminal proxy stuff)

thanks for a reply anyway

---

### Post by dmizer on 2009-02-24
> **Ampersand. said:**
> Im pretty sure it is some kind of VPN unless that sounds silly.
The java applet didnt initialise properly one time so i checked the details and it is made by Nortel Systems. I checked out their website but it is pretty useless from what i can see. 
I had used it on this computer when i was using vista and it didnt really seem to do much besides allow me to connect properly. Not sure if it is a checkpoint or a necessary program.
Ill call the guys tomorrow and see what work arounds they could think of, im not sure if they will let me do anything because they are pretty tight with their connection. Every time you go to a new website you have to retype your user name and password (however i see i can get around that using terminal proxy stuff)

thanks for a reply anyway
VPN would explain a few things. Windows doesn't handle VPN natively, but Linux does, so you don't really need that client you just need to know what kind of VPN network your connecting to and what settings you need to enter.

Figure out what the software is, and what it's purpose is and we can probably figure out a way to get you connected.

---

### Post by Ampersand. on 2009-02-25
Ok will do. I tried to talk to them today but they were busy every time i tried, some kind of update causing problems. Ill try again tomorrow.

While im waiting to talk to them:
Am i automatically the root user? 
Am i right in assuming that the root user is somewhat like the administrator in windows?
Should i check this before we do all the above and how?

---

### Post by dmizer on 2009-02-25
The security philosophy of Ubuntu is to not have a root account. This prevents programs like what you're trying to install from taking over the computer.

If you need a root prompt, it's easy enough to get one by typing:
```
sudo su
```

If all else fails, it is possible and fairly easy to enable the root account in Ubuntu but you're much much better off seeking alternative solutions.

---

### Post by Ampersand. on 2009-03-06
hey thanks for all the help. its been a busy week moving house and uni at the same time, not like i dont appreciate your help. :D
I havent had a chance to talk to them still, ill let them know about the native VPN support and ill find out about what the program actually does.

---

### Post by Ampersand. on 2009-04-06
they told me that i need to use tunnel guard (netdirect) or else i wont be able to connect.
i might be able to skip the vpn part of it but i still need it to install and work with my computer.

im thinking i will have to give up on getting it to work and chalk it up to not enough people supporting linux.

---

### Post by dmizer on 2009-04-06
Again, you can get a root prompt to install the software by entering the command:
```
sudo su
```

Was that not successful?

---

### Post by chrisbay90 on 2009-05-14
> **Ampersand. said:**
> 
...
about halfway through the normal setup routine it asks for my root password.
Now i assume this is my sudo password that i use in terminal or anywhere else but this doesnt work for NetDirect. It tells me that i have entered the incorrect root password and it shuts down leaving the browser open and me still logged in to the uni website.
...


I attend UWS, use Ubuntu and had the same problem.

It's not asking for your normal password its asking for the full root password. As dmizer said its a bit more access then you'd really want to give to it, i know.

Ubuntu doesnt give you root access by default (it assigns a random password), to get access to the root password you have to change it to something you will remember. You can do this in the terminal.
```
sudo passwd
```> **Ampersand. said:**
> 
Things i did:
-Changed proxy settings in Firefox (3 i might add) under edit>preferences (and made exceptions)

Just change the network settings (Firefox > Edit > Prefernces > Advanced > Network > Settings) to Auto-detect proxy settings for this network.

Thats all you should need to get it to work (Aside from java, although it appears you already have that.)

> **dmizer said:**
> The security philosophy of Ubuntu is to not have a root account. This prevents programs like what you're trying to install from taking over the computer.

If you need a root prompt, it's easy enough to get one by typing:
```
sudo su
```If all else fails, it is possible and fairly easy to enable the root account in Ubuntu but you're much much better off seeking alternative solutions.

dmizer. Your suggestion sounds much more appropriate then changing the root password and supplying this odd program (of which no one gives any explanation as to why we need it, what it does or why it needs root privilages).

However i tried the above (and it worked for me) weeks before reading this thread. Also i am new to linux and dont fully understand how i would use ```
sudo su
``` in the terminal to install a java applet that automatically (after java asks my permision to run it) pops up when you visit a website.

[B]Further info on netgaurd

[/B]I have no idea what netgaurd actually does to your computer but while running, clicking on details reveals the following.
> 
NetDirect: Parameters
* Tunnel IP = 172.21.128.176
* Primary DNS = 137.154.156.3
* Secondary DNS = 137.154.73.3
* Primary WINS = 0.0.0.0
* Secondary WINS = 0.0.0.0
* Netmask = 255.255.224.0
* UDP Port = 34835
* UDP SID = 393


Also in the fact sheet it asks Mac users to use the following .pac configuration file. (I would post a link but its on there internal server, so i downloaded and attached it with the extra extension .txt so the forum would accept it.)

---

### Post by dmizer on 2009-05-14
> **chrisbay90 said:**
> Also i am new to linux and dont fully understand how i would use ```
sudo su
``` in the terminal to install a java applet that automatically (after java asks my permision to run it) pops up when you visit a website.

Well, in Linux networking is traditionally handled by root. Since it seems that netguard needs to manipulate network configuration settings, it needs root access when installed.

In my opinion, this is a dangerous situation for Linux users as it's a potential inroad for a rootkit because Java applets are rarely "water tight".

---

### Post by johnny87au on 2011-08-19
Was just browsing the net and came across this thread, same thing happens to me when trying to acess the UWS site, i login with my uws credentials then netdirect pops open, i click ok to the root password then net direct closes, How did u get it working using ubuntu? Thanks

---

### Post by dmizer on 2011-08-21
> **johnny87au said:**
> Was just browsing the net and came across this thread, same thing happens to me when trying to acess the UWS site, i login with my uws credentials then netdirect pops open, i click ok to the root password then net direct closes, How did u get it working using ubuntu? Thanks

Since this thread is more than 2 years old, the OP has probably moved on. Your best bet is to start a new thread of your own.

---

