---
title: "Remote Desktop and Keyring problem"
date: 2011-02-23
forum: Networking &amp; Wireless
---

### Post by weaver4 on 2011-02-23
I am trying to use remote desktop to my Ubuntu 10.10 machine.  But when I connect it ask for my password and then the remote screen does not show up.  I go look at the monitor on the Ubuntu machine and this dialog box is displayed:
"Enter Password for keyring 'Default' to unlock"
Once I enter my password the desktop shows up on my  remote machine.

How do I fix this?  I am not going to my Ubuntu machine every time I want to do remote desktop; kind of defeats the purpose.

I do auto-login.

I want to get this machine to be "headless".  So I need to get it set up so that I can login remotely using vnc.

---

### Post by Bullwinkle_Moose on 2011-03-19
If you find a GOOD answer to this I'd love to know too.  Best I've found is you go to System | Preferences | Password and Encryption Keys and then follow the instructions at [http://ubuntu-help.blogspot.com/2011/01/ubuntu-enter-password-for-keyring.html](http://ubuntu-help.blogspot.com/2011/01/ubuntu-enter-password-for-keyring.html)

The problem with that is that it disables the VNC password completely, which probably isn't a horrible thing if you don't open it up to the outside world, but it's a step behind Karmic, where you could password protect VNC AND not have the dialog box, which as you say, defeats the whole purpose of using VNC!

---

### Post by ShiftyPowers on 2011-05-17
this is such a pain the butt. I have the same issue which pretty much makes a headless server out of the question.  :(

---

### Post by flotoonie on 2011-06-02
I am also having an issue with this.  Can anyone help?

---

### Post by Zeerots on 2011-06-02
Please remove this comment.

---

### Post by bwhite757 on 2011-07-12
Bumping up...  Looking for an answer for this as I'm wanting to run a headless setup in a remote location about 60 miles from me.  Need the ability to remote into it...

---

### Post by bwhite757 on 2011-07-12
Nevermind, found a working solution on the last thread of this post:

[http://ubuntuforums.org/showthread.php?t=1502232](http://ubuntuforums.org/showthread.php?t=1502232)

---

### Post by amathewk on 2011-10-29
As reported in the thread in the above post, this workaround did not work for me in 11.04.

---

