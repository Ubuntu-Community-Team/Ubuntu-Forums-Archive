---
title: "MythTV Settings - Cannot change OSD theme"
date: 2009-03-24
forum: Multimedia Software
---

### Post by zeiaar on 2009-03-24
How can I change the OSD Theme in MythTV? The documentation says that there should be a menu in the frontend settings (Setup-->TV Settings-->Playback-->8th screen) but it appears to be missing in my setup... Also didn't find it in the Appearance menu where I can select the overall MythTV Theme.

I'm running Ubuntu 8.04 and MythTV is installed through the Package Manager (so version 0.21 I guess).

---

### Post by zeiaar on 2009-03-25
Well, I found the reason/solution for my problem. :)  

I did earlierly modify the menu layouts, among others tv_settings.xml, and there was no entry for "Playback OSD" which seems to be the current place for modifying the OSD settings. So, I just added corresponding entry (below) into my modified tv_settings.xml and it's working again. :)

   <button>
      <type>TV_SETTINGS_PLAYBACK_OSD</type>
      <text>Playback OSD</text>
      <text lang="SI">OSD</text>
      <text lang="HE">×ª×¦××× ×××× ××¡×¨××</text>
      <text lang="FI">Toisto OSD</text>
      <action>SETTINGS OSD</action>
   </button>

---

