---
title: "I can watch live TV only if I run backend setup first."
date: 2009-02-08
forum: Mythbuntu
---

### Post by AKADAP on 2009-02-08
If I boot the computer and attempt to "Watch TV" from MythTV front end, the screen flashes and dumps me back in the menu.
If I have run MythTV backend setup at least once since the computer has booted, even if I don't do anything in it (immediately exit), "Watch TV" works.

I'm running Ubuntu 64 on an intel i920, using two HDHomeRun boxes. I originally installed MythTV by searching for "MythTV" under "Add/Remove..." and installing what I found. I have since installed the mythbuntu meta package. I have many other issues with MythTV, but I'll start with this one.

---

### Post by ian dobson on 2009-02-09
Hi,

The backend is required to control the tuners. Mythbackend runs as a deamon (runs in background without any user interface).

Regards
Ian Dobson

---

### Post by AKADAP on 2009-02-09
Shouldn't the daemon start automatically when I boot the computer?
I think it is running because every time I run the back end setup, I am required to approve of shutting it down.
I just checked, and it is running under the user "mythtv". I ran backend setup, and after closing backend setup, I see no difference in the mythbackend task.

---

### Post by crez79 on 2009-02-09
The backend does startup at boot. I think what is happening is the mythbackend daemon is starting before the HDHRs are discovered. When you start mythtv-setup it stops the backend and when you exit it starts it up again, but this time the HDHRs are discovered since the network is fully up. There are a few threads about it here and at least one on the [Silicon Dust]("http://www.silicondust.com/forum/viewtopic.php?t=5825") site.

You can verify this is what it is by rebooting and then ```
sudo /etc/init.d/mythbackend restart
```and that will restart the backend. If it works that is the problem and then it is just a matter of picking one of the solutions.

---

### Post by AKADAP on 2009-02-10
> **crez79 said:**
> The backend does startup at boot. I think what is happening is the mythbackend daemon is starting before the HDHRs are discovered. When you start mythtv-setup it stops the backend and when you exit it starts it up again, but this time the HDHRs are discovered since the network is fully up. There are a few threads about it here and at least one on the [Silicon Dust]("http://www.silicondust.com/forum/viewtopic.php?t=5825") site.

You can verify this is what it is by rebooting and then ```
sudo /etc/init.d/mythbackend restart
```and that will restart the backend. If it works that is the problem and then it is just a matter of picking one of the solutions.

I needed to change that command to ```
sudo /etc/init.d/mythtv-backend restart
``` before it did anything, but running that did allow me to watch live TV without running back end setup first. Now I just need to read that linked thread. Thanks.

---

### Post by AKADAP on 2009-02-10
> **AKADAP said:**
> I needed to change that command to ```
sudo /etc/init.d/mythtv-backend restart
``` before it did anything, but running that did allow me to watch live TV without running back end setup first. Now I just need to read that linked thread. Thanks.

I just implemented the script method in the linked thread. worked fine. One bug (of many) killed! Thanks

---

### Post by AKADAP on 2009-02-10
How does one change the name of the thread to include the [SOLVED] as I see on other threads?
I attempted to change the title of the first post, but that did not affect the title anywhere but the first post.

---

### Post by crez79 on 2009-02-11
Go to Thread Tools -> Mark this thread as solved.

---

### Post by AKADAP on 2009-02-11
> **crez79 said:**
> Go to Thread Tools -> Mark this thread as solved.

I guess I'm not allowed to do this. Under "Thread Tools" my only options are:
Show Printable Version
Email this page
Subscribe to this thread
Add Poll to This Thread

There is no "Mark this thread as solved" option.

---

