---
title: "How To Override Permissions Folder in Linux."
date: 2009-04-03
forum: Networking &amp; Wireless
---

### Post by tizero on 2009-04-03
Hello,


I'm building a website on a windows vista with joomla 1.5.10.
I have backupped the web site with a joomla extension (tool) named: "joomlapack".

I need to start a manual restoration of the backupped site, on a linux host, remotely with ssh secure file transfer. In order to migrate my site over there I have to move the website files of the root folder in another folder. I tried to do that and I get a message error about permissions. 

I have checked with ssh secure file transfer them and they are set all at 777 for that folder.

Now, how may workaround them and remotely move the folder content?


Bye.


Tizero.

---

### Post by Iowan on 2009-04-03
A couple of options... You could add your SSH-user to a group with write permissions on the directory, or you could create a directory your SSH user can access - and change server's document root to use that directory. (There's probably a good How-To link for this - if I can find it.)

---

### Post by tizero on 2009-04-03
> **Iowan said:**
> 
...  or you could create a directory your SSH user can access - and change server's document root to use that directory...


I have to run all from my windows workstation. What do you mean by that sentence?

Which directory? And what do you mean by document root?
:???:

Bye.


Tizero.

---

