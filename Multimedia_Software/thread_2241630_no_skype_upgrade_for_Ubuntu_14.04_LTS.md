---
title: "no skype upgrade for Ubuntu 14.04 LTS"
date: 2014-08-27
forum: Multimedia Software
---

### Post by zoltanbb on 2014-08-27
Skype has notified me that support for the skype version I am using will be discontinued. They suggested to download the latest version. To my dismay they apparently do not provide with a new version
for my ububtu distribution 14.04 LTS. Could anybody suggest a solution?
zoltanbb

---

### Post by anchitsingh9 on 2014-08-27
What version of skype are you using..? Is it 4.2..??
The latest version for linux is 4.3
If you are still on 4.2, uninstall it.
Go to Software-Center>Edit>Software-Sources>Other-Software.
Check the Canonical-Partners and Canonical-Partners(Source).
Open terminal, then :
> 
sudo apt-get update
sudo apt-get install skype

This will install Skype 4.3

---

### Post by martinr on 2014-08-27
If you upgrade to 4.3, you'll be in a world of pain.
Have a look at this instead: [Skype version spoofing (howto stick with your old skype version) ]("http://ubuntuforums.org/showthread.php?t=2240954")

---

### Post by ockac23 on 2014-08-27
I have done the steps above, skype still does not work. Does not start.
Message in terminal: Aborted (core dumped)

My system: Ubuntu 14.04.1 LTS (32 bit)
skype 4.3 installed

---

### Post by martinr on 2014-08-29
> **ockac23 said:**
> I have done the steps above, skype still does not work. Does not start.
Message in terminal: Aborted (core dumped)

My system: Ubuntu 14.04.1 LTS (32 bit)
skype 4.3 installed

As I said, you'll be in a world of pain with 4.3.
Install the last 4.2 version and try the spoofing instead.

---

### Post by monkeybrain20122 on 2014-08-29
I have 4.3 and it was upgraded normally through the software manager (I installed from the Partner's repository) I have not experienced a 'world of pain'.

---

### Post by martinr on 2014-08-30
> **monkeybrain20122 said:**
> I have 4.3 and it was upgraded normally through the software manager (I installed from the Partner's repository) I have not experienced a 'world of pain'.
Good for you, but have a look [here]("http://community.skype.com/t5/Linux/Having-trouble-signing-in-Retirement-of-older-versions-of-Skype/td-p/3439685/page/4") for all the people experiencing loads of trouble. You probably never use any of those features, do you?

---

### Post by monkeybrain20122 on 2014-08-31
martinr

re your link

 1) I have no problem with chat history 2) I always use pulseaudio since I can remember, always works great. Honestly I have no idea what the fuzz is all about, I have installed Ubuntu and other distros on a variety of hardware, never had any issue with pulseaudio 3) Camera works perfectly 4) I have not used screen sharing but I can test it next time. 5) It is subjective, I don't mind the UI.

BTW I even manage to get the webcam of my roommates' old Acer 5100 laptop to work. This webcam has always been problematic with Linux so it took some googling and messing around, I set it up to work with skype 4.2, upgraded to 4.3, still works after some trivial changes.

---

### Post by ockac23 on 2014-09-03
> **martinr said:**
> As I said, you'll be in a world of pain with 4.3.
Install the last 4.2 version and try the spoofing instead.


Spoofing worked for me!
Great!!! Thanks!
Now I can connect to M$ server with skype 4.2.0.11.

Can we skip the 4.3 update and update later maybe directly to skype 4.4., when available?

---

### Post by monkeybrain20122 on 2014-09-08
Checked share desktop, no problem either.

---

