---
title: "Samba share from Ubuntu, trouble accessing securely from Windows."
date: 2009-07-31
forum: Networking &amp; Wireless
---

### Post by debest on 2009-07-31
So, I'm looking to set up file sharing on Ubuntu Jaunty, accessing from Windows XP through Samba.  I've found several pages through search on setting this up (including [this nice video]("http://www.youtube.com/watch?v=89hjWOb8qmY&annotation_id=annotation_888326&feature=iv") on YouTube), but I have an issue which I cannot find addressed.

When I right-click on a folder to share, then select "Sharing Options", I get a dialog box with three checkboxes:
- "Share this folder" (self explanatory)
- "Allow other people to write in this folder" (presumably grants write permissions to all users on the machine)
- "Guest access (for people without a user account)" (presumably unfettered access to whomever is able to access the machine over the network)

If I check off the "Guest access" box, I can browse to the directory from my Windows machine directly.  But, if I do not check this box, Windows gives me a "Connect to <servername>" dialog box, and asks for a user name & password.  Entering my Ubuntu username & password does not work.  Nothing I try works.

Is there a way to set this up in a secured fashion?  Surely I don't need to share the folder openly across the entire network?  Perhaps there is User name & password that can be set up for use by Remote clients?  If so, how?

(BTW, someone asks this exact question in the above YouTube video, but as yet there is no response.)

Thanks in advance for your help.

---

### Post by dmizer on 2009-07-31
You'll need to add the Windows username and password as a samba user on the Ubuntu computer.

Veggitales FTW. :)

---

### Post by debest on 2009-07-31
Thanks for the nudge in the right direction.  I looked up how to add a user on Samba.  Don't know if this is exclusive to Ubuntu or not, but I apparently need to create a "real" user on Ubuntu first.  So... my steps were:

** Create User (GUI) **
1) System -> Administration -> Users and Groups
2) Click "Unlock", type sudo password.
3) Click "Add User"
4) Enter Username "sambauser", Real Name "Samba User", Profile "Unprivileged", and set a password.  Click "OK".
5) Click "Close"

** Create Samba User (command line, if there is a GUI, pls let me know) **
6) Applications -> Accessories -> Terminal
7) Enter "sudo smbpasswd -a sambauser" (enter sudo password)
8) At "New SMB password", enter a password (I used the same password created above at step 4).  Re-enter the password.  You will see "Added user sambauser."
9) Enter "exit"

That's it.  Now, I did not have to set my folder sharing to "Guest access" any longer.  When that box is unchecked, and I find the shared folder in Windows, the dialog box comes up asking for "User Name" and "Password".  Entering "sambauser" and the password entered in Step 8, and VOILA!!!  A useful shared folder!

Thank you.  Hope this helps others!

---

