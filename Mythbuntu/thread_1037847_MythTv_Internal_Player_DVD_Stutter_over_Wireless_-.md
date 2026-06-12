---
title: "MythTv Internal Player DVD Stutter over Wireless - cache?"
date: 2009-01-12
forum: Mythbuntu
---

### Post by Slate8 on 2009-01-12
I have been using Mythbuntu for a while on a box in my living room acting as the frontend and backend and it works a treat. I decided to extend the setup by putting another machine in my bedroom with a frontend only install. This new box connects over wi-fi and all is well, almost.

I have an NFS share on my backend which the bedroom frontend mounts to access videos and DVD files. The problem I have is that DVD rips and images stutter during playback; about once every second. This was also an issue with other video files until I changed the mplayer command to use the -cache option. With mplayer I can now play 720p content over wi-fi no problem. Is there any setting like this for MythTVs internal player so that DVDs are cached a little more allowing smooth playback over a wireless connection?

---

### Post by Slate8 on 2009-01-22
Bump - no one else get stuttering dvd playback over wirelss using the internal player? :(

---

### Post by C0pac3t1c on 2009-01-22
> **Slate8 said:**
> Bump - no one else get stuttering dvd playback over wirelss using the internal player? :(

My question for you is how do you go about setting up Mythtv or go about building your own DVR?

---

### Post by tgm4883 on 2009-01-22
> **C0pac3t1c said:**
> My question for you is how do you go about setting up Mythtv or go about building your own DVR?

Just a wild guess here, but since this is the Mythbuntu forum, I'm guessing he used Mythbuntu.

---

### Post by C0pac3t1c on 2009-01-22
> **tgm4883 said:**
> Just a wild guess here, but since this is the Mythbuntu forum, I'm guessing he used Mythbuntu.

lol...ok thank you

---

### Post by Slate8 on 2009-01-22
> **tgm4883 said:**
> Just a wild guess here, but since this is the Mythbuntu forum, I'm guessing he used Mythbuntu.

10 points to the man with the Mocha!
So no clues on the DVD over wireless issues? :D

---

### Post by tgm4883 on 2009-01-22
> **Slate8 said:**
> 10 points to the man with the Mocha!
So no clues on the DVD over wireless issues? :D

I'll see if I can find anything on that.  I don't use the internal player myself for DVD's, I use Xine, which works pretty well with mythtv.

Here is instructions for that if you want to try it.
[http://www.mythtv.org/wiki/Configuring_Xine](http://www.mythtv.org/wiki/Configuring_Xine)

---

### Post by Slate8 on 2009-01-23
> **tgm4883 said:**
> I'll see if I can find anything on that.  I don't use the internal player myself for DVD's, I use Xine, which works pretty well with mythtv.

Here is instructions for that if you want to try it.
[http://www.mythtv.org/wiki/Configuring_Xine](http://www.mythtv.org/wiki/Configuring_Xine)

Thanks will give Xine a go but have to say I'd rather be using the internal player if at all possible.

Thanks again...

---

### Post by maxim99 on 2009-01-23
I have stuttering on my wired connection. I would think it doesn't have anything to do with the medium. What you might be able to do is to extract a known stuttering ISO into a directory. Play the newly extracted DVD into an alternative player such as Mplayer. Since mythtv seems to be the only application I know of that supports playing DVDs straight in the ISO form, extracting is the only method I know to get other players to work properly.

That should help isolate the issue. For me I think it's the driver for my video card, i'm using alpha2, and will try alpha3 tonight when I get home.

---

### Post by rhpot1991 on 2009-01-24
I have this exact same problem, but I use some powerline ethernet adapters.  It is clearly not a bandwidth issue as I can stream 1080i content just fine.  After some testing I ended up switching my iso files to xine instead of internal player, solved the stuttering problem but I lose some of the internal player's functionality.  One thing I wanted to try but never got around to it was to switch from NFS to a samba share and see if I saw the same behavior.

---

### Post by Slate8 on 2009-01-24
> **rhpot1991 said:**
> I have this exact same problem, but I use some powerline ethernet adapters.  It is clearly not a bandwidth issue as I can stream 1080i content just fine.  After some testing I ended up switching my iso files to xine instead of internal player, solved the stuttering problem but I lose some of the internal player's functionality.  One thing I wanted to try but never got around to it was to switch from NFS to a samba share and see if I saw the same behavior.

Funny you should mention the share protocol. I was using samba and switched to NFS to see if it helped. The stutter didn't go away but large transfers over the network do seem marginally faster.

Have yet to try the suggestions further up in this thread, would be a shame to loose the ability to play from an iso though.

Wondering if I should report a bug to the MythTV team...

---

### Post by rhpot1991 on 2009-01-24
> **Slate8 said:**
> Funny you should mention the share protocol. I was using samba and switched to NFS to see if it helped. The stutter didn't go away but large transfers over the network do seem marginally faster.

Have yet to try the suggestions further up in this thread, would be a shame to loose the ability to play from an iso though.

Wondering if I should report a bug to the MythTV team...

DVD Menu support is actually a lot better in xine, but you lose things like dvd bookmarks and your skip buttons.  Functionality is more like playing a dvd in a dvd player (fast forward, chapter skip, pause, etc) than watching a recording.  The biggest thing I missed were the dvd bookmarks, but if you are using an iso you can just select your chapter and its close enough.

---

### Post by tgm4883 on 2009-01-24
> **Slate8 said:**
> Funny you should mention the share protocol. I was using samba and switched to NFS to see if it helped. The stutter didn't go away but large transfers over the network do seem marginally faster.

Have yet to try the suggestions further up in this thread, would be a shame to loose the ability to play from an iso though.

Wondering if I should report a bug to the MythTV team...

Xines plays ISO's just fine.

---

### Post by oobe-feisty on 2009-03-30
i have a iso image of the sex pistols that is dual layer i been meaning to burn but havent bought any DL disks so i copied it to my mythvideo directory and it played fine on my FE/BE machine using Internal player so i thought maybe it will stutter using my remote frontend over wireless-n nope it played fine im using sshfs fuse to mount my mythvideo folder on my remote backend from the remote frontend i wrote a small howto [here ]("http://ubuntuforums.org/showthread.php?t=1090085")

---

