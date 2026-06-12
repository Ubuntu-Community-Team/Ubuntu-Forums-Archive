---
title: "Connecting to Windows share on 10.10"
date: 2010-09-08
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Casey R on 2010-09-08
So, on Lynx, I just connected to my Windows desktop's local IP address and my shared folders would show up.

Now that I've updated to Meerkat, it's not working.

I'm kind of a noob to Ubuntu so any advice would be great :)

I get the following error:

> DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

Thanks in advance! :KS

---

### Post by Casey R on 2010-09-08
I also get this error when simply clicking on Places > Network.

---

### Post by Casey R on 2010-09-08
Anyone?

---

### Post by Iowan on 2010-09-08
Moved to Maverick Meerkat Testing and Discussion.

---

### Post by chrnovx on 2010-09-08
Hi, I also have the same issue.

**Edit

This issue has been reported on launchpad

[https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/633213](https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/633213)

---

### Post by jrd on 2010-09-08
Yes this is apparently a bug in gconf (per upstream). There is a little more info in this bug report (which is a duplicate of the above one) [https://bugs.launchpad.net/ubuntu/maverick/+source/gvfs/+bug/631960](https://bugs.launchpad.net/ubuntu/maverick/+source/gvfs/+bug/631960)

My question is...can we downgrade it until the fix is released without taking out most of the system?

---

### Post by Casey R on 2010-09-08
I read a bug report earlier that indicated this issue was also present in the initial release of Lynx and then a fix was rolled out.

I hope it won't take too long for this to get fixed. Need to be able to move files around.

---

### Post by PaulW2U on 2010-09-09
I see this bug and have added a 'me too' to the bug report. You can still move your files around by mounting the share. At least that still works for me.

---

### Post by jrd on 2010-09-09
> **PaulW2U said:**
> I see this bug and have added a 'me too' to the bug report. You can still move your files around by mounting the share. At least that still works for me.

Worked for me too. Thank you! I didn't think about trying that.

---

### Post by Casey R on 2010-09-09
> **PaulW2U said:**
> I see this bug and have added a 'me too' to the bug report. You can still move your files around by mounting the share. At least that still works for me.

How do I do that?

<--- noob here lol

---

### Post by ktp on 2010-09-09
this should help with mounting samba

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by PaulW2U on 2010-09-10
Today's updates have fixed this problem, although I had to log out and back in again to be able to browse the network.

---

### Post by Casey R on 2010-09-11
> **PaulW2U said:**
> Today's updates have fixed this problem, although I had to log out and back in again to be able to browse the network.

Yep - todays update fixed the problem for me too! :)

---

### Post by jrd on 2010-09-11
> **PaulW2U said:**
> Today's updates have fixed this problem, although I had to log out and back in again to be able to browse the network.

Confirmed, it's fixed now. The bugs are going away fast :D

---

### Post by gseward on 2010-09-11
Networking has been broken in Ubuntu for at least a couple of years, in the sense that clicking on the Network item in Nautilus did not open up the network. It was possible to somewhat fix this by editing smb.conf, but it was quirky, and you could frequently see only Windows computers, not other Linux computers..
In the early Alpha versions of 10.10 this was entirely fixed, Network opened up instantly, all I would have to edit was the workgroup name and even that was not really required. I just downloaded Ubuntu 10.10 Beta [and a couple of later daily builds] and now it is even more broken, click on network and it hangs for a couple of minutes and gives a message that the wrong application is being used. BTW I have installed Samba. Also if I go to System/Administration/Network Tools, the tools are all broken, I can't even ping a computer that I know the ip address of. I can ping that computer from Terminal, no problem.
So today I reinstalled the August 25 Daily build, and was ecstatic to see how nicely and instantly the network opened up,[several windows machines and two Ubuntu machines] but alas after I updated Ubuntu it was broken again.
I had just talked a small business client of mine into letting me put Ubuntu on two of his computers, but now I will have to put that on hold until this is fixed, as access to the network is essential to him.
Will someone PLEASE fix this.
Thanks
Gil Seward

---

### Post by jrd on 2010-09-11
If stability is super important to your business client you may want to install Debian stable (or an older version of Ubuntu) and add all the codecs etc for them. I'm not trying to down Ubuntu but for the most part running the newest version always means more bugs, which is fine just for a desktop but if they need this for mission critical stuff I would be more conservative.

---

