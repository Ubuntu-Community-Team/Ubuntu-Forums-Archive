---
title: "Videos/Movies are missing after upgrade to .26"
date: 2013-02-15
forum: Mythbuntu
---

### Post by voron on 2013-02-15
First post here.

I've been using Mythbuntu 11.10/MythTV 0.24 for about a year. Single box with BE and FE. After a recent upgrade to 12.04 and 0.25, and then to 0.26 I've got several thing broken.

The is no more 'Watch Videos' menu in the 'Media Library'. I was using storage groups in 0.24 and they have not changed. Database still have all my videos. Also MythWeb can list all of them with the correct metadata. Even WD TV used as DNLA client connected to my backend can list all my videos.   

I know that MythVideo  was merged with the core MythTV in 0.25. Do I need to do anything special to enable Videos in the FE?

There is no errors in logs.

---

### Post by larsolav on 2013-02-15
I think there may be a section in mythbuntu-control-centre where you can check (and undcheck) video. look around in mcc and make sure it is checked after the upgrade.
Cheers!

---

### Post by voron on 2013-02-15
There used to be a checkbox for MythVideo in Control Centre when it was a plugin (like [here]("http://www.kabatology.com/wp-content/uploads/2010/04/myth-plugins.png")).

But now it is removed from MCC. See attachment for my options

---

### Post by nickrout on 2013-02-15
There is no plugin now.

Media Library Menu
Watch Videos

---

### Post by voron on 2013-02-15
> **nickrout said:**
> There is no plugin now.

Media Library Menu
Watch Videos

Actually, I've mentioned that I know it's not a plugin anymore. And I don't have 'Watch Videos' anymore.

---

### Post by voron on 2013-02-15
Thanks nickrout! 

I put two things you've said together and found my answer. During upgrade default menu was not updated (it's at ~/.mythtv/themes/defaultmenu). So in my library.xml action for Watch Videos was still pointing to the PLUGIN, which is not available anymore.

Downloaded latest files for defaultmenu from github and got my videos back.

---

### Post by tgm4883 on 2013-02-16
> **voron said:**
> Thanks nickrout! 

I put two things you've said together and found my answer. During upgrade default menu was not updated (it's at ~/.mythtv/themes/defaultmenu). So in my library.xml action for Watch Videos was still pointing to the PLUGIN, which is not available anymore.

Downloaded latest files for defaultmenu from github and got my videos back.

What the heck is '~/.mythtv/themes/defaultmenu'? Sounds like you were overriding the theme previously. Anything for the Mythbuntu theme should be in ~/.mythtv/themes/Mythbuntu/

---

