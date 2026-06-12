---
title: "Flash stopped working in Firefox"
date: 2009-08-10
forum: Multimedia Software
---

### Post by martinstr on 2009-08-10
When I installed Ubuntu (9.04) I unfortunately selected Gnash as the flash plugin for Firefox. When I tried to remove it and install the Adobe plugin, flash stopped working altogether. I've tried doing:

```
sudo apt-get remove --purge swfdec-mozilla mozilla-plugin-gnash flashplugin-nonfree adobe-flashplugin

sudo apt-get install adobe-flashplugin
```

But if I type about:plugins in the Firefox address bar, no flash plugin shows up, and Firefox is unable to play flash.

Any suggestions how to get flash working in Firefox again?

Thanks!

/Martin

---

### Post by Tclarkie on 2009-08-10
[I]this might (should) work    
[http://ubuntuforums.org/showthread.php?t=1230177&highlight=flash+player](http://ubuntuforums.org/showthread.php?t=1230177&highlight=flash+player) 			[/I]

---

### Post by martinstr on 2009-08-10
[I]> this might (should) workThanks for the reply. Like you say this should work and it is what I've tried doing. However after installing the plugin it doesn't show up in about:plugins in Firefox. I'm completely stumped. It should be so straight-forward... 
[/I]

---

### Post by carlmig on 2009-08-10
I had the same problem.

I uninstalled the flash plugin. Then, I installed it again, not from synaptic, but from inside the browser, when it alerts you that you have missing plugins.
That worked for me.

---

### Post by Tclarkie on 2009-08-10
> **martinstr said:**
> [I]Thanks for the reply. Like you say this should work and it is what I've tried doing. However after installing the plugin it doesn't show up in about:plugins in Firefox. I'm completely stumped. It should be so straight-forward... 
[/I]

What version of firefox are you running

---

### Post by HappyFeet on 2009-08-10
Remove gnash or any other flash you may have installed, and go [here]("http://get.adobe.com/flashplayer/") and download the .deb flash file for ubuntu 8.04+

Click to install. Restart firefox.

---

### Post by martinstr on 2009-08-12
Thanks for all replies!

> I uninstalled the flash plugin. Then, I installed it again, not from synaptic, but from inside the browser, when it alerts you that you have missing plugins.
That worked for me. 	

Didn't do the trick... :-(

> What version of firefox are you running

3.5.3pre, but the problem has been with me since 3.0.

> Remove gnash or any other flash you may have installed, and go [here]("http://get.adobe.com/flashplayer/") and download the .deb flash file for ubuntu 8.04+

Click to install. Restart firefox. 	

No luck, unfortunately. :(

The following command should get rid of all possible flash installations, right?

sudo apt-get remove --purge swfdec-mozilla mozilla-plugin-gnash flashplugin-nonfree adobe-flashplugin

---

