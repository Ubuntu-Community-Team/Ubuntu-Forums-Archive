---
title: "Using LogMeIn"
date: 2013-04-12
forum: Networking &amp; Wireless
---

### Post by cmcanulty on 2013-04-12
I am trying to use logmein to manage some of our library networked computers as a remote login. I can easily see and use all the win 7 machines, but all of our public machines are running Ubuntu Classic 12.04. I don't know what information I need to do this. I am also running Ubuntu Classic 12.04 at home where I can access the win 7 machines. How do I go about adding the Ubuntu machines, like what do I need to do at the library end on each machine and at my home machine. I have read about this but am not too good at networking, so please answer for dummies.

---

### Post by dargaud on 2013-04-12
Some starters. LogMeIn is a Windows executable. I don't know if it has client/servers for Linux. The usual and secure way to log remotely on a linux machine is to use ssh. But it allows only console interaction. To see the screen one way to do it is to do VNC via a SSH tunnel. Another way if the connection is local and fast is to do X11 though a ssh tunnel. I don't go into details but if you search for those keywords you'll find plenty of tutorials.

---

### Post by cmcanulty on 2013-04-12
From my Ubuntu machine at home I can login by using logmein website and control the win 7 computers and control them just as if I am sitting at them. I need to know how to add the ubuntu machines and control them the same way

---

### Post by The Spectre on 2013-04-13
I am pretty sure that LogMeIn does not offer a version for Linux.

You should check out TeamViewer...
[http://www.teamviewer.com/en/download/linux.aspx](http://www.teamviewer.com/en/download/linux.aspx)

Not only do they have a Linux version but they also have the browser based login capability's...[URL="https://login.teamviewer.com/"]
https://login.teamviewer.com/[/URL]

Plus there is also a Portable Version that can be run from a USB Flash Drive...
[http://download.teamviewer.com/download/TeamViewerPortable.zip](http://download.teamviewer.com/download/TeamViewerPortable.zip)

The Portable version is only available for Windows but in my case that is perfect because I can use it at my work computer to Login to both my Linux and Windows based computers without having to install anything.

Plus there is also a free Android App that I use to login to both my Linux and Windows based computers.

---

### Post by cmcanulty on 2013-04-13
I will try itI hope you can provide some help. Logmein does work as I said in my Ubuntu 12.04 to access windows I just need to know how to fill it the network stuff to access the Ubuntus. If yours works with a GUI that would be great.
Here is the beta .deb for logmein
[https://secure.logmein.com/labs/#HamachiforLinux]("https://secure.logmein.com/labs/#HamachiforLinux")

---

### Post by cmcanulty on 2013-04-13
Oh that was sneaky I just figured out your app is a pay not open source after wasting an hour on it

---

### Post by The Spectre on 2013-04-13
> **cmcanulty said:**
> If yours works with a GUI that would be great.

It does Have a GUI...

[IMG]http://techbeat.com/wp-content/uploads/2013/03/Version-8-of-TeamViewer-for-Linux-Launched.jpg[/IMG]

---

### Post by The Spectre on 2013-04-13
> **cmcanulty said:**
> Oh that was sneaky I just figured out your app is a pay not open source after wasting an hour on it

Pay???

It is free if your not using in for commercial purposes.

I have been using it for years and it hasn't cost me a Penny.

I never said that it was Open Source and LogMeIn isn't Open Source either.

---

### Post by cmcanulty on 2013-04-13
sorry it said 15 days left on trial or buy

---

### Post by The Spectre on 2013-04-13
> **cmcanulty said:**
> sorry it said 15 days left on trial or buy

Which one did you download and install?

Maybe it automatically gives a trial of the non free version of TeamViewer just like LogMeIn does.

---

