---
title: "Configure LikeWise Open5 Auth with AD"
date: 2009-06-30
forum: Networking &amp; Wireless
---

### Post by ewendt on 2009-06-30
Ok I'm having a problem with configuring likewise to authenticate local rights based on domain rights. I have domain admin rights but when a log onto the machine with my AD credentials I am restricted to regular user rights. i would like to be able to at least have the domain admins have local admin rights while the rest of the users on the network have only regular rights. this would be fine with me since they do not need more rights than that. but if there was a way to assign rights baised off of AD rights that would be great.

---

### Post by Daimones on 2009-07-01
Well I am pretty sure this should do the trick, though I am currently having issues setting up my AD integration, so I may be wrong.

sudo sudovi
Then add this line at the end
%YOURDOMAINNAME\\domain^admins ALL=(ALL) ALL

This will give your "domain admins" group sudo rights, if you prefer a different group to have sudo rights just replace that part, using ^ for spaces.

---

### Post by ewendt on 2009-07-02
With respect to the command sudo sudovi
i get command not found im not sure what ur pointing at there except maybe  towards the etc/groups is this correct let me know please

---

### Post by Daimones on 2009-07-02
That was my fault, apparently went dyslexic for a second the command should be:
sudo visudo

It edits the file /etc/sudoers

---

### Post by ewendt on 2009-07-02
when I add that to the end of the file and exit i get a syntax error at line 25 which is the admin groupline 
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults        env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL

# Uncomment to allow members of group sudo to not need a password
# (Note that later entries override this, so you might need to move
# it further down)
# %sudo ALL=NOPASSWD: ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL


this is how it looks previous the the change im not a programmer so i undertsand the basics here but not all the details

---

### Post by Daimones on 2009-07-02
Haha, I was apparently drunk when I typed that post or something, but there should only be 1 \ not 2.

It should read 

%YOURDOMAINNAME\domain^admins ALL=(ALL) ALL

I couldn't get it to output an error even with it typed incorrectly however, but that might be the cause, also make sure there is a space between the final ) and ALL.

---

### Post by ewendt on 2009-07-02
thanks it seems to have worked ill have to relogin with my AD credentials now

---

### Post by Daimones on 2009-07-02
No problem, glad we got something working hah, noobs helping noobs =)

---

