---
title: "Shared folders not accessible after reboot???"
date: 2010-04-12
forum: Networking &amp; Wireless
---

### Post by travlemon on 2010-04-12
Hi everybody,

I'm somewhat new to Ubuntu. I've been flipping through distros a lot lately, trying to find which one best suits me.  I like Ubuntu quite a bit.

I just installed Ubuntu 9.10 on a desktop pc and I'm having and issue with shared folders.   I set up a test share by right clicking on Documents in my home folder, and clicking on Sharing Options.  Then I checked the box to "Share this folder" and the box to "allow others to create and delete files in this folder".  I click "Create Share" and in a new window, it prompts me for nautilus to add permissions automatically. So I allow it to do that.

Then, from a Virtualbox Ubuntu machine, I can access the share and do everything I want to do (view, create, modify files).  However, once I reboot my Ubuntu 9.10 machine, that has the shared folder on it, it's no longer shared when I log in and check on it. 

The sharing emblem has disappeared from the folder icon, but if I go into Sharing Options, the boxes are still checked. If I simply unshare and re-share the folder, it gets the sharing emblem again and the Ubuntu virtual box can access it again. 

Can anyone help me to pinpoint the problem?  My googling hasn't gotten me much, as most Ubuntu file sharing issues seem to be about Samba (though I think this is NFS??). 

Any help is much appreciated! Sorry to type a novel!

---

### Post by Morbius1 on 2010-04-12
The sharing icon thing is a known bug and has been reported.

What's different in you description is that it's more than cosmetic ( that's what's in the original bug ).

The only sure way to determine what is shared and what is not is to issue the following command in a Terminal: **net usershare info**

You should get an output that looks like this:
> [documents]
path=/home/morbius/Documents
comment=
usershare_acl=Everyone:F,
guest_ok=y


[COLOR=Blue]EDIT:[/COLOR] If you get that output and you still can't access the share then there is something else that's the problem.

---

### Post by travlemon on 2010-04-12
> **Morbius1 said:**
> The sharing icon thing is a known bug and has been reported.

What's different in you description is that it's more than cosmetic ( that's what's in the original bug ).

The only sure way to determine what is shared and what is not is to issue the following command in a Terminal: **net usershare info**

You should get an output that looks like this:


[COLOR=Blue]EDIT:[/COLOR] If you get that output and you still can't access the share then there is something else that's the problem.

Thank you for your input! I've discovered that it's a User related error haha.  I shared it correctly.  However, it looks like I was just being impatient about the share reconnecting on the client machine.  I rebooted the "server" once more.  Again, I kept refreshing the client to see if it could connect.  Eventually it did, but I guess I was just a little impatient. 

Sorry! Thank you again for your response. If not for that, I probably wouldn't have checked it a little more carefully.

---

### Post by Iowan on 2010-04-12
To mark your thread [[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")... :D

---

### Post by travlemon on 2010-04-12
> **Iowan said:**
> To mark your thread [[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")... :D

Ah, I saw "Solved" in the drop down menu when I created it. I was not sure how to do it. I did now!  Every forum should have that

---

