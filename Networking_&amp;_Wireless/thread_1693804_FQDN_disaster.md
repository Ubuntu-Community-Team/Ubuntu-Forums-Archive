---
title: "FQDN disaster"
date: 2011-02-23
forum: Networking &amp; Wireless
---

### Post by usatonycuba on 2011-02-23
Here's my problem .. I followed this tutorial [http://www.howtoforge.com/virtual-users-and-domains-with-postfix-courier-mysql-and-squirrelmail-ubuntu-10.10](http://www.howtoforge.com/virtual-users-and-domains-with-postfix-courier-mysql-and-squirrelmail-ubuntu-10.10) from Page 1 to Page 3 (there was a big stop to me) after i did follow install ```
amavisd-new spamassassin clamav clamav-daemon zoo unzip bzip2 libnet-ph-perl libnet-snpp-perl libnet-telnet-perl nomarch lzop pax 
```  this shows up  ```
Setting up amavisd-new (1:2.6.4-1ubuntu6) ...
Creating/updating amavis user account...
Starting amavisd:   The value of variable $myhostname is "admin", but should have been
  a fully qualified domain name; perhaps uname(3) did not provide such.
  You must explicitly assign a FQDN of this host to variable $myhostname
  in /etc/amavis/conf.d/05-node_id, or fix what uname(3) provides as a host's 
  network name!
(failed).
invoke-rc.d: initscript amavis, action "start" failed.
WARNING: Starting amavisd-new failed. Please check your configuration.
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
```Obviously pointing that  my  hostname is no a  FQDN, I did install and reistall Ubunutu 10.10 from last night more than 3 times, each time get stock here.

I changed more than three times the way i do set up this things no luck.. How do i change my FQDN?
I do post no more info because i really do not know what can be useful, but ask me to.. and i post any thing what i have done.
Forget to say that i do have install no-ip.. we have a DOMAIN with them.. 

what else?

---

### Post by SeijiSensei on 2011-02-24
Are you trying to accept inbound mail from the Internet?  Make the server's FQDN match the hostname corresponding to your domain's MX host.

---

### Post by usatonycuba on 2011-02-26
> **SeijiSensei said:**
> Are you trying to accept inbound mail from the Internet?  Make the server's FQDN match the hostname corresponding to your domain's MX host.
Thanks.. i did match the FQDN from local.. and is working good now.. your comments help a lot.. since i trying to see how it works in tests, then reinstall everything to production server.. and that exatcly was one big questions..

---

