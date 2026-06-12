---
title: "[SOLVED] MIxed problems with nuvexport in muthbuntu"
date: 2008-08-08
forum: Mythbuntu
---

### Post by malaTG on 2008-08-08
Hi everyone,

I have a couple of questions regarding nuvexport

I use a pvr-150 card to record an analog signal in Sweden with the resolution 720x576. 

1. 4:3 recordings covers the whole TV vertically, not horizontally because I have a 16:9 TV. When I watch 16:9 recorings I have to zoom in mythtv to remove the black borders above and under the picture. How do I remove the black borders when I use nuvexport? Is it possible to "zoom" the picture so I don't get any borders in my exports?

2. I thought that I would use Xvid when I export my recordings. Is this the best choice? What are reasonable settings for resolution, bitrate, VBR etc.?

3. I have tried to run nuvexport as a user job but I get this error message in the log. Does anyone know how tyo resolve this?


> 
OSPEED was not set, defaulting to 9600 at /usr/share/nuvexport/nuv_export/shared_utils.pm line 61
Can't find a valid termcap file at /usr/share/nuvexport/nuv_export/shared_utils.pm line 61
Compilation failed in require at /usr/bin/nuvexport-xvid line 45.
BEGIN failed--compilation aborted at /usr/bin/nuvexport-xvid line 45.

Thank you in advance!

Mala

---

### Post by malaTG on 2008-08-10
bump....

---

### Post by JugeHuge on 2008-08-11
Hello.

Have you looked this thread??
**[HOWTO: Auto transcode MYTHTV recorded shows]("http://ubuntuforums.org/showthread.php?t=346778")**

---

### Post by malaTG on 2008-08-11
Yes I have and it is a bit confusing. The error I get when I run a user job is when I use this guide. The problem with black borders I found an old relevant post about but no answer

[http://www.mythtv.org/pipermail/mythtv-users/2005-October/105788.html](http://www.mythtv.org/pipermail/mythtv-users/2005-October/105788.html)

---

### Post by JugeHuge on 2008-08-12
I haven't played much on nuvexport but i had problem on one show that didn't transcoded to correct format.. 

So i forced aspect ratio to 16:9 from /etc/nuvexportrc and it coded correctly..

```

#  If nuvexport is having trouble detecting the *input* aspect ratio of your
#    recordings (MythTV used to hard-code all software-encoded files as 1:1
#    regardless of the true aspect), set this option to one of the following:
#
#   force_aspect = [ 1:1 4:3 16:9 2.21:1 ]

```

There is also crop setting on same file

```
#
#  Nuvexport has the option to crop a percentage of the border of each recording
#  in order to get rid of the unsightly edges of the tv signal.  The default 2%
#  approximates the overscan of an average TV, but you can alter this from 0 to
#  5% to fit your preferences.  Please keep in mind that this amount is removed
#  prior to making any aspect conversions like removing black bars from 4:3
#  recordings to make a 16:9 export.
#
    
crop_pct = 2

#
#  Alternatively, you can override the general crop_pct to crop a different
#  amount from specific sides of the recording.
#
#   crop_top    = 2
#   crop_right  = 2
#   crop_bottom = 2
#   crop_left   = 2

```

---

### Post by malaTG on 2008-08-12
I found this option in my nuvexportrc file. Is this the correct way to get rid of black borders above and under a 16:9 recordings that lies within a 4:3 recording as described earlier?

> #
#  You can also override the output aspect ratio.  This is useful in
#  combination with crop_top=12.5 and crop_bottom=12.5 to remove the black
#  bars from the top/bottom of recordings broadcast in fake widescreen.
#
#   out_aspect  = 16:9
#

**Edit: It was the correct way**

---

### Post by Mr. Big on 2008-09-10
So others may find it:

to the above problem (Can't find a valid termcap file at /usr/share/nuvexport/nuv_export/shared_utils.pm line 61) the solution on debian was to upgrade the ncurses-term and ncurses-bin packages. I suppose the same will help on ubuntu too.

---

### Post by db260179 on 2008-09-15
You actually need to have the two packages installed! - for some reason mythbuntu doesnt have these packages installed?

> **Mr. Big said:**
> So others may find it:

to the above problem (Can't find a valid termcap file at /usr/share/nuvexport/nuv_export/shared_utils.pm line 61) the solution on debian was to upgrade the ncurses-term and ncurses-bin packages. I suppose the same will help on ubuntu too.

---

### Post by t3chn0b0y on 2008-11-07
> **db260179 said:**
> You actually need to have the two packages installed! - for some reason mythbuntu doesnt have these packages installed?

I'm using the latest version of Ubuntu and this problem still
exists, thanks for the fix.. I was also having another problem
with accessing the config.xml not being accessed.. others have
said to fix this by doing the following..

$sudo ln -s ~/.mythtv/config.xml /root/.mythtv/config.xml
$sudo /etc/init.d/mythtv-status reload

but I have found that that didnt complete fix the problem either
I had to do it also with the user mythtv..

$sudo ln -s ~/.mythtv/config.xml /home/mythtv/.mythtv/config.xml
$sudo /etc/init.d/mythtv-status reload

and it fixed the api issue also..  :lolflag:

now to fix the shutdown issue im having since I updated to 8.10..
getting a blank screen and it just sticks..even with reboot..
leave that too yet another post..

Hope this was a bit helpful..

oh heres the link to the other issue [http://ubuntuforums.org/showthread.php?t=770188]("http://ubuntuforums.org/showthread.php?t=770188")

---

### Post by Ares Drake on 2009-01-19
I can confirm the package problem vor Vanilla Ubuntu 8.10, ncurses-term is missing by default. After manually installing it, transcoding via nuvexport-xvid works fine.


even without ncurses-term nuvexport works in sandalone mode ie called from the cosole however. only when used as auto-transcode in mythtv ncurses-term is needed.

---

