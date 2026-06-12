---
title: "Transferring songs to iphone with 10.04 rhythmbox"
date: 2010-05-02
forum: Multimedia Software
---

### Post by forbzie22 on 2010-05-02
Just freshly installed ubuntu 10.04 and having issues syncing songs to iphone.

Rhythmbox can see the iphone ok, but i cannot drag and drop any songs to the device, cannot see any sync function either ?

anyone had this issue ?

thanks

---

### Post by d-base on 2010-05-02
yep, I'm having the same problem

---

### Post by bigsmitty64 on 2010-05-02
Are you using 3g or 3gs? I have a 3g, and everything works perfectly. It could be the firmware version?,  I'm just guessing here, check through an "advanced search" in this forum, I'm sure you are not the only one with this. I'll do some searching too.

---

### Post by bigsmitty64 on 2010-05-02
just to rule out if it is or is not the firmware version got to "settings/general/about" on your phone and see what version you are running. I am running version 3.1.3 and all is well.
If yours is newer, Apple may have hosed it with a firmware update?

---

### Post by forbzie22 on 2010-05-04
Working now!

Starting to act like windows.

I restarted the machine, reconnected the iphone 3gs and all is ok.

Just make sure you drop the MP3's onto the iphone device (top level) be patient as the sync is 3 times as slow as itunes. Should show a progress bar in bottom right of rhythmbox.

---

### Post by d-base on 2010-05-04
Still no joy. I'm using a 2g iphone with 3.1.3 firmware.
I don't get a progress indicator either

---

### Post by russo.mic on 2010-05-04
Anyone getting the message: "Error while getting peer-to-peer dbus connection: The name :1.66 was not provided by any .service files" ?

No matter what I do, restart rhythmbox, the phone, or the OS still getting it.

I Phone 3gs running 3.1.3 firmware

---

### Post by cough on 2010-05-04
This isn't at all helpful, but yes I'm getting this error.
I have firmware 3.1.3 and iPhone 3GS

---

### Post by russo.mic on 2010-05-04
I'm just glad to know i'm not the only one!  oh, Dell Insprion 1524, if that makes a difference.  

I believe it to be a bug in rhythmbox, as the iphone mounts fine, and I can browse it. That's just my thinking however, could be wrong.  Anybody to shed some light?

I'm currently trying a fresh installation on the same machine, so I'll let you guys know if that makes a difference.

Russo

---

### Post by russo.mic on 2010-05-04
Fresh installation instead of an upgrade cured my woes.  

It'd be nice to know what package got left behind that broke it.

---

### Post by oldsalt43 on 2010-05-04
Hi Guys, My issue is slightly different. I can transfer songs to the iPhone (Ver 3.1.3) OK, but now the iPhone won't play them! When I click the 'iPod' button on the iPhone I get the 'More' screen, but it just freezes. 
I used Rhythembox 0.12.8 & Ubuntu 10.04
Thanks in advance :)

---

### Post by cough on 2010-05-07
Ok. It looks like its working for me now. I'm really not sure why it started working all of a sudden. I didn't do anything. The most I did was rest my computer. Oh well, I'm happy but sadly can't provide any help to those still suffering this tragedy.

---

### Post by fafarafa on 2010-05-07
Error while getting peer-to-peer dbus connection: The name :1.148 was not provided by any .service files

```

lorcan@lorcan-t61p:~$  rhythmbox --debug &> rhythmbox-debug.txt
lorcan@lorcan-t61p:~$ cat rhythmbox-debug.txt 
(18:14:48) [0x1d76040] [rb_debug_init_match] rb-debug.c:213: Debugging enabled
(18:14:48) [0x1d76040] [main] main.c:176: initializing Rhythmbox 0.12.8
(18:14:48) [0x1d76040] [rb_threads_init] rb-util.c:482: GMutex isn't recursive
(18:14:48) [0x1d76040] [main] main.c:184: going to create DBus object
(18:14:48) [0x1d76040] [main] main.c:347: THE END

```

