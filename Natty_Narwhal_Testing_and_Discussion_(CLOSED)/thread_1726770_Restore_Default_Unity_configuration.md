---
title: "Restore Default Unity configuration"
date: 2011-04-11
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by gunksta on 2011-04-11
I've played with Unity and I think I like it, now I want to start clean with it and go from there.

I've looked on Google, this forum and in my home folder and I can't find a way to reset Unity to it's default values. I tried erasing ~/.gconf* but that didn't help. I also looked in .config and .local for a "unity" folder to delete, but didn't see one.

---

### Post by coffeecat on 2011-04-11
Are you using Unity in the netbook version of 10.10, or in 11.04?

The answer to where the configuration files are has been puzzling some of us posting in the Natty testing subforum:

[http://ubuntuforums.org/forumdisplay.php?f=394](http://ubuntuforums.org/forumdisplay.php?f=394)

If you're running the 11.04 version and don't know about that subforum, you might want to drop by there. Also - one for your bookmarks, which might help:

[https://wiki.ubuntu.com/Unity](https://wiki.ubuntu.com/Unity)

---

### Post by gunksta on 2011-04-11
Unless I am really confused, this is the Natty testing subforum. I am running Natty on a desktop, laptop, netbook and server, although the latter doesn't even have X installed, so my questions doesn't apply to it.

---

### Post by gunksta on 2011-04-11
I'm definitely not confused. This is showing up in the testing subforum.

---

### Post by coffeecat on 2011-04-11
> **gunksta said:**
> Unless I am really confused

No, I'm the one confused. :oops: For some reason I thought I was in the General forum when I answered your post. Sorry.

---

### Post by lucazade on 2011-04-11
> **gunksta said:**
> I've played with Unity and I think I like it, now I want to start clean with it and go from there.

I've looked on Google, this forum and in my home folder and I can't find a way to reset Unity to it's default values. I tried erasing ~/.gconf* but that didn't help. I also looked in .config and .local for a "unity" folder to delete, but didn't see one.

Try with:
unity --reset

---

### Post by KegHead on 2011-04-11
Hi!

System..admin...login screen.

Select what you want as default session.

Hope this is what you're seeking.

KegHead

---

### Post by gunksta on 2011-04-11
> **lucazade said:**
> Try with:
unity --reset

I have tried it and does reset the active unity / compiz, processes. It also returns compiz settings to their default. Unfortunately, it does not affect Unity's settings. Thus, anything I have added or deleted from Unity is still there when it all comes back.

---

### Post by gunksta on 2011-04-11
> **KegHead said:**
> Hi!

System..admin...login screen.

Select what you want as default session.

Hope this is what you're seeking.

KegHead


Thanks! But, I know how to get into the Ubuntu Desktop. I want, and am using Unity, but I want to reset it. 

Back in the day (most recently, Ubuntu 10.10) if you garbled up your gnome-panel settings, you could just erase your .gnome2 folder and you would return to the default settings for a basic gnome session and many gnome2 apps. At this point, it doesn't see, that deleting ~/.gnome2 will have the same affect on Unity and I can't find any other way to restore Unity's default settings.

---

### Post by godhika on 2011-04-11
Well almost every setting for Unity is now governed by compiz, so unity --reset will reset  those one. The only other thing you could possibly have changed are the pinned applications in the launcher. Default ( if I remember correctly) are home folder, firefox, 3x libreoffice, software center. You can pin/unpin those as you whish and can do this by hand.

---

### Post by gunksta on 2011-04-11
With additional google-fu, I figured it out.

I found, on my own, where Unity stores the list of applications.

```
gsettings get com.canonical.Unity.Launcher favorites
```That is nice, but I want to reset them and:

```
 gsettings reset com.canonical.Unity.Launcher favorites
```wasn't working. So I continued my search. Finally, I found this:

[http://askubuntu.com/questions/17610/how-do-i-reset-my-unity-configuration](http://askubuntu.com/questions/17610/how-do-i-reset-my-unity-configuration)

Turns out, there is a modifier command that is not available in the unity man page. Thus, this works.
```
 gsettings reset com.canonical.Unity.Launcher favorites
unity --reset-icons &
```This works on my system, which  is updated as of 04/11/2011. Since this is currently a relatively undocumented sequence, it may or may not make it into Natty. But, assuming that it does make it into Natty, they should document this in the unity man page.

---

### Post by cariboo on 2011-04-11
> **gunksta said:**
> Thanks! But, I know how to get into the Ubuntu Desktop. I want, and am using Unity, but I want to reset it. 

Back in the day (most recently, Ubuntu 10.10) if you garbled up your gnome-panel settings, you could just erase your .gnome2 folder and you would return to the default settings for a basic gnome session and many gnome2 apps. At this point, it doesn't see, that deleting ~/.gnome2 will have the same affect on Unity and I can't find any other way to restore Unity's default settings.

There are probably other settings your are missing, if you create a new user, you will be able to start anew.

---

