---
title: "Can't get both tuners working..."
date: 2014-11-18
forum: Mythbuntu
---

### Post by mma8x on 2014-11-18
I've been having a problem getting 2 tuners working correctly within mythtv.  I originally had 2 Hauppauge 850 tuners.  Couldn't get them both working, just bought a HDHomerun dual, and am having similar problems.  I can occasionally get both tuners working at the same time, but just as often one won't work.  From within mythweb, it will either show a dotted line box around the second program without any explanation of why it isn't recording, or sometimes will show a red line and indicate that "Another program with a higher recording priority will be recorded." The recorder status at that time will only show one in use. First, I need to figure out the correct set up.  

Should I have 1 or 2 input sources?  Do I need different input groups? What else should I look for?

---

### Post by dannyboy79 on 2014-11-19
did you set up both tuners in mythtv-setup?  [https://www.mythtv.org/wiki/Silicondust_HDHomeRun_Dual#Setup_Instructions](https://www.mythtv.org/wiki/Silicondust_HDHomeRun_Dual#Setup_Instructions)

---

### Post by mma8x on 2014-12-02
Well, after struggling mightily I just decided to nuke my myth setup and sql and start again.  Unfortunately, in my haste I forgot that myth uses a goofy storage directory (why are my programs in /lib?) and deleted all of my recordings as well.  I reinstalled, and then spent the requisite 5 hours dealing with stupid sql permissions and what not.  Surprised how difficult it still is to install myth, even from scratch.  Anyway, finally got everything working correctly.  I have no idea what the problem was, since the setup I'm using now is identical to one that I'd already tried.  FWIW, the settings that are working for me:
1.  Both tuners set up separately
2.  One video source
3. 2 input connections, one for each tuner.  Each uses the same default video source.  
4.  Input groups (under input connection setting):  For each input connection (AKA tuner), input group 1 = the tuner name, and input group 2 is generic.  In other words, each input connection has a different value for input group 1.

HTH somebody...

---

### Post by dannyboy79 on 2014-12-02
what's the specific error

---

### Post by mma8x on 2014-12-03
Which error? Don't recall any errors thrown with the tuners, they just didn't work. Sql gave me a ton of errors, mostly dealing with incorrect passwords

---

### Post by Lester_Burnham on 2014-12-03
Hi,

I don't know if it's the right thing to do or not, but I always put all my tuners in the generic group.
As for SQL errors, normally on a fresh install, you don't really get any, but check the password in /etc/mythtv/config.xml and add it to the config.xml in your home directory ~/.mythtv/config.xml

Lester

---

### Post by tgm4883 on 2014-12-03
> **mma8x said:**
> Well, after struggling mightily I just decided to nuke my myth setup and sql and start again.  Unfortunately, in my haste I forgot that myth uses a goofy storage directory (why are my programs in /lib?) and deleted all of my recordings as well.  I reinstalled, and then spent the requisite 5 hours dealing with stupid sql permissions and what not.  Surprised how difficult it still is to install myth, even from scratch.  Anyway, finally got everything working correctly.  I have no idea what the problem was, since the setup I'm using now is identical to one that I'd already tried.  FWIW, the settings that are working for me:
1.  Both tuners set up separately
2.  One video source
3. 2 input connections, one for each tuner.  Each uses the same default video source.  
4.  Input groups (under input connection setting):  For each input connection (AKA tuner), input group 1 = the tuner name, and input group 2 is generic.  In other words, each input connection has a different value for input group 1.

HTH somebody...

So in other words what worked for you was proper setup.

---

