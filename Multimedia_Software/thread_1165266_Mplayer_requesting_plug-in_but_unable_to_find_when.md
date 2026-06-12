---
title: "Mplayer requesting plug-in but unable to find when playing .mov file"
date: 2009-05-20
forum: Multimedia Software
---

### Post by chiques on 2009-05-20
Hi Everyone,
I was wondering if someone can give me some insight on what I can do to play *.*mov files.

When I play a .mov file in Jaunty 9.04 I get the following error:

> Search for suitable plugin?

The required software to play this file is not installed. You need to install suitable plugins top lay media files. Do you want to search for a plugin that supports teh selected file?

The search will also include software which is not officially supported

[[IMG]http://img411.imageshack.us/img411/954/searchplugin1.th.png[/IMG]](http://img411.imageshack.us/my.php?image=searchplugin1.png)

So I click "Search". I then get this:

> No packages with the requested plugins found.
The requested plugins are:

Mu-Law decoder

[[IMG]http://img411.imageshack.us/img411/5695/searchplugin2.th.png[/IMG]](http://img411.imageshack.us/my.php?image=searchplugin2.png)


I have tried installing restricted codecs as described on [https://help.ubuntu.com/community/RestrictedFormats/]("https://help.ubuntu.com/community/RestrictedFormats/") but I still keep getting the same error. 

Any suggestions would greatly be appreciated.

---

### Post by hatalar205 on 2009-05-20
Try this link:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
It has nearly all necessary codecs.

---

### Post by chiques on 2009-05-20
> **hatalar205 said:**
> Try this link:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
It has nearly all necessary codecs.


Hi hatalar205,
I have tried using that site but no luck. 


Is there a way to uninstall "ALL CODECS" I have installed and reinstall?

---

### Post by hatalar205 on 2009-05-20
> **chiques said:**
> Hi hatalar205,
I have tried using that site but no luck. 


Is there a way to uninstall "ALL CODECS" I have installed and reinstall?

Have you done the steps there and installed the codecs there?
libdvdcss2 + w32codecs

---

### Post by chiques on 2009-05-20
> **hatalar205 said:**
> Have you done the steps there and installed the codecs there?
libdvdcss2 + w32codecs

Hi hatalar205,
Yes, I have gone through the steps to install ***libdvdcss2*** and ***w32codec*** but I still get the prompts from the initial post.

*[COLOR="Blue"]You can see my terminal text on:[/COLOR]*
[http://paste.ubuntu.com/176638/](http://paste.ubuntu.com/176638/)

---

### Post by chiques on 2009-05-20
**[COLOR="Red"][SIZE="5"]UPDATE:[/SIZE][/COLOR]**

I was able to get VLC player to play the video and audio using the same file. I had to go to the Audio output settings and change it from Default to X11. Is there any way to do this with Mplayer?


[[IMG]http://img411.imageshack.us/img411/6057/vlcpreferences.th.png[/IMG]](http://img411.imageshack.us/my.php?image=vlcpreferences.png)

---

