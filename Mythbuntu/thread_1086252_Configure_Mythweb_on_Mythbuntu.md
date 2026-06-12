---
title: "Configure Mythweb on Mythbuntu"
date: 2009-03-03
forum: Mythbuntu
---

### Post by brian_hayward on 2009-03-03
I bought a book a while back dealing with setting up MythTv on an Ubuntu system.  I read it and then i found Mythbuntu and installed that instead of installing MythTv on a Ubuntu system.  I tried to setup the MythWeb on my Mythbuntu system by following the book i bought and nothing is working out for me, but the version of Ubuntu and MythTv in the book are earlier than the versions i have installed on my system.  Is there something on the web that explains setting up MythWeb on Mythbuntu.  I looked in the installation guide for Mythbuntu on the web but the section for configuring MythWeb was empty.  Any help will be greatly appreciated here...Thanks.

---

### Post by theophile on 2009-03-04
I hope you didn't pay much. Printed books on Linux software are pretty much worthless because they're outdated before they come to market and the same (or better) information is available for free online.

We can probably help you with Mythweb but you're going to have to tell us what's wrong.

---

### Post by tgm4883 on 2009-03-04
What exactly is the problem that you need to configure mythweb?  You should be able to just "apt-get install mythweb" and it should be configured for you.

---

### Post by bigtdp on 2009-03-05
> **tgm4883 said:**
> What exactly is the problem that you need to configure mythweb?  You should be able to just "apt-get install mythweb" and it should be configured for you.

I always have a problem getting mythweb to work... don't know if the OP is having the same problem as I do, but it never "just works"... :(

the error I get when I go to the mythweb page via the web is:

```
Database Access Denied

You are most likely receiving this message because you
have failed to configure mythweb's database login info.

Please see INSTALL for instructions.
```

If this is the same problem you're having, then Mythbuntu probably has the wrong password for the MYSQL DB in the apache config files...

try:

```
less /etc/mythtv/mysql.txt
```

make a note of the password on the "DBPassword=" line

then: (you don't have to use vi, you can use gedit or nano or whatever your fave text editor is!!)

```
sudo vi /etc/apache2/sites-available/mythweb.conf
```

In mine, the "setenv db_password" password was blank, just ""

I entered the password I found in mysql.txt between the ""'s and saved the file. All I needed to do to get it working was:

```
sudo /etc/init.d/apache2 restart
```

went back to the webpage and it worked!! :D

just noticed, when you set the password using the mythbuntu control panel, it clears the password in mythweb.conf again, so prolly worth doing this first!!

I just checked on the mythtv fault reports - seems this was first identified as Bug #221532 back in April last year :( 

[https://bugs.launchpad.net/mythbuntu/+bug/221532](https://bugs.launchpad.net/mythbuntu/+bug/221532)

***** as I always say on this forum, I may well not be doing this right, but it works... if someone can elaborate or make a different suggestion, please do - I'm no linux/mythtv expert by any stretch of the imagination! *****

:D

xTx

---

### Post by gidsmyth on 2009-08-28
G'day all
 
I too am having difficulty configuring mythweb. 
The most important part for me is the ability to remotely setup and manage recordings and this bit works fine, albeit that it appears as just
 
 
[CENTER][IMG]http://192.168.2.4/mythweb/skins/default/img/mythtv-logo.gif[/IMG]
[Listings]("http://192.168.2.4/mythweb/tv/list")
[Upcoming Recordings]("http://192.168.2.4/mythweb/tv/upcoming")
[Recorded Programs]("http://192.168.2.4/mythweb/tv/recorded")
[Backend Status]("http://192.168.2.4/mythweb/status")[/CENTER]
 
 
 
On all machines other than my WM6.1/Opera device the MythTv logo appears as above (ie graphic X), so I'm thinking that it might be a skin problem but I'm not sure. Anyway I do want the full functionality of streaming my recordings/music etc. Can anyone advise a numpty how to start?
 
I'm running Mythbuntu 9.04 and installed mythweb via
 
sudo apt-get install 
 
as I want to be able to run torrent flux on this machine as well (torrentflux installed but not configured yet)
 
Thanks!

---

### Post by joshoekstra on 2009-08-31
> **gidsmyth said:**
> G'day all
 
I too am having difficulty configuring mythweb. 
The most important part for me is the ability to remotely setup and manage recordings and this bit works fine, albeit that it appears as just
 
 
[CENTER][IMG]http://192.168.2.4/mythweb/skins/default/img/mythtv-logo.gif[/IMG]
[Listings]("http://192.168.2.4/mythweb/tv/list")
[Upcoming Recordings]("http://192.168.2.4/mythweb/tv/upcoming")
[Recorded Programs]("http://192.168.2.4/mythweb/tv/recorded")
[Backend Status]("http://192.168.2.4/mythweb/status")[/CENTER]
 
 
 
On all machines other than my WM6.1/Opera device the MythTv logo appears as above (ie graphic X), so I'm thinking that it might be a skin problem but I'm not sure. Anyway I do want the full functionality of streaming my recordings/music etc. Can anyone advise a numpty how to start?

If you go to this adress or any adress of your mythweb-server like this:
[http://192.168.2.4/mythweb/status?RESET_TMPL=yes](http://192.168.2.4/mythweb/status?RESET_TMPL=yes)
It will reset the template, which is the mobile one. It's a apache/mythweb buggie which has been around for some time(dunno if it still happens with .22).

---

