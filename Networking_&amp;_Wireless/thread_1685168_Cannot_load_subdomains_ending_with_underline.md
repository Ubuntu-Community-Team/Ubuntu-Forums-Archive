---
title: "Cannot load subdomains ending with underline"
date: 2011-02-10
forum: Networking &amp; Wireless
---

### Post by 5ulo on 2011-02-10
Hi, I work as webdeveloper and I and my co-workers have one rule - if we are done with any project, we comment them with underline at the end of the directory name. For example we have domain 'devel.domain.com' and our projects are located on 'projectname.devel.domain.com' . Commented project looks like this 'endedproject_.devel.domain.com'. And here is the problem. I can not acces subdomains ended with underline. It works last time in 9.10 (i think), but since 10.04 gives me the browser only SERVER NOT FOUND. We are using this comment-method for 7 years without problems. Why is this problem in last two editions of Ubuntu?
note: there is no problem with accessing ended projects under windows or osx.

Thank You

---

### Post by regala on 2011-02-10
> **5ulo said:**
> Hi, I work as webdeveloper and I and my co-workers have one rule - if we are done with any project, we comment them with underline at the end of the directory name. For example we have domain 'devel.domain.com' and our projects are located on 'projectname.devel.domain.com' . Commented project looks like this 'endedproject_.devel.domain.com'. And here is the problem. I can not acces subdomains ended with underline. It works last time in 9.10 (i think), but since 10.04 gives me the browser only SERVER NOT FOUND. We are using this comment-method for 7 years without problems. Why is this problem in last two editions of Ubuntu?
note: there is no problem with accessing ended projects under windows or osx.

Thank You

well, the reason is simple. while underscores are allowed in domain names "globally", i.e. in SRV requests/responses for example like _sip._udp.example.com. but it is theoretically forbidden in hostnames which is what endedproject_.devel.domain.com precisely is, as a FQDN. it was tolerated I imagine. but it should be forbidden and other OSes or browsers are at fault here.
source: [http://en.wikipedia.com/wiki/Hostname](http://en.wikipedia.com/wiki/Hostname)
"While a hostname may not contain other characters, such as the underscore character (_), other DNS names may contain the underscore. Systems such as DomainKeys and service records use the underscore as a means to assure that their special character is not confused with hostnames. For example, _http._sctp.[www.example.com](www.example.com) specifies a service pointer for an SCTP capable webserver host (www) in the domain example.com."

---

### Post by 5ulo on 2011-02-11
bad news for me :( but thank You for this info.

---

