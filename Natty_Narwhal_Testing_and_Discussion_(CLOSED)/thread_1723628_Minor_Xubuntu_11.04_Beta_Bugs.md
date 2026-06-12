---
title: "Minor Xubuntu 11.04 Beta Bugs"
date: 2011-04-07
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by loukingjr on 2011-04-07
I'm only having a few small issues with 11.04, one is, whatever cursor I choose only shows up when it's hovering over Firefox. I've tried logging out and rebooting but doesn't help. I also tried running the script for the icon theme ACYL to change it's appearance but it doesn't run. The script has a line in it that has to be changed from python2.6 to python2 in order to run on later versions of python but it didn't help in this case. 

any ideas?
thanks ahead of time.

---

### Post by ikt on 2011-04-07
[http://forum.xfce.org/viewtopic.php?pid=20778](http://forum.xfce.org/viewtopic.php?pid=20778)

same thing?

---

### Post by loukingjr on 2011-04-07
> **ikt said:**
> [http://forum.xfce.org/viewtopic.php?pid=20778](http://forum.xfce.org/viewtopic.php?pid=20778)

same thing?

yes it was. and running xfce4 --replace fixed it. thanks for the info.:)

as far as the ACYL icon scripts issue, I tried installing the icon theme in both the /home/<usr>/.icons folder and the /usr/shared/icons folder and for some reason Xubuntu doesn't think the scripts or directories exist even though I can drag them directly into the terminal.

---

### Post by loukingjr on 2011-04-15
any chance they are going to fix the problem with cursors? we are in beta 2 now and running xfwm4 --replace every time I boot or reboot is getting old.

---

### Post by tristan on 2011-04-16
I've been using xubutnu 11.04 beta 2 for a day now and while it's pretty nice I just keep finding new bugs to get irritated by. There seem to be far more bugs than previously, i think it's to do with xfce4.8 more than underlying ubuntu

1 - Huge delay when starting thunar for the first time if the computer is networked (seems to be looking for network shares)

2 - Notification popups not disappearing

3 - Reboot/Shut down more often than not simply log the user out

4 - Visual issues with scrollbars

Anyone else seeing these? I'd like to log bug reports but only if I see that other people are experiencing them too.

---

### Post by teachop on 2011-04-16
> **tristan said:**
> I've been using xubutnu 11.04 beta 2 for a day now and while it's pretty nice I just keep finding new bugs to get irritated by. There seem to be far more bugs than previously, i think it's to do with xfce4.8 more than underlying ubuntu

1 - Huge delay when starting thunar for the first time if the computer is networked (seems to be looking for network shares)

2 - Notification popups not disappearing

3 - Reboot/Shut down more often than not simply log the user out

4 - Visual issues with scrollbars

Anyone else seeing these? I'd like to log bug reports but only if I see that other people are experiencing them too.
1 - Have not seen that as an issue at all, but my network is pretty simple.
2 - I saw a setting for that someplace, was defaulted to zero seconds which perhaps means never, now I have to remember where I saw that setting...
3 - Yes, have seen that, then have to hit the shutdown from the login screen.
4 - Have not seen that at all.

My number one instability in Xubuntu has been evince, which crashes and actually causes loss of data if you work with pdf fill-in forms.  I imagine that is a problem across the Ubuntu family, but have not tried to reproduce on the others.

---

### Post by XubuRoxMySox on 2011-04-16
I have had none of those issues at all. But my 'puter is set up to automatically log me on at bootup, and I use PCManFM as my primary file manager instead of Thunar. So far Xfce 4.8 has been awesome. 

Teachop wrote:


> 
My number one instability in Xubuntu has been evince, which crashes and actually causes loss of data if you work with pdf fill-in forms.

I discovered a way-cool app for filling out pdfs. I was so impressed with it that I wrote a li'l blog post about it ([here]("http://dixiedancer.posterous.com/xournal-pdf-annotator-cool-applications-notes")). It's not a true alternative to Evince because it's a pdf *annotator* rather than a pdf *editor*, but it sure is simple and easy to fill out those pdf forms.

-Robin

---

