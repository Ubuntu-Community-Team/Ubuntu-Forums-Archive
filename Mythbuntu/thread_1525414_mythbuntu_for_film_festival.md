---
title: "mythbuntu for film festival"
date: 2010-07-06
forum: Mythbuntu
---

### Post by webdevelopment on 2010-07-06
i want to use mythbuntu to project dvd video files for a film festival

i have some questions:

1) is this recommended for mythbuntu
2) what is the fastest and easiest way to take all kinds of dvds, from non-commercial to commericial dvds, onto the hard drive in a format that mythbuntu can play?
3) any tips for doing this to avoid having any technical problems?  its really bad if you are projecting a film for 100 people and the system fails

---

### Post by nickrout on 2010-07-06
1. mythbuntu can do this **provided** your DVD's are readable by linux. DVD manufacturers are continually introducing new ways to makes discs unreadable by computers.

2. myth has a ripping function that enables you to load the dvds onto your system.

3. test thoroughly before use!

---

### Post by laffinet on 2010-07-06
Do you want to use mythbuntu or mythtv to play those DVDs. Mythbuntu is the distro, mythtv is the application within the distro.

I wouldn't use mythtv for playing DVDs. Just use any distro (standard ubuntu will do) and then vlc for playing DVDs. Or totem.
Or, if you want the media centre appearance, use xbmc.

There are many ways to copy the dvds onto the hard drive. If you are not worried about space the easiest and quickest is via command line:

```
dd if=/dev/dvd of=/somelocation/dvdname.iso
```

---

### Post by nickrout on 2010-07-06
> **laffinet said:**
> Do you want to use mythbuntu or mythtv to play those DVDs. Mythbuntu is the distro, mythtv is the application within the distro.

I wouldn't use mythtv for playing DVDs. 

I might, if I wanted viewers to see a nice interface with metadata and pretty fanart before playing each movie. However if you just want to hit play and start a movie on an otherwise blank screen your idea may be preferable. > 

Just use any distro (standard ubuntu will do) and then vlc for playing DVDs. Or totem.
Or, if you want the media centre appearance, use xbmc.

There are many ways to copy the dvds onto the hard drive. If you are not worried about space the easiest and quickest is via command line:

```
dd if=/dev/dvd of=/somelocation/dvdname.iso
```

That won't work for an encrypted DVD. The encryption keys are NOT stored in the iso9660 filesystem. 

To get a vob of the main title try:

mplayer dvd://1 -dumpstream -dumpfile title.iso

where 1 is the title number for the main title.

---

### Post by webdevelopment on 2010-07-07
thanks everyone... so i'll want to rip the DVD's to the hard drive, most are unecrypted indenpendent film submissions in dvd format, some will be HD avi files that the filmmaker will electronically deliver the file (less plastic use and better for the environment)...

so i need to know how to rip dvd's into the library

then to copy avi files into the library

then to copy commercials and intros into the library and be able to make a playlist/schedule for a day or a week

from what i know all i have to have is mythbuntu installed and the mythvideo plugin...

i have myth installed but its asking me for mysql information to install mythvideo and i dont have mysql installed as far as i know on my laptop so i'm stuck at this step...

is there a place that lists each component/plugin of myth and what exactly it does and why exactly i might need it?

what does myth do by itself without any plugins?

what does mythtv add to the system?

what does mythvideo add to the system?

how reliable is all of this and on a turion 64x2 laptop with a nvidia card will i have professional level playback (no skips, delays, lag, glitches, freezes) while screening a film to a large audience who have paid admission and will get really mad with technical errors?  i also have a bigger desktop with hdmi outputs and 4cpu's...

---

### Post by webdevelopment on 2010-07-07
> **laffinet said:**
> Do you want to use mythbuntu or mythtv to play those DVDs. Mythbuntu is the distro, mythtv is the application within the distro.

I wouldn't use mythtv for playing DVDs. Just use any distro (standard ubuntu will do) and then vlc for playing DVDs. Or totem.
Or, if you want the media centre appearance, use xbmc.

There are many ways to copy the dvds onto the hard drive. If you are not worried about space the easiest and quickest is via command line:

```
dd if=/dev/dvd of=/somelocation/dvdname.iso
```

can you tell me more about what you are saying here? i dont quite understand?

are you saying just copy the dvd file to the hard drive and play with any old player instead of mythtv?

i think i need clarification of what exactly is mythbuntu and mythtv and all its various plugins and options...

i just want a way to control the video files on my screen and play them back from my hard drive as opposed to optical discs that can skip and have menus and lack any intro or ability to put in sponsors commericals... so a scheduler, library, GUI, and playlist would be good...

ideas?

---

### Post by webdevelopment on 2010-07-07
after doing research i see that myth is for recording tv more than playing ripped dvd's

so now i need to know which is the best player and codecs to get HD quality video out of my computer to play ripped DVD's

i think i need to get k9copy to rip then some player that can schedule/make a playlist

---

### Post by nickrout on 2010-07-07
mythtv is first and foremost a tv recorder and playback machine. It is also a great all round media centre playing back videos (including ripped dvds) and music and photos etc.

However if you don't need the tv recoding functions you would be quicker and simpler to use xbmc, it will do all you want.

mythtv and the mythvideo plugin need a mysql database to store all metadata and settings in. It's a pain for something like you want to do.

xbmc also uses a database but it is hidden from you during setup - ie you don't need to bother setting it up or password or anything.

If you want suggestions about how to set up xbmc for your use let me know. PM me your email address and I'll email you.

---

### Post by laffinet on 2010-07-07
Plus you mentioned that you want to create playlists, I'm assuming to play several videos in a row without having to manually start and stop videos.

I don't think that's posssible with mythtv.

Again, you might be better off using xbmc, which supports playlists for videos, afaik.

One of the things you should figure out first is what formats the videos, DVDs etc. are that will be given to you and how to transfer, copy, rip them to your hard drive.

```
dd if=/dev/dvd of=/somelocation/dvdname.iso
```

This will copy the contents of a dvd to your hard drive, to a file called dvdname.iso in the folder /somelocation

From here it can be played with xbmc, vlc, etc.

To use this, open a terminal (Accessories -> Terminal), type the command I've given you and it should copy the DVD.

---

