---
title: "Simple Guide To Home File Server Setup"
date: 2009-05-15
forum: Networking &amp; Wireless
---

### Post by roystreet on 2009-05-15
Hello - I am trying to use a machine I have as a simple file server, mostly for backing up files.  It doesn't need printer connectivity at all.  This is just for home use & most likely will only have 2 machines connected to it at once, so it's not a huge network.  
....I have a copy of ubuntu desktop & server.  I'm not sure which is best to install...I'm thinking I'd rather use the server edition since I will not be logging into this machine locally.

....Is there an easy guide out there somewhere that will help me walk through this stuff?  Both of the machines that connect to it will be windows machines.  Security is an issue of the future.  What I mean is, I would like to implement more security in the future, but it isn't a necessity for right now.  It will be wired to a wireless router so it is behind a routers 'protection' which requires a keyphrase.

Thanks ahead for any helpful tips, hints, or guidance on this.  There is a lot of info out there & it's hard to pick which one to follow.

~roystreet

---

### Post by roystreet on 2009-05-18
Well, I didn't get a response here so I went ahead with just installing the server version.  It works great.  Be sure to install webmin which enables you to log into the server & configure a lot of things via a webpage.  Hardly ever needing to actually connect a monitor & keyboard to the actual box.

Now I'm just have troubles limiting access to specific folders.  Right now all windows Vista machines can access shares that I have made.

;)roystreet

---

### Post by swerdna on 2009-05-18
> **roystreet said:**
> ................Now I'm just have troubles limiting access to specific folders.  Right now all windows Vista machines can access shares that I have made.............

You can use the valid users parameter. The Samba shares are defined/configured in the file smb.conf. There's a stansa for each shared resoource. If you want to limit  a share to users starshine and mikhael, put this line in hte stanza for that share:
```
valid users = starshine mikhael
``` There's more on the sorts of shares that you can make on this tutorial:
[HowTo Configure a Professional File Server on a SOHO LAN]("http://www.swerdna.net.au/linhowtosambaserver.html")
In particular see the section titled: [Part II: Defining and Using File Shares (Services)]("http://www.swerdna.net.au/linhowtosambaserver.html#shares")

Luck

---

### Post by Iowan on 2009-05-18
> **roystreet said:**
> There is a lot of info out there & it's hard to pick which one to follow. Stop by [https://help.ubuntu.com](https://help.ubuntu.com). They have helpful guides on several server (and other) topics.

---

### Post by roystreet on 2009-05-19
I appreciate both of you helping me.  I created a user named stan & added him to exactly all of the same groups as my administrators account.  I do not have my shares limited to specific users in this test, nor are they forced to be a certain user.  When I try to go in as stan, sometimes it acts like it's trying to log into the folder.  Then it asks for the username/password again.  I specifically put the servers name then the user name: USERVE/stan (USERVE being the username) 

It just kinda hangs for 5 seconds or so.  I don't know if this has anything to do with it, but my username also exists on the local windows machine as an administrator, but stan doesn't.

I made sure stan has all the same rights in the system except for cd rom & plugdev, no samba rights were specified.  Just as no samba rights were specified for my account.

Now once I start working with other users do I now need to specify their names as valid users?  Even though stan is also a part of the adm group?  

Any thoughts,
   ~roystreet

---

### Post by swerdna on 2009-05-19
> I try to go in as stan, sometimes it acts like it's trying to log into the folder. Then it asks for the username/password again.
Samba will accept users over the LAN only if they've been added to the samba user database on the Ubuntu machine. This command will tell you who (if any) are members of the Samba database:```
sudo pdbedit -L
```and this command will allow you to add users (like stan):```
sudo smbpasswd -a stan
```The same command allows you to change the password once stan exists in the database.

> Now once I start working with other users do I now need to specify their names as valid users?
Yes, you add each "valid" user first to the normal Linux users of the Ubuntu machine, then each of them to the Samba database. 

If there are any problems after that, please post here the contents of the file smb.conf so we can see the access rights configured by Samba for the share/s.

---

### Post by roystreet on 2009-05-20
Hi swerdna,
   What you said here has helped me a lot.

The code below didn't work on the machine & I'm not sure why? It stated something along the lines that it wasn't a known command?
```
sudo pdbedit -L
```

Now, this is what really helped me a lot
```
sudo smbpasswd -a stan
```

This code opened the doors wide you could say.  It allowed me to make users samba users.  Before everyone was basically a guest or I guess treated as an admin user.  Please remember, I don't totally understand it all right now, so I may not be saying this 100% correctly.  Anyway, once I did that it required a password to even see what's on the server.  I did several tests with different user names with limited access & it worked perfectly. I use webmin extensively & no where in there does it allow me to create samba users.  I can edit them or delete them.  So I logged onto the system using ssh & ran that command & now it works great.

Thanks! :D
  ~roystreet

---

### Post by swerdna on 2009-05-20
> **roystreet said:**
> Hi swerdna,
   What you said here has helped me a lot.

The code below didn't work on the machine & I'm not sure why? It stated something along the lines that it wasn't a known command?
```
sudo pdbedit -L
```

Now, this is what really helped me a lot
```
sudo smbpasswd -a stan
```

This code opened the doors wide you could say.  It allowed me to make users samba users.  Before everyone was basically a guest or I guess treated as an admin user.  Please remember, I don't totally understand it all right now, so I may not be saying this 100% correctly.  Anyway, once I did that it required a password to even see what's on the server.  I did several tests with different user names with limited access & it worked perfectly. I use webmin extensively & no where in there does it allow me to create samba users.  I can edit them or delete them.  So I logged onto the system using ssh & ran that command & now it works great.

Thanks! :D
  ~roystreet
Glad its working for you [IMG]http://www.swerdna.net.au/forumpics/smiley/beer.gif[/IMG] 

Regarding pdbedit: a puzzle. Maybe a typo. Upper case L? Try 'man pdbedit' to see if it's installed. But that's not majorly important at this point in time.

---

