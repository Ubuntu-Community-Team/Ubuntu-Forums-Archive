---
title: "How to install mythbuntu onto new vivid install?"
date: 2015-06-07
forum: Mythbuntu
---

### Post by yonkiman on 2015-06-07
I've been running mythbuntu 0.28 / 14.04 for a while.  Now I've installed 15.04 and would like to migrate my database to it.  However I haven't been able to get a clean/working myth setup under 15.04 to migrate to.  I tried adding the mythbuntu 0.28 ppa, installing mythbuntu-control-centre, and trying to use mythbuntu-control-centre to install and get a basic mythtv setup running.  But that didn't work - I could never get past the endless front end config screen or a working backend, etc.  I messed around with that for a while and didn't get anywhere.  I also looked at the many tutorials on how to install mythtv (without mythbuntu), but couldn't get myth up and running that way, either (though I may have hosed something while I was experimenting).   

So I gave up on that install and reinstalled a brand spanking new 15.04 system and the 0.28 ppa.  Here are some of the mythbuntu-specific programs:
> mythbuntu-bare-client mythbuntu-bare-console, mythbuntu-common, mythbuntu-control-centre, mythbuntu-default-settings, mythbuntu-desktop         

mythbuntu-bare-client/console sounds promising, but I can't find any documentation on what it does.  mythbuntu-default-settings sounds useful, but at what point is it loaded?  Is there one program I can install that will pull in everything else it needs?  I thought that would be mythbuntu-control-centre, but as I said above, it didn't seem to work.

Does anyone have any suggestions on what I should install in what order to bring up a happy mythbuntu/mythtv system?

---

### Post by hollywoodpete on 2015-06-07
My answer will be no help but to really have a happy system, install 14.04 via mythbuntu and .27. It will save you a lot of wasted time and frustration. LTS releases handle quirky programs like Myth best. If you have to ask how to install on 15.04 and .28, you will pretty much be on your own.

---

### Post by yonkiman on 2015-06-07
> **hollywoodpete said:**
> My answer will be no help but to really have a happy system, install 14.04 via mythbuntu and .27. It will save you a lot of wasted time and frustration.

Thanks Pete.  My current system actually *is* mythbuntu 14.04, though with .28, not .27.  However mythtv .28 has been working stably and beautifully for a long time, more than a year I think.  I know there are warnings galore about 0.28 from the developers, and it's better to be safe/conservative than sorry, but the devs have been doing a really good job and I'd like people who are staying away because of the warnings to know that.  I'm not recommending people switch - just want to give the developers some props.

My problem has been with the ubuntu desktop part of mythbuntu 14.04.  I use my system for a lot more than mythtv, but several big things that should work (and would work with a vanilla 14.04 or 15.04 install) don't work with my system.  This may be my fault - maybe something got hosed somewhere in my system, but there are lots of big/little annoying things don't work right (like gedit not having write permission on any directory unless launched with gksu) that a clean install would fix.  I've spent a lot of time trying to fix them and a lot of people on various forums have tried to help, but  at this point I think the best thing for everyone would be to do a clean install.  I could reinstall mythbuntu 14.04, but thought I might as well start with a later version with better btrfs support, etc.

>  LTS releases handle quirky programs like Myth best. If you have to ask how to install on 15.04 and .28, you will pretty much be on your own.

Perhaps.  Still hoping someone familiar with mythtv/mythbuntu can give me a tip or two, and I can take it from there.  

Cheers,
Fred

---

### Post by yonkiman on 2015-06-07
Update:  I retried the basic "sudo apt-get install mythtv", which seemed to install everything with no errrors.  But when I run mythtv-setup, I find myself stuck in the "MythTV could not connect to the database" endless loop.  I've tried localhost and my PC's actual address, I've tried password "mythtv" and the password I entered earlier when it was installing mysql - none of those seem to work...  I think maybe mysql isn't running, but "sudo /etc/init.d/mysql start" doesn't help.

So I guess my basic question is, regardless of myth or ubuntu version, what does one need to do after "sudo apt-get install mythtv" to get the backend happily talking to the mythconverg database?

---

### Post by blm-ubunet on 2015-06-09
mysql is started by upstart, the correct cmd is:
```
sudo initctl start mysql
```
In the above you can sub "status" or "stop" for "start"

mythbackend could/should be upstart (is here because of manual install).
Both could possibly have moved on to using systemd ?

Test your mysql connection
```
mysql -umythtv -p mythconverg
```
type "quit" to exit

Then once you know the password is right make sure mythtv can read that from the config.xml file.
This file can be in multiple places & different users look in different locations.

Mythtv backend runs as user "mythtv" & so it looks for /home/mythtv/.mythtv/config.xml or /etc/mythtv/config.xml.

If you run frontend as a different user then it (FE) will look in /home/<user>/.mythtv/config.xml or then /etc/mythtv/..

You can symlink (2) of the files to same file/location to make things tidier.

---

