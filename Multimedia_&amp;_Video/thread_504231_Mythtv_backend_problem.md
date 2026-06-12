---
title: "Mythtv backend problem"
date: 2007-07-18
forum: Multimedia &amp; Video
---

### Post by qazphilby on 2007-07-18
Hi  all,

Well i seem to have a problem with setting up my myth tv backend.  I had previously had a similar problem when if first installed ubuntu and mythtv, however i eventually got it to work, however i decided to redoo the full install as i had changed some hardware.

So the install ran smoothly however when i went into the mythbackend (after following instructions from [here]("https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend_Desktop"), and at capture cards i could not see my capture card. so if found that i had to add "sudo echo "cx88-dvb" >> /etc/modules" from [here]("http://www.mythtv.org/wiki/index.php/Leadtek_WinFast") 

so after a reboot, i could see that my leadtek dtv 1000 t was available in the capture cards, however once i set it all up and clicked finished, it was not in the list.

i don't know but think this may be a database error.  how do i fix this?

---

### Post by newlinux on 2007-07-19
If this is a new installation try reinstalling the database. I've seen this problem with database corruption. I have no idea what causes it.

```

sudo apt-get remove --purge mythtv-database mysql-server-5.0
sudo apt-get install mysql-server-5.0 mythtv-database

```

If that doesn't work, take a look at your mythbackend logs.

---

### Post by qazphilby on 2007-07-19
Cheers, that worked great.  Everything seems to be working fine except for mythweather and mythweb but will have a bit more of a look before i can post any specifics. thanks again

---

### Post by newlinux on 2007-07-19
glad it worked. mythweather is currently broken for all due to the data source (MSNBC) changing its web site. There is an beta workaround:

[https://help.ubuntu.com/community/MythWeather](https://help.ubuntu.com/community/MythWeather)

---

### Post by qazphilby on 2007-07-24
Well i found that there was a permission problem on the passwords file for mythweb so that is all full working, however with mythweather i have found that [http://svn.mythtv.org/svn/branches/mythweather-revamp/mythplugins](http://svn.mythtv.org/svn/branches/mythweather-revamp/mythplugins)  no longer exists so i can't get this work as explained
[here]("http://www.mythtv.org/wiki/index.php/Using_mythweather-revamp_with_trunk_mythtv")

---

