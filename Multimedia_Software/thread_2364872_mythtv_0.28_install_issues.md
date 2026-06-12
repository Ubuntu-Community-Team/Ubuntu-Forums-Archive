---
title: "mythtv 0.28 install issues"
date: 2017-06-29
forum: Multimedia Software
---

### Post by phillip9 on 2017-06-29
hello forum i hope someone can help me out i am using Ubuntu 16.04 lts and trying to install and run MYTHTV which has in the past worked for me but at the moment i am getting all sorts of issues even thought MYTHTV installs fine as soon as i run MYTHTV-SETUP the horrible window asking for country comes up i do that and it is like in a loop but when i look at the terminal window i see the following messages 

Couldn't open /etc/mythtv/config.xml:
Permission denied at /usr/share/perl5/XML/SAX/Expat.pm line 75.
XML::Simple called at -e line 5.
Couldn't open /etc/mythtv/config.xml:
Permission denied at /usr/share/perl5/XML/SAX/Expat.pm line 75.
XML::Simple called at -e line 5.
Couldn't open /etc/mythtv/config.xml:
Permission denied at /usr/share/perl5/XML/SAX/Expat.pm line 75.
XML::Simple called at -e line 5.
Couldn't open /etc/mythtv/config.xml:
Permission denied at /usr/share/perl5/XML/SAX/Expat.pm line 75.
XML::Simple called at -e line 5.


does anyone know why this is happening or know what or where the issue lies please let me know thanks or any help would be greatly appreciated thanks in advance

---

### Post by wildmanne39 on 2017-06-29
*Thread moved to **Multimedia Software**.*

---

### Post by MoebusNet on 2017-09-16
If you're still stuck -

I ran into the same installation loop as you, could never get past the initial country, etc. screens. This is what worked for me:

The default password on Ubuntu for the mythtv database isn't mythtv.

Check the '/etc/mythtv/config.xml' file. The password will be there. Example:

```
 gedit /etc/mythtv/config.xml 
```

Copy down the username & password that is in the file. You can go ahead and close gedit (or whatever text editor you used) and the terminal; you can always reopen if needed. Now start Mythtv Backend Setup and use the username and password you copied from the '/etc/mythtv/config.xml' file.

Alternatively, if youu want to use a different username and password for the mythtv database, you can
Code:

```
 gksudo gedit /etc/mythtv/config.xml 
```

and change the username and password as desired. Save the changes in gedit (or whatever text editor), close everything and use that username & password for Mythtv Backend Setup.

I just used the default username and the random password assigned by Ubuntu's mythtv package. It all worked from there. Make sure you at least set up the Default Storage Group, or it still won't work: [https://www.mythtv.org/wiki/Configuring_MythTV](https://www.mythtv.org/wiki/Configuring_MythTV)

---

