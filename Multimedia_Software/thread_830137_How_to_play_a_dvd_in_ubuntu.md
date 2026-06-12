---
title: "How to play a dvd in ubuntu???"
date: 2008-06-15
forum: Multimedia Software
---

### Post by X_CheshireCat_x on 2008-06-15
I cannot get Ubuntu to play DVDs...  i have installed:

ubuntu-restricted-extras
VLC
OGLE
libdvdcss2
libdvdread3

possibly others but i cant remember i have tried so many things.

totem says it cant read the disc
VLC spins the disc then does nothing
OGLE on first attempt opens the first split second of the disc then closes. subsequent attempts results in OGLE closing with no picture. can't i just download a player that will play DVDs after install? VLC works straight after install on my windows machine i'd quite like something that works just as easily...

thanks

---

### Post by pytheas22 on 2008-06-15
If possible, could you try another DVD just so we're sure it's not the disc itself causing the problem?  Also, are you able to play stuff using the same drive in Windows (if you have a dual-boot system)?  All you should really have to do is install ubuntu-restricted-extras, so I want to make sure there's not a media/hardware problem.

You could also give it a shot with mplayer:
```

sudo apt-get install mplayer
```

Once you installed, you have to right-click to tell it to open a menu where you can select the disc to play.

Please report back with the information above and we can take it from there.

---

### Post by X_CheshireCat_x on 2008-06-15
hey.. ive installed mplayer but it doesnt open the disc. the video screen remains blank when i right click and open the disc. 
im not running dual boot on this computer - its 100 ubuntu :) i'm using VLC on another.. i did use VLC on this one when it was on XP and it worked fine...

---

### Post by mc4man on 2008-06-15
Open vlc from the terminal, try to playback a disc and read/post error messages

---

### Post by werries on 2008-06-15
maybe this will help?
[http://www.tech-recipes.com/rx/2765/ubuntu_enable_dvd_playback](http://www.tech-recipes.com/rx/2765/ubuntu_enable_dvd_playback)

---

### Post by rainwalker on 2008-06-15
I'm having the same problem here. This is the output when running Totem from a terminal and trying to play the DVD:
> *** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04

    - Repeat about 50 times, occasionally value changes to 0x05 or similar -

*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x08

*** libdvdread: CHECK_VALUE failed in ifo_read.c:714 ***
*** for cell_playback[i].first_sector <= cell_playback[i].last_vobu_start_sector ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:714 ***
*** for cell_playback[i].first_sector <= cell_playback[i].last_vobu_start_sector ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:714 ***
*** for cell_playback[i].first_sector <= cell_playback[i].last_vobu_start_sector ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:714 ***
*** for cell_playback[i].first_sector <= cell_playback[i].last_vobu_start_sector ***

*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04

    - Repeat about 50 more times, value occasionally changes to 0x05 or similar -

*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x08
OIL: ERROR liboiltest.c 361: oil_test_check_impl(): illegal instruction in mmxCombineAddU
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 60 error_code 11 request_code 140 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)


Then, here is the output while trying to open the DVD with VLC, notice that it's similar:
> libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Attempting to use device /dev/hdc mounted on /media/cdrom0 for CSS authentication
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/dragon/.dvdnav/.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000016b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000008bf
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00000977
libdvdread: Elapsed time 0

 - Repeats about 50 times, only "at" value changes -

libdvdread: Found 12 VTS's
libdvdread: Elapsed time 0
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04

 - Repeats around 50 times, value occasionally changes to 0x06 or similar -

    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x08
The program '.' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 89 error_code 11 request_code 140 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)


Any ideas?

---

### Post by mc4man on 2008-06-15
The first thing to ck. is a region set on the drive? Install regionset then with a _dvd in the drive_ run regionset and see if it says set on this line -  type: set

---

### Post by rainwalker on 2008-06-15
mc4man, does this line have anything to do with that:
> libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1
I haven't installed regionset yet, I was just wondering

---

### Post by bla on 2008-06-15
The players in linux can't set region for hardware.  Play it in windows than restart and try in linux.  Or find some guides to set region in linux using the regionset tool.  remember that if you have a dvd any region other than what you have your player set at, you can't play the disc.  Basically it is impossible to play foreign legal dvd's in linux.  If you try to change the region each time, your hardware will lock after the 5th time to the last region...

You're best bet is watching dvd's in windows until anydvd works in linux.

---

### Post by pytheas22 on 2008-06-15
> Basically it is impossible to play foreign legal dvd's in linux. If you try to change the region each time, your hardware will lock after the 5th time to the last region...

