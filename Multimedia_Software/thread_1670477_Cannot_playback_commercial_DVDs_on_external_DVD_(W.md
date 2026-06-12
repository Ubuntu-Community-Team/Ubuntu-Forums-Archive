---
title: "Cannot playback commercial DVDs on external DVD (Wrong region/mounting issues?)"
date: 2011-01-19
forum: Multimedia Software
---

### Post by ZombieGhandi on 2011-01-19
Hey guys,
Having issues getting my external dvd drive to play nice with 10.10. The usual horses have been beaten thoroughly.

1.) I've installed Medibuntu
2.) I've grabbed libdvdcss2, libdvdread, run the install script, etc., etc.

3.) I've *attempted* to check the region, with no avail. When I try a regionset, it offers the following complaint:

ERROR: Could not open disc "(null)"!
Please ensure there is a readable CD or DVD in the drive.

4.) The drive and disc(s) are all operational, as they work on different partitions and/or machines fine.

VLC/Totem will, briefly, open the menu for a given DVD. The menu video will briefly play, sputter, then die, which sounds like a region issue.

Any idea why the regionset isn't working? Perhaps it's not mounting right?

---

### Post by mc4man on 2011-01-19
While whether a region is set on the drive may not be the cause of your issue it's certainly worth checking (having a region set isn't necessarily a requirement though doesn't hurt to set **once**

