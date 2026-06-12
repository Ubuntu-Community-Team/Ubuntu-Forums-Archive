---
title: "Problems Using VLC as the Player for MythTV"
date: 2010-08-24
forum: Mythbuntu
---

### Post by philter on 2010-08-24
I'm setting up a Mythbuntu box for a family member and I've run into an issue with using VLC as the default player within Mythfrontend. They have the exact same versions of everything that I have on the server at my home. However, when ever I attempt to play a file through Mythfrontend I recieve the following error:

```

[0x15ef668] main access error: no access module matched "myth"
[0x1428f68] main input error: open of `myth://Videos@127.0.0.1:6543<path to file>' failed: no access module matched "myth"

```

At which point it executes the second portion of the run command and exits VLC.

Has anyone encountered this problem before, or have an idea on how to solve it?

Edit: I'm using Mythbuntu running on top of Lucid Lynx - 10.04, I also tried using mplayer, but it also failed with a similar error.

All of the searching I've done thus far has led to discussions on people that are trying to set up a secondary frontend on a main backend. In this case I've got both the front and back ends on the same machine, hence the 127.0.0.1 in the error.

---

### Post by bcg30506 on 2010-08-24
May I ask what the advantage of using VLC instead of the default Internal player is?  Also, I wasn't aware you could "swap out" the player for watching recordings.

---

### Post by philter on 2010-08-24
It's not for watched recordings, it's for the video files I have on the server. But I think changing the default player will lead to it using the player for all playback.

There are instructions on the [MythTV site on changing over]("http://www.mythtv.org/wiki/VLC"). All you have to do is change the command in the Default Player setting.

The advantage for changing from the internal player is that I believe VLC is more reliable and gives better performance. I have it set to use the Internal player for now, but on the new server I get much choppier frame rates than if I use VLC. Additionally, I've had issues where the Internal player will randomly lock up and then error out after freezing for 5 mins saying that the frame buffer failed to load. Stuff like that becomes old very quickly.

I also enjoy the ability to map keys with the LIRC configuration to do things such as increase or decrease the audio sync for situations where the mouths in the video are a little bit off of the audio. I usually map the Channel up and down to increase or decrease the audio delay by 50 ms. This is something that I'm not away the Internal player can do, though I will confess I don't know that much about the internal player.

---

### Post by bobpaul on 2010-08-24
To clarify, he's using VLC as the player for MythVideo, the plugin used for playing avi, mpeg, rm, and other video files on the computer or accessible via NFS or CIFS mounts.

Unfortunately, Myth errors are often somewhat cryptic. I think the solution is going to be related to this part: *myth://Videos@127.0.0.1:6543<path to file>'*. Why is it trying to connect to localhost on port 6543? Is that <path to file> you removed a full path on the machine (like /var/mythtv/Videos)?

I would ensure your files exist where you think they do, then ensure that mythvideo is setup correctly to play them. Does it play videos with the internal player, or did you immediately try VLC? When you say you also tried with mplayer, do you mean you setup mplayer as an external player (like you did with VLC) or you switched back to the internal player (which I think is mplayer derived)?

---

### Post by iamlindoro on 2010-08-24
Myth errors may at time be cryptic, but that's a VLC error.  He's attempting to play back Storage Group content with an external player.  You cannot play SG-hosted content with an external player.

---

### Post by philter on 2010-08-24
The location of the value I'm talking about is Utilities/Setup->Setup->Media Settings->Video Settings->Player Settings

I'm changing the Default Player command.

Initially it is set up to use an mplayer command and I changed that to what is posted on the site I referenced previously. From there I attempted to play the video and received the error in my original post. After I was unable to solve the issue I changed the Default Player to say Internal and the files will play correctly, but with low frame rates/choppiness.

I've double checked several times now to make sure the path that the file MythTV is looking for is correct. And I can open the files and play them fine outside of mythtv with VLC and Mplayer, just not inside of the GUI.

---

### Post by philter on 2010-08-24
> **iamlindoro said:**
> Myth errors may at time be cryptic, but that's a VLC error.  He's attempting to play back Storage Group content with an external player.  You cannot play SG-hosted content with an external player.

So how can I get around that? Should I delete the storage groups in the back end, since I don't need them for anything being that I'm running things from the same machine?

---

### Post by philter on 2010-08-24
So it turns out the issue was with the Storage Groups. Even after I went into the back end configuration and removed all other Storage Groups except "Default", since that one is required to run MythTV, the front end still thought that /var/lib/mythtv/videos was myth://Videos@localhost, which is a storage group path.

What I had to do was change the video path from /var/lib/mythtv/videos to /home/user/Videos and put my files in there and they played perfectly.

Thanks for all of your help everyone.

---

### Post by SL666 on 2011-02-23
thread revival - 

I did this a different way - creating a vlc_script.sh grabbing the command line, then substituting the storage group address with the actual physical location of the files.

This only works because all my video files are in the same physical location - but i use the storage groups so i can play them on other machines (rarely).

I run the script from the default player command.

---

### Post by abmoraz on 2011-08-16
> **SL666 said:**
> thread revival - 

I did this a different way - creating a vlc_script.sh grabbing the command line, then substituting the storage group address with the actual physical location of the files.

This only works because all my video files are in the same physical location - but i use the storage groups so i can play them on other machines (rarely).

I run the script from the default player command.


Thread re-revival -

Could you please share this script?  I've been trying to do it in BASH.  I can get a script that works when called from the command line, but when I use it in Mythtv, it bombs and I can't figure out why...

Thanks.

---

### Post by SL666 on 2011-08-17
```
#! /bin/bash

