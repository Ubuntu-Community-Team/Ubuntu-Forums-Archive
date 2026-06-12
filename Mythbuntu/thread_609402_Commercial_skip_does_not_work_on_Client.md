---
title: "Commercial skip does not work on Client"
date: 2007-11-10
forum: Mythbuntu
---

### Post by hotstyle765 on 2007-11-10
I am running Ubuntu Gutsy as a server with mythtv installed on it. When I watch recorded shows on the server I am able to commercial skip once my shows are flagged. 

So I decided to try to use mythbuntu on my laptop as a client that connects to that server. Everything works wireless, video playback and all. But I can not skip commercials. When browsing the recorded shows it says that they are all commercial flagged and I have verified this on the server. But when I watch shows on the mythbuntu Live CD client and I press Z for commercial skip it just says "Not flagged" and does not skip the commercial. 

Anyone have any ideas? I didnt see this problem anywhere in the forum.

Thanks in advance.

---

### Post by superm1 on 2007-11-10
You sure that your backend is running the flagging routines?  If so, then make sure that your database is good.  A corrupt mysql database will make for similar odd, hard to debug problems.

---

### Post by Panhead Bill on 2007-11-11
I have a similar problem; my master backend flaggs the commercials, and if I view the recordings from the MBE I can skip the commercials.  

If I use the live frontend on another pc, I get the "not flagged" message. 

This has happened on two different pc's - both with wired (ethernet) connections.  One pc is on the same switch as the MBE, the other is on the router that feeds the switch.

---

### Post by hotstyle765 on 2007-11-11
> **Panhead Bill said:**
> I have a similar problem; my master backend flaggs the commercials, and if I view the recordings from the MBE I can skip the commercials.  

If I use the live frontend on another pc, I get the "not flagged" message. 

This has happened on two different pc's - both with wired (ethernet) connections.  One pc is on the same switch as the MBE, the other is on the router that feeds the switch.

I wish i could test out if it is just the Live Frontend Client causing this problem. Panhead do you have another client on your network that is not using the Live CD?

---

### Post by superm1 on 2007-11-12
> **hotstyle765 said:**
> I wish i could test out if it is just the Live Frontend Client causing this problem. Panhead do you have another client on your network that is not using the Live CD?
I would be reluctant to believe it to be any different with a Live CD frontend since its just a squashfs/unionfs filesystem versus an ext3.  Same packages otherwise.

You know its possible too that in both your frontend and backend logs items about this are showing up.

Did you try to repair the SQL tables yet like I asked?

---

### Post by hotstyle765 on 2007-11-12
> **superm1 said:**
> I would be reluctant to believe it to be any different with a Live CD frontend since its just a squashfs/unionfs filesystem versus an ext3.  Same packages otherwise.

You know its possible too that in both your frontend and backend logs items about this are showing up.

Did you try to repair the SQL tables yet like I asked?

Do you really think i need to repair the database if the commercials are skipping fine on the master backend? Also that was going to be my next question... (should this show up in the backend log?) from your comment i guess it should show up in either the front end or backend logs. I am going to look into it tonight and get back to you. Thanks for the info.

---

### Post by superm1 on 2007-11-12
> **hotstyle765 said:**
> Do you really think i need to repair the database if the commercials are skipping fine on the master backend? 

Yes, i've had this EXACT same issue myself and it solved the problem.  There was corruption in some of the tables used for that remote frontend.

> 
Also that was going to be my next question... (should this show up in the backend log?) from your comment i guess it should show up in either the front end or backend logs. I am going to look into it tonight and get back to you. Thanks for the info.
This is likely showing up in at least one of the logs.

---

### Post by hotstyle765 on 2007-11-12
Ok just ran it again....

Nothing good from the backend log...

From the frontend Live CD client log... Everytime I press Z I get:

```
2007-11-13 00:24:10.806 mixer set channel 0 err -1: Operation not permitted
2007-11-13 00:24:10.806 mixer set channel 1 err -1: Operation not permitted

```

I am trying to google around for the error ask we speak... Does this ring any bells for anyone?
Going to try to do the repair also..
Thanks in advance!

