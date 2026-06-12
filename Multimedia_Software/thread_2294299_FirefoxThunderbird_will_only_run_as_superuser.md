---
title: "Firefox/Thunderbird will only run as superuser"
date: 2015-09-10
forum: Multimedia Software
---

### Post by theamazingjmo on 2015-09-10
Hello, as the title says, I can only launch my Mozilla software using sudo from a terminal. It just started doing this recently and I have no idea why. Any help would be appreciated. (Ubuntu 15.04)

---

### Post by TheFu on 2015-09-10
Don't use sudo with ANY GUI programs.  Why?  GUI programs tend (almost always) to write settings into the HOME directory.  sudo doesn't change the HOME from yours to /root, so root owns the files and any directories created in the process.

a) don't use sudo for GUI programs - that includes gedit.
b) run **sudo chown -R {userid}:{userid} ~/**

Fill in the {userid} based on your userid. Same for the groupid - Mine are thefu:thefu, as example.

---

