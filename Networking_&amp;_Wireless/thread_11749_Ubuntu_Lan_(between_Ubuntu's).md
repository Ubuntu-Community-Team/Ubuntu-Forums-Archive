---
title: "Ubuntu Lan (between Ubuntu's)"
date: 2005-01-19
forum: Networking &amp; Wireless
---

### Post by Brian on 2005-01-19
Hi 

I Installed Ubuntu on 2 computeres, 
and i would like to be able to tranfer files between them, 
i would perfer in some grapical way 

thanks in advance

Regards 

Brian (from Denmark)

---

### Post by hardcandy on 2005-01-19
Have you had a look at the Howto/FAQ forum? Have you looked through any documentation at all?  Google is your friend.  :wink:

---

### Post by Buffalo Soldier on 2005-01-19
Please read the Unofficial Ubuntu 4.10 Starter Guide at [http://ubuntuguide.org](http://ubuntuguide.org)

The networking section covers some, if not most of what you need:

1. How to configure network connections?
2. How to change computer name?
3. How to change computer descriptions?
4. How to change computer Domain/Workgroup?
5. How to access network folder without mounting?
6. How to mount/unmount network folder manually?
7. How to mount/unmount network folder manually, and allow all users to read/write?
8. How to mount network folder on boot-up?
9. How to mount network folder on boot-up, and allow all users to read/write?

[http://ubuntuguide.org/#networking](http://ubuntuguide.org/#networking)

---

### Post by Brian on 2005-01-19
Hi Tanks fore the Answers

it works now but new problems has emerged

i am able to tranfer files, but only a few 
and then the tranfer stops or crashes

---

### Post by 3spades on 2005-01-19
have you tried ftp? install vsftpd and gftp on both and ftp into the other to dl/ul files.
sudo apt-get install vsftpd
sudo apt-get install gftp

or open up synaptic and find & install em from there

---

