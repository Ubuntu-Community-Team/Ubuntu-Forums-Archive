---
title: "User Name Questions"
date: 2009-01-27
forum: Networking &amp; Wireless
---

### Post by 52Mike on 2009-01-27
New to Ubuntu.  Just set it up and it seems great.  Unfortunately I set up the computer using my name "mike" and now that I see it is working great and I want to network the computer with my existing Windows network (during transition from Windows to Ubuntu, I can't stand Windows) I need to change the identification of this computer.  I want to change the name of the user so that the networking can proceed.  How do I change the user name without losing the work I have done setting up this first ubuntu computer?  

Thanks in advance for your help. 

Mike

---

### Post by Therion on 2009-01-27
1.  From your toolbar, select System ->Administration -> Network
2. Select the General tab.
3. If you are not logged in as Root, select Unlock.
4. A window will open, asking you to verify you have permission to access this part of the system. 
5. Type your password into the textbox, and click Authenticate.
6. Type your desired computer name in the text box labeled Host Name.
7. Click Close

Restart your system to ensure the changes take effect.

---

### Post by Iowan on 2009-01-27
:confused: You want to change the username or hostname? or both? Username change can be done - but it's messy (easier to create another user).  Hostname change bears the caveat - change /etc/hosts file, too. Details [here]("https://bugs.launchpad.net/ubuntu/+source/hostname/+bug/113778").

---

