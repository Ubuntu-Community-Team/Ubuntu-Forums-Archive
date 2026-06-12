---
title: "Cannot Play DVDs in Karmic"
date: 2010-03-27
forum: Multimedia Software
---

### Post by clevertomato on 2010-03-27
I've tried everything I can find. On Karmic I have libdvdcss2 and libdvdread4 installed, along with VLC 1.0.2 and latest Mplayer. I also installed ubuntu-restricted-extras. Of the following DVDs


[LIST=1]
[*]Blazing Saddles
[*]Christmas Vacation
[*]It's a Wonderful Life
[*]So I Married an Axe Murderer
[*]Glengarry GlenRoss
[*]Blast From the Past
[*]Outlaw Josey Wales
[*]Monty Python Holy Grail
[*]Diana Krall Live in Paris
[/LIST]
...all fail to play because of error cracking the codes in both Mplayer and VLC except #9 does play in VLC. What is up with this? Anyone have any ideas?

---

### Post by ronnielsen1 on 2010-03-27
Type in vlc in a terminal and try to play a movie. This may give a clue to any problems

---

### Post by Matti L on 2010-03-27
Wrong DVD Region code?

---

### Post by clevertomato on 2010-03-27
I tried starting VLC from terminal before I posted my original message. That's how I knew it is getting an error cracking the codes. Output from one of these unplaying DVDs follows:

```
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdnav: DVD Title: OUTLAW_JOSEY_WALES
libdvdnav: DVD Serial Number: 2B348894
libdvdnav: DVD Title (Alternative): OUTLAW_JOSEY_WALES
libdvdnav: Unable to find map file '/home/shawn/.dvdnav/OUTLAW_JOSEY_WALES.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1
libdvdnav: Language 'en' not found, using '&#65533;&#65533;' instead
libdvdnav: Menu Languages available: &#65533;&#65533; 
libdvdnav: Language 'en' not found, using '&#65533;&#65533;' instead
libdvdnav: Menu Languages available: &#65533;&#65533; 
libdvdnav: Language 'en' not found, using '&#65533;&#65533;' instead
libdvdnav: Menu Languages available: &#65533;&#65533; 
[0x7fde70002578] main input error: ES_OUT_RESET_PCR called

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00026cc3
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x0005004a
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_02_0.VOB (0x0005004a)
libdvdread: Elapsed time 3
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x00050d52
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_02_1.VOB (0x00050d52)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x003520db
libdvdread: Elapsed time 0
libdvdread: Found 3 VTS's
libdvdread: Elapsed time 3
[0x7fde70002578] main input error: ES_OUT_RESET_PCR called
[0x7fde70002578] main input error: ES_OUT_RESET_PCR called
[0x7fde70002578] main input error: ES_OUT_RESET_PCR called
```As to region code, I've always been in US, purchased them in US, and my PC is from US. I would never have set anything different.

---

### Post by AntoniusUno on 2010-03-27
[apologies if I hijack this topic for an unrelated issue]

I also have issues with DVDs in Karmic. Running VLC from terminal gives me the following error:

> 
...
*** libdvdread: CHECK_VALUE failed in ifo_read.c:2103 ***
*** for (uint32_t)vts_atrt->nr_of_vtss * (4 + VTS_ATTRIBUTES_MIN_SIZE) + VTS_ATRT_SIZE < vts_atrt->last_byte + 1 ***

