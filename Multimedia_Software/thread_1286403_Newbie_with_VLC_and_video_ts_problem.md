---
title: "Newbie with VLC and video_ts problem"
date: 2009-10-08
forum: Multimedia Software
---

### Post by djm227 on 2009-10-08
First let me say that I just installed Ubuntu yesterday.  I have been really curious about Linux for a while, but I was not aware of the fact that you could install Ubuntu on an existing windows system though wubi until yesterday.  So far I really like it...but after working on windows for so long I am probably going to have a LOT of questions over the first few weeks, and this is the first.

I started off using Ubuntu by finding how to accomplish the same tasks that I used often on Windows.  One of those tasks is mounting ISO files and playing the Video_ts folders through VLC.  I was happy to find that Ubuntu has a build in mounting feature, which I utilized to mount one of my movies.  I installed VLC and tried to play the Video_TS folder with it....but no dice.  Usually the picture flashes up really quickly, then stops.  Sometimes an error message pops up stating "VLC could not read the file" or something similar.  

My question is, how do I get VLC to play these Video_TS folders?  I know it has to be something simple that I am overlooking, but some help would be much appreciated.  

Thank you, and I am looking forward to getting involved in this community.

---

### Post by mc4man on 2009-10-09
Assuming there are no playback issues ( audio or video output settings or video drivers in general) the for a .iso don't mount it, no need to.

A .iso is just a file so several ways

Open vlc -> media -> open file and browse to it

Or right click on the .iso -> open with and pick vlc ( if not in that list proceed to 'open with other application' list

open vlc and drag and drop the .iso onto vlc 

right click on any .iso -> properties -> open with and pick vlc ( or proceed as above if not seen and pick from list

Then you'd just d. left click on a .iso and it would open in vlc ( default file ext. association.


....................................................................

For a movie in file format, (not an .iso) but a  VIDEO_TS  folder or a VIDEO_TS in a movie name folder then the best method is 

open vlc -> media -> open disc
Then next to the disc device box is a browse button. Click on and browse to the holding folder or the VIDEO_TS folder itself

( if the holding folder has spaces in name the go to the VIDEO_TS

normally a VIDEO_TS folder is considered a directory (media -> open directory), but many vlc versions can lose navigation if a VIDEO_TS is opened that way

Or again r.click on a VIDEO_TS folder -> open with vlc or drag and drop

(**don't set an association** to a VIDEO_TS folder, all folders (directories) are treated the same


( best to set your vlc to  "allow only one instance" if the version you have supports it - Tools -> preferences, should be right there on the main interface settings

---

### Post by djm227 on 2009-10-09
Thanks, that worked like a charm...I can't believe I didn't try that.  Still though...I'd like to know why it won't play the video_ts folder, since that worked so well in windows.  Definitely not a deterrent now though since I can at least play them.

Thanks for the help!

---

### Post by mc4man on 2009-10-09
If you wanted to mount an .iso (though an utter waste of time with a dvd video) you could play it back as long as you know the mount point

The mount point will be what you use as the dvd device or if you  mount it to /media/whatever than a right click on the icon on your desktop will also work

If you're using that "archive mounter" I wouldn't know, never used it, it may not be suitable for a dvd video .iso, it may be, in any event you still need to know the mount point. 

If you know the mount point then just enter it in the media -> open disc -> dvd device box

A more 'traditional' way ( and as you'll see a waste, will use 'play' as a mount point

```
sudo mkdir /media/play
```

```
sudo mount -t iso9660 [COLOR="Blue"]name[/COLOR].iso /media/play -o loop
```

or if .iso isn't in home directory

```
sudo mount -t iso9660 /path/to/[COLOR="Blue"]name[/COLOR].iso /media/play -o loop

```

then the dvd device is /media/play

Then when done 
```
sudo umount /media/play
```

---

### Post by djm227 on 2009-10-09
Yeah it must have been the archive mounter that was having trouble, because I installed Gmount and it worked fine.  Thanks for your help.

---

### Post by Zini on 2009-10-13
Ooh sorry to hijack but I'm also having a VLC problem. I updated everything a while ago, and since then VLC is being annoying! The navigation/main control window is separate to the actual video which is playing, so everytime I want to pause, skip or anything, I have to minimise the video, maximise this navigation thing and do it then. Ugh! It used to be all integrated what's going on!? Please tell me there is some simple way to get non-annoying VLC again???

Ta x

---

### Post by djm227 on 2009-10-14
> **Zini said:**
> Ooh sorry to hijack but I'm also having a VLC problem. I updated everything a while ago, and since then VLC is being annoying! The navigation/main control window is separate to the actual video which is playing, so everytime I want to pause, skip or anything, I have to minimise the video, maximise this navigation thing and do it then. Ugh! It used to be all integrated what's going on!? Please tell me there is some simple way to get non-annoying VLC again???

Ta x


I've noticed this as well, it's a pain.

---

