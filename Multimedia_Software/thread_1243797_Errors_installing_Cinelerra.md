---
title: "Errors installing Cinelerra"
date: 2009-08-18
forum: Multimedia Software
---

### Post by PaulNKS on 2009-08-18
When I try to install Cinelerra through Synaptic I get the following message:

[INDENT]cinelerracv:
 Depends: libmjpegtools0c2a (>=1:1.8.0) but it is not installable
 Depends: libquicktimecv but it is not going to be installed
 Depends: libx264-59 (>=1:0.svn20080408) but it is not installable[/INDENT]

If I use the terminal, I get the following:

[INDENT]~$ sudo apt-get install cinelerra
[sudo] password for paul: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  cinelerra: Depends: cinelerracv but it is not going to be installed or
                      cinelerrahv but it is not installable
E: Broken packages[/INDENT]

Can anyone tell me how to successfully install Cinelerra?  Any help at all would certainly be appreciated.

Thanks.

---

### Post by PaulNKS on 2009-08-20
Does anyone have any ideas?  I could sure use the help...

Thank you.

---

