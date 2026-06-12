---
title: "Natty Terminal"
date: 2011-01-26
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by skymera on 2011-01-26
Right, hi guys.

Can't find the Natty testing section, so here will do.

Anyway, EVERY time I open the terminal, this appears


```
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

```

I've been using Ubuntu for over 4 years....

Right, I got that the first time ¬_¬ How do I stop this from appearing?

Thanks!

---

### Post by mc4man on 2011-01-26
There natty sub-forum is here.
[http://ubuntuforums.org/forumdisplay.php?f=394](http://ubuntuforums.org/forumdisplay.php?f=394)

As far as that sudo 'message' - 
it seems it will be seen every time, maybe when there is an update to sudo it will go away.

The issue I have with the current sudo in natty is that the admin. timeout only applies to the current instance.
So if you were to go  sudo apt-get update in a terminal it would ask for a password. Do it again in the same terminal or sudo <whatever> and no password required. Close and or open another terminal and sudo <whatever> - a password will be required.
For myself have reverted back to a sudo version that works right and as a bonus doesn't show the message.

---

### Post by hrhnick on 2011-01-27
To make the message go away:

Create a blank filed named ".sudo_as_admin_successful" in your home directory.

---

### Post by dlpfmVfH on 2011-01-27
thanks, didn't know that one...

---

### Post by Gourgi on 2011-01-27
here is another (standards compliant but more complicated) way 
[http://keramida.wordpress.com/2010/11/08/sudo-hints-and-hushlogin-in-debian-or-ubuntu/](http://keramida.wordpress.com/2010/11/08/sudo-hints-and-hushlogin-in-debian-or-ubuntu/)

---

