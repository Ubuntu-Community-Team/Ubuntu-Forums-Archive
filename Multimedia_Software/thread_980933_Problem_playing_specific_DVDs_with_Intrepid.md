---
title: "Problem playing specific DVDs with Intrepid"
date: 2008-11-13
forum: Multimedia Software
---

### Post by Angelos72 on 2008-11-13
Hi all,
I am having trouble playing a certain DVD using intrepid. What is funny is that the exact same DVD plays great on Hardy (which is installed on another PC).

Specific symptoms are:

- Totem --> It seems that it is trying to start the DVD menu (shows total time 12 seconds), but never starts anything

- VLC --> It shows the DVD menu alright, but when I select "start movie" I get no picture and just choppy sound of poor quality.

-Mplayer --> the clock works as if the movie is actually played, but I get no picture or sound.

[COLOR="Red"]_UPDATE (17Nov2008 )_[/COLOR]
Totem now refuses to play even another DVD that used to play fine. It just plays the "legal stuff" about intellectual property and then it gives a "Failed to connect to stream" error (as people say in this bug [https://bugs.launchpad.net/ubuntu/+s...10/+bug/260765](https://bugs.launchpad.net/ubuntu/+s...10/+bug/260765))

Furthemore, Totem just gives a black screen with the encrypted Harry Potter DVD and the playlist says "cdrom0" instead of "Title 1". The clock does not seem to run.

[COLOR="Red"][U]END OF UPDATE
[/U][/COLOR]
What's installed:
The  usual stuff from medibuntu

- Ubuntu restricted extras (incl. w32 codecs)
- libdvdcss2
- libdvdread3
- libdvdnav4
- gstreamer plugins ugly multiverse 

Is something wrong with intrepid?
Have I missed some essential  package?

Please note that several other DVDs play great.

I would really appreciate any ideas

---

### Post by tvtech on 2008-11-13
I've found the same problem.  maybe this a bug?  have you looked for bugs in launchpad?  if you haven't found one have you posted a bug report?

it seems to happen with encrypted dvds.

---

### Post by richard.e.morton on 2008-11-13
I have a similar problem with Kubuntu 8.10. 

Video from any source starts, media playback window opens (in VLC 0.9.x) then sound starts for a split second and VLC closes with no explanation.

I will post updates of what I find if you do ;-)

Rich

---

### Post by Angelos72 on 2008-11-13
Here is a bug that may correspond:

[https://bugs.launchpad.net/ubuntu/+source/gst-plugins-bad0.10/+bug/260765](https://bugs.launchpad.net/ubuntu/+source/gst-plugins-bad0.10/+bug/260765)

I am not sure that's the one though. This is a gstreamer bug, but I cannot play some DVDs with Xine either.

Xine returns the following Error.

> The source seems encrypted and can't be read. Your DVD is probably crypted. According to your country laws, you can or you can't install/use libdvdcss to be able to read this disk, which you bought (Media stream scrambledencrypted)

Can someone (more Ubuntu literate than me) confirm that this is the problem we are talking about?

---

### Post by richard.e.morton on 2008-11-17
Have you installed Libdvdcss?

You need to add the medibuntu repository and I think activate unsupported downloads. you can do this by following the instructions here
[https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories](https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories)

then in your package manager adding libdvdcss2, or typing into a console sudo apt-get install libdvdcss2

hope that helps

Richard

---

### Post by Angelos72 on 2008-11-17
> **richard.e.morton said:**
> Have you installed Libdvdcss?

You need to add the medibuntu repository and I think activate unsupported downloads. you can do this by following the instructions here
[https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories](https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories)

then in your package manager adding libdvdcss2, or typing into a console sudo apt-get install libdvdcss2

hope that helps

Richard

I have installed the ubuntu-restricted-extras meta-package from medibuntu, which among other things contain libdvdcss2. I have tried to uninstall and install it again with no success.

I am kind of sure it's a bug (like I wrote previously).

If anyone has an idea, I 'd love to hear it.

---

### Post by gandaran on 2008-11-17
> I have installed the ubuntu-restricted-extras meta-package from medibuntu, which among other things contain libdvdcss2. I have tried to uninstall and install it again with no success.

ubuntu-restricted-extras comes from multiverse repo not medibuntu and does not contain libdvdcss2.

totem-gstreamer doesn't support DVD menus only totem-xine can do that
for mplayer or vlc you can try changing the video driver/output in preferences

---

### Post by Angelos72 on 2008-11-17
> **gandaran said:**
> ubuntu-restricted-extras comes from multiverse repo not medibuntu and does not contain libdvdcss2.

totem-gstreamer doesn't support DVD.s menus only totem-xine can do that
for mplayer or vlc you can try changing the video driver/output in preferences

Yes, you are right, about the repositories. My mistake! 

However, I have libdvdcss2 installed.

The problem is really not the dvd menus. I do not have any dvd playback at all and not just using Totem, but with VLC and Mplayer as well (for on specific DVD, which is Harry Potter and the order of the phoenix. The DVD is bought and 100% legal and it also used to play fine on Hardy). 

Also a new thing that I just saw: 

Totem now refuses to play even another DVD that used to play fine. It just plays the "legal stuff" about intellectual property and then it gives a "Failed to connect to stream" error (as people say in this bug [https://bugs.launchpad.net/ubuntu/+source/gst-plugins-base0.10/+bug/260765](https://bugs.launchpad.net/ubuntu/+source/gst-plugins-base0.10/+bug/260765))

Furthemore, Totem just gives a black screen with the encrypted Harry Potter DVD and the playlist says "cdrom0" instead of "Title 1". The clock does not seem to run.

VLC and MPlayer work as I described in the initial post.

Finally, one question. 

How can I tell if I am using Totem-gstreamer or Totem-Xine?

---

### Post by gandaran on 2008-11-17
> How can I tell if I am using Totem-gstreamer or Totem-Xine?
totem-gstreamer is the default player installed, totem-xine you have to install and maybe remove totem-gstreamer
look, try starting totem and mplayer or vlc from the terminal/console, then run the dvd, post all the errors displayed in the terminal here

---

### Post by Angelos72 on 2008-11-18
Ok,
I have included in the attachments what came out of the terminal, when I tried to play the encrypted DVD, for:

- Totem Xine
- Totem gstreamer
- VLC
- Mplayer

Please note that **Totem Xine ** produces an error that says that I am trying to play an encrypted dvd, without having libdvdcss installed. However I DO have the libdvdcss2 package installed  

Also I remind you that **Totem-gstreamer** gives a "failed to connect to stream" error, which is probably a known bug (the one I wrote about in previous posts --> [https://bugs.launchpad.net/ubuntu/+s...10/+bug/260765](https://bugs.launchpad.net/ubuntu/+s...10/+bug/260765))

In the case of **Mplayer** I have deleted some lines that just kept repeating themselves.

Thanks in advance

Angelos

---

### Post by irish66 on 2008-11-18
no luck with mpplayer, totem. or vlc. Well this is a big problem, isn't it?
M

---

### Post by irish66 on 2008-11-18
Apologies. I thought Intrepid was another player. Thanks to a how to post, i can now play dvds. Thanks Angelos for your contribytion too.
M

---

### Post by retrovertigo on 2008-11-18
I had a similar problem in Intrepid with a recently purchased DVD drive.  It turns out that the drive had never had its region set.  To set the region of the drive, make sure that you have the Universe repositories enabled, and then run **sudo apt-get install regionset**.  Then just run **regionset** as root, like so:

```
ejohnson@dalek:~$ sudo regionset
regionset version 0.1 -- reads/sets region code on DVD drives
Current Region Code settings:
RPC Phase: II
type: **NONE**
vendor resets available: 4
user controlled changes resets available: 5
**drive plays discs from region(s):**, mask=0xFF

Would you like to change the region setting of your drive? [y/n]:y
Enter the new region number for your drive [1..8]:1
New mask: 0xFFFFFFFE, correct? [y/n]:y
Region code set successfully!
```

As you can see, "type" is set to NONE, and there are no region numbers specified after where it says "drive plays discs from region(s):".

I specified region 1, and upon running **regionset** again you can see that the region has been set.

```
ejohnson@dalek:~$ sudo regionset
regionset version 0.1 -- reads/sets region code on DVD drives
Current Region Code settings:
RPC Phase: II
type: **SET**
vendor resets available: 4
user controlled changes resets available: 4
**drive plays discs from region(s): 1**, mask=0xFE

Would you like to change the region setting of your drive? [y/n]:n
```

After doing this, the drive started playing DVDs just fine in all of my media players.

---

### Post by Angelos72 on 2008-11-20
That was a good idea Retrovertigo. It would never have crossed my mind

My DVD/RW is indeed new and did not have any region set.

I followed your instructions, but unfortunately nothing happened :(

I have the impression that libdvdcss unlocks the region too.

---

### Post by Angelos72 on 2008-11-20
I created a virtual machine using VirtualBox on my Windows PC (a different machine). I made a clean install of Intrepid and added:

- ubuntu-restricted-extras
- livdvdcss2
- VLC

I tried my DVDs and they did the exact same thing.

Until now I had the feeling that I am the only one that cannot play some encrypted DVDs, but I strongly suspect it's a bug.

Has this happened to anyone else?

Should should report it to launchpad?

---

### Post by steeleyuk on 2008-11-21
I'm having the same problems now. Playing DVDs was fine up until I tried yesterday. Whatever problem this is, its a big one.

---

### Post by Angelos72 on 2008-11-21
I filed a bug report to launchpad. If anyone else has the same problem, please confirm the bug:

[https://bugs.launchpad.net/ubuntu/+bug/300645](https://bugs.launchpad.net/ubuntu/+bug/300645)

---

### Post by Angelos72 on 2008-12-01
I rented from the video store the following DVDs that played alright in VLC

The Burn Ultimatum
Pan's Labirinth
Pirates of the Caribbean: At world's end

I am confused....

---

### Post by retrovertigo on 2008-12-01
I've got one other thing for you to try.  Unfortunately I tried this before running regionset so I don't know if this will make any difference for you.

I enabled the medibuntu repositories and installed libdvdcss, but before trying regionset I also did some googling and found that libdvdread has a script bundled with it that downloads and installs libdvdcss for you.

The script is located at /usr/share/doc/libdvdread3/install-css.sh.  Run it as root, and see if that works.

---

### Post by richard.e.morton on 2008-12-01
> **retrovertigo said:**
> I've got one other thing for you to try.  Unfortunately I tried this before running regionset so I don't know if this will make any difference for you.

I enabled the medibuntu repositories and installed libdvdcss, but before trying regionset I also did some googling and found that libdvdread has a script bundled with it that downloads and installs libdvdcss for you.

The script is located at /usr/share/doc/libdvdread3/install-css.sh.  Run it as root, and see if that works.

hi, thanks for that. but this affects all video playback not just dvds. audio playback is fine. However I can playback streamed flash videos in firefox. wierd.

R

---

### Post by Angelos72 on 2008-12-04
> **retrovertigo said:**
> I've got one other thing for you to try.  Unfortunately I tried this before running regionset so I don't know if this will make any difference for you.

I enabled the medibuntu repositories and installed libdvdcss, but before trying regionset I also did some googling and found that libdvdread has a script bundled with it that downloads and installs libdvdcss for you.

The script is located at /usr/share/doc/libdvdread3/install-css.sh.  Run it as root, and see if that works.

Well as you say this downloads and installs libdvdcss, no more, no less. No improvement.:(

Good thinking though.

---

### Post by retrovertigo on 2008-12-04
Yeah, I just figured though, maybe the libdvdcss from medibuntu's Intrepid repos is messed up, and the script from libdvdread actually does things right.

Worth a try, at least.

---

### Post by richard.e.morton on 2008-12-07
Hi There,

I have also installed Kubuntu Intrepid. I cannot play any videos outside of Flash videos in a browser. I ahve tried both Dragon and VLC (from repository). Neither play any file, DVD, downloaded, un-protected mpg, mpeg2 recorded off my DVR... all or which play fine in Hardy.

I have been struggling with this for a while, so I reinstalled, same problem. I am now going to update and apply all patches and if not I will be reverting to Hardy (8.04.1) Kubuntu ReMix.

Rich

---

### Post by Angelos72 on 2008-12-08
@richard.e.morton

This really does not sound like the problem I had. In my case everything plays with VLC and MPlayer, except a scecific encrypted DVD (I cannot say why this specific DVD plays under hardy, but not under intrepid.)

Have you tried using Ubuntu? (Although I do not believe you will see any difference...)

Have you found any place else reports that sound like your problem?

(BTW if you think that any of the stuff you have found applies here please let us know).

Best of luck to you.

---

### Post by bedhead75 on 2008-12-12
> **Angelos72 said:**
> Hi all,
I am having trouble playing a certain DVD using intrepid. What is funny is that the exact same DVD plays great on Hardy (which is installed on another PC).

Specific symptoms are:

- Totem --> It seems that it is trying to start the DVD menu (shows total time 12 seconds), but never starts anything

- VLC --> It shows the DVD menu alright, but when I select "start movie" I get no picture and just choppy sound of poor quality.

-Mplayer --> the clock works as if the movie is actually played, but I get no picture or sound.

[COLOR="Red"]_UPDATE (17Nov2008 )_[/COLOR]
Totem now refuses to play even another DVD that used to play fine. It just plays the "legal stuff" about intellectual property and then it gives a "Failed to connect to stream" error (as people say in this bug [https://bugs.launchpad.net/ubuntu/+s...10/+bug/260765](https://bugs.launchpad.net/ubuntu/+s...10/+bug/260765))

Furthemore, Totem just gives a black screen with the encrypted Harry Potter DVD and the playlist says "cdrom0" instead of "Title 1". The clock does not seem to run.

[COLOR="Red"][U]END OF UPDATE
[/U][/COLOR]
What's installed:
The  usual stuff from medibuntu

- Ubuntu restricted extras (incl. w32 codecs)
- libdvdcss2
- libdvdread3
- libdvdnav4
- gstreamer plugins ugly multiverse 

Is something wrong with intrepid?
Have I missed some essential  package?

Please note that several other DVDs play great.

I would really appreciate any ideas


     Are you running 64 or 32-bit Intrepid?  The reason I ask is because of the following...
     I did a fresh install of Intrepid 64-bit on a new computer, and after installing all of the necessary library files, I get the same results you describe.  The Notebook plays fine, but Duck Season doesn't work.  Thinking it was an Intrepid issue, I wiped the drive and fresh installed Hardy 64-bit.  I get the exact same result.  BUT...both DVD's play perfectly fine on my old computer with Hardy 32-bit.  It's starting to seem like a 64-bit vs 32-bit issue instead.  Does anyone else have similar results as myself?  
     I could always install Intrepid 32-bit and see if both DVD's work, but I'm too lazy.  It sounds more like a problem with specific library files and pluggins with certain DVD's.
     I also get different errors depending on the player I use.  Using Ogle in Hardy 64-bit gives:

WARNING[ogle_mpeg_vs]: wrong start_code picture_start_code: 00000108
WARNING[ogle_mpeg_ps]: Found a scrambled PES packet! (1)
WARNING[ogle_mpeg_ps]: Found a scrambled PES packet! (1)
WARNING[ogle_mpeg_ps]: Found a scrambled PES packet! (1)
WARNING[ogle_mpeg_ps]: Found a scrambled PES packet! (1)

Using VLC in Intrepid 64-bit gives:

[00000573] main decoder error: decoder is leaking pictures, resetting the heap
[00000573] main decoder error: decoder is leaking pictures, resetting the heap
[00000573] main decoder error: decoder is leaking pictures, resetting the heap

---

### Post by Angelos72 on 2008-12-13
The hardy and intrepid results, which I report here are about 32-bit editions.

The output I get from vlc when I run it from terminal is

```
[00000001] main libvlc debug: VLC media player - version 0.9.4 Grishenko - (c) 1996-2008 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintaner-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=1ubuntu3' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-arts' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-x264' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-alsa' '--enable-dv' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "C"
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libdvdnav: Using dvdnav version 4.1.2 from http://dvd.sf.net
libdvdnav: DVD Title: HARRY_POTTER_ORDER_OF_PHOENIX
libdvdnav: DVD Serial Number: 37148BD2
libdvdnav: DVD Title (Alternative): HARRY_POTTER_ORDER_OF_PHOENIX
libdvdnav: Unable to find map file '/home/avlass/.dvdnav/HARRY_POTTER_ORDER_OF_PHOENIX.map'
libdvdnav: DVD disk reports itself with Region mask 0x00ed0000. Regions: 2 5
libdvdnav: Language 'en' not found, using '&#65533;&#65533;' instead
libdvdnav: Menu Languages available: &#65533;&#65533; 
libdvdnav: Language 'en' not found, using '&#65533;&#65533;' instead
[00000459] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:192000
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
libdvdnav: Language 'en' not found, using 'el' instead
libdvdnav: Menu Languages available: el 
libdvdnav: Language 'en' not found, using 'el' instead
libdvdnav: Menu Languages available: el 
[00000482] a52 decoder: A/52 channels:6 samplerate:48000 bitrate:384000

```


With ogle I see a couple of seconds of scrambled picture before it hangs.

When I run it from terminal, I get a lot of 

```
WARNING[ogle_mpeg_ps]: Found a scrambled PES packet! (1)
```

I saw nowhere something like

```
WARNING[ogle_mpeg_vs]: wrong start_code picture_start_code: 00000108
```

I attach the entire output, just in case someone who knows better than me (just about everybody) can make something out of it.

I am not sure we are having the same problem.That's odd though...

---

### Post by Angelos72 on 2008-12-24
I am beginning to believe that this might be a hardware problem. My PC #1 and Laptop play the DVD with no problem on Hardy and Intrepid.

I will install Hardy on PC#2 that originally had the problem. If it plays ok with Hardy, then it's an Intrepid problem. If not, then it's probably hardware.

If anyone has the means to check this please post the results here.

---

### Post by muzikjock on 2009-04-22
I know this is a rather old thread for this. and I don't know why no one has brought this to the surface as a possible solution. I only saw this posted in one place after Googling all over the place. I have an acer aspire one model zg5. Installed intrepid on it. and couldn't for the life of me get encrypted dvd's to play . did everything mentioned here short of installing and running regionset. Then i decided to Google some more. only one place did i find this tried it and I am now watching the Led Zep DVD on my aspire one in xine! In your home directory there is a directory that is named ".dvdcss". Just delete that as it contains keys to cache files. If corrupted information gets in there for what ever reason, won't play. Just delete the whole directory and I was in business. Ubuntu is my friend again! Peace out!     :guitar:

---

### Post by retrovertigo on 2009-04-23
Nice!  I haven't been able to use my Ubuntu box a lot lately but I'll certainly keep this thread bookmarked in case I see any problems in the future.

---

### Post by gready on 2010-01-08
I had the same problem and removing the ".dvdcss" directory did the trick 
Thank you

---

