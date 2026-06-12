---
title: "Which file server do I need ??"
date: 2010-12-10
forum: Networking &amp; Wireless
---

### Post by Mobidoy on 2010-12-10
Hello, 

i am setting up a small network for a friend. He has a server which is home at the moment, he would like to access some files that are on it from his computer(s) at work.

I have set up an ssh server so far and tried vsftpd. Problem is that to be able to modify the files, he has to download them to the local computer, do what he need to do on them and then, remember to send the file back on the server.

Is there a better way to do it ?

---

### Post by tredegar on 2010-12-10
If **ssh** is working, he can just **ssh** with [COLOR="Red"]X[/COLOR]-forwarding turned on into his machine and edit the file there. **gedit** (or **nano**) is *running* on the machine at home, but *displaying* on his local machine
```
user@work:~$ ssh [COLOR="Red"]-X[/COLOR] user@home
user@home:~$ gedit /path/to/file
user@home:~$ nano /path/to/file
user@home:~$ exit
logout
Connection to home closed.
user@work:~$
```

If his server is open to the internet I hope you have secured it with
- a good, properly configured firewall
- no root logins allowed over **ssh**
- strong password(s)
- and, ideally, _only_ private / public key based **ssh** logins allowed (not password-based ones, which should be denied).

---

### Post by pricetech on 2010-12-10
He also needs to port forward SSH in his router.

If you need, or want, a full GUI I recommend NX from nomachine dot com.  There's a Windows client in case he's on a Windows machine at work.  WinSCP is good if he wants to copy files back and forth from a Windows client.  Putty, if all he wants is a command line.

He'll need a fixed IP as well, or use a Dynamic DNS service.

I use all of the above at various times with great success.

Have fun.

---

### Post by Mobidoy on 2010-12-10
It is moire than text editing, we are talking about cad files... Till he can have a server at work place, this is how he wants to do it. 

Later on, all of it will be moved within his shop.

I suspect it could get slow running cad over ssh X session...

---

