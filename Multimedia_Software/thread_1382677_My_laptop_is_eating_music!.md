---
title: "My laptop is eating music!"
date: 2010-01-16
forum: Multimedia Software
---

### Post by o2mcgovem on 2010-01-16
Hello all,

One of my geeky friends (he's on here, if he's reading this then hi :p) moved me over to Ubuntu. I love it, especially Banshee which is refreshingly fast compared to iTunes! However, my laptop seems to be eating up my music (deleting MP3s). I already lost music when I moved over to Ubuntu because of DRM (not your fault, I know) and to be quite honest I'm not happy that I'm losing more.

Check out this screenshot: [http://i45.tinypic.com/15ziobb.png](http://i45.tinypic.com/15ziobb.png)

The first window is of my external hard disk and the second is of my Ubuntu music folder. When I moved into Ubuntu about a month ago, I copied over everything from the external hard disk to my music folder so I have no idea where the stuff has gone. I've not noticed any of my other stuff going missing, though I rarely check my pictures or documents folder so I'd probably not notice.

Any help would be greatly appreciated :)

Thanks,
Michael

---

### Post by garvinrick4 on 2010-01-16
If it is Music that was paid for it will regurgitate it eventually, if it is Pirated music it will pass through the bowels of your CPU and be ejected, it is the Linux way.
 No just kidding Michael but I could not help myself. There will be someone who has had
same problem come along and help you, give it a little time. Weird problem. I have not
used Banshee so cannot help. Sorry but hang in there, hopefully you just copied it into
Banshee from backup source.

---

### Post by boombox1387 on 2010-01-21
Hmm, this is indeed a strange issue.  First of all, do the songs still play in Banshee, or are they completely missing?  If Banshee still plays them, then they definitely must be there somewhere.

If the files still play, you'll want to go to Edit > Preferences in Banshee and check the 'File Policies' options.  If 'Update File and Folder Names' is checked, it means that Banshee relocated the files based on the Artist/Album of the tracks.  They're still located in your Music folder somewhere, just organized in a different way for you.

If the files really are gone, that seems like a much bigger issue and we'll deal with it if we need to.

Let me know and I'll do my best to help.

---

### Post by slooksterpsv on 2010-01-21
ok this has happened to me - I copy all my music from Windows over to Ubuntu - its there, then I make a copy back over to Windows - sames sizes etc. file counts what not, but then some of its missing - none pirated, all purchased or ripped from original CDs, but they disappear.

I thought I was losing it, but if others are seeing this issue. I'm glad I'm not the only one.

---

### Post by o2mcgovem on 2010-01-22
> **boombox1387 said:**
> Hmm, this is indeed a strange issue.  First of all, do the songs still play in Banshee, or are they completely missing?  If Banshee still plays them, then they definitely must be there somewhere.

If the files still play, you'll want to go to Edit > Preferences in Banshee and check the 'File Policies' options.  If 'Update File and Folder Names' is checked, it means that Banshee relocated the files based on the Artist/Album of the tracks.  They're still located in your Music folder somewhere, just organized in a different way for you.

No, they don't play in Banshee.  They have a little grey cross to the side of them like this:
[http://i49.tinypic.com/5eekxy.jpg](http://i49.tinypic.com/5eekxy.jpg) (don't laugh at my bad taste in music :p)

I think you were partially right though, the other day I went to Tools > Rescan music library and some stuff that wasn't playing before would now play so I guess Banshee had moved the files and then it hadn't updated the library the point to the new location.

But, I know there's stuff that is still missing... I can only think of one band in particular who I copied from my dad's iTunes to mine that are not there. 

Also, when I skip past songs quickly Banshee seems to lose them. For example, in shuffle mode I skipped past the song "Rain" quickly and now it has a cross ( [http://i48.tinypic.com/2q8ybyh.png](http://i48.tinypic.com/2q8ybyh.png) ). When I try to play it plays something else in the list. I bought this song whilst using Ubuntu from Play.com ( [http://i50.tinypic.com/9rn5ad.png](http://i50.tinypic.com/9rn5ad.png) ) -- it has never been played in anything except Banshee. The file is still there in the folder but it just won't play. I have to re-add it by going to Media > Import media and then choosing the album folder. It's not in any playlists then, I have to re-add it.

> If it is Music that was paid for it will regurgitate it eventually, if it is Pirated music it will pass through the bowels of your CPU and be ejected, it is the Linux way.

Haha, most of it is paid for... maybe the copyright police are punishing me for copying that one band from my dad's iTunes. :p

Thanks for all the help thus far,
Michael

---

### Post by blazemore on 2010-01-22
Okay we're going to use the "locate" program to find your errant files.
Firstly, open a terminal and just make sure your indexes are up-to-date
```
sudo updatedb
```This may take a few seconds, depending on the speed of your aging Dell's laptop hard drive :P

Now we're going to find a Feeder file (I'm going to assume all your music has run off to the same place)
```
locate 03\ Shatter
```The backslash tells the shell to interpret the space literally, and not as a separator for arguments (like apt-get install)

With any luck, this will give you an output. This is a standard test for musical taste on all UNIX systems.

Here's mine
```
james@james-desktop ~ $ locate 03\ Shatter
/home/james/Music/Feeder/The Singles/03 Shatter.mp3

```EDIT: Make sure your external HDD isn't mounted unless you want duplicate results.
EDIT: I'd also like to point out that Ubuntu doesn't discriminate against music sources. It doesn't know if you bought a CD and then ripped it, or if your friend lent you it and you ripped it.

---

