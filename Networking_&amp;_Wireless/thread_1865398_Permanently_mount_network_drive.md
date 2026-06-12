---
title: "Permanently mount network drive"
date: 2011-10-20
forum: Networking &amp; Wireless
---

### Post by static_recharge on 2011-10-20
Hi I'm a little on the new side when it comes to Linux in general and I just installed Ubuntu a few days ago. There is a shared network drive that my school provides that I would like to have permanently mounted in Ubuntu. When performing this operation on Windows you simply click "map network drive" and enter the credentials. The address for the drive is like this: (where $something represents actual information)

https://$something.$something.$something/share

and there are username and password credentials to input as well.

I've tried many other fixes found on the web and tried to adapt them to my needs but I'm missing something.

currently i have the following line appended to my fstab file:

```
//$something.$something.$something/share cifs iocharset=utf8,credentials=/path/to/.smbcredentials,uid=1000 0 0
```when I run the ```
sudo mount -a
``` command i get this as the error:

```
mount error(115): Operation now in progress
```Any help would be greatly appreciated and I thank you in advance for taking the time to look into this!

---

### Post by georgeaperkins on 2011-10-20
Hi static_recharge

Once the drive is mounted, drag it onto the bookmarks bar on the left pane of nautilus. That way, when ever you click on it the drive will be mounted automatically. 

Hope this helps

George

---

### Post by static_recharge on 2011-10-20
> **georgeaperkins said:**
> Hi static_recharge

Once the drive is mounted, drag it onto the bookmarks bar on the left pane of nautilus. That way, when ever you click on it the drive will be mounted automatically. 

Hope this helps

George

Thank you for your quick reply, unfortunately this is not my issue. The exact issue is that the drive does not mount to begin with so i cannot bookmark it or anything of that nature quite yet. As mentioned above I am getting an error from the sudo mount -a command.

---

### Post by bab1 on 2011-10-20
> **static_recharge said:**
> Hi I'm a little on the new side when it comes to Linux in general and I just installed Ubuntu a few days ago. There is a shared network drive that my school provides that I would like to have permanently mounted in Ubuntu. When performing this operation on Windows you simply click "map network drive" and enter the credentials. The address for the drive is like this: (where $something represents actual information)

https://$something.$something.$something/share

and there are username and password credentials to input as well.

I've tried many other fixes found on the web and tried to adapt them to my needs but I'm missing something.

currently i have the following line appended to my fstab file:

```
//$something.$something.$something/share cifs iocharset=utf8,credentials=/path/to/.smbcredentials,uid=1000 0 0
```when I run the ```
sudo mount -a
``` command i get this as the error:

```
mount error(115): Operation now in progress
```Any help would be greatly appreciated and I thank you in advance for taking the time to look into this!

I'll bet this is a WebDav share and not a Samba (CIFS) share.  Check out web based sharing [_[COLOR="Blue"]here[/COLOR]_]("http://www.google.com/search?q=web+shares+8+webdav&btnG=Go!#pq=web+shares+8+webdav&hl=en&sugexp=kjrmc&cp=11&gs_id=4&xhr=t&q=web+shares++webdav&qe=d2ViIHNoYXJlcyAgd2ViZGF2&qesig=kXCm3Uhg76R6fP-UaXm25A&pkc=AFgZ2tnTD4eGCtSBQadrbZ6a0rU5r0DO6qlHMfxQJW4IgyvUwzYMUK3X8QDuLAc0yrBbBz2XePC-qPRll8Wlj_QUyOzIDJi5Qw&pf=p&sclient=psy-ab&source=hp&pbx=1&oq=web+shares++webdav&aq=f&aqi=&aql=&gs_sm=&gs_upl=&bav=on.2,or.r_gc.r_pw.,cf.osb&fp=dc20b2672385f007&biw=1171&bih=677").

---

