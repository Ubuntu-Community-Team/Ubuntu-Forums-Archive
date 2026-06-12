---
title: "How to run as mythtv"
date: 2007-09-12
forum: Multimedia &amp; Video
---

### Post by mkramer on 2007-09-12
I am trying to use [this script]("http://www.mythtv.org/wiki/index.php/Generatevideothumbs.pl") to generate thumbnails of my video collection.  Unfortunately I must run the script as user mythtv, and I cannot for the life of me figure out user mythtv's password.  I  This may be a silly question, but  what is it/how can I find out what it is?  (I'm not talking about the MySQL db password, but the user pw).

---

### Post by reckless2k2 on 2007-09-12
yikes....hahaha

simple kill....

sudo passwd mythtv

plug in your password then make a new mythtv password

BANG!!!!!!

did it work? mark it solved baby!!

---

### Post by mkramer on 2007-09-12
But how will mythtv know its own password when it tries to automatically log in?

---

### Post by reckless2k2 on 2007-09-12
huh? i thought you said you needed the mythtv passwd but forgot it or didn't know what it was. i just gave you the way to solve the mythtv passwd issue. 

is this something different?

---

### Post by mkramer on 2007-09-12
When I installed the MythTV frontend package, it automatically created a MythTV user and set it up to automatically log in (which I like, that's what I'm looking for).  However the package never asked me to specify a user password and never told me what it was using (it isn't blank).  Nor can I find that information in the MythTV wiki or google.

edit: and, though I want to run a script as user mythtv, I don't want to change mythtv's password in case it won't be able to login as mythtv anymore - unless you know how to also update the automatic login configuration?

---

### Post by rbm0307 on 2007-09-12
You could always include mythtv in the /etc/sudoers file with specific ability to only run that particular script.  Associate the NOPASSWD attribute with the entry.  That way, the script could be invoked with sudo and no need to provide the mythtv password.

- Robert

---

