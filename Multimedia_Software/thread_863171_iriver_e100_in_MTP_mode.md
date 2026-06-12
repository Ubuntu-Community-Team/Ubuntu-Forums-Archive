---
title: "iriver e100 in MTP mode"
date: 2008-07-18
forum: Multimedia Software
---

### Post by JoshHendo on 2008-07-18
Hi Everyone,

I recently bought a iriver e100, and so far it is great (after a firmware upgrade). It had two connection modes, MTP and one where it will just appear as a mounted hard disk. It works well under Ubuntu, when mounted as a hard disk, but I want to be able to use either Rhythmbox or Banshee to manage my music collection. Both of these programs support MTP.

The problem that I am having is, when I change my player to MTP, it doesn't seem to be detected by Ubuntu at all: I have libmtp, libmtp-dev, even tried mtpfs (or fsmtp? I can't remember). Is there something I need to do in particular to get Ubuntu to recognize it?

Any information needed is available upon request.

Thanks, Josh.

---

### Post by adam_kimber on 2008-07-18
I assume you have started Rhythmbox etc to see if the device is listed in the programs? 

What does the system log (I can tell you how to access this if required) have to say when you plug it in? 

I will have a play with my music player tonight as that has an MTP mode as see what happens...

---

### Post by JoshHendo on 2008-07-18
The log, which seems to not indicate anything good, looks like this:

```

[  980.549476] scsi9 : SCSI emulation for USB Mass Storage devices
[  980.549649] usb-storage: device found at 19
[  980.549651] usb-storage: waiting for device to settle before scanning
[  985.552017] usb-storage: device scan complete
[  985.600261] scsi 9:0:0:0: Direct-Access     iriver   E100                  PQ: 0 ANSI: 0 CCS
[  985.601967] scsi 9:0:0:1: Direct-Access     iriver   E100                  PQ: 0 ANSI: 0 CCS
[  985.613954] sd 9:0:0:0: [sdb] 15667200 512-byte hardware sectors (8022 MB)
[  985.614700] sd 9:0:0:0: [sdb] Write Protect is off
[  985.614702] sd 9:0:0:0: [sdb] Mode Sense: 00 12 00 00
[  985.614704] sd 9:0:0:0: [sdb] Assuming drive cache: write through
[  985.616950] sd 9:0:0:0: [sdb] 15667200 512-byte hardware sectors (8022 MB)
[  985.617576] sd 9:0:0:0: [sdb] Write Protect is off
[  985.617579] sd 9:0:0:0: [sdb] Mode Sense: 00 12 00 00
[  985.617581] sd 9:0:0:0: [sdb] Assuming drive cache: write through
[  985.617585]  sdb: unknown partition table
[  985.622483] sd 9:0:0:0: [sdb] Attached SCSI removable disk
[  985.622525] sd 9:0:0:0: Attached scsi generic sg2 type 0
[  985.624951] sd 9:0:0:1: [sdc] 15946752 512-byte hardware sectors (8165 MB)
[  985.625569] sd 9:0:0:1: [sdc] Write Protect is off
[  985.625572] sd 9:0:0:1: [sdc] Mode Sense: 00 12 00 00
[  985.625574] sd 9:0:0:1: [sdc] Assuming drive cache: write through
[  985.628192] sd 9:0:0:1: [sdc] 15946752 512-byte hardware sectors (8165 MB)
[  985.629066] sd 9:0:0:1: [sdc] Write Protect is off
[  985.629068] sd 9:0:0:1: [sdc] Mode Sense: 00 12 00 00
[  985.629070] sd 9:0:0:1: [sdc] Assuming drive cache: write through
[  985.629074]  sdc:
[  985.630871] sd 9:0:0:1: [sdc] Attached SCSI removable disk
[  985.630911] sd 9:0:0:1: Attached scsi generic sg3 type 0
[ 1165.630855] usb 7-4: USB disconnect, address 19
[ 1336.309673] audit(1216385003.254:3): type=1503 operation="capable" name="dac_override" pid=9568 profile="/usr/lib/cups/backend/cups-pdf" namespace="default"
[ 1336.309681] audit(1216385003.254:4): type=1503 operation="capable" name="dac_read_search" pid=9568 profile="/usr/lib/cups/backend/cups-pdf" namespace="default"
[ 1385.926340] audit(1216385052.902:5): type=1503 operation="capable" name="dac_override" pid=9612 profile="/usr/lib/cups/backend/cups-pdf" namespace="default"
[ 1385.926348] audit(1216385052.902:6): type=1503 operation="capable" name="dac_read_search" pid=9612 profile="/usr/lib/cups/backend/cups-pdf" namespace="default"
[ 2087.867125] usb 7-2: USB disconnect, address 14
[ 2087.867348] usblp0: removed
[ 2481.092918] usb 7-4: new high speed USB device using ehci_hcd and address 20
[ 2481.212842] usb 7-4: device descriptor read/64, error -71
[ 2481.432708] usb 7-4: device descriptor read/64, error -71
[ 2481.648579] usb 7-4: new high speed USB device using ehci_hcd and address 21
[ 2481.764514] usb 7-4: device descriptor read/64, error -71
[ 2481.980379] usb 7-4: device descriptor read/64, error -71
[ 2482.196235] usb 7-4: new high speed USB device using ehci_hcd and address 22
[ 2482.844411] usb 7-4: device descriptor read/8, error -71
[ 2482.965086] usb 7-4: device descriptor read/8, error -71
[ 2495.408200] usb 7-4: new high speed USB device using ehci_hcd and address 24
[ 2495.545501] usb 7-4: configuration #1 chosen from 1 choice
[ 2501.144441] usb 7-4: USB disconnect, address 24
[ 2515.272092] usb 7-4: new high speed USB device using ehci_hcd and address 25
[ 2519.236288] usb 7-4: new high speed USB device using ehci_hcd and address 26
[ 2519.372494] usb 7-4: configuration #1 chosen from 1 choice

```

