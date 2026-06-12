---
title: "lowest-risk way to fix one bug?"
date: 2010-08-07
forum: Mythbuntu
---

### Post by mycatsnameisbernie on 2010-08-07
I am using the standard MythTV Ubuntu package 0.23.0+fixes24158.
 
After lots of [hard work]("http://ubuntuforums.org/showpost.php?p=9635021&postcount=299"), I am really happy with my 1st ever Mythbuntu install, with one exception: bug 24274, which causes the front end to hang when the change tuner (Y) command is issued. 
 
I can see that the latest PPA is 25423, so I know this will be fixed if I take the plunge and go to autobuilds, but I get real nervous seeing all the issues listed in the autobuilds sticky thread, and by the statment in the autobuilds FAQ that says "There is no returning to regular releases after enabling trunk".
 
One thing I was considering was checking out 24274 from SVN, building it, and just putting its front-end executable in place of my 24158 version. That way I can go back the the old executable if I run into problems. Will that work? Or is there a better way? Or should I take the plunge to autobuilds?
 
Thanks for the help!

---

### Post by ian dobson on 2010-08-07
Hi,

Take the plunge with the autobuilds as long as you stay with 0.23 things are stable now. I've been running the 0.23 autobuilds for about 6weeks now and have never seen any problems.

Regards
Ian Dobson

---

### Post by nickrout on 2010-08-07
> **mycatsnameisbernie said:**
> I am using the standard MythTV Ubuntu package 0.23.0+fixes24158.
 
After lots of [hard work]("http://ubuntuforums.org/showpost.php?p=9635021&postcount=299"), I am really happy with my 1st ever Mythbuntu install, with one exception: bug 24274, which causes the front end to hang when the change tuner (Y) command is issued. 
 
I can see that the latest PPA is 25423, so I know this will be fixed if I take the plunge and go to autobuilds, but I get real nervous seeing all the issues listed in the autobuilds sticky thread, and by the statment in the autobuilds FAQ that says "There is no returning to regular releases after enabling trunk".
 
One thing I was considering was checking out 24274 from SVN, building it, and just putting its front-end executable in place of my 24158 version. That way I can go back the the old executable if I run into problems. Will that work? Or is there a better way? Or should I take the plunge to autobuilds?
 
Thanks for the help!

you are awfully confused about autobuilds. stick to the 0.23 autobuilds and you get 0.23-fixes. Go to 0.24 and you get trunk. You want the former.

It really was naughty of mythbuntu to release 10.04 with beta level mythtv builds and never update it.

---

