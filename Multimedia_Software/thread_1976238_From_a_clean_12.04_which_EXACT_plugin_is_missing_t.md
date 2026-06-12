---
title: "From a clean 12.04 which EXACT plugin is missing to view NFL.com videos"
date: 2012-05-08
forum: Multimedia Software
---

### Post by Milamber12 on 2012-05-08
I just got a clean 12.04 installed. When I go to NFL.com to look at videos, the page will load and the video doesn't appear. The view page info is only showing one object not functioning.

http://flash.static.nfl.com/static/site/4.0/flash/video/video-detail-player.swf

Which would lead me to believe that I am missing a Flash plugin. However, it is installed with the latest version.

Therefore, which exact plugin is required after a clean 12.04 install to play these videos?

---

### Post by shantiq on 2012-05-08
fresh install requires


```
sudo apt-get install ubuntu-restricted-extras
```


see if that changes anything:KS

---

### Post by SeijiSensei on 2012-05-08
So far I cannot open that stream with Adobe Flashplugin 11.2 r202 (latest available for Ubuntu), nor with VLC, nor with mplayer.  The flash plugin brings up the file then shows the Loading logo but never loads.  VLC says it cannot find the file when I enter that URL as a network stream.  Opening the URL with smplayer gives me an ffmpeg error that the "compressed SWF format is not supported."  I get the identical error using both mplayer and mplayer2.  Looking up that error [suggested]("http://code.google.com/p/vlcj-apps/issues/detail?id=1") it had been fixed in VLC last year, but if so, it didn't work with the NFL stream.

I'm striking out here.  Anyone else?

Oh, and I have all the restricted extras installed.

Update:  I had no problem viewing this video at nfl.com  with flashplugin though: [http://www.nfl.com/videos/nfl-game-highlights](http://www.nfl.com/videos/nfl-game-highlights)

OP: If you don't have the Flash plugin installed, check the file /etc/apt/sources.list and make sure you have the "partner" repository enabled.  You should see a line in that file like this:

```
deb http://archive.canonical.com/ubuntu precise partner
```

If the line begins with a hash mark ("#"), use the command "sudo nano /etc/apt/sources.list" to open the file in the nano editor, remove the hash mark, then save the file and exit.  Now enter these commands:

```

sudo apt-get update
sudo apt-get install adobe-flashplugin

```

Try the NFL site again.

---

### Post by Milamber12 on 2012-05-23
Shantiq,

I tried your suggestion and got this message back

  	 	 	 	 	 	   Reading package lists... Done  
 Building dependency tree        
 Reading state information... Done  
 ubuntu-restricted-extras is already the newest version.  
 The following packages were automatically installed and are no longer required:  
   libxss1 screen-resolution-extra  
 Use 'apt-get autoremove' to remove them.  
 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.  
  
Still can't view NFL videos

---

### Post by Milamber12 on 2012-05-23
SenjiSensei,

Tried your suggestions

sudo apt-get update

Got 13 new updates

With
  	 	 	 	 	 	   sudo apt-get install adobe-flashplugin  
 Reading package lists... Done  
 Building dependency tree        
 Reading state information... Done  
 adobe-flashplugin is already the newest version.  
 The following packages were automatically installed and are no longer required:  
   libxss1 screen-resolution-extra  
 Use 'apt-get autoremove' to remove them.  
 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.  
  
No progress. I still need help!
Thanks SenjiSensei

---

