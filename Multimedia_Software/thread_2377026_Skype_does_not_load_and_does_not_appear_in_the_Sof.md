---
title: "Skype does not load and does not appear in the Software Center"
date: 2017-11-08
forum: Multimedia Software
---

### Post by mortiba on 2017-11-08
Hi all,

Since yesterday Skype is not working on my computer (Ubuntu 16.04.3 LTS, 64 bits). I can open it and enter my data but after some seconds loading, it quits. When I try to open it from the Terminal, the same happens, and no warning/error messages appear. 
I uninstalled it and then reinstalled it many times, in different ways, but I have the same problem. Besides, when I uninstall it, it is never appearing in my Software Center, which is strange (I have the Canonical options clicked)...

Thank you for the help!

María

---

### Post by kostkon on 2017-11-08
What's your CPU? Latest Skype requires a SSE3 capable CPU.

---

### Post by mörgæs on 2017-11-08
> **kostkon said:**
> What's your CPU? Latest Skype requires a SSE3 capable CPU.

Really? Isn't SSE2 enough?

---

### Post by kostkon on 2017-11-08
> **mörgæs said:**
> Really? Isn't SSE2 enough?
According to Microsoft, no :(
[ATTACH=CONFIG]277464[/ATTACH]
Nonetheless, they state it's an known issue and they are working on a fix.

---

### Post by mortiba on 2017-11-08
How can I know this? I'm not very familiarized with computers.
And, another thing, the Software Center is not working in general. I tried to install chrome, but when I click Install, it does nothing.
Besides, when I try to install something in the terminal I get this message:

"dpkg: error processing archive google-talkplugin_current_amd64.deb (--install):
 cannot access archive: No such file or directory"
  


thanks!

---

### Post by kostkon on 2017-11-08
> **mortiba said:**
> How can I know this? I'm not very familiarized with computers.
It's actually called "SSSE3", I always miss the last 'S'. Anywho, what happens when you run this command in the terminal? You should get one or more lines of output, the same number of lines as your CPU cores:
```
cat /proc/cpuinfo | grep -io ssse3
```
> **mortiba said:**
> And, another thing, the Software Center is not working in general. I tried to install chrome, but when I click Install, it does nothing.
Besides, when I try to install something in the terminal I get this message:

"dpkg: error processing archive google-talkplugin_current_amd64.deb (--install):
 cannot access archive: No such file or directory"
Are you running that command from same folder that this file is in?

---

### Post by mortiba on 2017-11-09
Hi kostkon,

When I run that command I get 8 times ssse3.

About the dkpg, yes, I think I was in the same folder.

---

### Post by mörgæs on 2017-11-09
To make the confusion complete there is both an SSE3 and an SSSE3 but according to the screen shot posted SSSE3 is the one in question. 

So happy that most of my friends use Hangout.

---

### Post by monkeybrain20122 on 2017-11-09
Maybe your configuration is somehow corrupt? Open the hidden folder .config and delete the the subfoldder skypeforlinux and see if restarting skype works.

---

