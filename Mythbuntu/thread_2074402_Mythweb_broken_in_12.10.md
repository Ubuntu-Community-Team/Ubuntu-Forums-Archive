---
title: "Mythweb broken in 12.10"
date: 2012-10-21
forum: Mythbuntu
---

### Post by riddles on 2012-10-21
This weekend, I upgraded my Ubuntu installation to 12.10. I've recently moved away from MythTV to TVHeadend for recording tv, but still have MythTV installed to see my old recordings. As a result, I no longer use the Mythbuntu repository, but use the default Ubuntu installation for MythTV. 

Unfortunately, Mythweb seems to be broken. In order to test, I've completely uninstalled Mythweb (with --purge) and reinstalled it. The only change I made is to enable RewriteBase in the config (my DocRoot is not /var/www). But, that doesn't help. I get the error message:
```
PHP Warning:  Unknown: function '0' not found or invalid function name in Unknown on line 0
```
Googling leads me to this Mythtv ticket: [http://code.mythtv.org/trac/ticket/10504](http://code.mythtv.org/trac/ticket/10504). It seems Mythweb is not compatible with php 5.4 (the default in Ubuntu 12.10). This has been fixed in MythTV 0.26.1. But, my version installed is 2:0.25.2+fixes.20120801. all. Does this mean the current Mythweb in Ubuntu is simply not compatible with PHP 5.4? Do I have any hopes of getting this working (without having to add the Mythbuntu repository and completely upgrading)?

---

### Post by nickrout on 2012-10-21
Clearly you haven't looked very hard, this was posted 2 hours ago and would have been about 3rd in the list of posts when you asked [http://ubuntuforums.org/showthread.php?t=2074363](http://ubuntuforums.org/showthread.php?t=2074363)

---

