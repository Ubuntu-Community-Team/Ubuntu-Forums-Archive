---
title: "Missing Recordings...but still on Hard Drive"
date: 2008-12-01
forum: Mythbuntu
---

### Post by CGW on 2008-12-01
Hello all:

Questions:  I've performed several scheduled recordings.  Myth is recording the programs like instructed.  However, when I go to 'Media Library' and select 'Watch Recordings' they're missing.  The only recordings that are showing up are LiveTV recordings.  

For example: If I watch Live TV the subsequent videos are present in the 'Media Library.'  However, if I schedule a recording say 9pm-10pm Myth records it but it does not appear in the 'Media Library.'  However, if I access the recordings folder through the network or via the PC after exiting MythTV, the recordings are in the recordings folder.

Any suggestions??

Thanks in advance.

BTW, I'm running Mythbuntu 8.04.

---

### Post by Caps18 on 2008-12-02
Have you tried restarting it?  That seems to clear about half the problems I have.  Also, make sure you have enough hard drive space (you should if it is properly recording still).

If that doesn't work, look at the log files to see if there is an important error message or something.

You may need to look around here for the commands to use in order to fix or repair the database

---

### Post by SiHa on 2008-12-02
Live TV, by default, shouldn't display in the Watch Recordings list. I'm guessing your group filters have been changed somehow.

I'm at work now, so I can't remember the specifics but here goes.

In the Watch Recordings list, press Menu, there should be a 'change group filter' option, or something. If you select that, select 'default' if it's available - your recordings should be in there. 

Assuming they are there, you need to go to the TV playback settings, and somewhere in there is the options for the Watch Recordings screen. 'Include Live TV in list' should be unchecked, and 'starting group' you probably want set to 'default'.

If they're not there then, sorry, I don't know.

Do the recordings appear in Mythweb?

---

### Post by CGW on 2008-12-02
> **Caps18 said:**
> Have you tried restarting it?  That seems to clear about half the problems I have.  Also, make sure you have enough hard drive space (you should if it is properly recording still).

If that doesn't work, look at the log files to see if there is an important error message or something.

You may need to look around here for the commands to use in order to fix or repair the database

It's been restarted many, many times.  Hard drive space is also not a problem.  I haven't checked any logs yet...but I will.

> **SiHa said:**
> Live TV, by default, shouldn't display in the Watch Recordings list. I'm guessing your group filters have been changed somehow.

I'm at work now, so I can't remember the specifics but here goes.

In the Watch Recordings list, press Menu, there should be a 'change group filter' option, or something. If you select that, select 'default' if it's available - your recordings should be in there. 

Assuming they are there, you need to go to the TV playback settings, and somewhere in there is the options for the Watch Recordings screen. 'Include Live TV in list' should be unchecked, and 'starting group' you probably want set to 'default'.

If they're not there then, sorry, I don't know.

Do the recordings appear in Mythweb?

LiveTV is coming up under 'Watch Recordings.'  I don't recall changing any group settings but I will check it out when I get home tonight.  Also, I never thought to look in Mythweb either.

Thanks in advance.

---

### Post by CGW on 2008-12-02
> **SiHa said:**
> Live TV, by default, shouldn't display in the Watch Recordings list. I'm guessing your group filters have been changed somehow.

I'm at work now, so I can't remember the specifics but here goes.

In the Watch Recordings list, press Menu, there should be a 'change group filter' option, or something. If you select that, select 'default' if it's available - your recordings should be in there. 

Assuming they are there, you need to go to the TV playback settings, and somewhere in there is the options for the Watch Recordings screen. 'Include Live TV in list' should be unchecked, and 'starting group' you probably want set to 'default'.

If they're not there then, sorry, I don't know.

Do the recordings appear in Mythweb?

The filter group option solved it.  Thanks!!

---

