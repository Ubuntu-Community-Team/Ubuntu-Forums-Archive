---
title: "frontend w/ remote backend problems"
date: 2010-05-03
forum: Mythbuntu
---

### Post by jrbless on 2010-05-03
I am running a combination frontend/backend server as my main Mythbuntu system.  I'm trying to add a frontend Mythbuntu system to put upstairs and am running into problems and could use some help.

I was able to get the remote frontend to connect to the backend database without a problem.  The problem I have is the frontend is always saying "unable to connect to the master backend server..." and it doesn't see any of the recordings, videos, or music files that I have.  What do I need to do to make it work correctly?

Other information:
My main frontend/backend is located at IP address 192.168.0.20.  For  now, the remote frontend is at 192.168.0.100.  After I get it working  correctly, it will be moved to a wireless network with an IP of  192.168.0.250.  The main system will remain behind a router (which has  an IP address of 192.168.0.1).  I'm currently trying to get it working  on the same network before changing to the wireless network.

Thanks in advance!
James

---

### Post by David Grigor on 2010-05-03
Are you sure you have the checkbox which I believe is in the system roles or mysql section of the mythbuntu control center set to "Allow remote frontends". 

Sometimes after applying fixes and patches, this will get uncheck and have to go check it again. 


Unless your using a newer wireless version, it may not be zippy enough to handle a frontend.  All of mine have to be hardwired for HD content.

---

### Post by jrbless on 2010-05-04
I figured out part of it.

On the main FE/BE system, the "MasterServerIP" needed to be set to 192.168.0.20.  The same address needed put in the mysql.txt file so it would connect there.  There was nothing else that needed done for "allowing remote frontends" (I also was unable to find a setting like that).

On the remote FE system, I went to the Mythbuntu Control Centre and found it was not quite configured correctly.  It was set as a secondary BE and a remote FE.  Once changed to FE only, it stopped complaining about the "unable to connect to the master backend server" error.

The recorded tv programs came over right away and worked w/o any other work.  After setting up fstab and mount points on the FE to point to the main FE/BE system, the videos and video covers came over and started working great.  Doing the same to the music folder, however, didn't cause it to start working.  After I work with it some more, I'll post an update.  At that point, it will be a remote FE system working on the same wired network as the main FE/BE system.  Then will come the fun of transitioning it to the wireless G network...

James

---

