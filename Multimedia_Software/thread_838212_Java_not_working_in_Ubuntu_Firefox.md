---
title: "Java not working in Ubuntu Firefox"
date: 2008-06-23
forum: Multimedia Software
---

### Post by AndrewCooper on 2008-06-23
My wife likes to play the online games at Yahoo.  These games require Java.  I've recently installed Ubuntu 8.04 on a laptop (a Thinkpad T43) and tried to go to Yahoo to see if the games would load and play.  They don't.  Instead I get a message saying I need to make sure Java is enabled on my browser.  I check and Java is enabled on my browser.  At least the checkbox in the Preferences menu is checked on Firefox.  I used Synaptic to download and install Cacao and Jamvm, just in case those VM's were needed for some reason.  The games still don't work.  Has anyone run into this issue before?  If so, can you point me in the right direction?  I don't mind reading some instructions and figuring things out, I just can't find where to look for the answer at the moment which is frustrating.

Andrew Cooper

---

### Post by ahbart on 2008-06-23
The checkbox you are referring to is probably not java but javascript. Those are completely different things. 
If you type 'about:plugins' in the address bar of firefox, do you see something like 'GCJ Web Browser Plugin' of 'sun jave plugin'?
If not you should install one of these via synaptic. make sure you select the browser plugin also.
icedtea-gcjwebplugin or sun-java6 something. With the last one (Sun's) you have probably less trouble with java games, but it is not (completely) opensource. 

(If you have an X86_64 install only the teatime version will work) ;-(

---

### Post by AndrewCooper on 2008-06-23
Actually, it's a Java checkbox.  It is right below the JavaScript checkbox.  Both of them are checked.  I will try your suggestions when I get home this afternoon and can get on my Ubuntu box.  Thanks for the suggestions.

Andrew

---

### Post by ahbart on 2008-06-23
You're right. I've never seen this before. maybe new. :confused:
Good luck

---

### Post by Pjotr123 on 2008-06-23
You need Sun Java JRE for Yahoo Games ( I play chess there myself). :-)

Apply this how-to for 100 % multimedia support, including Java:

Step 1:
[http://ubuntutip.googlepages.com/multimediaubuntustep1](http://ubuntutip.googlepages.com/multimediaubuntustep1)

Step 2:
[http://ubuntutip.googlepages.com/multimediaubuntustep2](http://ubuntutip.googlepages.com/multimediaubuntustep2)

---

### Post by ahbart on 2008-06-23
I would prefer the steps as shown on this site. :)
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)
This includes java

---

### Post by AndrewCooper on 2008-06-23
> **ahbart said:**
> You're right. I've never seen this before. maybe new. :confused:
Good luck

Well, they just released a new Firefox.  It might have been added in it.

Thanks for the links you guys.  I'll definitely use them.

Andrew

---

