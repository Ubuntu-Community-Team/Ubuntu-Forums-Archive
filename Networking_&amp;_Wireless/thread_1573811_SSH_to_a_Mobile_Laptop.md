---
title: "SSH to a Mobile Laptop"
date: 2010-09-13
forum: Networking &amp; Wireless
---

### Post by Wangsta on 2010-09-13
Hey I'm going off to college soon. I have two dual-booted Windows/Ubuntu machines--one desktop and one laptop--and both have SSH servers installed. At home, I use port-forwarding to connect to these servers externally.

I am interested however, in being able to connect to my laptop's ssh server no matter where it is. I am interested in this partly due to anti-theft precautions and partly just curiosity. I know there is anti theft software that lets you remotely modify your computer--from ANY IP address--and I want to know if you can do this with SSH. 
Imagine someone stole my laptop and connected to the internet in a random location. Assuming i somehow know this ip address, is there any way I could SSH to it? (I doubt the router would forward port 22 or whatever to this computer...)

Thanks guys! Just interested in your responses.

---

### Post by BkkBonanza on 2010-09-13
You could set up an account at DynDns. Then install ddclient on your laptop. It runs as a service and will update your DynDns dynamic IP whenever it changes on the laptop. This will work until the thief either stops the ddclient service or just wipes the drive. But you may be ablr to get an initial fix if the thief is silly enough to boot up connected to the net or via wifi. He/She would be a bit surprised if you walked into the cafe where he was trying out his new possession. The chances of locating the physical location quick enough are a bit remote.

Regarding the second part, about ssh'ing to the laptop. You can set this up regardless of router port forwarding but it requires a server somewhere that you can connect to. In addition to sshd running you would add a line to your start up, say in /etc/local.rc to start ssh with a "reverse tunnel". Like this,

ssh -fNR 22:localhost:22 user@server

The first port has to match the port sshd is listening on, the second one is the port# that it will listen on, on the remote server. What this does is forward a port in reverse, ie. it listens on the server and forwards back to the ssh on the laptop. 

So to connect to your notebook no matter where it is (regardless of dynamic IP even) you connect to the server and your connection gets forwarded into the laptop. As long as the laptop is up with a net connection you can get to it. 

But you may want to start ssh in a simple script that can detect failure and restart ssh because if the connect drops while the laptop is up it won't auto-reconnect. (unless maybe there is an option for that, I haven't checked). Or maybe better, make a proper init script that uses "respawn".

If your laptop has a webcam then you can login and run a command to capture the user's photo to file and get it. Someone was just asking about this a couple days ago. One command that works is,

ffmpeg -f video4linux2 -s vga -i /dev/video0 -vframes 3 /tmp/vid-%01d.jpg

And of course you can combine this in the init script to photo any user who starts the notebook and rsync the photos to your server.

---

### Post by BkkBonanza on 2010-09-13
After thought...
you may not want it to auto-ssh into your home server, or any important one. After all it will need a key/password and anyone getting the laptop will be able to use the access provided (if they got the know how). At a very minimum a special very restricted user account could be created.

A better idea would be an on-demand intermediary server that the laptop finds using DynDns. Hint: EC2.

---

### Post by Wangsta on 2010-09-13
Wow. 

Wow...

Bkkbonaza, thank you SO much! I thought I had been around the block, but man, this is totally new stuff! I'm really excited to try this stuff out (and probably fail at it.  ahahahahaa..)
Perrrrrrfect.
And your comment about the photo on startup? Genius! Hadn't thought of that before!

People like you make Ubuntu and the Ubuntu Forums awesome.


Oh, P.S. Would you happen to have a link to the thread about webcam photos on startup? Thanks!

---

### Post by BkkBonanza on 2010-09-13
Here's that thread,
[http://ubuntuforums.org/showthread.php?t=1509424](http://ubuntuforums.org/showthread.php?t=1509424)

My latest thoughts on this are that a pam script should upload captured images to some file hosting service and/or email them, or a link. This way once they're captured they get sent off to "somewhere" you can get to, along with some IP info. 

The reason being that once they boot up and try to login a couple times unsuccessfully they'll probably install Windows and be done with it. You want to catch as much ID/Location info as you can in the briefest opportunity before it's gone.

---

