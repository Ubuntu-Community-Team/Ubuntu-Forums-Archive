---
title: "Adobe Flashplayer"
date: 2012-08-25
forum: Multimedia Software
---

### Post by jakell on 2012-08-25
OK. I know v 11.2 is problematic, and how to revert to v11.1 to get things working again.

I'm just wondering whether 11.2 works on *_any_*  'buntu setup (or other linux), if not, why is it still offered as updates in the repositories?

I tried the latest update to see if they had fixed the issue.... no luck, so back to 11.1 again


(using Xubuntu 12.04.1, system wont let me access my CP)

---

### Post by ajgreeny on 2012-08-25
Flash 11.2 is still not "fixed" and is probably not going to be for us, as Adobe have stopped supporting flash on linux, and will only continue with the current versions that are available.

I am fairly sure that the problem with flash 11.2 is caused by some ATI graphic cards; possibly older ones that use the open source driver, but I have no real evidence for that latter statement.  I can not use 11.2 as I get no video at all if I do, not even a blank video window, and I have an ATI 9200SE graphics card (and an AMD Sempron 2400+, though I don't think that is implicated).  I have seen other ATI 9200SE card users who have exactly my problem, hence my thoughts that the card is the problem.

Carry on with flash 11.1.102-63, but make sure you are using flashblock or no-script add-on if using Firefox, to reduce the security risks.  Flashblock is also available as an extension for chrome/chromium, but I'm not sure about no-script.

PS: You can't edit your CP until you have 50 posts, but that will not take long if you visit the forum much.

---

### Post by jakell on 2012-08-25
> **ajgreeny said:**
> Flash 11.2 is still not "fixed" and is probably not going to be for us, as Adobe have stopped supporting flash on linux, and will only continue with the current versions that are available.

I am fairly sure that the problem with flash 11.2 is caused by some ATI graphic cards; possibly older ones that use the open source driver, but I have no real evidence for that latter statement.  I can not use 11.2 as I get no video at all if I do, not even a blank video window, and I have an ATI 9200SE graphics card (and an AMD Sempron 2400+, though I don't think that is implicated).  I have seen other ATI 9200SE card users who have exactly my problem, hence my thoughts that the card is the problem.

Carry on with flash 11.1.102-63, but make sure you are using flashblock or no-script add-on if using Firefox, to reduce the security risks.  Flashblock is also available as an extension for chrome/chromium, but I'm not sure about no-script.

PS: You can't edit your CP until you have 50 posts, but that will not take long if you visit the forum much.

Thanks for replying.

It's not just ATI cards, I use Nvidia FX5700's, with or without the proprietory drivers, and get the same issues. I also use an old system
(Sempron 2400, VIA KT600 chipset).

I just wish Ubuntu would drop Flash 11.2 from their repositories, it keeps nagging at me for updates, and must be especially annoying/frustrating for newer users

---

### Post by laithbsoul on 2012-08-25
To get it to stop bugging you about updating the flash plugin try

```
# aptitude hold flashplugin-nonfree
```

iirc

---

### Post by Gokutux on 2012-08-26
Try Google Chrome!!! You do not need to install the Flashplayer... I think is the best choice! :p

---

### Post by ajgreeny on 2012-08-26
The easiest way to stop the update prompts is simply to copy the** libflashplayer.so** file of version 11.1.102-63 that works OK for you into /home/user/.mozilla/plugins and then uninstall the package that you installed to get flash.

Just search for flash using synaptic and remove what you find with that, and you will get no more flash update prompts.

---

### Post by jakell on 2012-08-26
> **Gokutux said:**
> Try Google Chrome!!! You do not need to install the Flashplayer... I think is the best choice! :p

I have found that Chrome uses the plugin that the system has installed. When I removed Flash, and then did a fresh install of Chrome, it complained that the plugin was missing.

---

### Post by jakell on 2012-08-26
> **ajgreeny said:**
> The easiest way to stop the update prompts is simply to copy the** libflashplayer.so** file of version 11.1.102-63 that works OK for you into /home/user/.mozilla/plugins and then uninstall the package that you installed to get flash.

Just search for flash using synaptic and remove what you find with that, and you will get no more flash update prompts.

Up till now, I've been replacing the flashplayer.so file in /usr/lib/flashplayer-installer with v 11.1. I have realised that there are several locations where browsers can 'find' the plugin. 
Also, in my installation there is no 'plugin' folder in /home/user/.mozilla

 The nagging to 'upgrade' doesn't really bother me, I just untick it. It does seem an untidy loose-end though and probably quite frustrating to newer users

---

### Post by Gokutux on 2012-08-26
> **jakell said:**
> I have found that Chrome uses the plugin that the system has installed. When I removed Flash, and then did a fresh install of Chrome, it complained that the plugin was missing.

On my system when I installed the Chrome didn't requested me for any plugin...

---

### Post by ajgreeny on 2012-08-26
> **jakell said:**
> Up till now, I've been replacing the flashplayer.so file in /usr/lib/flashplayer-installer with v 11.1. I have realised that there are several locations where browsers can 'find' the plugin. 
Also, in my installation there is no 'plugin' folder in /home/user/.mozilla

 The nagging to 'upgrade' doesn't really bother me, I just untick it. It does seem an untidy loose-end though and probably quite frustrating to newer users
I would remove all extant versions of **libflashplayer.so** from the system except the one in **/home/user/.mozilla/plugins**.  You will normally need to make that folder manually as it is not present by default.

You can find all the files with ```
locate libflashplayer.so
``` then remove the files, or just remove whatever packages you have installed for the flash plugin, but leave the 11.1 version still in  /home/user/.mozilla/plugins.

I promise it does save a lot of faffing around when flash packages are in the upgrades, as now your system will not have a flash package that the package manager knows about.

---

### Post by rookcifer on 2012-08-26
My problem with Flash is the smurfing effect (blue washed out colors in videos).  I have tried all the fixes but they cause Flash to crash continuously.  HTML5 fixes this problem but not all YouTube videos use HTML5.

Does anyone know what Flash version is the latest version that doesn't suffer from this smurf effect?

---

### Post by jakell on 2012-08-26
> **ajgreeny said:**
> I would remove all extant versions of **libflashplayer.so** from the system except the one in **/home/user/.mozilla/plugins**.  You will normally need to make that folder manually as it is not present by default.

You can find all the files with ```
locate libflashplayer.so
``` then remove the files, or just remove whatever packages you have installed for the flash plugin, but leave the 11.1 version still in  /home/user/.mozilla/plugins.

I promise it does save a lot of faffing around when flash packages are in the upgrades, as now your system will not have a flash package that the package manager knows about.

I've done all this, but the flashplayer has now reverted to Gnash, and the same has happened in Chrome. Gnash seems to work ok, but is jumpy when small, and unwatchable in fullscreen mode.

I'm not sure how to make Firefox find flashplayer.so in the new location. My Firefox folder is more complicated than you describe ie /home/user/.mozilla/w5bvfgdm.default/extensions.....
I think it is in this 'extensions' folder where plugins are stored, but it is not obvious how this is done.
 I may try a fresh install of Firefox, as the folder from this has passed through several upgrades.

Interestingly, a reinstallation of Chrome has brought with it the old v11.1 Flashplayer, but this cannot be found using locate, so I guess it's 'buried' somewhere under a different name. Firefox cannot find this either and is still using Gnash.

---

### Post by ajgreeny on 2012-08-26
If the disabling hardware acceleration does not work for you try version 11.1.102-63 details of which you can find at [Flash 11.1.102-63]("http://ubuntuforums.org/showthread.php?t=1953796").  Thanks to lovinglinux for all the hard work he's done on this problem.

---

### Post by jakell on 2012-08-27
> **jakell said:**
> 
Interestingly, a reinstallation of Chrome has brought with it the old v11.1 Flashplayer, but this cannot be found using locate, so I guess it's 'buried' somewhere under a different name. Firefox cannot find this either and is still using Gnash.

My mistake, after some investigation it seemed that Chrome had found the flashplayer.so I had put in /home/user/.mozilla/plugins, and now firefox has done this too. 
 Two positives though, updates no londer nag me about updating flash, and I don't have to open a root version of thunar to access/change the plugin.

Thanks for the links above.

---

### Post by jakell on 2012-08-28
I want to mark this thread as SOLVED, how do I do this?

 The issue about about flash updating itself has been fixed for me. Thanks to all who helped.

---

### Post by ajgreeny on 2012-08-28
> **jakell said:**
> I want to mark this thread as SOLVED, how do I do this?

 The issue about about flash updating itself has been fixed for me. Thanks to all who helped.
Go to the start of the thread, and in **Thread Tools** menu you can mark it SOLVED.

---

