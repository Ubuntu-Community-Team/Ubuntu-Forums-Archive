---
title: "Where is &quot;check_nrpe&quot; in ubuntu?"
date: 2008-12-17
forum: Networking &amp; Wireless
---

### Post by bobber205 on 2008-12-17
I ran sudo apt-get install nagios-nrpe-plugins

and it completed successfully. But for the life of me I can find the binary to run... :(

---

### Post by swiftone on 2009-07-07
Has anyone figured this out?  In most examples it instructs to test the nrpe plugin by running the following:

```
/usr/local/nagios/libexec/check_nrpe -H 192.168.1.3
```

However, I cannot find the check_nrpe in ubuntu.

---

### Post by cariboo on 2009-07-07
Open an Applications-->Accessories-->Terminal and type:

```
locate check_nrpe
```

it should give you the location of the file.

---

### Post by KOld Iron on 2009-08-06
You may have figured it out yourself meanwhile, but here the solution anyways (for others maybe then to read).

I just started playing around with Nagios myself a few days ago. To make my life easier (since I am still not so knowledgable about Linux), I have installed Nagios using the provided packages.

Unfortunately the package maintainer decided to use a different directory structure than the one described in the installation tutorial using the manual compilation. Even more unfortunate almost all tutorials in the internet and even some of the plugins are referring to the structure created by the manual installation. So meanwhile I tend to agree with another poster in one of the other threads, that it is even (or especially) for beginners better to also go the manual way of doing things.

To answer your question: First you may need to do 

```
[FONT="Courier New"]# updatedb[/FONT]
```

before

```
[FONT="Courier New"]# located check_nrpe[/FONT]
```

will yield the desired result, i.e. **/usr/lib/nagios/plugins/check_nrpe** and **/etc/nagios-plugins/check_nrpe.cfg** (for the config file)

P.S.: I have tried to install Centreon after Nagios and it assumes the old structure as well, so it becomes very difficult to get it working (have not been successful yet)

---

### Post by slakkie on 2009-08-06
dpkg -L $package_name | grep check_nrpe

or, asuming it is in your path: which check_nrpe.. 

or find.

```

apt-file search check_nrpe
nagios-nrpe-plugin: /etc/nagios-plugins/config/check_nrpe.cfg
nagios-nrpe-plugin: /usr/lib/nagios/plugins/check_nrpe

```

---

