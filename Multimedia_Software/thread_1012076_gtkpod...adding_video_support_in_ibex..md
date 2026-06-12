---
title: "gtkpod...adding video support in ibex."
date: 2008-12-15
forum: Multimedia Software
---

### Post by fewjr on 2008-12-15
Hello All,
I am trying to get video support for my ipod using gtkpod. There is no video section in the left pane under my ipod. I read that you need gtkpod compiled from source with a certain lib...I forget which one. I also read that we generally do not build from source in ubuntu if not needed. I have gtkpod-aac 0.99.12-1ubuntu-1 installed in synaptic from the multiverse. These are the installed files synaptic lists:
```

/usr
/usr/bin
/usr/bin/gtkpod
/usr/share
/usr/share/pixmaps
/usr/share/pixmaps/gtkpod-icon-32x32.xpm
/usr/share/locale
/usr/share/locale/de
/usr/share/locale/de/LC_MESSAGES
/usr/share/locale/de/LC_MESSAGES/gtkpod.mo
/usr/share/locale/es
/usr/share/locale/es/LC_MESSAGES
/usr/share/locale/es/LC_MESSAGES/gtkpod.mo
/usr/share/locale/fr
/usr/share/locale/fr/LC_MESSAGES
/usr/share/locale/fr/LC_MESSAGES/gtkpod.mo
/usr/share/locale/he
/usr/share/locale/he/LC_MESSAGES
/usr/share/locale/he/LC_MESSAGES/gtkpod.mo
/usr/share/locale/it
/usr/share/locale/it/LC_MESSAGES
/usr/share/locale/it/LC_MESSAGES/gtkpod.mo
/usr/share/locale/ja
/usr/share/locale/ja/LC_MESSAGES
/usr/share/locale/ja/LC_MESSAGES/gtkpod.mo
/usr/share/locale/ru
/usr/share/locale/ru/LC_MESSAGES
/usr/share/locale/ru/LC_MESSAGES/gtkpod.mo
/usr/share/locale/ro
/usr/share/locale/ro/LC_MESSAGES
/usr/share/locale/ro/LC_MESSAGES/gtkpod.mo
/usr/share/locale/sv
/usr/share/locale/sv/LC_MESSAGES
/usr/share/locale/sv/LC_MESSAGES/gtkpod.mo
/usr/share/gtkpod-aac
/usr/share/gtkpod-aac/scripts
/usr/share/gtkpod-aac/scripts/convert-2m4a.sh
/usr/share/gtkpod-aac/scripts/convert-2mp3.sh
/usr/share/gtkpod-aac/scripts/gtkpod-convert-common.sh
/usr/share/gtkpod-aac/scripts/ldif2vcf.sh
/usr/share/gtkpod-aac/scripts/mab2vcard
/usr/share/gtkpod-aac/scripts/sync-abook.sh
/usr/share/gtkpod-aac/scripts/sync-evocalendar.sh
/usr/share/gtkpod-aac/scripts/sync-evolution.sh
/usr/share/gtkpod-aac/scripts/sync-kaddressbook.sh
/usr/share/gtkpod-aac/scripts/sync-knotes.sh
/usr/share/gtkpod-aac/scripts/sync-korganizer.sh
/usr/share/gtkpod-aac/scripts/sync-ldif.sh
/usr/share/gtkpod-aac/scripts/sync-notes.sh
/usr/share/gtkpod-aac/scripts/sync-palm-jppy.py
/usr/share/gtkpod-aac/scripts/sync-thunderbird-nano.sh
/usr/share/gtkpod-aac/scripts/sync-thunderbird.sh
/usr/share/gtkpod-aac/scripts/sync-tomboy.sh
/usr/share/gtkpod-aac/scripts/sync-webcalendar.sh
/usr/share/gtkpod-aac/data
/usr/share/gtkpod-aac/data/gtkpod.glade
/usr/share/gtkpod-aac/data/cdshine.png
/usr/share/gtkpod-aac/data/cdshine_main.png
/usr/share/gtkpod-aac/data/default-cover.png
/usr/share/gtkpod-aac/data/gtkpod-add-dirs.png
/usr/share/gtkpod-aac/data/gtkpod-add-files.png
/usr/share/gtkpod-aac/data/gtkpod-add-playlists.png
/usr/share/gtkpod-aac/data/gtkpod-icon-32-2.png
/usr/share/gtkpod-aac/data/gtkpod-icon-32.png
/usr/share/gtkpod-aac/data/gtkpod-icon-48.png
/usr/share/gtkpod-aac/data/gtkpod-logo.png
/usr/share/gtkpod-aac/data/gtkpod-new-playlist.png
/usr/share/gtkpod-aac/data/gtkpod-read.png
/usr/share/gtkpod-aac/data/gtkpod-read-16.png
/usr/share/gtkpod-aac/data/gtkpod-sync.png
/usr/share/gtkpod-aac/data/gphoto_album_menuitem-32.png
/usr/share/gtkpod-aac/data/gphoto_album_menuitem-48.png
/usr/share/gtkpod-aac/data/gphoto_images_menuitem-32.png
/usr/share/gtkpod-aac/data/gphoto_images_menuitem-48.png
/usr/share/gtkpod-aac/data/gphoto_tools_menuitem-32.png
/usr/share/gtkpod-aac/data/gphoto_tools_menuitem-48.png
/usr/share/gtkpod-aac/data/gphoto_playlist_icon-48.png
/usr/share/gtkpod-aac/data/tunes_playlist_icon-48.png
/usr/share/icons
/usr/share/icons/hicolor
/usr/share/icons/hicolor/32x32
/usr/share/icons/hicolor/32x32/apps
/usr/share/icons/hicolor/32x32/apps/gtkpod.png
/usr/share/icons/hicolor/48x48
/usr/share/icons/hicolor/48x48/apps
/usr/share/icons/hicolor/48x48/apps/gtkpod.png
/usr/share/icons/hicolor/64x64
/usr/share/icons/hicolor/64x64/apps
/usr/share/icons/hicolor/64x64/apps/gtkpod.png
/usr/share/applications
/usr/share/applications/gtkpod.desktop
/usr/share/doc
/usr/share/doc/gtkpod-aac
/usr/share/doc/gtkpod-aac/changelog.gz
/usr/share/doc/gtkpod-aac/README.gz
/usr/share/doc/gtkpod-aac/copyright
/usr/share/doc/gtkpod-aac/changelog.Debian.gz
/usr/share/menu
/usr/share/menu/gtkpod-aac
/usr/share/man
/usr/share/man/man1
/usr/share/man/man1/gtkpod.1.gz

```
I do not know what to do to be able to add my video files to the ipod. I have read that gtkpod works for that. Please help!

