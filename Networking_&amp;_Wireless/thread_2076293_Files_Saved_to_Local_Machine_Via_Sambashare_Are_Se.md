---
title: "Files Saved to Local Machine Via Sambashare Are Set to Nobody:Nobody Access"
date: 2012-10-25
forum: Networking &amp; Wireless
---

### Post by SillySod on 2012-10-25
I have a little network set up with Sambashare areas on the main machine.  The problem is that when one of the remote machines creates or updates a file in the Sambashare area on the main machine, the file is set to owner and group access of "nobody".

Then when I try to access files in the Sambashare area on the main machine, they are only available to me as read-only.  The only solution I have is to reset the permissions on the main machine using chown or chmod recursively, but that's far from ideal.

How can I stop the remote machines from changing the access/permissions on the files stored on the main machine?

---

### Post by ahallubuntu on 2012-10-25
You can choose the group and user for a share in your smb.conf file, with these fields (change create mask/directory mask to your preference):
```

[MyShare]
comment = My Share
#other fields here for the share
path = /shares/MyShare
force user = thisuser
force group = thisgroup

```

---

### Post by SillySod on 2012-10-25
Thanks for the quick reply, is smb.conf on the local machine or remote machine?  And whereabouts?

---

### Post by ahallubuntu on 2012-10-25
The smb.conf you want is on the server - wherever the files are that you are accessing.

/etc/samba/smb.conf

That assumes you have setup the Samba server there deliberately vs. just enabling sharing on some specific folder.  In that case, I don't know how to do it - there must be a smb.conf file elsewhere.

---

### Post by SillySod on 2012-10-25
Thanks, it is in the place you said.

I think actually what I needed to do more than the force user/group thing was to set the change mask to 0755 so that the files have group rw access.  That way I can do what I want with them without them opening as read-only on the server machine (and without getting an error in Lightning when I change something in the shared calendar on the server machine after it has been updated by a remote machine).

I think I've fixed it but I will test a bit further over the weekend and hoepfully come back to mark the thread as solved.

---

### Post by SillySod on 2012-10-25
I have come across the next problem already, this always happens as well.

If I create a new file or folder in a Sambashare area on the server machine, it sets the group permission to read only, so I can't edit the file or create any further sub folders remotely.

How do I set it to give group rw access to any new file or folder created on the server in the Sambashare area?

---

### Post by bab1 on 2012-10-25
> **SillySod said:**
> I have come across the next problem already, this always happens as well.

If I create a new file or folder in a Sambashare area on the server machine, it sets the group permission to read only, so I can't edit the file or create any further sub folders remotely.

How do I set it to give group rw access to any new file or folder created on the server in the Sambashare area?

The default *umask* for current versions of Ubuntu is 022.  This allows permissions to be st at 775 for directories and 664 for all files.

You can test the *umask* settings with this terminal command ```
umask
```...what do you get?  What version of Ubuntu are you running?

The correct *umask* setting only solves part of the problem.  If you are going to have multiple users accessing the share you will need to provide a reliable way to provide for a common group for the users via the file system.  Do you think you might need that?

---

### Post by SillySod on 2012-10-26
I experimented with umask yesterday, it was initially set to 022.  I changed it to 077 following advice from a website, but that made things worse.

Then I decided it might need to be the same as "change mask" in the smb.conf file, so I set it to 0775 in my /etc/profile and this ruined everything - when I tried to log back in, I got a message saying the X server could not start due to an access problem, and I had to edit /etc/profile back to 022 from a terminal login using vi!

After that I set umask to 002, which appears to have done the trick.

This may have relaxed things a bit too far, but it doesn't really matter as I am only dealing with a home network so the only user is me.

---