I'm pretty sure this isn't correct...I don't know whether or Linux can actually change the region setting of the drive.  But I know it can just ignore the region setting and play whatever it wants.  I play European DVDs in mplayer on my American DVD drive all the time.  So it is definitely possible.

EDIT: from [http://www.linux.com/base/ldp/howto/DVD-Playback-HOWTO/prep.html:](http://www.linux.com/base/ldp/howto/DVD-Playback-HOWTO/prep.html:)

2.3. Setting the DVD Region

All DVD drives (except for RPC Phase I drives made in 1999 or before) enforce region playback restrictions in the drive firmware and consequently are supposed to be set to a specific region before they can play back discs from that region (and only that region). In reality, most Linux DVD playback software can bypass the DVD drive's built-in region locks, but it takes extra time for the software to break the region lock, and it is better to avoid the complications of region locks if you can.

For the small minority of readers who own RPC-I drives, you do not need to do anything: your drive is already capable of handling DVDs from all geographical regions. These drives are old enough by now that everybody who has one of them probably knows already that they have one.

For the majority of readers who have RPC-II drives, there are several options available:
> 
   1. If you only watch discs from one region, the easiest option is to use the regionset program to set your DVD drive to the correct region.
   2. If you want to watch discs from multiple regions, you can try to find a firmware upgrade for your DVD drive in the firmware-flash.com collection of unofficial firmware files. Note that most of these files require you to boot to DOS or Windows to install.
   3. You can buy a separate DVD drive for each DVD region that you wish to use. The prices for DVD-ROM drives have dropped low enough to make this strategy feasible.
   4. **Of course, you can simply do nothing, and rely on the built-in ability of Linux software to bypass the region restrictions.** Note that even in this case you should use the regionset program to set the drive to the region that you will be using the most, because an RPC-II drive without a region setting behaves as if all the regions are locked out.

---

### Post by mc4man on 2008-06-15
@ rainwalker
It's pretty simple - you should have a region set on the drive. It won't prevent you from playing titles from other regions, the player will brute force the keys and in most cases is successful. (the exception would be _some structure protected_ disks) There is no downside to setting the region and with RPC-II protected disks it's a must.
This might not be your problem but is the best 1st. thing to ck.

for example - my drive is set to region 1, playing a region 2
```
doug@doug-desktop:~$ vlc
VLC media player 0.8.6e Janus
libdvdnav: Using dvdnav version 0.1.10 from http://dvd.sf.net
libdvdread patched to play DVDs with DVD-Movie-Protect
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: HERO
libdvdnav: DVD Serial Number: 318F8888
libdvdnav: DVD Title (Alternative): HERO
libdvdnav: Unable to find map file '/home/doug/.dvdnav/HERO.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fd0000. Regions: 2

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000013d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000032af
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00012878
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x002fb1ed
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x00335e40
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x00356e41
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x00367a17
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x00391682
libdvdread: Elapsed time 0
libdvdread: Found 6 VTS's
```

---

### Post by rainwalker on 2008-06-15
So what are you saying I should do?
And how come I haven't had to worry about this on any other computers I've set up Ubuntu on (3 of them)?

---

### Post by mc4man on 2008-06-15
> So what are you saying I should do?
We're just checking run
```
sudo apt-get install regionset
```
with a dvd in the drive run ```
regionset
```
here's what a set drive looks like
```
doug@doug-desktop:~$ regionset
regionset version 0.1 -- reads/sets region code on DVD drives
Current Region Code settings:
RPC Phase: II
type: SET   [COLOR="Red"]<-[/COLOR]
vendor resets available: 4
user controlled changes resets available: 4
drive plays discs from region(s): 1, mask=0xFE

Would you like to change the region setting of your drive? [y/n]:n
```
If it looks like that answer n and exit. If it isn't set answer yes and select region 1 and exit.
If it _wasn't set_ before trying the same disk go to home dir. (show hidden files) open the .dvdcss folder and delete everything inside. If it was set post back

---

### Post by rainwalker on 2008-06-15
Yep, it's set

---

### Post by mc4man on 2008-06-16
What's the name of the title?
with the dvd in the drive try this 
```
 export DVDCSS_METHOD=title && vlc dvd://
```

---

### Post by shadedream on 2008-06-22
I'm having the same issue and running the above reports in failure as well. I did notice a line in the output that seemed odd:

libdvdnav: Unable to find map file '/home/shadedream/.dvdnav/SHAUN_OF_THE_DEAD.map'

is it supposed to be looking in my home directory? It gets the proper DVD title etc (as obvious from the line above). The weird thing about this whole thing is my machine was playing DVDs perfectly fine last week. Im guessing a software update or something introduced something wonky?

---

### Post by mc4man on 2008-06-22
> libdvdnav: Unable to find map file '/home/shadedream/.dvdnav/SHAUN_OF_THE_DEAD.map'
That's an expected line, of no consequence

post your terminal output of errors

---

### Post by shadedream on 2008-06-22
well I was getting the same errors as the first page but after using the following:

sudo /usr/share/doc/libdvdread3/examples/install-css.sh

Im now getting the following output:

VLC media player 0.8.6e Janus
/home/shadedream/.themes/Sandwich-black/gtk-2.0/panel.rc:61: Unable to locate image file in pixmap_path: "Menu-Menubar/menubaritem.png"
/home/shadedream/.themes/Sandwich-black/gtk-2.0/panel.rc:64: Background image options specified without filename
libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Using libdvdcss version 1.2.5 for DVD access
libdvdnav: DVD Title: SHAUN_OF_THE_DEAD
libdvdnav: DVD Serial Number: 3170b729
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/shadedream/.dvdnav/SHAUN_OF_THE_DEAD.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000015a
libdvdread: Elapsed time 3
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x0000db72
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0001b421
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x00292582
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x00292586
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x002ba399
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x002ba39d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x0034b625
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x0034b629
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x0036ff76
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x0036ff7a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x003a0bfb
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x003a0bff
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x003ae167
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x003ae16b
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_08_0.VOB at 0x003dcfcc
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x003dcfd0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_0.VOB at 0x003e7f2d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_1.VOB at 0x003e7f31
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_0.VOB at 0x003eb2a4
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_1.VOB at 0x003eb2a8
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_11_0.VOB at 0x003ed4a7
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_11_1.VOB at 0x003ed4ab
libdvdread: Elapsed time 0
libdvdread: Found 11 VTS's
libdvdread: Elapsed time 5
libdvdnav: ifoRead_PGCI_UT failed - CRASHING!!!
vlc: vm.c:210: ifoOpenNewVTSI: Assertion `0' failed.
Aborted

---

### Post by shadedream on 2008-06-22
Ok I think the libdvdcss command must have fixed it because just for kicks I ejected the DVD, and remounted it, and its working now... arg. I wouldnt have been so annoyed by this if it hadnt worked in the first place a week ago. Very odd.

---

### Post by mc4man on 2008-06-22
While i don't think that title has structure protection out of the ordinary give me a few min. and I'll write you a quick guide to adding a patched dvdnav4 - the error is very similar to what you'd expect with certain sp's. I use it , doesn't hurt to have, from my prev post
> libdvdread patched to play DVDs with DVD-Movie-Protect

In the meantime you know the region has been set on your drive to region 1?
And you did try cleaning out your .dvdcss folder in home dir.?

Didn't see your new post - good to hear, for some reason some systems need to use the older ver. of libdvdcss2
> libdvdread: Using libdvdcss version 1.2.5 for DVD access

---

### Post by prabath_fun on 2008-06-23
Hi,
 I have got some problem with playing DVD. I have installed mplayer from source code in Ubuntu 8.04 (in wubi) with ./configure, sudo make, sudo make install after package is extracted. Installation went fine witout problem. Then I tried to play an DVD from terminal with
mplayer dvd://3 -dvd-device /dev/hdc
command. It playes, but, I am getting only audio. No video. Worked without any problem in Fedora 8 earlier. But Now I am using ubuntu, because of huge support and impressed with it.
Let me know how to remove this installed mplayer?


Also I installed .deb package available in ubuntu packages website. But, while trying to play DVD I am geting the following message.
"Error opening/initializing the selected video_out (-vo)device"

Please update me, what is the wrong I am doing?
Prabath

---

### Post by pytheas22 on 2008-06-23
Unfortunately there's no easy way to uninstall mplayer if you compiled it from source.  The only way is to manually find all the files it created and remove them.  That's why it's almost always better to use a .deb package instead of build from source; then you can easily uninstall software using the apt-get remove command.

As for making the video play: start mplayer with the command:
```

gmplayer
```

so that you get a GUI.  Right-click on the mplayer window and select Preferences.  Under the Video tab of the Preferences window you can select different video output drivers.  Try some different ones and see if it makes a difference.

It could also help to turn off desktop effects and see if that solves the problem; then you know it's related to compiz.

Also, are you able to play video of any kind (not just DVD), and are you able to play video using Totem?

---

### Post by prabath_fun on 2008-06-24
Thanks. I got it with mplayer .deb package installation. I selected different codec for audio and video and checked. For few codecs mplayer hangs.

Now, I am looking for enabling 5.1 surround with Mplayer. My Mother board got 5.1 support. Help me to enable 5.1.
With Thanks,
Prabath

---

### Post by pytheas22 on 2008-06-27
> Now, I am looking for enabling 5.1 surround with Mplayer. My Mother board got 5.1 support. Help me to enable 5.1.

I don't have any experience with surround sound stuff, but this [NetBSD wiki]("http://wiki.netbsd.se/How_to_use_5.1_surround_sound_with_NetBSD") says that to enable 5.1 surround sound, you should run mplayer with the argument:
```

-channels 6
```

It should be the same for Linux.  So open a command line and start mplayer with:
```

mplayer -channels 6 [file name]
```

If this works, you could change the mplayer options so that it always starts with this argument.

---

### Post by bla on 2008-07-18
OK, some clarification is needed.

(1) You can not play DVD's in Linux without initializing the region code at least once. (think new drive)  Right?

(2) I was talking about RPC2 drives.  As I said, and was confirmed here, an RPC2 drive allows you to change the region code up to 5 times and this includes the initial initialization.  So in our example here, you would have 4 changes left after init. This is a fact so far.

(2a.) Are you saying that if you init the drive to region 1(N.A) and then insert a region 2 discs to play...the drive will not automatically change the region to region 2, leaving you with 3 changes left until region is locked???

Because if this is true, it is news to me.  Hope it is true but I wouldn't claim it unless I knew for sure it is true because it could mean having to throw away a drive if people missunderstand.

If 2a is true, what is the fine print???  

What application must be installed to bypass region protection and prevent drive lock? 

What player must be used?  Surely not all players ignore region protection?

Are you assuming here that people are buying certain model drives and flashing them to be region free?

---

### Post by mc4man on 2008-07-18
> 2a.) Are you saying that if you init the drive to region 1(N.A) and then insert a region 2 discs to play...the drive will not automatically change the region to region 2, leaving you with 3 changes left until region is locked? No player I've ever used will change the region setting on a drive, and certainly _no unlicensed open source player ever will or even offer to_. IIRC some licensed closed source players will offer to change the region setting when presented with a region mismatch. (powerdvd, windvd, maybe lindvd)
There is no reason to ever change your region under normal circumstances.
I routinely play R2 and R4 disks on my R1 drive (i have 4 resets left and always will)

> If 2a is true, what is the fine print??? 
> 
It won't prevent you from playing titles from other regions, the player will brute force the keys and in most cases is successful. (the exception would be some structure protected disks
And the other exception is most matshita dvd drives will not allow access to encrypted sectors when there is a region mismatch

---

### Post by bla on 2008-07-18
Thanks, that is very interesting.  On widows, players like powerdvd, windvd do change the region code and thus reduce the counter till a lock.  There is a method to bypass this in windows but that is not the topic.

Glad to hear linux tries to ignore the region.  The matshita issue is intersing, since most laptops have matshita drives, inluding Asus laptops.  So this in practice is an issue.  

I myself have an Asus and can not play dvd's in linux other than region 1.

No probs in XP because there I am able to bypass region protection fully.

So, is there a method to bypass this issue in Linux (for everyone)?

---

### Post by mc4man on 2008-07-18
> So, is there a method to bypass this issue in Linux (for everyone)?
I'm not sure what issue you're referring to so here's both.
As far as matshita drives - for _most laptop drives_ there's nothing that can be done, there is no rpc1 firmware available. I believe there may be a workaround for some models if it's in a Mac though. There is limited firmware available for desktop models  [http://forum.rpc1.org/index.php](http://forum.rpc1.org/index.php)

As far as when playback (cracking of keys) is prevented or limited in scope in the instance of a region mismatch and structure protection there is a work around. Many players will access .dvdcss first for a folder associated with the volume name of the disk. If one is found they'll use the stored keys for decrypting rather than thru the disk. So all you need to do is provide the proper key files in there.

There's 2 possible ways to acquire the keys

In my case I have several boxes with 2 dvd drives so I've set one drive on one of them to region 2, the other drive to region 4. (I never watch dvds on this box anyway). I'll insert the disk, start up vlc and then copy the proper folder to a flash drive and transfer  to .dvdcss in the box I do watch with.
The other way would be to have a 'friend' with the _same disk_ and the proper region set drive, ect.

edit: an interesting post from one of the programmers of 'anydvd' concerning matshita drives (you could pretty much substitute vlc for anydvd in terms of theory)
[http://club.cdfreaks.com/637240-post2.html](http://club.cdfreaks.com/637240-post2.html)

---

