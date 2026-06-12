---
title: "Trying to set up TACACS Server"
date: 2009-01-01
forum: Networking &amp; Wireless
---

### Post by OneMixDJ on 2009-01-01
Greetings,

After enough time searching all over the place, I can't seem to find a way to set up my Ubuntu server (8.04) as a TACACS server.

I have several Cisco devices in my lab network VLAN that I want to set up for TACACS.

Some of the research I did pointed me to do an "apt-get" for tac-plus, but that doesn't seem to be available anymore.

Is there a way I can set up server as a TACACS server?

Any help would be appreciated.

Thanks!!!

---

### Post by mykul31217 on 2009-01-23
has there been any word when tac-plus will be coming back to the repos?

---

### Post by OneMixDJ on 2009-02-12
...so far, I haven't heard or found anything...:(

---

### Post by bejoybkn on 2011-07-17
Hello,

I have a forum which discuss about tac plus server setup

[http://bejoybkn.blogspot.com/](http://bejoybkn.blogspot.com/)

Bejoy

---

### Post by bejoybkn on 2011-07-17
I have a blog on setting up tacplus

[http://bejoybkn.blogspot.com/](http://bejoybkn.blogspot.com/)
Bejoy

> **OneMixDJ said:**
> Greetings,

After enough time searching all over the place, I can't seem to find a way to set up my Ubuntu server (8.04) as a TACACS server.

I have several Cisco devices in my lab network VLAN that I want to set up for TACACS.

Some of the research I did pointed me to do an "apt-get" for tac-plus, but that doesn't seem to be available anymore.

Is there a way I can set up server as a TACACS server?

Any help would be appreciated.

Thanks!!!

---

### Post by mruiz@ic-sa.com on 2011-08-03
What you got to do is load the TACACS software onto the server.  Normally it is not installed.

Once this is done you have to create the tac. file.

Here is a template that help you along. 

cat tac_plus.conf #######################  # CONFIGURE ENCYPTION KEY  key =  put your key here.  #######################  # CONFIGURE DEFAULT AUTHENTICATION  # Query the /etc/passwd file for default authentication  default authentication = file /etc/passwd --> this queries the passwd file for user accounts.  # Location of text file to log Accounting records  #######################  # CONFIGURE ACCOUNTING LOG FILE  accounting file = /var/log/tac.log  ######################  # CONFIGURE GROUP  ######################  # Network administrator group  group = netadmin {  # netadmin group for supervisor access   # disconnect the group-members, if idle for 25 minutes  default service = permit  service = exec {  priv-lvl = 15  }  }  # Regular user group  group = regularusers {   # regular users will be added to this group  default service = deny  service = exec {  priv-lvl = 7   }
######################  # CONFIGURE USERS  ######################  # Netadmin users  # note that there is no password entry  # tacacs+ daemon will query the /etc/passwd file for this user  user = users {  member = netadmin  }  You can get more specific by only specifying certain commands to be run.  It would like like something this

# Limited Access  group = limitedaccess {  default service = deny  service = exec {  priv-lvl = 15    } cmd = show {  permit "running-config.*" permit "ip int*" permit "inter.*" permit "controllers.*"  }  cmd = ping { permit .* } cmd = traceroute { permit .* } }

You would have to do a lot of tweaking but the above configuration I have been working on for a few weeks

Hope that helps.

---

