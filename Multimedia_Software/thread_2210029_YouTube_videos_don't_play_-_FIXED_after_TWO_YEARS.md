---
title: "YouTube videos don't play - FIXED after TWO YEARS"
date: 2014-03-08
forum: Multimedia Software
---

### Post by rebeltaz on 2014-03-08
Two years ago I asked for help with a problem I was having on my grilfriend's computer ([http://ubuntuforums.org/showthread.php?t=1966088](http://ubuntuforums.org/showthread.php?t=1966088)). After upgrading to the latest Ubuntu (at the time) she was no longer able to play YouTube videos or anything else having to do with Flash. Someone did suggest installing an older version of flash using "Flash Plugin Installer" instead of "Adobe Flash Plugin". For some reason, that didn't work. 

Fast forward two years and one angry girlfriend and I FINALLY found the issue. The guy suggesting the older version was right, but his fix didn't work. This one - [http://www.linuxquestions.org/questions/linuxquestions-org-member-success-stories-23/getting-flash-plug-in-to-work-with-older-cpus-4175420481/](http://www.linuxquestions.org/questions/linuxquestions-org-member-success-stories-23/getting-flash-plug-in-to-work-with-older-cpus-4175420481/) - did and provides and explanation as to why - my favorite question. 

I am posting this here some someone else doesn't end up on a two year search for answers as I did.

---

### Post by monkeybrain20122 on 2014-03-09
Unmaintained flash is a security risk. I would not use it even if it 'works'. Now you can watch Youtube without flash in many ways (through Viewtube, a greasemonkey script that renders it in mplayer, or html5,--most are in html5 anyway and there is a FF addon that allows you to watch all of Youtube in html5, through vlc, and there are at least two standalone Youtube viewers: smtube and minitube) Therefore, there is no need to install flash in the first place if Youtube is the only thing you worry about. Other popular sites such as vimeo, soundclound also have html5 options now they work out of the box in Chrome (in FF you need to install gstreamer-ffmeg or gstreamer-libav because of h264 for video sites, I think that come with restricted-extras)

P.S. Congrads that you are still with the same girl friend after two years. But she probably needs  a new computer:)

---

