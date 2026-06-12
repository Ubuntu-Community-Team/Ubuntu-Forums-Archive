---
title: "[SOLVED] iPod Issues making me go nuts"
date: 2008-12-27
forum: Multimedia Software
---

### Post by Archie69 on 2008-12-27
Hello all,

This is the second time I've posted regarding this issue.  I connect my iPod to the computer, it recognizes the iPod in Rythmbox however, it will not let me edit my songs.  My question is this...

1. Would it be easier to just reformat (clean erae of the ipod) and then just put songs on it again
2. Has anyone had this issue and had it resolved?
3. Has 8.10 solved this issue?

I have an older iPod Mini or nano, im not sure.  its 4g and I'm running Ubuntu 8.04 Hardy.

Please someone, this is driving me nuts.

---

### Post by MarblePanther on 2008-12-27
rhythmbox seems to have problems with some tags.

try ex falso to edit tags.

also gtkpod is a great tool to put songs on it and edit tags

songbird is a player that has the capability to sync!

---

### Post by Archie69 on 2008-12-27
Looks like gtkpod would work well, but i get error messages when i try to edit everything.

Seems as though my iPod is read only.  is that even possible?  
Anyone know how to fix that?
It seems as though if I fix this problem it should work.

---

### Post by Archie69 on 2008-12-28
Does anyone know why or how to fix the iPod being "READ ONLY"???

I don't even know how thats possible, let alone fixing it.  

HELP PLEASE!!!!

---

### Post by rudihawk on 2008-12-28
Try amarok - i've found it works the best of all the apps i Have tried with my ipod. I have a 6th Gen Ipod Classic (160GB)

---

### Post by dartmusic on 2008-12-28
I'll second that vote for amarok, but have a question:  how do you get your artwork to transfer correctly to your Classic 160gb?  I get the small thumbnails in the album list per artist, but when I'm playing an album, there are no album covers.  It's kind of a bummer.

But yes, start with a freshly formatted iPod, and load up the 1.4.x version of amarok and go to town.

---

### Post by Archie69 on 2008-12-28
Hey All,

I'm trying to use Amarok, and its the worst yet...at least it seems that way.  I have no idea what to do.

How can I wipe the iPod clean and start from scratch?

---

### Post by Archie69 on 2008-12-28
So I have erased my iPod of all its music and I still can't load songs onto my iPod.  It seems to me that Ubuntu and linux in general are not ideal for multimedia.  This has been my experience, it has been a very frustrating transition.

---

### Post by SuperSonic4 on 2008-12-28
It is the device, not the OS. Apple don't support any other way other than iTunes which, as we know, doesn't work on Linux natively if it all.

Have you tried removing the iTunes lock file? /media/iPod/iPod Control/iTunesLock or something.

---

### Post by Archie69 on 2008-12-28
yeah, it wont let me becuase the iPod is "read Only" apparently.

By the way its an iPod mini 4G.  Older version.

---