If it helps anyone... I've reinstalled rhythmbox, did not help, I'll try restart :p

---

### Post by fafarafa on 2010-05-07
Solution...

1) Unplug you iPhone

2) Reboot

3) Start Rhythmbox

4) Plug your iPhone in

5) Enjoy...

What seamed to be an issue was starting the system/rhythmbox while the iPhone was already plugged in...

---

### Post by russo.mic on 2010-05-10
So I spoke too soon.  Now, it transfers, but the iphone just says Updating Library forever.  The only way I can get it back is by deleteing my itunes directory on the phone, then copying it back over without the new files.  (Thank god I thought to make a backup).

Anyone?

Russo

---

### Post by maf138 on 2010-05-10
Try dragging your tracks to the iPhone icon instead of the playlist.
This worked for me.
Ubuntu 10.04
iPhone 3G Version 3.1.2

---

### Post by charlie1953 on 2010-05-14
I can drag and drop Podcasts but not music. Tried all the suggestions in this thread but no luck. My music is on a USB drive which I thought was the problem but I have tried moving some songs to the Music folder on the system drive and it still does not work. No error just nothing happens.
Anyone else getting this? Anyone got any suggestions?

Ubuntu 10.04
iPhone 3G Ver 3.1.2 (not jailbroken)

---

### Post by Wintersdark on 2010-05-14
Hmmmm, lucid 10.4 with no extra iphone related packages, iphone 3g on 3.1.2 (jailbroken).

I can drag-and-drop songs to my iphone, but not playlists.  I can create a playlist on my phone in Rhythmbox, but I cannot add songs to it, nor can I move Rhythmbox playlists to my phone.

I have a vast music library, and I'm really a playlist junky.  Am I missing something?  Or is there another player better able to transfer playlists to my phone?

---

### Post by frncz on 2010-05-14
I also had problems, but with gtkpod instead of rhythmbox, everything seems to be OK. Worth a try. Besides, rhythmbox keeps looking for other codecs and never finds them.
when I first used the brand new Ipod nano 5th generation, I could not get it to be recognised by any program in Ubuntu. I initialised the Ipod in Windows XP, and after that initial problem, music transfers to the Ipod with gtkpod work very well.

---

### Post by Wintersdark on 2010-05-14
> **frncz said:**
> I also had problems, but with gtkpod instead of rhythmbox, everything seems to be OK. Worth a try. Besides, rhythmbox keeps looking for other codecs and never finds them.
when I first used the brand new Ipod nano 5th generation, I could not get it to be recognised by any program in Ubuntu. I initialised the Ipod in Windows XP, and after that initial problem, music transfers to the Ipod with gtkpod work very well.

Hmmm, gtkpod and GPixPod don't seem to be able to "see" my iPhone at all :(

It's mounted, but not in a traditional sense.  When plugged in, it appears in Nautilus's Places, but on mouseover it's location shows as afc://<long string of numbers>

---

### Post by yunone on 2010-05-14
i am running 9.10 and cant get my 3g with 3.1.2 FW to show in rhythmbox

does it only work in 10.04?

---

### Post by Wintersdark on 2010-05-14
Not certain.  I didn't try with 9.10; only started running ubuntu on this system with 10.4.  It shows in rhythmbox with no additional software installed, and you can copy songs to the iphone simply by dragging and dropping.  Playlists don't seem to work, though.

That is, again, with 3.1.2fw/iPhone3g and "out of the ISO" stock 10.4 ubuntu.

---

### Post by Junge on 2010-05-15
I was wondering if it is possible to sync my iPhone (no jailbreak) with rhythmbox over wlan? I don't zeem to get a clearing answer on it.

---

### Post by miguelastico on 2010-05-15
> **forbzie22 said:**
> Working now!

Starting to act like windows.

I restarted the machine, reconnected the iphone 3gs and all is ok.

Just make sure you drop the MP3's onto the iphone device (top level) be patient as the sync is 3 times as slow as itunes. Should show a progress bar in bottom right of rhythmbox.

