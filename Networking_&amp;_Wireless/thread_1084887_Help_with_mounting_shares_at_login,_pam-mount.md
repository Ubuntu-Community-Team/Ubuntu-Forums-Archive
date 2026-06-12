---
title: "Help with mounting shares at login, pam-mount?"
date: 2009-03-02
forum: Networking &amp; Wireless
---

### Post by jstars on 2009-03-02
I am a home user that is looking for help mounting windows network shares (from a NAS) on a ubuntu machine with two different users (my wife and I). I would like to mount the samba shares according to the same username and password used for each gnome account. I understand that [pam-mount]("http://pam-mount.sourceforge.net/") can do this but I cannot find documentation on how to set it up anywhere.  Is this the best way to do this?

---

### Post by dmizer on 2009-03-02
Please see the second link in my sig. :)

---

### Post by jstars on 2009-03-03
I reviewed the first two pages of that post but there are 87 pages! Is there anything in there that discusses how to mount shares at login? I don't think I can mount them at boot because I have two users.

---

### Post by dmizer on 2009-03-03
> **jstars said:**
> I reviewed the first two pages of that post but there are 87 pages! Is there anything in there that discusses how to mount shares at login? I don't think I can mount them at boot because I have two users.

Do both users need to have access to different shares?

---

### Post by jstars on 2009-03-03
> **dmizer said:**
> Do both users need to have access to different shares?
Right now no. However, the next step will be to add my kids as users. In this case they will need different access to different shares. Windows makes this very easy as each windows username/password is the same as the samba username/password and the NAS shares are mounted accordingly with applicable permissions. Achieving this in ubuntu seems to be very difficult. Bear in mind that I am not an IT professional; just an ambitious home user.

---

### Post by dmizer on 2009-03-03
Okay, this is indeed doable with pam, but I have zero experience with it. Perhaps this will be of help? [http://www.novell.com/coolsolutions/feature/15354.html](http://www.novell.com/coolsolutions/feature/15354.html)

Alternatively, you can use cifs in /etc/fstab along with autofs: [http://www.howtoforge.com/accessing_windows_or_samba_shares_using_autofs](http://www.howtoforge.com/accessing_windows_or_samba_shares_using_autofs)

Neither option is intuitive, and both require CLI work. I have used the autofs method successfully. Keep in mind though that Samba is, of course, a Windows proprietary protocol. However, it IS doable.

---

### Post by jstars on 2009-03-04
Thanks for the Novell pam reference. I have no idea how you know where all of this stuff is. Too bad there is not a lot of expertise on pam as I have seen other posts on this forum asking for the same thing.

Now given that I am using a NAS that probably runs linux ([Synology DS207+]("http://www.synology.com/enu/products/DS207+/index.php")), is samba the best way to share with both WinXP and Ubuntu? The NAS has a NFS option; however I have no clue about NFS.

---

### Post by dmizer on 2009-03-04
> **jstars said:**
> Thanks for the Novell pam reference. I have no idea how you know where all of this stuff is. Too bad there is not a lot of expertise on pam as I have seen other posts on this forum asking for the same thing.
google knows all :)

Well, this is your opportunity to change that! Learn how to make pam mount work, and post a thorough howto.

> **jstars said:**
> Now given that I am using a NAS that probably runs linux ([Synology DS207+]("http://www.synology.com/enu/products/DS207+/index.php")), is samba the best way to share with both WinXP and Ubuntu? The NAS has a NFS option; however I have no clue about NFS.
There is an NFS link in my sig which includes information on connecting to NFS shares. It would certainly be faster, but it would come with the same "how do I mount it per user?" questions and answers.

---

