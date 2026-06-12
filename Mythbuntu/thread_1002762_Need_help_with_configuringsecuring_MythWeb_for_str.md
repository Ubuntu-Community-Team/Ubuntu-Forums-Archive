---
title: "Need help with configuring/securing MythWeb for streaming"
date: 2008-12-05
forum: Mythbuntu
---

### Post by bmwman on 2008-12-05
I have my Backend "fully" working. Mythweb is working within my home network, i have the symlinks done and I can see all my Movies, Music, etc. I also have SSH set up and I can connect to my home PC from work and use VNC to see my desktop. I think I followed the Wiki how to set up MythWeb authentication and it asks for login when i do it at home. The problem is it seems like it works as a plain HTTP and not HTTPS. 

Q1: How to make MythWeb more secure so it uses HTTPS or make everything go trough the SSH tunnel.
Q2: How do I set it up so I can stream and watch my movies from work or anywhere. I have FIOS internet so my bandwidht is really good.

Thanks

---

### Post by bmwman on 2008-12-05
Can anyone point me to a good How-To for starters?? I've seen stuff about streaming recordings but nothing about streaming the movies. Also what is the best wat to secure the MythWeb?

---

### Post by toorima on 2008-12-05
guide to setup ssl [http://bubble.gritto.net/db/query.php?id=51&ty=HOWTO](http://bubble.gritto.net/db/query.php?id=51&ty=HOWTO)

If you want to use SSH to tunnel traffic from work it comes down to what you use at work, if its a windows machine, just look at tunneling (i think its called) in the setup/config window. If you use linux at work, just use the -L flag with SSH

edit: there is some info in this thread [http://ubuntuforums.org/showthread.php?t=4466&highlight=a2enmod&page=2](http://ubuntuforums.org/showthread.php?t=4466&highlight=a2enmod&page=2) as well, such as info on how to change how long the ssl cert is valid.

Hope its any help.

---

### Post by bmwman on 2008-12-05
Great. I followed the guide and I was able to set it to use HTTPS. I think it still works with HTTP though. How do I make it to work only with HTTPS??

I'm going to read over the second link you gave me for more details.

Thank you.

---

### Post by toorima on 2008-12-05
well there are several ways of disabling http, don't forward port 80 on the router is quick and simple if you only run mythweb on apache. Another way of doing it would be to comment out the two lines with port 80 in /etc/apache2/ports.conf
A third way would be to have only 443 stuff in your /etc/apache2/sites-available/default
I'm sure there are other ways of doing it too, and if others then you use it, then maybe keep port 80 open and have a redirect to port 443 in case they forget to write https

---

### Post by bmwman on 2008-12-05
Got it all working. It only uses 443 and hhtps. Step 1 completed :D

Now need to set up the streaming part :)

Thank you for your help again.

---

### Post by bmwman on 2008-12-08
Any help with setting up streaming is greatly apreciated. I followed the guide in MythTv.org and i was able to set up the HTACCESS file to ask for password when when I try to stream mp3 for example and my Media Player is asking for password again and nothing works.

---

