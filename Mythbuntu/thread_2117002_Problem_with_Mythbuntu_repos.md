---
title: "Problem with Mythbuntu repos"
date: 2013-02-17
forum: Mythbuntu
---

### Post by acodring on 2013-02-17
I've got a mythbuntu system that I left on 9.04 for a few years. Last year in a moment of weakness I dist-upgraded through to 12.04 over a weekend.

I don't think I checked if MCC continued working at each dist step, but it doesn't work well now.

For a while it wouldn't open at all.

Today I've been opening it from the terminal as suggested above. I can see Repositories and Log Grabber.

If I select Repositories and then 'Activate Mythtv repositories' and Apply it hangs.

Here's the output:


```
acodring@mythbackend:~$ sudo mythbuntu-control-centre
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ERROR: Unable to set arguments ({'mythbuntu_repos': {'MythTV-Updates-Repo': None}}, '/usr/share/mythbuntu/plugins') according to signature u'a{sa{sv}}s': <type 'exceptions.TypeError'>: Don't know which D-Bus type to use to encode type "NoneType"
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 604, in msg_reply_handler
    reply_handler(*message.get_args_list(**get_args_opts))
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 401, in _introspect_reply_handler
    self._introspect_execute_queue()
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 387, in _introspect_execute_queue
    proxy_method(*args, **keywords)
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 137, in __call__
    **keywords)
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 584, in call_async
    message.append(signature=signature, *args)
TypeError: Don't know which D-Bus type to use to encode type "NoneType"

```

I should mention that mythtv is working OK. I've had trouble with my HD PVR locking up, but that's a separate thing.


Lately I'm not seeing any mythv updates coming through but that might be normal given that I'm still on .25.
As I wrote this I noticed that the mythbuntu repos were still pointing at oneiric instead of precise. 
I changed it and suddenly there are myth updates again... 

Not sure if this will be helpful for anyone or just confusing, but there it is.

---

### Post by Bucky Ball on 2013-02-17
[I][B]Your post has been moved to its own thread.
[/B][/I]
Please post new threads rather than hijacking existing threads with thread titles bearing no relation to your issue. It dilutes community effort, creates confusion and is unfair to the original poster. 

You will greatly improve your chances of getting help by creating your own thread with a descriptive title and as much information as you can provide about your problem. 

Good luck.

BB

---

