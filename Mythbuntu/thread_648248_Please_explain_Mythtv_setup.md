---
title: "Please explain Mythtv setup"
date: 2007-12-23
forum: Mythbuntu
---

### Post by volkswagner on 2007-12-23
I hate to play the "what if" game.  I have had problems with a past install now I want to get this correct the first time for a re-install.

I have gone over these instructions many times yet I am still unclear how my specific setup relates ( one master backend/frontend, 1 slave backend/frontend, and one frontend). 

[http://www.mythtv.org/wiki/index.php/User_Manual:Detailed_configuration_Backend#Backend_Configuration]("http://www.mythtv.org/wiki/index.php/User_Manual:Detailed_configuration_Backend#Backend_Configuration")

The above instructions are unclear.  

For a master backend/frontend machine it seems I should put the actual lan ip address for the first entry since I will be running another frontend.  Is this correct I  put actual ip for

>  IP address for mythtv

For the same machine master backend running a frontend shall I use the actual ip address again for

> Master Server IP address

or is it better to have the loop back address here?

Now for the set up of a slave backend with a frontend also running what shall tthe two above entries be on this machine?

I have tried both actual ip and and local address and have run into "can't connect to backend."  Some were post install so maybe I did not edit some .conf file to get it all correct.  So I am hoping to get this accurate at install time.

Thanks in advance

---

### Post by volkswagner on 2007-12-24
Can anyone give a better description for the various setups?

Can anyone agree "always use 127.0.0.1 when frontend resides on same machine as the master backend", even if there will be other remote frontend and other slave backends?

Then use the actual ip (of master) for setup on remote machines????

What do you use with multiple machines on same lan?  Particularly if you have a master backend/frontend machine?

I am tired of the dreaded "cant connect to backend".. 
I am tired of booting into setup sreen.

Please any advice is appreciated.

---

### Post by newlinux on 2007-12-24
I always use the IP address of the backend, regardless of whether the frontend is remote or local. Make sure you mysql.txt use the same info (password and IP address) on all frontends. Also make sure you master backend is set to listen to more than localhost connections (make sure the following line is not present or commented out of your /etc/mysql/my.cnf file):

```
bind-address           = 127.0.0.1

```

So what is not working for you? Can you get your  frontend to connect to the master backend on the same machine? Is it just the remote frontends you can't get to connect?

---

### Post by volkswagner on 2007-12-24
Thanks for the reply.  I tried so many variations.

From what I can remember when I installed mythbuntu I entered the actual IP address.  When restarting the machine would complain cannot connect to backend.  I then changed to local address which seemed to work for a while.  I had made other changes to mysql passwords so these combinations of problems where difficult to detect what was causing the connection problems.  So I just wanted to be able to eliminate possible cause due to ip address.  I thought the backend should be able to be found with actual ip or local host, so I will verify the files you mentioned.

I want to do a clean install because I have made other changes, remote not working, vfd not working, etc., which have caused undesired results.  I need a clean slate.

Thanks again

---

### Post by LeAstrale on 2007-12-24
Hi

You might want to checkout the latest issue of FUll Circle Magazine, they have a full step by step tutorial 

[http://fullcirclemagazine.org/download-manager.php?id=51](http://fullcirclemagazine.org/download-manager.php?id=51)

/LeAstrale

---

### Post by newlinux on 2007-12-24
Does your master backend have a static IP?

---

### Post by volkswagner on 2007-12-24
Thanks for the link.

My backend does not have a static ip yet because it has yet to change from when  I first installed the OS.  I relocated the machine so it was on another router port but the linksys gave it the same address.  Most machines on my lan keep the same ip without me forcing the router to apply a specific ip to the mac address.

---

### Post by volkswagner on 2007-12-24
OK  new install, master backend/frontend, used actual ip for machine and server location, edited /etc/mysql/my.cnf and commented out bind 127.0.0.1 restart and still says cant connect to server.

In control center it still says mysql server = local host   what gives

what shall I change?

Why should I have to change anything when I performed a master backend/frontend install?  Shouldn't it just work?  Or shouldn't I be prompted to change somthing?

In mythtv setup general settings both addresses are set to actual ip of machine.  This can be confirmed since I ssh @ that ip address and it works.

where am I going wrong?

---

### Post by volkswagner on 2007-12-24
Why while in control center I can click on configure mythtv but all settings related to mysql are grayed out including test connection?

---

