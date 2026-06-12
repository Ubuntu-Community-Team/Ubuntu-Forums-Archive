---
title: "BIND configuration and SSH to domain without 'www'"
date: 2010-07-14
forum: Networking &amp; Wireless
---

### Post by vandil on 2010-07-14
I have configured BIND and I am able to resolve the configured domains with one exception.  I am able to SSH (putty) to 'www.domain2.me' but if I try to SSH to 'domain2.me' it fails.  What have I failed to configure?

Kindest regards for reviewing my post.

   **Named.conf.local**
  
  zone "domain2.me" {
           type master;
           file "/etc/bind/zones/domain2.me.db";
  };
  
   **domain2.me.db**


domain2.me.      IN      SOA     ns1.domain1.ws. admin.domain2.me. (
   
                                                                                  2006081401
                                                                                  28800
                                                                                  3600
                                                                                  604800
                                                                                  38400
  );
   
  domain2.me.      IN      NS                ns1.domain1.ws.
  domain2.me.      IN      MX     10    mail.domain2.me.
   
  www                     IN      A       ***.70.34.179
  mail                       IN      A       ***.70.34.187
  ns1                         IN      A       ***.70.34.186

---

