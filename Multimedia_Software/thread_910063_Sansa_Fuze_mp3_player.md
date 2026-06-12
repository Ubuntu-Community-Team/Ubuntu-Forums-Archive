---
title: "Sansa Fuze mp3 player"
date: 2008-09-04
forum: Multimedia Software
---

### Post by rcdeacon on 2008-09-04
I just bought a Sansa Fuze mp3 player. It seems to mount ok in Hardy (there is an icon placed on the desktop) but neither rythymbox or amarok will access it. I'm not sure of the problem. I did do a search of the forums and most people seemed to have problems mounting e250's etc but mine mounts and you can see all of the folders and the music you just can't manage the music with a program. Thanks for any insight.

---

### Post by ajgreeny on 2008-09-04
In rhythmbox try adding the MTP plugin, if youhave not enabled it.  That may do the trick. With my simple drag and drop mp3 player, I just use nautilus, anyway, but you may prefer to use rhythmbox.

---

### Post by rcdeacon on 2008-09-04
Thank you for the speedy reply. I'm not sure how to use Nautilus. I've actually seen this mentioned a couple of times but I assume you simply drag and drop stuff into the folders? At any rate thanks again.

---

### Post by jaygo on 2008-09-04
@deacon
could you help me out a bit? Would you tell me what size fuze you have, what firmware, and what USB mode you're using?

-size as in 2gb, 4gb
-firmware is listed under fuze settings > system settings > info > version
-usb mode is listed under fuze settings > system settings > usb mode
-also, do you add a microSD card to the fuze?

As for your question, I don't think you can use drag and drop from nautilus if you're using MTP mode, so MSC mode should do the trick if that's how you want to manage it. However, MTP mode may give you some better options with Rhythmbox.

---

### Post by rcdeacon on 2008-09-05
Jaygo, the firmware version is V01.0111A. It is a 2 gig model with a 2 gig micro sd card inserted.

---

### Post by shortylonglegs on 2008-10-17
Try adding a blank file to the root of the Fuze's drive named ".is_audio_player" (with no quotes).  This worked for me in Rhythmbox and with a Fuze 4G

---

### Post by MunkyJunky on 2008-10-19
I've just found out I've been bought one of these, so I was looking to see how well it works under linux. The official website says it runs fine under linux using MSC. From what I understand, there should be something under the settings menu that lets you change it from MTP to MSC, since (from what I've read) MTP is a Microsoft thing, and hates linux. I can't really be more specific though till I pick mine up next week. 

If this helps though, let me know! I'll be doing the same this time next week :D

---

### Post by JamesDownWell on 2008-10-20
I'm interested in this as well. I currently use an old Zen which is MTP enabled. At first this was a problem before I realised that Rhythmbox and Amarok both have MTP support by way of plugins.

To me this is ideal as I manage all of my music in RB/Amarok and can just transfer the music to the device using MTP. I can only assume the same would work for the Sansa (which I'm interested in buying myself).

Another point/question would be, with another MicroSD in the device, does this pick up separately in RB/Amarok or mount as one device?

---

### Post by shortylonglegs on 2008-10-20
Did you use the MTP plugin that came with RB?  I have never been able to get that working right, although it works fine in MSC.  I had a MicroSD card with my Fuze at one point and if I recall, it showed as two seperate drives (this was in MSC so it could be different for MTP) I don't have a MicroSD card anymore though, so I can't check to be sure.

---

### Post by JamesDownWell on 2008-10-23
Well thanks for the info shortylonglegs! I'll do some more digging on the subject.

As for the MTP in RB, I'm using Ubuntu on an EEE and I've had no problems with it, just making sure I enable the plugin! On my desktop I used my MTP device with Amaraok, again, with no real problems. I obviously can't comment on the Sansa compatibility though, as I don't own one!

---

### Post by DarKnyht on 2008-12-01
We own two Sansa now (just bought one for the wife for Christmas).  I've always used mine in MSC mode, just dragging the files to the music folder.  It was great inspiration for me to clean up my music files.  However, I tried using hers in MTP mode with the lastest firmware (1.0.1.15A) and it didn't work very well.  The files would transfer in Rhythmbox but the playback was choppy, while they worked fine on my own (transferred with MSC).  So for now (on Ubuntu 8.10), I would suggest using the filemanager (w tabs) to transfer between the local Music Folder and the Music Folder on the Sansa.

With the MicroSD card, in MSC mode it will show up as another drive.  I just created a Music folder and managed it on mine the same I have managed the main storage.  I've haven't tried it with MTP mode, as it is also used in our camera and I don't want to lose pictures.

Another item of note, is that I managed to get photos to load onto the Sansa without the media convert by saving a copy of the jpg files used in Facebook photo albums.  Apparently, Facebook converts photos into the same format that the Sansa uses.

---

### Post by ProfBib on 2009-01-25
I received a Sansa Fuze 8gb as a Christmas gift from my sister and, once I had a moment to sit down with it, I was able to get the music and photo functions working in Hardy without any trouble.
[B]
Music - Rhythmbox[/B]
First, note that you must (as mentioned earlier in this thread) create an empty file titled '.is_audio_player' in the root directory of your Fuze for it to be recognized correctly in RB.

Using rythmbox with the necessary plugin, the player shows up in RB and I am able to transfer music and associated album artwork (contained in the same folder as the album music files) without any problem whatsoever.  Using this transfer method, there is NO NEED to rename the album artwork files.  Before I had the player working with RB, I transferred a few albums by dropping and dragging from my desktop into the Fuze's MUSIC folder, but was unable to view album artwork on the Fuze unless I renamed each file from its original name (usually cover.jpg in my case) to 'folder.jpg' (without the quotes) on the Sansa.
[B]
[COLOR=Red]Update Regarding Album Artwork
[/COLOR][/B][COLOR=Red]I didn't realize that the albums I transferred using RB contained files with embedded artwork in the ID3s, so that's why it showed up automatically when others did not.  For albums with an accompanying jpg in the folder, the name change to 'folder.jpg' is still necessary.
[/COLOR][B]
Photos - F-Spot[/B]
In some other forums, there were some comments about the mediocre quality of photos on the Fuze, but I'm quite happy with mine.  Sure, the resolution is not equal to that of some other players, but I've had absolutely no trouble exporting pictures using F-Spot.  Using the export to folder function, just be sure to resize the photos to 320 pixels.  This has worked well for me, producing a better result that some of the command line strings that I ran across on other websites.

_**Wish List**_

[B]Videos
[/B]I would love to get an exported video to work on the Fuze and have found summaries of the ridiculous format specifications elsewhere on the net, but haven't yet managed to get anything to play
[B]
Automatic mounting of the player.[/B]
Before upgrading to the latest firmware, I had to use 'lususb' to mount th player.  Now, I have to rmmod and modprobe before the player will show up on the desktop.

---

