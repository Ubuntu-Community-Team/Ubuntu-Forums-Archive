---
title: "I am literally begging for some help"
date: 2010-08-12
forum: Networking &amp; Wireless
---

### Post by TheMiz on 2010-08-12
I really need some help with file sharing.

I just got a new MacBook.  I now have 2 MacBooks and I have a Ubuntu machine that I would like to access from my MacBooks.

I set up samba on the Ubuntu machine some time ago and I am able to access my samba shares from my old Macbook.  These shares do not automatically show up in the sidebar of the MacBook's finder, instead each time I connect I have to go to "Connect to Server" and type in "smb://192.168.0.102" (the IP of my Ubuntu machine).

So **Problem #1**: I would really like my samba shares to show up automatically in my MacBook's finder.  (I think I need to set up a samba.service file in avahi (which I have running), but I'm not sure how to do this)

So I got a new Macbook, and I have been trying to get it to connect to my Ubuntu samba shares just like my old MacBook.  For some reason, it is just not working at all.  I do the same exact thing on the new MacBook as I did on the old MacBook, but it will not connect.  Each time I go to "Connect to server" and type in "smb://192.168.0.102" I am asked to enter my name and password.  I use my Ubuntu login and password, but I get an "Invalid username or password" message (this doesn't happen on the old MacBook).  If I try to login as "Guest" I get a "Connection failed" message that tells me the server doesn't allow Guest access (I CAN login to my Ubuntu shares as guest with the old MacBook).

I have no problem using a terminal to connect to my ubuntu machine from my new MacBook.  My remote desktop program (Chicken of the VNC) works perfectly on the new MacBook.  I can even connect to the smb shares through my MacBook's terminal by using ```
smbclient //192.168.0.102/share
```  When I do that, it asks for a password, I enter one and then it tells me:
```
Domain=[MSHOME] OS=[Unix] Server=[Samba 3.4.7]
Server not using user level security and no password supplied.

```
Then I get an smb: \> prompt and I can see the files in my "share" folder.

Both MackBooks are running Mac OS 10.6.4, and I am running a Mythbuntu distribution of Ubuntu 10.04

So **Problem #2**: Why isn't my new MacBook able to connect to my samba shares like my old MacBook?  

I am literally begging for help.  I have searched everywhere I can think of before trying this forum.  I haven't tried Mac forums, because I seem to always get better advice here.  

Thanks!!!!!

---

