---
title: "Import database from older different distro"
date: 2010-09-20
forum: Mythbuntu
---

### Post by lviperz on 2010-09-20
I've been running myth on fedora since 2005. Current version is FC7 with myth 0.20. Thinking about running mythbuntu. Can I import my old recordings and history from my old setup in to this new setup?

I know if I install FC13 and myth 0.23.1 I can import my old database and it will update for me when I run mythtv-setup. Will this work for mythbuntu? I really don't want to lose the recording history. I hate telling myth not to record a repeat if I've already watched it which is what I would have to do with a fresh install.

---

### Post by LowSky on 2010-09-20
I cant see why not, just copy the database and import it. All should work in theory

---

### Post by ian dobson on 2010-09-20
Hi,

Mythbuntu is nothing more than ubuntu with mythtv included, so actually importing/updating the database is no problem.

Regards
Ian Dobson

---

### Post by superm1 on 2010-09-20
> **ian dobson said:**
> Hi,

Mythbuntu is nothing more than ubuntu with mythtv included, so actually importing/updating the database is no problem.

Regards
Ian Dobson

A bit of an over simplification, but relevantly accurate for this scenario...

---

### Post by lviperz on 2010-09-20
Thanks everyone. I'll give it a go.

---

### Post by ian dobson on 2010-09-20
> **superm1 said:**
> A bit of an over simplification, but relevantly accurate for this scenario...

Hi superm1,

I know that mythbuntu is abit more than that, I didn't want to insult any of the project members. But in this case you can just treat mythbuntu as a ubuntu with mythtv and all the dependancies meet (including soft dependancies ie LIRC/codecs) and a nice configuration tool (mcc).

Regards
Ian Dobson

---

### Post by lviperz on 2010-09-21
Ok, I installed the latest mythbuntu 10.04 and everything worked fine. So I decided to import my old database from my Fedora 7 install with Mythtv 0.20. I dumped the current database, created a blank mythconverg and restored my old database.

I ran mythtv-setup and it converted my database. I went through the settings and adjusted as needed. Such as the IP and storage directories as well as the tuners.

When I started the frontend it asked to select a CD drive, so I did. Then it asked to upgrade the database for the video schema from 1016 to 1032. I said upgrade.

Problem is, it continues to ask for to select a CD drive and upgrade the video schema everytime. Any ideas?

---

### Post by lviperz on 2010-09-21
So I ran the control panel and removed all the plugin except MythWeb. I started the frontend and no upgrade prompts. I enabled each plugin one at a time. When I enabled MythMusic I was prompted for the CD drive again. So I went to setup for music and the cd device was default and I changed it to /dev/sr0, exited the frontend, went back in and that prompt was gone.

I then continued to enable one plugin at a time and left MythVideo for last. Once I enabled MythVideo my prompt to upgrade the database was back. So I tried to upgrade but it is telling me there is another client connected. This is a stand-alone box for the moment so it has to be a local client but I don't know what is connected? The backend?

I selected upgrade anyway and went to settings for video. I get prompted again to upgrade the database. I select upgrade, still get the message about other clients connected and should disconnect first. Select upgrade and get a message that failed to configure mythvideo.

So I assume the problem is in my database or permissions because another client in using the database. So how do I find who has the database locked? Or how do I wipe out the mythvideo settings. I thought removing the plugin would do that.

---

### Post by lviperz on 2010-09-21
Ok, solved the problem. I had to flush the old mythvideo tables and settings and restart the frontend and let it rebuild the schema. All fine now.

---

