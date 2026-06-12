---
title: "Problem with adding subtitles to an avi with mencoder; accents appearing as ?'s"
date: 2011-01-06
forum: Multimedia Software
---

### Post by Robert Buckmaster on 2011-01-06
Hi,

Following this guide [http://www.howtoguidehome.com/main/index.php?option=com_content&view=article&id=53:how-to-add-subtitles-to-your-video-avi-divx-xvid-files-under-ubuntu-linux&catid=16:multimedia-playersmoviescddvdseriessubtitle&Itemid=3&lang=en](http://www.howtoguidehome.com/main/index.php?option=com_content&view=article&id=53:how-to-add-subtitles-to-your-video-avi-divx-xvid-files-under-ubuntu-linux&catid=16:multimedia-playersmoviescddvdseriessubtitle&Itemid=3&lang=en), I used mencoder to add subtitles to an avi file. This was the command I entered. 

mencoder Le_fabuleux_destin_d\'Amélie_Poulain.avi -oac copy -ovc lavc -sub Le_fabuleux_destin_d\'Amélie_Poulain.srt -subfont-text-scale 3 -o Le_fabuleux_destin_d\'Amélie_Poulainsubs.avi

Unfortunately, the French accents in the output video appear as ?'s. Is there any way to fix this?

Thanks.

---

### Post by Robert Buckmaster on 2011-01-06
This French help page gives the solution [http://doc.ubuntu-fr.org/mencoder](http://doc.ubuntu-fr.org/mencoder). Adding the flag -utf8 makes sure the accents are properly rendered. In my case, the correct command line was as follows.

mencoder Le_fabuleux_destin_d\'Amélie_Poulain.avi -oac copy -ovc lavc -sub Le_fabuleux_destin_d\'Amélie_Poulain.srt -utf8 -subfont-text-scale 3 -o Le_fabuleux_destin_d\'Amélie_Poulainsubs.avi

---

### Post by wildmanne39 on 2012-12-03
Thanks for sharing and please do not post in threads that have not had activity for a year or longer, since this is an old thread it has been closed.

---

