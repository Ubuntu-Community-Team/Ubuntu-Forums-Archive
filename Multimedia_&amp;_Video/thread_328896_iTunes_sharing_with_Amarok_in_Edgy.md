---
title: "iTunes sharing with Amarok in Edgy"
date: 2006-12-31
forum: Multimedia &amp; Video
---

### Post by valavanisalex on 2006-12-31
I am on a network in university accommodation.  In Windows XP, when I run iTunes, I am able to see (and play) every other shared iTunes folder on the network.  I have seen in various forums that Amarok should be able to play these streams but have had no luck so far.

I have added "Music Sharing" as a media device in Amarok.  When I click on the Media Devices tab, it shows that I am connected (the connect button is grey at least!), but I can't see anyone else's music listed :( 

I have installed all the avahi packages I could see, as I believe they are required :confused:.  I have no idea if (or how) I need to configure these to allow music sharing however.  I've spent a while searching these forums, but no one seems to have the same problem. ](*,) 

I'd be very grateful if someone could tell me if I need any other packages and how to configure and test my sharing... I think this is the last thing that is making me hold on to Windows, so it's quite important for me :)

---

### Post by valavanisalex on 2007-01-01
bump

---

### Post by thesmartace on 2007-01-01
I use Banshee and recently tried to set it up to access shared music from iTunes. I found this post helpful: [http://www.ubuntuforums.org/showthread.php?t=286929&highlight=daap](http://www.ubuntuforums.org/showthread.php?t=286929&highlight=daap)

Long story short, although I can now 'see' the shared playlist in Banshee, it won't actually play any music across it. It seems apple have changed how DAAP works in iTunes 7: [http://www.ubuntuforums.org/showthread.php?t=260672&highlight=itunes+daap](http://www.ubuntuforums.org/showthread.php?t=260672&highlight=itunes+daap)

---

### Post by valavanisalex on 2007-01-01
> **thesmartace said:**
> I use Banshee and recently tried to set it up to access shared music from iTunes. I found this post helpful: [http://www.ubuntuforums.org/showthread.php?t=286929&highlight=daap](http://www.ubuntuforums.org/showthread.php?t=286929&highlight=daap)

Long story short, although I can now 'see' the shared playlist in Banshee, it won't actually play any music across it. It seems apple have changed how DAAP works in iTunes 7: [http://www.ubuntuforums.org/showthread.php?t=260672&highlight=itunes+daap](http://www.ubuntuforums.org/showthread.php?t=260672&highlight=itunes+daap)

Thanks.  I've tried this and it seems to work the same.  When you say you can see the shared playlist in Banshee, do you mean that you can actually see all the names of the tracks too?  When I try it, I can only see the name of the share.  When I click on the share, I get an error dialog, and the following message at the command line:

Connecting to DAAP share: xxx.xxx.xxx.xxx:3689 (Sharename)
Error: [01/01/2007 23:00:11] (Cannot login to DAAP share) - Failed to login

(Note that I have hidden the IP address and share name above)

It does not show me the names of the tracks in the share.  Anyway, I'm very happy because this is the closest I've been so far!

---

### Post by Falcorian on 2007-01-01
iTunes 7 will not share with anything but iTunes 7. It will read others, but won't allow other clients to connect.

So that might be one problem.

---

