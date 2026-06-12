---
title: "Access SAMBA share without credentials?"
date: 2011-12-27
forum: Networking &amp; Wireless
---

### Post by ChrisRChamberlain on 2011-12-27
Have customer with a small LAN consisting of:-

1 x Ubuntu server
n x Win 7 boxes
1 x WIN XP Pro box

SAMBA is installed and the Windows boxes can access the shares without a problem.

Customer has added a Win XP Home box which can access the server after username/password has been entered.

Reboot/boot the Win XP Home box and credentials are required again.

Windows XP Home is known to be problematical in a networked environment.

So, is it possible to configure SAMBA to work without username/password to accomodate this Windows XP Home box?

TIA

---

### Post by dandnsmith on 2011-12-27
Just make the shares open, with no username/password to be validated.

XP Home isn't really any worse than the other Windows products, it's mainly that the defaults for each new version changes - I've just been having to accomodate Win7 on my local network, and that is a real patience tryer, as a lot of the bits are harder to find.

---

### Post by collisionystm on 2011-12-27
> **ChrisRChamberlain said:**
> Have customer with a small LAN consisting of:-

1 x Ubuntu server
n x Win 7 boxes
1 x WIN XP Pro box

SAMBA is installed and the Windows boxes can access the shares without a problem.

Customer has added a Win XP Home box which can access the server after username/password has been entered.

Reboot/boot the Win XP Home box and credentials are required again.

Windows XP Home is known to be problematical in a networked environment.

So, is it possible to configure SAMBA to work without username/password to accomodate this Windows XP Home box?

TIA

Is the samba share password protected?

The best way to do it is to use mapped network drives

write a login script that automatically maps if you like.

---

### Post by ChrisRChamberlain on 2011-12-28
dandnsmith, collisionystm

Thanks for your replies. Found a simple explanation here:-

[http://www.go2linux.org/linux/2011/02/how-share-files-windows-linux-samba-no-password-public-905](http://www.go2linux.org/linux/2011/02/how-share-files-windows-linux-samba-no-password-public-905)

---

### Post by Morbius1 on 2011-12-28
Presumably you noticed the mistake in that linked HowTo:
>  chmod 666 /tmp/share/ -RDirectories need the execute bit turned on or else you won't be able to "open" them to see what's inside. This is better:
```
chmod 777 /tmp/share/ -R
```The only problem with that is that the octal mode of chmod isn't smart enough to differentiate between the a folder and a file so that command will make all folders executable ( this you want ) but also all files executable ( this you don't want ). The best way is this:
```
chmod -R a+rwX /tmp/share
```All folders will be 777 and all files will be 666

---

### Post by ChrisRChamberlain on 2011-12-28
Morbius1

Thanks for that - as the required /path/folders already exist, that part of the 'HowTo' code was not used.

But

```
chmod -R a+rwX /tmp/share
```

has been noted and will certainly be used in the future.:)

---

