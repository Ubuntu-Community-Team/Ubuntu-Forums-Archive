---
title: "Ubuntu 9.04 + X11 forwarding + Windows XP + Putty + XMing ?"
date: 2009-04-30
forum: Networking &amp; Wireless
---

### Post by timkoop on 2009-04-30
Has anyone got Ubuntu 9.04 + X11 forwarding + Windows XP + Putty + XMing working?  I've tried and failed.

I'm using a standard install of everything, and have followed all instructions that exist, but still it doesn't work.

Has anyone out there actually got this working?  I suspect it just isn't possible.

If anyone can actually claim to have got this to work, or is willing to give me any more advice, I'll post what I've done.  

Any takers?

--
Tim

---

### Post by dmizer on 2009-05-01
I use cygwin for my xforwarding needs in Windows: [http://www.cygwin.com/](http://www.cygwin.com/)

I was never able to Xforwarding to work with putty.

---

### Post by Mud.Knee.Havoc on 2009-05-04
@timkoop

I've got it all working. I found it to be quite easy, actually.

What do you have working so far, and what isn't working?  Can you log into Ubuntu from WinXP with putty?  Do you have X11 forwarding turned on (both on Ubuntu's side, and in xming)?

---

### Post by timkoop on 2009-05-05
> **Mud.Knee.Havoc said:**
> What do you have working so far, and what isn't working?  Can you log into Ubuntu from WinXP with putty?  Do you have X11 forwarding turned on (both on Ubuntu's side, and in xming)?

Yes, I can log in with putty from WinXP.

In Putty, in the Connection->SSH->X11 options window, I have checked "Enable X11 forwarding", and the "X display location" is blank.  I have also tried putting other stuff in there.

I start Xming first before establishing the putty connection.

When I log into my Ubuntu with putty, I get the message "/usr/bin/X11/xauth:  /home/koop/.Xauthority not writable, changes will be ignored"  I don't know if this is related.

If I run the command "echo $DISPLAY" I get: "localhost:10.0"

If I run the command "xeyes" (or any other gui app) I get: "PuTTY X11 proxy: wrong authentication protocol attemptedError: Can't open display: localhost:10.0"

And in /etc/ssh/sshd_config I have uncommented these lines:
X11Forwarding yes
X11UseLocalhost yes
X11DisplayOffset 10

And I restarted sshd with "service ssh restart"


I'm open to any other ideas.

Oh, maybe I get this error because I am logged in already and it doesn't let the same user establish two X sessions.  Just a thought.

---

### Post by Mud.Knee.Havoc on 2009-05-05
> **timkoop said:**
> 
When I log into my Ubuntu with putty, I get the message "/usr/bin/X11/xauth:  /home/koop/.Xauthority not writable, changes will be ignored"  I don't know if this is related.


I'd look into that error that you're getting.  Are you logging in with the same username?  That error seems to think that you don't have permissions for that file, which you should have if you're logging into your own account.  

I just noticed [another post]("http://ubuntuforums.org/showthread.php?t=246370") where the guy was getting this error, but it went away as soon as he disabled X forwarding - which doesn't help you at all! :(

Hopefully somebody who has had this problem will see this thread.  I'll think about it a bit and see if I can't figure something out.  Sorry I'm not of any more help!

---

### Post by timkoop on 2009-05-05
> **Mud.Knee.Havoc said:**
> I'd look into that error that you're getting.

Well well well, it seems as if I have found the answer.  Thank you Mr. Havoc for the tip.  Here is the story:

I looked at that file .Xauthority and gave myself full permissions to it.  That didn't fix it, but I got a different error message (something like "error in locking authority file"), which I asked Google about, and he told me to run this command:

xauth -b quit

which I did.  Then I just plain deleted that .Xauthority file, then ran the command again.  After that, all worked well.  I can now play knetwalk in Windows.

Thank you to everyone for the continued encouragement to find the answer to this problem even after I had given up.  Well done.

---

### Post by Mud.Knee.Havoc on 2009-05-06
@timkoop

That's great news!! :)

---

### Post by jdice on 2010-07-07
Ok i got a pretty simple question, how do i change the permissions in the  .Xauthority file? Also, i'm using version 7.5.0.23 of XMing. - [Ubuntu Fix]("http://ubuntuforums.org/showthread.php?t=1144669")

---

### Post by timkoop on 2010-07-07
> **jdice said:**
> Ok i got a pretty simple question, how do i change the permissions in the  .Xauthority file?

Probably with the chmod command.  But that didn't actually fix the problem.  The problem was fixed when I deleted that file entirely.

---

