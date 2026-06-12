---
title: "Request help configuring Plexmediaserver"
date: 2023-06-06
forum: Multimedia Software
---

### Post by m9ke2 on 2023-06-06
Big problems getting Plex to see the media on my local Linux computer.

Plexversion: plexmediaserver_1.32.3.7162-b0a36929b_amd64.deb

OS Ubuntu Mate LTS ubuntu-mate-22.04.1-desktop-amd64

I will use my local TV directory as example as once this is figured out the other libraries should have the same solution.

Path to my media: /home/m9ke/media/TV

**Permissions **to the TV library:  drwxrwxr

**History: **just had to reinstall linux due to an unrelated problem. Plex was working on the same computer with the same libraries before the reinstall.

**Issue: **when I try to add the TV library using the correct path, Plex seems to take the input, but won't scan the library.

I am at wit's end and would greatly appreciate any help!

Thanks--Mike

---

### Post by TheFu on 2023-06-07
a)  Putting media under a user's HOME is a really bad idea. There are many, many, reasons.  Setup separate storage just for Plex.  

b) If you reinstalled the OS, chances are that the uid and gid numbers changed for the plex userid.  If you don't change the owner:group and permissions on all the media files, then that is almost certainly the issue.

I setup my media with these permissions:
```
$ ll /d/D1
total 1540
drwxrw**s**r-x   11 thefu   jellyfin    4096 May  8 20:17 ./
drwxr-xr-x   12 root root        4096 Jan 28 15:06 ../
drwxrwsr-x    6 thefu   jellyfin    4096 Nov 28  2022 ebooks/
drwx-wS---    2 thefu   jellyfin   16384 Feb 16  2014 lost+found/
drwxrwsr-x 1280 thefu   jellyfin   65536 Jun  5 20:17 M/
drwxrwsr-x    5 thefu   jellyfin    4096 Mar 27  2014 Photos/
drwxrwsr-x  108 thefu   jellyfin    4096 May 18 19:36 T/
drwxrwsr-x    4 thefu   jellyfin    4096 Oct  5  2022 V/
```
I have D2, D3, D4, D5, D6, D7 setup similarly.  Jellyfin merges the content spread across all those devices into a single view.  Plex and Kodi work the same, BTW.  As you can see from the dates, I've been doing media servers for a really long time. ;)

