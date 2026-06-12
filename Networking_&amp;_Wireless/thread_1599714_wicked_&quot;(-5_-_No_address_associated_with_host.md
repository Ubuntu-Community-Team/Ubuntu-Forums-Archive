---
title: "wicked &quot;(-5 - No address associated with hostname)&quot;  error upon package installation"
date: 2010-10-18
forum: Networking &amp; Wireless
---

### Post by Siljrath on 2010-10-18
i've read a number of threads on this topic (and similar) but am yet to resolve my problem.

using ubuntu 10.04, which was upgraded from crunchbang 9.04.

when trying to install packages or upgrade, i get error messages consisting of stuff like: ```
Failed to fetch http://uk.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg  Something wicked happened resolving 'uk.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://uk.archive.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg  Something wicked happened resolving 'uk.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://uk.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release.gpg  Something wicked happened resolving 'uk.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://uk.archive.ubuntu.com/ubuntu/dists/lucid/main/binary-amd64/Packages.gz  Something wicked happened resolving 'uk.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://uk.archive.ubuntu.com/ubuntu/dists/lucid/restricted/binary-amd64/Packages.gz  Something wicked happened resolving 'uk.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://uk.archive.ubuntu.com/ubuntu/dists/lucid/universe/binary-amd64/Packages.gz  Something wicked happened resolving 'uk.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://uk.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/binary-amd64/Packages.gz  Something wicked happened resolving 'uk.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://uk.archive.ubuntu.com/ubuntu/dists/lucid-security/main/binary-amd64/Packages.gz  Something wicked happened resolving 'uk.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://uk.archive.ubuntu.com/ubuntu/dists/lucid-security/restricted/binary-amd64/Packages.gz  Something wicked happened resolving 'uk.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://uk.archive.ubuntu.com/ubuntu/dists/lucid-security/universe/binary-amd64/Packages.gz  Something wicked happened resolving 'uk.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://uk.archive.ubuntu.com/ubuntu/dists/lucid-security/multiverse/binary-amd64/Packages.gz  Something wicked happened resolving 'uk.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://uk.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-amd64/Packages.gz  Something wicked happened resolving 'uk.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://uk.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/binary-amd64/Packages.gz  Something wicked happened resolving 'uk.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://uk.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/binary-amd64/Packages.gz  Something wicked happened resolving 'uk.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://uk.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/binary-amd64/Packages.gz  Something wicked happened resolving 'uk.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Some index files failed to download, they have been ignored, or old ones used instead.
```

i have attempted to issue the correct details to my /etc/hosts
having checked my hostname with the command ```
hostname
``` andmy ip with ```
sudo ifconfig
```

i thought i had entered them correctly, but i still get these errors.
```
 (-5 - No address associated with hostname)
```

with just my hostname after the ip adress, i have tried several variations to the ip address (inc obviously the one's mentioned in th eoutput from sudo ifconfig).   127.0.0.0, 127.0.0.1, 192.168.1.2, 192.168.1.1, 192.168.0.2, etc,,, but still i get the same result.

i'm at a loss as to what to try next.

any suggestions where i might be going wrong?

could it be anything to do with having generated my sources.list from [http://repogen.simplylinux.ch/generate.php](http://repogen.simplylinux.ch/generate.php) ?

---

### Post by Siljrath on 2010-10-18
[http://ubuntuforums.org/showthread.php?t=799695](http://ubuntuforums.org/showthread.php?t=799695)

s'ok, found a solution that works here.

in synaptic, changed the respository, ubuntu software, download from : main server... and all's well again.  :$

---

### Post by GuiGuy on 2010-10-18
> **Siljrath said:**
> [http://ubuntuforums.org/showthread.php?t=799695](http://ubuntuforums.org/showthread.php?t=799695)

s'ok, found a solution that works here.

in synaptic, changed the respository, ubuntu software, download from : main server... and all's well again.  :$

I'm still that same error even when using mainserver!? :confused:

---

### Post by naga2raja on 2011-04-25
One of the Cause may be due to your network proxy settings may not be applied System Wide.

For applying Proxy setting system wide, In chrome -> preference -> Under the Hood -> Change Proxy settings -> Give the proxy configuration and Click on "Apply system wide" options.

Then try installing the package

---