---

### Post by hotstyle765 on 2007-11-12
Just did the optimize and repair script and same issue. I keep getting those two errors when pressing the commercial skip button on the live frontend client.

---

### Post by hotstyle765 on 2007-11-15
Anyone have any ideas on what this error means? I have been googling without much luck.

---

### Post by superm1 on 2007-11-15
Does the audio control work on the live frontend for this system?  Try changing the volume and see if you are getting the same issues.

---

### Post by hotstyle765 on 2007-11-15
> **superm1 said:**
> Does the audio control work on the live frontend for this system?  Try changing the volume and see if you are getting the same issues.

The volume stays the same when adjusting with the f10 and f11 keys.

Thanks for the reply.

---

### Post by superm1 on 2007-11-15
> **hotstyle765 said:**
> The volume stays the same when adjusting with the f10 and f11 keys.

Thanks for the reply.
Okay so that confirmed one of my suspicions.  It seems like whatever audio card you have doesn't have the default mixers available to it.  You will want to go into the general setup section of the frontend setup, and see if you can tweak the mixers used.  You might also consider turning off the option allowing myth to manage your audio all together.

---

### Post by hotstyle765 on 2007-11-15
> **superm1 said:**
> Okay so that confirmed one of my suspicions.  It seems like whatever audio card you have doesn't have the default mixers available to it.  You will want to go into the general setup section of the frontend setup, and see if you can tweak the mixers used.  You might also consider turning off the option allowing myth to manage your audio all together.

Ok I will give this a try later today. Any clue why this would stop commercials from skipping?

---

### Post by superm1 on 2007-11-15
> **hotstyle765 said:**
> Ok I will give this a try later today. Any clue why this would stop commercials from skipping?
Here is how a commercial skip takes place:

1) Mute volume
2) Skip
3) Unmute volume


This is so that you don't hear a loud pop or volume level difference right after the skip.

---

### Post by hotstyle765 on 2007-11-15
Ok that did solve the error but I am still having the same problem. Still says "Not Flagged" when I press Z. 

Here is the output from the client from when I start a recorded commercial flagged show:
```
0: start_time: 0.036 duration: 323.672
1: start_time: 0.017 duration: 323.667
stream: start_time: 0.189 duration: 3596.571 bitrate=5190 kb/s
2007-11-15 23:24:03.251 AFD: Opened codec 0x84c8730, id(MPEG2VIDEO) type(Video)
2007-11-15 23:24:03.252 AFD: Opened codec 0x84882b0, id(MP2) type(Audio)
2007-11-15 23:24:04.304 TV: Attempting to change from None to WatchingPreRecorded
2007-11-15 23:24:04.516 DPMS Deactivated 
0: start_time: 0.036 duration: 323.672
1: start_time: 0.017 duration: 323.667
stream: start_time: 0.189 duration: 3596.571 bitrate=5190 kb/s
2007-11-15 23:24:04.604 AFD: Opened codec 0xafd388a0, id(MPEG2VIDEO) type(Video)
2007-11-15 23:24:04.604 AFD: Opened codec 0xafd38bf0, id(MP2) type(Audio)
2007-11-15 23:24:04.643 Opening ALSA audio device 'default'.
2007-11-15 23:24:04.714 VideoOutputXv: XvMCTex: Init failed
2007-11-15 23:24:04.715 VideoOutputXv: XVideo Adaptor Name: 'Intel(R) Video Overlay'
2007-11-15 23:24:05.131 Realtime priority would require SUID as root.
2007-11-15 23:24:05.148 TV: Changing from None to WatchingPreRecorded
2007-11-15 23:24:07.319 NVP: Timed out waiting for free video buffers.
2007-11-15 23:24:08.158 Video timing method: USleep with busy wait

```

If that helps any.

Thanks again.

Also I tried the live client on a second machine and it is having the same problem.

**Edit:** Just to add a little more info... I decided to install Ubuntu on the machine and installed the Myth Client. Commercial Skip works fine. This is the machine that I tested the live mythbuntu CD on and commercial skip did not work. Does this isolate the problem to the live CD now?

---

