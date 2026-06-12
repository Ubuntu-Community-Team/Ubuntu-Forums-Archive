---
title: "Opera 65.x plays YouTube videos erratically."
date: 2020-01-12
forum: Multimedia Software
---

### Post by DanPerecky on 2020-01-12
I have Opera 65.0.3467.69 for Linux installed. which is the latest level/vrsn...  but none of the YouTube 'live' videos ever played. Regular YouTube videos would operate erratically... even with 800,000 bytes of Ram still available (as reported by free -k command).

The fix... or actually the workaround is to swap the Opera file: **libffmpeg.so** with the Chromium one.

Opera directory is: usr/lib/X86_64-linux-gnu/opera 
    - visible if you do a 'sudo caja'.

Chromium directory is at: /usr/lib/chromium-browser/

I found the solution here: [https://forums.opera.com/topic/27463/bug-html5-h-264-codec-videos-no-longer-working-on-opera-54-0-2952-41-ubuntu-18-04-lts-x86_64-xfce/15](https://forums.opera.com/topic/27463/bug-html5-h-264-codec-videos-no-longer-working-on-opera-54-0-2952-41-ubuntu-18-04-lts-x86_64-xfce/15)

:P

---

### Post by coffeecat on 2020-01-12
Health warning. Please do not do this:

> **DanPerecky said:**
> visible if you do a 'sudo caja'.


from [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) :

> You should **never** use normal sudo to start graphical applications as root. Using sudo with graphical apps has the potential to corrupt your environment by allowing root to take ownership of and/or change permissions on critical files that you must own. The forums frequently see panicked requests for help from users who can no longer log in after running graphical applications under sudo. 

---

### Post by DanPerecky on 2020-01-12
Coffeecat...

OK... Thanks for the warning...    

So how would you suggest that we access this directory...  What is the safe way to do this?

..

---

### Post by yetimon_64 on 2020-01-12
> **DanPerecky said:**
> Coffeecat...

OK... Thanks for the warning...    

So how would you suggest that we access this directory...  What is the safe way to do this?

..

**IF** you use "sudo" *_use the "-H" switch_*; from man sudo....
```
     -H, --set-home
                 Request that the security policy set the HOME environment vari&#8208;
                 able to the home directory specified by the target user's pass&#8208;
                 word database entry.  Depending on the policy, this may be the
                 default behavior.

```
... this will protect you from the damage of root taking over your user environment.

For running graphical apps with root I use "pkexec" here. I am not sure what the latest Ubuntu main release is using, I am running Ubuntu Mate 18.

---

