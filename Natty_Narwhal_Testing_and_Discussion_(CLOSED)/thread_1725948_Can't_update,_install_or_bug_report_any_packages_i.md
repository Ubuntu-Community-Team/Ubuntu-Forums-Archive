---
title: "Can't update, install or bug report any packages in Natty 64-bit beta"
date: 2011-04-10
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by krippa on 2011-04-10
Hi,

I really want to help out in the beta testing progress but it seems I have found a bug that's pretty much impossible to report. I can't install or update any packages, which by extension means i cannot file any bug reports since I don't have the latest version of the packages. 

What do I do to report this bug?

I have:
A pretty much fresh natty beta1 install. 64-bit.
A Dell Studio XPS 16

When I try updating manually (even after switching mirrors) I get the following:
$ sudo apt-get update
Ign [http://ftp.df.lth.se](http://ftp.df.lth.se) natty InRelease
Hit [http://ftp.df.lth.se](http://ftp.df.lth.se) natty Release.gpg
Hit [http://ftp.df.lth.se](http://ftp.df.lth.se) natty Release
Get:1 [http://ftp.df.lth.se](http://ftp.df.lth.se) natty/main amd64 Packages [1,557 kB]
Get:2 [http://ftp.df.lth.se](http://ftp.df.lth.se) natty/universe amd64 Packages [6,010 kB]
Get:3 [http://ftp.df.lth.se](http://ftp.df.lth.se) natty/restricted amd64 Packages [9,027 B]
Get:4 [http://ftp.df.lth.se](http://ftp.df.lth.se) natty/multiverse amd64 Packages [180 kB]
Ign [http://ftp.df.lth.se](http://ftp.df.lth.se) natty/main TranslationIndex      
Ign [http://ftp.df.lth.se](http://ftp.df.lth.se) natty/multiverse TranslationIndex
Ign [http://ftp.df.lth.se](http://ftp.df.lth.se) natty/restricted TranslationIndex
Ign [http://ftp.df.lth.se](http://ftp.df.lth.se) natty/universe TranslationIndex
Ign [http://ftp.df.lth.se](http://ftp.df.lth.se) natty/main Translation-en_US
Ign [http://ftp.df.lth.se](http://ftp.df.lth.se) natty/main Translation-en
Ign [http://ftp.df.lth.se](http://ftp.df.lth.se) natty/multiverse Translation-en_US
Ign [http://ftp.df.lth.se](http://ftp.df.lth.se) natty/multiverse Translation-en                       
Ign [http://ftp.df.lth.se](http://ftp.df.lth.se) natty/restricted Translation-en_US                    
Ign [http://ftp.df.lth.se](http://ftp.df.lth.se) natty/restricted Translation-en                       
Ign [http://ftp.df.lth.se](http://ftp.df.lth.se) natty/universe Translation-en_US                      
Ign [http://ftp.df.lth.se](http://ftp.df.lth.se) natty/universe Translation-en                         
Fetched 7,756 kB in 7s (1,026 kB/s)                                            
Reading package lists... Done

---

### Post by krippa on 2011-04-10
If anyone else has this problem it seems like the software sources and update options got all messed up for some reason. I have no idea how they got de-selected but after going in there and ticking the right stuff i got updates to work again.

---

