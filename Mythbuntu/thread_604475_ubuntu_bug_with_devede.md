---
title: "ubuntu bug with devede"
date: 2007-11-06
forum: Mythbuntu
---

### Post by stevetv on 2007-11-06
i like devede for transcoding avi files to dvd playable dvds.  

it installs fine through apt.

the authors site says that there is bad sound with ubuntu due to the mplayer/memcoder versions shipped with 7.10.
[http://www.rastersoft.com/programas/devede.html](http://www.rastersoft.com/programas/devede.html)

it also suggests to download a devede package with "functional" versions of mplayer/memcoder.  my guess is that these are older versions of mplayer/memcoder?

im frightened to do this? .. it will revert mplayer/memcoder to previous versions and i believe this would be a bad thing? (that wasnt a very well structured question.. hopefully u get my point.

will weekly builds fix this? or will i need to wait for at least 8.3?  in which case ill need to find another transcoding solution.. probably try getting mytharchive working.. 

thanks for your help :guitar:

---

### Post by linuxfrank on 2007-11-12
I had the same problem. Im using Ubuntu 7.10  deevede and iriverter to convert. I had good video but the audio was all white noise. I did the downgrade of mplayer and mencoder. All is fine now.
Linuxfrank:)

---

### Post by stevetv on 2007-11-14
thankyou.  i was concerned downgrading would break something.. but ill give it a go if it's work well for yourself.

thanks for replying.

---

### Post by Chang An on 2007-11-16
I'm using the 7.10 version of devede and mencoder and it seems to work fine with a fix.  Well the preview had no noise.  I'll write back when my dvd is done burning.  I got this from this thread.  [http://ubuntuforums.org/showthread.php?t=524006&highlight=devede+sound](http://ubuntuforums.org/showthread.php?t=524006&highlight=devede+sound)

from davidbenson

1. Launch DeVeDe as you normally would
2. Create a new Video DVD project and select your interlaced file
3. Expand the Advanced options and you should now see a row of TABS
4. Click the "Quality Options" tab
5. From the De-interlacing group, select "Linear Blend"

That did the trick for me.  No need to downgrade mencoder.

---

### Post by kelvin spratt on 2007-11-16
The downgrade works fine, its a shame once again Ubuntu has failed to address a problem the same problem was in edgy, feisty, now Gutsy,

---

### Post by Chang An on 2007-11-16
I did not have to downgrade.  Just change the settings as in the post above.

---

### Post by s3a on 2008-02-27
> **kelvin spratt said:**
> The downgrade works fine, its a shame once again Ubuntu has failed to address a problem the same problem was in edgy, feisty, now Gutsy,


That ticking a box "clever trick" didn't work for me....how do you do "the downgrade"...please, please, please help me!!

---

### Post by soluckytouselinux on 2009-01-07
Hello. having all kinds of trouble with devede and mythbuntu. I have lots of room, yet it says that I don't have a enough disk space. Googled, looked everwhere. People have the same problem, no real answers. Should I remove mythbuntu and go back to a older version of ubuntu  (8.04?) I worked fine in my older version of ubuntu 8.04. Can I even find a copy of 8.04?

Have a good day, Eh!

---

### Post by klc5555 on 2009-01-07
> **stevetv said:**
> i like devede for transcoding avi files to dvd playable dvds.  

it installs fine through apt.

the authors site says that there is bad sound with ubuntu due to the mplayer/memcoder versions shipped with 7.10.
[http://www.rastersoft.com/programas/devede.html](http://www.rastersoft.com/programas/devede.html)

it also suggests to download a devede package with "functional" versions of mplayer/memcoder.  my guess is that these are older versions of mplayer/memcoder?

im frightened to do this? .. it will revert mplayer/memcoder to previous versions and i believe this would be a bad thing? (that wasnt a very well structured question.. hopefully u get my point.

will weekly builds fix this? or will i need to wait for at least 8.3?  in which case ill need to find another transcoding solution.. probably try getting mytharchive working.. 

thanks for your help :guitar:

The version of mencoder that you need (release candidate 2) is available as an upgrade as a gutsy backport. Upgrade to this version rather than downgrading anything. (Also upgrade mplayer to the same level).

If you're already running mythtv 0.21 and all the backports on 7.10, you're good to go. Don't change anything! (Unless by chance you've never installed mencoder) I use the rc2 version of mencoder/mplayer almost daily on Mythbuntu 7.10, and they work fine!

BTW, if you've installed the Gutsy package for DeVeDe itself, you may not be satisfied with it, as it is an ancient version, 2.something that doesn't do menus. You will be much happier with the current version 3.11. I found that while the .deb file for this would not install on Mythbuntu 7.10, downloading the tarball from the author's website, extracting it, and using his shell script to do the installation worked like a charm.

Also BTW, as an unusual quirk, I've found that I needed to kill and restart X (ctrl-alt-bckspace) immediately before and immediately after using DeVeDe, as otherwise mencoder/mplayer get a bit confused and render scrambled green screen until this is done. This of course doesn't affect recordings or anything running on the backend. 

Cheers! :)

---

### Post by sideburns on 2009-01-07
> **klc5555 said:**
> 
Also BTW, as an unusual quirk, I've found that I needed to kill and restart X (ctrl-alt-bckspace) immediately before and immediately after using DeVeDe, as otherwise mencoder/mplayer get a bit confused and render scrambled green screen until this is done. This of course doesn't affect recordings or anything running on the backend. 

Cheers! :)

Thanks for the warning.  I've been trying to get it installed on my sister's Ubuntu box and running into dependency issues.  I keep getting complaints from apt-get that it needs more recent versions of some of the libraries than are available.  Now that I know this, I shan't bother because we can always use the copy on my Fedora 9 box that doesn't mess up my video.  Of course, it might be that you have a driver issue; if so, that's different.

---

