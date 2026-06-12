---
title: "help with mp3/mp/4"
date: 2010-03-17
forum: Multimedia Software
---

### Post by cowboy7305 on 2010-03-17
just bought one of the 32gig mp3/mp4 players of ebay ,has any one else done this stupid thing ,was just wondering if any one else has and if so having any trouble with it ,I can load songs and pics on to it .but have one heck of a time doing vids or movies ,when i load then on it says thy are there but will not play,that are to be AVI files 
any help please

---

### Post by ajgreeny on 2010-03-17
What make of player?  There is no way to suggest any help when you just call it a 32gig mp3/mp4 player.

---

### Post by LintonHanes on 2010-03-17
poor guy,, it's called a chipod

mympx.org/forum:
[http://mympx.org/forum/video-related/44972-ubuntu-encoding-help.html#post285133](http://mympx.org/forum/video-related/44972-ubuntu-encoding-help.html#post285133)

you should've got a sample .avi with it and you can $mplayer (the).avi for a half a minute to check out the video info -the audio should be mp3 so that doesn't matter so much

I got a $30 'chipod' that's even worse ( IF you want the video ) as it plays .amv format, and I cant encode to the right fps/bitrate on linux at-all, and they told me I was getting 8gb (I was stoked!/had) and it was only 2gb -hacked to show up as 8gb and then jumbling all the info when I loaded it up  with media...
-have a look ( it's the top one )  [http://chipod-videos.blogspot.com](http://chipod-videos.blogspot.com)

---

### Post by pickarooney on 2010-03-17
I got a similar device (DJIX) but have never managed to get the codec to work with avidemux or anything else. I can only convert to the right format with the supplied software and in Windows

---

### Post by LintonHanes on 2010-03-17
well maybe this'll help then:
[http://wiki.nanthrax.net/NanthraxWiki/Wiki.jsp?page=RockshipMP4PlayerAndLinux](http://wiki.nanthrax.net/NanthraxWiki/Wiki.jsp?page=RockshipMP4PlayerAndLinux)

but if all else fails you can go to mympx.org/forum 
and you'd be sorted quick, as mencoder handles .avi with ease

---

### Post by cowboy7305 on 2010-03-17
[http://cgi.ebay.com.au/32GB-2-8-LCD-TouchScreen-MP3-MP4-FM-MEDIA-PLAYER-games_W0QQitemZ250598584190QQihZ015QQcategoryZ79387QQssPageNameZWDVWQQrdZ1QQcmdZViewItem](http://cgi.ebay.com.au/32GB-2-8-LCD-TouchScreen-MP3-MP4-FM-MEDIA-PLAYER-games_W0QQitemZ250598584190QQihZ015QQcategoryZ79387QQssPageNameZWDVWQQrdZ1QQcmdZViewItem)
this is the same item that i have

---

### Post by cowboy7305 on 2010-03-17
Also lost the disk that came with it bummer

---

### Post by LintonHanes on 2010-03-22
..useful for putting your music folders + files on your player
(you may have noticed that 'ls' is not 'ls -t' therefore file numbers get jumbled)

```
[COLOR=Blue]cd MusicFoldersToMove/
find . -print0 | sort -z | xargs -0 cp --parents --target-directory=/media/disk/Moved[/COLOR]

``` [edit]
..but now you can copy 20 music folders (encoded to 96kbps for size like me?) at once > after the inevitable 'dosfsck -w -a -v'  when deleting folders 'seemed' to reduce your partition's capacity? [edit]

---

### Post by derekeverett on 2010-03-22
VLC should be able to convert your video files to .avi if thats an issue.

---