### Post by namdung on 2008-12-28
There is no iTunes for Linux. Songbird is an excellent option with plugin for iPod. It supports editing tags and sync with iPod. Give it a try.
[http://getsongbird.com/](http://getsongbird.com/)

You may also try FOSS OS for iPod
[http://www.rockbox.org/](http://www.rockbox.org/)
[http://www.ipodlinux.org/](http://www.ipodlinux.org/)

---

### Post by Archie69 on 2008-12-29
Seems like its the REad Only issue....I'm hoping.  Anyway, the only thing I think it can be is the fact that the iPod is Read Only and I dont know what to do.  I've tried to erase the iPod control or whatever but no dice.  Again, it wont allow me to erase anything because of the Read Only ****.  Has anyone ever run into this much trouble with a effing iPod?  I know apple are a bunch of dicks but F, there has to be a way around this.  

Thanks for all the help so far everyone.

---

### Post by namdung on 2008-12-29
I reckon ur iPod has some disk error.
```
chkdsk /f (in Windows) to check errors on ur iPod.
```

Ubuntu should be happy after this.

[http://ubuntuforums.org/archive/index.php/t-189962.html](http://ubuntuforums.org/archive/index.php/t-189962.html)

---

### Post by Archie69 on 2008-12-29
do i type that in terminal?

I dont run windows nor do I have a computer that runs Windows.  I have a Mac, but thats it.

---

### Post by namdung on 2008-12-29
> **Archie69 said:**
> do i type that in terminal?

I dont run windows nor do I have a computer that runs Windows.  I have a Mac, but thats it.

Taken from the previous link: [http://ubuntuforums.org/archive/index.php/t-189962.html](http://ubuntuforums.org/archive/index.php/t-189962.html)

> Type in terminal in Ubuntu PC
```
cat /etc/mtab
```

To find out where the ipod is mounted (it'll be the line with /media/ipod, cat that when the iPod is plugged in and automounted, obviously). Once you have the /dev, alls you do is

```
dosfsck /dev/sdb2 -a
```

Where /dev/sdb2 is your ipod's device.

---

### Post by Archie69 on 2008-12-29
this is what i see in Terminal

/dev/sda1 / ext3 rw,relatime,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.24-21-generic/volatile tmpfs rw 0 0
securityfs /sys/kernel/security securityfs rw 0 0
gvfs-fuse-daemon /home/marco/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=marco 0 0
/dev/sdb3 /media/Marco&#8217;s\040iPod hfsplus rw,nosuid,nodev,uhelper=hal 0 0


I'm kinda new so I dont know where to go from here for the second step.  There are too many lines that say "dev"

Thanks

---

### Post by Archie69 on 2008-12-29
so now  I am in terminal trying to fix this issue with a little help, but guess what?  I'm stuck (boo me)

so this is where I am:

 dosfsck /dev/sdb3 /media/Marco’s\040iPod hfsplus rw,nosuid,nodev,uhelper=hal 0 0

I type that and I see this:

usage: dosfsck [-aAflrtvVwy] [-d path -d ...] [-u path -u ...]
               device
  -a       automatically repair the file system
  -A       toggle Atari file system format
  -d path  drop that file
  -f       salvage unused chains to files
  -l       list path names
  -n       no-op, check non-interactively without changing
  -r       interactively repair the file system
  -t       test for bad clusters
  -u path  try to undelete that (non-directory) file
  -v       verbose mode
  -V       perform a verification pass
  -w       write changes to disk immediately
  -y       same as -a, for compat with other *fsck


So I try to type -a, but nothing haoppens.  What am I doing wrong?
Please help folks.  Thanks

---

### Post by gandaran on 2008-12-29
open the terminal and type **sudo nautilus ** hit enter and password, enter again
this will open a new nautilus window with root administration rights, use this window to navigate to your ipod, now you can copy or delete any file,  you can also change the music folder or files proprieties from root to user so next time you mount the ipod you have access to them

---

### Post by soxs on 2008-12-29
if your ipod is <read only>, get the root directory(which is the mountpoint) of your ipod and do: ```
sudo chmod 755 -Rvf /media/<ipod-mount-point-name>
``` in a terminal (like xterm or gnome-terminal or whatever...)
If you want to make the user you currently logged in as being the owner of the ipod files do:
```
sudo chown $USER -Rvf /media/<ipod-mount-point-name>
```

---

### Post by namdung on 2008-12-29
> **Archie69 said:**
> so now  I am in terminal trying to fix this issue with a little help, but guess what?  I'm stuck (boo me)

so this is where I am:

 dosfsck /dev/sdb3 /media/Marco’s\040iPod hfsplus rw,nosuid,nodev,uhelper=hal 0 0

I type that and I see this:

usage: dosfsck [-aAflrtvVwy] [-d path -d ...] [-u path -u ...]
               device
  -a       automatically repair the file system
  -A       toggle Atari file system format
  -d path  drop that file
  -f       salvage unused chains to files
  -l       list path names
  -n       no-op, check non-interactively without changing
  -r       interactively repair the file system
  -t       test for bad clusters
  -u path  try to undelete that (non-directory) file
  -v       verbose mode
  -V       perform a verification pass
  -w       write changes to disk immediately
  -y       same as -a, for compat with other *fsck


So I try to type -a, but nothing haoppens.  What am I doing wrong?
Please help folks.  Thanks

Type in terminal

```
dosfsck /dev/sdb3 -a
```

Now unmount and mount ur iPod.

---

### Post by Archie69 on 2008-12-29
> **namdung said:**
> Type in terminal

```
dosfsck /dev/sdb3 -a
```

Now unmount and mount ur iPod.



hey, it says PERMISSION DENIED when I type the last line.  Thanks for the help I really appreciate it, what do you think I should do next?

---

### Post by namdung on 2008-12-29
> **Archie69 said:**
> hey, it says PERMISSION DENIED when I type the last line.  Thanks for the help I really appreciate it, what do you think I should do next?

```
sudo dosfsck /dev/sdb3 -a
```

sudo gives a user root privileges. 
Just ensure that ur iPod is in sdb3.

---

### Post by ezsurfer on 2008-12-29
STOP - You are going way too far.  I believe your question really involves editing tags (can be done in Rythmbox Music Listing tab, not directly on the iPod view), not deleting the files.  Selected files can be deleted by the right button click option (also works on multiple selections) move to trash.

Your Music tags can be edited, but not the iPod entry.  For the tags, go to the Music Listing and edit there.  Only real issue then is the iPod sees that listing as all new, duping everything you drag and drop over to the iPod.

So, to make it easy to understand what I have found out in the last day of my iPod and Rythmbox, 

1) Drag and drop works vice "sync" in iTunes
2) If you can, start with the iPod, select all the songs, and drop them into the MusiC Listing file
2a) Delete all the files on the ipod (right button click - move to trash)
3) Then get all the other folders imported into the Music Listing Folder from your files (various drives and folders)
4) Edit properties as you wish until you have everything set the way you want it.
5)  Select all the Music Listing entries, drag and drop them on a fully deleted iPod, and all the data transfers well and ends up working very well.  (and the sync is very fast, albeit manual)
6) turn on the Rythmbox preferences that track changes, so that as you add songs to the Music Listing, you'll know which ones to add to the iPod.

