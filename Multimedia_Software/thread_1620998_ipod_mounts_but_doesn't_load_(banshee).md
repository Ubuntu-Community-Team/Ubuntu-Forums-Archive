---
title: "ipod mounts but doesn't load (banshee)"
date: 2010-11-13
forum: Multimedia Software
---

### Post by novus721 on 2010-11-13
(New thread due to significant change in info)

5th gen iPod is recognized, but will not load files into banshee. It is the latest version of banshee. 

My ipod (named SON2) shows up in the menu, but when selected it hangs on "Loading SON2" and showing that it's busy...but this goes on without end, no files ever get loaded. Also, banshee doesn't recognize any music or video on the ipod, only "other". 

Steps taken so far:
- A complete removal and reinstallation of banshee has had no effect.
- Installed latest version of podsleuth, no effect
- Previous had "automount" in nautilus preferences unchecked, rechecked - no effect

Possible signs of danger:
[Running Banshee from Terminal output (CLICK HERE FOR NOPASTE OUTPUT)]("http://nopaste.voric.com/paste.php?f=9jqrel")
- skipping my song errors, at the bottom 4 warnings occur, followed by a number of failures which I don't understand

---

### Post by novus721 on 2010-11-13
As a side note, this is the warning that caught my attention the most > [Warn  16:10:04.748] iPod database could be loaded, creating a new one - GLib.GException: Not a Play Counts file: '/media/SON2/iPod_Control/iTunes/Play Counts' (missing mhdp header). (in `libgpod-sharp')
  at GPod.ITDB.itdb_parse_wrapped (System.String mountpoint) [0x00000] 
  at GPod.ITDB..ctor (System.String mountpoint) [0x00000] 
  at Banshee.Dap.AppleDevice.AppleDeviceSource.LoadFromDevice (Boolean refresh) [0x00000] 

Why is it creating a new one if it can load it?

---

### Post by itlarson on 2010-11-13
I have a similar problem.  My year old classic syncs fine with Rhythmbox, but with Banshee, it shows the music as "other".

---

### Post by itlarson on 2010-11-13
Update:  I installed 1.8 from the ppa, and now the music shows up as locked video.  Just as useless.

---

### Post by novus721 on 2010-11-13
Do you get similar errors whenever you run banshee through terminal?

---

### Post by evilkastel on 2010-11-13
Not really the solution you are looking for, but i have used 4 ipods on linux since 8.10, and banshee never got the job done. MOst of the time when it did sync, the ipos was full but unable to play anything and ended up needing a restore. I tried every major release of banshee and was all the same. (Until 2 months ago when i got rid of the ipods and got some Sansa players) But ok.  Debugging and bug reporting is the way to go, but in the mean time, you might want to try syncing with rhythmbox (works fine), exaile (fine too). In grim cases, gtkpod.

---

### Post by novus721 on 2010-11-25
bump!

---

### Post by novus721 on 2010-11-25
[IMG]http://i55.tinypic.com/23rsifl.jpg[/IMG]

For a screenshot of the problem

---

### Post by novus721 on 2010-11-25
> **evilkastel said:**
> Debugging and bug reporting is the way to go, but in the mean time, you might want to try syncing with rhythmbox (works fine), exaile (fine too). In grim cases, gtkpod. I guess I'll have to report the bug, but as an fyi Rythmbox recognizes but also doesn't load the ipod (and cashes when I click on my ipo's properties) and Exaile flat out doesn't see it even though its mounted. 

And I still have nightmares about gtkpod, but it may have given me a few clues...

[IMG]http://i56.tinypic.com/2py5oq1.png[/IMG]

---

### Post by kingbilly on 2010-12-08
My friend has the same problem as your screenshot with the status: Loading SON2.

It just hangs there.  Her ipod worked in 9.10 but now it won't work in banshee rhythmbox,

---

### Post by evolmachine on 2010-12-17
has anyone found a solution to this yet?  I have exactly the same problem on a 3rd Gen Nano.. 8GB of "other" data.  I upgraded Banshee to 1.8 and got 8GB of "video" data.  Still just as useless.

---

### Post by cccthestyle on 2011-01-16
same problem with 10.04 and banshee 1.9.2 using an ipod classic. songs show up in rhythmbox, stuck on loading in banshee, wont scrobble with last.fm, and get an error with gtkpod: "ipod database import failed: illegal seek to offset 0 (length 4) in file 'media/CLUTCH's IP/iPod_Control/iTunes/OTGPlaylistInfo'"

---

### Post by evolmachine on 2011-01-16
I solved my problem with the following:

```
Buy new computer loaded with Windows 7.  Install iTunes. End headache.
```

Good luck guys.

No really, I'll miss Ubuntu/Mint... like that cancerous mole I had removed last year. ;)

---

### Post by evolmachine on 2011-01-16
in all seriousness, I did solve it by running VirtualBox (nonfree) with Windows XP to get iTunes.  Its the only way to restore the ipod after it gets corrupted like that.

---

### Post by inobe on 2011-01-16
upgrading breaks function on the iphone and the ipod, i think the ipod is similar ?

[http://ubuntuforums.org/showthread.php?t=1628529](http://ubuntuforums.org/showthread.php?t=1628529)

i recommend clementine to transfer music.

---

### Post by evolmachine on 2011-01-16
I tried Banshee, gtkpod, and amarok, rhythmbox all with similar failing results.  I seriously doubt clementine or any other program can rescue an ipod once it needs to be restored other than itunes.  good luck to you tho, I'm sure someone will eventually crack it.  I gave in.

---

### Post by dondiego2 on 2011-01-16
I have a 5th generation 60 gig iPod and I could never get it to work in Banshee so I gave up.  It works great in Rhythmbox though.  If you still have access to Windows, see if iTunes will recognize it and the files.  There might be something messed up.  If you can fix it on the Windows side in iTunes it should then work in Rhythmbox.

---

### Post by cerda on 2011-01-16
My ipod nano used to work perfectly on 10.04, after i upgraded to 10.10 i couldn't transfer a song anymore. My solution has been log into Windows and use Itunes, hope 11.04 will fix this.

---

### Post by earthquakefish on 2011-04-24
This has happened before to me with banshee.  I've always found various ways of fixing it, never with Banshee though, once banshee has a problem with an ipod it never seems to recover it.  Usually, I slip back into Windows and restore the iPod using iTunes, but when doing that you lose all your music uploaded - a serious pain.  

This just happened to me again today after my ipod was considered full by banshee.  After it would not load the contents of my iPod and only showed me an unmovable block of 7.4GB of other data.  So I installed gtkpod which still was able to read the ipod and deleted various tracks, restarted banshee and once I did that Banshee was again working with the iPod.  Not an ideal fix, but you don't lose your data, and don't have to reboot into windows.

GtkPod found orphaned tracks which is likely the culprit in my case.  Banshee I expect couldn't read the database with the orphaned files *it* put on. 

The problems I read listed above sound slightly different from mine, but you may find luck in trying gtkpod before going insane and driven back to Windows.  I have also found Rhythmbox more stable with the iPod, but never loads cover art onto it.

---

