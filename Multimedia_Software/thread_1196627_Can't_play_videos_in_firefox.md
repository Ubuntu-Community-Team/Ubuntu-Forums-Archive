---
title: "Can't play videos in firefox"
date: 2009-06-25
forum: Multimedia Software
---

### Post by da85 on 2009-06-25
Hi

I'm running the latest released version of ubuntu with firefox 3.0.11

The problem is that I can't play videos like youtube

When I go to these sites, where the video normally is i just get a big black box with a play symbol in the middle with a circle.

I often also get this for advertisements on websites

Can anyone let me know what i need to do to watch videos?

Thanks

---

### Post by PaganHippie on 2009-06-25
Install one of the Flash plugins

---

### Post by d3ngar on 2009-06-25
Hi da85,

Videos on YouTube are played through flash-player.
You might need to install the right plug-in...

Start the package manager:
System >> Administration >> Synaptic Package Manager

Type in the quick search: flash

Somewhere you should see the adobe-flashplugin, simply install this, restart your browser and check it out.

I'm not sure if there is an adobe flash-player for 64bit yet (just in case you have installed a 64bit version (note, it's always good to tell people what OS version you are running)). I used to run a 64bit version and had no problems with flash. There are some replacements available though. I'm not sure which one I used, but try Gnash...

Hope this helps.


Chris

---

### Post by Divider on 2009-06-25
Get the latest version of flash from adobe.

Get the .deb package, let it download and then close all firefox windows and install it.

Works like a charm. :)

-Divider

---

### Post by da85 on 2009-06-25
I've checked and the latest version of flash is installed so it shouldn't be that.

My system is 32 bit.

The main problem seems to be this play symbol appearing in flash boxes.

---

### Post by 6205 on 2009-06-25
For this i am using with Flash player also gstreamer plugins 'ffmpeg', 'bad' and 'ugly' versions. You should have already installed 'good' plugins. 

Also for non-flash embeded videos i am using default totem mozilla plugin with those plugins and everything works fine..

---

### Post by lovinglinux on 2009-06-25
The solution to your problem is my [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567). Take a look in the troubleshooting section.

> **lovinglinux said:**
> 

**Problems:**

[list][*] 
[*] **Can't play streaming videos**
[*] **Flash videos display only a symbol and won't start**[/list]

**Solution:**

Some video issues are caused by conflicting plug-ins. It's not a good idea to have multiple plug-ins for the same type of content. You can disable plug-ins through the Addons window. Open "Tools >> Addons", then select the "Plug-ins" icon, then select the plug-in you want to disable and click the "Disable" button. Unfortunately, this not work every time, so the best procedure is to remove the conflicting plug-ins.

To remove conflicting flash plug-ins and install only the one from Adobe open "Applications >> Accessories >> Terminal", then paste (CTRL+SHIFT+V) the code below in the terminal window and hit enter:

```
sudo apt-get remove swfdec-mozilla mozilla-plugin-gnash && sudo apt-get install flashplugin-nonfree 
```

To solve additional video issues, visit the [Comprehensive Multimedia & Video Howto](http://ubuntuforums.org/showthread.php?t=766683). It solves most of the problems related to video codecs and plug-ins.

---

