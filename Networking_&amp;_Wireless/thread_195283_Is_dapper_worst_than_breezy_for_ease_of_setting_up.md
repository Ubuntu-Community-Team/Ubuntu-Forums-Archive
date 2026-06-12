---
title: "Is dapper worst than breezy for ease of setting up internet/networking?"
date: 2006-06-12
forum: Networking &amp; Wireless
---

### Post by zxee on 2006-06-12
I'm curious about the experiances others have had setting up connection to internet with dapper. I use dial up to connect and I've experianced much more problems with dapper than with breezy or hoary for that matter. I also have noticed what seems like a lot of reports of problems with ethernet in dapper. Specific to dial up there have been several posts here that define the problem but no response from the developers (there was a bug submitted) In the posts I've read, users that get dial up working generally have to use commandline tools to connect.  Note: if this poll isn't working perhaps someone can give me guidence-this is the 1st poll I've attempted.
[LIST=1]
[*]Yes, I've had more problems with internet and or networking in dapper.
[*]about the same for breezy and dapper.
[*]No, dapper is better for me than breezy was.
[*]I've had problems setting up internet/networking but I can't compare the two releases.
[*]I have no problems with internet/networking everything works fine.
[/LIST]

---

### Post by HeavyAl on 2006-06-12
I rarely use dialup except when I'm on biz trips but havent had any trouble with it when I did need it. Simply go into Network Settings, deactivate ethernet, activate the modem connection, set the vars and away we go.

As far as the ethernet part (my most oft used connection) I just plug it in and then unplug it to take it to work and drop it on my port replicator and boom, i'm done. 

Dapper is by far the easiest to get going. It even recognizes all the connected machines without me having to reconfigure anything (since I'm always connecting to other windows machine shares this is  agood thing imo).

Now, I have to say though that breezy wasnt much different. All I see is that the interfaces were polished a bit more.

One thing that I do have problems with is wireless - but thats not the fault of Ubuntu or any Linux distro actually since most of the drivers for the cards that are out there are proprietary and without releasing them to the community its difficult to figure out how to make them work 'out of the box' like the rest of the standard networking technology.

Just my 2c.

---

### Post by deadgobby on 2006-06-12
I do feel that this may be a bug issue. As long I have my Cable modem on before I boot up takes care of connecting to the internet. Or I will be not a happy camper and go back to Breezy version.
my soap box.
Gobby

---

### Post by zxee on 2006-06-16
I refrained from repyling to my own post long enough. I'd really like to see the sample size of the poll get a little higher, and I do use dapper a lot even though the interenet connection is less dependable than it was in breezy. My whole purpose is to bring a little attention to this problem in hopes that we can focus development mindpower on it. Thanks to those that voted and commented.

---

### Post by chuckman78 on 2006-06-21
I didn`t catch this poll untill today. I used to have Breazy installed in my box and I used (and keep using) a US Robotics external modem (conected to COM1) as my internet connection. I juste needed to use gnome-ppp and voila! the connection worked flawlessly. Dapper has been another story thought. I have tried gnome-ppp, wvdial (which is the base for gnome-ppp), pppconfig, modem appplet but no joy after all. The connection begins, the modem chirps, but right in the middle of the thing it drops the connection during transaction with the ISP side. I always get a "Carrier not detected)" (even when I specified no carrier detect in gnome-ppp) or "dialup time out". Then I go back to my XP partition and the modem works great as always. 

This problem is getting very irritating and frustating. I really would like to use Ubuntu but looks like Ubuntu doesn`t like me!  :)


Regards,

Carlos.

---

### Post by epohs on 2006-06-21
I had trouble getting my wireless cards recognized in breezy.  Had to install some linux-headers (i can't really remember, i had help with that) and a version of ndiswrapper from cvs..  I never would've figured that out on my own.

But, with Dapper installing ndiswrapper from synaptic and the windows drivers got that up fairly easilly, however I'm having a lot of trouble browsing my local network by computer name and I'm not finding any answers for that.  

So, I'd say they're about the same.

:D

---

### Post by FrancoNero on 2006-06-22
with breezy i just installed and it worked, with dapper, internet doesnt work once it's installed (it works during install)

---

