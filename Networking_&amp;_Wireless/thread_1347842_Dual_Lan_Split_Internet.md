---
title: "Dual Lan Split Internet"
date: 2009-12-06
forum: Networking &amp; Wireless
---

### Post by verbuyst on 2009-12-06
Hi,

I have a GA-EX58-UD5 motherboard and it has a dual lan connection. What I don't need is to bridge the connection and use it for a very fast internet.

I have a fast Cable connection on eth0 and I have a slower ADSL connection with eth1.

What I do want to do is:
Use connection 1 (eth0) for only internet use (like firefox, internet explorer)
Use connection 2 (eth1) for dowload use (like flashget, IDM)

I have used google, but I can only find people that want to bridge the connection to have a faster internet, but I dont need that. I want to be able to download with IDM on my slow ADSL and still have fast internet with my cable.

I have found an app that is capable to select what ethernet port it should use: Vuze (it's a torrent client, witch I don't need but it does what I would like to do => Select what interface to use eth0 or eth1)
[IMG]http://kakku.files.wordpress.com/2008/02/screenshot-azureus.jpg[/IMG]

So is this also possible in other apps or with the use of something like this:
[http://www.r1ch.net/stuff/forcebindip/](http://www.r1ch.net/stuff/forcebindip/)
But with a grafical interface ;-)

Now I use Windows 7 X64 Ultimate but I am willing to create a multi-boot with Ubuntu IF it is easy to creat a rule or something like that to select what app uses what ethernet interface and working under Ubuntu. I have used Ubuntu 9.04 but switched back to Windows because I just needed some windows apps at that time.

---

### Post by verbuyst on 2009-12-07
I have found the solution, this is the app (without grafical layout) but it does what I want.
[ForceBindIP - Bind any Windows application to a specific interface]("http://www.r1ch.net/stuff/forcebindip/")

I only created a *.bat file and created a shortcut to it on my desktop if I want to run a program on a specific eth-port.

So if anybody has this problem I can assure you that it works like a charm.

Example of a *.bat file:
ForceBindIP -i {9EF71B38-9648-4E29-B752-4561455AFBF4} "C:\Program Files (x86)\Download\Firefox\firefox.exe"

the {*-*-*-*} is the name of my eth0-port (dynamic range) you only need to change this to the other name of the eth1-port if you want Firefox to use the other Port.

So that was the solution for Windows 7 X64, but what about Ubuntu?
I have VMware running a Ubuntu 9.10 release to figure this one out on my own, but hasn't anybody else try to do this?

---

### Post by kingwooky on 2010-07-05
I have the same problem but on Ubuntu. I have been trying to bind the ip of quamachi to starcraft so I can play lan against my friends. If you have any programs that bind ip's to programs. Or codes I can put into the terminal it would be appreciated.

---

