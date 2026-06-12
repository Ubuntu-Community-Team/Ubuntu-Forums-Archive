---
title: "I Deleted Mythbuntu Control Center, Reinstall?"
date: 2009-07-09
forum: Mythbuntu
---

### Post by Macus on 2009-07-09
Hi all,

I have managed to delete MCC by accident

i was attempting to get LIRC to work and i got up to the IRW part, but then MCC wouldn't launch
so after some goggling I found that this will output the errors:

sudo /usr/share/mythbuntu-control-centre/bin/mythbuntu-control-centre

wich returned:


```
/var/lib/python-support/python2.6/MySQLdb/__init__.py:34: DeprecationWarning: the sets module is deprecated
  from sets import ImmutableSet
/usr/lib/python2.6/dist-packages/MythbuntuControlCentre/changer.py:48: DeprecationWarning: The popen2 module is deprecated.  Use the subprocess module.
  from popen2 import Popen3
Reading package lists... Done
Building dependency tree
Reading state information... Done
Traceback (most recent call last):
  File "/usr/share/mythbuntu-control-centre/bin/mythbuntu-control-centre", line 46, in <module>
    script = ControlCentre()
  File "/usr/lib/python2.6/dist-packages/MythbuntuControlCentre/core.py", line 189, in __init__
    populate_lirc(self)
  File "/usr/lib/python2.6/dist-packages/MythbuntuControlCentre/core.py", line 132, in populate_lirc
    self.lirc=LircHandler()
  File "/var/lib/python-support/python2.6/mythbuntu_common/lirc.py", line 64, in __init__
    self.read_hardware_conf(hw_conf)
  File "/var/lib/python-support/python2.6/mythbuntu_common/lirc.py", line 184, in read_hardware_conf
    self.remote_modules = string.split(line,'"')[1]
IndexError: list index out of range
```I saw that most of them were LIRC related, so I thought simply remove LIRC (deal with it later)
so I ran:

sudo apt-get remove lirc

but then I found that all refrence to MCC was GONE, was no longer on the system menu and was removed from the front end 

I tred the command agin but the dir /usr/share/mythbuntu-control-centre/ was gone too

so, any way to reinstall it?

---

### Post by Macus on 2009-07-09
Dont worry, I fixed it, turns out its in synaptic

BTW I found this to be a useful LIRC guide [http://en.kioskea.net/faq/sujet-1942-configure-your-tv-card-on-linux](http://en.kioskea.net/faq/sujet-1942-configure-your-tv-card-on-linux)

So far I can get IRW to respond but thats it

---

### Post by SiHa on 2009-07-09
If you're getting the correct button presses reported by IRW, then you're 95% of the way there. You just need to get the keymapping right in your lircrc.

---

