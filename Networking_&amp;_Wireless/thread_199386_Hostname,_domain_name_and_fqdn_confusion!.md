---
title: "Hostname, domain name and fqdn confusion!"
date: 2006-06-18
forum: Networking &amp; Wireless
---

### Post by GlennB on 2006-06-18
Hi All,

I just finished the LAMP server install of 6.06. During the install I think I screwed up and specified just the hostname ('fred' let's say) rather than a full fqdn (say 'fred.domain.co.uk'). I thought I could change this in  /etc/hosts like this:

```
127.0.0.1       localhost localhost.localdomain
192.168.x.xx    fred fred.domain.co.uk
```

Edit: that top line should read

```

127.0.0.1    localhost.localdomain  localhost fred 
```

But after doing that, if I run 'hostname' I get back

```
glenn@fred:~$ hostname
fred
```

even after a reboot, and hostname -f gives me back the same thing.

I thought that creating /etc/domainname containing 

```
domain.co.uk
```

would do the job, but I was wrong! I'm trying to get Drupal configured, and
it's failing to resolve the server at [http://fred.domain.co.uk/drupal](http://fred.domain.co.uk/drupal). I can see the Drupal config page by using the IP address, but Drupal is fetching pages based on the fred.domain.co.uk address, so any links off the main page fail.

I'm stumped, and it's got to be simple, but things seem to be different to some other distros :-). Where does Ubuntu keep the host & domain name settings, and how do I change them??

thanks,

Glenn.

---

