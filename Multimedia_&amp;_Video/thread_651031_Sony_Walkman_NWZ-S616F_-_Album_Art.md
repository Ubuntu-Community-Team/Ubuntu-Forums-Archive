---
title: "Sony Walkman NWZ-S616F - Album Art"
date: 2007-12-27
forum: Multimedia &amp; Video
---

### Post by Daniel15 on 2007-12-27
Hi everyone,
 I recently bought a new MP3 player; a Sony Walkman NWZ-S616F. It's working great, the device is detected and mounted when I plug it in, and Amarok (the media player I use) can successfully transfer my MP3s onto it.

I have one question though - This particular MP3 player supports displaying album art when you choose a song. However, when I transfer songs using Amarok, the album art is not transferred. Any way to get this working properly, or will I have to rely on using Windows Media Player on another PC to transfer songs with album art?

Thanks in advance :)

---

### Post by kendoka55 on 2007-12-28
Hi Im experiancing exactly the same problem. I cant get one single Album Art to transfer to the WALKMAN. Also the ITUNES store, which I purchase tunes from sets a lock on them and I cant transfer them to my WALKMAN either. Im really begining to wish I bought the IPOD. I think I have sorted the Video now .....
So if anyone does have info please do tell..

---

### Post by linuxaz on 2007-12-28
Hello,
Interesting....I just received one of these for Christmas.  It's working great as well, but I also am having the album art issue.  I added the /music addendum in Amarok to make sure the music went into the folder that was already on the machine.  Before I did that, Amarok just created a directory in the most top level, which was not was I wanted.  Now, it puts the music in the proper location.  Perhaps this should be posted in the Amarok forums?

linuxaz

---

### Post by sub2007 on 2007-12-28
I recently got one similar (NWZ-S515 - almost exactly the same but without video). I don't use Amarok to add music, preferring to just drag and drop the files into the /music directory. Anyway I had no problem getting music on but did have problems getting the artwork on. It's a matter of editing the ID3 tags and unfortunately (as much as I hate to say it) most Linux programs, at least that I tried, can't do it very well. The thing I found worked best was to install under Wine a program called MP3Tag editor: [http://www.mp3tag.de/en/](http://www.mp3tag.de/en/) Then you can add album art to the ID3 tags and it will show up fine on your Walkman. 

To do it for a whole album, I sort the songs by album by clicking on the album button at the top and select all songs by the same album. On the panel on the left hand side, set all the tags to <keep> (select it from the drop down menu) and then right click on the album art box and set it there. You must use the .jpg file format for the art (I think). Then click the Save button.

It won't collect album art for you, so make sure you have all the album art you want to set downloaded before you start (Google Image search is best).

Hope this works for you and enjoy your new MP3 players :D.

---

### Post by mlkv on 2007-12-28
Under Linux you can quickly tag your files with EasyTAG (a really powerful tool), but when you move your files onto the device album arts won't show up, and most tags will be messed up. For example "ARTIST NAME" would become "ARTIST NAME <- loads of spaces -> X", were X is a random character.. pretty annoying because makes every string scroll across the screen.

The only solution I've come up with is to boot into Windows and do the dirty work with WMP. Not quite what I was looking for.

---

### Post by Daniel15 on 2007-12-28
>  The thing I found worked best was to install under Wine a program called MP3Tag editor: [http://www.mp3tag.de/en/](http://www.mp3tag.de/en/) Then you can add album art to the ID3 tags and it will show up fine on your Walkman.
Thanks, this worked fine for me :)

> most tags will be messed up. For example "ARTIST NAME" would become "ARTIST NAME <- loads of spaces -> X", were X is a random character.. pretty annoying because makes every string scroll across the screen.
I set most of my tags using Amarok, and they all worked fine. The album art was the only problem I was having.

---

### Post by sub2007 on 2007-12-29
You're welcome :)

> Under Linux you can quickly tag your files with EasyTAG (a really powerful tool), but when you move your files onto the device album arts won't show up, and most tags will be messed up. For example "ARTIST NAME" would become "ARTIST NAME <- loads of spaces -> X", were X is a random character.. pretty annoying because makes every string scroll across the screen.

The only solution I've come up with is to boot into Windows and do the dirty work with WMP. Not quite what I was looking for.

Yeah I tried EasyTag and got the exact same problem. MP3Tag Editor did fix it though.

Just noticed this as well:

> Also the ITUNES store, which I purchase tunes from sets a lock on them and I cant transfer them to my WALKMAN either.

Yeah unfortunately the iTunes Music Store sells you the songs in encrypted AAC format, which is confined to iPod's only. Other music stores sell the songs in protected WMA format which is recognised by Walkman (and nearly every other MP3 player). I think the only workaround is to use iTunes to burn the songs onto an audio CD and then rip them back in MP3 format (don't know about the legality of that but I've heard it does work).

---

### Post by sread on 2007-12-29
If you don't want to search out all your album art again manually, I found that the MusicBrainz Picard program (with the album art plugin) will find, download and attach the correct cover art for most songs.

However, I was wondering if anyone knows if these players support any other method of supplying cover art, because attaching a jpg to the ID3 tag of every single song doesn't seem like a very efficient use of space on the player. Thoughts?

---

### Post by Robertjm on 2007-12-29
Can't add a different resolution to this problem, but got a really strange occurance that maybe someone can answer for me.

I put a whole bunch of podcasts on my player. One of them was TWiT (this week in Tech by Leo LaPorte). The album art showed up just fine and I didn't do a single thing to make sure it was there. However, none of the other stuff I put on there had it!

A side issue, which is a nag is that when I remove the songs/podcasts from the device via Amarok it leaves the empty folders on the device. I can delete them manually through Drag/drop, but its still a pain. 

Robert

---

### Post by Robertjm on 2008-03-12
Just a quick follow-up to my last post.

When I looked at my mp3 files I noticed there were no track numbers within the ID3 tags. Additionally, that podcast didn't have the artwork within Amarok.

Next thing I did was make sure to make sure all the tracks had track numbers and that Amarok had artwork. Next time I synced that album to my Sony player it created a .alb file with the track info and the cover art made its way onto the Sony player!!

Still creating individual folders for each and every mp3 file and as far as I can tell still not manually deleting empty folders, but at least its progress!!

Robert

---

### Post by lolobu on 2008-03-19
> Under Linux you can quickly tag your files with EasyTAG (a really powerful tool), but when you move your files onto the device album arts won't show up, and most tags will be messed up. For example "ARTIST NAME" would become "ARTIST NAME <- loads of spaces -> X", were X is a random character.. pretty annoying because makes every string scroll across the screen.

I had the exact same problem with [COLOR="Red"]EasyTag[/COLOR] on my [COLOR="Red"]Sony[/COLOR]  NWZ A818 and finally got around it. What screws up the Artist name and so on is the usage of ID3v2.4 which is the default setup for EasyTag. In the tag parameters configuration, just put it to version ID3v2.3 and that will do !!
Unfortunately though, it seems that once the tag has been converted to 2.4, you can't fix it back. The only way I got around is to actually delete the tag and rewrite it with 2.3 in the configuration.
It seems that with version 2.4, the end of the string is not detected. And the first character that you get after all the spaces is the first of the album name.

---

