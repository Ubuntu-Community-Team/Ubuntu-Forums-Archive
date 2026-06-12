---
title: "xbox 360 not seeing samba, but windows pcs do"
date: 2009-09-23
forum: Networking &amp; Wireless
---

### Post by cicatrix1 on 2009-09-23
The title basically sums it up, but I'm trying to get my Xbox 360 to see my new fileserver.  Other Windows PCs on the network can see and access it just fine.

I found this link [http://viperxx.com/index.php/Xbox_360_Linux_Samba]("http://viperxx.com/index.php/Xbox_360_Linux_Samba") and followed those instructions, but I can't seem to get the 360 to see it when I go into video library like it sees the other Windows PCs after a short network scan.

I have security set to user, because I want a couple of people to be able to have private shares.  There are public shares that the other computers can get to that I'd like to work on the 360.  Is that just not going to work or am I missing something obvious?

I can post the config if needed, but I'd rather not if possible.  It basically looks like the second one on that link.

---

### Post by cicatrix1 on 2009-09-23
Anybody got their 360 to see their samba share?  Did you use share level security or have you got it to work with user?

---

### Post by steev182 on 2009-09-23
I think most people go the uShare or Fuppes route...

---

### Post by steev182 on 2009-09-23
Continuing from the previous reply, I decided to set it up here...

This is what you need to do:

Open a terminal and type ```
sudo apt-get install ushare
```
Press enter, then Y and press enter again.

You should now have uShare installed.

Now you need to look at the uShare configuration file and make it right for you.

In the terminal do ```
sudo dpkg-reconfigure ushare
```

Then you can specify the name of your server, the network interface it runs on and the folders to share. I used the following:

Name: Media
Network Interface: WLAN0
Folders: /home/steve/Videos,/home/steve/Music

It needs a comma between the folders, rather than a space, but once thats done, it should be plain sailing from then...

---

