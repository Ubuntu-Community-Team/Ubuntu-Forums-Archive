---
title: "Help! Cannot use Hauppauge WinTV PVR-350 ?"
date: 2007-02-07
forum: Multimedia &amp; Video
---

### Post by johann_p on 2007-02-07
I have installed a Hauppauge WinTV PVR-350 in my system but I cannot use it with either tvtime or kdetv.
I am running Feisty because Edgy did not install on my Intel motherboard (worked fine with Suse and and now Feisty).

I have looked at the instructions at [https://help.ubuntu.com/community/Install_IVTV_Feisty](https://help.ubuntu.com/community/Install_IVTV_Feisty) and everything mentioned there is fine: the card is found, modules loaded, no problems reported with dmesg. When I do (as root) "cat /dev/video0 > t.mpg" I get something like the picture of an untuned TV.

But when I e.g. run tvtime from my user I get the error message: "Permission denied. Cannot open capture device /dev/video0" . When I run tvtime as root I get "ivtv: Invalid argument. Cannot open capture device /dev/video0"

Permissions: "crw-rw---- 1 root video 81, 0 2007-02-07 23:41 /dev/video0"

When I try kdetv the video menu has an entry "No Devices found."

I though Hauppauge 350 is one of the cards that is expected to work best under Linux/Ubuntu??

---

### Post by crispy_420 on 2007-02-09
I think tvtime is made to be used with bttv based cards or other non-hardware encoder cards. Don't get my wrong, you have a great card there. You just need to a different app to watch tv. I would suggest looking into mythtv. For that just search these forums.

---

### Post by barney_1 on 2007-02-09
> **johann_p said:**
> But when I e.g. run tvtime from my user I get the error message: "Permission denied. Cannot open capture device /dev/video0". 

I've had this problem before myself.  You need to make sure that the user is part of the group "video".  First check to see if your user is part of the group:

```
grep video /etc/group
```

This will list the users in the video group:

```
video:x:44:mike,mythtv
```

If your user is not listed then add him:

```
sudo useradd --group video USERNAME
```

---

### Post by johann_p on 2007-02-09
> **barney_1 said:**
> I've had this problem before myself.  You need to make sure that the user is part of the group "video".  First check to see if your user is part of the group:

```
grep video /etc/group
```This will list the users in the video group:

```
video:x:44:mike,mythtv
```If your user is not listed then add him:

```
sudo useradd --group video USERNAME
```


Thanks, that takes care of the permission problem!
However your command gave me a "user already exists" error message, I used "adduser USERNAME video" instead and that worked.

However, now I get the same message as previously under root (which I tried in the meantime): tvtime shows the error message "ivtv: Invalid argument. Cannot open capture device /dev/video0"

Now  I can show video from exactly that device using mplayer under my own user: "mplayer -ao oss -vo xv /dev/video0"


However I cannot tune the card from my user: when I do e.g. "ivtv-tune -t europe-west -c E7" I get the error message "Failed to open /dev/video0"

Under root, that same command succeeds. 

This is all totally odd.

Regarding mythtv: I installed this using synaptic and the installation script asked me for the mysql root password. Looks a bit like overkill to have mysql just for watching tv, but ok, I told it the password.

Then I get informed that I need to run mythtv-setup as the mythtv user! I want to look at that user in the System->Control Center -> Users and Groups dialog but it does not show here! I do not know th password of that user either. How is a normal user supposed to do all this just to watch TV??

OK I log in as root and then do su mythtv but I cannot start any X program. 

I give up.

---

### Post by johann_p on 2007-02-09
This is extremely frustrating, none of the tv playing programs work: zapping, kdetv, xawtv, tvtime, mythtv. None of the programs provides any usable error message or hints about what could be the problem :(

---

### Post by plb on 2007-02-13
mplayer /dev/video0

---

### Post by johann_p on 2007-02-13
I have mentioned that mplayer /dev/video0 works in an earlier post, but it is still odd and frustrating that no GUI program works - how can that be?

Something has to be very wrong and/or buggy here.

---

### Post by Joshua on 2007-02-18
> **johann_p said:**
> Then I get informed that I need to run mythtv-setup as the mythtv user! I want to look at that user in the System->Control Center -> Users and Groups dialog but it does not show here! I do not know th password of that user either. How is a normal user supposed to do all this just to watch TV??

Does anyone know why the mythtv user doesn't show up in the "Users and Groups" dialog?  Or how to get it to show up there?  If it showed up there, I think it would also show up as an option in the "Automatic Login" user box under the Security tab of the "Login Window" administration dialog.  Seems to me that the ability to use those dialogs would be nice for a new user.

Edit: Thought this would be better as a [new post]("http://ubuntuforums.org/showthread.php?t=364634").

---

