---
title: "MythTV, No Channel Data, Weather data, ect"
date: 2007-06-08
forum: Multimedia &amp; Video
---

### Post by poke4christ on 2007-06-08
Well, I've got my MythTV up and running including getting my remote to work.  I'm using a PVR-150 with the remote and an old system as  kind of starter mythtv box (just getting things working).  However, I'm haveing a lot of problems.  I can't get the program data to download (does it do it automatically?)  Also, I can't get Myth Weather to work.  It doesn't seem to be successful at downloading the data.  I figure that these may be the same problem and that there may be other things affected. I wanted to get back into the backend-setup menu and play around with some things, but I could figure out how. 

Zach

---

### Post by newlinux on 2007-06-09
mythweather is currently broken. A patch exists, but I don't know the details.

What output do you get when you run mythfilldatabase on your master backend?

---

### Post by poke4christ on 2007-06-09
> **newlinux said:**
> mythweather is currently broken. A patch exists, but I don't know the details.

What output do you get when you run mythfilldatabase on your master backend?

Well, that's kind of a problem.  I'm not sure how to do that.  I know how to switch windows and login as myself, but I don't know how to login as mythtv to run things like mythfilldatabase.  I tried to login as it, but I couldn't get the password.  Is this something that the user is expected to do every time it is needed?  If so, I'll guess I just have to setup a schedule for automation.

---

### Post by newlinux on 2007-06-09
Well, I don't have my system setup this way, as i run mythfrontend as my regular desktop user. but you can still log in as yourself and run mythfilldatabase as the mythtv user using sudo:

```

sudo -u mythtv mythfilldatabase

```

and enter your password as you normally do with sudo. You probably should, however, figure out the mythtv user password. What tutorial did you follow to set it up? Does it indicate a password?

And let's see what is output. If it works fine, you can schedule  mythfilldatabase to run regularly in mythfrontend (Utilities/Setup->General go a few screens). If it doesn't work, post the output.

---

### Post by poke4christ on 2007-06-09
> **newlinux said:**
> Well, I don't have my system setup this way, as i run mythfrontend as my regular desktop user. but you can still log in as yourself and run mythfilldatabase as the mythtv user using sudo:

```

sudo -u mythtv mythfilldatabase

```

and enter your password as you normally do with sudo. You probably should, however, figure out the mythtv user password. What tutorial did you follow to set it up? Does it indicate a password?

And let's see what is output. If it works fine, you can schedule  mythfilldatabase to run regularly in mythfrontend (Utilities/Setup->General go a few screens). If it doesn't work, post the output.

Here's the tutorial I used.  It's the Fiesty Backend Frontend one.

[https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend](https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend)

I can't see any mention of a password for the MythTV user.  Is there anyway to access the shell from MythTV without having to login as a new user?  I know the "Ctrl+Alt+F*" command, but I have to login then.  Also, once I've done this, how do I get back to mythtv?

As for MythFillDatabase, I'll run that and get back to you.

---

### Post by cantormath on 2007-06-09
video tutorial and setup
[http://revision3.com/systm/mythtv](http://revision3.com/systm/mythtv)

---

### Post by newlinux on 2007-06-09
> **poke4christ said:**
> Here's the tutorial I used.  It's the Fiesty Backend Frontend one.

[https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend](https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend)

I can't see any mention of a password for the MythTV user.  Is there anyway to access the shell from MythTV without having to login as a new user?  I know the "Ctrl+Alt+F*" command, but I have to login then.  Also, once I've done this, how do I get back to mythtv?

As for MythFillDatabase, I'll run that and get back to you.


After you've done "Ctrl-Alt-F1" you can go back your graphical login by doing "Ctrl-Alt-F7" most likely. If it isn't at F7 try F9 or some others. It's one of them. You can go back and forth.

It looks like that tutorial doesn't setup a normal ubuntu-desktop. I'm guessing it uses openbox as your windowmanager. When you autologin as mythtv, exit the mythtv frontend (by pressing ESC) and you will probably have a blank background. Your mouse menus (left and right click) may be configured to have a couple      of simple menus (I don't know how this windowmanager is configured by default). Look for an item like "Xterm" or terminal to open up a shell that you can run commands in.

Also, I think using those tutorials the default password for mythtv is "mythtv"

---

### Post by poke4christ on 2007-06-09
> **newlinux said:**
> Also, I think using those tutorials the default password for mythtv is "mythtv"

tried that, didn't work.

---

### Post by poke4christ on 2007-06-09
Well, I ran Mythfilldatabase and it seemed to have no affect.  This is what is shown in the system status section of my MythTV.

```
Myth version: 0.20.20060828-3 Unkonwn
Last mythfilldatabase guide update:
Started: 2007-06-09 12:33
Finished: 2007-06-09 12:33
Result:

There's no guide data available!
Have you run mythfilldatabase?
WARNING:: is mythfilldatabase running?
DataDirect Status:
Your subscription expires on 08/15/2007 06:48:09 PM
```

---

### Post by newlinux on 2007-06-09
can you post your mythfilldatabase output? The first run of it should produce a lot of output and take some time since it would need to download complete listings for about 2 weeks. Looks like it isn't set up correctly if it completed in less than a minute.

Also,

1. Double check zap2it account  (go to your zap2it account and look at which stations are selected) and make sure there are channels selected to download data for, and that they correspond to the channels you are looking for.

2. Double check your input connection and video source with the proper zap2it account are setup correctly.

---

### Post by mjezell on 2007-07-07
To your question on the password for your mysql database... in the ubuntu mythtv fiesty tutorial for frontend/backend installation, you will find this screen shot with the instruction on the automatic password creation that the install will preform for you.

[IMG]http://www.renewabletechnology.us/mythtv/images/mysql_pw_s2.png[/IMG]

You can locate the generated password by following this - 
As also shown, the information will also be stored in /etc/mythv/mysql.txt if you need to refer to it later.

---

