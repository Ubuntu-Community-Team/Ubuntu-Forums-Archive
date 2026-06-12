---
title: "Lucid Lynx and iPod touch/iPhone video sync"
date: 2010-05-12
forum: Multimedia Software
---

### Post by drillerccg on 2010-05-12
May 13, 2010: still unsloved

I have searched and searched but can't find an easy way to copy and paste videos from/to iPod touch to/from Lucid. 

The music part is now easy. 

The out of the box USB support is awesome,plug in ipod touch, start Rythmbox, drag files from library to the ipod touch. Done. Thank you. But how about movies? How do we transfer them?

TIA

---

### Post by drillerccg on 2010-05-12
I'm sure there is a program to this, a link would be appreciated. anyone else having problems?

---

### Post by Zappanale on 2010-05-12
I have had VERY bizarre experiences with iPod touches and 10.04.
Ok, first, when I installed 10.04, I plugged in my ipod, hey, it appeared in rhythmbox. I copied a few albums across, but they never appeared in the iPod. Also, all the album artwork was mixed up. Huh?!?!

Anyway, I was on my Windows partitio earlier, with my iPod plugged in. Itunes starts up and wants to sync. I cancel. Upon using my iPod later, not only had the correct album artwork appeared, but the previously unavailable albums appeared in my ipod's music!

Very confusing. Even more infuriating, as now my iPod wont even appear in rhythmbox.

---

### Post by drillerccg on 2010-05-12
Music wise I have no problems. Have not really checked the album art but the songs go both ways, computer to ipod touch and back. This is my son's ipod and I want to switch him to Ubuntu and this is our last hurdle (getting rid of iTunes). All we want now is to be able to transfer movies to the iPod touch 3.xx version. Please help. Starting to think that this issue may have not been solved yet. I hate Apple...

---

### Post by drillerccg on 2010-05-13
I'm going to post this in the newbie area also. Maybe someone there knows.

---

### Post by David Deu on 2010-05-17
I have the same problem.

---

### Post by Endless_Nameless on 2010-05-21
I have also the same problem. Some say that gtkpod with the right codecs can do the trick, but when I start gtkpod, it don't show ipod contents.

Rhythmbox is working perfectly, to import and to export music, but no video.

@Zappanale:
I just need to wait some time and it start to synchronize, and the music are instantly available in the ipod, even before disconnecting.

---

### Post by clintec on 2010-05-27
I too am very interested in this feature function.

I have been a LONG-TIME Fedora user and after utilizing 10.04 for a few weeks now, I'm highly impressed and have switched both my server and my laptop over to this release.  

The one feature I have found that I could still use is iPod Touch video syncing.

Thanks.

---

### Post by BrumleyGap on 2010-06-01
I'd love to be able to transfer video to my Touch! But all I have ever read about are attempts at running iTunes under Wine and jail-breaking the Touch. Neither really seems to work well. I think I just need to get another media player at some point. Maybe an Android device?

---

### Post by Zappanale on 2010-06-02
Well, another sync attempt, another failure. This time, even after the files are transferred, even after the sync screen on the ipod has gone, everytime I go into my music menu, the ipod crashes. LAst time it took day for it to stop.

I really like the ipod, but I may have to consider getting a creative zen. I had an older model before my iPod and it was good, and with no propriety nonsense.

---

### Post by aa4bb on 2010-06-02
I have successfully synced Music between RhythmBox and my iPod touch with the native 10.04 support. However, as yet, I haven't heard about a definite way to sync Videos.

I read about using DropBox, and I tried that. It did accomplish getting a video onto the iPod so I could watch it, but it was very slow. Don't expect instant gratification.

Then I found GoodReader from the App Store, which I got in order to read PDFs. Turns out, it is a much more capable app than I realized. You can set up folders in GoodReader just as you would on your computer. You can mount it in Nautilus over WiFi and transfer files to and from its file system just like a remote drive. Once those files are there, if they are a file type recognized by GoodReader, and including videos (!!), it will open and display / play them!!!

Here's how: Start the GoodReader app. The left-most icon in the task bar at the bottom takes you to a page "WiFi-transfer". If you have connected your iPod to your WiFi, this page will show "WiFi status: ON" and "Connection: not established". It will also show "IP address: http://192.168.1.104:8080" or something similar. 

Now in Ubuntu, start Nautilus, choose File>Connect to Server...
Under "Service Type", choose "WebDAV (HTTP)". In "Server", enter IP address  (192.168.1.104, for example) and in "Port" enter 8080, as found on the GoodReader display. Click "Connect". Another instance of Nautilus pops up, showing the GoodReader's file system. On the iPod, Connection now changes to "established".

Just drag and drop, copy and paste, or whatever, and it works like you think it should. Transfers are very fast!! 

Once you have the files copied over, unmount the iPod and tap Done on the WiFi Transfer page of GoodReader. Then navigate the file system and tap on the file to play. If it's a video, it starts playing.

This is not ideal, and there may be a limit on total size of the GoodReader directory, but it's better than nuttin'.

---

### Post by mediamind on 2010-06-07
Thanks for the tip aa4bb - I just installed GoodReaderLite and your instructions worked perfectly with Lucid and my jailbroken first gen iPhone.  

Fyi, GoodReaderLite is free and fully functional other than it will only allow 5 files to be stored at one time. The full version with unlimited file storage is available for 99 cents. 

