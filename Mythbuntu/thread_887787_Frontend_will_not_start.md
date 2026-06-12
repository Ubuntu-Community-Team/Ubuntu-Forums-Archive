---
title: "Frontend will not start"
date: 2008-08-12
forum: Mythbuntu
---

### Post by rubrboots on 2008-08-12
I am trying to switch from a knoppmyth setup to a Mythbuntu setup. I have just installed mythbuntu 8.04.1 on a computer destined to be a frontend. I chose the advanced setup and selected a frontend role. Also during the setup I entered the address and mysql password of the backend and it tested ok. The installation seemed to go well, but the computer always boots to the desktop. When a manually start the frontend from the menu, nothing happens. :confused:

---

### Post by novellahub on 2008-08-12
Run mythtv-frontend from the terminal and see what the messages say. Also, what version of Knoppmyth are you running on the backend?  You will need a Knoppmyth R5.5 or Mythbuntu 8.04.1 backend in order for the remote frontend to work.

---

### Post by rubrboots on 2008-08-12
I am running knoppmyth R5F27, so that must be the problem. I did not want to mess with the backend until I have seen the performance of Mythbuntu. Either way, this is what I get in the terminal.

```
boots@mythfe3:~$ sudo mythtv-frontend
sudo: mythtv-frontend: command not found

```

---

### Post by novellahub on 2008-08-12
> **rubrboots said:**
> I am running knoppmyth R5F27, so that must be the problem. I did not want to mess with the backend until I have seen the performance of Mythbuntu. Either way, this is what I get in the terminal.

```
boots@mythfe3:~$ sudo mythtv-frontend
sudo: mythtv-frontend: command not found

```

Knoppmyth R5F27 needs to be upgrade to R5.5 before you can use a Mythbuntu 8.04 frontend.  I am not in front of my machine right now so the command to launch the frontend may be "mythfrontend".  Why did you attempt to launch it as sudo?

---

### Post by rubrboots on 2008-08-12
When commands dont work, I usually try again with sudo. (I am certainly not a linux expert:)). I guess I will try the knoppmyth upgrade and hope it still works afterwards.

---

### Post by novellahub on 2008-08-12
Make sure you follow the upgrade guide at the Knoppmyth site:

[http://knoppmyth.net/phpBB2/viewtopic.php?t=18453](http://knoppmyth.net/phpBB2/viewtopic.php?t=18453)

Make sure you do a backup as well before the upgrade through the frontend menu.  I have done this already succesully :).

My Master backend is Knoppmyth R5.5 and have a Mythbuntu 8.04 slave backend / frontend.

---

