---
title: "Installed Flash plugin will not work in lubuntu 13.10"
date: 2013-12-20
forum: Multimedia Software
---

### Post by xclegend on 2013-12-20
I am having issues with flash working on both firefox and chromium. I have the flash packages installed on both browsers. When i attempt to watch a flash video i get a black screen and or a plugin is needed message. This is a clean install of lubuntu 13.10. Any help would be greatly appreciated. Thanks.

---

### Post by tfrue on 2013-12-20
I recently had this problem, so what you need to do is create a new Firefox profile. I cant really help with the Chromium side, sorry. Open a terminal and type:
```
firefox -p
```
We are wanting to create a new profile, and Firefox will need to be closed, but you should get a box that prompts for a to 'Create a New Profile' 'Rename a Profile' and 'Delete Profile', but we want to create a new profile. So click the button to do so, and make sure you have the new profile selected and hit 'Start Firefox'. 

Hope this helps!

-Chris

---

### Post by Yellow Pasque on 2013-12-21
If your CPU is a bit dated (AMD Socket A, Pentium III or older), then the issue may be that your CPU does not support SSE2, which is needed for later versions of Flash. You can still download older versions of Flash from Adobe or you can try something open-source like Lightspark.

---

