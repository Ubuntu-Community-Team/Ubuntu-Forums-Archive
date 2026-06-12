---
title: "When do they start with daily builds?"
date: 2010-05-08
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by ranch hand on 2010-05-08
I can't for the life of me remember when the dailies started being posted.

I am a little excited about it as I am going to try having a separate /var partition.  I have read about reasons for separate partitions for just about everything and most just seem silly.  The /var seems to make some sense if you need to reinstall.

Seeing that it may come down to reinstalling at some point in this cycle I think this is the time to give this a whack.  Might not ever use it on a stable install but I have to try it.

Thus the interest in the Daily Build timing.

---

### Post by Slug71 on 2010-05-08
IRC from Alpha 1.

---

### Post by ranch hand on 2010-05-08
I thought it was about 2 weeks before A1 so that they had some practice before the need to ISO test for A1.  That testing would be Monday of Tuesday before A1s release.

Ah well, I suppose we will find out.

---

### Post by kansasnoob on 2010-05-08
I think iso-testers get the very first one just before Alpha 1.

Anyone else notice that there's only one Beta coming in Maverick?

I'm thinking that's a good choice.

That means 7 rounds of iso-testing:

A-1
A-2
A-3
A-4
Beta
RC
Final

I love iso-testing, but every time I end up feeling like I should have done just a little better.

---

### Post by ranch hand on 2010-05-08
It really is a lot of fun.

It is even more fun if the dailies have everyones knickers in a knot but the test ISO is working great.

My only clean installs have come from the test ISOs.

---

### Post by eyelessfade on 2010-05-08
> **ranch hand said:**
> I have read about reasons for separate partitions for just about everything and most just seem silly.  The /var seems to make some sense if you need to reinstall.

Silly if its your desktop, not if its a server. Partitions insure that even if one part of the systems gets full it doesn't drag the system down.
/var/log is a great sinner. A server might get several gigabytes of logs each day. Other on the top of my head. /var/mail, /var/www, /usr/local if you have some other maintaining local files. Perhaps a /backup og /var/backup so you don't have to monitor that to closely (I rsync several virtual machines into one physical and then use tivoli to backup that one.) /boot since that is the most important files for boot :) and don't forget /home other then that depends what you run on it. one where the database is stored if you want it on a really fast drive?

---

### Post by ratcheer on 2010-05-10
Ranch Hand, I have a testing partition with Lucid beta installed. Please tell me how to upgrade it to 10.10 before the CD images become available.

Thank you,
Tim

---

### Post by philinux on 2010-05-10
Edit your sources list. Replace lucid with maverick then ```
sudo apt-get update && sudo apt-get upgrade
```.

---

### Post by ranch hand on 2010-05-10
Pretty simple really.  It is the traditional Debian way of upgrading.

Simply run;
```

gksudo gedit /etc/apt/sources.list

```
and change every instance of "lucid" to "maverick".  Run;
```

sudo apt-get update

```
and;
```

sudo apt-get dist-upgrade

```
You will need to edit the /user/share/python-apt file when finished to read "maverick" and "10.10" and "Maverick Meercat" in the first section after you finish or some things like the Software Sources will not work.

---

### Post by ratcheer on 2010-05-10
Thanks, Ranch Hand and philinux. I'm off to a new adventure!

Tim

---

### Post by ranch hand on 2010-05-10
There is no reason to hog all the FUN for just us.  I am sure that you too can break things.

---

### Post by taavikko on 2010-05-10
> **ranch hand said:**
> Pretty simple really.  It is the traditional Debian way of upgrading.

Simply run;
```

gksudo gedit /etc/apt/sources.list

```
and change every instance of "lucid" to "maverick".  Run;
```

sudo apt-get update

```
and;
```

sudo apt-get dist-upgrade

```
You will need to edit the /user/share/python-apt file when finished to read "maverick" and "10.10" and "Maverick Meercat" in the first section after you finish or some things like the Software Sources will not work.

Traditional way is to use "sed"
```
sed -i 's/lucid/maverick/g' /etc/apt/sources.list && sudo aptitude update && sudo aptitude full-upgrade
```

---

### Post by VMC on 2010-05-10
> **taavikko said:**
> Traditional way is to use "sed"
```
sed -i 's/lucid/maverick/g' /etc/apt/sources.list && sudo aptitude update && sudo aptitude full-upgrade
```

Yes it is! I lost. Thanks taavikko for the reminder!

---

