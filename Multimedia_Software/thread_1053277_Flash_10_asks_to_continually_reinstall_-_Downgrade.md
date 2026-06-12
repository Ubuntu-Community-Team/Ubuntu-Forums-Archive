---
title: "Flash 10 asks to continually reinstall - Downgrade to Flash 9"
date: 2009-01-28
forum: Multimedia Software
---

### Post by bscook on 2009-01-28
Hi all.  I've been banging my head for a week trying to get Adobe Flash to "play nice" with Firefox.  It was working fine until I upgraded to Flash 10 last week then it went wonko.  After cruisin' the forums looking for potential fixes, the best suggestion I found was to go back to Flash 9... problem is that it is no longer "officially" available.  Here's the steps and everything works for me now.  Hope this helps.

Adobe technote:
[http://kb.adobe.com/selfservice/viewContent.do?externalId=kb406791&sliceId=1]("http://kb.adobe.com/selfservice/viewContent.do?externalId=kb406791&sliceId=1")

open synaptec, remove flashplayer, etc.

open terminal
cd /home/myusername/.mozilla/plugins
rm libflashplayer.so

cd /tmp
wget [http://download.macromedia.com/pub/flashplayer/installers/current/9/install_flash_player_9.tar.gz](http://download.macromedia.com/pub/flashplayer/installers/current/9/install_flash_player_9.tar.gz)

tar -zxvf install_flash_player_9.tar.gz
cd install_flash_player_9_linux

[close Firefox]

in terminal enter:
./flashplayer-installer

[follow the instructions]

everything works again. 

good luck.

---

### Post by Gaudentius on 2009-02-03
Thank you very much! This worked great.

GD:popcorn:

---

