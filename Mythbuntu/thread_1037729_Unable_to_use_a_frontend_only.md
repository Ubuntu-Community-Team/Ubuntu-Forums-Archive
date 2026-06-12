---
title: "Unable to use a frontend only"
date: 2009-01-12
forum: Mythbuntu
---

### Post by Elv13 on 2009-01-12
Hi, I have installed mythbuntu 8.10 on one of my server, modified mysql to be usable over the network, filled my database and all those details. I tested a frontend on the server itself to see if it work, and it does. Now, I want frontend. I use the live-cd and when I enter the mysql informated, I see connection succefull and I can see file movie in my database from the remote frontend. But I can't play them, nor I can see my pictures or my music. So I think it is connected to the database correctly, but not the backend. How can I trully connect to the backend?

*In mythtv-setup (in the backend), I did set IP as 192.168.1.107 in both field and the security pin to 0000.

---

### Post by ReddogOne on 2009-01-12
For me...

Follow [this guys]("http://parker1.co.uk/mythtv_ubuntu.php") instructions and it'll work. 

Not sure why it won't work for other ways of installs, or how to modify them to work. 

You don't need to do all the database stuff as it just uses UPnP.

---

### Post by Elv13 on 2009-01-12
This guide dosen't really talk about client/server mythTV, and assume you are using Ubuntu and not Mythbuntu. I don't have the setup "allow remote connection to frontend" because I never had to actually install mythTV with APT. That was the only usefull information for me in this guide.

---

### Post by larsolav on 2009-01-12
You will have to mount the music, video, and picture folders on the backend to the frontend. Only recordings work on the frontend automagically without mounting.
Check out this link for mounting instructions: 
[http://ubuntuforums.org/showthread.php?t=973180]("http://ubuntuforums.org/showthread.php?t=973180")

I hope this is what you were looking for.

Good luck!

---

### Post by ReddogOne on 2009-01-29
> **Elv13 said:**
> This guide dosen't really talk about client/server mythTV, and assume you are using Ubuntu and not Mythbuntu. 

You are right as it does not talk about client server. But if you set up the 'backend' following the instructions. Any install on a client seems to work. (If memory serves, all you need to do is set the password on the backend).

---

