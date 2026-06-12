---
title: "Wifi notification + multiple users"
date: 2010-11-01
forum: Networking &amp; Wireless
---

### Post by Fastgalix on 2010-11-01
Hi all,

I am running Ubuntu 10.10 and I am trying to set up several accounts on one computer. When switching from one account (let's call it A) to the other (B) to check that everything works fine I noticed that the wifi in the notification area disappeared. I checked and the wifi is working, the user is allowed to "play" with the wifi and the network manager box is checked in the startup application menu. Furthermore, when I first log on B and switch to A the problem appears on A. I should also precise that the notification area is there and I tried to add it again and "killall" it via terminal but it didn't solve the problem...

Do you experience the same and/or do you have a fix ?

Thank you very much

Bests

Fastgalix

PS : I looked for fix to this problem but couldn't find any; if this is a repost please forgive me :P

---

### Post by JohnFr on 2010-12-22
I am having the same problem.  I suspect this is done intentionally as
a "security" issue.  This is a real problem since it is necessary to 
access this applet to turn on vpn.

A very similar thing happened to me with pulseaudio.
Only the first person logged in could access the sound.  This was fixed
by making sure all users are members of the 'pulse-access' group, and 
enabling system mode in /etc/default/pulseaudio and rebooting.  I don't
know a similar solution.

---

### Post by zinzolin on 2011-01-19
Hello,

I have the same problem with the visibility of nm-applet on the notification area. I find this really annoying. 
Did you guys find a solution to this problem ?

Thanks for the help,

Nicolas

---

### Post by zinzolin on 2011-01-19
Hello,

I have the same problem with the visibility of nm-applet on the notification area. I find this really annoying. 
Did you guys find a solution to this problem ?

Thanks for the help,

Nicolas

---

### Post by zinzolin on 2011-01-19
Hello,

I have the same problem with the visibility of nm-applet on the notification area. I find this really annoying. 
Did you guys find a solution to this problem ?

Thanks for the help,

Nicolas

---

### Post by grahammechanical on 2011-01-19
Is the wireless connection ticked as Available to all users?

What user permissions are you giving to each user?

Regards.

---

### Post by grahammechanical on 2011-01-19
Is the wireless connection ticked as Available to all users?

What user permissions are you giving to each user?

Regards.

---

### Post by zinzolin on 2011-01-19
Hi grahammechanical !

> Is the wireless connection ticked as Available to all users?
The wireless connection is available to all users, but only the one who has logged first is able to manage the wifi. The only way to manage the wifi for a secondary user is to kill nm-applet and to restart it. It then appears on its notification area.

> What user permissions are you giving to each user?
All have administrators privileges.

Thanks,

Nicolas

---

