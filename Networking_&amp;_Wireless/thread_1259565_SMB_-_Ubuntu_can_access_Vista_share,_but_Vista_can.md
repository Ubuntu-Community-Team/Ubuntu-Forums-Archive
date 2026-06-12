---
title: "SMB - Ubuntu can access Vista share, but Vista cannot access Ubuntu share"
date: 2009-09-06
forum: Networking &amp; Wireless
---

### Post by nsacco on 2009-09-06
*I had already posted this thread yesterday morning, but I messed up the thread title, which was posted as just 'Smb - ', so I'm remaking the thread.*

I've got a strange issue concerning Samba on Ubuntu. I've got a Vista PC, which is my desktop machine. I recently built an HTPC, running Ubuntu Jaunty for XBMC. The problem I'm having is this:

The Ubuntu machine can see my Vista share on the network
The Ubuntu machine can access the Vista share
The Vista machine can see my Ubuntu share on the network
The Vista machine CANNOT access the Ubuntu share

I've read up on this on Google, and I've ruled out two things:

It's not the Vista machine, because my XP laptop has the same exact problem
It's not the router, because I've reset the power on it, and even purchased a new one (I've been needing to replace it anyways)

What confuses me even more is that I CAN get it to work. Here's what I do:

Uninstall 'samba' and it's dependencies
Try to share a folder. This causes Ubuntu to notice that samba isn't installed.
Let Ubuntu install samba, and share the folder

And now it'll work. The Vista machine can access, read, and write on the share. But if I restart, I lose that access. The Vista machine can still see the share after I refresh the Network window, but I get an error: 0x80070035.

I have tried using the share name 'XBMC' and the IP address, neither work. I can ping the IP address of the Ubuntu machine from the Vista machine, but that's yet. Yet, the Ubuntu can still access the Vista share. What possibly could be going on here?

Oh, real quick, just FYI, the Ubuntu and Vista machines use wire network, XP laptop is wireless.

---

### Post by uylug on 2009-09-06
Btw, do you get a login dialog when trying to access shares stored on the ubuntu machine?

If so, what happens if you enter your user credentials?
What happens if you enter 'guest' as username without any passwords?

Also, make sure there are no permission issues involved. I've been stuck with issues like this for days because of simple permission issues.

---

### Post by nsacco on 2009-09-06
> **uylug said:**
> Btw, do you get a login dialog when trying to access shares stored on the ubuntu machine?

If so, what happens if you enter your user credentials?
What happens if you enter 'guest' as username without any passwords?

Also, make sure there are no permission issues involved. I've been stuck with issues like this for days because of simple permission issues.

Yes, I login using my Ubuntu user credentials, and it'll work.. before the reboot, of course.

Never tried guest.

How would I see if I have permission issues? I've had the problem with /home/.rmsc or whatever having permissions problems, but I've fixed it.

---

### Post by uylug on 2009-09-06
Do you think you could post the output of:

```
cat /etc/samba/smb.conf
```before and [B]after rebooting?

[/B]So basically, it works as expected before rebooting. Your problem is that settings are not being stored, right?

---

### Post by nsacco on 2009-09-06
I just did a reinstall of samba, and it isn't working at all. I install it by uninstalling the samba package (with its two dependencies), and then attempting to share a folder, which makes me install Samba. It then says I should restart my session. I click the button to do so, but nothing seems to happen.

Usually, by now I'd be able to see each other's shares.. but it isn't happening now.

[http://pastebin.com/m7f29aed6](http://pastebin.com/m7f29aed6)

Actually, you know what? I think I know why it isn't working right now; I'm using a different smb.conf, that I got off Synaptic. How do I get a new, clean smb.conf?

---

### Post by yeats on 2009-09-06
The problem is with Vista.  It added a new layer of complexity in its networking model, and I've had a *devil* of a time getting Vista to play well with the other computer children.  I don't have any advice for you except to study up on the way Vista handles non-Vista network shares :-)

---

### Post by nsacco on 2009-09-06
I do have a solution: use a program to mount network drives via SSH. I'm doing it now, it works great, and no more messing with Samba.

---

