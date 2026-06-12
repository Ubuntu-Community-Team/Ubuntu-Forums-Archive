---
title: "Update notifications in Unity"
date: 2011-04-15
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by wgarcia on 2011-04-15
How does one get update notifications in Unity? Is an indicator coming for that or is there any other way now?

I've been running Unity since Beta 1 but I don't get any update notifications.

---

### Post by KegHead on 2011-04-15
Hi!

Should be daily.

Try: in terminal

sudo apt-get update

sudo apt-get upgrade -f

sudo apt-get dist-upgrade -f (you may need to restart)

Please advise

KegHead

---

### Post by rburkartjo on 2011-04-15
i use this command in the terminal to check for updates and do it a lot



sudo aptitude update && sudo aptitude safe-upgrade

make sure that you have aptitude installed from the spm

---

### Post by wgarcia on 2011-04-15
Thanks, I know I can do it from the command line, and for the time being since we are in development phase there are a lot of updates every day. 

But what I was referring to is any notification that you have updates, I used to have it configured as an indicator in the gnome panel and that indicator told if there were updates (and also with different colours if it was a security update).

What is the equivalent in Unity?

---

### Post by Harry33 on 2011-04-15
> **wgarcia said:**
> Thanks, I know I can do it from the command line, and for the time being since we are in development phase there are a lot of updates every day. 

But what I was referring to is any notification that you have updates, I used to have it configured as an indicator in the gnome panel and that indicator told if there were updates (and also with different colours if it was a security update).

What is the equivalent in Unity?

You are talking about the update-notifier (packages update-notifier and update-notifier-common).
It should put an icon in the notification area in the panel to inform of the availability of updates.
This thing has not worked for a long time on my setups and I have uninstalled them.

---

### Post by Steel-Bunz on 2011-04-15
Very strange indeed. I don't get any notifications either. This used work flawlessly and in fact one of the huge advantages of Ubuntu and Linux, in general. Unified Software Update and prompt notifications when such an update is available.
 
Can any one throw some light on how to diagonize this problem?

---

### Post by Harry33 on 2011-04-15
> **Steel-Bunz said:**
> Very strange indeed. I don't get any notifications either. This used work flawlessly and in fact one of the huge advantages of Ubuntu and Linux, in general. Unified Software Update and prompt notifications when such an update is available.
 
Can any one throw some light on how to diagonize this problem?

You should first check the settings in the software-properties-gtk (Software Sources).
So open the application and go to the tab "Updates".
Then see the settings from the section "Automatic updates".

---

### Post by frankbooth on 2011-04-15
> **wgarcia said:**
> But what I was referring to is any notification that you have updates, I used to have it configured as an indicator in the gnome panel and that indicator told if there were updates (and also with different colours if it was a security update).

What is the equivalent in Unity?

Sounds like you might want to check this thread: [http://ubuntuforums.org/showthread.php?t=1726472](http://ubuntuforums.org/showthread.php?t=1726472)

---

### Post by wgarcia on 2011-04-16
Yes, thanks, I followed the instructions in that thread, let's see if I get the update notifications back, it is not clear from that thread that it works if you read until the end and despite the very promising first post.

---

### Post by wgarcia on 2011-04-16
I confirm that the workaround in:

[http://ubuntuforums.org/showthread.php?t=1726472](http://ubuntuforums.org/showthread.php?t=1726472)

works, today I got the notification indicator back in the systray area of the Unity panel.

---

### Post by Steel-Bunz on 2011-04-16
I understand that there is a workaround to get the old style update notifications back. But is there any default method at all in Natty for automatic updates?

---