temp_val="$1"

echo $temp_val >> /tmp/vlc_script.log
temp_val2=${temp_val/"myth://Videos@192.168.x.x:6543/"/"/data/videogroup/video/"}
echo $temp_val2 >> /tmp/vlc_script.log
vlc -f "$temp_val2" vlc://quit

```


These are of course specific to my machine..

and from the log you can see the val that mythtv passes in, and what the script then passes to vlc as the file name


```
myth://Videos@192.168.x.x:6543/movies/new/Howard the Duck.avi
/data/videogroup/video/movies/new/Howard the Duck.avi
```


again - this only works because all my video's are stored in one directory, not in several storage groups.

---

### Post by nickrout on 2011-08-17
Just use the internal player!

---

### Post by SL666 on 2011-08-17
> **nickrout said:**
> Just use the internal player!

While I appreciate your constructive advice :P the internal player falls short of vlc when playing HD content - it is excellent for nearly everything else.

---

### Post by TheMiz on 2011-08-17
> **nickrout said:**
> Just use the internal player!


The internal player is not that great for playing my .mp4 files or my .iso files.  I always heard this comment when I was asking for help to switch over; the internal player is better in 0.24 than it was in previous versions, but it isn't as good as VLC.

I use VLC because: 
#1 the subtitles look much better.
#2 VLC understands embedded subtitles, and the internal player requires a separate subtitle file.
#3 the volume can be increase to 200x.
#4 I think playback is generally smother.

---

### Post by abmoraz on 2011-08-17
> **nickrout said:**
> Just use the internal player!

I do use the internal player.  I'm trying to set up VLC as my alternet player for things like subtitle selection when watching foreign imports (it handles it much better than the internal), for things like simulcasting on Justin.tv (which VLC can do and the internal player can not).

When I'm stuck at work and want to watch a show on break, I currently can VNC to my mythbox at home and play a show, but it is VERY choppy and the run sound over the VNC connection is horrible.  I can, however, using VLC, broadcast the video to my JTV account, close the VNC session and watch it at reduced quality, but not choppy or fuzzy sound.

So yeah, the internal player is nice and I use it for my default, there are reasons to have it work with other players.

---

### Post by abmoraz on 2011-08-17
> **SL666 said:**
> ```
#! /bin/bash

temp_val="$1"

echo $temp_val >> /tmp/vlc_script.log
temp_val2=${temp_val/"myth://Videos@192.168.x.x:6543/"/"/data/videogroup/video/"}
echo $temp_val2 >> /tmp/vlc_script.log
vlc -f "$temp_val2" vlc://quit

```
These are of course specific to my machine..

and from the log you can see the val that mythtv passes in, and what the script then passes to vlc as the file name


```
myth://Videos@192.168.x.x:6543/movies/new/Howard the Duck.avi
/data/videogroup/video/movies/new/Howard the Duck.avi
```
again - this only works because all my video's are stored in one directory, not in several storage groups.


Ok, I was using sed to do a replace on the fly.  Removing the "myth://Videos@127.0.0.1:6543/" and replacing it with "/myth/video/"

It worked when I ran the script directly, but not when I called it via MythTV.  I will try your method when I get home toinight

---

### Post by alec.leamas on 2011-10-16
There are many ways of doing this, here's another. The first three lines are just for debugging and can be removed. Same limitations, all videos in the fixed path VIDEODIR

#!/bin/bash

echo "Args: $@" >/tmp/myth-vlc.log
exec >> /tmp/myth-vlc.log 2>&1
set -x

VIDEODIR="/mnt/myth/Videos"

file=$( basename "$1" )
vlc -f "$VIDEODIR/$file" vlc://quit

---

### Post by nickrout on 2011-10-16
> **alec.leamas said:**
> There are many ways of doing this, here's another. The first three lines are just for debugging and can be removed. Same limitations, all videos in the fixed path VIDEODIR

#!/bin/bash

echo "Args: $@" >/tmp/myth-vlc.log
exec >> /tmp/myth-vlc.log 2>&1
set -x

VIDEODIR="/mnt/myth/Videos"

file=$( basename "$1" )
vlc -f "$VIDEODIR/$file" vlc://quit

That's fine as long as you only have one resting place for your videos. The whol idea of storage groups is that you can use a whole lot of directories.

---

