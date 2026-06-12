---
title: "Mythvideo 0.22 regressions?"
date: 2009-11-04
forum: Mythbuntu
---

### Post by NTolerance on 2009-11-04
In Mythvideo 0.21 I was able to browse a simple directory listing of video files and play them in mplayer.  mplayer support is [broken](http://ubuntuforums.org/showthread.php?t=847575) in Mythvideo 0.22.  

In Mythvideo 0.22 I am given a truncated list of files that fails to show the full filename.  This prevents me from knowing which file I am playing if several shows from the same season have a similar file name.  I use the "video list" menu.  

Also, it seems I have to manually refresh the video database before I can see newly added files.  In Mythvideo 0.21 I could exit the video menu and re-enter to see new files.

---

### Post by NTolerance on 2009-11-04
I see that there are a ton of new metadata features in Mythvideo 0.22.  That's awesome, but what if I want to just browse a directory listing and not use metadata?  Is this still possible?

Edit:  After further testing it appears that a file listing is available via the "M" key menu with the "Enable File Browse Mode" option.

The remaining issue is that the fantastic-looking new Mythbuntu theme is heavily truncating the filenames.  The widescreen Mythcenter theme doesn't have this problem.  I may need to look into how to edit the Mythbuntu theme.

Edit:  So the Mythbuntu's video-ui.xml theme file is causing this problem.  I noticed that Mythcenter doesn't have this file and likely uses the sensible default UI settings.  I simply backed up and deleted the video-ui.xml file from the Mythbuntu theme directory and now I can see my filenames.

---

### Post by Stig11 on 2009-11-04
Does your MythVideo find all the directories? Just a few of my directories actually appear.

---

### Post by NTolerance on 2009-11-04
> **Stig11 said:**
> Does your MythVideo find all the directories? Just a few of my directories actually appear.

Yes, but to be clear I am not using storage groups.

---