libdvdread: Invalid main menu IFO (VIDEO_TS.IFO), ifoRead_VTS_ATRT() failed.
[0x2693c88] main access error: no access module matched "dvd"
[0x7fddb40448b8] main input error: open of `dvd:///media/cdrom0' failed: no access module matched "dvd"


---

### Post by mc4man on 2010-03-27
@ shawnboy

Maybe try using a different extraction method to test, a couple of different ways. (could also use libdvdcss2 in debug mode.

Easiest would be to put a dvd in your default drive, close out any player that opens. (by default one that vlc can open w/ dvd://

Then open home folder (show hidden files), and delete the .dvdcss folder

Then in a terminal

```
export DVDCSS_METHOD=title && export DVDCSS_VERBOSE=2
```

```
vlc dvd://  > vlc_output.log 2>&1
```

(if disc isn't in default drive then just go this and then open the dvd from vlc
```
vlc  > vlc_output.log 2>&1
```

See what happens and if needed ck. log in home folder

Note - always delete the .dvdcss folder before any libdvdcss2 troubleshooting

---

### Post by clevertomato on 2010-03-28
I did as suggested and following is what the vlc output log contained after trying to play Outlaw Josey Wales:

```
VLC media player 1.0.2 Goldeneye
[0x192e888] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdcss debug: opening target `/dev/sr0'
libdvdcss debug: using libc for access
libdvdcss debug: disc is scrambled
libdvdcss debug: requesting AGID
libdvdcss debug: drive authenticated, using variant 0
libdvdcss debug: authentication established
libdvdcss debug: GetASF authenticated, ASF=1
libdvdcss debug: disc key needs not be decrypted
libdvdcss debug: using CSS key cache dir: /home/thisuser/.dvdcss/OUTLAW_JOSEY_WALES-2001092017044000-0000000000/
[0x7f5cfc002578] main input error: ES_OUT_RESET_PCR called

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00026cc3
libdvdcss debug: cracking title key at block 158915
libdvdcss error: read error
libdvdcss debug: read error at block 158916, resorting to secret arcanes to recover
libdvdcss debug: opening target `/dev/sr0'
libdvdcss debug: using libc for access
libdvdcss error: read error
libdvdcss debug: end of title reached
libdvdcss debug: successful attempts 0/0, scrambled blocks 0/1
libdvdcss debug: no scrambled sectors found
libdvdcss debug: title key is 00:00:00:00:00
libdvdcss debug: unencrypted title
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x0005004a
libdvdcss debug: cracking title key at block 327754
libdvdcss error: read error
libdvdcss debug: read error at block 327754, resorting to secret arcanes to recover
libdvdcss debug: opening target `/dev/sr0'
libdvdcss debug: using libc for access
libdvdcss error: read error
libdvdcss debug: end of title reached
libdvdcss debug: successful attempts 0/0, scrambled blocks 0/0
libdvdcss debug: title key is 00:00:00:00:00
libdvdcss error: fatal error in vts css key
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_02_0.VOB (0x0005004a)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x00050d52
libdvdcss debug: cracking title key at block 331090
libdvdcss error: read error
libdvdcss debug: read error at block 331090, resorting to secret arcanes to recover
libdvdcss debug: opening target `/dev/sr0'
libdvdcss debug: using libc for access
libdvdcss error: read error
libdvdcss debug: end of title reached
libdvdcss debug: successful attempts 0/0, scrambled blocks 0/0
libdvdcss debug: title key is 00:00:00:00:00
libdvdcss error: fatal error in vts css key
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_02_1.VOB (0x00050d52)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x003520db
libdvdcss debug: cracking title key at block 3481819
libdvdcss debug: end of title reached
libdvdcss debug: successful attempts 0/0, scrambled blocks 0/2000
libdvdcss debug: no scrambled sectors found
libdvdcss debug: title key is 00:00:00:00:00
libdvdcss debug: unencrypted title
libdvdread: Elapsed time 1
libdvdread: Found 3 VTS's
libdvdread: Elapsed time 1
[0x7f5cfc002578] main input error: ES_OUT_RESET_PCR called
libdvdcss debug: cracking title key at block 327754
libdvdcss error: read error
libdvdcss debug: read error at block 327754, resorting to secret arcanes to recover
libdvdcss debug: opening target `/dev/sr0'
libdvdcss debug: using libc for access
libdvdcss error: read error
libdvdcss debug: end of title reached
libdvdcss debug: successful attempts 0/0, scrambled blocks 0/0
libdvdcss debug: title key is 00:00:00:00:00
libdvdcss error: fatal error in vts css key
libdvdcss error: read error
[0x7f5cfc002578] main input error: ES_OUT_RESET_PCR called
[0x7f5cfc002578] main input error: ES_OUT_RESET_PCR called
libdvdcss debug: cracking title key at block 331090
libdvdcss error: read error
libdvdcss debug: read error at block 331090, resorting to secret arcanes to recover
libdvdcss debug: opening target `/dev/sr0'
libdvdcss debug: using libc for access
libdvdcss error: read error
libdvdcss debug: end of title reached
libdvdcss debug: successful attempts 0/0, scrambled blocks 0/0
libdvdcss debug: title key is 00:00:00:00:00
libdvdcss error: fatal error in vts css key
libdvdcss error: read error
libdvdnav: Using dvdnav version 4.1.3
libdvdnav: DVD Title: OUTLAW_JOSEY_WALES
libdvdnav: DVD Serial Number: 2B348894
libdvdnav: DVD Title (Alternative): OUTLAW_JOSEY_WALES
libdvdnav: Unable to find map file '/home/thisuser/.dvdnav/OUTLAW_JOSEY_WALES.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1
libdvdnav: Language 'en' not found, using 'ÿÿ' instead
libdvdnav: Menu Languages available: ÿÿ 
libdvdnav: Language 'en' not found, using 'ÿÿ' instead
libdvdnav: Menu Languages available: ÿÿ 
libdvdnav: Language 'en' not found, using 'ÿÿ' instead
libdvdnav: Menu Languages available: ÿÿ 
```Any suggestions?

EDIT #1: By the way, all these DVDs work flawlessly in my PS3, on other computers (using Windows XP), and in this drive on this computer using Windows 7. So, the discs themselves are not damaged.

EDIT #2: Wow! For the heck of it I just tried Totem Movie Player (the application I have cursed ever since I discovered Ubuntu because it can NEVER play ANYTHING). It plays one of the DVDs that VLC and Mplayer won't play. I haven't tried the others yet, but presumably they will work in Totem Movie Player, also. I still would really like to know why VLC and Mplayer cannot play my DVDs, but at least for now SOMETHING will. I still welcome any help if someone has ideas.

---

### Post by mc4man on 2010-03-28
> Any suggestions? 
I'm assuming, based on earlier reply,  that at some point a region had been set on the drive.

You could double check by installing regionset and with a disc in the drive running
regionset

The 4th line would show - type: SET
*(usually* if there is an issue with no region being set then it would be a failure to authenticate, won't hurt to ck. and set to 1 if not already.

You could try an earlier version of libdvdcss2, [available from videolan]("http://download.videolan.org/pub/libdvdcss/1.2.6/deb/") (i386 only, remove current one first, delete .dvdcss

If you have access to another pc that plays the dvd's, then copy the individual movie's folder in .dvdcss to your .dvdcss folder and then try again. 
 (players always check .dvdcss first and use the keys found in a title's folder  if it exists, even if the keys are wrong or incomplete or if copied then the correct ones

Try another drive or externel one (usb) if possible.

---

### Post by clevertomato on 2010-03-28
Good news and bad news. The good news is DVD playback is working now in Totem Movie Player, Mplayer, & VLC. The bad news is I'm not sure exactly what changed. I tried so many things, but things began working after I booted into Windows 7 on same machine to test DVD in it (it worked fine). After that I booted back into Karmic and out of desperation tried playing it in Totem Movie Player. That never plays ANYTHING for me, but it worked. After that, it worked in everything. I have no idea why, especially since, to my knowledge, VLC is supposed to play DVDs without any messing around with codecs or other stuff. Weird. Still wish I knew WHY/HOW I got it to work.

---

### Post by JosephGarrison on 2010-03-28
When I started using Ubuntu not that long ago I was having problems with DVDS. What ended up happening is I ended up installing, un-installing, then reinstalling the files needed to play the dvds. Once I did that they did start working. A reinstall can be miraculous for some reason.

---

### Post by clevertomato on 2010-03-28
@JosephGarrison: Unfortunately that sounds a lot like a characteristic of another popular OS that Linux fans ridicule for that very reason (among others). But... you're right. Sometimes a reboot or reinstall works magic.

---

### Post by clevertomato on 2010-03-28
I had the same problem in Jaunty on my old notebook just now. So here's what I did to recap for anyone who may be experiencing same...

installed:

libdvdcss2
libdvdread4
ubuntu-restricted-extras

I made sure the Canonical partner repos were enabled in my sources.list and also added the following line to /etc/apt/sources.list :
[FONT=monospace]
[/FONT]deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) karmic free non-free

then did:

sudo aptitude update
and
sudo aptitude safe-upgrade

then reboot and try to play a DVD. It never worked for me at this point, but what seems to be the key (no pun intended) is deleting the ~/.dvdcss directory with the failed keys from before. So I did (disclaimer... be careful with "rm -r"):

sudo rm -r ~/.dvdcss

then try to play DVD. I don't know if ALL of these things were necessary, but this is what I did and eventually everything worked in VLC and in other players like Totem Movie Player. I hope this helps someone.

---

### Post by mc4man on 2010-03-28
> but things began working after I booted into Windows 7 on same machine to test DVD in it (it worked fine)

It's quite possible you didn't have a region set and when you tried a dvd in win. it set it for you. ( I believe windows player may do that automatically - been a while since I used...
Or it could have been a reboot - karmic is funny that way sometimes

---

### Post by clevertomato on 2010-03-28
Doesn't the following line from my previous post in this thread indicate that the region was already set to 1?
```
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1
```
It was part of the output log from VLC when things were not working.

---

### Post by mc4man on 2010-03-28
> Doesn't the following line from my previous post in this thread indicate that the region was already set to 1?
No that's just what's 'reported' by dvdread (dvdnav) as to what region the disk is, not the drive

---

### Post by Matt G Dalian on 2010-05-08
Thought I'd share what I did to get DVD playback working.

I installed Ubuntu Karmic (9.10) amd64 and DVDs didn't work.
I never tried to fix it.

A few months later, I upgrated to Ubuntu Lucid Lynx (10.04) and DVD playback still didn't work.

To fix it, I installed two packages:

1. From the Synaptic Package Manager I installed ubuntu-restricted-extras

2. I also installed libdvdcss2.
This wasn't in my respository list in Synaptic Package Manager, so I had to download the .deb file from packages.medibuntu.org
Just select your Ubuntu version on the first page and then select the package to download.

After both of these packages were installed, when I insert a DVD into my DVD drive and select the default "Play with Movie Player" option, the DVD will work.

By the way, I'm using a Dell Studio 1558 Intel Core i3 64 bit 4 GB ram, ATI Mobility Radeon video card.

---

### Post by Labyrinth on 2011-07-22
Having the same problem, using regionset to set the DVD region to 2 allowed me to play DVDs.
Region set output:

```

