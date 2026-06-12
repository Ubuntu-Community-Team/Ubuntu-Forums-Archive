---
title: "Error when trying to install PS3 Media Server onto Ubuntu 14.04 LTS"
date: 2014-05-13
forum: Multimedia Software
---

### Post by Alan_Rimkeit on 2014-05-13
[FONT=verdana]Hello all. I cannot install the PS3 Media Server onto Ubuntu 14.04 LTS. I get the following error message.[/FONT]
[FONT=verdana]
[/FONT]
[FONT=verdana]The following packages have unmet dependencies:[/FONT]
[FONT=verdana]ps3mediaserver : Depends : ps3mediaserver-multiarch but it is not installable[/FONT]
[FONT=verdana]E: Unable to correct problems, you have held broken packages.[/FONT]
[FONT=verdana]
[/FONT]
[FONT=verdana]The commands I used are:[/FONT]
[FONT=verdana]
[/FONT]
[FONT=verdana]sudo add-apt-repository ppa:happy-neko/ps3mediaserver [/FONT]
[FONT=verdana]
[/FONT]
[FONT=verdana]sudo apt-get update [/FONT]
[FONT=verdana]
[/FONT]
[FONT=verdana]sudo apt-get install ps3mediaserver[/FONT]
[FONT=verdana]
[/FONT]
[FONT=verdana]I do not know what the "ps3mediaserver-multiarch" part is about at all. I have searched high and low but no one seems to really know. Does anyone have any ideas on a way to get PS3 Media Server install on Ubuntu 14.04 LTS? O_o Any feed back is much appreciated.[/FONT]
[FONT=verdana]
[/FONT]
[FONT=verdana]I also have installed mencoder, ffmpeg and other transcoding tools like VLC, ect. This did not assist in solving the issue.[/FONT]

---

### Post by faizanakram99 on 2014-08-14
Check the tutorial below

[http://adam.pohorecki.pl/blog/2014/05/16/how-to-install-ps3-media-server-on-ubuntu-14-dot-04-trusty-tahr/](http://adam.pohorecki.pl/blog/2014/05/16/how-to-install-ps3-media-server-on-ubuntu-14-dot-04-trusty-tahr/)

**IF it doesnt work**, follow the steps below [B](Note:Follow steps below iff above tutorial doesnt work)
[/B]

sudo add-apt-repository ppa:noobslab/apps
  sudo add-apt-repository ppa:happy-neko/ps3mediaserver
sudo apt-get update 

sudo apt-get install ps3mediaserver-multiarch
sudo apt-get install ps3mediaserver

---

