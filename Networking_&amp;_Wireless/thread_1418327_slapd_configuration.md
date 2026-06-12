---
title: "slapd configuration"
date: 2010-02-28
forum: Networking &amp; Wireless
---

### Post by gnerdman on 2010-02-28
I've been trying to install and configure slapd/openldap on Karmic without any luck.  I've been using the guide published here:

[http://doc.ubuntu.com/ubuntu/serverguide/C/openldap-server.html](http://doc.ubuntu.com/ubuntu/serverguide/C/openldap-server.html)

I'm successful up to the ACL section (skipping replication).  However, when I enter the command:

ldapsearch -xLLL -b cn=config -D cn=admin,cn=config -W olcDatabase=hdb olcAccess

I get "invalid credentials".  I'm using the password I entered in the backend and frontend ldif files in the following directives (respective):

olcRootPW: thirdday
userPassword: thirdday

I on a wiki today (wikipedia? Can't find it again) I read that the guide referenced above won't work with 2.4.18-0ubuntu1 (which is what ships with Karmic, and which, oddly enough is supposedly what the guide is about).  I'm running the x86_64 version of Karmic.  Can someone point me to an accurate step x step that will help me get the thing running?  I'm a complete noob and have no grasp at all of directory theory - hence my desire to get something running and learn it.  Thanks in advance.

---

