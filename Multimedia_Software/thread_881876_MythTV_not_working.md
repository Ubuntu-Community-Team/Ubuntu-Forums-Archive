---
title: "MythTV not working"
date: 2008-08-06
forum: Multimedia Software
---

### Post by BiscuitTin on 2008-08-06
Having installed Ubuntu, I then downloaded and installed mythtv. Unfortunately when I start the frontend, it just says that No UPnP backends found. It then gpoes tp a config screen but all the details appear to be correct.

What's a UPnP backed and how do I ensure that it is running?

---

### Post by dannyboy79 on 2008-08-06
how did you install mythtv? are you sure that the mythbackend is gettting started when you start your system? you can see by issuing

ps aux | grep mythbackend

it should return results if you installed the backend correctly. Also, there is something I thought I read about being able to turn off the frontend looking for other uPNP seervers. Goggle it.

---

### Post by BiscuitTin on 2008-08-06
Installed it using the Ubuntu Applications | Add/Remove menu.

Doing a ps aux |grep mythbackend shows that there is one instamce of /usr/bin/mythbackend running.

---

### Post by dannyboy79 on 2008-08-06
check this post out.

[http://ubuntuforums.org/showthread.php?t=726680](http://ubuntuforums.org/showthread.php?t=726680)

---

### Post by BiscuitTin on 2008-08-07
Thanks for the link to the other post dannyboy. It seems that the mythconverg database was not created during the install. I also found some helpful info on how to create it here:

[http://www.mythtv.org/docs/mythtv-HOWTO-6.html](http://www.mythtv.org/docs/mythtv-HOWTO-6.html)

I created the database and ssigned the mythtv user access:

grant all on myhconverg.* to mythtv@localhost identified by "password";

I can now load up the myhtv application, but it still keeps cmplaining that it can't see the backend. The backend is running so I'm still puzzled.

---

### Post by dannyboy79 on 2008-08-07
is the backend and the frontend on the same machine? are the ip address's setup correctly? did you restart the backend after doing stuff?

sudo /etc/init.d/mythtv-backend restart

also, check this out

[https://help.ubuntu.com/community/MythTV](https://help.ubuntu.com/community/MythTV)

---

### Post by BiscuitTin on 2008-08-07
Ok, front-end and back-end are now 'talking' to one another. I found I needed to run mythtv-setup. As you mention, I then needed to run ./mythtv-backend start to get the back end up and running again.

Now we have got this far, does this thing actually work in the UK?
I couldn't see any UK settings when running the backend setup - I used west europe.

Problems still outstanding are;

1. Tuner is not recognised
2. Remote control is not working

For 1, the tuner is a hybrid DVB and analogue. I tried selecting the DVB option, but is seems not to be recognised.

For 2, I've installed lircd (apt-get install lirc) but still no joy. I'm having a look at the mythtv and lirc websites for further info. I have a Windows Media Centre remote (MCE20E) but I don't see this listed on the lirc site so it might not be supported.

---

### Post by dannyboy79 on 2008-08-07
you'll have to check around or subscribe to the mythtv mailing list and ask them about your tuner card. I have no idea about DVB cards.

---

### Post by NT4usB on 2008-08-07
Many DVB cards are not supported.
Have a look at the [Linux DVB wikki.]("http://www.linuxtv.org/wiki/index.php/Main_Page")

---