Also, now when I change it back to the old mode, it doesn't work either, which is rather annoying as now I don't have any music on it (it needs to be formatted each time it changes).

Anyway, if anyone can decypher the logs, that would be great.

- Josh

---

### Post by adam_kimber on 2008-07-18
Right. I need you to restart Ubuntu and then go to the log again. Just found a log viewer under System --> Administration --> System Log. That's cool. I am used to looking through the terminal. Anyway why I say use this as it makes new events bold for a bit. Plug your device in in Mass Storage mode and look at the results. Then unmount it. YOu should get a one line message on disconnect. Something like this. ```
Jul 18 19:40:27 zia kernel: [ 1445.384543] usb 4-6.4: new high speed USB device using ehci_hcd and address 6
Jul 18 19:40:27 zia kernel: [ 1445.477808] usb 4-6.4: configuration #1 chosen from 1 choice
Jul 18 19:40:27 zia kernel: [ 1445.570725] usbcore: registered new interface driver libusual
Jul 18 19:40:27 zia kernel: [ 1445.583088] Initializing USB Mass Storage driver...
Jul 18 19:40:27 zia kernel: [ 1445.583579] scsi8 : SCSI emulation for USB Mass Storage devices
Jul 18 19:40:27 zia kernel: [ 1445.584050] usbcore: registered new interface driver usb-storage
Jul 18 19:40:27 zia kernel: [ 1445.584053] USB Mass Storage support registered.
Jul 18 19:40:33 zia kernel: [ 1452.105808] scsi 8:0:0:0: Direct-Access     Meizu    MiniPlayer       1.00 PQ: 0 ANSI: 2
Jul 18 19:40:33 zia kernel: [ 1452.110526] sd 8:0:0:0: [sdc] 15908864 512-byte hardware sectors (8145 MB)
Jul 18 19:40:33 zia kernel: [ 1452.111145] sd 8:0:0:0: [sdc] Write Protect is off
Jul 18 19:40:33 zia kernel: [ 1452.113144] sd 8:0:0:0: [sdc] 15908864 512-byte hardware sectors (8145 MB)
Jul 18 19:40:33 zia kernel: [ 1452.113766] sd 8:0:0:0: [sdc] Write Protect is off
Jul 18 19:40:33 zia kernel: [ 1452.113773]  sdc:
Jul 18 19:40:33 zia kernel: [ 1452.115909] sd 8:0:0:0: [sdc] Attached SCSI removable disk
Jul 18 19:40:33 zia kernel: [ 1452.115942] sd 8:0:0:0: Attached scsi generic sg3 type 0
```
```
Jul 18 19:41:15 zia kernel: [ 1493.908532] usb 4-6.4: USB disconnect, address 6
```

Then attach in the MTP mode and see post the results. I think your log above is incomplete. I might be wrong though....

---

### Post by JoshHendo on 2008-07-19
Connected the device (in hard disk mode though, as I can't see the drive any more, so I want at least that working!).

I still get the specific lines that looks something like "...kernel: [  514.459986] usb 2-2: device descriptor read/8, error -71..."

I am pretty sure that has something to do with what the problem is, but I am not sure.

The line output when I disconnected it looked like:
"Jul 19 19:25:18 Scruffy kernel: [  549.635329] usb 2-2: USB disconnect, address 10"

---

### Post by thekidd1049 on 2008-07-27
hi every one my e100 is connected to my ubuntu and doesnt do a thing. i am kind of a noob with these things but i tried what was listed before and it didnt work, is there any way someone can walk me through this? my e100 is in the right connection format and it is reconized by the computer. it just wont do anything else...help please? 
thank u

tyler

---

### Post by JoshHendo on 2008-07-29
thekidd1029:

I have posted an post [here]("http://ubuntuforums.org/showthread.php?t=860046") on how to get it so you can use the iriver in UMP mode (and how to convert it to UMP mode if it is not already). There are two modes, and I can't seem to get MTP working (which is a shame, because it does make managing playlist etc easier).

- Josh

---

### Post by Grippon on 2008-10-03
I've been tinkering with the iRiver E100/ubuntu/banshee thing for a bit now.
if you are running Hardy you might need to:
1. install libmtp 3.3
2. build banshee from source version (1.2.1)
3. edit  /etc/udev/rules.d/45-libmtp7.rules
   Add the lines 
```
# iRiver E100
ATTR{idVendor}=="4102", ATTR{idProduct}=="1141", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
```
restart udev
4. Back up your iriver and format it for mtp
5. At this point we should be able to use the iRiver with banshee. But I have had no luck yet.
 mtp-detect returns alot of info and this at the very end

```
WMPInfo.xml Does not exist on this device
PTP: Closing session
usb_clear_halt() on INTERRUPT endpoint: Broken pipe
OK.
```

then it kills the usb connection, no surprise there ... I guess I'll just have to wait.

---

### Post by Grippon on 2008-10-06
For those that need a quick fix for playlists:
I hacked up a perl script that converts m3u to pla for the iRiver E100. I don't know if if works for other devices, Use it at your own risk. This should help until the community gets the E100 working with MTP.

Process:
1. Mount your iRiver E100 in UMC Mode ( Hard disk mode)
2. Use your banshee/rhythmbox/songbird or some such program to create an m3u playlist
3. Save the m3u to a file
4. Open a terminal and run 
```
m3u2pla.pl --infile=/path/to/infile.m3u --outfile=/path/to/outfile.pla --mount=/path/to/iriver-e100/mount
```

5. Copy the pla file to /path/to/iriver/Playlists

Hope this helps.

---

### Post by cmire on 2008-12-06
Hi Grippon,

I tried your script, but it didn't work for me. My E100 has firmware 1.09, but I can't imagine playlist code changed greatly between that version and 1.10. I'm using Kubuntu Hardy and Rythmbox 0.11.5.

I got a sample playlist emailed to me from iRiver support, and when I took a closer look at that versus what your script is generating, here are some differences I found.

The hex values for the character preceding the filename appear to be incorrect.

Your script: hex 00
Sample file: hex 14 (this is hex 14 for mp3, hex 13 for wma)

For the final file in the playlist,

Your script: hex 00
Sample file: hex 0F

When viewing the pla file in the hex editor, these values are found in this position (the bold dot):

**.**.\.M.u.s.i.c.\.f.o.l.d.e.r._.n.a.m.e.\.song...mp3...

Also, the initial offset in the header appears to be off by a couple of hex 00's.

Here's the sample file I got if you would like to review it.

BTW, I tried manually editing the pla file created by your script to fix the differences, but the E100 went from seeing the songs in the playlist to an empty playlist. Neither the playlist from your script or my edited playlist actually worked, though.

---

### Post by cmire on 2008-12-06
Tried the script again and it works nicely! :D

I had commented out the lines

$hxdrcnt = chr($namecnt);
$pack_string = "\x00$hxdrcnt";

because I thought the characters generated were strange. This was part of my problem. I uncommented those lines again.

The original problem I had was that the absolute path to the file needed to be corrected in the m3u playlist so that it would be from the E100 device perspective, not the Ubuntu system perspective:

/Music/folder/filename.mp3

Not: /media/disk/Music/folder/filename.mp3 or /home/user/music/folder/filename.mp3 and so forth.

When I view the playlist in the E100, there is still a strange character in front of each song in the list -- but I don't care because it works!

---

### Post by Grippon on 2009-10-07
I wrote the script for ogg files I/we may want rework the script to  discover the file type and use the right hexcode.  And the --mount option is goofy...confusing. I just couldn't think of a better way to do it at the time. I'm very glad it works for you!

---

