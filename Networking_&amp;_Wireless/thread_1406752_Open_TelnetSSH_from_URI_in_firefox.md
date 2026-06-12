---
title: "Open Telnet/SSH from URI in firefox"
date: 2010-02-14
forum: Networking &amp; Wireless
---

### Post by FlameLicker on 2010-02-14
Dear all,

There is a number of mini-HowTos around which are describing how to start telnet sessions from firefox.

Somewhen since Ubuntu 8.04 the procedures Jonathan Ernst, James Zuelow and others provided stopped working - at least in my enviroment. Since I'm a newbie in this regard it took some time to figure out how to cope with this one. Please be carefull. Maybe my approach of the problem only worked because of I had a brandnew firefox installation and no rules for mms:// were in place.

**1) Open Firefox and start an URL 'mms://'**
   Firefox wants to know whether it shall open 'totem' or 'another application'.
   Choose 'another application' and apply the telnet-script shown below.

**2) Look for the directory which contains the config files of Firefox.**
   (It looks like '~/.mozilla/firefox/abcdef0g.default')
   Open mimeTypes.rdf with vi and substitute all 'mms' with 'telnet'.

**3) If you want to you can repeat the procedure (steps 1 + 2) with replacing telnet with ssh.**

**4) Restart Firefox**
The first time you start URI [telnet://](telnet://)... and URI [ssh://]("ssh://")... you will be asked to choose totem or another application. Apply your appropriate script and make the choice permanent by clicking the checkbox.

   URI '[telnet://]("telnet://")' should open the configuration panel of putty ready to start a telnet session.
   URI 'telnet://hostname.domain' should open a telnet session with the default port number 23.
   URI 'telnet://hostname.domain/8023' should open a telnet session with the port number 8023.
   URI '[ssh://]("ssh://")' should open the configuration panel of putty ready to start a ssh session.
   URI 'ssh://hostname.domain' should open a ssh session with the default port number 22.
   URI 'ssh://hostname.domain/8444' should open a ssh session with the port number 8444.

**My scripts:**
(Don't forget 'sudo chmod 755 /usr/local/bin/moz-*')

   /usr/local/bin/moz-telnet.sh:
      #!/bin/bash
      address=`echo $1 | cut -d / -f 3`
      port=`echo $1 | cut -d / -f 4`
      if [ "$port" == "" ]; then
        port=23
      fi
      putty -telnet ${address} -P ${port}

   /usr/local/bin/moz-ssh.sh:
      #!/bin/bash
      address=`echo $1 | cut -d / -f 3`
      port=`echo $1 | cut -d / -f 4`
      if [ "$port" == "" ]; then
        port=22
      fi
      putty -ssh ${address} -P ${port}

**Reference:**

   [http://www.cyberciti.biz/faq/how-do-i-turn-on-telnet-service-on-for-a-linuxfreebsd-system/](http://www.cyberciti.biz/faq/how-do-i-turn-on-telnet-service-on-for-a-linuxfreebsd-system/)
   [http://www.freelists.org/post/juneau-lug/Telnet-in-Firefox](http://www.freelists.org/post/juneau-lug/Telnet-in-Firefox)
   [http://ernstfamily.ch/jonathan/2008/10/ssh-and-telnet-protocol-handler-for-firefox/](http://ernstfamily.ch/jonathan/2008/10/ssh-and-telnet-protocol-handler-for-firefox/)
   [https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/480502](https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/480502)
   [http://ubuntuforums.org/showthread.php?p=2630018](http://ubuntuforums.org/showthread.php?p=2630018)
   + others I can't remember anymore

**My enviroment:**

   Ubuntu 9.10 Karmic Koala
   Gnome 2.28.1
   Firefox 3.5.7 (Mozilla Firefox for Ubuntu canonicle -1.0)

Hopefully this helps anyone.

Cheers

---

### Post by supine on 2010-02-25
"The right way" to do this is to register the handler (i.e your script(s) ) with gconf.

```
gconftool-2 -s /desktop/gnome/url-handlers/ssh/command '/path/to/app %s' --type String
gconftool-2 -s /desktop/gnome/url-handlers/ssh/enabled --type Boolean true
gconftool-2 -s /desktop/gnome/url-handlers/ssh/needs_terminal --type Boolean true
gconftool-2 -s /desktop/gnome/url-handlers/telnet/command '/path/to/app %s' --type String
gconftool-2 -s /desktop/gnome/url-handlers/telnet/enabled --type Boolean true
gconftool-2 -s /desktop/gnome/url-handlers/telnet/needs_terminal --type Boolean true
```

---

### Post by FlameLicker on 2010-02-25
Great! I looked for such kind of solution but could not find it. Thanks.

---

### Post by darky_mtp on 2011-02-08
Perfect !

---

