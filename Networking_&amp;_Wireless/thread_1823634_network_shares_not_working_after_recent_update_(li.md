---
title: "network shares not working after recent update (libsmbclient problem)"
date: 2011-08-12
forum: Networking &amp; Wireless
---

### Post by gggie on 2011-08-12
I have ubuntu 10.04.  After update I performed yesterday, I could no longer access from other computers shared folders on my ubuntu machine.

I checked update history and it included the following that appeared to be related to network shares:

```
libsmbclient (2:3.4.7~dfsg-1ubuntu3.4) to 2:3.4.7~dfsg-1ubuntu3.7
libpam-smbpass (2:3.4.7~dfsg-1ubuntu3.4) to 2:3.4.7~dfsg-1ubuntu3.7
samba (2:3.4.7~dfsg-1ubuntu3.4) to 2:3.4.7~dfsg-1ubuntu3.7
samba-common (2:3.4.7~dfsg-1ubuntu3.4) to 2:3.4.7~dfsg-1ubuntu3.7
samba-common-bin (2:3.4.7~dfsg-1ubuntu3.4) to 2:3.4.7~dfsg-1ubuntu3.7
smbclient (2:3.4.7~dfsg-1ubuntu3.4) to 2:3.4.7~dfsg-1ubuntu3.7
```

I managed to fix by downgrading (using "force version") libsmbclient.  After downgrade, network shares all worked fine again.

I would prefer to use the latest version because it includes security updates.  Does anyone know if there's some trick to getting network shares to work with the latest version of libsmbclient?

---

### Post by capscrew on 2011-08-12
> **gggie said:**
> I have ubuntu 10.04.  After update I performed yesterday, I could no longer access from other computers shared folders on my ubuntu machine.

I checked update history and it included the following that appeared to be related to network shares:

```
libsmbclient (2:3.4.7~dfsg-1ubuntu3.4) to 2:3.4.7~dfsg-1ubuntu3.7
libpam-smbpass (2:3.4.7~dfsg-1ubuntu3.4) to 2:3.4.7~dfsg-1ubuntu3.7
samba (2:3.4.7~dfsg-1ubuntu3.4) to 2:3.4.7~dfsg-1ubuntu3.7
samba-common (2:3.4.7~dfsg-1ubuntu3.4) to 2:3.4.7~dfsg-1ubuntu3.7
samba-common-bin (2:3.4.7~dfsg-1ubuntu3.4) to 2:3.4.7~dfsg-1ubuntu3.7
smbclient (2:3.4.7~dfsg-1ubuntu3.4) to 2:3.4.7~dfsg-1ubuntu3.7
```

I managed to fix by downgrading (using "force version") libsmbclient.  After downgrade, network shares all worked fine again.

I would prefer to use the latest version because it includes security updates.  Does anyone know if there's some trick to getting network shares to work with the latest version of libsmbclient?

The package *libpam-smbpass *is not absolutely needed for Samba to perform correctly.  It is installed when you create shares using the GUI interface (Gnome usershares) or when you are administering a system in which you wish to sync the **nix local password *to the *smbpasswd*.  See [**_[COLOR="DarkSlateGray"]here[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=1723762&page=2") for more info.

How have you setup your users?

---

### Post by Morbius1 on 2011-08-12
> After update I performed yesterday, I could no longer access [COLOR=Blue]from other computers shared folders on my ubuntu machine.[/COLOR]> I managed to fix by downgrading (using "force version") libsmbclient.Someone's going to have to explain to me very slowly how upgrading, downgrading, or even removing libsmbclient on the server would have any affect on a client accessing it's shares.

Am I missing something?

---

### Post by capscrew on 2011-08-12
> **Morbius1 said:**
> Someone's going to have to explain to me very slowly how upgrading, downgrading, or even removing libsmbclient on the server would have any affect on a client accessing it's shares.

Am I missing something?

One learns never to question a users *perception*.  :-)

---

### Post by gggie on 2011-08-12
> **capscrew said:**
> How have you setup your users?

I have the shares set up to allow anyone (guest) to access.

> **Morbius1 said:**
> Someone's going to have to explain to me very slowly how upgrading, downgrading, or even removing libsmbclient on the server would have any affect on a client accessing it's shares.

Am I missing something?

I have no clue what libsmbclient does.  All I know is this: 
(1) my shares had been working fine for a long time; 
(2) I did an ubunutu update yesterday; 
(3) immediately after the update, my shares weren't working (my Windows machine couldn't even see the ubuntu machine on the network anymore); 
(4) I downgraded libsmbclient **and made no other changes whatsoever**; 
(5) immediately after that downgrade, my shares worked again and my ubuntu machine was visible on the network again.

So while I certainly understand capscrew's point about user perception not always being reality, I'd welcome an explanation for how, despite those facts, I'm somehow mistaken about the problem and/or the solution.

---

### Post by capscrew on 2011-08-12
> **gggie said:**
> I have the shares set up to allow anyone (guest) to access.


I have no clue what libsmbclient does.  All I know is this: 
(1) my shares had been working fine for a long time; 
(2) I did an ubunutu update yesterday; 
(3) immediately after the update, my shares weren't working (my Windows machine couldn't even see the ubuntu machine on the network anymore); 
(4) I downgraded libsmbclient **and made no other changes whatsoever**; 
(5) immediately after that downgrade, my shares worked again and my ubuntu machine was visible on the network again.

