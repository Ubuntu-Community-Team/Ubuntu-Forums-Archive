---
title: "Skype v4.3 not signing in ubuntu 14.04"
date: 2015-09-21
forum: Multimedia Software
---

### Post by lefteris3 on 2015-09-21
Greetings to all and thank you in advance for your kind effort to help.

As written in the title field, I have installed skype version 4.3 and when I try to connect skype the signing in takes forever. I use the correct username and password since I am able to connect to the official webpage. The account is good.

I have followed step-by-step the guidelines of the following post to remove the old version of skype and install this new one: [http://askubuntu.com/questions/488053/how-to-install-skype-4-3](http://askubuntu.com/questions/488053/how-to-install-skype-4-3)

but with no success. I.e., I still have the same problem.

What am I missing here?

---

### Post by philinux on 2015-09-21
[http://news.sky.com/story/1556436/skype-chat-down-for-users-across-the-world](http://news.sky.com/story/1556436/skype-chat-down-for-users-across-the-world)

Could be due to that.

---

### Post by lefteris3 on 2015-09-21
Thank you philinux, most possibly it is the case...

---

### Post by Bucky Ball on 2015-09-21
Skype will not even log in for me. Just the spinning thing, so there is something amiss. Could be due to the fairly non-explanatory link posted. It gives virtually NO detail about what really actually has gone wrong.

Also, when I launched Skype this morning a window came up offering me to log in with my Microsoft account! I have never ever seen this window before. I don't even know what a Windows account is. It gave me the option of logging in with another account and clicking that option took me to a regular Skype login.

Maybe something screwed up while they were trying to implement this useless (for me) 'improvement'.

---

### Post by monkeybrain20122 on 2015-09-21
Not working here either. Problems at their end.

---

### Post by philinux on 2015-09-21
[http://heartbeat.skype.com/2015/09/skype_presence_issues.html](http://heartbeat.skype.com/2015/09/skype_presence_issues.html)

Looks like in process of getting fixed.

---

### Post by fortworthtechs on 2015-09-22
32-bit package is provided by Skype website for ubuntu 12.04 and higher. You will be able to uninstall directly on 64-bit system due to dependencies issue. Installing the old Skype from the Canonical partner&#8217;s repository will automatically install the required libraries that will be needed Skype.

---

### Post by Bucky Ball on 2015-09-22
> **fortworthtechs said:**
> 32-bit package is provided by Skype website for ubuntu 12.04 and higher. You will be able to uninstall directly on 64-bit system due to dependencies issue. Installing the old Skype from the Canonical partner&#8217;s repository will automatically install the required libraries that will be needed Skype.

Not sure you have read the rest of the thread. There is nothing wrong with the Skype install on this users machine locally. It is a problem at Skype's end. We are all getting this issue.

I haven't tried today but I would imagine it would be fixed by now. 

* Yep, fixed now. 

Always best to read all posts rather than just the first. See links in other posts here to official statements from Skype about the problem the poster, and everyone else, has been having.

---

### Post by fortworthtechs on 2015-09-27
Configure your proxy to use with Skype. Skype Icon is to be clicked and the option is to be selected. Proxy&#8217;s details are to be filled for host, port and optionally user and password in the appropriate fields. Trust worthy list is to be finding out from the Google. Hidemymass is very useful as security is important than speed. Always make sure that ports are forwarded to your PC.

---

