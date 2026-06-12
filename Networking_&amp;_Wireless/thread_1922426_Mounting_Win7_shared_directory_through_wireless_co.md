---
title: "Mounting Win7 shared directory through wireless connection"
date: 2012-02-08
forum: Networking &amp; Wireless
---

### Post by Icculus on 2012-02-08
Hello ubuntu forums.

I am trying to mount a shared folder from my Win7 box. I would like to be able to connect to it through a terminal so I can run something like "find */*.avi | shuf -n 1" to give me a random video file. Perhaps pipe this into to totem or something down the line.

Anywho, I am running the command:

sudo smbmount //ipaddress/directory /mount/mountloaction -o ro,credentials=credentials.txt


Everything works great... until my laptop goes to sleep or something.  When I wake up my computer it asks for my wifi password (which should be saved).  Then when I try to fly to the directory it gives what I've seen called an uninterruptable loop.  Even if I go to /media/ and hit [tab] or try to ls in that directory, I have to close the terminal.

I was able to do this to get it back to normal:

mkdir /media/mountlocation2
sudo smbmount //ipaddress/directory /mount/mountloaction2 -o ro,credentials=credentials.txt
sudo umount -l /mount/mountlocation2
rmdir /media/mountlocation2

Now when I fly to /media/mountloaction everything works as expected.  Is there something that I can do to avert this issue? Any reason why this is happening?  Should I include any more info with this post?


I'm running 11.10 ;-)

EDIT: It also stops me from shutting down my computer: Stopping all running processes [failed]

---

