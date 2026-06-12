---
title: "Aventail VPN on Jaunty (9.04)"
date: 2009-06-11
forum: Networking &amp; Wireless
---

### Post by Cavillis on 2009-06-11
I have successfully installed Aventail on Ubuntu with no errors, but I cannot connect to my company's network. I know our VPN accepts connections from linux because other people here have it working with Fedora. MY error is that whenever I type in the hostname, I get a 'Connection Failed' error. I can successfully ping the hostname so I don't understand why Aventail won't connect. 

Is there anyone here who has been successful with Aventail on Ubuntu that can help me out?

A possible problem (all of the following also applies to libcrypto.so.0.9.7): Aventail looks for libssl.0.9.7, but I could not find 0.9.7 to install on Ubuntu. I created a symlink called libssl.0.9.7 that points to libssl.0.9.8. Could this be the problem? If so, where can I get libssl.0.9.7?

---

### Post by Cavillis on 2009-06-11
It seems just as I was giving up, I found the solution! I shall post my process here so others can find it:

The problem was the libssl version 0.9.8. My problem was solved after installing 0.9.7 which I finally found here 
[http://packages.debian.org/search?keywords=libssl0.9.7](http://packages.debian.org/search?keywords=libssl0.9.7)

On top of installing that library, I had to change the first line of all the .sh files in the Aventail directory (/usr/local/Aventail for me). Where it said #!/bin/sh, I had to change it to #!/bin/bash

These should solve anyones problem, as long as you have a recent version of Java. I tried a multitude of solutions in my 3 day journey trying to solve this, i'll be happy to help anyone who posts here or sends me a private message.

---

### Post by spaleo on 2009-06-18
Hi 

 I installed the libssl.so.0.9.7, following the link, BUT ldd gives 
the following message 

	linux-gate.so.1 =>  (0xffffe000)
	libpthread.so.0 => /lib32/libpthread.so.0 (0xf7f5f000)
	libssl.so.0.9.7 => not found
	libcrypto.so.0.9.7 => not found
	libm.so.6 => /lib32/libm.so.6 (0xf7f39000)
	libc.so.6 => /lib32/libc.so.6 (0xf7dea000)
	/lib/ld-linux.so.2 (0xf7f8e000)

I tried to use getlibs

getlibs AvConnect

with the error message

No match found for package libcrypto.so.0.9.7
No match found for package libssl.so.0.9.7
No libraries to download.


anyone had similar troubles?

---

### Post by abbandon on 2009-08-04
Hi, all
Just follow this [[COLOR="RoyalBlue"]guide[/COLOR]]("http://just-another.net/2008/11/20/ubuntu-intrepid-and-aventail-ssl-client/") 

it works for me since 8.10, as well as 9.04

good luck !

---

### Post by connermcd on 2009-11-05
Finally got it working using Benjamin's guide - thanks!

---

### Post by kmsiva on 2010-11-20
The link is not working anymore. I am trying to install Aventail. Request your help with link or material


> **abbandon said:**
> Hi, all
Just follow this [[COLOR="RoyalBlue"]guide[/COLOR]]("http://just-another.net/2008/11/20/ubuntu-intrepid-and-aventail-ssl-client/") 

it works for me since 8.10, as well as 9.04

good luck !

---

