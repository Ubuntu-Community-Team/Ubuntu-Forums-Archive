---
title: "Could not Connect to the Master Backend Server - Remote Frontend"
date: 2009-11-17
forum: Mythbuntu
---

### Post by zosoMythbuntu on 2009-11-17
I have installed Mythbuntu 9.10 on a new Backend/Frontend that is working fine so far.  I am trying to get another frontend only computer to connect to it.  When I went through the initial install I put in the backend's IP and password and the test connection succeeded.  Now when I try to open the frontend I get the message that it can't connect and it asks me if the backend is running and if the ip address is right.  The answer to both are "yes".

Also, I tried putting the ip address of the backend/frontend computer in it's settings where localhost usually goes and it could still connect just fine.  I am at a loss to why the backend/frontend can still connect that way but the frontend only pc cannot.

Please help.

---

### Post by zosoMythbuntu on 2009-11-17
Update - 

I tried running this statement GRANT ALL ON mythconverg.* to 'mythtv'@'192.168.1%'.  I found it here: [http://ubuntuforums.org/showthread.php?t=1265485&highlight=Could+-Connect+to+the+Master+Backend+Server](http://ubuntuforums.org/showthread.php?t=1265485&highlight=Could+-Connect+to+the+Master+Backend+Server)

That seemed to have made it worse.  Now I get a message that says that no upnp settings could be detected and it doesn't even get into the frontend GUI.  I get the same thing when I try putting the backend/frontend's IP where "localhost" usually goes on the backend/frontend machine.

I was hopeful that that would fix the problem.  I can't see how it made it worse.  I've been working on this all day and have made negative progress.  Any help would be greatly appreciated.

---

### Post by zosoMythbuntu on 2009-11-18
Update 2 -

I still don't have it working.  I found another SQL statement that has to do with permissions: grant all on mythconverg.* to 'mythtv'@'192.168.1%' identified  
by 'Fqei30MI';

After running this I got back to the original error message.  I don't know what to try next.  Please help.

---

### Post by klc5555 on 2009-11-18
Don't know if they've changed this since 9.04/0.21 ('cause I think I'm going to wait a _good_ long while before moving any of my machines to Mythtv 0.22). But traditionally the MySQL service has to be enabled on the master backend (in the services section of the Mythbuntu Control Center) in order for remote machines to connect to it, and in the backend setup itself, the PIN number has to be set to 0000

In addition to the things you've already reported doing.

---

### Post by zosoMythbuntu on 2009-11-18
> **klc5555 said:**
> Don't know if they've changed this since 9.04/0.21 ('cause I think I'm going to wait a _good_ long while before moving any of my machines to Mythtv 0.22). But traditionally the MySQL service has to be enabled on the master backend (in the services section of the Mythbuntu Control Center) in order for remote machines to connect to it, and in the backend setup itself, the PIN number has to be set to 0000

In addition to the things you've already reported doing.

Thank you so much for responding.  You were 100% correct with everything you said.

I made the problem way more complicated than it needed to be.  I had everything set correctly except the very first spot on the backend setup where you put the backend IP address.  After I changed that to the correct address, my frontend pc would crash after opening Mythtv Frontend.  This is probably because of all the complicated solutions I tried.  After doing a complete reinstall on the backend, my frontend pc now works correctly.

I can't believe I waisted so much time on something that could have been so easy, if I would have just read the description of the very first setup option. :redface:

Thanks again for responding to my post.

---

