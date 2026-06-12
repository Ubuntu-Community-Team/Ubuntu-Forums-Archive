---
title: "MythTV 0.26 Repos warn of a Partial  Update."
date: 2013-01-27
forum: Mythbuntu
---

### Post by jmail524 on 2013-01-27
Hi everybody,

I just installed Mythbuntu 12.04 and wanted to upgrade to MythTV 0.26 as it is suppose to have some fixes in it for us that have to deal with Daylight Savings Time changes.

I enabled the 0.26 repositories through the Mythbuntu Control Center.  Then I went to the Update Manager to install the new software.  However, it is telling me that it can only do a Partial Update.

QUESTIONS:
Am I executing the correct procedure for upgrading to MythTV 0.26?  If not, what is the correct procedure?

Should I just ignore the warning and install the partial update?  Is there any problems that might arise from doing only a partial update?

Thanks.
-Brian

---

### Post by ibjsb4 on 2013-01-27
Read this

[http://ubuntuforums.org/showthread.php?t=1859240](http://ubuntuforums.org/showthread.php?t=1859240)

---

### Post by tgm4883 on 2013-01-27
That is actually probably normal. Take a look at the FAQ on [http://www.mythbuntu.org/repos](http://www.mythbuntu.org/repos)

---

### Post by jmail524 on 2013-01-27
Hello again,

**@ibjsb4:**  That is an interesting read.  It sounds like the Upgrade Manager will update everything it can except if it requires removal of a previously installed package. So in my case, because "mythtv-backend 0.25"  needs to be removed, Update Manager leaves it alone and all packages that depend on the upgrade get held back.  Because of that, not all of the new 0.26 packages can be installed. (If I am understanding things properly.)

**@tgm4883:**  I had read through the FAQ when I first experienced the message, but I either didn't scroll down far enough or comprehend well enough and I completely missed the last entry of the FAQ.  It sounds like the "dist-upgrade" command will make all the necessary package transitions occur.  I going to give it a try and see what happens.

Thanks for the same-day service...
-Brian

---

### Post by tgm4883 on 2013-01-27
> **jmail524 said:**
> Hello again,

**@ibjsb4:**  That is an interesting read.  It sounds like the Upgrade Manager will update everything it can except if it requires removal of a previously installed package. So in my case, because "mythtv-backend 0.25"  needs to be removed, Update Manager leaves it alone and all packages that depend on the upgrade get held back.  Because of that, not all of the new 0.26 packages can be installed. (If I am understanding things properly.)

**@tgm4883:**  I had read through the FAQ when I first experienced the message, but I either didn't scroll down far enough or comprehend well enough and I completely missed the last entry of the FAQ.  It sounds like the "dist-upgrade" command will make all the necessary package transitions occur.  I going to give it a try and see what happens.

Thanks for the same-day service...
-Brian

You didn't miss it or not comprehend it. I added it after I saw this thread :)

---

### Post by zip1 on 2013-01-31
When I had had a problem with mythtv_common 2.025 causing a problem. What I did was use synaptic package manager, clicked on mark all upgrades, then apply.  It was able to deal with the problem and install everything correctly.

---

### Post by jmail524 on 2013-02-02
HI,

Sorry for the slow reply, I got called away for a while.  I would like to extend a big thank you to everyone here for their suggestions.

In the end I used *tgm4883's* suggestion (found in the Mythbuntu FAQ) and did a "dist-upgrade" (after enabling the 0.26 repository.)  All went well and my system seems to be running the 0.26 version of MythTV.

My fear was that a "dist-upgrade" would push the OS to 12.10 and I wanted to stay with 12.04 for the long-term support.  My fears were unfounded as the only thing that was upgraded was MythTV itself and required packages.

Again, thanks for the assistance...
-Brian

---

