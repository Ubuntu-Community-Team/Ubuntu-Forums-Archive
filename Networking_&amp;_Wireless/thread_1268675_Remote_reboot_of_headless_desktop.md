---
title: "Remote reboot of headless desktop"
date: 2009-09-17
forum: Networking &amp; Wireless
---

### Post by Docaltmed on 2009-09-17
I've searched and searched, and perhaps I'm overlooking something, but I just can't figure out what the problem is.

I have an Ubuntu box running 9.04 (call it PC1) which I am using as a remote desktop. It is not equipped with either a keyboard or a display.

I can connect to it via ssh or vnc from my laptop, running 8.10. (call this PC2)

When PC1 has been rebooted, I can ssh into it and start vncserver manually, at which point I can then use vnc on PC2 to access the GUI. However, even though I am logging in as the same user which, locally, is an administrator, I have no administrative privileges and several of the folder icons on the desktop are grayed out.

But if I connect a keyboard and display to PC1 and log in locally, I can then connect from PC2 via vnc and have full privileges.

Is there any way I can remotely boot PC1 and access the GUI without first having to log in remotely?

I have also tried setting up XDMCP to log in remotely that way. It worked exactly once; since that time, PC2 has been unable to locate PC1, even when given the correct IP address.

I'm lost. Any help would be greatly appreciated.

---

### Post by chili555 on 2009-09-17
Does it work any better if you do:```
ssh -l user PC1
```After PC1 accepts your login, do:```
sudo reboot -f
```If you do not have PC1 in the hosts file of PC2, of course, you will have to specify the IP address.

This should work fine if PC1 is set up to log in automatically to a specific user. Otherwise, it will sit there waiting for a user name and password.

---

### Post by Docaltmed on 2009-09-17
Thank you, Chili! It works *almost* perfectly.

After inputting the commands you suggested, I can log into PC1 via XDMCP from PC2 without difficulty.

The only hangup now is that, although I can log in, perform administrative tasks, etc., I cannot get PC1 to play any sound. This is somewhat important, as I use PC1 to play background music in the office. 

If I plug in the display and keyboard locally and log in, there is no problem. And after a local login, I can use ssh or vnc to access PC1 and have it play music with the output coming from PC1's speaker port. 

But if I reboot and use the method you described, I cannot get sound out of PC1's local speaker.

So, I'm 99.9% there. If you or anyone else has any more suggestions, I'll be glad to take them.

(And I'm also going to study up on how those two commands made a difference. After a quick glance at the man pages, I can't figure it out, but this is truly intriguing me at this point).

---

