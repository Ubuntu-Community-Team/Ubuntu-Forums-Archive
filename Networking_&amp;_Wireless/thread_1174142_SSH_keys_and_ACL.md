---
title: "SSH keys and ACL"
date: 2009-05-30
forum: Networking &amp; Wireless
---

### Post by Nampla on 2009-05-30
I just recently enabled acl on our server for a partition that contains our /home dir.  Now my ssh keys are not working.  I have to use a password.  Does anybody have any ideas as to what is wrong?

Thanks,

---

### Post by Brandon Williams on 2009-05-30
The ssh server is very picky about the permissions for ~/.ssh and anything in it, and it will simply refuse to use the content of files when it "thinks" the settings are too permissive. This will be impacted by the ACL settings, too. Use getfacl to view the ACL settings for ~/.ssh itself and for all files under ~/.ssh, especially the authorized keys file, and make sure that no-one other than the owner has read, write, or execute permission for any of it.

---

### Post by Nampla on 2009-05-30
I have played around with various permission and setfacl settings.  Nothing works.
uuugh

---

### Post by Brandon Williams on 2009-05-31
Are you in a position to run the ssh server in debug mode? 'sshd -eddd' will send very verbose debug messages to stdout. I have often found this to be incredibly useful in diagnosing such problems. This along with 'ssh -vvv' on the client should give you enough information about what the specific problem is.

---

### Post by Nampla on 2009-05-31
:p I solved it.  My /home directory had the wrong factl settings.  The .ssh folder and containg files were all correct but since the /home/{me} was wrong it would'nt allow ssh to work properly.  

I am sure there is a better explanation to this but im a noooooob!
;)

---

### Post by midfel11 on 2009-06-01
I just ran into the same problem here - wrong permissions on my home dir by default with Ubuntu 9.0.4.  Had to chmod it to 755 and then it worked.

---

