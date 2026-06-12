---
title: "Can we install boxee as a user account?"
date: 2011-01-12
forum: Multimedia Software
---

### Post by searayman on 2011-01-12
I am on ubuntu 10.10 and want to install boxee to use as a media player for me and my roomates. My ubuntu account is password protected and I would like to create another user that when you log on (with out a password) it automatically runs boxee, and nothing else. 

Is this possible and if so how?

---

### Post by aeiah on 2011-01-13
just create a new user and as that new user, select boxxee as one of your startup applications. i dont know if ubuntu will let you create an account with no password, but you could just have the password as the letter 'p' or something.

i presume you trust your roomates enough that you don't need to lock things down too much.. just make sure your guest user cant get into your home dir and isnt part of the sudoers. you should find plenty of tutorials for that.

---

### Post by tjones00 on 2011-01-13
You could enable auto login with the boxee user set as default. Then if you wanted to switch to your account logout and switch.

You can even enable auto login and default user boxee and a boxee session without a desktop environment (gnome) running boxee as a desktop but this involves changing some system files. I haven't tested it myself configuring gdm to launch a stand alone boxee session. 

[http://forums.boxee.tv/showthread.php?t=2046&page=](http://forums.boxee.tv/showthread.php?t=2046&page=)

So you could theoretically create a custom gdm session defined as boxee by defining the session as exec /opt/boxee/run-boxee-desktop. (as described on the first post of that thread).

I've tested the boxee desktop launch method myself in ubuntu 9.10 and 10.04 it works. When I tinkered with it I didn't have gnome or gdm installed at all. So I can't give you any pointers as how to enable this as a gdm session.

Edit: snap I just realized.

1) Install boxee and create a user named boxee

2) Login as the user boxee. Create the default xsession file 

gedit /home/boxee/.xsession

Add

exe /opt/boxee/run-boxee-desktop

save the close the file

3) Go to System > Administration > Login Screen select Login as boxee automatically. User Defined Session as default session. Save and reboot.

Now it should work. Auto login/boot to boxee desktop. If you log out of boxee desktop it should bring up gdm and you can chose your user and session.

If that doesn't work you'll have to figure out how to add boxee as a session to one of the predefined gdm sessions.

---

