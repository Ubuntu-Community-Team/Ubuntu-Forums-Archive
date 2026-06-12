---
title: "Can't figure out how to change flash plugin for firefox"
date: 2008-04-23
forum: Multimedia Software
---

### Post by p-stone on 2008-04-23
Hi all

So I loaded on the RC for Hardy, opened up firefox and tried to check out some youtube. As expected I was asked to pick a plugin, I saw gnash, flash-nonfree and a third option I hadn't seen before, I'm afraid I can't recall the name. Feeling adventurous I picked the third option and installed it. Sadly it's not quite up to the task, it will load youtube but it won't ever get anywhere and play videos. What I'd like to do is simply remove this plugin and use flash-nonfree, which I know will work without a hitch. However I can't seem to find the plugin in question in my package manager and there's no option to remove it from firefox, disabling it doesn't let me try and install a new plugin. I've installed flash-nonfree but I can't figure out where to tell firefox to use it instead. Any help would be appreciated, thanks much

---

### Post by warp99 on 2008-04-23
Delete the old flash plugins from your '/usr/lib/firefox/plugins' or ~/.mozilla/firefox/plugins directory. Then download the plugin from Adobe:

[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&promoid=BUIGP](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&promoid=BUIGP)

and follow the installation instructions:

[http://www.adobe.com/products/flashplayer/productinfo/instructions/](http://www.adobe.com/products/flashplayer/productinfo/instructions/)

---

