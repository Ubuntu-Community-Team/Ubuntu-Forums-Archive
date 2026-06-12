---
title: "Upgrade --VNC authentication failed"
date: 2008-04-21
forum: Mythbuntu
---

### Post by Chewiesw on 2008-04-21
I keep getting VNC authentication failed message when I try to use VNC in mythbuntu, it did work prior to the upgrade. I have tried uninstalling and re-installing vnc using the myth control center, I have tried changing the password to 8 characters exactly, also to under 8 characters. But I still get the same message.

I use realvnc viewer on my xp box to make the changes I need, without having to connect up to the myth box.

SSH does work however, please can someone tell me how to purge vnc completely from my system and then re-install it all from the command line.

---

### Post by funkydan2 on 2008-04-24
Not an answer but maybe a "me too"!

Just upgraded my 7.10 myth box to hardy and VNC doesn't want to play.

I can log in and see what's on the screen, however any mouse clicks or keyboard messages sent to the remote machine cause the connection to be closed.

VNC was enabled on the myth box through the mythbuntu control centre, and so I don't know which files I need to edit to get things up and running again.  (The myth box is headless.)

---

### Post by Nikas on 2008-04-24
funkydan2, yes. It's a known bug. Thought it should have been solved by now. I will NOT upgrade to 8.04 before VNC works. It's crucial for me.

---

### Post by funkydan2 on 2008-04-24
Thanks Nikas,

Yeah, with a bit more research I've worked that out too.  I'm not holding out on it being fixed by the time they release 8.04.

---

### Post by laga on 2008-04-24
Is there a bug report somewhere? The only thing I can find is [https://bugs.launchpad.net/bugs/196804](https://bugs.launchpad.net/bugs/196804) which has been closed a few months ago. Maybe you want to re-open it to get it fixed.

---

### Post by Trimble Epic on 2008-04-24
Yeah, I'm getting the same thing.  I can connect, I can see the screen, and I can move the mouse around.  Heck, I can even mouse over some things and get it to show tooltips... But the second I click anything, *poof* it disconnects, and on the box, the desktop appears to crash to a login screen (then it auto-logs back in)

---

### Post by Nikas on 2008-04-24
> **Trimble Epic said:**
> Yeah, I'm getting the same thing.  I can connect, I can see the screen, and I can move the mouse around.  Heck, I can even mouse over some things and get it to show tooltips... But the second I click anything, *poof* it disconnects, and on the box, the desktop appears to crash to a login screen (then it auto-logs back in)

I had the same problem when i upgraded to 8.04 (back to 7.10 again later). Superm1 said that it was a known bug with VNC and 8.04 but that was like 2 m ago.

---

### Post by Trimble Epic on 2008-04-24
So, is it an option for me to roll back to 7.10?

---

### Post by Nikas on 2008-04-24
[http://www.mythbuntu.org/8.04/upgrade_notes](http://www.mythbuntu.org/8.04/upgrade_notes)

"If you use VNC to connect to your Mythbuntu computer, you need to reconfigure the VNC service in the Mythbuntu Control Centre. The original VNC server used for this feature in Mythbuntu 7.10 doesn't work properly anymore, hence the need to reconfigure after updating."

Have you tried that?

---

### Post by Trimble Epic on 2008-04-24
Nope.  can it be done via remote shell?  or do I need keyboard/mouse plugged into the box?

---

### Post by superm1 on 2008-04-25
It can be done via a remote shell if you X forward (ssh -X)

We couldn't find a consistent and safe way to transition during the upgrade, so anyone with VNC just has to reconfigure in MCC and it will perform all the transition steps.

---

### Post by Trimble Epic on 2008-04-25
So, I hooked up a real keyboard/mouse and started MCC.  re-enabled VNC and entered a new password and it's working now.

---

### Post by funkydan2 on 2008-04-25
> **superm1 said:**
> It can be done via a remote shell if you X forward (ssh -X)

For those who haven't done this before (or have, but it was a long time ago at uni!) this is really simple.

Just ssh to your machine - ```
ssh -X username@your.mythbox.address
``` and once you've logged in run ```
mythbuntu-control-centre
``` from the command line, and magically the control centre will start to run, with the display on the machine that you're running ssh **from**!  (So you'll be asked for the sudo password, and then the control centre will be up and running.)

Thanks heaps - it's not too hard after all!

---

