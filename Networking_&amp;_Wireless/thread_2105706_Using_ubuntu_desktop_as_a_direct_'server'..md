---
title: "Using ubuntu desktop as a direct 'server'."
date: 2013-01-16
forum: Networking &amp; Wireless
---

### Post by Shmeves on 2013-01-16
Going to keep this short and sweet, as well as pretend that I've done nothing so far (I've tried a lot of stuff and nothing's worked like I wanted it to, or not at all).

I want to have my Ubuntu Desktop 12.10 run like a 'server', but not through my router, rather a direct connection to my laptop via a crossover cable.  Don't ask why, it's my only option at this point.  

Anyways, what I want to be able to do with this 'server' is three things (Well 2).  First, be able to Remotely access it with my laptop (obviously when I have it plugged into the crossover cable).
Second, host files on the desktop's HDD.  I don't need them to run on ubuntu, I just need to be able to access them with my laptop by either opening on the server or moving to the laptop for a short while.  Movie files mostly.
Third, run a private Minecraft server (bukkit if it makes a difference).  I am not using this for anyone but me.  


I don't care if I can't connect to the internet on the Ubuntu desktop, if I can access files on it I'd be able to transfer .deb packages if I had to in the future.  

Any help would be appreciated.  I don't know if all of these are possible at once even, if so let me know.  Thanks.

---

### Post by alexii on 2013-01-17
Your interesting set up does not really complicate the server that you want. Simple steps with many many good 'how to's around:

1) Give both machines an IP address in the same subnet on the interfaces that are cabled together. Confirm you can ping each from the other. At this point, it matters not wether the two computers are across the room or across the world.


2) Set up a samba share on the desktop and mount the share on your laptop. This is your best file sharing option. You will probably have to install the smbd package. Make sure you set up samba users in addition to the system users - again, tons of good tutorials.


3) Set up mine craft server...


Tell us where your are in this process and then more specific guidance can be given.

---

### Post by jonobr on 2013-01-17
Just a personal preference but I like controlling and moving of files using ssh and scp.

Installing openssh-server 
```
sudo apt-get install openssh-server
```
allows you to ssh in (or use putty from a windows client)
and administor your machine.
Its all CLI but, lightweight and secure.
When you become proficient at CLI , life becomes a lot easier.

When you want to copy files openssh-server allows for scp.

To copy files from linux ot linux ( eg copy all wmv files in the /home/user/files directory)
its as easy as
```
scp user@serverip:/home/user/files/*.wmv .
```
or to copy them up
```
scp . user@serverip:/home/user/files/*.wmv 
```

What , how and where you copy is dependent on  your cli proficiency.

I suggest all this not to deride using samba etc, but just using CLI is so much easier as when GUIs stop working, you get into,
is it permission problems? did the last update kill samba? is it not working for something I did... and so on

Also just to add. if your copying linux<->windows, you can use winscp

---

### Post by alexii on 2013-01-17
It's ridiculous to use crypto and to enter a password or do pub key auth each time to transfer files over a crossover cable.

You can mount and dismount samba just as quickly from the command line, and shares in /etc/ftab will always be mounted. I don't think an update has ever broken samba for me.

it's as easy as:
```
cp /remote/file /local/file
```

In windows, you can use windows explorer!

/cynicism.

Regardless, we don't know if Shmeves can even ping across a line yet...

---

### Post by jonobr on 2013-01-17
> It's ridiculous to use crypto and to enter a password or do pub key auth each time to transfer files over a crossover cable.

Wow, Someone got out on the wrong side of bed this morning ....

Shmeves

Apologies if it sounded like I was forcing you to use the scp and ssh, or that I was going turn you in to the openssh police for not using the aformentioned.

Just to reiterate what I said

> Just a**_ personal preference _**but I like controlling and moving of files using ssh and scp.


---