You most likely just need to point regionset to the drive (and have a disk in the drive
So, insert a disk in drive, then run this in a terminal, find the drive in the listing and get the /dev/sr[COLOR="Blue"]X[/COLOR] for it.
```
sudo lshw -C disk
```
Then 
regionset /dev/sr[COLOR="Blue"]X[/COLOR]

Ex. here  - my external is /dev/sr2
regionset /dev/sr2

---

### Post by ZombieGhandi on 2011-01-19
Ah ha! You're a prince, I was able to get regionset to work. It's set to region 1 (that's me) That's the good news. Obviously, since the region is correct, there was nothing to change, so my original problem remains. Any other ideas with the playback difficulty?

---

### Post by mc4man on 2011-01-19
If not installed maybe go ahead and install vlc.

Then insert a dvd in the drive - **Close** out any player that starts if any.
**Before **attempting playback of the dvd first go ahead and open your home folder -> View -> show hidden file

Scroll down a bit and locate a folder named .dvdcss, go ahead and delete the folder

Now open a terminal and start vlc w/ just a command of vlc
Once vlc is open go - Media -> Open Disc. For the Disc device enter the /dev/srX that you found above, then click play.
If the dvd doesn't play correctly then copy all the terminal output and post

(note to re-emphasize - insert the dvd first & close out any player, then delete the .dvdcss folder, not the other way around

---

### Post by BicyclerBoy on 2011-01-19
Regionset is of no use & not required if libdvdcss is installed properly.

Region setting/detection can also be avoid with firmware "upgrades" but only for some optical drives.

You still need a player with the latest file sytem navigation/patches to work well.

HandBrake can be used to debug navigation problems (output error console) because of the detailed logs.

---

### Post by mc4man on 2011-01-19
> Regionset is of no use & not required if libdvdcss is installed properly.
Not exactly true - 
While generally having a region set or not doesn't matter, in some cases it does.
> Region setting/detection can also be avoid with firmware "upgrades" but only for some optical drives.
For most use cases in linix RPC1  firmware is not needed.

> You still need a player with the latest file sytem navigation/patches to work well.
Pure nonsense

---

### Post by ZombieGhandi on 2011-01-19
> **mc4man said:**
> If not installed maybe go ahead and install vlc.

Then insert a dvd in the drive - **Close** out any player that starts if any.
**Before **attempting playback of the dvd first go ahead and open your home folder -> View -> show hidden file

Scroll down a bit and locate a folder named .dvdcss, go ahead and delete the folder


A'ight. Did that.

[QUOTE=mc4man]
Now open a terminal and start vlc w/ just a command of vlc
Once vlc is open go - Media -> Open Disc. For the Disc device enter the /dev/srX that you found above, then click play.
If the dvd doesn't play correctly then copy all the terminal output and post
[/QUOTE]

Ok. Did that, and got the crash again.

[QUOTE=mc4man]
(note to re-emphasize - insert the dvd first & close out any player, then delete the .dvdcss folder, not the other way around[/QUOTE]

10-4 ;)

```
phoenix@phoenix-laptop:~$ vlc
VLC media player 1.1.4 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0x2036120] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Blocked: call to setlocale(6, "")
Blocked: call to sigaction(17, 0x7fc628156b20, 0x7fc628156a80)
Warning: call to signal(13, 0x1)
Warning: call to signal(13, 0x1)
Warning: call to srand(1295835660)
Warning: call to rand()
Blocked: call to setlocale(6, "")

(process:5188): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.
Warning: call to signal(13, 0x1)
Warning: call to signal(13, 0x1)
Blocked: call to setlocale(6, "")
Warning: call to rand()
Warning: call to signal(13, 0x1)
Warning: call to rand()
Warning: call to rand()
Warning: call to rand()
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdnav: DVD Title: JCVD_DC_US
libdvdnav: DVD Serial Number: cd3565d3        
libdvdnav: DVD Title (Alternative): JCVD_DC_US
libdvdnav: Unable to find map file '/home/phoenix/.dvdnav/JCVD_DC_US.map'
libdvdnav: DVD disk reports itself with Region mask 0x00400000. Regions: 1 2 3 4 5 6 8

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000014b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000001bf
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0001297f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x001d6dd5
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x001d9c92
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x001d9c98
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x001ec92b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x001f04e3
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x001fbb73
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x001fbb79
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x00204398
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x0020439e
libdvdread: Elapsed time 0
libdvdread: Found 6 VTS's
libdvdread: Elapsed time 1
Warning: call to srand(555094)
[0x2577340] main input error: ES_OUT_SET_(GROUP_)PCR  is called too late (pts_delay increased to 300 ms)
[0x2577340] main input error: ES_OUT_SET_(GROUP_)PCR  is called too late (pts_delay increased to 632 ms)
[0x2577340] main input error: ES_OUT_SET_(GROUP_)PCR  is called too late (pts_delay increased to 766 ms)
[0x2577340] main input error: ES_OUT_SET_(GROUP_)PCR  is called too late (jitter of 61068 ms ignored)


```

---

### Post by BicyclerBoy on 2011-01-20
It is not pure nonsense..

Do you think the dvdnav dvdread libraries are perfect & unchanging..both these libs were updated Nov2010 & maybe since.
I had a half dozen DVDs that did not play 1 month ago now they do. 
I know why they play now & I know who to thank.

Various media player projects have invested lots of time (& recently) patching these dvd libs.
These projects are statically linked to these patched libs.
You do not get the benefit without either replacing your system shared libraries or you must use SVN/git or a recent build of a media player.

I suggest the OP tries a recent build of VLC or mplayer.

---

### Post by mc4man on 2011-01-20
> Do you think the dvdnav dvdread libraries are perfect & unchanging..both these libs were updated Nov2010 & maybe since.
Don't recollect saying they were perfect - you said to work "well"
> I had a half dozen DVDs that did not play 1 month ago now they do. 
Would be interested to hear the titles and what software player is now playing them.
Over maybe 3000+ titles that have come across here only a handful that can't be played with unlicensed software players no matter what dvdnav/dvdread version. 
Additionally have found a very few that the commonly used 4.1.3 dvdnav/read can't navigate properly, all of those few are handled fine with dvdnav 1.1.1X
(actually just received a title last week to look at that 4.1.3 can't handle quite right

Whether this particular disk (Jean-Claude Van Damme) is one remains to be seen.
There is also some indication from ZombieGhandi that this occurs with all dvd's he has tried..

> tries a recent build of VLC or mplayer
That would be worth trying, a recent mplayer most likely includes these patches, a recent or current vlc will still use the same dvdnav

ZombieGhandi - 
may as well try this just to see - try having vlc open the main movie directly, either from the open disc menu - "No dvd menus" or cli
```
vlc dvdsimple:///dev/srX[COLOR="Blue"][/COLOR]
```
If it fails or can't find the right title # and if you know the title number for the main movie then it's also available from the Open disc menu or done like - 
```
vlc dvd:///dev/sr[COLOR="Blue"]X[/COLOR]@[COLOR="Blue"]X[/COLOR]

```

the last 4 lines from your vlc output - the first one is typical, that's the default buffer for dvd's (300ms)
the next 2 aren't too bad, just indicate some read/seek trouble
the last one I'm not 100% up on, seems vlc either can't find or read the main menu

(I'm curious about this title so I'll have a copy dropped off sometime this week and see if there is anything noteworthy in regards to dvdnav

Another thing to try is a different dvdnav altogether - dvdnav-1.1.X which is used by xine based players.
Unfortunately the best xine player for dvd's - totem-xine is now only available if you build it

Of the rest xine-ui is a very good player, though a bit to set up - has 'levels' of settings available (it defaults to /dev/dvd
To quickly test with out messing w/ the settings install xine-ui
Then just command line it
```
xine dvd:///dev/sr[COLOR="Blue"]X[/COLOR]
```

(you could also try ripping this title to the hdd in any of several methods...

---

### Post by ZombieGhandi on 2011-01-21
> **BicyclerBoy said:**
> 
I suggest the OP tries a recent build of VLC or mplayer.

[QUOTE=mc4man]
That would be worth trying, a recent mplayer most likely includes these  patches, a recent or current vlc will still use the same dvdnav
[/QUOTE]

Thanks guys. Got the latest vlc source code and built it. The issue persists. Oddly enough, after powering down/up my machine, that build no longer works. I get a segmentation fault. Not really here nor there, though.

[QUOTE=mc4man]
may as well try this just to see - try having vlc open the main movie  directly, either from the open disc menu - "No dvd menus" or cli
[/QUOTE]

Tried this and I get the same behavior as the menu. The movie starts, sputters, chokes out and (sometimes) crashes.

[QUOTE=mc4man]
Another thing to try is a different dvdnav altogether - dvdnav-1.1.X which is used by xine based players.
Unfortunately the best xine player for dvd's - totem-xine is now only available if you build it

Of the rest xine-ui is a very good player, though a bit to set up - has 'levels' of settings available (it defaults to /dev/dvd
To quickly test with out messing w/ the settings install xine-ui
Then just command line it
[/QUOTE]

Ok. Tried xine-ui. It fared slightly better, actually. Made it a minute or two into the movie, but again finally, it choked out.

And just to be clear ......

[QUOTE=mc4man]
Whether this particular disk (Jean-Claude Van Damme) is one remains to be seen.
There is also some indication from ZombieGhandi that this occurs with all dvd's he has tried..
[/QUOTE]

Yeah, I've tried at least 1/2 a dozen movies. All have the same problem.

[QUOTE=mc4man]
you could also try ripping this title to the hdd in any of several methods... 	
[/QUOTE]

Yeah, that's a possibility, but I'll probably just flip over to my Windows partition, which is a shame. Oh well, I *do* appreciate all the grunt work gentlemen, thanks again!

---

### Post by mc4man on 2011-01-21
A bit of a follow up on that title - JCVD

There is no structure protection on the disk though there may be a slight  authoring  issue where it's possible from main menu - movie could bring one to the chapter menu instead. No big deal and may not happen.

Plays here quite fine w/ both the 4.1.3 and 1.1.19 dvdnav, on both internal and external drives
so I'd think this is a local hardware issue - the info isn't getting accessed in a timely enough fashion for some reason (and your drive may be just fine itself.

(the main movie is title one if wanting to try w/ a cli mplayer
```
mplayer -dvd-device /dev/sr[COLOR="Blue"]2[/COLOR] dvd://1
```
or
```
mplayer -dvd-device /dev/sr[COLOR="Blue"]2[/COLOR] dvdnav://
```

Ex. vlc

> vlc dvd:///dev/sr2
VLC media player 1.2.0-git Twoflower (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0x9b2117c] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Blocked: call to setlocale(6, "")
Blocked: call to strerror(2)
Blocked: call to strerror(2)
Blocked: call to strerror(2)
Blocked: call to strerror(2)
Blocked: call to strerror(2)
Warning: call to srand(1295548602)
Warning: call to rand()
Blocked: call to setlocale(6, "")

(process:4463): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdnav: DVD Title: JCVD_DC_US
libdvdnav: DVD Serial Number: cd3565d3        
libdvdnav: DVD Title (Alternative): JCVD_DC_US
libdvdnav: Unable to find map file '/home/doug/.dvdnav/JCVD_DC_US.map'
libdvdnav: DVD disk reports itself with Region mask 0x00400000. Regions: 1 2 3 4 5 6 8

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000014b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000001bf
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0001297f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x001d6dd5
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x001d9c92
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x001d9c98
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x001ec92b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x001f04e3
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x001fbb73
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x001fbb79
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x00204398
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x0020439e
libdvdread: Elapsed time 0
libdvdread: Found 6 VTS's
libdvdread: Elapsed time 0
Warning: call to srand(117307)
[0x9bcd524] main input error: ES_OUT_RESET_PCR called
[0x9bcd524] main input error: ES_OUT_RESET_PCR called
 - is now playing fine

Because there is no structure protection you may want to try a rip of the dvd with vobcopy, it could show you if there are any read and or transfer issues

If so
```
sudo apt-get install vobcopy
```
vobcopy should find the disc (mount) on it's own

```
vobcopy -v -m
```

---

### Post by ZombieGhandi on 2011-01-21
Will try a rip, although I'm relatively confident of success. I've played rips before (but never with a specific DVD that I've had trouble playing).

I realize you're (probably) not a computer engineer, but any idea what kind of hardware failure would cause the PC/DVD drive to fail in Ubuntu, but work fine in Windows 7 (this is indeed, the case)? I'd like to bellyache to Asus (PC maker) or Samsung (drive maker) about it, but this little fact makes things difficult. I get the feeling that, some theoretical firmware update for my drive would fix the problem. That is, if Samsung thought much about the drive playing with Linux in the 1st place.

---

### Post by ZombieGhandi on 2011-02-12
Update:

Finally got tired of this, and my cd/dvd burning issues, so I went out and bought a 2nd external optical drive, just to make sure. Wouldn't you know it, it WAS the drive. Odd that it worked in Win7, but not Ubuntu. Oh well, that's how she goes. So, in the interest of never having to pick the perfect external DVD writer again, I'll be taking my overpriced Best Buy external to the grave. The CD burning is flawless and the playback, with a few exceptions, is working as well. 

Thanks again, everyone. How do I mark this as SOLVED?

---

### Post by mc4man on 2011-02-12
> How do I mark this as SOLVED?
I believe if you use the 'thread tools' dropdown there should be an option

(glad you're going again - have no clue as to why there can be diff.'s in cd/dvd drive behavior between win and linux though there clearly are.

---

### Post by ZombieGhandi on 2011-02-13
Thanks. It's now marked SOLVED. 

No idea either. The drives look almost identical. Wouldn't be surprised if they are from the same factory. Going to try swapping the cable with the old drive. You never now, it could simply be a bum cable. At least I have a spare drive for the next Windows/OS X ultraportable that comes home.

---

