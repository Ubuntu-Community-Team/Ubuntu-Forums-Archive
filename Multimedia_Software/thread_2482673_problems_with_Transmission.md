---
title: "problems with Transmission"
date: 2023-01-07
forum: Multimedia Software
---

### Post by shantiq on 2023-01-07
havin used up most of my 1Tb on my harddrive I decided to add a 2Tb USB stick/flashdrive to add memory. I had done this before with an external drive and Transmission did not like it.  Sometimes the files would show up red on reloading and paused and could not be started again


This time with the memory stick for the first week it went brilliant;  but now some files show up red/paused also here and some of the music/videos files show up as having NO audio basically they have been erased/destroyed/nullified


Does anyone understand why that might/could be

the 2Tb  i added to the Fstab thus

```
UUID="76E8-CACF" /media/shan/76E8-CACF exfat nofail,rw,user,exec,umask=000  0   0
```

All clever and useful info welcome

Thanx   shan


PS    i have also realized that the Owner and Group were Root on this USB; unlike the Original harddrive which is shan so I have changed it now to be in line with the OHardrive and changed the fstab line to: ```
UUID="76E8-CACF" /media/shan/76E8-CACF exfat nofail,rw,user,exec,umask=0077  0   0
```


where 0077 is also the same as OHardrive   ;   will monitor and report if OK now


All clever and useful info STILL welcome meantimes :KS

---

### Post by TheFu on 2023-01-10
For spinning disks connected only to Linux, use ext4 as the file system.
For spinning disks connected to a dual-boot Linux/Windows system, use NTFS as the file system.

Never use exFAT or FAT32.  These are non-journaled file systems.  You want a journaled file system.  ext3, ext4, xfs, NTFS are the main options.

Fix it now, before there it too much data on the system.  If you use a Linux file system, then chown and chmod will work.  Foreign file systems don't support those and only mount options can be used.

Why mount to a funky named directory?  Set a LABEL for the file system using 'gparted' and use that unique LABEL in the mount line of the fstab file to mount the storage where you like.  For most people (not me), the best location to mount it would be /media/{LABEL}/

The mount options differ based on the file system involved.  NTFS needs a few extras or performance can suck.
As you might expect, ext4 doesn't need many extra options. It is the native file system for Linux.
Regardless, once a LABEL is set, that can be used instead of the UUID to mount a specific file system.  Much nicer for all the humans using computers.