### Post by ranch hand on 2010-05-10
This is true.  When I do that I, invariably, leave things like back ports uncommented and ppas uncommented that have no maverick repo yet.  I just prefer to go in and see the stuff myself.

That way I know who to blame.

---

### Post by ratcheer on 2010-05-10
> **ranch hand said:**
> There is no reason to hog all the FUN for just us.  I am sure that you too can break things.

Ok, I have MM installed in my testing partition. There were three broken packages that were subsequently removed by aptitude (gnome-desktop and tomboy, I forget the third one) but everything seems to work. For now, I am keeping it simple by sticking with the nouveau driver.

Man, does MM boot and start the desktop fast!

Thanks again,
Tim

---

### Post by taavikko on 2010-05-10
> **ratcheer said:**
> Ok, I have MM installed in my testing partition. There were three broken packages that were subsequently removed by aptitude (gnome-desktop and tomboy, I forget the third one) but everything seems to work.

Read the sticky about partial upgrades.
Use "sudo aptitude update && sudo aptitude safe-upgrade"

---

### Post by afv on 2010-05-10
> **ratcheer said:**
> […]
Man, does MM boot and start the desktop fast!

Thanks again,
Tim

Should be no different than LL at the moment. :)

---

### Post by ratcheer on 2010-05-10
> **taavikko said:**
> Read the sticky about partial upgrades.
Use "sudo aptitude update && sudo aptitude safe-upgrade"

That is what I did. Then I ran "sudo aptitude keep-all", then another update. That is where I hit the broken packages and removed them.

Tim

---

### Post by ratcheer on 2010-05-10
> **afv said:**
> Should be no different than LL at the moment. :)

Well, it seems a lot faster to me. I will try timing it, next time.

Tim

---

### Post by philinux on 2010-05-10
> **ratcheer said:**
> Well, it seems a lot faster to me. I will try timing it, next time.

Tim

Bootchart!!

[[COLOR="Red"]**apt:bootchart**[/COLOR]]("apt:bootchart")

---

### Post by taavikko on 2010-05-10
> **ratcheer said:**
> That is what I did. Then I ran "sudo aptitude keep-all", then another update. That is where I hit the broken packages and removed them.

Tim

There's hardly ever need to use keep-all, which caused you to have a partial upgrade.

Just re-install "ubuntu-desktop" to ensure you have the version canonical wants means it to be.

---

### Post by ratcheer on 2010-05-11
> **taavikko said:**
> There's hardly ever need to use keep-all, which caused you to have a partial upgrade.

Just re-install "ubuntu-desktop" to ensure you have the version canonical wants means it to be.

I ended up by just reinstalling Lucid clean from CD image, updating and upgrading it to current, then changed apt sources to Maverick and updated and dist-upgraded, again. It still complained about the three incompatibilities, but did not remove the packages. I guess I am where I should be.

Thanks,
Tim

---

### Post by ranch hand on 2010-05-11
You will find that the packages do not get to the repo in the proper order.  This is why many are held back.  Wait a day or two and they will go fine.

Kernel updates will be held back because of files being added however.  This generally do need upgraded.

The safe thing to do is go to synaptic and see why packages or e held back.

It is also a good thing to read the stickies.  This one for example may be a good one for you to start on;

[http://ubuntuforums.org/showthread.php?t=1479146](http://ubuntuforums.org/showthread.php?t=1479146)

---

### Post by kansasnoob on 2010-05-11
I just noticed that the package list is not even available for Maverick yet:

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

Click on Maverick :)

I know patience is a virtue, but I'm not at all virtuous :P

---

### Post by ranch hand on 2010-05-11
You need to edit the /usr/share/python-apt/templates/Ubuntu.info file to have a section for maverick.

---

### Post by taavikko on 2010-05-11
> **ranch hand said:**
> You need to edit the /usr/share/python-apt/templates/Ubuntu.info file to have a section for maverick.

No you don't, python-apt is already been updated to include this info.
python-apt 0.7.94.2ubuntu7
```
* data/templates/Ubuntu.info.in:
    - add maverick
```

---

### Post by ratcheer on 2010-05-11
> **taavikko said:**
> No you don't, python-apt is already been updated to include this info.
python-apt 0.7.94.2ubuntu7
```
* data/templates/Ubuntu.info.in:
    - add maverick
```

Yes, I went to edit mine and it is already there.

Tim

---

### Post by xebian on 2010-05-13
Just changed mine to maverick and today got 158 upgrades and 1 new install.:guitar:

---

