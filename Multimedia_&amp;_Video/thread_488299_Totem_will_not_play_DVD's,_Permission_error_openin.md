---
title: "Totem will not play DVD's, Permission error opening directory"
date: 2007-06-30
forum: Multimedia &amp; Video
---

### Post by chele on 2007-06-30
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/10550](https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/10550) [br].[/br] ---------------------------- [br].[/br] [br].[/br]                 On inserting a video DVD, it automounts, then Totem (Movie Player) starts up and gives a permission error: ```
"Failed to play Audio/Video Disc
 Error opening directory '/media/cdrom0/'
VIDEO_TS': Permission denied."
``` A bit of research shows that the DVD is mounted with funny permissions, resulting in normal users not being able to view the DVD.

This is using Ubuntu Feisty, the same DVD just plays in Ubuntu Dapper. I have tried several DVD's and they all give the same error.

Is anyone having the same problem, and what was done to work around the issue?

---

### Post by chele on 2007-06-30
Here is the error I get. ```
An error occurred

Could not open location. You may not have permission to open the file.
```

---

### Post by RomeReactor on 2007-06-30
Hi. I don't know if this will help, but try going to the User Settings application (System-->Administration-->Users and Groups), choose your account (don't choose **root**) and on the "User Privileges" tab, make sure the **Use CD-ROM drives** case is checked.

---

### Post by chele on 2007-07-02
> **RomeReactor said:**
> Hi. I don't know if this will help, but try going to the User Settings application (System-->Administration-->Users and Groups), choose your account (don't choose **root**) and on the "User Privileges" tab, make sure the **Use CD-ROM drives** case is checked.I can otherwise use the drive, it plays music CD's, I can burn CD's, the DVD's even get mounted on the desktop and I can browse the files. The error occurs when the Movie Player automatically tries to play a video DVD. 

It is related to how the DVD is mounted by the system. It is mounted as UDF and the file permissions do not allow a non-root user to open/play the DVD.

A workaround I found is to put "gksudo" in front of the "totem" command in the System Preferences. Now when a video DVD is inserted, a password prompt comes up. ON entering the user password, the video DVD plays (as root)

I am looking for a workaround that is more transparent an secure then entering a password and running the movie player as root.

---

