---
title: "Not all DVD's work in Ubuntu 10.04"
date: 2010-09-14
forum: Multimedia Software
---

### Post by msknight on 2010-09-14
Hi Folks,

I've sort of found similar-ish posts but nothing is quite working.

Situation...

Decided to rip my collection of 400-ish DVDs. The computer has four different DVD players attached from different manufacturers. Ubuntu 64 bit, patched.

Some DVDs appear, "corrupted," in the form of green blocks or sometimes white lines. It can be a part of a DVD (like a special feature track) or a whole DVD. It can also be a single DVD in a box set of five or six. 

Also, sometimes it won't pick up some of the special features tracks so they're not even visible in Handbrake ... although in VLC they are visible but also, won't play.

However, the "corrupt" DVDs work fine in my one remaining Windows machine, and also in a commercial DVD player. Just not in Ubuntu.

And when I mean not in Ubuntu, I mean anything on any of the four DVD readers. It is as if there is a genuine problem reading the tracks; that's how the errors come back; read errors.

One of the worst was Constantine. I thought it was a corrupt DVD at first and bought a second copy, but that did the same thing so that's how I worked out that it just didn't get on well with Ubuntu ... and then I found other DVD's started doing the same. This feels like it is affecting between 1 in 10, or 1 in 20 DVDs, thereabouts.

So far my solution is to use the Windows machine to rip the VOBs off the trouble DVD's and then transfer to Linux to Handbrake them.

But it would be great to work out what is going on here.

If you want me to report on something, it might save time if you also post the command just in case I don't know it.

---

### Post by mc4man on 2010-09-14
With so many drives can't give you a complete comm. but maybe try this to produce some dvdcss debugging.

