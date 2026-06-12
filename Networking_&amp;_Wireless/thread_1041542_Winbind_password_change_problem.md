---
title: "Winbind password change problem"
date: 2009-01-16
forum: Networking &amp; Wireless
---

### Post by red_five on 2009-01-16
My work network is mostly Windows 2000 servers and XP Pro workstations. We are, however, experimenting with Ubuntu 8.10 on the desktop, and I have 2 test workstations out on the floor for this purpose. They are configured to log into our Windows AD forest, and everything works fine except for changing passwords.

I've followed instructions on the Ubuntu Wiki for getting everything set up, but they seem to have missed one thing. When a user's password expires, the Wiki configuration just leaves the user hanging with an expired password and no way to change it. I saw on several other places where you could add a line to /etc/pam.d/common-password, which had the effect of allowing winbind to handle password change requests.

Now, for a user with an expired password, or one with a password that was manually set to be changed upon next login, it alerts the user to change the password. Then it asks for the user's current password, his new password twice, then promptly bombs with the error (in red text) "The change of the authentication token failed. Please try again later or contact the system administrator." (Of course, I am the system admin)

Looking at /var/log/auth.log, I can see the output from pam_winbind where it enters the gdm:chauthtok function. There's a line where it says "getting password (0x00000001), followed immediately by a line that says "request failed: Buffer too small, PAM error was System error (4), NT error was NT_STATUS_BUFFER_TOO_SMALL". Then there's "internal module error (retval = 4, user = 'aerosmith'), which appears to be something of a generic error, then the whole thing ends.

The line added to /etc/pam.d/common-password is:
```
password sufficient pam_winbind.so debug use_first_pass
```
You can also add "use_authtok" to the line, but that only makes the change process fail before the change process can begin.

This is something of a show-stopper. I can work around it somewhat, by writing up a script to allow the user to change the password, but the password change from the GDM login needs to work and it isn't. If I can't get this resolved, we'll have to keep shelling out $$$$$ to the Redmond folks, and none of us in the IT group want to do that!

---

### Post by nroussi on 2009-09-08
I have the same problem and I am not using winbind. I have an SMB-LDAP installation. The OpenLDAP server works fine, then I have 2 other servers as LDAP clients and each one of those 2 servers is a thin client server. Users are able to log in but after the password expires the users cannot use GDM's login screen to change their password. I receive the following error when I try to change a password:
> the change of the authentication token failed

---

### Post by nroussi on 2009-09-09
Apparently there were 2 /etc/passwd files.
One was a temp /etc/passwd- and the other /etc/passwd
Once I deleted the temp everything worked out well

---

