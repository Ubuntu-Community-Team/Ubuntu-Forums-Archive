---
title: "Ubuntu One"
date: 2010-08-26
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by sgage on 2010-08-26
Does Ubuntu One _do_ anything? I have tried to get it going to test it out, but I'll be darned if I can get to any screen that offers a chance to "add a computer" to the setup. The website is confusing and circular, and the instructions don't match what happens when you try to follow them. In short, WTF?

---

### Post by zenarcher on 2010-08-26
Ubuntu One was working fine for me (Kubuntu 10.00) until a bit over a day ago.  Then, it quit working.  All I have is "trying to establish a connection."  It's that way on both of my systems.  However, prior to that time, it was just fine...let me add a second computer and everything was working beautifully.

Cheers,
zenarcher

---

### Post by sgage on 2010-08-26
I can log in with my SSO ID, but nowhere can I find a page where there is a button to allow me to add a computer. I just get sent round and round, and it's frustrating as heck.

---

### Post by kyleabaker on 2010-08-26
It seems to "work" for me in that files are synchronized, but it never gives me a successful sync icon.

Online, everything is sync'd properly, but for some reason all of my folders inside of the Ubuntu One folder have this attention icon (even though they are completely sync'd)..

[IMG]http://a.imageshack.us/img801/1882/screenshothks.png[/IMG]

---

### Post by mc4man on 2010-08-26
> I can log in with my SSO ID, but nowhere can I find a page where there is a button 

You may want to look thru the ubuntu one sub forum. 
On the machine you want to add, when opening Ubuntu One you should get a browser window pop up to add that computer,

The couple of times I haven't I've resolved by going System -> Pref's -> Passwords and Encryption Keys - expanding 'password' and if there is a token for UbuntuOne then deleting it and trying again.

Otherwise maybe read here..?
[http://ubuntuforums.org/showthread.php?t=1531179](http://ubuntuforums.org/showthread.php?t=1531179)

---

### Post by ratcheer on 2010-08-26
I had the same problem the first time I tried to add a computer. I found a support article and ran a recommended command, but it did not help.

On a whim, I restarted my computer and tried again. The link to add a computer was there. I have had no trouble with it since then, and I have added three more computers.

Tim

---

### Post by sgage on 2010-08-27
I have tried everything I could think of, and searched the forums and other people's blogs. There are some workarounds posted, but none of them work for me. 

Like I said, I have a U1 account, I can log in and see my dashboard and files and such, but nowhow can I get to a page that lets me add a machine. If any of you are able to, how about posting the URL of the page that has the "add machine" button on it? I'd sure appreciate it.

---

### Post by ratcheer on 2010-08-27
This is the command I ran. It may have fixed the problem, but if so, it only worked after a reboot. Which doesn't make any sense...

```
u1sdtool -q; killall ubuntuone-login; u1sdtool -c
```

I hope it helps.

Tim

---

### Post by mc4man on 2010-08-27
> If any of you are able to, how about posting the URL of the page that has the "add machine" button on it? I'd sure appreciate it.

There is no url so to speak, you need the have *the computer you're on and trying to add open the browser page that's used for adding a computer.*

(you can't add a computer from another computer if that's what you're trying

Did you find a ubuntuone token on the machine you're trying to add?
I assume you tried either of the [2 methods here]("https://wiki.ubuntu.com/UbuntuOne/FAQ#How%20do%20I%20add%20my%20computer?") or [here]("http://ubuntuforums.org/showthread.php?t=1531179") #8

---

### Post by sgage on 2010-08-27
> **mc4man said:**
> There is no url so to speak, you need the have *the computer you're on and trying to add open the browser page that's used for adding a computer.*

Did you find a ubuntuone token on the machine you're trying to add?
I assume you tried either of the [2 methods here]("https://wiki.ubuntu.com/UbuntuOne/FAQ#How%20do%20I%20add%20my%20computer?") or [here]("http://ubuntuforums.org/showthread.php?t=1531179") #8

Yes, I've tried them all. I stop the syncdaemon. Then, "killall ubuntuone-login" doesn't find a process called ubuntuone-login, since it now seems to use ubuntu-sso-login. So I kill that process, run u1sdtool -c, and nothing happens at all.

There is no ubuntuone token on the machine.

I have spent hours on this. I've tried everything. I've purged everything ubuntuone from my machine and reinstalled. I tried subscribing again with a different email address. No joy.

I was all excited when I noticed there was a bunch of ubuntuone-related packages in the updates this morning. Still no joy.

Why can't they just stick an "add machine" button on the dashboard? That would seem to make sense. Or on the page you go to to see what machines have been added. Either or both of those places would seem to be logical.

Oh well.

---

