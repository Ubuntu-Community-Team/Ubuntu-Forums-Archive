---
title: "IP Change: Master Backend unavailable"
date: 2009-06-17
forum: Mythbuntu
---

### Post by gamerteck on 2009-06-17
Hi Everyone,

Ever since I changed my IP address i'm getting the error below.

[B]> Could not connect to the master backend server -- is it running.
Is the IP address set for it in the setup program correct?[/B]

I have one machine that is the master/frontend.

I changed the IP in myth-setup but I can't figure out where else it has to be changed.
Thanks for the help.

---

### Post by AboveTheLogic on 2009-06-17
the IP in myth-setup needs to match the IP that shows up when you run "ifconfig"

if the ifconfig IP differs, you can change it and the other IP settings by editing the following files:

/etc/network/interfaces
/etc/resolv.conf

---

### Post by gamerteck on 2009-06-17
Yes. I have changed it in both places bu the issue persists :(

---

### Post by ian dobson on 2009-06-17
Hi,

Have a look in mysql.txt, the IP/hostname of the backend SQL server is also in there.

Regards
Ian Dobson

---

### Post by gamerteck on 2009-06-17
Sweet...
Thanks AboveTheLogic and Ian.

When I checked my mysql.txt I realized that, in my haste, I had set the local backend to my new IP instead of keeping it set to localhost. 

Thanks again!

---

### Post by gamerteck on 2009-06-17
Just an update, in case someone searches on this.

I think the true cause was that my .dB got corrupted, coincidence, I can't say but all my recording schedules got wiped when I accessed Mythweb. Thankfully, I had backups running which I created from the wiki here - [**MythTV Backup**]("http://www.mythtv.org/wiki/User_Manual:Periodic_Maintenance").
After the restore I couldn't connect to the .dB again, so I went into myth-setup and low and behold both IP address for local and master backend where set to my old IP address; the mysql.txt had localhost. When I changed the IP to my new one, just in myth-setup, I was back up and running.

Hooray for backups \\:D/

---

