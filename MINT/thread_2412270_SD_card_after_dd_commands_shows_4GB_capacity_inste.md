---
title: "SD card after dd commands shows 4GB capacity instead of 16 GB"
date: 2019-02-10
forum: MINT
---

### Post by deepakdeshp on 2019-02-10
[COLOR=#333333]I have an SD card , capacity 16 gb which had 3 partitions ,msdos 500MB , ext4 2gb and Ext4 12GB. After trying some dd commands which are required to write Raspbian, the card gave error**.**[/COLOR][COLOR=#333333][FONT=&amp]
*The location is outside of the device /dev/sdb*[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]. The 3rd partition is missing . I deleted all partitions and formatted both the partitions. The partition and the drive size shown is 4GB instead of the correct 16 GB[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]Any hints, help are welcome. Using Ubuntu 18.04[/FONT][/COLOR]

---

### Post by TheFu on 2019-02-11
Instead of describing what you see, please post real data. Use "code tags" so things are readable and line up.

**sudo fdisk -l**

And the exact dd command would be helpful.

If you wrote to the disk device /dev/sdb, then you over wrote the partition table.  If you wrote to an early partition more data than that partition could hold, it would over write the next partition too.  dd is dumb.  It writes the input data until either 1) the input ends, or 2) the output device is full and STOPS accepting data.

---

### Post by coffeecat on 2019-02-11
According to your post in the [link](https://forums.linuxmint.com/viewtopic.php?f=49&t=287760#) that you included in your post here, and then edited out, you are using Mint 19.1, not Ubuntu 18.04.

*Thread moved to the **MINT** sub-forum.*

I provide this link so that those helping here may see what advice you are being given on the Linux Mint forums. You might consider extending the same courtesy to the Linux Mint forum members.

---