first - while not always needed do you know if all your drives have a region set? (assuming region 2.
Are all of your titles region 2?

Put a problem dvd (for starters not from a tv series, a movie would be best) in one of your drives, close out any pop up or player.

**Then** go into home folder, find the .dvdcss folder and delete all the contents (.dvdcss is a hidden folder

From a terminal
```
export DVDCSS_VERBOSE=2 && vlc > vlc_output.log 2>&1
```
Once vlc opens go media - open disc, ect. Let the dvd start up for a few seconds and then close vlc out

See if the vlc_output.log (in home folder) reports any errors about cracking keys and what dvdcss method is used.

---

### Post by msknight on 2010-09-15
Well, it is possible that it is a region thing.  I don't like setting regions on the DVD players because some of my DVD's are region 1 and I'm region 2. This is 'cause some of the stuff I want isn't available in region 2.

How do I set the region on my DVD devices in Ubuntu please? It is starting to look like this is the problem.

Here's an excerpt from Indiana Jones and the Temple of Doom ... 

```
michelle@michelle-desktop:~$ cat vlc_output.log 
VLC media player 1.0.6 Goldeneye
[0x14a94b8] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdcss debug: opening target `/dev/sr3'
libdvdcss debug: using libc for access
libdvdcss debug: disc is scrambled
libdvdcss debug: requesting AGID
libdvdcss debug: drive authenticated, using variant 0
libdvdcss debug: authentication established
libdvdcss debug: GetASF authenticated, ASF=1
libdvdcss debug: decrypting disc key bc:f7:bb:99:4e
libdvdcss debug: trying player key 01:af:e3:12:80
libdvdcss debug: decrypted disc key is 0a:f0:cd:c1:81
libdvdcss debug: using CSS key cache dir: /home/michelle/.dvdcss/INDIANAJONES_TOD_UKCENSOR-2003070718212200-0af0cdc181/

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x000001ef
libdvdcss debug: getting title key at block 495 the classic way
libdvdcss debug: requesting AGID
libdvdcss debug: drive authenticated, using variant 0
libdvdcss debug: authentication established
libdvdcss debug: ioctl ReadTitleKey failed (region mismatch?)
libdvdcss debug: GetASF not authenticated, ASF=0
libdvdcss debug: lost ASF requesting title key
libdvdcss debug: resetting drive and cracking title key
libdvdcss debug: requesting AGID
libdvdcss debug: ioctl ReportAgid failed, invalidating AGID 0
libdvdcss debug: requesting AGID
libdvdcss debug: drive authenticated, using variant 0
libdvdcss debug: authentication established
libdvdcss debug: GetASF authenticated, ASF=1
libdvdcss debug: decrypting disc key bc:f7:bb:99:4e
libdvdcss debug: trying player key 01:af:e3:12:80
libdvdcss debug: decrypted disc key is 0a:f0:cd:c1:81
libdvdcss debug: cracking title key at block 495
libdvdcss debug: non MPEG block found at block 616 (end of title)
libdvdcss debug: end of title reached
libdvdcss debug: successful attempts 0/0, scrambled blocks 0/121
libdvdcss debug: no scrambled sectors found
libdvdcss debug: title key is 00:00:00:00:00
libdvdcss debug: unencrypted title
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x0000027b
libdvdcss debug: getting title key at block 635 the classic way
libdvdcss debug: requesting AGID
libdvdcss debug: drive authenticated, using variant 0
libdvdcss debug: authentication established
libdvdcss debug: ioctl ReadTitleKey failed (region mismatch?)
libdvdcss debug: GetASF not authenticated, ASF=0
libdvdcss debug: lost ASF requesting title key
libdvdcss debug: resetting drive and cracking title key
libdvdcss debug: requesting AGID
libdvdcss debug: ioctl ReportAgid failed, invalidating AGID 0
libdvdcss debug: requesting AGID
libdvdcss debug: drive authenticated, using variant 0
libdvdcss debug: authentication established
libdvdcss debug: GetASF authenticated, ASF=1
libdvdcss debug: decrypting disc key bc:f7:bb:99:4e
libdvdcss debug: trying player key 01:af:e3:12:80
libdvdcss debug: decrypted disc key is 0a:f0:cd:c1:81
libdvdcss debug: cracking title key at block 635
libdvdcss debug: successful attempts 1/1, scrambled blocks 57/136
libdvdcss debug: vts key initialized
libdvdcss debug: title key is c2:f3:c8:5f:79
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x000002fe
libdvdcss debug: getting title key at block 766 the classic way
libdvdcss debug: requesting AGID
libdvdcss debug: drive authenticated, using variant 0
libdvdcss debug: authentication established
libdvdcss debug: ioctl ReadTitleKey failed (region mismatch?)
libdvdcss debug: GetASF not authenticated, ASF=0
libdvdcss debug: lost ASF requesting title key
libdvdcss debug: resetting drive and cracking title key
libdvdcss debug: requesting AGID
libdvdcss debug: ioctl ReportAgid failed, invalidating AGID 0
libdvdcss debug: requesting AGID
libdvdcss debug: drive authenticated, using variant 0
libdvdcss debug: authentication established
libdvdcss debug: GetASF authenticated, ASF=1
libdvdcss debug: decrypting disc key bc:f7:bb:99:4e
libdvdcss debug: trying player key 01:af:e3:12:80
libdvdcss debug: decrypted disc key is 0a:f0:cd:c1:81
libdvdcss debug: cracking title key at block 766
libdvdcss debug: successful attempts 1/1, scrambled blocks 2/5
libdvdcss debug: vts key initialized
libdvdcss debug: title key is c2:f3:c8:5f:79
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x0000033c
libdvdcss debug: getting title key at block 828 the classic way
libdvdcss debug: requesting AGID
libdvdcss debug: drive authenticated, using variant 0
libdvdcss debug: authentication established
libdvdcss debug: ioctl ReadTitleKey failed (region mismatch?)
libdvdcss debug: GetASF not authenticated, ASF=0
libdvdcss debug: lost ASF requesting title key
libdvdcss debug: resetting drive and cracking title key
libdvdcss debug: requesting AGID
libdvdcss debug: ioctl ReportAgid failed, invalidating AGID 0
libdvdcss debug: requesting AGID
libdvdcss debug: drive authenticated, using variant 0
libdvdcss debug: authentication established
libdvdcss debug: GetASF authenticated, ASF=1
libdvdcss debug: decrypting disc key bc:f7:bb:99:4e
libdvdcss debug: trying player key 01:af:e3:12:80
libdvdcss debug: decrypted disc key is 0a:f0:cd:c1:81
libdvdcss debug: cracking title key at block 828
libdvdcss error: read error
libdvdcss debug: read error at block 858, resorting to secret arcanes to recover
libdvdcss debug: opening target `/dev/sr3'
libdvdcss debug: using libc for access
libdvdcss error: read error
libdvdcss debug: end of title reached
libdvdcss debug: successful attempts 0/0, scrambled blocks 14/30
libdvdcss debug: title key is 00:00:00:00:00
libdvdcss error: fatal error in vts css key
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_02_0.VOB (0x0000033c)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x0001e592
libdvdcss debug: getting title key at block 124306 the classic way
libdvdcss debug: requesting AGID
libdvdcss debug: drive authenticated, using variant 0
libdvdcss debug: authentication established
libdvdcss debug: ioctl ReadTitleKey failed (region mismatch?)
libdvdcss debug: GetASF not authenticated, ASF=0
libdvdcss debug: lost ASF requesting title key
libdvdcss debug: resetting drive and cracking title key
libdvdcss debug: requesting AGID
libdvdcss debug: ioctl ReportAgid failed, invalidating AGID 0
libdvdcss debug: requesting AGID
libdvdcss debug: drive authenticated, using variant 0
libdvdcss debug: authentication established
libdvdcss debug: GetASF authenticated, ASF=1
libdvdcss debug: decrypting disc key bc:f7:bb:99:4e
libdvdcss debug: trying player key 01:af:e3:12:80
libdvdcss debug: decrypted disc key is 0a:f0:cd:c1:81
libdvdcss debug: cracking title key at block 124306
libdvdcss debug: successful attempts 1/1, scrambled blocks 1/3
libdvdcss debug: vts key initialized
libdvdcss debug: title key is c5:84:07:f2:1a

```

---

### Post by msknight on 2010-09-15
Well, well, well. I used regionset and this is what happened...

```
michelle@michelle-desktop:~$ regionset
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
```

...and this seems to have worked.

But I've got four DVD drives in the system and I'm not sure which one it has changed. It doesn't respond to --help.

---

### Post by msknight on 2010-09-15
I found out how to issue the command for specific drives...

regionset /dev/sr0

...when I ran it without a parameter, this is the state of the drives...

sr0 - disk installed
sr1 - disk installed
sr2 - no disk
sr3 - disk installed

After I found out how to give the specific drive name, I checked each of the three main drives in turn...

sr0 - region 2
sr1 - region 2
sr3 - #FF

... and sr3 was the drive that wasn't working, but then did work. so I'm not sure what is going on here.

Also, when I put a drive in sr2 and checked it, it was already region 2.

So I don't know what to make of this. I'm not 100% certain whether the region coding is to blame, whether there was simply a delay in emptying the css directory or what.

Time will tell if I get more problems.

---

### Post by msknight on 2010-09-15
Well,

By far the worst movie for this was Constantine ... and I don't know which one it was ... deleting the css files or setting the region codes, but it has worked.

I tried it in the player which was already set to region 2, so I guess that the css folder has had a part in this.

I think I'll set up a cron job to clear that folder at 5am every morning.

Many thanks for the help.

---

### Post by mc4man on 2010-09-15
> and I don't know which one it was ... deleting the css files or setting the region code

> I think I'll set up a cron job to clear that folder at 5am every morning.
no need to - may not work as you wish unless you match drive and region - 

When you play a dvd **for the first time**  a folder is created in .dvdcss that contains the decryption keys.

All players will access .dvdcss and if a folder is found matching the volume label of the dvd,  **they will then use the keys inside whether good, bad or incomplete**

When there is a region mismatch between the disk and the drive, - libdvdcss will switch from the default extraction method (disc key) to a brute force method which is usually successful but not always. 

The most likely titles on a dvd to produce wrong or incomplete keys are small sample titles like extras.
So going back to what I've mentioned, if the drive used for the 'first play' on a dvd fails to get the proper, complete set then all subsequent plays of that title will use that 'bad' set, no matter what the player or drive used.

So in your case I'd 'first play' R1 titles in a R1 drive, R2 titles in a R2 drive - I'm sure you get the idea.

( by deleting the folders in .dvdcss the player was forced to re-aquire the keys - successfully this time.

Edit: don't be switching the region setting to play disks, drives only have 5 total. I'd probably leave 3 drives at R2, set one to R1 and just match the first play, region to drive.
Also note that the key folders can be transferred to other machines if the need arises

---

