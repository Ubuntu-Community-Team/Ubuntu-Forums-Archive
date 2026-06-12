---
title: "Change root password on AD-authenticated system"
date: 2011-10-05
forum: Networking &amp; Wireless
---

### Post by jkherrick on 2011-10-05
Okay all, I like to believe I've done my due diligence on this issue before posting. I can usually find all my answers to questions already asked, but this one is a doozy.

Took over SA duties from the last guy after he'd been gone 3 months, so I won't get his help. Have an Xubuntu server running system-auditing software. The root password has been changed (no longer the hash), and the DIS has no idea what it could be. There's a single user account (the DIS' name), but he's forgotten that password too.

I've booted (single mode and password-less terminal mode) to no avail. You see, it seems someone setup this system using AD authentication from [http://ubuntuforums.org/showthread.php?t=91510](http://ubuntuforums.org/showthread.php?t=91510)

[COLOR=Black]So any time I try to change password (root or otherwise) I'm getting the to-be-expected "authentication information cannot be recovered | password unchanged[/COLOR]" message lines.

Now, daring as I am, I've already tried editing (in bash during single boot) "/etc/pam.d/common-password" and removing the "use_authtok", saved, and restarted (single and rw init=... again). I still get that error message when trying to edit root's password.

So I'm guessing I have to either edit-out more from that file, or else edit more files or another file.

I can't kill this VM without a lot of migration work, and I can't login to do said work until I can reset the password. Please, someone, help?

---