Also fyi, I used [HandBrake]("https://edge.launchpad.net/~stebbins/+archive/handbrake-snapshots") to prepare the video for playback on my iPhone.

---

### Post by aa4bb on 2010-06-08
Glad it worked, mediamind.

I'll have to try Handbrake. Thanks for that suggestion.

---

### Post by clintec on 2010-06-08
> **aa4bb said:**
> I have successfully synced Music between RhythmBox and my iPod touch with the native 10.04 support. However, as yet, I haven't heard about a definite way to sync Videos.

I read about using DropBox, and I tried that. It did accomplish getting a video onto the iPod so I could watch it, but it was very slow. Don't expect instant gratification.

Then I found GoodReader from the App Store, which I got in order to read PDFs. Turns out, it is a much more capable app than I realized. You can set up folders in GoodReader just as you would on your computer. You can mount it in Nautilus over WiFi and transfer files to and from its file system just like a remote drive. Once those files are there, if they are a file type recognized by GoodReader, and including videos (!!), it will open and display / play them!!!

Here's how: Start the GoodReader app. The left-most icon in the task bar at the bottom takes you to a page "WiFi-transfer". If you have connected your iPod to your WiFi, this page will show "WiFi status: ON" and "Connection: not established". It will also show "IP address: http://192.168.1.104:8080" or something similar. 

Now in Ubuntu, start Nautilus, choose File>Connect to Server...
Under "Service Type", choose "WebDAV (HTTP)". In "Server", enter IP address  (192.168.1.104, for example) and in "Port" enter 8080, as found on the GoodReader display. Click "Connect". Another instance of Nautilus pops up, showing the GoodReader's file system. On the iPod, Connection now changes to "established".

Just drag and drop, copy and paste, or whatever, and it works like you think it should. Transfers are very fast!! 

Once you have the files copied over, unmount the iPod and tap Done on the WiFi Transfer page of GoodReader. Then navigate the file system and tap on the file to play. If it's a video, it starts playing.

This is not ideal, and there may be a limit on total size of the GoodReader directory, but it's better than nuttin'.

I'll see about giving this a shot when I get home tonight!

Thanks for the good find!

---

### Post by Denimwizard on 2010-06-08
I have been using rhythmbox to deal with my music on my second generation ipod touch. It worked flawlessly, just had to drag and drop the files. You can even go back and forth from ipod to rhythmbox, or rhythmbox to ipod. Fspot syncs up any saved photos on the ipod. I didn't try anything with movies yet. 

However I did run into a snag this morning when I went to use my ipod. Unfortunately I think the process of copying files actually screwed up the music library directory on my ipod. Which causes the ipod to try and update the music library and subsequently crash after a few seconds. I am going to restore it when I get home I just thought i would let everyone know about this potential hazard to your ipod touches.

---

### Post by clintec on 2010-06-10
I meant to respond to this yesterday.

This is a pretty nice little app.  I may be tempted to spend the $0.99!  ;-)

Works like a charm for videos.  I too have been utilizing HandBrake to convert my videos over.
It will simply allow you to select "iPhone & iPod Touch" output template.

I hope this resolves the issues for others, it did me.

Thanks again.

---

### Post by dmbminaret on 2010-06-12
Thanks too aa4bb,
This is a quick fix to loading a video quickly without having to boot into windows and use itunes. Maybe next year we will be able to sync video aswell as music, but until then I can live with it...I am happy with the recent developments in the linux platform to enable users to interface their ipods without itunes.

I held out as long as I could, always using plug and play/drag and drop mp3 players like iriver, but I succumbed to the app feature and pdf support. I wanted a music player with wi-fi and pdf support and no other decent product is coming to the party for the same money.

So hello apple, but hopefully goodbye itunes...soon!

---

### Post by bshosey on 2010-06-19
Install gtkpod then for the ipod or iphone mappoint

/home/"username"/.gvfs/"iphone or ipod name"

replace "username" with your home folder name.
replace "iphone or ipod name" with the device name.

it is slow but be patient. It works for me hope it works for you.

---

### Post by clintec on 2010-06-21
bshosey,
When I plug my iPod Touch in, a .gvfs mount is automatically created.  "~/.gvfs/iPod touch"

However, when I launch gtkpod, I don't see it listed there.  If I click "Load iPods", and let it sit for a relatively long period of time (10+ minutes), still nothing shows up.

Any thoughts would be appreciated.

---

### Post by bshosey on 2010-06-22
In gtkipod click on "edit" then "Repositories/iPod Directory. 
Make sure setting are set to my previous post

---

### Post by clintec on 2010-06-22
> **bshosey said:**
> In gtkipod click on "edit" then "Repositories/iPod Directory. 
Make sure setting are set to my previous post

That appears to have been the trick.
It appears that the "Browse" button didn't work, but by manually adding the /home/<user>/.gvfs/iPod touch
into the box, and selecting my version of iPod touch, it worked like a charm!

Thanks.

---

### Post by uncleray on 2010-07-06
Thanks to  aa4bb and [FakeOutdoorsman]("http://ubuntuforums.org/member.php?u=162846")
Using these two posts was able to install new version of ffmpeg, modify a vid
and transfer to Ipod Touch thru GoodReader.
Thanks a lot!

---

### Post by schenier on 2010-08-16
I have tried to upload a video with gtkpod or even directly in a directory of the mounted ipod but it keeps crashing (like it unmounts itself).

Anyone knows why?

thanks

---

