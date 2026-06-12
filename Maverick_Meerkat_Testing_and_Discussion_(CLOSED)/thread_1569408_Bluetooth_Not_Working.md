---
title: "Bluetooth Not Working"
date: 2010-09-06
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by CoolJohnB on 2010-09-06
When I first boot up I get a message saying a keyring requires a password, which I give, then I get the explanation mark, which tells me Bluetooth isn't working, and the option to send a report.  When I try to send the report it tells me there is a problem with my internet connection!  There is no problem with internet connection (apart from being slow! but that's down to where I am and the provider).

By the way I don't use Bluetooth but I thought this might help and I would like to stop the keyring keep coming up!

Any suggestions?

---

### Post by ranch hand on 2010-09-06
I do not use bluetooth either, don't really know what it is even, sounds like a dental problem to me.

However, to get that message to stop you could go to System>Preferences>Startup Applications and uncheck the box for it.  You may find some more there that you do not use, uncheck them too and it may help your boot time.

If you have any doubt about unchecking a box in there just don't do it.  There are things you need that you may not be aware of.   Bluetooth is not one of them.

---

### Post by CoolJohnB on 2010-09-06
Thank you for that, it has cured the Bluetooth problem.

But when I boot up I am now asked for the 'default' keyring password!?

Not sure what that's for or why it's there, more interested in how to stop it!

---

### Post by cariboo on 2010-09-06
If you have auto login set, the keyring will ask you for a password/ To stop it create a blank password.

---

### Post by ktp on 2010-09-06
> **CoolJohnB said:**
> Thank you for that, it has cured the Bluetooth problem.

But when I boot up I am now asked for the 'default' keyring password!?

Not sure what that's for or why it's there, more interested in how to stop it!

this should help you with keyring password.  Make sure to read the thread and take the best option for you.

[http://ubuntuforums.org/showthread.php?t=1533830](http://ubuntuforums.org/showthread.php?t=1533830)

---

### Post by CoolJohnB on 2010-09-06
> **ktp said:**
> this should help you with keyring password.  Make sure to read the thread and take the best option for you.

[http://ubuntuforums.org/showthread.php?t=1533830](http://ubuntuforums.org/showthread.php?t=1533830)

Read the thread very interesting now undecided whether to keep login password or not!  Although in 10.04 I had auto login set it never asked for a password until I triad installing or using sudo, so why is 10.10 different in that area?

Tried System>Preferences>Passwords and encryption keys and there doesn't seem to be anyway of editing the login password to leave it blank - or am I missing something here?

---

### Post by ktp on 2010-09-06
so if you are sure you have never used keyring for anything before, then you can just delete or move following file: 

~/.gnome2/keyrings/default.keyring

That should stop the keyring from asking password.  

**NOTE:** default.keyring file holds saved passwords for things like wireless, bluetooth, and any other application that might use it.  So at worst, your saved passwords will not be there and application will ask you for them if you remove/move the file.

---

