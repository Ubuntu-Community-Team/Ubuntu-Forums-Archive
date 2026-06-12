---
title: "Xubuntu shared files issues"
date: 2011-02-05
forum: Networking &amp; Wireless
---

### Post by Synaesthes1a on 2011-02-05
Hello,

First of all, I´m new to this forum. I have read and searched for several things to help me setting up an Xubuntu server in the past, which, in the end, helped me a lot.

So here´s my situation. I have set up a Xubuntu server with a cable connected to my Windows PC and a Network adapter for a connection to the internet and for remote access from outside.

However, I can´t boot Windows XP properly anymore. Luckily, I have a dual boot with Ubuntu. What I want right now is to back my files up from Windows XP onto my server using SAMBA. Normally, in Windows, I would connect to the shared files on Xubuntu by using ´\\ipadress\homes´ in the run window. I thought I could access my files on Xubuntu with Ubuntu on a different way by using Places > Network.

However, there’s nothing in the folder that holds the server name. So, I can’t seem to access my files using Ubuntu. I checked the connection by using Firefox, and fill in the IP adress of my server. It works fine, I can still access torrentflux. But that’s not what I want right now. 

Is there any way to fix this issue? 

Thanks in advance.

---

### Post by Morbius1 on 2011-02-05
Not exactly sure I followed that. If you have a [homes] section defined in your smb.conf then to access it from Linux you use the following in a terminal:
```
nautilus smb://ipaddress/user-name
```

---

### Post by Synaesthes1a on 2011-02-05
> **Morbius1 said:**
> Not exactly sure I followed that. If you have a [homes] section defined in your smb.conf then to access it from Linux you use the following in a terminal:
```
nautilus smb://ipaddress/user-name
```

Didn&#8217;t work, got an error right of the bat. Displaying ¨Nautilus cannot handle ¨SMB¨ locations¨.

**Edit:** It seems I can get to Network > Windows Network > MSHOME > Akiyama (name of server) > Homes. However, it gives me an error saying that it Failed to mount Windows share. Which is an issue I had before, but I tried to fix that, without results.

---

### Post by Morbius1 on 2011-02-05
See if you have the following package installed:
```
sudo apt-get install gvfs-backends
```

---

### Post by Synaesthes1a on 2011-02-05
> **Morbius1 said:**
> See if you have the following package installed:
```
sudo apt-get install gvfs-backends
```

Yes, I have that package installed.

---

### Post by Morbius1 on 2011-02-05
This is getting curiouser and curiouser.

The only situation I can think of if you have gvfs-backends installed and you are still gettng that error is if you are running as root. If you are then log into a normal user.

Also, if on your Xubuntu server you have a [homes] section that looks something like this:
> [homes]
    comment = Home Directories
    valid users = %S
    create mask = 0700
    directory mask = 0700
    read only = yesIt's not a real share that you browse to and mount it's a template. It creates a share "on the fly" and you can only access it by explicitly using an ip address or host name and a user name. 

When you are in Nautilus and you go to Network > Windows Network > MSHOME > Akiyama you should see the following in the location bar:
> smb://akiyama[COLOR=Blue]*If you don't have a location bar then press Ctrl+L over Nautilus*[/COLOR]

Is this not what you see?

If it is then finish it:
```
 smb://akiyama/your-user-name
```

---

### Post by Synaesthes1a on 2011-02-05
> **Morbius1 said:**
> This is getting curiouser and curiouser.

The only situation I can think of if you have gvfs-backends installed and you are still gettng that error is if you are running as root. If you are then log into a normal user.

Also, if on your Xubuntu server you have a [homes] section that looks something like this:
It's not a real share that you browse to and mount it's a template. It creates a share "on the fly" and you can only access it by explicitly using an ip address or host name and a user name. 

When you are in Nautilus and you go to Network > Windows Network > MSHOME > Akiyama you should see the following in the location bar:
[COLOR=Blue]*If you don't have a location bar then press Ctrl+L over Nautilus*[/COLOR]

Is this not what you see?

If it is then finish it:
```
 smb://akiyama/your-user-name
```

It are the simplest things that fix such issues, isn’t it? Followed the steps, worked like a charm. Thank you very much!

---

