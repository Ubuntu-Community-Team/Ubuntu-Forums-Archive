---
title: "ipod &amp; rhythmbox"
date: 2006-10-17
forum: Multimedia &amp; Video
---

### Post by McHenry on 2006-10-17
I am running Dapper and have plugged in my ipod video to my laptop via the usb cable supplied and it works !!.

I can see it's icon on the desktop
I can see it's icon in rhythmbox
I can play music ffrom the ipod in rhythmbox
I can browse the ipod and see it's folders etc containing my photos etc

What I cannot do is the following:
I cannot work out how to move music from my laptop to my ipod, I am ripping CDs using juice and saving the files as ogg however in rhythmnbox I drag and drop files onto my ipod. I am using rhythmbox 9.3.1, I know newer versions are available elsewhere but I understand this version should allow me to write to my ipod.

I have read the following guide which interestingly makes no mention of rhythmbox:
[https://help.ubuntu.com/community/IPodHowto](https://help.ubuntu.com/community/IPodHowto)

Is this document the difinitive guide and I should ditch rhythmbox and use banshee or similar or is there another way using rhythmbox ?

Thanks

---

### Post by chajuram on 2006-10-17
Not really answering your question but I use amarok and it works great.

---

### Post by smoothridersean on 2006-10-18
The deal is that only very recent versions of Rhythmbox support adding files to an iPod.  Even those (0.9.6 is the latest I've used) won't let you drag songs into an iPod playlist - only onto the ipod icon.  This is just "in my experience" etc, etc, but as I recall the version of Rhythmbox in Dapper doesn't support any kind of adding-to-ipod.

So, it's coming.  Meanwhile, Amarok works, as does GTKpod.  Banshee now has some degree of ipod support now, too.

---

### Post by gdi2k on 2006-12-01
Edgy's version of Rhythmbox supports writing to iPods.

However, iPods don't support the ogg format. You'll need to rip your CDs in MP3 format to listen to them on your iPod.

To do that, you'll need to add mp3 support to gstreamer. See [here]("https://help.ubuntu.com/community/CDRipping") for more info.

---

### Post by wrycatcher on 2006-12-15
> **gdi2k said:**
> Edgy's version of Rhythmbox supports writing to iPods.

However, iPods don't support the ogg format. You'll need to rip your CDs in MP3 format to listen to them on your iPod.

To do that, you'll need to add mp3 support to gstreamer. See [here]("https://help.ubuntu.com/community/CDRipping") for more info.

99% of my digital music files are MP3 (thanks to Windows/IPOD really).  In the interest of supporting open formats, I was really thinking of **converting** all my music files to Ogg Vorbis format.  2 questions:

[LIST=1]
[*]Will this result in noticable degradation in audio quality?  I *could* re-rip/record from the original media (tape, vinyl, CD) to Ogg format, but it would be painfully slow, especially for the the analog sources (tape and vinyl).
[*]Does _any_ music library application (Amarok, Banshees, Rhythmbox, etc) have the ability to convert from Ogg to MP3 *on the fly* when moving music files from the music library to the IPOD device?  Or would this be prohibitively slow?
[/LIST]

I do want to move to Ogg format but I'd like to better understand what I'm getting myself into.  :-k

---

### Post by flotsaminthecosmicsea on 2006-12-17
How do I install 0.9.6 if I have Dapper? I know there are ways because I am running 0.9.6 right now. But I must have done it incorrectly somehow, b/c when I plug my iPod in, Rhythmbox shuts down. Any ideas for a noob?

---

### Post by Neffscape on 2006-12-25
How is it possible to enable ipod writing in Rhythmbox 0.9.6 and edgy? I still cannot copy songs and playlists from the PC to the iPod! On the contrary Listen, Amarok and GTKpod have a good support of iPods in general.

Why is Rhythmbox still so bad in iPod management? It's the player that I overall prefere, but I need it to work with my iPod!

---

### Post by gdi2k on 2006-12-25
iPod support in Rhythmbox is handled like any other Playlist. Once you connect your iPod, it appears in the list on the left. Then you can just drag tracks onto it, and they're written. 

That's about it - I haven't fiddled with Playlists much, but I'm sure it works similarly.

---

### Post by wrycatcher on 2006-12-31
My findings:

Converting an MP3 to an Ogg format using the Gnome Converter application yields an inferior audio file.   So, I'm re-ripping/re-recording anything for which I have a master source (i.e. vinyl, tape, CD).  All else will get converted as best as possible, and delete the MP3 equivalents.  For the rest (only mp3 or m4p), I will preserve the original files while trying to create the best .ogg files I can.

---

### Post by wickstopher on 2007-01-25
I have been attempting to get my iPod to work through various programs in Edgy.  I am using a first generation 2gb iPod Nano.  I am a new linux convert, so bear with me.

In Rhythmbox, it recognizes my iPod, allows me to browse songs on my iPod, successfully delete songs off of my iPod, and even play songs off of my iPod.  It does not, however, allow me to add new songs to my iPod.  Instead, I get an error message saying that there is no space left on the resource:

[IMG]http://www.christopherwicks.com/bucket/Screenshot-rhythmbox.png[/IMG]

this is very frustrating, because it is so close!  And as far as I can tell, Rhythmbox succesfully deleted song files from my iPod, which means there has to be space available!

I have also tried with Amarok, to no avail.  I just can't seem to figure out how to "mount" my ipod, and I'm not sure if I entirely understand what that means.  If there is a tutorial/explanation that somebody out there could point me to, much appreciation would be due.

Thanks!

---

### Post by wrycatcher on 2007-01-29
Aha!!!  I have seen this!   It may have to do with files in a hidden "trash" folder on your iPod.   Browse your iPod in a file window and select the option to "view hidden files".   I had issues with space and found a hidden *.trash* folder.   My deleted files were sitting in there...I had to delete this directory and then I saw my disk usage reduced significantly and could transfer more files to my iPod.

Also, make sure you don't have weird characters like ":" or "?" in your filenames because the iPod file system will choke when trying to copy the file from your Linux partition to the "windows" formatted (NTFS or FAT) device.

---

### Post by hotani on 2007-02-07
Rhythmbox allows you to work with playlists on the iPod, delete songs from them, add songs and rearrange them. This is fantastic. 

Then when you remove the iPod, you will see that no changes were made. This could cause a violent eruption of distress, followed by a spewing of obscenities directly proportional to the time spent carefully arranging the new playlists. 

GTKpod works, the only difference is that the obscenities start much, much sooner.

---

### Post by resist- on 2007-02-09
> **hotani said:**
> Rhythmbox allows you to work with playlists on the iPod, delete songs from them, add songs and rearrange them. This is fantastic. 

Then when you remove the iPod, you will see that no changes were made. This could cause a violent eruption of distress, followed by a spewing of obscenities directly proportional to the time spent carefully arranging the new playlists. 

GTKpod works, the only difference is that the obscenities start much, much sooner.

I had the same surprise today... Any idea of way to work this around ? Any idea if that's going to be fixed in the new version ?

---

### Post by hotani on 2007-02-09
I'm going to try it on Feisty tomorrow and see what happens, maybe they fixed it. My test mule is at work.

---

### Post by hotani on 2007-02-09
And..... nope! Same thing. The iPod shows up in rhythmbox, I can manipulate the tracks all I want in the playlists but the changes do not stick. I cannot make new playlists, nor can I delete current ones. 

I guess we're stuck with GTKpod for a while. :(

---

### Post by gdi2k on 2007-02-09
Great pitty. Does anyone know if Banshee is any better these days? I think it's installable with Automatix...

---

### Post by hotani on 2007-02-09
Just tried that too. No luck. It sees the iPod but no playlists.

---

### Post by StOnE LiBeRaTiOn on 2007-02-19
So, which music player at the moment has the best ipod support

---

### Post by agiamba on 2007-02-19
i use amarok and i've had no problems whatsoever. it not only handles my iPod fine, but is a great overall program, far superior to iTunes

---

### Post by hotani on 2007-02-19
Ok, let's get this out of the way: There are Amarok people, and there are iTunes/Rhythmbox/Songbird people. Amarok may be the greatest program since the window for you, but it doesn't add anything to the current "ipod and **rhythmbox**" discussion. 

Oh, and I hate Amarok. BTW, does it do playlists on the iPod?

---

### Post by hotani on 2007-02-19
> **StOnE LiBeRaTiOn said:**
> So, which music player at the moment has the best ipod support
So far, it looks like none of the music players will do playlists. GTKpod "works" but is an unintuitive pain to use. 

I think several of the music players will work for putting music on your iPod if that is all you want to do. Since I use mine in the car with a connector that links up to my factory stereo, and maps the 6 buttons to playlists, I *really* need to have good playlist access.

---

### Post by Joe_Ipsen on 2008-01-30
[INDENT] Re: ipod & rhythmbox
Aha!!! I have seen this! It may have to do with files in a hidden "trash" folder on your iPod. Browse your iPod in a file window and select the option to "view hidden files". I had issues with space and found a hidden .trash folder. My deleted files were sitting in there...I had to delete this directory and then I saw my disk usage reduced significantly and could transfer more files to my iPod.

Also, make sure you don't have weird characters like ":" or "?" in your filenames because the iPod file system will choke when trying to copy the file from your Linux partition to the "windows" formatted (NTFS or FAT) device.[/INDENT]

Thanks for the tip, but I don't seem to have a .trash folder.  I was sure to show all of the Hidden Files.

Anyone have any other suggestions?

---

### Post by coonj on 2008-02-11
In regards to the **No space left on resource** error and the **.trash** folder

The .trash folder appears when you delete files from Nautilus.

When you use the **Move to Trash** command in RhythmBox, it will not actually delete anything until you **Eject**. 
If an error occurs when you eject, the file may still be on your iPod, but not in the database file that stores file information; this means it will look like you have space as far as RhythmBox is concerned because it reads the db file, but actually you don't have that much space because files were not deleted properly.

This will cause the **No space left of resource** error.

So now you have files on there that you don't know what folder they are in, or what they are even called if iTunes put them there (like XYGW.mp3).
I figured out a way to find them based on file-access history:

Note: this may not be 100% effective in finding the "stuck" MP3s, but it did work for me.

In the Music folder on your iPod: /iPod_Control/Music
There is a list of directories containing all your songs.

You want to open each one, and sort by **Date Accessed**
(If this is not a column header, then you can toggle it on in Edit > Preferences > List Columns)

The ones you deleted in RhythmBox will be last accessed on the day you deleted them, and the time will be 0:00:00. Go through each directory in /Music and delete those files.

No go back to the root directory on the iPod, make sure hidden files are shown (CTRL+H) and delete the .trash folder. If it isn't there, press F5 to refresh.

Eject and remount your iPod, and try transferring files. You should have some space now...

good luck!

---

### Post by lunanueva on 2008-02-24
still can't find hidden .trash folder.

---

### Post by dingclancy on 2008-02-25
You can try Yamipod. So far this is the best ipod manager I have used. Light too...

[http://www.yamipod.com/main/modules/home/](http://www.yamipod.com/main/modules/home/)

---

### Post by neurophyre on 2008-03-03
I've filed a bug report.  Please see [http://bugzilla.gnome.org/show_bug.cgi?id=520044](http://bugzilla.gnome.org/show_bug.cgi?id=520044) 

As it stands now, a full iPod affected by this bug is currently read-only with Rhythmbox.

---

### Post by neurophyre on 2008-03-03
> **coonj said:**
> 
Note: this may not be 100% effective in finding the "stuck" MP3s, but it did work for me.


You're right, it revealed almost none of them on my nano.  My iPod is now pretty much read only because of this bug, this workaround doesn't work, at least not for files that were transferred on from something other than Rhythmbox.  Not to mention it's a giant pain.

Not trying to be a jerk, just sayin'.

---

### Post by noland on 2008-06-08
june 2008 still no support for playlists... that is kinda sad... i think ill have to run a QEMU winxp to use itunes... cuz it would be great to have support for playlists.... (30Go ipod video)

---