Thanks
fewjr

---

### Post by dorkdork777 on 2008-12-15
The way I do it is just import them to my library in gtkpod, then drag-and-drop to my iPod. Just using the standard one from the repos, no recompiling or anything. Vids show up under 'Movies' on the iPod. :)

EDIT: Just tried it again, I could have sworn... well I know it worked for me in Amarok :P

---

### Post by chee on 2008-12-15
> **fewjr said:**
>  I read that you need gtkpod compiled from source with a certain lib...I forget which one. 

i believe it was mp4v2 libraries as i have had the same problem.  i may try amarok.  i don't know if it makes difference but my ipod is one of the new 4gb nanos with video capability.  hopefully someone has the answer as i was just about to post this exact question.

---

### Post by fewjr on 2008-12-15
chee,
yeah, that is it. I installed it in synaptic, but I don't think thats all thats needed. The thing is I don't know what else to do. I can't find anything online. On this link, [https://help.ubuntu.com/community/iPodVideoTransferring#Transferring%20Videos%20to%20the%20iPod%20Video](https://help.ubuntu.com/community/iPodVideoTransferring#Transferring%20Videos%20to%20the%20iPod%20Video) there is a screenshot of gtkpod and it shows a video section on the left under ipod. So I know it must work. I hear it works, but I have not had any luck yet. I really want to be able to NOT use itunes. I've seen this tutorial, [http://ubuntuforums.org/showthread.php?t=114946](http://ubuntuforums.org/showthread.php?t=114946) but I'm not sure if it is up to date with Ibex.

---

### Post by chee on 2008-12-15
hopefully someone chymes in here cuz i don't either.  the only thing i can think is that maybe the version in the repos is an old one and if you got it somewhere else in its most updated form then it will be video compatible.

---

### Post by chee on 2008-12-15
i did notice in the preferences under tools,  under on-the-fly conversion there are some boxes to check that have something to do with the m4a and m4b files.  not sure if that has anything to do with it.

---

### Post by fewjr on 2008-12-15
I just noticed something under the screenshot in the wiki here:
[https://help.ubuntu.com/community/iPodVideoTransferring#Transferring%20Videos%20to%20the%20iPod%20Video](https://help.ubuntu.com/community/iPodVideoTransferring#Transferring%20Videos%20to%20the%20iPod%20Video)
It says > Notice I made a playlist just for Video. You don't have to, but it helps organize things. Just click on the Add Files button, select the .mov that you want to transfer to the iPod, and then you're all set. 

 I didn't think of that. I guess being used to iTunes I expected a video section to be there. I will post after I get off work if it does/doesn't work chee.

---

### Post by fewjr on 2008-12-16
I got it to work chee. I'll post tomorrow when I get a chance to tell you what I did. It was just a matter of clicking the right buttons.

---

### Post by chee on 2008-12-16
i can't wait.  i have been trying to get my .mp4 files to work.  i'm guessing they are different from .mov files?  i am pretty new so thanks for the help.

---

### Post by fewjr on 2008-12-16
I'm a bit new too when it comes to the movie thing. Anyway, the one movie I have ripped/converted is an mp4 file....and it worked on my Ipod last night. So what I did was I clicked on the Ipod down arrow on the left pane in gtkpod. Ipod is connected of course. I clicked "new playlist" and I named it Video. Then I highlighted the Video playlist and then clicked "add folder" or "add file" and chose the movie. Then I clicked on "save changes". You'll see it write to the Ipod. So I still don't know what the "Load Ipod" button does. I clicked it anyway but it doesn't seem to do anything. . I would think that would be what puts the files on the Ipod. Save changes did it though. Anyway to get the Ipod to eject, just right click on any of the playlist under Ipod and click eject ipod. 
So I still need to figure out whats going on here though. This worked to load the video, but the music I've been adding to my library are not transferring to the Ipod like the video did. They seem to because it shows a progress bar. I had the Ipod filled with all my music in iTunes already but the only ones that show up under my Ipod are the ones I've been adding with gtkpod and the ones I purchased from iTunes store. The music from the iTunes store were not in my music folder in Ubuntu. They reside on the ipod from before. So what I am lead to believe here is that gtkpod can only recognize the iTunes loaded music that was purchased on the iTunes store and shows the music that I have added to the Ipod from gtkpod because it is already there from before. I'm not sure why it doesn't show all the music on the Ipod in gtkpod yet. If it can show the purchaced music, why not the music I added from my cd collection in iTunes too?  If it had been an empty Ipod it may have actually looked like it added the music in gtkpod. I know this is confusing, but that is why it is taking so long to figure out. I guess it is adding it but seems like it isn't because it is already really there. You know what I'm trying to say? Got to go to work. I'll check back from there.

fewjr

---

### Post by razy60 on 2008-12-16
You might find that some of the problems stem from licensing. in some cases if you load an ipod with music from one source then try to use it in another pc it wont let you because it thinks your trying to pirate it.
As for video my mate tried this, best help he got was to ensure that the file containing the film is named exactly the same as the destination, i.e video to video(or whatever itunes calls it)


Raz

---

### Post by fewjr on 2008-12-17
Yeah...I figure it may be that. So how would you go about clearing out the Ipod of iTunes data. I guess I need to go to WinXP>iTunes and delete everything except the purchased music. Then go back to gtkpod and see if it actually is adding my music.

---

### Post by chee on 2008-12-17
alright i am still having the exact same problems with putting videos on my 4gig ipod nano video.  i did what i was told and it still gave me the errors.  the weird thing is i tried to put video on it at work on a winXP computer and i don't even know how to do that.  i am a noob.  is it because this is the newest version of the nano,  can i put videos on it?  i googled it and could only find things about changing the old nano so you could play video on it.  i got nothin

---

### Post by fewjr on 2008-12-17
chee,
I did read somewhere in my travels on the forum/web that the newer ipods had problems as of yet. If I see that again I will get you the link. The videos your trying to put on your ipod...are the movies you downloaded from iTunes? Also...I feel like a dummy. When I said I didn't know what the "Load Ipod" button did....well it is for actually bringing up the Ipod in the left pane of gtkpod. My Ipod showed up when the program starts...so I thought it was for putting the music and videos on the Ipod. So here is a link to a little howto for using gtkpod:
[http://www.simplehelp.net/2007/07/07/how-to-use-gtkpod-to-manage-your-ipod-in-ubuntu/](http://www.simplehelp.net/2007/07/07/how-to-use-gtkpod-to-manage-your-ipod-in-ubuntu/)

---

### Post by chee on 2008-12-17
ya i was hoping that it was just me and not that my ipod was too new.  i may try setting it up like an ipod video or some different things.  i can use it just fine for music,  but when i realized it could be used for videos i really wanted to try it.  i may have to wait i guess.  i still can't get any videos on it in itunes either.  did i mention that itunes sucks?  cuz i really do dislike it.  i tried to set up a podcast and i can get it in the itunes library but for some reason it won't go on my ipod.  i swear there should be an easier way then that crap program.

the movie i tried was a south park episode that was in mp4 format.  i haven't bought anything from itunes yet.  i doubt that i will.  if i can only use it for music then that is fine.

---

### Post by fewjr on 2008-12-17
I do not believe the 4th generation nano is supported yet by gtkpod. [http://gtkpod.wikispaces.com/Supported+iPods](http://gtkpod.wikispaces.com/Supported+iPods)
[http://en.wikipedia.org/wiki/IPod](http://en.wikipedia.org/wiki/IPod)
  If you could not get a video on it with gtkpod that makes sense. If you are having trouble using it in iTunes then I'd say you may be having problems because of your settings. [http://manuals.info.apple.com/en_US/iPod_nano_4th_gen_UserGuide.pdf](http://manuals.info.apple.com/en_US/iPod_nano_4th_gen_UserGuide.pdf)    I never had any trouble using iTunes. I am trying to switch everything away from Windows, using Ubuntu. The one thing I really hate about iTunes is that it breaks up compilation cds. For example, I have the cd "Les Paul & Friends: American Made World Played", which he plays with a host of other musicians (Billy Gibbons, Peter Frampton,Buddy Guy, Steve Miller) to name a few. Well when I rip it to iTunes it takes some of the songs and list them as the artist he plays with instead of leaving them all in one folder or album. I hate that and I have not been able to figure out what settings control that. iTunes has too many features for me. I don't need all that. I really don't need movies on it that bad either. My eyes aren't what they used to be..:)
Anyway...so you have the newest ipod nano....am I right? That is the 4th Generation nano.

---

### Post by chee on 2008-12-18
alrighty.  so i think my problem seems to be my work computer.  i went home and tried itunes on my ubuntu computer ( i have 10gb set aside for windows still) and it worked great.  so now i am seeing what is up with my work computer.  i will still use gtkpod for music but the little bit of videos i will be putting on will have to go through itunes. i am using avidemux to convert files to mp4 so i think i will be fine.  i tend to get a little frustrated with working between computer since my work computer is pretty old and slow,  and only runs windows.

BTW,(off topic)  that Les Paul CD sounds pretty good i think i will look it up and see if i can find it.  i'm  a huge SRV fan normally but i need something good to mix it up.

---

### Post by razy60 on 2008-12-18
if you are fed up with itunes try last.fm, not a bad prog.

Raz

---

### Post by fewjr on 2008-12-18
Also chee...I used a program called Poddox.
[http://www.poddox.com/](http://www.poddox.com/)
It was very minimal. I liked it alot.

---

### Post by fewjr on 2008-12-18
Stevie Ray is one of my most favorite guitarist ever. Of course I love Hendrick, Clapton, Frank Zappa, Robin Trower and many more, but I have completed my SRV collection. I can't say that about any other group.

---

