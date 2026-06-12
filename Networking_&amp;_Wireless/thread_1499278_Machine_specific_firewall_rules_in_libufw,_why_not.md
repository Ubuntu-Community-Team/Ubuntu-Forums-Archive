---
title: "Machine specific firewall rules in /lib/ufw, why not /etc?"
date: 2010-06-01
forum: Networking &amp; Wireless
---

### Post by mathog on 2010-06-01
I used gufw to configure some firewall rules on a 10.04LTS machine.  Then when getting ready to clone that machine went to see if the local machine's address was hardwired.  It took a lot of searching but I finally found the configuration files for ufw  - in /lib/ufw.

Why isn't this configuration information under /etc, for instance in /etc/ufw or /etc/default?  Machine specific configuration settings don't belong in /lib!

Specifically, one of the things added by gufw was a line that gave full access to all local ports to a particular subnet server.  (Much easier than setting a rule for each port.)   That was found in 
/lib/ufw/user.rules as:

### tuple ### allow any any 0.0.0.0/0 any XXX.XXX.XXX.XXX in
-A ufw-user-input -s XXX.XXX.XXX.XXX -j ACCEPT

where XXX.XXX.XXX.XXX was that server's address.  This time the ufw config did not need to be changed for the clones, but that was just luck, they could easily have needed a different server entry here. 

Does ubuntu store any _other_ machine specific configuration information outside of /etc??? 

Regards,

David Mathog

---

