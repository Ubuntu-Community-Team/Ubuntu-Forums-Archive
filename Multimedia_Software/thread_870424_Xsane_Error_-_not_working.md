---
title: "Xsane Error - not working"
date: 2008-07-25
forum: Multimedia Software
---

### Post by geovino on 2008-07-25
I was using xsane and hit a button and that basically wrecked xsane. I get this error message:

Error during CMS conversion. could not open scanner ICM profile.

I even uninstalled and reinstalled xsane and it still is messed up.

what can I do to get it to work again??

---

### Post by Teddix2 on 2008-08-21
I had exactly the same problem like Geovino today: Xsane worked, then afer some action (don't exactly remember what I did ...) the program stopped coming up with exactly the same messages:

Error during CMS conversion. could not open scanner ICM profile.

Is there no help in sight? It would certainly greatly appreciated.

Thank you very much.

---

### Post by michiel33 on 2008-12-28
Same error here. Help greatly appreciated!

Strange thing is that it used to work before I reinstalled Ubuntu 8.10

Michiel

---

### Post by xc3RnbFO8P on 2008-12-28
Found this hope it helps:
> For me, if I uncheck "Preferences / Enable Color Management" this error goes away - and scanner works normally.

[http://www.xsane.org/doc/sane-xsane-setup-color-management-doc.html]("http://www.xsane.org/doc/sane-xsane-setup-color-management-doc.html")

---

### Post by michiel33 on 2008-12-30
Indeed, the ICM message goes away but now if I click Scan, it says "failed to start scanner, invalid argument"

Any tips here?

---

### Post by MakisM1 on 2009-06-24
If you launch XSANE and go

Preferences>Setup>Color Management

You will find that it expects you to specify 5 ICM profiles

A quick search found one (1) available in the whole file system!

It is in

/usr/share/ImageMagick-6.4.5/config/sRGB.icm

sRGB.icm being the filename.

I input, for the time being, this file for all 5 ICM profiles and enabled Color Management in the Preferences. It works fine.

---

### Post by linuxford on 2009-09-13
I also have had trouble. It is not apparent to me why the problem started. I use the scanner to save it to pdf files. I don't believe I changed any options accidently. Maybe something was changed that XSane somehow references.

---

### Post by dogafin on 2009-10-14
[IMG]http://i35.tinypic.com/m0gf8.png[/IMG]

i am not sure if the switch to karmic did this, but it used to work for me. now i am looking at a dead end. after repeated reinstall of xsane, it has proved to not fix anything.

---

### Post by bdalzell on 2009-12-04
Try this:

Under the Preferences Menu in Xsane - look to see if the check box "enable color management" is checked. If it is, uncheck it.

---

### Post by mjolnar on 2009-12-11
> **dogafin said:**
> [IMG]http://i35.tinypic.com/m0gf8.png[/IMG]

i am not sure if the switch to karmic did this, but it used to work for me. now i am looking at a dead end. after repeated reinstall of xsane, it has proved to not fix anything.
 
This is about when mine went.  I worked fine till I updated a week or two ago.  I didn't notice it till my wife wanted me to copy some old pictures.  I have uninstalled and reinstalled the printer and XSane. I add network printer PhotoSmart 6280, print test page.  When I try to us XSane, I get,
Error during CMS conversion:  
Could not open scanner ICM profile
When I enabled Color managment. It tells me:Failed to Scanner: Invalid Argument.

This is so frustrating, because it has always worked flawlessly.  I never had to setup anything, now I can't find anyway to set it up.

---

### Post by xc3RnbFO8P on 2009-12-11
Try:
> sudo apt-get install libsane-extras

---

### Post by aymj on 2012-06-26
i have the same problem.
"Error during CMS conversion. could not open scanner ICM profile".
as you suggest(**MakisM1**) i had made changes in xsane after that the error has gone and the scanner work fine but after scan process complete its showing blank page..
please help ..........

---

### Post by aymj on 2012-06-26
i have the same problem.
"Error during CMS conversion. could not open scanner ICM profile".
as _**MakisM1 **_suggest i have made changes in xsane after that the error has gone and the scanning process working fine but after scan process complete its showing blank page.

plz help.......

---

### Post by overdrank on 2012-06-26
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

