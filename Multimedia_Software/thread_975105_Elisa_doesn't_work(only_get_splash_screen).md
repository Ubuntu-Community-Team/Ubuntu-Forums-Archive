---
title: "Elisa doesn't work(only get splash screen)"
date: 2008-11-08
forum: Multimedia Software
---

### Post by Glaecius on 2008-11-08
My Elisa media center doesn't work ever since i installed Intrepid Ibex.
I tried reinstalling python and Elisa dn everything but still doesnt work.
Here is what i get if i run Elisa in Terminal.

_______________________________________________________________


WARN  MainThread      plugin_registry             Nov 07 20:49:37  plugin conflict elisa-plugin-coherence 0.1 (elisa/core/plugin_registry.py:221)
WARN  MainThread      flickr_resource_provider    Nov 07 20:49:37  Login to Flickr failed. Full output at /tmp/elisa_t6p8jL.txt (elisa/plugins/flickr/resource_provider.py:90)
WARN  MainThread      resource_manager            Nov 07 20:49:37  Creating elisa.plugins.flickr.resource_provider:FlickrResourceProvider failed. A full traceback can be found at /tmp/elisa_9hwNAS.txt (elisa/core/manager.py:83)
WARN  MainThread      service_manager             Nov 07 20:49:37  Creating elisa.plugins.winscreensaver.winscreensaver:WinScreenSaver failed. A full traceback can be found at /tmp/elisa_dYHg-e.txt (elisa/core/manager.py:83)
WARN  MainThread      input_manager               Nov 07 20:49:37  Creating elisa.plugins.lirc.lirc_input:LircInput failed. A full traceback can be found at /tmp/elisa_etM1OL.txt (elisa/core/manager.py:83)
WARN  MainThread      interface_controller        Nov 07 20:49:37  creating frontend frontend1 failed. A full traceback can be found at [Failure instance: Traceback: <type 'exceptions.AttributeError'>: 'module' object has no attribute 'service'
/usr/lib/python2.5/site-packages/twisted/internet/gtk2reactor.py:226:simulate
/usr/lib/python2.5/site-packages/twisted/internet/base.py:705:runUntilCurrent
/usr/lib/python2.5/site-packages/twisted/internet/task.py:251:_tick
/usr/lib/python2.5/site-packages/elisa/core/interface_controller.py:104:load_frontends_iter
--- <exception caught here> ---
/usr/lib/python2.5/site-packages/elisa/core/plugin_registry.py:438:create_component
/usr/lib/python2.5/site-packages/twisted/python/reflect.py:426:namedAny
/usr/lib/python2.5/site-packages/twisted/python/reflect.py:377:_importAndCheckStack
/usr/lib/python2.5/site-packages/elisa/plugins/pigment/pigment_frontend.py:42:<module>
/usr/lib/python2.5/site-packages/elisa/plugins/pigment/dbus_frontend.py:20:<module>
] (elisa/core/interface_controller.py:88)
WARN  MainThread      interface_controller        Nov 07 20:49:37  Could not load any frontend (elisa/core/interface_controller.py:123)
WARN  MainThread      twisted                     Nov 07 20:49:37  A twisted traceback occurred. (twisted/internet/base.py:679)

Twisted traceback:
Traceback (most recent call last):
  File "/usr/bin/elisa", line 304, in main
    _start_reactor()
  File "/usr/bin/elisa", line 143, in _start_reactor
    reactor.run()
  File "/usr/lib/python2.5/site-packages/twisted/internet/gtk2reactor.py", line 186, in run
    self.__run()
  File "/usr/lib/python2.5/site-packages/twisted/internet/gtk2reactor.py", line 226, in simulate
    self.runUntilCurrent()
--- <exception caught here> ---
  File "/usr/lib/python2.5/site-packages/twisted/internet/base.py", line 677, in runUntilCurrent
    f(*a, **kw)
  File "/usr/lib/python2.5/site-packages/elisa/core/bus.py", line 178, in _dispatch
    callback(message, sender)
  File "/usr/lib/python2.5/site-packages/elisa/plugins/gnome/gnome_screensaver_service.py", line 137, in _components_loaded
    frontend = frontends.values()[0]
exceptions.IndexError: list index out of range

Does anyone know what to do?

---

### Post by kilativv on 2008-11-09
Hey,
I had a similar problem. Elisa wouldn't start. Try deleting its config directory:
```

rm -fr ~/.elisa
rm -fr ~./elisa-0.5
```
[COLOR="Red"]That will obviously delete all your customizations as well[/COLOR]. 
However it seems like elisa in Ibex is half-broken. Bunch of plugins don't work.

---

### Post by balaji.ramasubramanian on 2008-11-15
Ok, I had a big problem earlier. I would only see the splashscreen and everything would be dark. But I figured some way to fix it.

In ${HOME}/.elisa-0.5/elisa_0_5_6.conf, I changed the [frontend1] section to look like this. I hope this helps. Things started working perfectly for me after this.

[frontend1]
frontend = 'pigment.pigment_frontend:PigmentFrontend'
theme = 'elisa.plugins.poblesec'
controller_path = '/poblesec'
touchscreen = '0'
use_gtk = '1'
window_width = '0'
headless = '0'
start_fullscreen = '1'

---

### Post by Glaecius on 2008-11-22
well after a LOT of hassle i installed newer pigment trough the hardy repos, and at least i gotpast the splash screen, only to find myself in a black screen :P
well i'll try your last tip now, if that doesn't work i'm going back to hardy heron cause elisa is one of the only reasons i use that pc and i am NOT going back to windows:mad:

---

### Post by apoth on 2008-11-25
Yeah, this software isn't even appearing like alpha quality, it's crashing all over the place.

---

