---
title: "problem installing flash plaeyr square preview"
date: 2011-06-13
forum: Multimedia Software
---

### Post by guardacaccia on 2011-06-13
I wonder if anyone could help me with this issue. I tried to download and install flash player square preview release to my computer, but I came across a problem which I can't solve myself and couldn't find any quick answers from web posts either.
So, the downloading was fine and I got the tar.gz file to my downloads file after which I untarred the file and the file opened as a .so-file. I've never used this kind of files before as I'm rather new to Ubuntu anyhow and now I have no clue what so ever of how to deal with this .so-file to get my hands on the flash player square release and get it working.

I would be very grateful for an answer to my little problem. Or if there's any other way of installing flash player or other program which would play internet radio..?

---

### Post by kc1di on 2011-06-13
Hi guardacaccia,

I would make a file in your home folder and move or copy the .so file to it call the folder flash or something similar.

Now it's just a matter of linking this file to the proper file in your /usr/lib64 directory.

Since your trying to install flash square I'm assuming your doing this on a 64 bit system.

open up your file manager and go to filesystem >usr>lib64>mozilla>plugins  see if you have any libflashplayer.so files already installed. if you do you'll need to remove it. (Note **you'll have to do this a root.)**

Next copy the file from your /home/(User Name)/flash folder 
it sould be libflashplayer.so to the /usr/lib64/mozilla/plugins 
that it restart your browser and see if it works for you.

**(Note: again you'll have to be root to do all this) **
or your can do it from a terminal with the sudo command.

hope this helps 
Dave
P.S. This article may also be of Help.
[http://nxadm.wordpress.com/2009/04/26/install-64-bit-adobe-flash-player-on-ubuntu-904/]("http://nxadm.wordpress.com/2009/04/26/install-64-bit-adobe-flash-player-on-ubuntu-904/")

---

### Post by guardacaccia on 2011-06-13
Thanks for your help Dave! I'll try this one and if it doesn't work I'll read the article you linked and maybe I'll find the answer from there.

---

### Post by Yellow Pasque on 2011-06-13
I'm not sure where this user said they're running 64-bit, and if s/he is, SevenMachines' PPA is the best way to get the latest Flash: [https://launchpad.net/~sevenmachines/+archive/flash](https://launchpad.net/~sevenmachines/+archive/flash)

---

### Post by lovinglinux on 2011-06-15
Install [Flash-Aid](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/) and run the extension wizard. It will detect installed flash plugins, remove them and install the best option according to your system architecture and version. Additionally, it will apply some tweaks that should improve performance.

---

