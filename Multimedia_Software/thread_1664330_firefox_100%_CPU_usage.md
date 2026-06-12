---
title: "firefox 100% CPU usage"
date: 2011-01-10
forum: Multimedia Software
---

### Post by supasoaker on 2011-01-10
I know on windows firefox currently has an issue with playing flash stuff such as youtube and this is related to the new plugin-container they have put together, where videos will play slowly as for some reason the CPU usage rockets up to 100%..............

I am not the only one with this issue...........now I have found the same problem on Ubuntu - does anyone know if it can be fixed?

---

### Post by lovinglinux on 2011-01-11
You can disable the plugin container via about[noparse]:[/noparse]config:

[http://kb.mozillazine.org/Plugin-container_and_out-of-process_plugins#Plugin-container](http://kb.mozillazine.org/Plugin-container_and_out-of-process_plugins#Plugin-container)

But I would recommend trying my [Flash-Aid]("https://addons.mozilla.org/en-US/firefox/addon/161939/") extension first, since it will install the latest square preview and apply some performance tweaks.

---

### Post by supasoaker on 2011-01-12
thanks - tried both and still no go...........I did notice a slight performance increase with your plugin.....haven't restarted yet but internet seems to be slower now!!!! :(

trying to get this to work with lots of other flash windows open at the same time, my PC still isn't having it and its a 6Ghz+ Dual core with 4GB ram which should take this kind of abuse..........

[http://www.youtube.com/watch?v=sSO5DDLHnhQ](http://www.youtube.com/watch?v=sSO5DDLHnhQ)

still stalls :confused:

i'm gonna keep the plugin container off for now, does it need to be on for your plugin to work properly?

---

### Post by lovinglinux on 2011-01-12
> **supasoaker said:**
> i'm gonna keep the plugin container off for now, does it need to be on for your plugin to work properly?

Nope. What Flash-Aid does is simply to create a installation/removal/tweaking script based on your system information, in order to remove conflicting plugins, install the best version and apply some tweaks. It only do something when you hit the "Execute" button. When you are not interacting with the extension, it only check for flash beta updates once a day, nothing else. It doesn't interact with the flash plugin itself or the plugin container. It is just a script generator.

---

