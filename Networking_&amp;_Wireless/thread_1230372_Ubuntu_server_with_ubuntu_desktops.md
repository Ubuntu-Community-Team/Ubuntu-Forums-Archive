---
title: "Ubuntu server with ubuntu desktops"
date: 2009-08-03
forum: Networking &amp; Wireless
---

### Post by minerbog on 2009-08-03
Hi all,

Hope this is in the right place!!!! :)

I have search high and low on google to try and find out if ubuntu can act as a active directory but none of the results really tell me what I need to know.

Basiclly, I want to set up a ubuntu server with ubuntu desktops, and have the desktops retrieve user information from the server like in windoz active directory. I have found info about connecting either from a win desktop to a ubuntu server using samba or from ubuntu to a win server but can't seem to find info on using both desktop a client running linux.

Any links would be greatly received.

Gav.

---

### Post by wojox on 2009-08-03
Sure look here:

[https://help.ubuntu.com/8.04/serverguide/C/index.html](https://help.ubuntu.com/8.04/serverguide/C/index.html)

---

### Post by minerbog on 2009-08-03
I have read this and it does supply some great infomation.

However, its doesn't really inform me of what I need.  Windoz for example is a simple matter of setting up users on the server and the connecting the client to the domain. The client the retrieves the data from the sever (providing it doesn't crash that is!!).

How is done using ubuntu???

Many thanks.

Gav.

---

### Post by snek on 2009-08-03
You will have to use Samba for this..
As far as I know it's not going to be easy, but it is definitely possible. Our office used a Linux server as AD server for many years.

If you want an instant solution with a nice graphical interface you might want to checkout [http://ebox-platform.com/](http://ebox-platform.com/) which is an all-in-one solution built ontop of Ubuntu.

---

### Post by FreakTech on 2009-08-03
I think what you are looking for is an LDAP server.  Look here

[https://help.ubuntu.com/8.10/serverguide/C/openldap-server.html](https://help.ubuntu.com/8.10/serverguide/C/openldap-server.html)

---

### Post by minerbog on 2009-09-09
Thanks the LDAP server does just the thing. Bit of a pig to confirgure properly tho!! :)

---

