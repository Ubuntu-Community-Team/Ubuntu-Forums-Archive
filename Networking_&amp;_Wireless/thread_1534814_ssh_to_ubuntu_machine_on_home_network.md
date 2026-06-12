---
title: "ssh to ubuntu machine on home network"
date: 2010-07-20
forum: Networking &amp; Wireless
---

### Post by wannabegeek on 2010-07-20
hello

I recently setup a media server with Karmic on it.
I would like to log onto the machine while at home from my laptop, with ssh, however networking is my least understood topic. Ultimately I'd like to 
ssh to it from anywhere, although I have a dynamic IP.

My wireless router is setup to use 10.0.0.100 for the various machines which connect to 
it.  The media  server is 10.0.0.103

just trying
```
 ssh user@10.0.0.103 
```returns the connection refused error

not sure what the next thing to try is...googling is hard for me since I don't know the terminology involved.

thanks,
wbg

---

### Post by Drenriza on 2010-07-20
ssh (server-user-name)@(ip-address)
example

ssh cristian@192.168.x.x
and then enter that particular users password, when prompted.

---

### Post by james_xxx on 2010-07-20
wannabegeek,

Have you made sure that openssh-server is installed on the media server?

If not, install it, and give it another go.

```
sudo apt-get install ssh
```


Hopefully that is all that is holding you up!

---

### Post by wannabegeek on 2010-07-20
thanks james_xxx but no luck, ssh is there...I tried making another user account with 
admin priv but that didn't help...
wbg

---

### Post by james_xxx on 2010-07-20
wannabegeek,

Just to double-check, are you sure that openssh-server is present?

It will not be there by default, although openssh-client should be. Without openssh-server, you would be able to ssh from but not to your media server. This may all be old news to you.

'ssh' is just a small meta-package that pulls in both the SSH client and server packages, and possibly one or two others.

If you have made sure that openssh-server is there, you might just try running:
```
sudo apt-get install ssh --reinstall
```

Perhaps something strange happened, and your keys never got generated the first time around.

To check and see whether or not your SSH daemon is running, enter:
```
sudo /etc/init.d/ssh status
```

If it isn't running, you can start it with: 
```
sudo /etc/init.d/ssh start
```

---

### Post by wannabegeek on 2010-07-20
I see...did not have openssh-server installed...
gonna get it from repo and repost....
thanks !
wbg

---

### Post by wannabegeek on 2010-07-20
WORKS ! 
thank you ...

---

### Post by james_xxx on 2010-07-20
Glad to hear it. Good Luck!

---

