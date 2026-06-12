---
title: "Pidgin freezes up indefinitely, Ubuntu 8.10 Pidgin 2.5.2/2.5.4"
date: 2009-02-26
forum: Networking &amp; Wireless
---

### Post by zaarin on 2009-02-26
Ubunto 8.10
Pidgin 2.5.2
Using **AIM only**.

Every time I run Pidgin, it connects normally to the AIM servers and loads my Buddy List correctly.  However, as soon as I send or receive the first instant message over AIM, the program (buddy list and message window both) freezes.  The windows go dim and stop responding forever, until I force quit.

I started a Terminal and ran Pidgin from there to check error messages as suggested in an unresolved thread by another user on this issue from over a month ago, but no error messages were displayed in the Terminal.

Today I attempted upgrading Pidgin to **version 2.5.4**.  It still connects normally and loads my AIM Buddy List, but it still freezes as soon as I send or receive one message over AIM.

I am a serious newbie and I'm stumbling along through this process, so please be gentle!!

---

### Post by kevdog on 2009-02-26
Please start pidgin from the command line and see if any output is given in the terminal which may help you determine what is going on here!

---

### Post by bab1 on 2009-02-26
> **zaarin said:**
> Ubunto 8.10
Pidgin 2.5.2
Using **AIM only**.

Every time I run Pidgin, it connects normally to the AIM servers and loads my Buddy List correctly.  However, as soon as I send or receive the first instant message over AIM, the program (buddy list and message window both) freezes.  The windows go dim and stop responding forever, until I force quit.

[COLOR="Blue"]*I started a Terminal and ran Pidgin from there to check error messages as suggested in an unresolved thread by another user on this issue from over a month ago, but no error messages were displayed in the Terminal.*[/COLOR]

Today I attempted upgrading Pidgin to **version 2.5.4**.  It still connects normally and loads my AIM Buddy List, but it still freezes as soon as I send or receive one message over AIM.

I am a serious newbie and I'm stumbling along through this process, so please be gentle!!

I had this same problem.  including the fact that there were no error messages displayed.

I disabled the sounds in the Preferences section after reading about a cure in a similar post on this forum.  I don't have speakers attached to my Ubuntu host, so it was no big deal for me.  Pidgin has worked fine for me since then.

To disable the sound go to Buddy List >>Tools >>Preferences and select the Sounds tab.  Under Sound Method select No sounds.

---

### Post by zaarin on 2009-02-26
Thank you so much, Bab!  It is working just fine now.  It's weird that it throws no codes... oh well.  Thanks again!  I have Pidgin back now!!

---

### Post by bab1 on 2009-02-26
> **zaarin said:**
> Thank you so much, Bab!  It is working just fine now.  It's weird that it throws no codes... oh well.  Thanks again!  I have Pidgin back now!!

I searched for months for the answer.  I'm glad I could help someone else.  :p

Edit:  I think what happens is the app is stalled waiting for a response.  This will not send errors.

---

### Post by zarthon on 2009-03-10
Has anyone logged a bug on this ?

A silent pidgin is better than a frozen one. Thanks for that work around!
I agree that if an asynchronous function call does not return a result an application may not throw an error and log. A debug version of the app should do better so I will try that.

I have this problem and I need Pidgin to ring like a phone when new conversation are opened.
I do not have a freeze until i am involved in a conversation and a few messages have been exchanged. Things can be fine for 5 minutes or more but I do not get any sound from Pidgin. Then it freezes and does not recover.

I would like to see if there is a bug report and if i get time i will try to help solve this problem.

I believe this is a bug in Pidgin or a degenerate state in configuration temp files and the like. Wiping my temp files did not solve it. I am going to try wiping my configuration files to see if that fixes things.

Any such condition should not be created by a regular application (non distro version) upgrade.

What sound system are others having this problem using ?
I think am using ALSA
Does anyone know how ALSA deals with requests when multiple applications are making sounds?

This problem started after an update in the past month. 

The application should time out on any wait state condition and report the error in question and also should return control to the GUI event loop.

The issue here is that it is not being treaded asynchronously if the application is freezing! Additionally you can code to keep track of asynchronous calls and call backs / messages and either log the conversation so that omissions can be found or use timeouts to log omissions. I would put this code in the debug version or logging level because they are not issues expected in normal operation. I may have time to test this theory later today after a searching bug databases and so forth. Then log a bug.

---

### Post by zaarin on 2009-03-10
For what it's worth, I was using an absolutely virgin install of 8.10 when I ran into this problem.  I just installed the OS and ran Pidgin, and the problem cropped up immediately.  So I can't imagine it has to do with anything other than my own hardware OR errors in the code as I downloaded it.

---

### Post by JoshTodd on 2009-03-30
I had this same issue, and I am using OSS 4.1.  The No Sounds fix worked for me, but I do wish there was another solution.  I don't like to miss AIMs because I don't notice them...

---

### Post by capscrew on 2009-03-30
> **JoshTodd said:**
> I had this same issue, and I am using OSS 4.1.  The No Sounds fix worked for me, but I do wish there was another solution.  I don't like to miss AIMs because I don't notice them...

Check and see if you have ALSA sounds selected in the sounds preferences.  This is how the gstreamer libs are configured.  The gstreamer is usually the prob with pidgin sound.

---

