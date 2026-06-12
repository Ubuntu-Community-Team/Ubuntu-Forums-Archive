---
title: "Watch YouTube Videos"
date: 2009-07-04
forum: Multimedia Software
---

### Post by AnotherMuggle on 2009-07-04
I wanted to watch YouTube videos so installed the suggested plugin: gstreamer0.10-plugins-bad but have noticed that some of the videos being in a broken state.  Is this because the plugin is "bad" as suggested in its name?

Is there a better plugin I can use so that playback is as good as I'd get in Windows?

Cheers,
Tom

---

### Post by lovinglinux on 2009-07-04
See **Solution** [*[COLOR="Red"]**FOT004**[/COLOR]*] from [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT004)

> **lovinglinux said:**
> 
Some video issues are caused by conflicting plug-ins. It's not a good idea to have multiple plug-ins for the same type of content.

To remove conflicting flash plug-ins and install only the one from Adobe Open "Applications >> Accessories >> Terminal", then paste (CTRL+SHIFT+V) the code below in the terminal window and hit enter:

```
sudo apt-get remove swfdec-mozilla mozilla-plugin-gnash && sudo apt-get install flashplugin-nonfree 
```



---

### Post by AnotherMuggle on 2009-07-04
> **lovinglinux said:**
> The solution to your problem is in the Troubleshooting section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

Thanks mate.  I will have a go now and see how I get on.  Much appreciated!!

I ran the command and followed the output.  Some old stuff was removed and the new plugin installed.  

I remain with a few issues.  Certain sites, here's an example: [http://www.gbatemp.net/](http://www.gbatemp.net/), tell me there are required plugins to install.  When I select the Flash Plugin it recommends, I am told it's already installed, yet it persists in asking me to install the plugin.

---

### Post by AnotherMuggle on 2009-07-05
Looks like I got it!

I went through the Firefox Add Ons menu and added the Adobe Flash Plugin, everything seems spot on now.

---

### Post by OpenBoss on 2009-07-05
Works clean in Firefox 3.5. Installed the flash 10 (.deb) package and it got running fine.

---

### Post by WatchingThePain on 2009-07-05
All I ever do is put ubuntu-restricted-extras (from synaptic), then flash works (including youtube) and that's on 64-bit Jaunty.

---

