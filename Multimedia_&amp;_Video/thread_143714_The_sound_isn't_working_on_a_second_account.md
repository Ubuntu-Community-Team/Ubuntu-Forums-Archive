---
title: "The sound isn't working on a second account"
date: 2006-03-13
forum: Multimedia &amp; Video
---

### Post by chimera on 2006-03-13
Now, when I installed Ubuntu, the sound pretty much Just Worked (TM), but when I created a second user account a few minutes ago, the sound didn't work in it. If I log in with my first user account, it works. What am I to do?

---

### Post by Sutekh on 2006-03-13
You probably need to add the new user to the **audio** group
```
sudo adduser <2nd username> audio
```

You should check all the other groups that the first user is in too (for things like admin, plugdev - removable devices, etc).
```
groups <1st username>
groups <2nd username>
```

---

### Post by chimera on 2006-03-13
thanks, I got it working now:) 

Anther question: How do I disable that user the perimmision to sudo or become root?

(yay, I'm now a Linux system admin, I've always wanted to boss other people around :D )

---

### Post by Sutekh on 2006-03-13
I'll give you a run down of some of the groups that are available.  These are the groups that match up with the options in the **Users and Groups** (System  - > Administration) program.

```

**adm**  		-  Monitor system logs
**admin**	        -  Executing system administration tasks
**audio**    	-  Use audio devices
**cdrom**           -  Use CD-Rom drives
**dialout**  	-  Use modems
**dip**  		-  Connect to internet using a modem
**fax**      	-  Send and receive faxes
**floppy**          -  Use floppy drives
**lpadmin**  	-  Setup printers
**plugdev**  	-  Enable access to external storage devices automatically
**scanner**  	-  Use scanner devices
**tape**  		-  Use tape drives
**video**  		-  Use video acceleration

```

You can remove a user from a group using **deluser**
```
sudo deluser <username> <groupname>
```

---