Hmmm it happened for me as well...strange...it is slow but I am so happy that I can manage my music from ubuntu...now I just have to find some way with the apps, and I have just to wait that ubuntu one sync works as expected, and I am DONE

Oh, and about playlists, I am not able to drop the music directly on the playlist, but I can drop it on the phone icon, and then move it into the playlist

---

### Post by ofca213 on 2010-05-16
Hi,

I've got problem with syncing music with my iphone. I've got iphone 2G jailbroken with 3.0 firmware. After plugin in I can see iphone on my desktop (and browse it) and in Rhtyhmbox. I can drag and drop song in it and even i can see, in left bottom of screen, progress bar when sending. But after for example restarting Rhythmbox or unplug-in my iphone there's no change in music collection.
Any help?
I even compiled and installed newest verison of libimobiledevice from [http://www.libimobiledevice.org/](http://www.libimobiledevice.org/)
I'm running Ubuntu 10.04.

---

### Post by roalt on 2010-05-16
I also have problems with syncing music with my iPhone (firmware 3.1.3, non-jailbroken) and Rhythmbox. I can see the iPhone, it displays itself in Rhythmbox, but moving music to it doesn't do anything.

Note: iPhone is completely empty w.r.t. music. It does have some podcasts on it. Could it be that the syncing only works after at least some music is transferred first via iTunes?

---

### Post by Mr-C on 2010-05-17
> **ofca213 said:**
> But after for example restarting Rhythmbox or unplug-in my iphone there's no change in music collection.
Same problem. The progress bar indicates that the transfer is completed. I can find this files (iPhone is JB) in e.g. /mobile/Media/iTunes_Control/Music/f35/  directory. Files are still unavailable from the iPhone (except Cydia apps like AVplayer) and after next synchronization Rhythmbox doesn't see them.

Ubuntu 10.4
iPhone1,2
3.1.2

---

### Post by charlie1953 on 2010-05-19
I have just figured out why dropping podcasts on the iPhone worked but when I dropped music files nothing happened. Most of my music is in flac files. Drag an mp3 and all is good but drag a flac and absolutely nothing happens - stupid iPhone.

---

### Post by Wintersdark on 2010-05-22
> **charlie1953 said:**
> I have just figured out why dropping podcasts on the iPhone worked but when I dropped music files nothing happened. Most of my music is in flac files. Drag an mp3 and all is good but drag a flac and absolutely nothing happens - stupid iPhone.

If you're jailbroken, you can install the flac codec
with Cydia, then you should be able to play them.  Without it, I don't think the iPod app will see the flacs at all.

---

### Post by Isis242 on 2010-05-26
Ok, I had the same problem (Rhythmbox saw my Iphone but it would not transfer files) and I was able to get it working. I think there was a problem when Rhythmbox initialized the iPhone, maybe I didn't even need to initialize it. This worked for me but try at your own risk and only if you don't want to save the music on your iPhone.

Background:
Ubuntu 10.04
Rhythmbox 0.12.8
2G iPhone
iPhone OS 3.1.3 jailbroken and unlocked

The first thing I did after jailbreaking and updating Cydia was connect it to my computer. I was able to see the iPhone on my desktop. When I opened Rhythmbox it asked to initialize the iPhone. Since it was a fresh install I thought I had to do this. After that Rhythmbox saw the iPhone but nothing would happen when I dragged files over, whether they were m4a files or mp3s. When I right clicked on the icon and clicked on properties Rhythmbox would crash.

I then plugged it in to my windows machine and started up itunes. itunes didn't recognize the iphone and only gave me the option to restore it, which I didn't want to do since it is a pain to jailbreak. After some searching I found the fix for that was this:

I plugged the iPhone back into my ubuntu box and opened the file browser. I went to the iTunes folder that is inside the iTunes_control folder. I saved the iTunesDB file to my home directory as a backup then deleted the file from the iTunes folder. After that process I initialized the iPhone through iTunes.

I then plugged it back into my ubuntu machine and loaded Rhythmbox by right clicking on my phone icon and "open with" Rhythmbox (which seems to be the only way it sees the phone.) Rhythmbox asked me to initialize my phone, I ignored it and restarted Rhythmbox. Once I restarted it saw the phone and files transferred.

---

### Post by tjpoe on 2010-05-26
> **russo.mic said:**
> So I spoke too soon.  Now, it transfers, but the iphone just says Updating Library forever.  The only way I can get it back is by deleteing my itunes directory on the phone, then copying it back over without the new files.  (Thank god I thought to make a backup).

Anyone?

Russo

Same thing happened to me. I was able to get the iPhone's ipod working again by just doing a simple sync on iTunes because I didn't do a backup before I started goofing around w/ it. 

But it seems like the issue happens every time I drag new music to it. Today I put a dozen or so new songs on it, then let it sync and sit there for about 3 hrs. then I disconnected it and when I opened the ipod app, all i get is "updating library... this may take a few minutes" and it never does anything. Same happens when trying to plug it into my car or any other accessory.

---

### Post by roalt on 2010-05-27
> **roalt said:**
> I also have problems with syncing music with my iPhone (firmware 3.1.3, non-jailbroken) and Rhythmbox. I can see the iPhone, it displays itself in Rhythmbox, but moving music to it doesn't do anything.

Note: iPhone is completely empty w.r.t. music. It does have some podcasts on it. Could it be that the syncing only works after at least some music is transferred first via iTunes?

I found out that when I connected it to iTunes it also didn't recognize it. I completely cleared the iPhone as a new phone and after that I was able to connect it to Rhythmbox. So now it works!

---

### Post by no0ne on 2010-06-07
I can see mine (jailbroken with Spirit, a 3gs running fw 3.1.3) in Nautilus on Kubuntu Lucid x64, but can't see it in rhythmbox. Also my first Apple device so any tips getting it to work are appreciated.

---

### Post by firstbishop on 2010-06-07
I've ditched Windows and don't have access to Itunes any more, so I couldn't sync the ipod in Itunes. Installing [floola]("http://www.floola.com") and repairing the database in Floola did the trick for me. My Ipod shuffle works fine in rhythmbox now.

---

### Post by cancerian1in on 2010-07-24
Hi guys
pls help to create playlist for my iphone through Rhythmbox.
I can sync songs from music file to my iphone and also I can create playlist to my iphone through Rhythmbox.
Also, I  can add songs to that playlist (it is visible in Rhythmbox). Finally the problem occurs, after sync-ing I am not able to see that playlist in my phone :(

---

### Post by paulstandtkejr on 2010-08-06
im using iphone 4 with ios 4.01 ..
Rhythmbox sees phone no issue ..
when i drag song to iphone it appears to copy to iphone no issue(it shows like it copied to iphone).. 
when i unplug phone from usb  and look at music library the song is not there.. when i plug usb back in song on iphone doesnt show in rhythm box..

 it seems like it transfers it but its never there after i unplug and look in my music library  on phone.

Any help?

---

### Post by PatrickVogeli on 2010-08-07
same issue here...

---

### Post by collectperth on 2010-08-24
i am finding it  hell  slower than itunes, syncing 200 songs in itunes only takes minutes, in rythmbox running lucid took over an hour, anyone come up with a solution ?

---

### Post by MrRainMan on 2010-09-07
> **paulstandtkejr said:**
> im using iphone 4 with ios 4.01 ..
Rhythmbox sees phone no issue ..
when i drag song to iphone it appears to copy to iphone no issue(it shows like it copied to iphone).. 
when i unplug phone from usb  and look at music library the song is not there.. when i plug usb back in song on iphone doesnt show in rhythm box..

 it seems like it transfers it but its never there after i unplug and look in my music library  on phone.

Any help?


this.
edit: f*** it, this is taking far to much work then it should, im just going to install itunes with wine.

---

