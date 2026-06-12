---
title: "gFTP problem / Question"
date: 2009-01-19
forum: Networking &amp; Wireless
---

### Post by slew on 2009-01-19
Hi,

Currently I'm using Ubuntu Studio and am trying to connect to my church's ftp site so I can manage the website. Whenever I try to connect to ftp.stmatthewstoledo.org, gFTP says:
Trying ftp.stmatthewstoledo.org.bexmta.net:21. 
I've tried creating a bookmark from within the .gftp/bookmarks file but I get the same result every time. 
This doesn't make sense because the FTP connects on the Windows computer from the same network. 
I'm on a Sony Vaio, wireless laptop.
The website should work as well, same address, however it appears to be a dead link in Firefox. If I type the same website on any other computer on my network, the website loads fine.
Anyone have any clues?
Thanks!

---

### Post by metalguy639 on 2009-01-19
Personally I had MANY problems with gFTP. Its kinda annoying IMO. maybe you should try another FTP client instead for your needs. I found that filezilla does great for what I need and its pretty close to what I used to use in windows (FlashFXP). To install just open your terminal and type in:

```
sudo apt-get install filezilla
```

and that should install it on your system.

---

### Post by slew on 2009-01-20
Hi,

Thanks, and I installed FileZilla yet didn't get connected to the ftp server. This time, it didn't append any extra domains, just eventually timed out. I checked the site on another computer and it connected fine. I can ping both the ftp server and the ip address with no problems.
I'm on a wireless laptop. Does anyone have any suggestions?

Thanks!


> **metalguy639 said:**
> Personally I had MANY problems with gFTP. Its kinda annoying IMO. maybe you should try another FTP client instead for your needs. I found that filezilla does great for what I need and its pretty close to what I used to use in windows (FlashFXP). To install just open your terminal and type in:

```
sudo apt-get install filezilla
```

and that should install it on your system.

---

### Post by metalguy639 on 2009-01-20
Do yo have the direct IP address? Should be a series of 4 numbers something like 180.12.54.70 (not that but like it). Sometimes for some odd reason that works. 

A couple of other things you might want to look into..Do you have a firewall installed on your PC that you are trying to connect with? Is your laptop behind any kind of router at all? If so then you might need to configure your router or firewall to allow connections from that machine. Sorry I'm not much more help.

---

### Post by slew on 2009-01-20
Hi,

I do have the IP address, and have tried connecting that way but it just doesn't work. As far as I know, the firewall is turned off, and I've even added this laptop to the DMZ on my router. 
It's starting to look like Ubuntu won't be able to handle my FTP requests. :(

---

### Post by slew on 2009-01-20
The really weird thing is that I can connect to other ftp sites through gFTP, FileZilla, and even the command line. I don't get why I cant connect to this one site.

---

### Post by metalguy639 on 2009-01-20
> **slew said:**
> The really weird thing is that I can connect to other ftp sites through gFTP, FileZilla, and even the command line. I don't get why I cant connect to this one site.

Have you tried clearing your history maybe & cache?

---