klaus@coral:~$ regionset 
regionset version 0.1 -- reads/sets region code on DVD drives
Current Region Code settings:
RPC Phase: II
type: NONE
vendor resets available: 4
user controlled changes resets available: 5
drive plays discs from region(s):, mask=0xFF

Would you like to change the region setting of your drive? [y/n]:y
Enter the new region number for your drive [1..8]:2
New mask: 0xFFFFFFFD, correct? [y/n]:y
Region code set successfully!
klaus@coral:~$ regionset 
regionset version 0.1 -- reads/sets region code on DVD drives
Current Region Code settings:
RPC Phase: II
type: SET
vendor resets available: 4
user controlled changes resets available: 4
drive plays discs from region(s): 2, mask=0xFD

Would you like to change the region setting of your drive? [y/n]:n

```


VLC & libdvdcss output before setting the region:

```
VLC media player 1.1.9 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0x8aa9914] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Blocked: call to setlocale(6, "")
Blocked: call to setlocale(6, "")
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdcss debug: opening target `/dev/sr0'
libdvdcss debug: using libc for access
libdvdcss debug: disc is scrambled
libdvdcss debug: requesting AGID
libdvdcss debug: drive authenticated, using variant 0
libdvdcss debug: authentication established
libdvdcss debug: GetASF authenticated, ASF=1
libdvdcss debug: disc key needs not be decrypted
libdvdcss debug: using CSS key cache dir: /home/klaus/.dvdcss/LAND_OF_THE_DEAD-2006022315071077-0000000000/

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000145
libdvdcss debug: cracking title key at block 325
libdvdcss debug: non MPEG block found at block 402 (end of title)
libdvdcss debug: end of title reached
libdvdcss debug: successful attempts 0/0, scrambled blocks 0/77
libdvdcss debug: no scrambled sectors found
libdvdcss debug: title key is 00:00:00:00:00
libdvdcss debug: unencrypted title
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000001ac
libdvdcss debug: cracking title key at block 428
libdvdcss error: read error
libdvdcss debug: read error at block 428, resorting to secret arcanes to recover
libdvdcss debug: opening target `/dev/sr0'
libdvdcss debug: using libc for access
libdvdcss error: read error
libdvdcss debug: end of title reached
libdvdcss debug: successful attempts 0/0, scrambled blocks 0/0
libdvdcss debug: title key is 00:00:00:00:00
libdvdcss error: fatal error in vts css key
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_0.VOB (0x000001ac)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x000008a8
libdvdcss debug: cracking title key at block 2216
libdvdcss error: read error
libdvdcss debug: read error at block 2216, resorting to secret arcanes to recover
libdvdcss debug: opening target `/dev/sr0'
libdvdcss debug: using libc for access
libdvdcss error: read error
libdvdcss debug: end of title reached
libdvdcss debug: successful attempts 0/0, scrambled blocks 0/0
libdvdcss debug: title key is 00:00:00:00:00
libdvdcss error: fatal error in vts css key
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_1.VOB (0x000008a8)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x00003fc2
libdvdcss debug: cracking title key at block 16322
libdvdcss error: read error
libdvdcss debug: read error at block 16322, resorting to secret arcanes to recover
libdvdcss debug: opening target `/dev/sr0'
libdvdcss debug: using libc for access
libdvdcss error: read error
libdvdcss debug: end of title reached
libdvdcss debug: successful attempts 0/0, scrambled blocks 0/0
libdvdcss debug: title key is 00:00:00:00:00
libdvdcss error: fatal error in vts css key
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_02_0.VOB (0x00003fc2)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x0000400f
libdvdcss debug: cracking title key at block 16399
libdvdcss error: read error
libdvdcss debug: read error at block 16400, resorting to secret arcanes to recover
libdvdcss debug: opening target `/dev/sr0'
libdvdcss debug: using libc for access
libdvdcss error: read error
libdvdcss debug: end of title reached
libdvdcss debug: successful attempts 0/0, scrambled blocks 0/1
libdvdcss debug: no scrambled sectors found
libdvdcss debug: title key is 00:00:00:00:00
libdvdcss debug: unencrypted title
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x0000407e
libdvdcss debug: cracking title key at block 16510
libdvdcss error: read error
libdvdcss debug: read error at block 16510, resorting to secret arcanes to recover
libdvdcss debug: opening target `/dev/sr0'
libdvdcss debug: using libc for access
libdvdcss error: read error
libdvdcss debug: end of title reached
libdvdcss debug: successful attempts 0/0, scrambled blocks 0/0
libdvdcss debug: title key is 00:00:00:00:00
libdvdcss error: fatal error in vts css key
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_03_0.VOB (0x0000407e)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x000040cb
libdvdcss debug: cracking title key at block 16587
libdvdcss error: read error
libdvdcss debug: read error at block 16588, resorting to secret arcanes to recover
libdvdcss debug: opening target `/dev/sr0'
libdvdcss debug: using libc for access
libdvdcss error: read error
libdvdcss debug: end of title reached
libdvdcss debug: successful attempts 0/0, scrambled blocks 0/1
libdvdcss debug: no scrambled sectors found
libdvdcss debug: title key is 00:00:00:00:00
libdvdcss debug: unencrypted title
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x00004d85
libdvdcss debug: cracking title key at block 19845
libdvdcss error: read error
libdvdcss debug: read error at block 19846, resorting to secret arcanes to recover
libdvdcss debug: opening target `/dev/sr0'
libdvdcss debug: using libc for access
libdvdcss error: read error
libdvdcss debug: end of title reached
libdvdcss debug: successful attempts 0/0, scrambled blocks 0/1
libdvdcss debug: no scrambled sectors found
libdvdcss debug: title key is 00:00:00:00:00
libdvdcss debug: unencrypted title
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x00004dd2
libdvdcss debug: cracking title key at block 19922
libdvdcss error: read error
libdvdcss debug: read error at block 19922, resorting to secret arcanes to recover
libdvdcss debug: opening target `/dev/sr0'
libdvdcss debug: using libc for access
libdvdcss error: read error
libdvdcss debug: end of title reached
libdvdcss debug: successful attempts 0/0, scrambled blocks 0/0
libdvdcss debug: title key is 00:00:00:00:00
libdvdcss error: fatal error in vts css key
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_04_1.VOB (0x00004dd2)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x002a9e8c
libdvdcss debug: cracking title key at block 2793100
libdvdcss error: read error
libdvdcss debug: read error at block 2793100, resorting to secret arcanes to recover
libdvdcss debug: opening target `/dev/sr0'
libdvdcss debug: using libc for access
libdvdcss error: read error
libdvdcss debug: end of title reached
libdvdcss debug: successful attempts 0/0, scrambled blocks 0/0
libdvdcss debug: title key is 00:00:00:00:00
libdvdcss error: fatal error in vts css key
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_05_0.VOB (0x002a9e8c)
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x002a9ed9
libdvdcss debug: cracking title key at block 2793177
libdvdcss error: read error
libdvdcss debug: read error at block 2793178, resorting to secret arcanes to recover
libdvdcss debug: opening target `/dev/sr0'
libdvdcss debug: using libc for access
libdvdcss error: read error
libdvdcss debug: end of title reached
libdvdcss debug: successful attempts 0/0, scrambled blocks 0/1
libdvdcss debug: no scrambled sectors found
libdvdcss debug: title key is 00:00:00:00:00
libdvdcss debug: unencrypted title
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x002b28d8
libdvdcss debug: cracking title key at block 2828504
libdvdcss error: read error
libdvdcss debug: read error at block 2828504, resorting to secret arcanes to recover
libdvdcss debug: opening target `/dev/sr0'
libdvdcss debug: using libc for access
libdvdcss error: read error
libdvdcss debug: end of title reached
libdvdcss debug: successful attempts 0/0, scrambled blocks 0/0
libdvdcss debug: title key is 00:00:00:00:00
libdvdcss error: fatal error in vts css key
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_06_0.VOB (0x002b28d8)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x002b2925
libdvdcss debug: cracking title key at block 2828581
libdvdcss error: read error
libdvdcss debug: read error at block 2828582, resorting to secret arcanes to recover
libdvdcss debug: opening target `/dev/sr0'
libdvdcss debug: using libc for access
libdvdcss error: read error
libdvdcss debug: end of title reached
libdvdcss debug: successful attempts 0/0, scrambled blocks 0/1
libdvdcss debug: no scrambled sectors found
libdvdcss debug: title key is 00:00:00:00:00
libdvdcss debug: unencrypted title
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x002c5e81
libdvdcss debug: cracking title key at block 2907777
libdvdcss error: read error
libdvdcss debug: read error at block 2907778, resorting to secret arcanes to recover
libdvdcss debug: opening target `/dev/sr0'
libdvdcss debug: using libc for access
libdvdcss error: read error
libdvdcss debug: end of title reached
libdvdcss debug: successful attempts 0/0, scrambled blocks 0/1
libdvdcss debug: no scrambled sectors found
libdvdcss debug: title key is 00:00:00:00:00
libdvdcss debug: unencrypted title
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x002c5ece
libdvdcss debug: cracking title key at block 2907854
libdvdcss error: read error
libdvdcss debug: read error at block 2907854, resorting to secret arcanes to recover
libdvdcss debug: opening target `/dev/sr0'
libdvdcss debug: using libc for access
libdvdcss error: read error
libdvdcss debug: end of title reached
libdvdcss debug: successful attempts 0/0, scrambled blocks 0/0
libdvdcss debug: title key is 00:00:00:00:00
libdvdcss error: fatal error in vts css key
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_07_1.VOB (0x002c5ece)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_0.VOB at 0x002d1055
libdvdcss debug: cracking title key at block 2953301
libdvdcss error: read error
libdvdcss debug: read error at block 2953302, resorting to secret arcanes to recover
libdvdcss debug: opening target `/dev/sr0'
libdvdcss debug: using libc for access
libdvdcss error: read error
libdvdcss debug: end of title reached
libdvdcss debug: successful attempts 0/0, scrambled blocks 0/1
libdvdcss debug: no scrambled sectors found
libdvdcss debug: title key is 00:00:00:00:00
libdvdcss debug: unencrypted title
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x002d10a2
libdvdcss debug: cracking title key at block 2953378
libdvdcss error: read error
libdvdcss debug: read error at block 2953378, resorting to secret arcanes to recover
libdvdcss debug: opening target `/dev/sr0'
libdvdcss debug: using libc for access
libdvdcss error: read error
libdvdcss debug: end of title reached
libdvdcss debug: successful attempts 0/0, scrambled blocks 0/0
libdvdcss debug: title key is 00:00:00:00:00
libdvdcss error: fatal error in vts css key
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_08_1.VOB (0x002d10a2)!!
libdvdread: Elapsed time 0
libdvdread: Found 8 VTS's
libdvdread: Elapsed time 1
Warning: call to srand(900888)
libdvdcss debug: cracking title key at block 428
libdvdcss error: read error
libdvdcss debug: read error at block 428, resorting to secret arcanes to recover
libdvdcss debug: opening target `/dev/sr0'
libdvdcss debug: using libc for access
libdvdcss error: read error
libdvdcss debug: end of title reached
libdvdcss debug: successful attempts 0/0, scrambled blocks 0/0
libdvdcss debug: title key is 00:00:00:00:00
libdvdcss error: fatal error in vts css key
libdvdcss error: read error
libdvdcss debug: cracking title key at block 2216
libdvdcss error: read error
libdvdcss debug: read error at block 2216, resorting to secret arcanes to recover
libdvdcss debug: opening target `/dev/sr0'
libdvdcss debug: using libc for access
libdvdcss error: read error
libdvdcss debug: end of title reached
libdvdcss debug: successful attempts 0/0, scrambled blocks 0/0
libdvdcss debug: title key is 00:00:00:00:00
libdvdcss error: fatal error in vts css key
libdvdcss error: read error

```

---

