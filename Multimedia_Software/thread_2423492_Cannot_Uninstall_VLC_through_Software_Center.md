---
title: "Cannot Uninstall VLC through Software Center"
date: 2019-07-24
forum: Multimedia Software
---

### Post by jbh54enwiler on 2019-07-24
In light of the security vulnerability VLC has been revealed to apparently have, I am trying to temporarily uninstall it on my Ubuntu 19.04 and Kubuntu 19.04 systems.  However, on my GNOME Ubuntu system, my copy of VLC, which I swear I downloaded through the Ubuntu Software Center, brings up an error reading "Unable to find "vlc_vlc.desktop."  The version of VLC that IS available on the Software Center is marked as not installed.  I don't know how to uninstall VLC from the command line or any other method, so could someone direct me how to do this?

---

### Post by again? on 2019-07-24
Software Center has a deb and a snap for vlc
Check if either is installed.
```
type -a vlc
```

eg I have the deb and snap installed
```
**[COLOR="#006400"]glen@Ubionic:~$[/COLOR] type -a vlc**
vlc is /usr/bin/vlc
vlc is /snap/bin/vlc
```

For deb removal...
```
sudo apt remove vlc
```

For snap removal...
```
snap remove vlc
```

---

### Post by jbh54enwiler on 2019-07-24
That did it, thanks.  However, according to VideoLAN on Twitter, the issue with VLC isn't in existence.  Apparently some security company jumped the gun, broke the rules, and submitted a warning without notifying the devs or even checking their facts.  I might reinstall VLC because apparently the article I read about security flaws in VLC was the result of a misguided affair.  I'll have to dig deeper and research this issue further.

---

### Post by TheFu on 2019-07-24
> **jbh54enwiler said:**
> That did it, thanks.  However, according to VideoLAN on Twitter, the issue with VLC isn't in existence.  Apparently some security company jumped the gun, broke the rules, and submitted a warning without notifying the devs or even checking their facts.  I might reinstall VLC because apparently the article I read about security flaws in VLC was the result of a misguided affair.  I'll have to dig deeper and research this issue further.

I know nothing about this specific issue, besides seeing some headlines yesterday.  I seldom worry much about most security issues, since I patch weekly (Saturday mornings).  If VLC isn't actively being used as a streaming server, there is little risk using it locally.  The same would apply to any program, so I just trust that Canonical will make the patch available when it is ready, if it is a valid concern.  

As a desktop user, I wouldn't worry, assuming I patched weekly and had excellent daily, automatic, versioned, backups that were mostly disconnected from the target systems.  Security is about avoiding and mitigating risks.  Backups mitigate almost all risks, except data stealing.

This year, there has been 2 times when I specifically took action on my public facing internet servers for security needs. An attack was in the wild, being used actively, against the software I run on multiple servers.  I scan the CVE data daily.

---

### Post by again? on 2019-07-25
According to [https://twitter.com/videolan](https://twitter.com/videolan), the bug was in an out of date third party 
library Bionic uses.
I just received updates to this library and vlc so I'm guessing it's been fixed in Ubuntu.
```
**[COLOR="#006400"]glen@Bionic:~$[/COLOR] apt policy libebml4v5**
libebml4v5:
  Installed: [COLOR="#FF0000"]1.3.5-2ubuntu0.1[/COLOR]
  Candidate: 1.3.5-2ubuntu0.1
  Version table:
 *** 1.3.5-2ubuntu0.1 500
        500 http://security.ubuntu.com/ubuntu bionic-security/universe amd64 Packages
        100 /var/lib/dpkg/status
     1.3.5-2 500
        500 http://ftp.iinet.net.au/pub/ubuntu bionic/universe amd64 Packages
```
From [https://usn.ubuntu.com/4073-1/](https://usn.ubuntu.com/4073-1/)
> Update instructions
The problem can be corrected by updating your system to the following package versions:

Ubuntu 18.04 LTS
libebml4v5 - [COLOR="#FF0000"]1.3.5-2ubuntu0.1[/COLOR]

Ubuntu 16.04 LTS
libebml4v5 - 1.3.3-1ubuntu0.1

---

