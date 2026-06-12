---
title: "Not picking up Belken wireless signal anymore"
date: 2012-03-16
forum: Networking &amp; Wireless
---

### Post by malsha on 2012-03-16
First let me say, although I've been using Ubuntu w/ Linux for about two years I'm still not versed on how to solve most issues when they arrise, too tedius to deal with so I usully have to go get a professional. 
 
Well, the other day I was fiddling around with the password settings in System- Administration the Login Screen (configue login screen behavior) and I changed the setting to failsafe GNOME and there begun my problems now I can't change it back to what is was because the box is grayed out and 'unlock' is not unlocking it. My biggest issue is now I can't get unto the internet :confused: . I use a Belkin router connected to DSL but all the routher and password and server information is gone including the icon that indicates whether I'm connected to he net. On my laptop my internet wirless light is on so I know that is working but I just can't connect to the net. I don't even remember what information was there and it is not recognizing or picking up the wireless singal from the router to automatically connect. 
 
I did some other stuff but I just made things worse and now my original information and icons that were on the desktop screen are gone. This is too hard for me. Ready to just give up. Help!

---

### Post by praseodym on 2012-03-16
Hi,

try to start the tool from terminal (CTRL+ALT+T):

```
gksu nm-connection-editor
```
and set up the connection. Does the icon show up with the command

```
nm-applet
```
?

---

