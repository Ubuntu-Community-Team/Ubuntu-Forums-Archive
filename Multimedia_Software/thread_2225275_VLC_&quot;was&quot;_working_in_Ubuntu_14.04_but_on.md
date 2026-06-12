---
title: "VLC &quot;was&quot; working in Ubuntu 14.04 but only for one DVD ..."
date: 2014-05-20
forum: Multimedia Software
---

### Post by J Tinsby on 2014-05-20
Hello,


I installed VLC player and tried to play a DVD and of course it wouldn't play. So I installed all the libraries that were recommended and ran the command to see how my 2 DVD burners were listed. I found one at /dev/sr0 and the other at /dev/sr1 So I polnted VLC at sr0 and after a reboot it played fine.

Now when I try and run VLC, the icon for it on the dock simply pulsates and the program doesn't open. If I reboot it will play a DVD but only once then I have to reboot again so it will play again!

The commands to show if the libraries are installed shows they are where they need to be.

Did a remove and re-install and rebooted immediately. This time when I inserted a DVD I was asked what program I wanted to use to always open that type of file.  But sadly it's back to the way it was originally. IE: The program won't open and the icon pulsates and it won't play the same DVD a second time. I get no notice on screen that a DVD has been inserted in the player. Sorry I misspoke: the problem persists!! :(

This morning from a cold boot, I insert another DVD and VLC opened automatically and played it as it should do. Once that DVD was taken out of the tray and re-inserted, VLC would not open automatically, nor could I get the DVD to play by choosing the drive and using the "open disc" command.


Thanks,

J T

---

### Post by ian-weisser on 2014-05-23
Are your devices really in ALL CAPS? That's very unusual.
Where did you install VLC from? Software Center? VLC website? Random internet link?
What were the 'recommended libraries' you installed? Who recommended them?

Insert an audio CD, open a terminal and try the following command. Please post all terminal output here.
```
$ vlc cdda:///dev/cdrom
```

For example, here's what happens when I use that command to successfully play an audio CD. Note the info messages, the warning, and the stream error that VLC successfully recovered from:
```
$ vlc cdda:///dev/cdrom
VLC media player 2.0.8 Twoflower (revision 2.0.8a-0-g68cf50b)
[0x8cef908] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
"sni-qt/23403" WARN  11:35:55.788 void StatusNotifierItemFactory::connectToSnw() Invalid interface to SNW_SERVICE 
[0x8cff090] main playlist: stopping playback
[0xb4535e68] main stream error: cannot pre fill buffer
$ 
```

---

### Post by J Tinsby on 2014-05-23
> **ian-weisser said:**
> Are your devices really in ALL CAPS? That's very unusual.
Where did you install VLC from? Software Center? VLC website? Random internet link?
What were the 'recommended libraries' you installed? Who recommended them?

Insert an audio CD, open a terminal and try the following command. Please post all terminal output here.
```
$ vlc cdda:///dev/cdrom
```

For example, here's what happens when I use that command to successfully play an audio CD. Note the info messages, the warning, and the stream error that VLC successfully recovered from:
```
$ vlc cdda:///dev/cdrom
VLC media player 2.0.8 Twoflower (revision 2.0.8a-0-g68cf50b)
[0x8cef908] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
"sni-qt/23403" WARN  11:35:55.788 void StatusNotifierItemFactory::connectToSnw() Invalid interface to SNW_SERVICE 
[0x8cff090] main playlist: stopping playback
[0xb4535e68] main stream error: cannot pre fill buffer
$ 
```

Hello Ian,

Thank you for responding!

No my drives aren't in caps I realize that caps are shouting, and I'm not shouting at anything except VLC right now! 

NB: I am not using both drives when I am testing, I am only using the  one drive continuously to avoid further compounding the problem.

Here are the libraries I installed I got them from a link in this forum that pertained to a VLC problem with Lubuntu.I used the software center to get VLC and the libraries as I recall.

I have installed libdvdread4 & libdvdnav4 and then ran the command sudo /usr/share/doc/libdvdread4/install-css.sh 