So while I certainly understand capscrew's point about user perception not always being reality, I'd welcome an explanation for how, despite those facts, I'm somehow mistaken about the problem and/or the solution.

The reality is that this sounds like a DNS/NetBIOS problem.

Edit: The update has revealed misconfiguration of your setup.  This can be caused by you or by Gnome (Nautilus).  Regardless of how it was caused, your problem is one of the most common: lack of proper Local LAN name services.

What have you done to provide host name resolution for the LAN?

---

### Post by gggie on 2011-08-12
> **capscrew said:**
> What have you done to provide host name resolution for the LAN?

Don't think I've done anything special.  My recollection is that network connectivity/shares just worked "out of the box."

If you've got something that just works from a base install of ubuntu, you leave all the default settings, and a later update breaks that functionality, the notion that the update "revealed a misconfiguration" in my setup doesn't quite seem to me to be the right way of looking at the issue...

---

### Post by capscrew on 2011-08-12
> **gggie said:**
> Don't think I've done anything special.  My recollection is that network connectivity/shares just worked "out of the box."

If you've got something that just works from a base install of ubuntu, you leave all the default settings, and a later update breaks that functionality, the notion that the update "revealed a misconfiguration" in my setup doesn't quite seem to me to be the right way of looking at the issue...

That's all fine and dandy.  You can look at it anyway you want.  The fact is there are a lot of people between you and the developers of both Gnome and Samba.  You have Debian packagers and Ubuntu packagers.  The packager can make arbitrary decisions that will affect your experience.  In addition not all developers talk amongst each other.  The Gnome devs don't necessarily have the same view of Samba as the Samba devs.  

In short, there is no singular way of monitoring the interrelationship between the differing projects.  This is the part of the price you pay with open source (FOSS) software.  You get to figure out what happened.  If you think it is a bug then you can post a bug report.

I'm a practical guy.  I say: understand the problem and get on with fixing it.  There is no "out of the box".  There are just too many variations to the setup of Samba.  One thing I do know is that Samba expects that you have proper running TCP/IP connectivity in the LAN.  This means configuring IP addressing and DNS host name at minimum.  If you don't do that we need to modify the "base install" of Samba.

I use the same smb.conf file I created with Ubuntu Dapper (6.06 LTS) and it has worked on every upgrade to 10.04 LTS.  I have installed Ubuntu 11.04 and it has worked there too.  In a sense my install works "out of the box", but then again, I laid the proper groundwork.

---

