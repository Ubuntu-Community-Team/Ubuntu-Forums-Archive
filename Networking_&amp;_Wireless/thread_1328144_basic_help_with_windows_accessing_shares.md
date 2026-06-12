---
title: "basic help with windows accessing shares?"
date: 2009-11-16
forum: Networking &amp; Wireless
---

### Post by callmecheez on 2009-11-16
Dear All,

I have searched for an answer to this but haven't come up with anything, so apologies if it is obvious / simple or frequently asked!

I have installed Ubuntu 9.10 on a spare machine, and have connected it to my router using LAN connection.

I created a folder in ubuntu - clicked 'share' and gave it a name, and ticked the box 'allow other users to access' and UNticked 'guest access'.

My windows 7 can't access this share - it keeps prompting me for a username / password, and showing the domain as the user account for windows 7.

Where am I going wrong, please?

I'd simply like a share on my network that requires a simply password to get into!

---

### Post by puppywhacker on 2009-11-16
if you untick the "use guest account", windows as the client will need to provide the correct username and server to linux as the server.

The problem is that samba will have it's own users seperate from the normal linux users, unless you synchronize them. This means that you can create users with smbpasswd and add those users to linux, and use it on the windows machine to access the share

[http://www.howtogeek.com/howto/ubuntu/create-a-samba-user-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/create-a-samba-user-on-ubuntu/)

P.S. To create the user, run "sudo smbpasswd -a <username>"

---

### Post by callmecheez on 2009-11-16
> **puppywhacker said:**
> if you untick the "use guest account", windows as the client will need to provide the correct username and server to linux as the server.

The problem is that samba will have it's own users seperate from the normal linux users, unless you synchronize them. This means that you can create users with smbpasswd and add those users to linux, and use it on the windows machine to access the share

[http://www.howtogeek.com/howto/ubuntu/create-a-samba-user-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/create-a-samba-user-on-ubuntu/)

P.S. To create the user, run "sudo smbpasswd -a <username>"


Thanks for the quick reply! So I can't login, from windows, using my ubuntu default / admin account? Thanks again :)

---

### Post by dmizer on 2009-11-16
> **callmecheez said:**
> Thanks for the quick reply! So I can't login, from windows, using my ubuntu default / admin account? Thanks again :)

No, you can't ... nor should you be able to. The same is true in correctly configured Windows file servers.

Edit:
Actually, you can if you mount the drive. But you're better off adding the Windows account to the Ubuntu computer.

---

### Post by callmecheez on 2009-11-16
Thanks for the reply (and patient response) i'm very new to this and thought i'd have a go. .

I assumed i could simply set a username and password for a share on ubuntu, and have that be independant of any other username (windows OR ubuntu) - so that if any random laptop was on my network I could use a username and password to get onto THAT share?

Does that make sense?  Thanks again

---

### Post by callmecheez on 2009-11-16
may I bump? :)

---

### Post by puppywhacker on 2009-11-16
yes, so you can create a samba user with this command 

```
sudo smbpasswd -a callmecheez
```

that user is taken from linux, the password can be different

---

### Post by Iowan on 2009-11-16
> **callmecheez said:**
>  So I can't login, from windows, using my ubuntu default / admin account? Maybe I'm over analyzing it, but if your windows account happens to match the Ubuntu account (and has a matching Samba account)...

---