When I put an audio CD into the one of two drives I have VLC popped open and said :  [COLOR=#ff0000]Your input can't be opened:[/COLOR]
 [COLOR=#000000]VLC is unable to open the MRL 'cdda:///dev/cdrom'. Check the log for details.[/COLOR]


Your terminal command rendered this:

tinsby@THISDARNUBUNTU:~$ vlc cdda:///dev/cdrom
VLC media player 2.1.4 Rincewind (revision 2.1.4-0-g2a072be)
[0xeb8118] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0x7f41e0001048] cdda access error: could not read TOCHDR
[0x7f41e0001048] cdda access error: no audio tracks found
[0x7f41dc0009b8] main input error: open of `cdda:///dev/cdrom' failed
Your input can't be opened:
VLC is unable to open the MRL 'cdda:///dev/cdrom'. Check the log for details.

But then Ubuntu started asking me what program I wanted to use to play the CD! I chose to cancel and didn't choose VLC or anything else.

I defer to your knowledge about Linux and it's foibles,. But in spite of the message in VLC it seems to me that the drive is being recognized, I say that only because *immediately after a reboot*, VLC will play a DVD or CD with no trouble at all. Odd thing is you can only do it once per boot up. After that it does nothing! Suffice it to say that everything works fine in the MS OS's I have.

As odd as it may seem I can repeatedly insert an audio CD and be prompted by the OS to tell it what program to use to play it. Conversely after using the CD I tried a DVD and it did nothing. hth you in some way.

Looking forward to your thoughts on this and thank you again.

J T

---

### Post by J Tinsby on 2014-05-29
Can someone please explain why I see 5 CD drives listed? Is this what is confusing the VLC player or SMPlayer? VLC plays once, smplayer does nothing.

I see sr0 sg1 sg2 sr0 sr1 in the list below, yes I have 2 DVD drives but no matter which one of these 5 I choose, none will work more than one time.

Seems no one has a clue, least of all me. I only added this information to help someone more knowledgeable than I to help sort this out. Should I not pay attention to all the others that are listed after lrwxrwxrwx   1 root root           3 May 29 19:34 cdrom -> sr0 ?

Now doing an 
sudo lshw command tells me that sr0 is my Sony dvd and sr1 is the LiteOn drive.

 *-cdrom:0
             description: DVD writer
             product: DVD RW DW-U10A
             vendor: SONY
             physical id: 0.0.0
             bus info: scsi@5:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: 1.1d
             serial: [
             capabilities: removable audio cd-r cd-rw dvd dvd-r
             configuration: ansiversion=5 status=nodisc
        *-cdrom:1
             description: DVD-RAM writer
             product: iHAP322   9
             vendor: ATAPI
             physical id: 0.1.0
             bus info: scsi@5:0.1.0
             logical name: /dev/sr1
             version: 6L1C
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
     *-scsi:2
Right now VLC and SMplayer have been removed from the OS out of frustration I guess :/ 

thanks to all in advance

J T


tinsby@THISDARNUBUNTU:~$  cd /dev; ls -la
total 4
drwxr-xr-x  16 root root        4420 May 29 19:34 .
drwxr-xr-x  24 root root        4096 May 28 16:52 ..
crw-------   1 root root     10, 235 May 29 19:34 autofs
drwxr-xr-x   2 root root         820 May 29 19:34 block
drwxr-xr-x   2 root root         180 May 29 15:34 bsg
crw-------   1 root root     10, 234 May 29 19:34 btrfs-control
drwxr-xr-x   3 root root          60 May 29 15:34 bus
lrwxrwxrwx   1 root root           3 May 29 19:34 cdrom -> sr0
drwxr-xr-x   2 root root        3940 May 29 19:34 char
crw-------   1 root root      5,   1 May 29 19:34 console
lrwxrwxrwx   1 root root          11 May 29 15:34 core -> /proc/kcore
drwxr-xr-x   2 root root          60 May 29 15:34 cpu
crw-------   1 root root     10,  60 May 29 19:34 cpu_dma_latency
crw-------   1 root root     10, 203 May 29 19:34 cuse
drwxr-xr-x   6 root root         120 May 29 19:34 disk
drwxr-xr-x   2 root root          60 May 29 19:34 dri
crw-------   1 root root     10,  61 May 29 19:34 ecryptfs
lrwxrwxrwx   1 root root          13 May 29 15:34 fd -> /proc/self/fd
brw-rw----   1 root floppy    2,   0 May 29 19:34 fd0
crw-rw-rw-   1 root root      1,   7 May 29 19:34 full
crw-rw-rw-   1 root root     10, 229 May 29 19:34 fuse
crw-------   1 root root    251,   0 May 29 19:34 fw0
crw-------   1 root root    250,   0 May 29 19:34 hidraw0
crw-------   1 root root     10, 228 May 29 19:34 hpet
lrwxrwxrwx   1 root root          14 May 29 15:34 .initramfs -> /run/initramfsfre
drwxr-xr-x   4 root root         360 May 29 19:34 input
crw-r--r--   1 root root      1,  11 May 29 19:34 kmsg
crw-rw----+  1 root root     10, 232 May 29 19:34 kvm
srw-rw-rw-   1 root root           0 May 29 19:34 log
brw-rw----   1 root disk      7,   0 May 29 19:34 loop0
brw-rw----   1 root disk      7,   1 May 29 19:34 loop1
brw-rw----   1 root disk      7,   2 May 29 19:34 loop2
brw-rw----   1 root disk      7,   3 May 29 19:34 loop3
brw-rw----   1 root disk      7,   4 May 29 19:34 loop4
brw-rw----   1 root disk      7,   5 May 29 19:34 loop5
brw-rw----   1 root disk      7,   6 May 29 19:34 loop6
brw-rw----   1 root disk      7,   7 May 29 19:34 loop7
crw-------   1 root root     10, 237 May 29 19:34 loop-control
drwxr-xr-x   2 root root          60 May 29 15:34 mapper
crw-------   1 root root     10, 227 May 29 19:34 mcelog
crw-r-----   1 root kmem      1,   1 May 29 19:34 mem
drwxr-xr-x   2 root root          60 May 29 15:34 net
crw-------   1 root root     10,  59 May 29 19:34 network_latency
crw-------   1 root root     10,  58 May 29 19:34 network_throughput
crw-rw-rw-   1 root root      1,   3 May 29 19:34 null
crw-rw-rw-   1 root root    195,   0 May 29 19:34 nvidia0
crw-rw-rw-   1 root root    195, 255 May 29 19:34 nvidiactl
crw-r-----   1 root kmem      1,   4 May 29 19:34 port
crw-------   1 root root    108,   0 May 29 19:34 ppp
crw-------   1 root root     10,   1 May 29 19:34 psaux
crw-rw-rw-   1 root tty       5,   2 May 29 19:47 ptmx
drwxr-xr-x   2 root root           0 May 29 15:34 pts
brw-rw----   1 root disk      1,   0 May 29 19:34 ram0
brw-rw----   1 root disk      1,   1 May 29 19:34 ram1
brw-rw----   1 root disk      1,  10 May 29 19:34 ram10
brw-rw----   1 root disk      1,  11 May 29 19:34 ram11
brw-rw----   1 root disk      1,  12 May 29 19:34 ram12
brw-rw----   1 root disk      1,  13 May 29 19:34 ram13
brw-rw----   1 root disk      1,  14 May 29 19:34 ram14
brw-rw----   1 root disk      1,  15 May 29 19:34 ram15
brw-rw----   1 root disk      1,   2 May 29 19:34 ram2
brw-rw----   1 root disk      1,   3 May 29 19:34 ram3
brw-rw----   1 root disk      1,   4 May 29 19:34 ram4
brw-rw----   1 root disk      1,   5 May 29 19:34 ram5
brw-rw----   1 root disk      1,   6 May 29 19:34 ram6
brw-rw----   1 root disk      1,   7 May 29 19:34 ram7
brw-rw----   1 root disk      1,   8 May 29 19:34 ram8
brw-rw----   1 root disk      1,   9 May 29 19:34 ram9
crw-rw-rw-   1 root root      1,   8 May 29 19:34 random
crw-rw-r--+  1 root root     10,  62 May 29 19:34 rfkill
lrwxrwxrwx   1 root root           4 May 29 19:34 rtc -> rtc0
crw-------   1 root root    254,   0 May 29 19:34 rtc0
brw-rw----   1 root disk      8,   0 May 29 19:34 sda
brw-rw----   1 root disk      8,   1 May 29 19:34 sda1
brw-rw----   1 root disk      8,   2 May 29 19:34 sda2
brw-rw----   1 root disk      8,   3 May 29 19:34 sda3
brw-rw----   1 root disk      8,   4 May 29 19:34 sda4
brw-rw----   1 root disk      8,   5 May 29 19:34 sda5
brw-rw----   1 root disk      8,   6 May 29 19:34 sda6
brw-rw----   1 root disk      8,   7 May 29 19:34 sda7
brw-rw----   1 root disk      8,  16 May 29 19:34 sdb
brw-rw----   1 root disk      8,  32 May 29 19:34 sdc
brw-rw----   1 root disk      8,  48 May 29 19:34 sdd
brw-rw----   1 root disk      8,  64 May 29 19:34 sde
crw-rw----   1 root disk     21,   0 May 29 19:34 sg0
crw-rw----+  1 root cdrom    21,   1 May 29 19:34 sg1
crw-rw----+  1 root cdrom    21,   2 May 29 19:34 sg2
crw-rw----   1 root disk     21,   3 May 29 19:34 sg3
crw-rw----   1 root disk     21,   4 May 29 19:34 sg4
crw-rw----   1 root disk     21,   5 May 29 19:34 sg5
crw-rw----   1 root disk     21,   6 May 29 19:34 sg6
lrwxrwxrwx   1 root root           8 May 29 19:34 shm -> /run/shm
crw-------   1 root root     10, 231 May 29 19:34 snapshot
drwxr-xr-x   3 root root         240 May 29 19:34 snd
brw-rw----+  1 root cdrom    11,   0 May 29 19:34 sr0
brw-rw----+  1 root cdrom    11,   1 May 29 19:38 sr1
lrwxrwxrwx   1 root root          15 May 29 15:34 stderr -> /proc/self/fd/2
lrwxrwxrwx   1 root root          15 May 29 15:34 stdin -> /proc/self/fd/0
lrwxrwxrwx   1 root root          15 May 29 15:34 stdout -> /proc/self/fd/1
crw-rw-rw-   1 root tty       5,   0 May 29 19:44 tty
crw--w----   1 root tty       4,   0 May 29 19:34 tty0
crw-rw----   1 root tty       4,   1 May 29 19:34 tty1
crw--w----   1 root tty       4,  10 May 29 19:34 tty10
crw--w----   1 root tty       4,  11 May 29 19:34 tty11
crw--w----   1 root tty       4,  12 May 29 19:34 tty12
crw--w----   1 root tty       4,  13 May 29 19:34 tty13
crw--w----   1 root tty       4,  14 May 29 19:34 tty14
crw--w----   1 root tty       4,  15 May 29 19:34 tty15
crw--w----   1 root tty       4,  16 May 29 19:34 tty16
crw--w----   1 root tty       4,  17 May 29 19:34 tty17
crw--w----   1 root tty       4,  18 May 29 19:34 tty18
crw--w----   1 root tty       4,  19 May 29 19:34 tty19
crw-rw----   1 root tty       4,   2 May 29 19:34 tty2
crw--w----   1 root tty       4,  20 May 29 19:34 tty20
crw--w----   1 root tty       4,  21 May 29 19:34 tty21
crw--w----   1 root tty       4,  22 May 29 19:34 tty22
crw--w----   1 root tty       4,  23 May 29 19:34 tty23
crw--w----   1 root tty       4,  24 May 29 19:34 tty24
crw--w----   1 root tty       4,  25 May 29 19:34 tty25
crw--w----   1 root tty       4,  26 May 29 19:34 tty26
crw--w----   1 root tty       4,  27 May 29 19:34 tty27
crw--w----   1 root tty       4,  28 May 29 19:34 tty28
crw--w----   1 root tty       4,  29 May 29 19:34 tty29
crw-rw----   1 root tty       4,   3 May 29 19:34 tty3
crw--w----   1 root tty       4,  30 May 29 19:34 tty30
crw--w----   1 root tty       4,  31 May 29 19:34 tty31
crw--w----   1 root tty       4,  32 May 29 19:34 tty32
crw--w----   1 root tty       4,  33 May 29 19:34 tty33
crw--w----   1 root tty       4,  34 May 29 19:34 tty34
crw--w----   1 root tty       4,  35 May 29 19:34 tty35
crw--w----   1 root tty       4,  36 May 29 19:34 tty36
crw--w----   1 root tty       4,  37 May 29 19:34 tty37
crw--w----   1 root tty       4,  38 May 29 19:34 tty38
crw--w----   1 root tty       4,  39 May 29 19:34 tty39
crw-rw----   1 root tty       4,   4 May 29 19:34 tty4
crw--w----   1 root tty       4,  40 May 29 19:34 tty40
crw--w----   1 root tty       4,  41 May 29 19:34 tty41
crw--w----   1 root tty       4,  42 May 29 19:34 tty42
crw--w----   1 root tty       4,  43 May 29 19:34 tty43
crw--w----   1 root tty       4,  44 May 29 19:34 tty44
crw--w----   1 root tty       4,  45 May 29 19:34 tty45
crw--w----   1 root tty       4,  46 May 29 19:34 tty46
crw--w----   1 root tty       4,  47 May 29 19:34 tty47
crw--w----   1 root tty       4,  48 May 29 19:34 tty48
crw--w----   1 root tty       4,  49 May 29 19:34 tty49
crw-rw----   1 root tty       4,   5 May 29 19:34 tty5
crw--w----   1 root tty       4,  50 May 29 19:34 tty50
crw--w----   1 root tty       4,  51 May 29 19:34 tty51
crw--w----   1 root tty       4,  52 May 29 19:34 tty52
crw--w----   1 root tty       4,  53 May 29 19:34 tty53
crw--w----   1 root tty       4,  54 May 29 19:34 tty54
crw--w----   1 root tty       4,  55 May 29 19:34 tty55
crw--w----   1 root tty       4,  56 May 29 19:34 tty56
crw--w----   1 root tty       4,  57 May 29 19:34 tty57
crw--w----   1 root tty       4,  58 May 29 19:34 tty58
crw--w----   1 root tty       4,  59 May 29 19:34 tty59
crw-rw----   1 root tty       4,   6 May 29 19:34 tty6
crw--w----   1 root tty       4,  60 May 29 19:34 tty60
crw--w----   1 root tty       4,  61 May 29 19:34 tty61
crw--w----   1 root tty       4,  62 May 29 19:34 tty62
crw--w----   1 root tty       4,  63 May 29 19:34 tty63
crw--w----   1 root tty       4,   7 May 29 19:34 tty7
crw--w----   1 root tty       4,   8 May 29 19:34 tty8
crw--w----   1 root tty       4,   9 May 29 19:34 tty9
crw-------   1 root root      5,   3 May 29 19:34 ttyprintk
crw-rw----   1 root dialout   4,  64 May 29 19:34 ttyS0
crw-rw----   1 root dialout   4,  65 May 29 19:34 ttyS1
crw-rw----   1 root dialout   4,  74 May 29 19:34 ttyS10
crw-rw----   1 root dialout   4,  75 May 29 19:34 ttyS11
crw-rw----   1 root dialout   4,  76 May 29 19:34 ttyS12
crw-rw----   1 root dialout   4,  77 May 29 19:34 ttyS13
crw-rw----   1 root dialout   4,  78 May 29 19:34 ttyS14
crw-rw----   1 root dialout   4,  79 May 29 19:34 ttyS15
crw-rw----   1 root dialout   4,  80 May 29 19:34 ttyS16
crw-rw----   1 root dialout   4,  81 May 29 19:34 ttyS17
crw-rw----   1 root dialout   4,  82 May 29 19:34 ttyS18
crw-rw----   1 root dialout   4,  83 May 29 19:34 ttyS19
crw-rw----   1 root dialout   4,  66 May 29 19:34 ttyS2
crw-rw----   1 root dialout   4,  84 May 29 19:34 ttyS20
crw-rw----   1 root dialout   4,  85 May 29 19:34 ttyS21
crw-rw----   1 root dialout   4,  86 May 29 19:34 ttyS22
crw-rw----   1 root dialout   4,  87 May 29 19:34 ttyS23
crw-rw----   1 root dialout   4,  88 May 29 19:34 ttyS24
crw-rw----   1 root dialout   4,  89 May 29 19:34 ttyS25
crw-rw----   1 root dialout   4,  90 May 29 19:34 ttyS26
crw-rw----   1 root dialout   4,  91 May 29 19:34 ttyS27
crw-rw----   1 root dialout   4,  92 May 29 19:34 ttyS28
crw-rw----   1 root dialout   4,  93 May 29 19:34 ttyS29
crw-rw----   1 root dialout   4,  67 May 29 19:34 ttyS3
crw-rw----   1 root dialout   4,  94 May 29 19:34 ttyS30
crw-rw----   1 root dialout   4,  95 May 29 19:34 ttyS31
crw-rw----   1 root dialout   4,  68 May 29 19:34 ttyS4
crw-rw----   1 root dialout   4,  69 May 29 19:34 ttyS5
crw-rw----   1 root dialout   4,  70 May 29 19:34 ttyS6
crw-rw----   1 root dialout   4,  71 May 29 19:34 ttyS7
crw-rw----   1 root dialout   4,  72 May 29 19:34 ttyS8
crw-rw----   1 root dialout   4,  73 May 29 19:34 ttyS9
drwxr-xr-x   3 root root          60 May 29 19:34 .udev
crw-------   1 root root     10, 239 May 29 19:34 uhid
crw-------   1 root root     10, 223 May 29 19:34 uinput
crw-rw-rw-   1 root root      1,   9 May 29 19:34 urandomfre
drwxr-xr-x   2 root root          60 May 29 19:34 usb
crw-rw----   1 root tty       7,   0 May 29 19:34 vcs
crw-rw----   1 root tty       7,   1 May 29 19:34 vcs1
crw-rw----   1 root tty       7,   2 May 29 19:34 vcs2
crw-rw----   1 root tty       7,   3 May 29 19:34 vcs3
crw-rw----   1 root tty       7,   4 May 29 19:34 vcs4
crw-rw----   1 root tty       7,   5 May 29 19:34 vcs5
crw-rw----   1 root tty       7,   6 May 29 19:34 vcs6
crw-rw----   1 root tty       7,   7 May 29 19:34 vcs7
crw-rw----   1 root tty       7, 128 May 29 19:34 vcsa
crw-rw----   1 root tty       7, 129 May 29 19:34 vcsa1
crw-rw----   1 root tty       7, 130 May 29 19:34 vcsa2
crw-rw----   1 root tty       7, 131 May 29 19:34 vcsa3
crw-rw----   1 root tty       7, 132 May 29 19:34 vcsa4
crw-rw----   1 root tty       7, 133 May 29 19:34 vcsa5
crw-rw----   1 root tty       7, 134 May 29 19:34 vcsa6
crw-rw----   1 root tty       7, 135 May 29 19:34 vcsa7
crw-------   1 root root     10,  63 May 29 19:34 vga_arbiter
crw-------   1 root root     10, 238 May 29 19:34 vhost-net
crw-rw-rw-   1 root root      1,   5 May 29 19:34 zero
fred@THISDARNUBUNTU:/dev$

---

### Post by mc4man on 2014-05-30
If inclined to pursue - 
Seeing as it works fine once per boot I'd look at what happens after that first play as obviously all is well for the first play.

As far as vlc - it defaults to /dev/cdrom (Sony drive) though from autoplay it should use either. From command line or Media > Open disc  you need to pick the correct drive, /dev/sr0 for sony or /dev/sr1 for  iHAP322 9

I'd ck. by doing a fresh boot, play a dvd, then *eject properly* from either nautilus sidebar or Unity launcher. 
Then insert another dvd, after the drive settles run sudo lshw -C disk & see if the filesystem on the dvd (udf) has been mounted
(- while playback of a dvd with an unmounted filesystem is possible it's better for troubleshooting if it is 

You should see something similar to this in *-cdrom section  - 
> configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,umask=77,iocharset=utf8 state=mounted status=ready

---

### Post by VMC on 2014-05-31
[COLOR=#DD4814][COLOR=#000000]J Tinsby,
Try it from the command line and observe the outputs. First find the correct disk:
```
lsblk
``` output show reflect the correct name. Mine is 'sr0'.
So using the terminal:
[/COLOR][/COLOR]```
**cvlc dvd://sr0**
```

Should show something on this order:

```
libdvdnav: Using dvdnav version 4.2.1
libdvdread: Encrypted DVD support unavailable.
************************************************
**                                            **
**  No css library available. See             **
**  /usr/share/doc/libdvdread4/README.css     **
**  for more information.                     **
**                                            **
************************************************
libdvdnav: DVD Title: JACK_REACHER
libdvdnav: DVD Serial Number: 52268BF300000000
libdvdnav: DVD Title (Alternative): 
...

```

If your movie plays the first time, do it again from the terminal, and see if you have different outputs/errors.

---

### Post by J Tinsby on 2014-06-12
Hi mc4man,

Sorry didn't get back here sooner I had to remove ubuntu and start over again, had no backup to install <sigh>

Anyway I now have the same libaries installed and have run the command for restricted files.

Please note that at present I have not re-installed vlc but was experimenting with the 'videos' player that come with ubuntu. I have found the following"

1/ Just like vlc, the 'videos' player will play a dvd just fine one time only.
2/ Upon ejecting the disc using the dvd icon and closing the tray, I can't open the tray again the button won't respond it is effectively locked! Vlc nevef did that, this is new.
3/ Trying the second drive the result is the same as in vlc, IE: the 'videos' player won't open a second time.
4/ Like when using vlc a reboot will allow a one time play of the dvd.

I ran the command you suggested and got this:

*-cdrom:0
       description: DVD writer
       product: DVD RW DW-U10A
       vendor: SONY
       physical id: 0.0.0
       bus info: scsi@5:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/sr0
       version: 1.1d
       serial: [
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 status=nodisc
  *-cdrom:1
       description: DVD-RAM writer
       product: iHAP322   9
       vendor: ATAPI
       physical id: 0.1.0
       bus info: scsi@5:0.1.0
       logical name: /dev/sr1
       logical name: /media/fred/PHANTOM_OF_THE_OPERA_DISK_2
       version: 6L1C
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,umask=77,iocharset=utf8 state=mounted status=nodisc


NB: I find it interesting, if not maddening, that the  /media/fred/PHANTOM_OF_THE_OPERA_DISK_2 line is there..... because the disc was NOT in the tray at the time I ran your command string. Yes I see that it says status=nodisc but why save the title of what isn't there?

 vlc used to do the same thing, if I got it to open a second time, the name of the previous disc was displayed in the vlc menu bar, not the disc I was trying to play. Maybe it's supposed to be held in memory but I wouln't know why. Also the dvd icon in the launcher remains in the open position even though the tray is closed. I have to manually unlook it from the launcher.

I have no other players like SMplayer installed. I need vlc for other formats as well as dvd's, I listen to streaming media that comes in the form of a .pls file. Vlc will play that just fine in windows 7 or even xp.

I am very appreciative for your and VMC's help and anyone elses, I am determined to figure this out before I go further into ubuntu.

Regards and thanks!

J T

---

### Post by J Tinsby on 2014-06-12
Hi VMC,

Thank you for the information you kindly posted for me.

If you read my reply to mc4man you will see where I am now and what's going on, maybe it will help get this thing sorted. Right now since I have no vlc player installed of course I can't use your last command. I am having similar trouble with the Totem player that comes with ubuntu. If that isn't going to work correctly there is little hope of vlc ever working.

I will be happy to re-install vlc if necessary but when I can only play a dvd one time with the most basic player, a re-install of vlc may not prove anything.

You all know far more about linux than I, sorry I can't be of more help with this annoying problem.

Cheers and look forward to hearing your ideas as well as anyone else's.

J T

---

### Post by J Tinsby on 2014-06-19
> **mc4man said:**
> If inclined to pursue - 
Seeing as it works fine once per boot I'd look at what happens after that first play as obviously all is well for the first play.

As far as vlc - it defaults to /dev/cdrom (Sony drive) though from autoplay it should use either. From command line or Media > Open disc  you need to pick the correct drive, /dev/sr0 for sony or /dev/sr1 for  iHAP322 9

I'd ck. by doing a fresh boot, play a dvd, then *eject properly* from either nautilus sidebar or Unity launcher. 
Then insert another dvd, after the drive settles run sudo lshw -C disk & see if the filesystem on the dvd (udf) has been mounted
(- while playback of a dvd with an unmounted filesystem is possible it's better for troubleshooting if it is 

You should see something similar to this in *-cdrom section  -

mc4man,

Sorry for the delay in replying to your instructions.

I re-installed vlc player and tried your command of sudo lshw -C disk, this is what I got:

 *-cdrom:1
       description: DVD-RAM writer
       product: iHAP322   9
       vendor: ATAPI
       physical id: 0.1.0
       bus info: scsi@5:0.1.0
       logical name: /dev/sr1
       logical name: /media/fred/Punisher_EC
       version: 6L1C
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,umask=77,iocharset=utf8 state=mounted status=ready

I got the same message from the default CD ROM /sr0 and it gave me the choice when I inserted the disc what to use to play it. Of course I chose vlc. Then I used the launcher and ejected the disc and tried it again. Of course the tray was locked!

 So I then tried to use the /sr1 drive with another disc, and I was again given the choice of what program to play the dvd with, and again I chose vlc and it opened and played the dvd.. Note that I used 2 dvd's not the same one over and over for the test.

Now able to re insert the SAME disc over and over into sr1 and each time I get the prompt asking what to play it with etc. However sr0's tray remains locked. What changed to allow me to do this I have no idea. 

Wanted to let you know where I am in the process! No idea though how to unlock the /dev/s0 drive or why it locks to begin with.

Cheers!

---

### Post by J Tinsby on 2014-06-19
> **J Tinsby said:**
> 

I see sr0 sr1 in the list below, yes I have 2 DVD drives but no matter which one of these 2 I choose, none will work more than one time.

Seems no one has a clue, least of all me. I only added this information to help someone more knowledgeable than I to help sort this out. Should I not pay attention to all the others that are listed after lrwxrwxrwx   1 root root           3 May 29 19:34 cdrom -> sr0 ?

Now doing an 
sudo lshw command tells me that sr0 is my Sony dvd and sr1 is the LiteOn drive.

 *-cdrom:0
             description: DVD writer
             product: DVD RW DW-U10A
             vendor: SONY
             physical id: 0.0.0
             bus info: scsi@5:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: 1.1d
             serial: [
             capabilities: removable audio cd-r cd-rw dvd dvd-r
             configuration: ansiversion=5 status=nodisc
        *-cdrom:1
             description: DVD-RAM writer
             product: iHAP322   9
             vendor: ATAPI
             physical id: 0.1.0
             bus info: scsi@5:0.1.0
             logical name: /dev/sr1
             version: 6L1C
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
     *-scsi:2


thanks to all in advance



J T

<< post edited for brevity>>

---

### Post by Yellow Pasque on 2014-06-19
I would try playing with 'eject -v' command when tray is locked and see what output that gives you.

---

### Post by J Tinsby on 2014-06-20
> **Temüjin said:**
> I would try playing with 'eject -v' command when tray is locked and see what output that gives you.

HI Temujin,

Here's what I get when I use that command:

fred@fred-CAUS:~$ sudo eject -v
[sudo] password for fred: 
eject: using default device `cdrom'
eject: device name is `cdrom'
eject: expanded name is `/dev/cdrom'
eject: `/dev/cdrom' is a link to `/dev/sr0'
eject: `/dev/sr0' is not mounted
eject: `/dev/sr0' is not a mount point
eject: `/dev/sr0' is not a multipartition device
eject: trying to eject `/dev/sr0' using CD-ROM eject command
eject: CD-ROM eject command failed
eject: trying to eject `/dev/sr0' using SCSI commands
eject: SCSI eject failed
eject: trying to eject `/dev/sr0' using floppy eject command
eject: floppy eject command failed
eject: trying to eject `/dev/sr0' using tape offline command
eject: tape offline command failed
eject: unable to eject, last error: Inappropriate ioctl for device

However I can use /dev/sr1 over and over again with a DVD or audio CD and it never is locked. The screenshot makes it sound like Ubuntu see's the drives mounted on top of each other, or that's the way I read it.

Please see the screenshot that I get when I run the command: 

lshw -C disk

Thank you for your interest in my problem! 

Cheers! J T

---

### Post by mc4man on 2014-06-20
I no longer have a desktop machine with 2 dvd drives so really can't compare some things. But maybe some others do...

Would be interesting to know if sudo lshw -C  disk under the *-cdrom:1 section only shows 1 logical drive (/dev/sr1) or also has something like /dev/cdrom1
(I'm inclined to think only the 1 vs. *-cdrom:0 which has 2 logical drives (/dev/sr0 & /dev/cdrom

Also in this file are there 2 KERNEL== lines or just 1?, eg. KERNEL=="sr0", SYMLINK+="cdrom", OPTIONS+="link_priority=-100"
```
cat  /lib/udev/rules.d/60-cdrom_id.rules
```

What happens if you turn off automounting of media, (other than autoplay won't work), can you use the sr0 drive multiple times?
```
gsettings set org.gnome.desktop.media-handling automount false
```

(- to reset back just go 
```
gsettings set org.gnome.desktop.media-handling automount true
```

I do have an external drive I can pick up tomorrow though it may not be the same as 2 internal...

Worst case if nothing else works (you may wish to wait for further info from ^
You could  try creating 2 mountpoints & setting each drive in fstab, whether there is a downside to this I currently can't say as haven't done so in some time.

Ex. - 
```
sudo mkdir /media/cdrom0 /media/cdrom1
```

Then add these 2 lines to bottom of /etc/fstab, save & restart
```
/dev/sr0  /media/cdrom0 udf,iso9660 user,noauto,exec    0  0
/dev/sr1  /media/cdrom1 udf,iso9660 user,noauto,exec    0  0
```

To revert just remove the 2 lines from fstab ( and the space they occupied) & remove the 2 folders in media

---

### Post by J Tinsby on 2014-06-21
Mc4man,

Here's what I come up with so far. The sudo lshw -C disk command yields this:

fred@fred-CAUS:~$ sudo lshw -C disk
[sudo] password for fred: 
  *-disk                  
       description: ATA Disk
       product: WDC WD6401AALS-0
       vendor: Western Digital
       physical id: 0.0.0
       bus info: scsi@1:0.0.0
       logical name: /dev/sda
       version: 01.0
       serial: WD-WCASY7603189
       size: 596GiB (640GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 sectorsize=512 signature=ef5bef5b
  *-cdrom:0
       description: DVD writer
       product: DVD RW DW-U10A
       vendor: SONY
       physical id: 0.0.0
       bus info: scsi@5:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/sr0
       version: 1.1d
       serial: [
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 status=nodisc
  *-cdrom:1
       description: DVD-RAM writer
       product: iHAP322   9
       vendor: ATAPI
       physical id: 0.1.0
       bus info: scsi@5:0.1.0
       logical name: /dev/sr1
       version: 6L1C
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=nodisc
  *-disk:0
       description: SCSI Disk
       product: USB   HS-CF Card
       vendor: Sony
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/sdb
       version: 3.95
       capabilities: removable
       configuration: sectorsize=512
     *-medium
          physical id: 0
          logical name: /dev/sdb
  *-disk:1
       description: SCSI Disk
       product: USB   HS-xD/SM
       vendor: Sony
       physical id: 0.0.1
       bus info: scsi@4:0.0.1
       logical name: /dev/sdc
       version: 3.95
       capabilities: removable
       configuration: sectorsize=512
     *-medium
          physical id: 0
          logical name: /dev/sdc
  *-disk:2
       description: SCSI Disk
       product: USB   HS-MS Card
       vendor: Sony
       physical id: 0.0.2
       bus info: scsi@4:0.0.2
       logical name: /dev/sdd
       version: 3.95
       serial: 3
       capabilities: removable
       configuration: sectorsize=512
     *-medium
          physical id: 0
          logical name: /dev/sdd
  *-disk:3
       description: SCSI Disk
       product: USB   HS-SD Card
       vendor: Sony
       physical id: 0.0.3
       bus info: scsi@4:0.0.3
       logical name: /dev/sde
       version: 3.95
       capabilities: removable
       configuration: sectorsize=512
     *-medium
          physical id: 0
          logical name: /dev/sde
fred@fred-CAUS:~$ 

Then I ran the other one and got this:

fred@fred-CAUS:~$ cat  /lib/udev/rules.d/60-cdrom_id.rules
# do not edit this file, it will be overwritten on update

ACTION=="remove", GOTO="cdrom_end"
SUBSYSTEM!="block", GOTO="cdrom_end"
KERNEL!="sr[0-9]*|xvd*", GOTO="cdrom_end"
ENV{DEVTYPE}!="disk", GOTO="cdrom_end"

# unconditionally tag device as CDROM
KERNEL=="sr[0-9]*", ENV{ID_CDROM}="1"

# media eject button pressed
ENV{DISK_EJECT_REQUEST}=="?*", RUN+="cdrom_id --eject-media $devnode", GOTO="cdrom_end"

# import device and media properties and lock tray to
# enable the receiving of media eject button events
IMPORT{program}="cdrom_id --lock-media $devnode"

KERNEL=="sr0", SYMLINK+="cdrom", OPTIONS+="link_priority=-100"

LABEL="cdrom_end"
fred@fred-CAUS:~$ 

Interesting to see that it mentions locking the drive...

If I disable the automount of the /sr0 it has no effect, one play and one eject and the drive is locked again. It is possible to play a DVD/CD many times in /dev/sr1 and it never locks the tray!

I also notice that now I have *no* prompt asking me what player to use  when I insert a DVD. The daemon for that option is enabled in System  Settings | Details |Removeable Media. I have tried setting the default player to VLC for DVD's but that won't work it doesn't open up when a disc is inserted.

If I go to the etc fstab folder, it's listed as fstab.d not just etc/fstab, I do not know if that makes a difference so I didn't go any further with it until I hear from you or temujin again, when you have the time of course.Currently that folder etc/fstab.d is devoid of any files or folders. So it's not clear when you say "add to the bottom," of that folder...



I'm in very unfamiliar territory with all of this, but it's sure a learning experience and I'm glad for all the help that's for sure :D

J T

---

### Post by J Tinsby on 2014-06-23
I found this link to a bug in Ubuntu :[https://bugs.launchpad.net/ubuntu/+source/devicekit-disks/+bug/397734](https://bugs.launchpad.net/ubuntu/+source/devicekit-disks/+bug/397734)

It references a line to add to the /etc/sysctl.d folder but it appears to be for a bug in ubuntu 9.10

The question is will it work on my machine? The line is 

# CD/DVD eject button doesn't work until /proc/sys/dev/cdrom/lock is 1

I can find the folder and use the terminal to log in as root but I still can't make a new folder to add to the /etc/sysctl.d folder

Maybe that's a good thing! Can't see how adding that line above will help in v 14.04 but I am trying anything to make it work.

Probably going about it all wrong but I am trying....

Thanks

---

### Post by mc4man on 2014-06-23
Just to clear up - your current situation is
1. the sr0 drive can play one dvd on fresh boot & then you are unable to play anymore dvd's because you can't eject that dvd.
2. the sr0 drive can play one dvd on fresh boot, you can eject that dvd but then no other dvd's will work without a reboot
3. some combination of the 2 above

---

### Post by J Tinsby on 2014-06-23
mc4man,

I can eject the sr0 disc but after that the tray is locked.
sr1 can repeatedly play and eject audio or dvd discs with no lockup of tray, but everything, IE: VLC, has to be started manually
A reboot makes sr0 available again, but for one play only.

Inserting a disc would give a popup window asking me "what do you want to use the play the media?" ( paraphrasing) I no longer get that window on inserting a CD or DVD. The daemon for the 'prompt on insert IS running, or at least the box for it isn't ticked. I think that "might" have been caused by an update that I did today to the OS. Not certain tho' would be nice to see that again....

I prefer not to have one player associated with a particular file type, I guess it's a holdover from MS, I do the same thing there usually.

Did you see the screenshot in my post #12 above? It makes it sound like both drives are mounted to the same space, causing it not to eject.

Regards, thanks very much, I appreciate your interest as I do all the others! Tough to take on someone else's troubles when you can't be there to have your hands on the box, so to speak. Trust me I know from experience! :D

J T

---

### Post by mc4man on 2014-06-23
Then I would try what I suggested about creating specific mountpoints for each drive & setting in fstab
Are you comfortable using nano as a root text editor? (or you can use  gedit  in one of 2 specific ways.

---

### Post by J Tinsby on 2014-06-24
> **mc4man said:**
> Then I would try what I suggested about creating specific mountpoints for each drive & setting in fstab
Are you comfortable using nano as a root text editor? (or you can use  gedit  in one of 2 specific ways.

I'll be glad to try whatever is the least cumbersome for you, gedit reminds me of Notepad, but I will try anything that will work!

It might be safer for me to use gedit.  I wanted to do what you suggested prior but wasn't sure if the folder /etc/fstab.d is the same as /etc/fstab as you referred to it. So that's where or why I stopped the process, I don't want to be editing the wrong file(s). Seems like a logical thing to have a mount point for each drive.

Plus you said " Then add these 2 lines to** bottom** of /etc/fstab, save & restart"      >>>>> Since the fstab.d folder is *empty* already I was confused when you said "bottom", so again went no further. I am taking all your advice literally, as you can see, so as to get it right.

     Code:
     /dev/sr0  /media/cdrom0 udf,iso9660 user,noauto,exec    0  0
/dev/sr1  /media/cdrom1 udf,iso9660 user,noauto,exec    0  0

Can I just paste those files into the fstab.d folder or must they be put in, in a certain way?

Thanks,

J T

---

### Post by mc4man on 2014-06-24
/etc/fstab is a file, not referring to /etc/fstab.d

Do a fresh boot with no media in any dvd drive.
open a terminal - 
```
sudo mkdir /media/cdrom0 /media/cdrom1
```
Make a backup of /etc/fstab just in case..
```
sudo cp /etc/fstab /etc/fstab.bak
```

When that is done in the terminal
```
sudo -H gedit /etc/fstab
```

In the gedit window that opens copy & paste this at bottom, directly below the last line 
```
/dev/sr0  /media/cdrom0 udf,iso9660 user,noauto,exec    0  0
/dev/sr1  /media/cdrom1 udf,iso9660 user,noauto,exec    0  0
```

look at screen to see how it should look, (this is my fstab, so lines above the added are different, highlighted is what you are adding

---

### Post by J Tinsby on 2014-06-24
> **mc4man said:**
> /etc/fstab is a file, not referring to /etc/fstab.d

Do a fresh boot with no media in any dvd drive.
open a terminal - 
```
sudo mkdir /media/cdrom0 /media/cdrom1
```
Make a backup of /etc/fstab just in case..
```
sudo cp /etc/fstab /etc/fstab.bak
```

When that is done in the terminal
```
sudo -H gedit /etc/fstab
```

In the gedit window that opens copy & paste this at bottom, directly below the last line 
```
/dev/sr0  /media/cdrom0 udf,iso9660 user,noauto,exec    0  0
/dev/sr1  /media/cdrom1 udf,iso9660 user,noauto,exec    0  0
```

look at screen to see how it should look, (this is my fstab, so lines above the added are different, highlighted is what you are adding

mc4man,

Did as you indicated, and it DID work for about 3 plays  of a dvd, then then sr0 was locked yet again, while sr1 remains  available. Sorry I thought you / we had it :( Of course I had to manually open VLC | Open Disc | sr0 to get it to play, there was no prompt asking me what to use to play the dvd, same as for sr1. Don't get me wrong I am not complaining, just wanted you to know how I got it to play.

I included a screenshot so you can see what I did.

I also tried to eject / open the tray using sudo eject /dvd/sr0 but got a message "fred@fred-CAUS:~$ eject: unable to eject, last error: Inappropriate ioctl for device"



Thanks so much!

J T

---

### Post by mc4man on 2014-06-24
then this sounds like a potential bug, (the locking of an unoccupied drive.
Unfortunetly I'm not in a position to explore it & confirm if overall or maybe something localized.
(- I'll try to remember to pick up that external tonight though as mentioned it may be treated differently than a 2nd internal

possible workaround - 
if you were *really* comfortable opening the pc case you could try swapping the mobo cables on the drives, then see if the issue switches to the now current sr1 drive.
Or it's possible that the current sr1 drive will be unaffected. 
(some drives will never be locked even when media is inserted

---

### Post by mc4man on 2014-06-24
With those fstab entries autoplay should work as long as that gsetting is set to true - 
```
gsettings set org.gnome.desktop.media-handling automount true
```

If desired you can reopen fstab & either remove those 2 lines plus the space they occupied or simply comment them out by placing a # a front of each line - ex

```
#/dev/sr0  /media/cdrom0 udf,iso9660 user,noauto,exec    0  0
#/dev/sr1  /media/cdrom1 udf,iso9660 user,noauto,exec    0  0
```

Or possibly as a test comment out just the /dev/sr0 line...

---

### Post by J Tinsby on 2014-06-25
> **mc4man said:**
> With those fstab entries autoplay should work as long as that gsetting is set to true - 
```
gsettings set org.gnome.desktop.media-handling automount true
```

If desired you can reopen fstab & either remove those 2 lines plus the space they occupied or simply comment them out by placing a # a front of each line - ex

```
#/dev/sr0  /media/cdrom0 udf,iso9660 user,noauto,exec    0  0
#/dev/sr1  /media/cdrom1 udf,iso9660 user,noauto,exec    0  0
```

Or possibly as a test comment out just the /dev/sr0 line...

No worries about opening the case, I built this machine as I do with all the ones I use. You are thinking just as I was IE: switch cables and see if the problem goes along with the change. I do know that the /sr0 drive is an old Sony, it may well be that there's no or little support for it for some reason.Really I thought it would have died years ago but it still keeps working! Lol. But then when lshw -C is run it accurately shows what the drive is. 

I added the line to make the on screen message come up when I insert a disc, that is now working again. Using the # to REM(ark) out a line reminds me of DOS...

In reality I don't have need for both drives anyway and I can be content to just use sr1 and forget sr0. There were times in windows when I was making a duplicate disc, I could copy from one to the other directly without copying the contents to the HD and then burning them back in the same burner.

I am of the opinion that the trouble we are wrestling with is machine specific and won't effect the majority of other users, although that remains to be seen I guess.

Let me know what happens if you get the external drive and see how it behaves. 

Regards and many thanks for your time and effort, it's most appreciated! 

J T

---

### Post by mc4man on 2014-06-25
It's been over 3 years since I had a desktop machine & how cd/dvd drives are handled has changed a lot, there used to a simple rules file where one could specify dev links ect.
(- plus I'd guess newer desktops may be using sata for dvd drives vs. the ata ribbon
One other thing comes to mind - 
Are you using a single ata cable for both drives & if so are they set to master/slave or cable-select?

---

### Post by J Tinsby on 2014-06-25
> **mc4man said:**
> It's been over 3 years since I had a desktop machine & how cd/dvd drives are handled has changed a lot, there used to a simple rules file where one could specify dev links ect.
(- plus I'd guess newer desktops may be using sata for dvd drives vs. the ata ribbon
One other thing comes to mind - 
Are you using a single ata cable for both drives & if so are they set to master/slave or cable-select?

I agree that the new ones have sata in most cases.

Thats a good question! The case I use has a clear side to it maybe I can peer in and have a look w/o taking the side off. But I need to disconnect all the cabling to let me move the box so I can see inside. Can't for the life of me remember what the config is. Both drives are IDE I can say that most likely with a ribbon, possibly shared between them. Don't remember if they are cable select, I 'think' I used that but maybe master & slave. Just been a while since I did anything inside the box, except add another HD. Wasn't fooling with Ubuntu or VLC then so I never had occasion to look at the optical drives. I know they aren't sata,  just the 2 HD's are and one of them isn't connected.

I'll get after it tomorrow!

Thanks!

J T

---

### Post by J Tinsby on 2014-06-27
mc4man,

Here's what I came up with today RE: the sr0 locking the tray on repeat plays:

I looked at the connections for the 2 drives. First they were connnected with one ribbon cable. The drives were both set to cable select. I thought of just switching the physical positions of the drives and plugging them back in, not changing the jumpers. Then I thought "what difference would that make?," You're not chaning anything really. So I changed the jumper on the former sr1 drive to 'master' and the former sr0 drive to "slave" and also put them in opposite spots in the case if for no other reason, the cable length worked better.

Now testing the drives I come up with the exact same problem! The Sony drive, now sr1, the slave, still locks the tray after one play of a dvd or cd. The LiteOn drive,sr0, continues to play discs repeatedly over and over, with no trouble. So at the end of the day I guess the answer is that the Sony drive is the culprit, irrespective of the reason. Handliy though for me the Sony is now the second one in the stack of two so I don't have to deal with it locking up!

Thanks for all you did, sorry to put you through all this, but I appreciate your kind attention to something that isn't effecting you in the least.

Regards and thanks again,

J T

---

