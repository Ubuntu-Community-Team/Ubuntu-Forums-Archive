---
title: "not seeing updates from mythbuntu for lucid - 0.25"
date: 2013-05-04
forum: Mythbuntu
---

### Post by evuraan on 2013-05-04
I've 2:0.25.3+fixes.2013[COLOR=#a52a2a]0113[/COLOR].fa3ebd4-0ubuntu0mythbuntu1: 

```
# dpkg -l |grep mythtv
ii  libmythtv-perl                                                 2:0.25.3+fixes.20130113.fa3ebd4-0ubuntu0mythbuntu1    A PERL library to access some MythTV feature
ii  mythtv-backend                                                 2:0.25.3+fixes.20130113.fa3ebd4-0ubuntu0mythbuntu1    A personal video recorder application (serve
ii  mythtv-common                                                  2:0.25.3+fixes.20130113.fa3ebd4-0ubuntu0mythbuntu1    A personal video recorder application (commo
ii  mythtv-frontend                                                2:0.25.3+fixes.20130113.fa3ebd4-0ubuntu0mythbuntu1    A personal video recorder application (clien
ii  mythtv-transcode-utils                                         2:0.25.3+fixes.20130113.fa3ebd4-0ubuntu0mythbuntu1    Utilities used for transcoding MythTV tasks
ii  php-mythtv                                                     2:0.25.3+fixes.20130113.fa3ebd4-0ubuntu0mythbuntu1    PHP Bindings for MythTV

```

Although I see  0.25.3+fixes.2013[COLOR=#ff0000]0423[/COLOR].94d67fc* [here]("http://ppa.launchpad.net/mythbuntu/0.25/ubuntu/pool/main/m/mythtv/?C=M;O=D"),  I longer see available updates during apt-get [update,upgrade] et al on my ***two*** machines.

Further, I noticed this during manual apt-get update's: 
```
Ign http://ppa.launchpad.net/mythbuntu/0.25/ubuntu/ lucid/main Translation-en_US                                                                                               
```

Hence gotta ask, has anything changed with mythbuntu repo's for lucid? Have you stopped providing 0.25 updates for 10.04? 

 ```
wget -O /dev/null -S http://ppa.launchpad.net/mythbuntu/0.25/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz 
--2013-05-04 01:49:10--  http://ppa.launchpad.net/mythbuntu/0.25/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz
Resolving ppa.launchpad.net... 91.189.95.83
Connecting to ppa.launchpad.net|91.189.95.83|:80... connected.
HTTP request sent, awaiting response... 
  HTTP/1.1 404 Not Found
  Date: Sat, 04 May 2013 08:49:10 GMT
  Server: Apache/2.2.14 (Ubuntu)
  Vary: Accept-Encoding
  Content-Length: 345
  Keep-Alive: timeout=15, max=100
  Connection: Keep-Alive
  Content-Type: text/html; charset=iso-8859-1
2013-05-04 01:49:10 ERROR 404: Not Found.

```


Many thanks!

---

### Post by ajgreeny on 2013-05-04
I think Lucid (the GUI operating systems) have now lost support, and I assume this will be so for mythbuntu as well as the others of the *ubuntu family. Only the server editions are still supported for another two years.

---

### Post by tgm4883 on 2013-05-04
Hmm, it seems lucid should be getting 0.25 updates (it won't get 0.26 though). I'll check on it.

---

### Post by evuraan on 2013-05-11
> **tgm4883 said:**
> Hmm, it seems lucid should be getting 0.25 updates (it won't get 0.26 though). I'll check on it.

any update on this? ):P

thanks!

---

### Post by tgm4883 on 2013-05-11
Yes, there is good news and bad news. 

The good news. I was able to create a blacklist in our build scripts so I have reenabled the lucid builds. We needed the blacklist as 0.26 and later won't build on lucid. 

The bad news. We need an update in the 0.25 branch before it will rebuild. We can't just force a rebuild as that hash already exists on the PPA. I'll look into possibly bypassing that if we can, but I'm unsure if that will be possible.

---

### Post by tgm4883 on 2013-05-11
Looks like I was able to get just a lucid 0.25 build uploaded. Currently getting the dependencies back for building (they were removed when we stopped building for it). I would expect an updated 0.25+fixes lucid build in a few hours.

---

### Post by matt06 on 2013-05-12
Still running lucid here as well.  The new build showed up this morning in my updates.  Thanks for your work tgm4883!

---

### Post by evuraan on 2013-05-12
Excellent! thank you tgm4883! 

This helps very much! I don't intend to upgrade from 10.04 until the 5 year LTS span expires in another 2 years; too much work.

---

### Post by tgm4883 on 2013-05-12
> **evuraan said:**
> Excellent! thank you tgm4883! 

This helps very much! I don't intend to upgrade from 10.04 until the 5 year LTS span expires in another 2 years; too much work.

Please note a few things.

A) 10.04 will NOT get anything later than 0.25. It just fails to build and we WONT be fixing that (We've tried, but it's not trivial)

B) 10.04 desktop only has a support length of 3 years, and that expired last week. You'll only get updates for the underlying stuff (stuff that server has as well). This probably won't be an issue, but it's worth mentioning.

---

