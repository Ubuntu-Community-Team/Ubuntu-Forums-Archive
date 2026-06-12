---
title: "Upgraded to Jaunty, hulu et al stopped working"
date: 2009-05-02
forum: Multimedia Software
---

### Post by IsmAvatar on 2009-05-02
The title pretty much explains it. 

I upgraded to Jaunty (9.04) recently, and it must have uninstalled flash or something, because some sites that need it (in firefox) told me that I needed a plugin for flash, so I installed it, and it worked for the most part, like Youtube now works. However, Hulu stopped working. I'll click on one of the thumbnails, and it'll load the page, but the movie itself will not appear - the space will just be that black-gray gradient for hulu. I've experienced this at other places as well, but youtube works fine.

Also, games on like Addicting Games often run into problems which make them unplayable, like I can't click a button, or pressing an arrow key brings up a menu, etc. I believe this is related.

I think what happened was I installed a different version of Flash, like a non-proprietary version or something, because now whenever I see a flash video, instead of a preview of one of the frames like it did before, now it just shows me a gray box with a play button in the middle. 
I don't really care whether I have the proprietary version, just as long as I have a version that *works*.

Thanks
-IsmAvatar

---

### Post by IsmAvatar on 2009-05-04
Anybody? Please?

---

### Post by inobe on 2009-05-04
if you have **swfdec-mozilla** installed remove it from synaptic then try.

---

### Post by zzyx on 2009-05-04
Hi, I have the same problem. It was working under the 9.02 install via Wubi. After updating, I lost HULU apparently due to auto upgrade to 9.04. I am struggling with Flash plugin.

Hi Inobe, I tried your suggestion but no change. However, I am writing this before restarting FF. I will let you guys know if it works after restart.

---

### Post by zzyx on 2009-05-04
Hi!

Before changing things via terminal make sure you have the following packages installed via Synaptic Package Manager (do a search and install as necessary):

   mozilla-plugin-gnash
   flashplugin-nonfree

After installing, make sure to close the Synaptic Package Manager. Open the Terminal and follow the instruction below using the provided commands:

   1. remove all orphan and broken files

     'sudo apt-get autoremove'

   2. purge old plugins

     'sudo apt-get remove --purge swfdec-mozilla mozilla-plugin-gnash flashplugin-nonfree adobe-flashplugin'

   3. i think this gets the appropriate plugin

     'sudo apt-get install adobe-flashplugin'

   4. reset your network connection to refresh the lines
   5. go to hulu and choose a video
   6. click to play but give it time to do its thing 

Mine took about 5-10 minutes and it will depend on how quickly your hardware resets and purges its cache, etc. 
I hope this helps you as it worked for me like a charm.

Cheers!

---

### Post by IsmAvatar on 2009-05-04
I got all that up until step 3

```
$ sudo apt-get install adobe-flashplugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package adobe-flashplugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package adobe-flashplugin has no installation candidate
```

---

### Post by IsmAvatar on 2009-05-04
i got it! I used synaptic package manager to install flashplugin-nonfree (after following steps 1 and 2 above), and restarted firefox. Hulu worked.

Thanks so much guys. Solved.

-IsmAvatar

---

### Post by jshaw22 on 2009-05-19
Same thing happened to me when I upgraded to Jaunty. Thank you for the directions!!!! Everything worked perfectly for me even though I also got the 

Package adobe-flashplugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package adobe-flashplugin has no installation candidate


message.

thanks agian!!

---

### Post by stickx911 on 2009-05-20
worked for me!

Thanks

---

### Post by neogeek on 2009-05-21
Works for me ... now I can play Pet society on FB again :popcorn:

---

### Post by mbspark on 2009-09-16
> **inobe said:**
> if you have **swfdec-mozilla** installed remove it from synaptic then try.

Just want to say this worked for me on getting slacker radio to work. Thanks forums.

---

### Post by revekha on 2009-10-01
This did the trick! Thanks so much.

---

