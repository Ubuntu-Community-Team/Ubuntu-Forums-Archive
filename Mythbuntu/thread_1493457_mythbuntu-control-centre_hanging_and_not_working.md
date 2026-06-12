---
title: "mythbuntu-control-centre hanging and not working"
date: 2010-05-25
forum: Mythbuntu
---

### Post by yzfr1 on 2010-05-25
Just updated to 10.04

I am trying to make updates in mythbuntu-control-centre and it just hangs with a waiting cursor... 


I tried using the terminal and typing ```
sudo mythbuntu-control-centre
``` which just opens the mcc.  I get the following errors when I click apply.

```
process 5311: Array or variant type requires that type variant be written, but end_dict_entry was written.
The overall signature expected here was 'a{sa{sv}}' and we are on byte 6 of that signature.
ERROR: Unable to set arguments ({'proprietary_codecs': {'DVD Support': True}, 'mythbuntu_repos': {'WeeklyRepo': None}}, '/usr/share/mythbuntu/plugins') according to signature u'a{sa{sv}}s': <type 'exceptions.TypeError'>: Don't know how which D-Bus type to use to encode type "NoneType"
Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/dbus/connection.py", line 576, in msg_reply_handler
    reply_handler(*message.get_args_list(**get_args_opts))
  File "/usr/lib/pymodules/python2.6/dbus/proxies.py", line 391, in _introspect_reply_handler
    self._introspect_execute_queue()
  File "/usr/lib/pymodules/python2.6/dbus/proxies.py", line 378, in _introspect_execute_queue
    proxy_method(*args, **keywords)
  File "/usr/lib/pymodules/python2.6/dbus/proxies.py", line 132, in __call__
    **keywords)
  File "/usr/lib/pymodules/python2.6/dbus/connection.py", line 556, in call_async
    message.append(signature=signature, *args)
TypeError: Don't know how which D-Bus type to use to encode type "NoneType"

```Does anyone know what this means?  I have searched a lot of these errors but have not found anything.

---

### Post by superm1 on 2010-05-26
> **yzfr1 said:**
> Just updated to 10.04

I am trying to make updates in mythbuntu-control-centre and it just hangs with a waiting cursor... 


I tried using the terminal and typing ```
sudo mythbuntu-control-centre
``` which just opens the mcc.  I get the following errors when I click apply.

```
process 5311: Array or variant type requires that type variant be written, but end_dict_entry was written.
The overall signature expected here was 'a{sa{sv}}' and we are on byte 6 of that signature.
ERROR: Unable to set arguments ({'proprietary_codecs': {'DVD Support': True}, 'mythbuntu_repos': {'WeeklyRepo': None}}, '/usr/share/mythbuntu/plugins') according to signature u'a{sa{sv}}s': <type 'exceptions.TypeError'>: Don't know how which D-Bus type to use to encode type "NoneType"
Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/dbus/connection.py", line 576, in msg_reply_handler
    reply_handler(*message.get_args_list(**get_args_opts))
  File "/usr/lib/pymodules/python2.6/dbus/proxies.py", line 391, in _introspect_reply_handler
    self._introspect_execute_queue()
  File "/usr/lib/pymodules/python2.6/dbus/proxies.py", line 378, in _introspect_execute_queue
    proxy_method(*args, **keywords)
  File "/usr/lib/pymodules/python2.6/dbus/proxies.py", line 132, in __call__
    **keywords)
  File "/usr/lib/pymodules/python2.6/dbus/connection.py", line 556, in call_async
    message.append(signature=signature, *args)
TypeError: Don't know how which D-Bus type to use to encode type "NoneType"

```Does anyone know what this means?  I have searched a lot of these errors but have not found anything.

For starters, don't launch as root.  Do you have an old mythbuntu-repos installed?  Could you go fetch it from mythbuntu.org again and try again?

---

### Post by tgm4883 on 2010-05-26
What version of mythbuntu-common do you have?

---

### Post by yzfr1 on 2010-05-26
> **tgm4883 said:**
> What version of mythbuntu-common do you have?

How do I find that out?

> Could you go fetch it from mythbuntu.org again and try again?

What am I fetching from mythbuntu.org?

---

### Post by superm1 on 2010-05-26
```
dpkg -l | grep mythbuntu-common
dpkg -l | grep mythbuntu-repos
```

Will tell you the versions.

[http://www.mythbuntu.org/auto-builds](http://www.mythbuntu.org/auto-builds) will get you the updated mythbuntu-repos.

---

### Post by yzfr1 on 2010-05-26
dpkg -l | grep mythbuntu-common

```
ii  mythbuntu-common                           0.50-0ubuntu1                                   Mythbuntu application support functions
```

dpkg -l | grep mythbuntu-repos

```
ii  mythbuntu-repos                            7.5-0ubuntu0+mythbuntu~lucid                    Mythbuntu repos installer
```

---

### Post by tgm4883 on 2010-05-27
Odd, same versions I have here and I'm not getting the error messages. Can you check the following

```

dpkg -l dbus
dpkg -l python
md5sum /usr/lib/python2.6/dist-packages/mythbuntu_common/dictionaries.py

```

---

### Post by purple52 on 2010-12-05
I had a very similar problem on a new Maverick frontend. After a lot of digging, I think I tracked down the problem.

On the Repositories plugin in the control centre, there are two dropdown menus. In my case, the second menu (location) had no value - neither "DE" or "PPA" was selected. The control centre would not let me select a value due to a permissions problem, so from the command line I ran:

```
sudo dpkg-reconfigure mythbuntu-repos
```And selected "PPA" as the repo location. I can now apply changes in the control centre.

Your error message is very slightly different to mine - but my guess is that some other field in your Repositories plugin has no value - eg, the first dropdown menu where you select a build.

---

### Post by yojimbo-San on 2011-01-15
> **yzfr1 said:**
> I am trying to make updates in mythbuntu-control-centre and it just hangs with a waiting cursor... 


Check to see if the package aptdaemon is installed; this is required but oddly missing on some new installs.

---

