---
title: "MythTV Player (Windows) can connect WITHOUT a password but mythfrontend cannot!"
date: 2008-09-18
forum: Mythbuntu
---

### Post by linuxvacuum on 2008-09-18
I tested [MythTv Player (it is like a reduced mythfrontend for Windows, http://www.sudu.dk/mythtvplayer/]("http://www.sudu.dk/mythtvplayer/")) and it can connect to a remote backend WITHOUT a password! 

How can I fix this?
I am puzzled because mythfrontend for Ubuntu cannot connect, but the Windows version isn't supposed to be able to connect but it does without a password. 
The frontend and server are on the same LAN.

---

### Post by funkydan2 on 2008-09-18
Great observation.  I've been using both a remote Linux frontend and mythtv player for some time and never realised this.

I think the password you set in remote frontends is the username/password for the MySQL database, not for the mythtv backend server.  Maybe the difference is that the full MythTV frontend system actually makes a connection to the database whereas the MythTV Player somehow just sends messages to the MythTV Backend server.

---

### Post by tgm4883 on 2008-09-18
Can you alter the backend contents or db contents in any way?  I'd venture that you are unable to do things like delete programs or schedule programs.

:EDIT:

In other words, I would guess that it is acting as a UPNP client

---

### Post by funkydan2 on 2008-09-18
Well you can delete recordings through the MythTV Player, but you can't schedule new recordings (I don't think the developer is too concerned about that due to the ease of doing that through MythWeb).

---

### Post by Eric Boring on 2008-09-19
I struggled with this for quite a while. I finally had to reset the mysql password. I think I followed this guide:
[http://www.mythtv.org/wiki/index.php/Category:MySQL](http://www.mythtv.org/wiki/index.php/Category:MySQL)

Shoot, you also need to comment out the bind address line in etc/mysql/my.cnf 

Finally, when the frontend is trying to connect, make sure that the port numbers are the same as your backend is using. For some reason one side chose 6543 and the other chose 3306. 

On the other hand,  you can use mythweb to schedule recordings and even to watch the streams if you use the vlc player for the streams (but only if you don't require a login and password for mythweb--don't so that unless you are happy with your network security).

By the way, I think the reason the windows player can connect but the frontend can't  is because the windows plater doesn't use mysql at all. Not sure how that works, but there you go.

Hope this helps.

---

### Post by tgm4883 on 2008-09-19
> **funkydan2 said:**
> Well you can delete recordings through the MythTV Player, but you can't schedule new recordings (I don't think the developer is too concerned about that due to the ease of doing that through MythWeb).

Can you delete recordings without using a password though?

---

### Post by Eric Boring on 2008-09-19
> **tgm4883 said:**
> Can you delete recordings without using a password though?

Yep.

---

### Post by linuxvacuum on 2008-09-20
Thanks for the info! I will definitely look that up. Yes recordings can be deleted...

When I connect to the PC I type the local IP. If I type the IP given by my ISP it doesn't connect. So at least my router is blocking Internet access to the server.

---

