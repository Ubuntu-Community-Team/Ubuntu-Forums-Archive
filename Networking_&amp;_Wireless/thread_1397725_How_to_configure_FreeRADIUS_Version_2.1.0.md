---
title: "How to configure FreeRADIUS Version 2.1.0"
date: 2010-02-03
forum: Networking &amp; Wireless
---

### Post by pateld_ca on 2010-02-03
When I execute freeradius -X
 I get the following error initializing modules:
How do I fix this? 
Where can I find information on installing freeradius server in ubuntu? 

I could not find anything at 
 Module: Instantiating mschap
  mschap {
    use_mppe = yes
    require_encryption = no
    require_strong = no
    with_ntdomain_hack = no
  }
 Module: Linked to module rlm_unix
 Module: Instantiating unix
  unix {
    radwtmp = "/var/log/freeradius/radwtmp"
  }
/etc/freeradius/sites-enabled/inner-tunnel[223]: Failed to find module "eap".
/etc/freeradius/sites-enabled/inner-tunnel[176]: Errors parsing authenticate section. 
 }
}
Errors initializing modules

---

