---
title: "How can I change the hostname for DHCP and make it has effect without restarting?"
date: 2012-08-20
forum: Networking &amp; Wireless
---

### Post by Efemeral on 2012-08-20
I've already tried changing the hostname by editing both:

[LEFT]
[LIST]
[*]    /etc/hostname
[*]    /etc/hosts
[/LIST]
[/LEFT]

However when I try to use sudo it doesn't work. I have to restart the computer to make sudo work again. The errors I get before restarting the computer are:
[CENTER] ```

unable to resolve host **<hostname>**
No protocol specified
No protocol specified
**<application name>**: cannot connect to X server :0

```where **<hostname>** is the new name I changed and **<application name>** the name of the application I tried to run with sudo.
[/CENTER]
  
I have also tried:


[LIST]
[*]    sudo hostname **<new hostname>**
[/LIST]

but after successfully executing the command I start getting the same errors as if I had manually modified the files. Also, while to the computer it appears as if the hostname is another, the hostname on the network doesn't change with this command. It appears to only change it for the computer and not for the DHCP data.

I have also tried modifying

[LIST]
[*]/etc/dhcp/dhclien.conf
[/LIST]
line

[LIST]
[*]send host-name "**<hostname>**";
[/LIST]
but it doesn't have any effect.


So, is there anyway to make it without having to restart the computer? Maybe if I know the services that deal with hostname validation on the machine I might be able to restart those services instead of restarting the computer.

---

### Post by Efemeral on 2012-08-20
```
sudo pkill X
```That's how it's done and there won't be a need to restart the computer after editing the files.

---

### Post by CharlesA on 2012-08-20
You should have only had to restart networking for those to take effect.

```
sudo /etc/init.d/networking restart
```

---

### Post by Efemeral on 2012-08-20
Oh, my bad. Let me try it. Wait...

---

### Post by CharlesA on 2012-08-20
How are you connected to the machine? What applications are you trying to run?

---

### Post by Iowan on 2012-08-20
I presume you meant /*etc/dhcp/dhclient.conf*...
To which address did you assign the new hostname (in */etc/hosts*)?
Mine uses 127.0.1.1

---

### Post by Efemeral on 2012-08-20
> **CharlesA said:**
> How are you connected to the machine? What applications are you trying to run?
I don't really get the first question. I was trying to run an application I made that requires administrative privileges. Since it didn't worked I then tried with applications like kate and dolphin which I know should be better ran with kdesudo but I ran them with sudo just to test it wasn't only my application that didn't run.

> **Iowan said:**
> I presume you meant /*etc/dhcp/dhclient.conf*...
To which address did you assign the new hostname (in */etc/hosts*)?
Mine uses 127.0.1.1
That same one. 127.0.1.1

> **CharlesA said:**
> You should have only had to restart networking for those to take effect.
 
 ```
sudo /etc/init.d/networking restart
```
Tried this and... meh, it works more or less like pkill X. With pkill X the session logs out automatically and when you log in again sudo works good again. With the one you gave me I have to manually log out and log in again. Otherwise if I don't log out with the one you gave me, when I try to use sudo I get:
```
Invalid MIT-MAGIC-COOKIE-1 keyInvalid MIT-MAGIC-COOKIE-1 key**<application>**: cannot connect to X server :0
```I think that logging out and logging in is still better than restarting the computer.

EDIT: I think the key component here is the part that says **X server : 0**

---

### Post by CharlesA on 2012-08-21
Sounds like you are trying to forward X over SSH, is this what you are trying to do?

---

