---
title: "[SOLVED] Skype 2.0 buttons disappear in the video conversation window"
date: 2008-05-15
forum: Multimedia Software
---

### Post by viduliya on 2008-05-15
I am using Hardy with all the updates and I have noticed this new annoying problem with Skype 2.0.  I just got it working with pulseaudio and now there is a new video problem.

When I start a video conversation the buttons at the bottom of the conversation window (buttons like: Hold Call, Mute Mic, etc.) disappear.

I can see video from both my camera and my contacts camera, I simply can not pause the call or stop my video since the buttons are now gone.  Anyone else have this annoying new problem with skype?  This did not happen before I updated something in the last week.

Since a picture is worth a 1000 words here is what happens...

Before video is started:

[IMG]http://lh4.ggpht.com/viduliya/SCy9YiqBBOI/AAAAAAAAABg/7pXcZnwgeAk/s800/b4video.jpg[/IMG]

After video is started:

[IMG]http://lh5.ggpht.com/viduliya/SCy9YyqBBPI/AAAAAAAAABo/_obMwRLj9uc/s800/aftervideo.jpg[/IMG]

If anyone has a solution to this please let me know.

Thank you.

---

### Post by soro2005 on 2008-05-16
I also have this (button disappear during conversation), and in my case, the little window with my own video also disappears. Finally, my Skype icon in the notification area does not redraw the background or something, so that there is always clutter from past icons occupying the same space underneath. All of this since more than a week ago. No clue where that comes from.

---

### Post by viduliya on 2008-05-16
I had installed the shared library version of skype by downloading it from: [http://www.skype.com/download/skype/linux/choose/]("http://www.skype.com/download/skype/linux/choose/").  The shared library version is available by default when you get the "Ubuntu 7.04+" version from the Skype site.

To fix the above problem I installed the static library version of Skype from the medibuntu repository.   See [https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu") for instructions on adding the medibuntu repository.  Then install the static library version of Skype using Synaptic.

Once the static library version of Skype was installed the disappearing button problem was solved.

---

### Post by soro2005 on 2008-05-16
> To fix the above problem I installed the static library version of Skype from the medibuntu repository.

I don't know how that is a solution. Rather, it seems that there's a bug or something in Ubuntu's qt libraries. The shared version shouldn't have this sort of issues, and the static version looks horrible on my setup.

---

### Post by soro2005 on 2008-05-16
I have downgraded my qt libraries to 4.3.4 (4.4 is in backports), and that seems to haved solved all the issues with the shared libraries version of Skype. So I assume there's some conflict with 4.4.

---

### Post by viduliya on 2008-05-19
> The shared version shouldn't have this sort of issues, and the static version looks horrible on my setup.

I agree that the shared version should not have this sort of issues.  I do not know if this is a bug in QT libs or Skype.  Considering the amount of trouble I had with [pulseaudio and Skype]("http://ubuntuforums.org/showthread.php?p=4526841#post4526841"), and the workaround I have to do to get my [Logitech Quickcam]("http://forum.skype.com/index.php?showtopic=102838&pid=518891&st=20&#entry518891") to work with Skype I would not be surprised if there is some other issue with the shared lib version of Skype and I would not expect a fix for it soon.

> I don't know how that is a solution. 
I do know that the static lib version of Skype works without a problem and looks the same as the shared lib version here on my setup on two machines a desktop and a laptop.  The key requirement for me is that it remain functional and I do not have to start Windows in a VM.  So for all intensive purposes the problem I had is solved by installing the static lib version.

> I have downgraded my qt libraries to 4.3.4 (4.4 is in backports), and that seems to haved solved all the issues with the shared libraries version of Skype.
Also, I would not want to change/downgrade the default qt version for Hardy and effect other QT based programs running on this machine for the benefit of the shared lib version of Skype.  

I hope the shared lib version gets fixed soon either by Skype or by Qt libs.

---

### Post by soro2005 on 2008-05-27
> Also, I would not want to change/downgrade the default qt version for Hardy and effect other QT based programs running on this machine for the benefit of the shared lib version of Skype.
Actually, 4.3.4 *is* the default version for Hardy. 4.4 is in backports, but quite possibly not ready yet for primetime. So in essence, it's not downgrading, but just not upgrading to a version that is not fully implemented in Hardy. :)

Also, I didn't mean to offend anyone by saying I didn't consider the static version a solution. Just saying that there are bugs and issues which could be sorted out, rather than just tagging a thread "solved" on the grounds that some other version works fine. But this is a very mild complaint only.

---

### Post by mystuff on 2008-06-25
Just to let you know that this problem is not limited to Ubuntu, but rather applies to all Linux distribution using QT 4.4. For instance, openSUSE 11.0 using KDE 4.0 has this problem too.

A bug report has been filed, and a post was also made about this in the Skype forums, here:
[https://developer.skype.com/jira/browse/SCL-385](https://developer.skype.com/jira/browse/SCL-385)
and here respectively:
[http://forum.skype.com/index.php?showtopic=149951](http://forum.skype.com/index.php?showtopic=149951)

---

### Post by shein on 2008-08-16
I have this same problem.  How do you downgrade your qt libraries?  thanks!

---

### Post by Cyber Source on 2009-03-12
This is probably way old but I found this thread and wanted to reply with the easiest fix ever!
As I was checking my qt libs installed and what was available in the repos so I could look into the actions listed above about backporting/static/shared qt libs issue with Skype. I noticed this in the repos!

skype-static - A VoIP software - static variant - Medibuntu package

So, I did an "apt-get install skype-static" (without the need to add any other repos other than the stock ubuntu hardy ones), and voila! It removed the installed version I had (with the missing button issue) and installed this one with all deps needed. Fired her up after and all was good!

Gotta Love Ubuntu!!!!!!!!!!!

---

