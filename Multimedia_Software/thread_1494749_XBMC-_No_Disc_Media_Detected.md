---
title: "XBMC- No Disc Media Detected"
date: 2010-05-27
forum: Multimedia Software
---

### Post by ghostborg on 2010-05-27
XBMC gives me an error that "No Disc Media Detected" for every DVD movie protected/unprotected I try to play using the play icon at the bottom.
DVD movies play fine using the Totem Movie Player.
Tried changing out the drive.
Tried changing between IDE and SATA interface.

Was able to hook up a DVD drive via usb and it played using XBMC but not using the play button had to navigate to it through Video section, not practical for household users.
Searched around the Net but did not see anything solutions.


Ubuntu 10.04 AMD64

Thanks.

---

### Post by sisco70 on 2010-05-27
Same problem with XBMC 9.11 and Ubuntu 10.04  (Intel Dual Core E5300, HD and DVD with SATA).
I've tried in AHCI or IDE MODE without results.

dmesg output after inserted a copyrighted DVD:

```
[ 1649.032719] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK  driverbyte=DRIVER_SENSE
[ 1649.032723] sr 3:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 1649.032726] sr 3:0:0:0: [sr0] Add. Sense: Read of scrambled sector  without authentication
[ 1649.032731] sr 3:0:0:0: [sr0] CDB: Read(10): 28 00 00 3a 17 1a 00 00  02 00
[ 1649.032738] end_request: I/O error, dev sr0, sector 15228008
[ 1649.032742] __ratelimit: 18 callbacks suppressed
[ 1649.032744] Buffer I/O error on device sr0, logical block 3807002
[ 1649.032747] Buffer I/O error on device sr0, logical block 3807003
[ 1649.042002] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK  driverbyte=DRIVER_SENSE
[ 1649.042005] sr 3:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 1649.042008] sr 3:0:0:0: [sr0] Add. Sense: Read of scrambled sector  without authentication
[ 1649.042013] sr 3:0:0:0: [sr0] CDB: Read(10): 28 00 00 3a 17 1a 00 00  02 00
[ 1649.042019] end_request: I/O error, dev sr0, sector 15228008
[ 1649.042022] Buffer I/O error on device sr0, logical block 3807002
[ 1649.042024] Buffer I/O error on device sr0, logical block 3807003
[ 1649.057126] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK  driverbyte=DRIVER_SENSE
[ 1649.057130] sr 3:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 1649.057133] sr 3:0:0:0: [sr0] Add. Sense: Read of scrambled sector  without authentication
[ 1649.057138] sr 3:0:0:0: [sr0] CDB: Read(10): 28 00 00 3a 17 1a 00 00  02 00
[ 1649.057144] end_request: I/O error, dev sr0, sector 15228008
[ 1649.057148] Buffer I/O error on device sr0, logical block 3807002
[ 1649.057150] Buffer I/O error on device sr0, logical block 3807003

```But using Gnome and Movie Player i can watch dvd (dmesg still outputs same errors)...

---

### Post by DrTebi on 2010-06-02
I can confirm this problem, however, there is a workaround so that you can still access your DVD drive:

create a symbolic link in your home directory to the /media/ directory, call it e.g. "Media":

# cd
# ln -s /media/ Media

Then open XBMC and do "Add Source" in e.g. your Video section, in the popup window choose "Browse", browse to "Home Folder" and then to the newly created "Media" folder. Click "OK", then give the source a name, click "OK" again.

Now just insert your DVD, let Ubuntu mount it, then in XBMC you can access it by browsing to the "Media" folder and in there by choosing whatever Ubuntu named the DVD... in my case "Avengers 63 D 7" :)

With this it takes two clicks/keystrokes more, but otherwise everything works just as usual.

It seems a bug report has been opened for this:
[http://trac.xbmc.org/ticket/8026](http://trac.xbmc.org/ticket/8026)

---

### Post by ghostborg on 2010-06-02
Thanks for the info DrTebi:guitar:

---

