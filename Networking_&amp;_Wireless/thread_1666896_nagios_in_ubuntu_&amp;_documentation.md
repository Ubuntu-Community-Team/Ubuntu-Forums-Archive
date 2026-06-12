---
title: "nagios in ubuntu &amp; documentation"
date: 2011-01-14
forum: Networking &amp; Wireless
---

### Post by kelargo on 2011-01-14
hi,

I just install nagios3 in my ubuntu server. and I'm able to monitor some ubuntu desktops.

I was able to add more hosts by creating the host.cfg config files in this location

/etc/nagios3/conf.d

now I want to add some cisco switches. The official Nagios documentation says to place objects in /usr/local/nagios/etc/objects .. 

but the ubuntu install didnt create that directory structure. 
The translation of the proper directory structure for this is a bit confusing..

why is the ubuntu layout different? and not using /usr/local ?

should I place the switch.cfg in /etc/nagios3/conf.d ??
or just make /usr/local/nagios/etc/objects ??

thanks

---

### Post by cholt45 on 2011-04-08
Same question. There is no objects folder to be found. Its a shame the info is so scarce on nagios3 and ubuntu 10+ .

---

### Post by smugas on 2011-08-05
try to download [http://www.nagios.org/download/core/thanks/](http://www.nagios.org/download/core/thanks/) nagios-core package (nagios-3.3.1.tar.gz) and get definitions files from sample-config/templae-objects/ directory renaming i.e. switch.cfg.in file to switch.cfg. 

Put it into /etc/nagios3/objects/ directory as defined in /etc/nagios3/nagios.cfg file


PS. in case of an error:

> Error: Template 'generic-switch' specified in host definition could not be not found (config file '/etc/nagios3/objects/switch.cfg', starting on line 32)

in file /etc/nagios3/nagios.cfg uncomment this line:
cfg_file=/etc/nagios3/objects/templates.cfg

Next will be some like this: 

> Warning: Duplicate definition found for host 'generic-host' (config file '/etc/nagios3/objects/templates.cfg', starting on line 52)
Error: Could not add object property in file '/etc/nagios3/objects/templates.cfg' on line 53.


just comment all templates that are duplicated (probably from dierectory: /etc/nagios3/conf.d)

---

