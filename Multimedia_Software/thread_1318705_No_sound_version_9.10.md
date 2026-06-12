---
title: "No sound version 9.10"
date: 2009-11-07
forum: Multimedia Software
---

### Post by bagman1301 on 2009-11-07
Being a new ubuntu user I was so pleased that version 9.04 loaded without any problems.
Everything worked. When I updated to version 9.10 I now have no sound. The O/S finds the sound card (SB Audigy 2) but when I choose preferences/sound I see a window that says " Waiting for sound system to respond ". And there it stops.

I have spent four days looking in the forums for an answer. I have tried almost everything suggested to no avail. I really want to make this work and retire my Vista machine. I can do everything with ubuntu I want to but not if the sound won't work. 

I do not want to reinstall 9.04 but I will if I have to.

Any help would be appriciated.

---

### Post by peterdvlhick on 2009-11-08
I'm having a similar problem in that the output on my sound is showing dummy output. My install today wasn't without hiccups. It had some big problems surrounding python. something to do with dpkg dependencies. I ran this in terminal:

peter@peter-desktop:~$ sudo dpkg --configure -a
[sudo] password for peter: 
Setting up python-zopeinterface (3.4.0-0ubuntu3.3) ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2196, in <module>
    main()
  File "/usr/bin/pycentral", line 2190, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1478, in run
    runtimes = get_installed_runtimes()
  File "/usr/bin/pycentral", line 279, in get_installed_runtimes
    default_version = pyversions.default_version(version_only=True)
  File "/usr/share/pycentral-data/pyversions.py", line 172, in default_version
    raise ValueError, "/usr/bin/python does not match the python default version. It must be reset to point to %s" % debian_default
