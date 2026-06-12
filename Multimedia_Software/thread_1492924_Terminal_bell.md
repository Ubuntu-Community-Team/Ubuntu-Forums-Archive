---
title: "Terminal bell"
date: 2010-05-25
forum: Multimedia Software
---

### Post by narasimhan1990 on 2010-05-25
i just installed ubuntu 10.04 a few days ago. the terminal beep is not working. 

i have checked in the terminal settings as well (Edit->Current profile->General) that "terminal bell" is indeed checked.

though its not a big problem. i just want to know the reason.

---

### Post by ajgreeny on 2010-05-25
Are other sounds working?  A lot of new installs seem to find that sound is muted for some inexplicable reason, and needs to be un-muted using alsamixer or some other method.

---

### Post by narasimhan1990 on 2010-05-25
i can hear the welcome music when i log in.

---

### Post by narasimhan1990 on 2010-05-29
any solution to my problem

---

### Post by evilxsystems on 2010-09-13
same problem here...sound works but terminal bell doesn't and box is checked...actually need the bell for an application I'm writing....
echo -e '/a'  makes no sound

---

### Post by fixitdude on 2011-06-09
From terminal type:

sudo modprobe pcspkr

Then try the beep. That is only temporary.

If that worked, edit /etc/modules and add "pcspkr" as the last line in the file.

pcspkr

That worked for me after reboot.

If not, read here...

[https://answers.launchpad.net/ubuntu/+source/beep/+question/111077](https://answers.launchpad.net/ubuntu/+source/beep/+question/111077)

Oh, and check your control panels for sound/audio and see if you have it set to use the system speaker.

If the damn terminal bell is so loud that the developer felt it necessary to make the system bell off as default, and if they are just so smart, why don't they just reach in there and pull the speaker connector?

---