Mounting using LABELs: [Https://ubuntuforums.org/showthread.php?t=2464944&p=14048909#post14048909](Https://ubuntuforums.org/showthread.php?t=2464944&p=14048909#post14048909)  
```
UUID=2471d686-fde5-4680-a75a-a6c99c8a5550 /media/Videos    ext4 defaults 0     2
```
would become
```
LABEL=VIDEOS3    /media/Videos3    ext4 defaults 0     2
```
Which is easier to understand?  The label is just a tag and not related to the mount directory. It just happens that a useful label is also a useful mount point.

LABELs on file systems completely rock!

---

### Post by shantiq on 2023-01-10
> **TheFu said:**
> For spinning disks connected ;;;


thanx TheFu for this advice you write spinning disk you do realize it is a USB stick i am trying to use here?

---

### Post by TheFu on 2023-01-10
> **shantiq said:**
> thanx TheFu for this advice you write spinning disk you do realize it is a USB stick i am trying to use here?

USB is the interface.  

The actual storage can be spinning disk, SSD (SATA or NVMe), or Flash storage.  For SSD and HDD devices, you should use ext4 or NTFS, never exFAT. You want to use a journaled file system whenever possible, provided it doesn't drastically impact storage lifetime.  It doesn't for all but flash storage, like a USB-thumb drive or SDHC/microSD cards.

Since you said it was 2TB, I assumed you hadn't spent $200 for an SSD and got a $40 external HDD with a USB connector.  Flash storage isn't really larger than 512GB and I wouldn't bother with one of those - actually I don't go larger than 64GB for flash storage due to the relatively poor lifetime.

[https://en.wikipedia.org/wiki/Journaled_file_system](https://en.wikipedia.org/wiki/Journaled_file_system) explains what a Journaled file system is.  You really want to use one, whenever possible.  Before they came along, data corruption and data loss was pretty common for tiny issues that are easily handled through journaling.

---

### Post by shantiq on 2023-01-10
this [[IMG]https://i.postimg.cc/t7xhXpFK/s-l1600.jpg[/IMG]]("https://postimg.cc/t7xhXpFK")

i tried [COLOR=#000000]ext4 or NTFS but it did not seem to be recognized once plugged in[/COLOR]

---

### Post by SeijiSensei on 2023-01-10
Open a terminal and run
```
$ sudo mkfs -t ext4 /dev/sdb1
```
Replace sdb1 with whatever the partition identifier is that you want to format.

---

### Post by shantiq on 2023-01-10
> **SeijiSensei said:**
> Open a terminal and run
```
$ sudo mkfs -t ext4 /dev/sdb1
```
Replace sdb1 with whatever the partition identifier is that you want to format.


EDIT

mounted it then unmounted and this is what it gave me

```
shan@shan-Aspire-XC-780:~$ sudo mkfs -t ext4 /dev/sdc1[sudo] password for shan: 
mke2fs 1.46.5 (30-Dec-2021)
/dev/sdc1 is mounted; will not make a filesystem here!
shan@shan-Aspire-XC-780:~$ sudo mkfs -t ext4 /dev/sdc1
mke2fs 1.46.5 (30-Dec-2021)
/dev/sdc1 contains a ext4 filesystem
    last mounted on Tue Jan 10 21:20:30 2023
Proceed anyway? (y/N) 
```


what do i do here?  NOT SEEN until i say yes here?


this is the entry i placed in fstab (which i will remove until i understand what i am doing :)


```
LABEL=2Tb    /media/2Tb    ext4 defaults,nofail 0     2
```


i used LABEL as Senji suggested

If you can explain how to move now will be grateful


NB   managed to lock myself out of Ubuntu with faulty entry in fstab before WAS a performance to get back in; ***so very cagey is me***


Thanx guys


PS    formatted that route


[[IMG]https://i.postimg.cc/QVrSFfhY/1.png[/IMG]]("https://postimg.cc/QVrSFfhY")


[[IMG]https://i.postimg.cc/sGcMxjsz/2.png[/IMG]]("https://postimg.cc/sGcMxjsz")

---

### Post by TheFu on 2023-01-10
> **shantiq said:**
> this [[IMG]https://i.postimg.cc/t7xhXpFK/s-l1600.jpg[/IMG]]("https://postimg.cc/t7xhXpFK")

i tried [COLOR=#000000]ext4 or NTFS but it did not seem to be recognized once plugged in[/COLOR]

That looks like flash storage to me.  exFAT is the 2nd best option and only if you want to plug it into MS-Windows computers too.  If for linux only use, use f2fs.

I though you had something like this:  [https://www.microcenter.com/product/476642/wd-elements-2tb-usb-31-(gen-1-type-a)-25-portable-external-hard-drive-black](https://www.microcenter.com/product/476642/wd-elements-2tb-usb-31-(gen-1-type-a)-25-portable-external-hard-drive-black)  Wow, $62.  Last week (or the week before), I saw a 2TB HDD for $44.  

I hope that flash thumb drive doesn't wear out too quickly.  I've had a reputable 64G flash drive die just after 1 yr of daily use. Maybe they are better now and have better controllers for better wear leveling?  IDK.

TL;DR - flash drives should use f2fs on Linux and exFAT for cross-platform, unless you have a specific hardware device that only works with FAT32 (my PnS camera doesn't do exFAT).

---

### Post by shantiq on 2023-01-10
> **TheFu said:**
> That looks like flash storage to me.  exFAT is the 2nd best option


YES    i do not think i can use ext4 with this it is too basic  this was very cheap :o

---

### Post by TheFu on 2023-01-10
> **shantiq said:**
> YES    i do not think i can use ext4 with this it is too basic  this was very cheap :o

You can, but you shouldn't.  That isn't a "harddrive", it is a "flash drive" or a "thumb drive".
You wrote:
> havin used up most of my 1Tb on my harddrive I decided to add a 2Tb USB to add memory. I had done this before with an external drive and Transmission did not like it. Sometimes the files would show up red on reloading and paused and could not be started again

BTW, "memory" usually means RAM, not storage.

I've never used Transmission. I think it runs under a different userid, probably "transmission", so you'll need to ensure that userid has write access to whatever storage you plan to write files using that bittorrent tool.

---

### Post by shantiq on 2023-01-11
thanx for that and previous info Fu   much appreciated.   These are areas I am very shaky on

```
shan@shan-Aspire-XC-780:~$ id
uid=1000(shan) gid=1000(shan) groups=1000(shan),4(adm),24(cdrom),27(sudo),29(audio),30(dip),44(video),46(plugdev),113(lpadmin),124(pulse),125(pulse-access),128(sambashare)
```

no sign of transmission here

also ran    ```
[COLOR=#1F2937][FONT=&amp]getent passwd | grep transmission[/FONT][/COLOR]
```    and nada but i might be looking at the wrong thing

---

### Post by TheFu on 2023-01-11
[https://help.ubuntu.com/community/TransmissionHowTo](https://help.ubuntu.com/community/TransmissionHowTo) ... looks like they use a different userid for the server than I guessed. 

I'm a little surprised that very little is said about directory and file permissions in the How-To.  It does suggest putting your user and the transmission daemon user into the same group, but it doesn't say to make the place where files get placed have that group, nor anything about the setgid bit on the directories there. I suppose people are supposed to know that by osmosis.

---

### Post by shantiq on 2023-01-11
that looks useful from the link

```
**"umask" parameter**

[COLOR=#333333][FONT=Ubuntu]You will also have to set the "umask" parameter in Transmission’s settings file to “2” (default is 18) for the account user to have full access to files/folders created by Transmission.[/FONT][/COLOR]

[COLOR=#333333][FONT=UbuntuMono]"umask": 2,[/FONT][/COLOR]
```

---

### Post by shantiq on 2023-01-13
what i did in the end:


thanx to both for the clever advice i learnt much from it all

So the 2Tb flashdrive was really/is a case of taking a knife to a gun fight

It really cannot be used as a HDD or an SSD could

So I repurposed an old HDD to a caddy which has still 250Gb of free space and added that to my fstab. It still loads up as Root whatever I do but if i unplug it or load it after PC restart it shows me as the User and the files are visible and fine (it seems) in Transmission.   I am not horsing around with fstab which easily locks you out if you make any mistake/ getting back in is plain scary if that happens :KS

I will later on add an SSD in the same fashion probably but for the coming year this should be fine

Again thanx for the help. Will mark as solved as got what i set out to get albeit NOT with the flashdrive but that really matters not it costs me £7 so no biggie (it loads up photos at a fair transfer rate but does not audio and video files {very slow} totally unsure why)



**PS:   **if adding an SSD to my setup would this be a sound line to add to my fstab?


```
#Use for an SSD
LABEL=SSD   /media/shan/SSD  ntfs  nofail,user,fmask=0111,dmask=0000   0   0
```

---

### Post by TheFu on 2023-01-13
£7 for 1TB/2TB sounds like a fake.  The that price, I'd expect 32GB or perhaps 64GB if you get a really, really, really, good deal.  

Things that sound too good to be true almost always are.  After all, fake "20TB - 40TB SSDs" are being sold for $30-$50 and people gullible enough to pay.  When they get $12 worth of cheap, SDHC storage with a USB controller and case that claims to be 30TB, they are surprised.  They write lots of stuff to the drive, but only get the last 2GB back, since that's the total amount of real SDHC storage inside the case.
Ref: [https://arstechnica.com/gadgets/2022/08/walmart-lists-a-30tb-portable-ssd-for-39-it-is-naturally-a-scam/](https://arstechnica.com/gadgets/2022/08/walmart-lists-a-30tb-portable-ssd-for-39-it-is-naturally-a-scam/)

These scams have been happening and working far too often for far too long.
 
As for permissions, foreign file systems, and having different users in the same group being able to write to the same directories and files, that requires a good understanding for each, beginning with normal Unix file and directory permissions.

this is incomplete and seems wrong to me.
```
LABEL=SSD   /media/shan/SSD  ntfs  nofail,user,fmask=0111,dmask=0000   0   0
```

Assuming you add "SSD" as the LABEL for the partition/file system, then I think you are missing the steps where your userid and the transmission daemon user are put into the same group, then that group is forced for the NTFS storage mount options.  The fmask should probably be '0002' and the same for the dmask.  If using NTFS, I'd specify these options too:  nodev,nosuid,noatime,windows_names,async,big_writes   to prevent names that NTFS doesn't allow and get some better performance.
```
LABEL=SSD /media/shan/SSD ntfs  nofail,nodev,nosuid,noatime,windows_names,async,big_writes,fmask=0002,dmask=0002,uid=shan,gid=shantrans 0 0
```
all on 1 line. Be certain to add the shan and whatever the transmission daemon userid is to the "shantrans" group.
Anyway, that's my best guess, but I've made lots of assumptions.

---

### Post by shantiq on 2023-01-14
Thanx for all the info again and yes I have just sent off for one of [those]("https://arstechnica.com/gadgets/2022/08/walmart-lists-a-30tb-portable-ssd-for-39-it-is-naturally-a-scam/")  :KS  too late now   and YES my "2Tb"    does just that it says in the article it stores those files but when you try to open them the file is void ;    criminal scam   never knew

anyway you live and learn thanx on the fstab line which i will use when i finally get a proper one


PS    i understand what the elements you have written mean apart from [COLOR=#000000]the "transmission daemon user"    where would that be visible all we have for that software is a settings documents
which contains this; I see no line which would be the right one for a change

[/COLOR][COLOR=#000000]
[/COLOR]```
{    "alt-speed-down": 50,
    "alt-speed-enabled": false,
    "alt-speed-time-begin": 540,
    "alt-speed-time-day": 127,
    "alt-speed-time-enabled": false,
    "alt-speed-time-end": 1020,
    "alt-speed-up": 50,
    "bind-address-ipv4": "0.0.0.0",
    "bind-address-ipv6": "::",
    "blocklist-enabled": false,
    "blocklist-updates-enabled": true,
    "blocklist-url": "http://www.example.com/blocklist",
    "cache-size-mb": 4,
    "compact-view": true,
    "details-window-height": 527,
    "details-window-width": 566,
    "dht-enabled": true,
    "download-dir": "/home/shan/Videos",
    "download-queue-enabled": true,
    "download-queue-size": 17,
    "encryption": 1,
    "idle-seeding-limit": 30,
    "idle-seeding-limit-enabled": false,
    "incomplete-dir": "/home/shan/Downloads",
    "incomplete-dir-enabled": false,
    "inhibit-desktop-hibernation": false,
    "lpd-enabled": false,
    "main-window-height": 653,
    "main-window-is-maximized": 1,
    "main-window-width": 909,
    "main-window-x": 781,
    "main-window-y": 95,
    "message-level": 2,
    "open-dialog-dir": "/home/shan/Desktop",
    "peer-congestion-algorithm": "",
    "peer-id-ttl-hours": 6,
    "peer-limit-global": 200,
    "peer-limit-per-torrent": 50,
    "peer-port": 51413,
    "peer-port-random-high": 65535,
    "peer-port-random-low": 49152,
    "peer-port-random-on-start": false,
    "peer-socket-tos": "default",
    "pex-enabled": true,
    "port-forwarding-enabled": true,
    "preallocation": 1,
    "prefetch-enabled": true,
    "queue-stalled-enabled": true,
    "queue-stalled-minutes": 30,
    "ratio-limit": 2,
    "ratio-limit-enabled": false,
    "recent-download-dir-1": "/home/shan/Videos/Transmission Files",
    "recent-download-dir-2": "/home/shan/Videos",
    "recent-download-dir-3": "/media/shan/76E8-CACF1",
    "recent-download-dir-4": "/media/shan/76E8-CACF",
    "rename-partial-files": true,
    "rpc-authentication-required": false,
    "rpc-bind-address": "0.0.0.0",
    "rpc-enabled": false,
    "rpc-host-whitelist": "",
    "rpc-host-whitelist-enabled": true,
    "rpc-password": "{058bb85ed7643ed404181a05128a8b67ee63d10aPu/KbvkM",
    "rpc-port": 9091,
    "rpc-url": "/transmission/",
    "rpc-username": "",
    "rpc-whitelist": "127.0.0.1",
    "rpc-whitelist-enabled": true,
    "scrape-paused-torrents-enabled": true,
    "script-torrent-done-enabled": false,
    "script-torrent-done-filename": "/home/shan",
    "seed-queue-enabled": false,
    "seed-queue-size": 10,
    "show-backup-trackers": true,
    "show-extra-peer-details": false,
    "show-filterbar": true,
    "show-notification-area-icon": true,
    "show-options-window": true,
    "show-statusbar": true,
    "show-toolbar": true,
    "show-tracker-scrapes": true,
    "sort-mode": "sort-by-age",
    "sort-reversed": false,
    "speed-limit-down": 3000,
    "speed-limit-down-enabled": false,
    "speed-limit-up": 300,
    "speed-limit-up-enabled": true,
    "start-added-torrents": true,
    "statusbar-stats": "session-transfer",
    "torrent-added-notification-enabled": true,
    "torrent-complete-notification-enabled": true,
    "torrent-complete-sound-command": "canberra-gtk-play -i complete-download -d 'transmission torrent downloaded'",
    "torrent-complete-sound-enabled": true,
    "trash-can-enabled": true,
    "trash-original-torrent-files": false,
    "umask": 18,
    "upload-slots-per-torrent": 14,
    "user-has-given-informed-consent": true,
    "utp-enabled": true,
    "watch-dir": "/home/shan/Downloads",
    "watch-dir-enabled": false
}



```[COLOR=#000000]

[I][B]unless it is
[/B][/I]
[/COLOR]```
**"umask" parameter**

[COLOR=#333333][FONT=Ubuntu]You will also have to set the "umask" parameter in Transmission&#8217;s settings file to &#8220;2&#8221; (default is 18) for the account user to have full access to files/folders created by Transmission.[/FONT][/COLOR]
 [COLOR=#333333][FONT=UbuntuMono]"umask": 2,[/FONT][/COLOR]
```[COLOR=#000000]

which i have done so maybe i can omit [/COLOR]```
[COLOR=#000000][FONT=&amp]uid=shan,gid=shantrans[/FONT][/COLOR]
``` ???    not sure[COLOR=#000000]
[/COLOR][COLOR=#000000]

[/COLOR]

---

### Post by TheFu on 2023-01-14
Feel free to ignore me. Good luck.

---

