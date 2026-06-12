---
title: "Totem crashes when using an external screen"
date: 2006-12-28
forum: Multimedia &amp; Video
---

### Post by binneypl on 2006-12-28
I have a Toshiba notebook with a docking station, and am running 6.06.
I can play DVD's fine with totem using the notebook's screen.
When I dock the notebook and use the connected 20" LCD, totem crashes with:
```
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 101 error_code 11 request_code 141 minor_code 19)

```
I've scoured many postings which have lead me to try adding or changing the following
in my /etc/X11/xorg.conf, to no avail:

1. The two Option lines in:
```
Section "Device"
	Identifier	"S3 Inc. 86C270-294 Savage/IX-MV"
	Driver		"savage"
	BusID		"PCI:1:0:0"
	Option  "VideoRam"      "65536"
        Option  "CacheLines"    "1980"
EndSection
```

2. HorizSync and VertRefresh in:
```
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-81
	VertRefresh	56-75
EndSection
```

---

### Post by binneypl on 2007-03-25
Anyone any ideas on how to get this thing working??
Interestingly, the crash only occurs when playing DVD's.
Totem can play, for instance, a .mpg file fine.

---

### Post by M$LOL on 2007-04-04
First of all, you should install xine instead of gstreamer.

sudo apt-get install totem-xine

...should do the trick.
I could never play a dvd before I installed xine, now they work perfectly.

You should also install libdvdcss, [http://download.videolan.org/pub/libdvdcss]("http://download.videolan.org/pub/libdvdcss")

EDIT: I just saw that you could play them with the notebook's screen. I doubt if this has anything to do with gstreamer/xine, but you could try it anyway.

---

### Post by binneypl on 2007-04-13
Many thanks for the follow-up, but I'm afraid I already have the latest -xine.
The command you showed returned:
> totem-xine is already the newest version.

---

