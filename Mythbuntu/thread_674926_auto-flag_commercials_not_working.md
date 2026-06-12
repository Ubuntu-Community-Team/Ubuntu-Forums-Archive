---
title: "auto-flag commercials not working"
date: 2008-01-22
forum: Mythbuntu
---

### Post by harlee188 on 2008-01-22
I have tried to play with having the commercials flagged but can not get it to work.
In MythWeb I would set up a recording, and select:
auto-flag commercials

And this does not work.
I have also added the auto-transcode

But still nothing.

If I go in and view the "Recorded programs"

Has commflag: No
Has cutlist: No
Is editing: No
Has bookmark: No

I have no idea what I am missing...

---

### Post by tgm4883 on 2008-01-22
If you set the autoflag commercials, that only works for shows that are in the future, past shows will not be auto flagged.  Although you can manually tell them to do so

---

### Post by harlee188 on 2008-01-22
Yes, I understand this, I have gone and set this for all future recordings, and I still do not get auto flag set.

---

### Post by tgm4883 on 2008-01-22
any errors in the backend log?

/var/log/mythtv/mythbackend.log

---

### Post by newlinux on 2008-01-22
Does your job queue in mythweb or mythfrontend show any commercial flagging jobs? Is your backend setup to allow commercial flagging and transcoding jobs (look in mythtv-setup-general)?

---

### Post by harlee188 on 2008-01-23
I have nothing set up in the job queue.
Yes, it is allowed to to do commercial flagging.

I will recheck tonight

---

### Post by newlinux on 2008-01-23
Also, check and see if you can run a commercial flagging job on an existing recordings...

---

### Post by Archmage on 2008-01-24
I think the trick is that you have to manual change all the jobs that you created, since they are not affected.

E.g. if you had made a job for American Gladiatior without comercial flagging and you later change the settings that new recordings will do comerical flagging than the old job will still record without comercial flagging.

If you do a new job with Gilmore Girls it will have comercial flagging enabled.


To check, please do the following: Make a new job and see if comercial flagging will enable. Than test if comercial flagging will work.

BTW: You can see the status of your last planed and performed jobs in the browser under the adresse 127.0.0.1:6544

---

### Post by harlee188 on 2008-01-24
Well it turns out the flagging was not set on the back end!
I do not know how many times I went back to check this...
 It's just that on a 53" Projection TV it is very hard to determine if those boxes are selected or not!
Appreciate the help!
Flagging is now set.

---

### Post by novellahub on 2008-01-25
> **harlee188 said:**
> Well it turns out the flagging was not set on the back end!
I do not know how many times I went back to check this...
 It's just that on a 53" Projection TV it is very hard to determine if those boxes are selected or not!
Appreciate the help!
Flagging is now set.

Have you used VNC to remotely connect to your Mythbuntu machine?  It is much easier to read the screen and check boxes.  It works on both Windows and Linux machines.  Just make sure it is enabled in the Mythbuntu control panel and a password is set.

[https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

---