or - I am the one misunderstanding your question.

Clif

---

### Post by Cracauer on 2008-12-29
I use Rockbox on my iPod. Problem solved.

---

### Post by Archie69 on 2008-12-29
> **namdung said:**
> ```
sudo dosfsck /dev/sdb3 -a
```

sudo gives a user root privileges. 
Just ensure that ur iPod is in sdb3.


Got it.  but guess what?  It didn't work.  I have no idea why.  I run the auto repair by typing that line, and get the message 
**Logical sector size is zero.**

I unmounted the iPod, then mounted it again and tried to preform tasks on Rythmbox and it still wont allow me.  Banshee doesn't recognize it and gtkpod says read only still.  Any other ideas?

---

### Post by nickrout on 2008-12-29
seems to me theres little point in using dosfsck when the ipod is formatted as hfs

---

### Post by Archie69 on 2008-12-29
well do you have any further suggestions to assist me with this ongoing issue?

It would be greatly appreciated since I'd like to have the convenience of an operating system that is fully functional with everyday usage.

---

### Post by mc4man on 2008-12-29
By FAR the safest thing to do would be to copy your songs off of the ipod and find someone with a win box and itunes, and redo the ipod with fat32.

If you do a search you can find methods to manually format though I wouldn't do that. 
Be aware that the ipod has 2 partitions, the first one is your firmware, lose that and you won't have an ipod till it's restored.

Maybe try installing hfsprogs to run a fsck 

There should be a man or --help on it

maybe ....??
sudo fsck.hfs /dev/sdb3   or
sudo fsck.hfsplus /dev/sdb3



If you want to search manual ways try something like this in google (try some other key words also

ipod hfs site:ubuntuforums.org

---

### Post by Cracauer on 2008-12-29
If you don't want to switch the iPod to rockbox, let a Windoze installation with iTune reformat the whole thing. That way you also get a windoze filesystem, which might shield you from previous trouble.

It's not our fault, BTW.

---

### Post by nickrout on 2008-12-29
nor linux's fault. I bought an ipod nano 4Gen 16GB this afternoon and I am listening to music on it now. No windows computer in sight. gtkpod set up the directories on it, and rhythymbox was then able to load my music onto it.

---

### Post by Archie69 on 2009-01-04
OMG I can't believe I fixed this ipod thing.  It seems to work so far.  Cheek out this link to see if it helps you.

[http://davesource.com/Solutions/20080225.iPod-linux-read-only.html](http://davesource.com/Solutions/20080225.iPod-linux-read-only.html)

WOW.  what a chore

---

### Post by MrMarkAZ on 2010-01-10
This procedure solved a problem I was having:

> **namdung said:**
> Taken from the previous link: [http://ubuntuforums.org/archive/index.php/t-189962.html](http://ubuntuforums.org/archive/index.php/t-189962.html)

My symptoms were as follows: RhythmBox could see my iPod and all files on it and would play them just fine. However, I could not add music files to the iPod: any file transfer of this nature would return a copy error with "access is denied" message.

After I ran the previous commands, the same file transferred without any problem. Much appreciated.:guitar:

---

