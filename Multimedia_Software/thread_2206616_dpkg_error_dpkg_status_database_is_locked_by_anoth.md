---
title: "dpkg: error: dpkg status database is locked by another process"
date: 2014-02-19
forum: Multimedia Software
---

### Post by Brotell1950 on 2014-02-19
This keeps appearing when I try to use the terminal how do I get around ..

Regards

Terry

---

### Post by monkeybrain20122 on 2014-02-19
Just means that another instant of the package manager like software centre or synaptic is running. If you have any of those open then just close it. If not then maybe the updater is checking things in the background. Usually that will go away if you just wait a bit and try again. You can run top to see what is running if you are curious.

---

### Post by Brotell1950 on 2014-02-19
I have tried to close everything including shutting down and restarting. But still no go

Terry

---

### Post by monkeybrain20122 on 2014-02-19
Could be the software updater, just wait for a bit after boot. If it turns out to be the case and it bothers you you can disable automatic update checking (In the dash type Software and Updates, enter password then go to updates and change automatic check for updates to "never" in the drop down. If you do that you would have to manually check for update say with synaptic in the future, Or you can choose less drastic options like checking every week etc)

---

### Post by Alexander_Lopez on 2014-11-22
> **Brotell1950 said:**
> This keeps appearing when I try to use the terminal how do I get around ..

Regards

Terry

The easiest way to get around this is to use the terminal command gksu nautilus.  When prompted, enter your administrator password.  Afterward, you are looking for the "whoopsie" file in the lock folder and delete it.  The reason to use the "gksu" command is because you **must** be an admin in order to delete this file.  Once deleted, you can either open another terminal or just close the File Explorer and wait for the current terminal to set back to a command entry and re-enter the sudo dpkg command.

---

### Post by ibjsb4 on 2014-11-22
Try this

[http://ubuntuforums.org/showthread.php?t=1015279&p=10012663#post10012663](http://ubuntuforums.org/showthread.php?t=1015279&p=10012663#post10012663)

more here

[https://www.google.com/search?client=ubuntu&channel=fs&q=dpkg%3A+error%3A+dpkg+status+database+is+locked+by+another+process&ie=utf-8&oe=utf-8](https://www.google.com/search?client=ubuntu&channel=fs&q=dpkg%3A+error%3A+dpkg+status+database+is+locked+by+another+process&ie=utf-8&oe=utf-8)

---