### Post by static_recharge on 2011-10-20
> I'll bet this is a WebDav share and not a Samba (CIFS) share.  Check out web based sharing [_[COLOR=Blue]here[/COLOR]_]("http://www.google.com/search?q=web+shares+8+webdav&btnG=Go%21#pq=web+shares+8+webdav&hl=en&sugexp=kjrmc&cp=11&gs_id=4&xhr=t&q=web+shares++webdav&qe=d2ViIHNoYXJlcyAgd2ViZGF2&qesig=kXCm3Uhg76R6fP-UaXm25A&pkc=AFgZ2tnTD4eGCtSBQadrbZ6a0rU5r0DO6qlHMfxQJW4IgyvUwzYMUK3X8QDuLAc0yrBbBz2XePC-qPRll8Wlj_QUyOzIDJi5Qw&pf=p&sclient=psy-ab&source=hp&pbx=1&oq=web+shares++webdav&aq=f&aqi=&aql=&gs_sm=&gs_upl=&bav=on.2,or.r_gc.r_pw.,cf.osb&fp=dc20b2672385f007&biw=1171&bih=677").

could you maybe point me to a preferred site? i'm not having much luck on my own.

---

### Post by bab1 on 2011-10-20
> **static_recharge said:**
> could you maybe point me to a preferred site? i'm not having much luck on my own.

Be more specific with what you are trying to mount.  The site is public facing I assume.  Are there any instructions at their site?  Do they have any kind of documentation?

---

### Post by static_recharge on 2011-10-20
> **bab1 said:**
> Be more specific with what you are trying to mount.  The site is public facing I assume.  Are there any instructions at their site?  Do they have any kind of documentation?

The only documentation that they have is for windows or mac setups. This is a https share drive that the school uses to pass out and in assignments and required documents for the courses. On windows you just hit "map network drive" and fill in the info.

Just recently I have been successful when connecting to the drive through "connect to server" but I don't know how to make it connect or mount automatically. Here is the info I filled out to get it to connect:

Server: [servername]  Port: 443
Type: Secure WebDAV (HTTPS)
Folder: /share
Username: [username]
Password: [password]
checked "remember password"

This works for that session but as soon as I log out or restart the computer I have to reenter this information.

If you need any more information please let me know exactly what you are looking for and I will try my best to get it!

---

### Post by bab1 on 2011-10-21
> **static_recharge said:**
> The only documentation that they have is for windows or mac setups. This is a https share drive that the school uses to pass out and in assignments and required documents for the courses. On windows you just hit "map network drive" and fill in the info.
Yes, WebDav is very Windows centric and Windows Explorer has HTTP browsing capabilities.  Unfortunately there has never been much interest in the FOSS world regarding this method. > 

Just recently I have been successful when connecting to the drive through "connect to server" but I don't know how to make it connect or mount automatically. Here is the info I filled out to get it to connect:

Server: [servername]  Port: 443
Type: Secure WebDAV (HTTPS)
Folder: /share
Username: [username]
Password: [password]
checked "remember password"

This works for that session but as soon as I log out or restart the computer I have to reenter this information.

If you need any more information please let me know exactly what you are looking for and I will try my best to get it!
This is as close to the Windows way of accessing a WebDav enabled server as you are going to get using Linux.  Once you have mounted the share you can *bookmark *it for future use.  To bookmark the mounted share (in the Nautilus file browser) ou you can either click on Bookmarks>>Add Bookmark or you can just hit CNTL+D.

There are 2 other ways.  You can look in Firefox Plug-ins for a WebDav plug-in but you must use FireFox and not Nautilus.  The second way is to install the userland filesystem called davfs and use it to mount the share via fstab.  I warn you that this is VERY insecure.  You must configure it very carefully.  You are on your own there; I've not done this myself.

So now you have the 3 ways to mount the share.  I would do the first one.  Nautilus knows how to mount the share securely and now you know how to book mark the share for easy access later on.

Let me know how it works for you.

---

### Post by static_recharge on 2011-10-21
Thank you, using the nautilus bookmark appears to work even after a restart and for my purposes that is perfect. Thanks again!

---

