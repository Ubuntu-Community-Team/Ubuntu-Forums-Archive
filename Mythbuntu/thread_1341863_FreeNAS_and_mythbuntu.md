---
title: "FreeNAS and mythbuntu"
date: 2009-11-30
forum: Mythbuntu
---

### Post by ss2115 on 2009-11-30
Hi.
I'm mostly new to Linux. Pretty good with Windows and experience stretches back to the days of DOS, so think I'll pick it up quickly enough (hope so anyway).

I'm building a mediabox. Chose to try Mythbuntu because of the rock steady stability of my Linux Fileserver running FreeNAS.

I need assist with two things -
I've installed Mythbuntu to the new Media PC. Chose the default "both front and back ends on the same PC".
However, in looking around and getting to know it, I can't seem to get any music or any media files onto it that it can find. I had MP3's on a USB stick to try but Mythbuntu doesn't find them.
I dropped out of Mythbuntu into the std Ubuntu and used the file manager to copy the MP3's to the "My Music" folder and then went back into Mythbuntu but it still cannot find them. Found in the settings section that Mythbuntu has its own music and video and photo directories but after dropping back into Ubuntu to use the file manager again, I cannot access these directories - they just don't showup.
Don't know what to do next!

I did notice in the applications the possibility to select "install myth backend". So perhaps although I chose to have both front& back ends on the same PC in the original setup, do I still need to install the backend separately???

Second item. I have a 1.2Tb fileserver running FreeNAS. Its a Raid 5 array with seperate Hdd on the normal IDE channel to run the OS.

If i get Mythbuntu running correctly, will it be able to access movie and music files on this server as it all stands now? Or do I have to somehow make the fileserver a backend? And is it possible to do this - ie: can I install mythbuntu to the FreeNas OS and have them co-exist?
If not and I decide to change the fileserver to a Mythbuntu backend, can it still be used as a networked PC and with the automatic backup programs I have for saving our individual desktops and laptops backups as well as any files I decide to send to it for safe keeping.

---

### Post by blackoper on 2009-12-01
you won't need to make the freenas a backend. (you can't anyway, mythtv won't run on the freenas system. You'd have to use actual freebsd). To setup these samba/cifs based shares you'll need to add these shares to the /etc/fstab file to be mounted on boot.

go into mythtv-setup and change your directory structure to match what you choose. Also I've found it's easier to use webmin admin administration program to change your cifs/samba shares. I don't like the default mythbuntu ones.

---

### Post by nickrout on 2009-12-01
By default mythbuntu looks in /var/lib/mythtv/music for music files and /var/lib/mythtv/videos for video files. Place your music and video files accordingly.

In mythvideo you need to hit 'm' or the menu key on you remote and then choose 'scan for changes' to get the videos into your database.

I am not sure on 0.22 how to get your music into the database, probably still have to go through the menu system until you find mythmusic setup and then get it to scan for your music (sorry to be a bit vague, its hard to remember the steps to go through without a system in front of me)

As far as the NAS is concerned, I suggest you mount the NAS's music directory and videos directory under the appropriate points in the filesystem. eg

```
mkdir /var/lib/mythtv/music/nas
mount -t cifs //nasbox/musicshare /var/lib/mythtv/music/nas -o username=bill,password=secret
```

where nasbox is the name of the nas machine and musicshare is the name of the share with the music in. Similarly for the videos.

By the way FreeNAS runs freebsd, not linux. Myth will work on freebsd, but whether you could add it to freenas is another matter. Anyway you don't need to, see above :)

---

### Post by d2tw4all on 2009-12-01
I use a freenas as my storage for DVD ISO files and mount the shares using the fstab method on the frontends as mentioned.  One thing to point out though, if you have multiple frontends you MUST mount the shares in the same mount point on each frontend, for some reason when you set source in myth it's not specific to each frontend but a general setting that ALL frontends share.  Maybe there's a way around this but I've not found one.  It's not a problem as long as all your frontends mount the freenas share in the same mount folder.

Tom

---

### Post by nickrout on 2009-12-02
> **d2tw4all said:**
> I use a freenas as my storage for DVD ISO files and mount the shares using the fstab method on the frontends as mentioned.  One thing to point out though, if you have multiple frontends you MUST mount the shares in the same mount point on each frontend, for some reason when you set source in myth it's not specific to each frontend but a general setting that ALL frontends share.  Maybe there's a way around this but I've not found one.  It's not a problem as long as all your frontends mount the freenas share in the same mount folder.

Tom

**Unfortunately** the database stores the full path of each video file so it must be the same path on each frontend.

**Fortunately** you can solve this in 0.22 by using storage groups.

**Unfortunately** storage groups don't work with iso files or video_ts directories, or with players other than internal.

**Fortunately** this is slated to be fixed in 0.23

**Unfortunately** 0.23 is not yet released :)

---

### Post by bcg30506 on 2009-12-02
> **nickrout said:**
> **Unfortunately** the database stores the full path of each video file so it must be the same path on each frontend.

**Fortunately** you can solve this in 0.22 by using storage groups.

**Unfortunately** storage groups don't work with iso files or video_ts directories, or with players other than internal.

**Fortunately** this is slated to be fixed in 0.23

**Unfortunately** 0.23 is not yet released :)

This make me choke on my drink by laughing so hard!  Thanks.  I nominate this the post of the day.  :D

---

### Post by seeker5528 on 2009-12-02
> **ss2115 said:**
> If i get Mythbuntu running correctly, will it be able to access movie and music files on this server as it all stands now?

In theory if you mount your network shares in fstab:

[http://opensuse.swerdna.org/susesambacifs.html](http://opensuse.swerdna.org/susesambacifs.html)

Then in your local music directory that you have MythTV pointed at create a symlink to your music directory on the network share, it should work. Then do the same for your video directories.

I have not really done the music and video thing much in MythTV at all, much less over the network. 

In my Debian install with Myth 0.22 symlinking works for my music and images, there seems to be a problem at the moment with the video stuff, but it should work for that too, still have not tried it yet in my Ubuntu install.

Later, Seeker

---

### Post by nickrout on 2009-12-02
I simply mount them under /var/lib/mythtv/music|videos but symlinking to another mount point works too. You can also specify more than one point in your filesystem that has videos, separate different paths by : (or is it ;, I forget)

I should have added that after you have it set up how you like you should add the mountpoints to /etc/fstab

A point to note, /etc/fstab, and therefore your cifs passwords, are readable by anyone. Instead of putting the username and password in the fstab file, use option credentials=/root/cifscredentials

/root/cifscredentials will look like:

```
username=bill
password=secret
```

make /root/cifscredentials readable and writable only by root.

---

### Post by movieman on 2009-12-03
BTW, note that installing mythmusic will currently delete any symbolic link at /var/lib/mythtv/music, so don't be surprised when all your music disappears from the MythTV interface after a major upgrade :). At least it will still be in the directory the symbolic link points to, but you'll need to create the link again.

That confused me for a while after upgrading 9.04->9.10 until I realised there was now an empty directory there instead of a symbolic link.

---

