---
title: "Myth shutdown"
date: 2008-01-11
forum: Mythbuntu
---

### Post by jolly79 on 2008-01-11
Hi

I have one of those black Hauppage remotes, and i cant figure out how to shut the box down with out a keybord.

The best way would really be if when i choose:
Yes, exit and shutdown

It would actually shutdown, and not just return to the desktop.

Is there a way to make it shutdown that way??
I have change the shutdown command to "poweroff" in myth, but it dosent have eny effect.
have enybody gotten the power off button on the remote working yet??
Been lookin every where in this forum, and cant seem to find eny help on this.

hope to here from someone that can point me in the right direction.

-jolly79

---

### Post by laga on 2008-01-12
Hi,

you're right - that's one of the things that's not working properly in Mythbuntu gutsy. Here's what I'd do: use visudo to extend the sudoers file to let you run /sbin/poweroff or /sbin/shutdown -h now without having to enter a password. Then enter that command in MythTV as the "shutdown command", including "sudo", eg "sudo /sbin/shutdown -h now". If you don't know how to edit /etc/sudoers (which you shouldn't have to do normally, granted), I'm pretty sure the Ubuntu wiki or Google will let you find out how it works.

Always use visudo for that task! It includes some sanity checks which may prevent you from locking you out of your system.

Hope that helps :)

---

### Post by jolly79 on 2008-01-12
Thanx

i have been looking into the visudo option myself.

Can you by eny chance write whats in your /etc/sudoers file.

Because i cant get i working.

---

### Post by jolly79 on 2008-01-12
ok got it working...

Put this in the end.

%mythtv ALL = NOPASSWD: /sbin/poweroff

and just use this command i myth shutdown.

sudo /sbin/poweroff

If enybody should run into the same trouble as me :-)

---

