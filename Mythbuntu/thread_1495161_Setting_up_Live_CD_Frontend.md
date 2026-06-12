---
title: "Setting up Live CD Frontend"
date: 2010-05-27
forum: Mythbuntu
---

### Post by sinkyboy2000 on 2010-05-27
Probably more through luck than judgment, I have managed to get Mythtv frontend and backend set up on my atom-based net-top.  I'm pretty new to linux, but I've picked up some bits and pieces.

My next project is to get a second frontend running on my netbook.  I've created a usb pendrive live "cd".  This boots fine and connects to my network.  I open the live session configuration and am asked for the following:-

MySQL MythTV User:
MySQL MythTV Password: 
MySQL MythTV Database:
MySQL MythTV Server:

A google search suggested I could get these from the mysql.txt file. I have inserted these (I assume the last one is "DBHostName"), but the test says "Failure".  I can ping the backend machine from the frontend and mythweb works perfectly well.

Can't work out what to do next.

---

### Post by sinkyboy2000 on 2010-05-28
Thought I had success and then my hopes were dashed!:(

I followed this link:-
[http://www.hackourlives.com/setting-up-multiple-remote-frontend-for-an-existing-mythtv-backend/](http://www.hackourlives.com/setting-up-multiple-remote-frontend-for-an-existing-mythtv-backend/)

Which showed me how to set up my backend.  Followed all the instructions and I eventually got a successful test in the frontend.  However, when I start  up the frontend I get the "select language scree" and then the screen has that graphite background used in mythtv. It stays like that for a bit then seems to crash.

Any ideas?

I'm on Mythbuntu 9.10 btw

---

### Post by sinkyboy2000 on 2010-05-30
In case anyone's interested - I solved the problem.  My frontend and backend had different timezone settings.

---

