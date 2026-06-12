---
title: "Playing Flash games offline?"
date: 2009-05-16
forum: Multimedia Software
---

### Post by snakeman21 on 2009-05-16
There was another thread about this, but it wasn't very helpful, so I'm starting my own.  I'm running Ubuntu 9.04, the Netbook Remix edition on an Acer Aspire One Netbook.  I'm looking for a program that can play flash games offline.  When I try to open one, the default program is Totem Movie Player, but it is incapable of running the game, naturally.  I have tried Xamp, Swfdec Flash Player, and Flash Offliner with Wine, with no success.  I tried just opening them with Firefox, but for some reason, they run very roughly.  Firefox plays embedded ones just fine, but if I try to run one from my hard disk, it flashes gray and makes it hard to see.  I've done google searches and scoured the repos, and just can't seem to find an appropriate application.  Any suggestions?

Thanks in advance!

---

### Post by gandaran on 2009-05-16
what type of flash files are they, .swf?
if the answer is yes then you can download a stand alone adobe flash player for linux from adobe.com.

---

### Post by hansdown on 2009-05-16
Hi snakeman21.

Try this site.

[http://www.torrentroom.com/torrent/1753078-Ubuntu-restricted-extras-for-Ubuntu-9-04-offline-installer.html](http://www.torrentroom.com/torrent/1753078-Ubuntu-restricted-extras-for-Ubuntu-9-04-offline-installer.html)

---

### Post by gandaran on 2009-05-16
> **hansdown said:**
> Hi snakeman21.

Try this site.

[http://www.torrentroom.com/torrent/1753078-Ubuntu-restricted-extras-for-Ubuntu-9-04-offline-installer.html](http://www.torrentroom.com/torrent/1753078-Ubuntu-restricted-extras-for-Ubuntu-9-04-offline-installer.html)
why would you download ubuntu-restricted-extras if you can install it from ubuntu official repositorys?
would you install it?
I wouldn't, be careful about installing anything outside the repository, you never know what it could contain?

---

### Post by snakeman21 on 2009-05-16
Gandaran:  I went to adobe.com and downloaded the standalone player... it did nothing.  When I open .swf files with it, all I get is a blank screen.  

Handsdown:  Against my better judgement, I downloaded that torrent.  The only flash player it has is the plugin, which I already have.  I need a standalone player (one that works).  Is there anything else out there?

---

### Post by gandaran on 2009-05-16
> **snakeman21 said:**
> Gandaran:  I went to adobe.com and downloaded the standalone player... it did nothing.  When I open .swf files with it, all I get is a blank screen.  

Handsdown:  Against my better judgement, I downloaded that torrent.  The only flash player it has is the plugin, which I already have.  I need a standalone player (one that works).  Is there anything else out there?
okay but are those files really .swf files? the adobe stand alone flash player will only play shockwave flash (.swf) files and nothing else not even flash video.
if your files are shockwave games (not shockwave flash which is something quite deferent) then forget it you will never get it to play in linux as adobe never made a shockwave player for linux.
maybe you can try installing a windows firefox version  in wine and install the windows shockwave player, some people did get shockwave to work with wine but I haven't been able to do it!

---

### Post by snakeman21 on 2009-05-16
Yes, they are .swf files.  And I just solved the problem.  I downloaded a standalone flash player (for .swf and .flv) that is intended for M$ Winblows, and ran it under Wine with no problem.  It installed in about 20 seconds, and in about twenty more I was playing my game.  Thanks for your suggestions, even though I figured it out, I do appreciate the help.

If anyone's interested, the player I used can be found [HERE]("http://www.standaloneflashplayer.com/")):P

---

