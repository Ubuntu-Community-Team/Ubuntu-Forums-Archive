---
title: "CD play problem"
date: 2008-05-24
forum: Multimedia Software
---

### Post by dfpd62 on 2008-05-24
Hi Folks

Have had a few weird problems since I upgraded to Hardy, with this one I cannot play audio CD's with any of a variety of players, Amarok,VLC,Xine,Helix,KSCD...Ect.
When an audio cd is loaded, choosing "open with Amarok" launches Amarok, the cd drive light flickers And nothing else happens.
The disk can be browsed with Dolphin, and I have tried various CD's, Including a disk just burned on the same drive (after having to search forums to make K3B convert audio files to CD, which it did quite happily before Hardy upgrade (had to install libk3b2-extracodecs)).

Any help appreciated.

D

---

### Post by ARlyLngUsrNameJustBecause on 2008-05-24
Im having similar problems. Try opening Amarok or some of the other players from the console. When they crash out they should print out some error messages. Hopefully that will be usefull. Mine either just says "segmentation fault" or depending on the program something about not being able to lock the optical drive.

Maybe it would be helpful if we compared setups. Are you using the 32bit or 64bit version? and what kind of hardware do you have? Im using the 64bit version of Ubuntu. I have an AMD Athlon x2, ASUS Nvidia board, ASUS dvd burner and im just using the onboard audio. I think its a realtek chip.

---

### Post by mc4man on 2008-05-24
on the kubuntu side after the disk shows up on desktop what is the device node shown when you mouse over?

---

### Post by dfpd62 on 2008-05-25
Device Node /dev/scd1, and my players dont crash, just nothing shows in their playlist boxes. this is 32bit Hardy, athlon xp2500 1gb Ram, dont know what difference this makes, because it all worked with every version since Dapper (I apply all updates).
The machine has an LG DVD ROM drive ( /dev/scd0 )and a Sony CDRW drive (/dev/scd1 ),tried both.
I can read and rip from both drives and burn discs with the Sony, they just wont play audio CD's .
I have been running FreeBSD and Linux for 10 years now, and this is just weird. 

starting Amarok from the command line I get this output
"dd@mulberry:~$ amarok
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x809db78 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x809db78 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
        StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)"


D

---

### Post by dfpd62 on 2008-05-25
Hi Again.

As you can see from this screenshot, KSCD can see the disk, grab the cddb info, press play and nothing happens, even the eject button works.
Am I just doing something dim....

---

### Post by dfpd62 on 2008-05-25
Update,
Got vlc and amarok to play CD's by changing default device from "/cdrom" to "/dev/scd1".
KSCD problem is still baffeling!!!, maybe thats why they removed it from the default installation. 

D

---

### Post by ARlyLngUsrNameJustBecause on 2008-05-25
It looks to me from your output that your problem probably isnt related to mine. the reason I was wondering if there were any similarities in the setups that could affect the problem and give a hint as to where the problem might be but thats a mute point if its not the same problem. good luck with yours.

---