ValueError: /usr/bin/python does not match the python default version. It must be reset to point to python2.6
dpkg: error processing python-zopeinterface (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of python-lazr-restfulclient:
 python-lazr-restfulclient depends on python-zope.interface | python-zopeinterface; however:
  Package python-zope.interface is not installed.
  Package python-zopeinterface is not configured yet.
dpkg: error processing python-lazr-restfulclient (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-twisted-core:
 python-twisted-core depends on python-zope.interface | python-zopeinterface (>= 3.2.1-3); however:
  Package python-zope.interface is not installed.
  Package python-zopeinterface is not configured yet.
dpkg: error processing python-twisted-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-ubuntuone-storageprotocol:
 python-ubuntuone-storageprotocol depends on python-twisted-core; however:
  Package python-twisted-core is not configured yet.
dpkg: error processing python-ubuntuone-storageprotocol (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-desktopcouch:
 python-desktopcouch depends on python-twisted-core; however:
  Package python-twisted-core is not configured yet.
dpkg: error processing python-desktopcouch (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-twisted-mail:
 python-twisted-mail depends on python-twisted-core (>= 8.2.0-2); however:
  Package python-twisted-core is not configured yet.
dpkg: error processing python-twisted-mail (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-desktopcouch-records:
 python-desktopcouch-records depends on python-desktopcouch; however:
  Package python-desktopcouch is not configured yet.
dpkg: error processing python-desktopcouch-records (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-launchpadlib:
 python-launchpadlib depends on python-lazr-restfulclient; however:
  Package python-lazr-restfulclient is not configured yet.
dpkg: error processing python-launchpadlib (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-twisted-names:
 python-twisted-names depends on python-twisted-core (>= 8.2); however:
  Package python-twisted-core is not configured yet.
dpkg: error processing python-twisted-names (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-twisted-conch:
 python-twisted-conch depends on python-twisted-core (>= 8.2.0-2); however:
  Package python-twisted-core is not configured yet.
dpkg: error processing python-twisted-conch (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-ubuntuone-client:
 python-ubuntuone-client depends on python-ubuntuone-storageprotocol (>= 0.95.0); however:
  Package python-ubuntuone-storageprotocol is not configured yet.
 python-ubuntuone-client depends on python-twisted-names; however:
  Package python-twisted-names is not configured yet.
dpkg: error processing python-ubuntuone-client (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-twisted:
 python-twisted depends on python-twisted-core (>= 8.2); however:
  Package python-twisted-core is not configured yet.
 python-twisted depends on python-twisted-conch (>= 1:8.2); however:
  Package python-twisted-conch is not configured yet.
 python-twisted depends on python-twisted-mail (>= 8.2); however:
  Package python-twisted-mail is not configured yet.
 python-twisted depends on python-twisted-names (>= 8.2); however:
  Package python-twisted-names is not configured yet.
dpkg: error processing python-twisted (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-twisted-web:
 python-twisted-web depends on python-twisted-core (>= 8.2.0-2); however:
  Package python-twisted-core is not configured yet.
dpkg: error processing python-twisted-web (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of desktopcouch:
 desktopcouch depends on python-twisted-core; however:
  Package python-twisted-core is not configured yet.
 desktopcouch depends on python-desktopcouch; however:
  Package python-desktopcouch is not configured yet.
 desktopcouch depends on python-desktopcouch-records; however:
  Package python-desktopcouch-records is not configured yet.
dpkg: error processing desktopcouch (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntuone-client:
 ubuntuone-client depends on python-ubuntuone-client (= 1.0.2-0ubuntu2); however:
  Package python-ubuntuone-client is not configured yet.
dpkg: error processing ubuntuone-client (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-apport:
 python-apport depends on python-launchpadlib; however:
  Package python-launchpadlib is not configured yet.
dpkg: error processing python-apport (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ardour:
 ardour depends on python-twisted; however:
  Package python-twisted is not configured yet.
dpkg: error processing ardour (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-twisted-runner:
 python-twisted-runner depends on python-twisted-core (>= 8.2); however:
  Package python-twisted-core is not configured yet.
dpkg: error processing python-twisted-runner (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-twisted-words:
 python-twisted-words depends on python-twisted-core (>= 8.2.0-2); however:
  Package python-twisted-core is not configured yet.
dpkg: error processing python-twisted-words (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-twisted-lore:
 python-twisted-lore depends on python-twisted-web (>= 8.2); however:
  Package python-twisted-web is not configured yet.
dpkg: error processing python-twisted-lore (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntuone-client-gnome:
 ubuntuone-client-gnome depends on ubuntuone-client (= 1.0.2-0ubuntu2); however:
  Package ubuntuone-client is not configured yet.
dpkg: error processing ubuntuone-client-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-couchdb:
 evolution-couchdb depends on desktopcouch; however:
  Package desktopcouch is not configured yet.
dpkg: error processing evolution-couchdb (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apport:
 apport depends on python-apport (>= 0.120); however:
  Package python-apport is not configured yet.
dpkg: error processing apport (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apport-gtk:
 apport-gtk depends on python-apport (>= 0.80); however:
  Package python-apport is not configured yet.
 apport-gtk depends on apport (>= 0.41); however:
  Package apport is not configured yet.
dpkg: error processing apport-gtk (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python-zopeinterface
 python-lazr-restfulclient
 python-twisted-core
 python-ubuntuone-storageprotocol
 python-desktopcouch
 python-twisted-mail
 python-desktopcouch-records
 python-launchpadlib
 python-twisted-names
 python-twisted-conch
 python-ubuntuone-client
 python-twisted
 python-twisted-web
 desktopcouch
 ubuntuone-client
 python-apport
 ardour
 python-twisted-runner
 python-twisted-words
 python-twisted-lore
 ubuntuone-client-gnome
 evolution-couchdb
 apport
 apport-gtk
peter@peter-desktop:~$ 

I have no sound, basic graphic capabilities and it all seems to stem from this trouble with Python.

Hope you can help

---

### Post by BabiiNiya on 2009-11-29
same goes to mine but it's say something about the alsa

---

### Post by omnipotentperson on 2009-11-29
It looks like you have the shortcut in /usr/bin/python for Python pointing to the wrong version. You could try deleting that, creating a new one for python 2.6, and running update manager.

> **peterdvlhick said:**
> I'm having a similar problem in that the output on my sound is showing dummy output. My install today wasn't without hiccups. It had some big problems surrounding python. something to do with dpkg dependencies. I ran this in terminal:

peter@peter-desktop:~$ sudo dpkg --configure -a
[sudo] password for peter: 
Setting up python-zopeinterface (3.4.0-0ubuntu3.3) ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2196, in <module>
    main()
  File "/usr/bin/pycentral", line 2190, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1478, in run
    runtimes = get_installed_runtimes()
  File "/usr/bin/pycentral", line 279, in get_installed_runtimes
    default_version = pyversions.default_version(version_only=True)
  File "/usr/share/pycentral-data/pyversions.py", line 172, in default_version
    raise ValueError, "/usr/bin/python does not match the python default version. It must be reset to point to %s" % debian_default
[COLOR="Red"]>>>>ValueError: /usr/bin/python does not match the python default version. It must be reset to point to python2.6[/COLOR]
dpkg: error processing python-zopeinterface (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of python-lazr-restfulclient:
 python-lazr-restfulclient depends on python-zope.interface | python-zopeinterface; however:
  Package python-zope.interface is not installed.
  Package python-zopeinterface is not configured yet.
dpkg: error processing python-lazr-restfulclient (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-twisted-core:
 python-twisted-core depends on python-zope.interface | python-zopeinterface (>= 3.2.1-3); however:
  Package python-zope.interface is not installed.
  Package python-zopeinterface is not configured yet.
dpkg: error processing python-twisted-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-ubuntuone-storageprotocol:
 python-ubuntuone-storageprotocol depends on python-twisted-core; however:
  Package python-twisted-core is not configured yet.
dpkg: error processing python-ubuntuone-storageprotocol (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-desktopcouch:
 python-desktopcouch depends on python-twisted-core; however:
  Package python-twisted-core is not configured yet.
dpkg: error processing python-desktopcouch (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-twisted-mail:
 python-twisted-mail depends on python-twisted-core (>= 8.2.0-2); however:
  Package python-twisted-core is not configured yet.
dpkg: error processing python-twisted-mail (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-desktopcouch-records:
 python-desktopcouch-records depends on python-desktopcouch; however:
  Package python-desktopcouch is not configured yet.
dpkg: error processing python-desktopcouch-records (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-launchpadlib:
 python-launchpadlib depends on python-lazr-restfulclient; however:
  Package python-lazr-restfulclient is not configured yet.
dpkg: error processing python-launchpadlib (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-twisted-names:
 python-twisted-names depends on python-twisted-core (>= 8.2); however:
  Package python-twisted-core is not configured yet.
dpkg: error processing python-twisted-names (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-twisted-conch:
 python-twisted-conch depends on python-twisted-core (>= 8.2.0-2); however:
  Package python-twisted-core is not configured yet.
dpkg: error processing python-twisted-conch (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-ubuntuone-client:
 python-ubuntuone-client depends on python-ubuntuone-storageprotocol (>= 0.95.0); however:
  Package python-ubuntuone-storageprotocol is not configured yet.
 python-ubuntuone-client depends on python-twisted-names; however:
  Package python-twisted-names is not configured yet.
dpkg: error processing python-ubuntuone-client (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-twisted:
 python-twisted depends on python-twisted-core (>= 8.2); however:
  Package python-twisted-core is not configured yet.
 python-twisted depends on python-twisted-conch (>= 1:8.2); however:
  Package python-twisted-conch is not configured yet.
 python-twisted depends on python-twisted-mail (>= 8.2); however:
  Package python-twisted-mail is not configured yet.
 python-twisted depends on python-twisted-names (>= 8.2); however:
  Package python-twisted-names is not configured yet.
dpkg: error processing python-twisted (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-twisted-web:
 python-twisted-web depends on python-twisted-core (>= 8.2.0-2); however:
  Package python-twisted-core is not configured yet.
dpkg: error processing python-twisted-web (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of desktopcouch:
 desktopcouch depends on python-twisted-core; however:
  Package python-twisted-core is not configured yet.
 desktopcouch depends on python-desktopcouch; however:
  Package python-desktopcouch is not configured yet.
 desktopcouch depends on python-desktopcouch-records; however:
  Package python-desktopcouch-records is not configured yet.
dpkg: error processing desktopcouch (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntuone-client:
 ubuntuone-client depends on python-ubuntuone-client (= 1.0.2-0ubuntu2); however:
  Package python-ubuntuone-client is not configured yet.
dpkg: error processing ubuntuone-client (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-apport:
 python-apport depends on python-launchpadlib; however:
  Package python-launchpadlib is not configured yet.
dpkg: error processing python-apport (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ardour:
 ardour depends on python-twisted; however:
  Package python-twisted is not configured yet.
dpkg: error processing ardour (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-twisted-runner:
 python-twisted-runner depends on python-twisted-core (>= 8.2); however:
  Package python-twisted-core is not configured yet.
dpkg: error processing python-twisted-runner (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-twisted-words:
 python-twisted-words depends on python-twisted-core (>= 8.2.0-2); however:
  Package python-twisted-core is not configured yet.
dpkg: error processing python-twisted-words (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-twisted-lore:
 python-twisted-lore depends on python-twisted-web (>= 8.2); however:
  Package python-twisted-web is not configured yet.
dpkg: error processing python-twisted-lore (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntuone-client-gnome:
 ubuntuone-client-gnome depends on ubuntuone-client (= 1.0.2-0ubuntu2); however:
  Package ubuntuone-client is not configured yet.
dpkg: error processing ubuntuone-client-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-couchdb:
 evolution-couchdb depends on desktopcouch; however:
  Package desktopcouch is not configured yet.
dpkg: error processing evolution-couchdb (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apport:
 apport depends on python-apport (>= 0.120); however:
  Package python-apport is not configured yet.
dpkg: error processing apport (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apport-gtk:
 apport-gtk depends on python-apport (>= 0.80); however:
  Package python-apport is not configured yet.
 apport-gtk depends on apport (>= 0.41); however:
  Package apport is not configured yet.
dpkg: error processing apport-gtk (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python-zopeinterface
 python-lazr-restfulclient
 python-twisted-core
 python-ubuntuone-storageprotocol
 python-desktopcouch
 python-twisted-mail
 python-desktopcouch-records
 python-launchpadlib
 python-twisted-names
 python-twisted-conch
 python-ubuntuone-client
 python-twisted
 python-twisted-web
 desktopcouch
 ubuntuone-client
 python-apport
 ardour
 python-twisted-runner
 python-twisted-words
 python-twisted-lore
 ubuntuone-client-gnome
 evolution-couchdb
 apport
 apport-gtk
peter@peter-desktop:~$ 

I have no sound, basic graphic capabilities and it all seems to stem from this trouble with Python.

Hope you can help

Sorry Bagman1301, I don't know about your problem. However, there seem to be a lot of problems with sound in the new version. I was unable to use sound for several weeks after I upgraded. You might want to try reinstalling the sound drivers. I have had a lot of problems with Ubuntu deleting drivers upon an upgrade, or with files becoming corrupt. I managed to fix my problem by deleting a corrupt log file.

---