My userid is part of the jellyfin Unix group. You'd use plex instead.
That "s" means I've set the **setgid** flag on the directory and it has 'x' permissions.  This way, jellyfin (or plex) can add nfo files into the directories and all newly created subdirectories are created with the same group 'rwx' permissions.  this is following my "*working together*" guide.  I'd has been posted in these forums a few times. [Https://ubuntuforums.org/showthread.php?t=2382965&highlight=working+chgrp](Https://ubuntuforums.org/showthread.php?t=2382965&highlight=working+chgrp) is one link.

Of course, this only works for Linux file systems, not NTFS or exfat storage. They don't support Unix permissions.

Any chance I could talk you into using Jellyfin rather than Plex.  Jellyfin respects our privacy, unlike Plex which is selling that data to all buyers.  I ran a Plex server for a few years.  Jellyfin works directly with my HDHomerun TV tuners for recording and Jellyfin is 100% F/LOSS.  Of course, there are many things that Plex can do that Jellyfin doesn't.  For example, Plex only plays 3 types of audio files, so if you prefer better quality audio, you'll want Jellyfin.  Plex provides bonehead remote access, whereas with Jellyfin, I use either remote ssh tunnels or a VPN that I run at home to access the Jellyfin media.

Hope all this helps.  BTW, if we get the permissions, owner, and group setup, then we (me too) don't need to allow "other" any access.  Sometimes, even I am lazy. Sigh.

---

### Post by Tadaen_Sylvermane on 2023-06-07
Without knowing how or if plex is using a dedicated group your permissions are likely the problem.

```
**Permissions **to the TV library:  drwxrwxr
```

I'd expect more like this.

```
drwxrwxr-x
```

Without that execute bit anything outside of the user or group can't see inside the folder. The 3rd r is meaningless without the x.

---

### Post by TheFu on 2023-06-07
Also, any directories above where the media is stored can prevent access below, regardless of the permissions, owner and group being correct.  For some reason, I thought default HOME directory permissions had recently changed.  Just 1 reason never to play media under a HOME directory.

---

### Post by ajgreeny on 2023-06-07
I haven't used Plex for a few years now but it used to work very well for me even though I had all my media in my separate /home partition.

I always added me as user to the plex group and also added plex user to my own user group and all worked perfectly.

Worth a try I think.

PS:
I now use Emby in place of Plex for which I do the same group additions.

---

### Post by m9ke2 on 2023-06-07
The Fu: thank you for replying. Regarding Jellyfin: I am no fan of Plex. Before this post I completely uninstalled and purged Plex and installed Jellyfin. When I got to configuring Jellyfin, I  ran into the same basic problem. I understand the Jellyfin community is going dark for a couple of days. I didn't want to jump in to a new server with out community support. I totally get that Jellyfin is a better option. Once I get this issue figured out I will investigate upgrading from Plex to jellyfin.

---

### Post by m9ke2 on 2023-06-07
Digging into this more: 
1. I found that the files contained in the TV dir have different perms than the directory. I thought I set the perms recursively but they are different. Next: make sure the perms for enclosed files are proper down thru all the directories to individual files. I would like to set these perm to the minimum that will allow plex to work. What do folks think for owner, group and others?
2. I did not create a plex group. I think I better do that and add my user to it.

---

### Post by ajgreeny on 2023-06-07
You should not need to create the user named ***plex*** as far as I'm aware; I believe the system itself will create that user when plex is installed, as my system does with an emby user.

I would love to be able to use jellyfin as my mediaserver instead of Emby on my smart TV which is the main reason I need a mediaserver, but unfortunately there is no jellyfin client application for my smart TV at the moment as the LG TV is just too old and I refuse to spend large amounts of money just to get jellyfin working.  It may come before too many years as it's available on newer LG TV models so I am just waiting, hopefully for not too much longer.

---

### Post by TheFu on 2023-06-07
In 22.04, they changed the default umask and settings on HOME directories to improve security.

they are this on my untouched, 22.04 install:
```
drwxr-x---  7 thefu   thefu   4096 May 31 21:57 thefu/

```

Just checked this.

So, nobody or any process running as another user, can access anything in a user's HOME by default.
I suspect people who aren't seeing permission issues for plex, emby, or jellyfin with media inside their HOMEs,  retained that storage directories from earlier installs.

There are a number of other reasons why having media accessed by any daemon or other user in a HOME is a bad idea.

---

### Post by m9ke2 on 2023-06-07
I will mark this one solved. I got the TV library working and used the same method for the other libs. Plex is building new libraries now.
I learned:
 - The x is needed to Plex to see directories and files in order to build its libraries. Thanks Tadaen_Sylvermane!
 - Need to set up a plex group and adjust permissions. Thanks TheFu!
 - Emby and Jellyfin are good alternatives to Plex. I'll look at t hose when I get the beast that is Plex chased back into its cave (for now) Thanks TheFu and ajgreeny!

---

### Post by TheFu on 2023-06-07
> **m9ke2 said:**
> I will mark this one solved. I got the TV library working and used the same method for the other libs. Plex is building new libraries now.
I learned:
 - The x is needed to Plex to see directories and files in order to build its libraries. Thanks Tadaen_Sylvermane!
 - Need to set up a plex group and adjust permissions. Thanks TheFu!
 - Emby and Jellyfin are good alternatives to Plex. I'll look at t hose when I get the beast that is Plex chased back into its cave (for now) Thanks TheFu and ajgreeny!

The plex group was already created when plex was installed. Just add your userid to that group.
The 'x' is necessary for any user to access anything inside a directory.  There are 3 groups involved.

owner, group, "other".   "Other" means anyone who isn't the owner or a member of the group connected to the directory.  Some training calls that "world", but that isn't accurate. It truly is "other".  For example
```
rwx---r-x   some_directory
```
Will block all members of the group who are not the owner from access, but anyone outside the group would have read and execute.  On a directory, execute means they can "cd" into the directory. With out read and execute, getting a list of the subdirectories and files isn't allowed.  These are subtle things to make Unix permissions very powerful.  

There are times with having 751 (rwxr-x--x) permissions on a directory is perfectly fine.  Anyone can run a compiled program in that directory, if the absolute path to that program is known and used.  However, scripts cannot be run, since read permissions are required to interpret a script.
Subtle things.  Very powerful.

---

