---
title: "Using KGet through the network (LAN)"
date: 2009-04-09
forum: Networking &amp; Wireless
---

### Post by kumoshk on 2009-04-09
I have some extremely huge files that I need to copy from one computer to another through a local area network. I'd rather not have to copy them all at once, since it'll take hours, and I'd like to do things on my computer that require a restart. Therefore, I was wondering if it is possible that instead of mounting a network share and copying files over I could download using KGet. KGet allows you to stop/resume/etc. You can restart your computer and pick up where you left off.

Can you access files of network shares through Firefox?

Lest you be tempted to move this to the Kubuntu prefix, I don't use KDE. I use Gnome (I just like KGet is all).

---

### Post by Ayuthia on 2009-04-09
> **kumoshk said:**
> I have some extremely huge files that I need to copy from one computer to another through a local area network. I'd rather not have to copy them all at once, since it'll take hours, and I'd like to do things on my computer that require a restart. Therefore, I was wondering if it is possible that instead of mounting a network share and copying files over I could download using KGet. KGet allows you to stop/resume/etc. You can restart your computer and pick up where you left off.

Can you access files of network shares through Firefox?

Lest you be tempted to move this to the Kubuntu prefix, I don't use KDE. I use Gnome (I just like KGet is all).

If it is from Linux to Linux, you can use NFS mounts to access your network files.  You can then access them through Firefox via file:///...

Another option would be to install Apache and then move the files to /var/www and then you can access them like a web page.

---

### Post by kumoshk on 2009-04-09
Yep, it sure is Linux to Linux. Both Jaunty Jackalope betas. Both use Ext4 file systems. One is 32-bit and the other is 64-bit.

Thanks for the tips! I'll have to check out this NFS thing. I wonder why samba is the network default protocol.

---

### Post by Ayuthia on 2009-04-09
> **kumoshk said:**
> Yep, it sure is Linux to Linux. Both Jaunty Jackalope betas. Both use Ext4 file systems. One is 32-bit and the other is 64-bit.

Thanks for the tips! I'll have to check out this NFS thing. I wonder why samba is the network default protocol.

Samba works with Windows and Linux where I don't think that NFS works with Windows.  Konqueror also works with Samba and KGet so that would be another option.

---

### Post by kumoshk on 2009-04-09
Ah, thanks.

Hmm. I'm having trouble mounting nfs shares. How do I go about mounting and accessing them?

---

### Post by Ayuthia on 2009-04-09
> **kumoshk said:**
> Ah, thanks.

Hmm. I'm having trouble mounting nfs shares. How do I go about mounting and accessing them?

I have used this thread in getting mine set up a while back:
[http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)

Hope it helps.

---

