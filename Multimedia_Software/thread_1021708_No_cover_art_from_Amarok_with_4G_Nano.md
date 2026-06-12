---
title: "No cover art from Amarok with 4G Nano"
date: 2008-12-25
forum: Multimedia Software
---

### Post by Muchacho_Gasolino on 2008-12-25
I have my 4G ipod nano running *almost* perfectly with Amarok 1.4.10 and libgpod 0.7.0rc1. The songs work fine, just the art won't go.

I have all my art loaded into Amarok, and when compiling libgpod, the autogen.sh reports "Artwork support.... yes" at the end. The SysInfoExtended XML file is there in iPod_Control/Device. But when I click iPod -> Update Artwork in Amarok, nothing happens. 

I also noticed that if I try to use Amarok to set the iPod model, it does not have an option for a 4G nano. However, the Amarok wiki says that Amarok 1.4.10 supports the 4G nano.

Anyone have any suggestions? Is there a way to manually drag and drop album art onto the iPod? I'm just curious if I could get it to work at all.

---

### Post by euchrid33 on 2008-12-27
I've got it halfway there.  I have art in the cover flow, but not when the song is playing.  I have a black 8gb 4G, in Amarok I set it as a black 8gb video nano, as that's the closest.  Not sure if the colour matters, but the option was there.  From there I loaded all the songs as usual, then opened the little iPod menu (it's kind of hidden unless you extend the side panel all the way, let me know if you can't find it) and selected Update Cover Art.  From there I disconnected as usual and it was all there in Cover Flow.

Still working on getting it to show when songs play.  Any help, anyone?

---

### Post by BlackHawk1990 on 2008-12-27
Same problem here...

At first I used Amarok with the pre-installed libgpod-version to update music, podcasts and artwork. When I clicked "Update Artwork" it said all covers were updated. On my iPod 4th Gen. 8 GB Silver I saw all covers in Cover Flow, but not when playing any track. In the main menu with "Music" highlighted I see single-colored squares with stripes of different colors on it or squares that look like a TV-screen without cable connection, well, just nonsense-images.

So I read I'd have to use the svn-version of libgpod. When configuring it said me at first there won't be support for the ipod artwork. That was because I didn't have a version of gdkpixbuf installed. But when I finally got it working (with artwork-support) I restarted Amarok and according to [this guide]("http://neoaddict.wordpress.com/2007/09/26/updating-libgpod/") it should work now.

So I looked again in Amarok and found there was still no 4th gen ipod option. Updating artwork still gives me the same output on the ipod.

(By the way: when I try to connect to the ipod with gtkpod it says me he didn't find a "Photos"-folder on the ipod. Even creating it manually didn't help ... still same error.)

Hope anyone out there can help us with this problem. I'm wondering why there isn't any real guide for the ipod 4G on Linux. Nobody having the same problem we three have?

BlackHawk

(Hope you can read and understand everything so far as english is not my native language!)

---

### Post by euchrid33 on 2008-12-27
I think that the 4G nano is just too new for there to be decent Linux support for it.  This sort of thing always lags behind the bigger systems.  The current system is very complicated and tricky, but hopefully someone will make a script (its beyond me to do so) or a program that supports art on the 4g.  It won't be Amarok, though, as they're not supporting any sort of ipod at all with Amarok 2 - very disappointed about that.

By the way, your English was fine, I knew exactly what you meant.

---

### Post by BlackHawk1990 on 2008-12-27
Thanks for your answer! :)

You're probably right ... Hope there'll be such a script soon. I was just wondering, why the wiki says the libgpod-subversion is supporting artwork on the new iPod when that's not the case. Is Amarok2 really not supporting any kind of ipod? I once installed it on Windows when my brother searched for an alternative to iTunes and I thought Amarok would do as it's running native on Windows now. Then after installing I realized there was no device support. But I still thought that would just be with the Windows-version.

And I still wonder why there isn't any thread concerning ipod 4g on linux but this. Except for the link in my last post I didn't even find any (useful) installation guide for the libgpod SVN. I still think I did sth wrong as it's not working with gtkpod neither. Would be great if anyone could tell me how he got it working or has the time to develop a script as the "Now playing"-window looks boring and the main menu really ugly now ...

BlackHawk

---

### Post by euchrid33 on 2008-12-27
This isn't the only discussion of the issue, there's a thread on the official Amarok forum, and one two scattered about here and there:

[http://www.google.com.au/search?hl=en&safe=off&client=firefox-a&rls=com.ubuntu%3Aen-GB%3Aunofficial&hs=MSQ&q=ipod+4th+cover+amarok&btnG=Search&meta=](http://www.google.com.au/search?hl=en&safe=off&client=firefox-a&rls=com.ubuntu%3Aen-GB%3Aunofficial&hs=MSQ&q=ipod+4th+cover+amarok&btnG=Search&meta=)

Not many of them have much more information than you do, though.

And yeah, there's no device support in Amarok 2, and no intention of adding it.  I had a play with it, but it's missing lots  of features - no queuing of songs, no playlist filtering.  They're going to add those, but not device management.  I guess sooner or later we'll be using GTKpod, or just never upgrading Amarok.  I don't really like either option.

---

### Post by Muchacho_Gasolino on 2008-12-29
I used the same guide to install libgpod SVN. You two seem better off than me, though. I don't have anything in cover flow. 

Did both of you use the libgpod in the ubuntu repositories to originally add your coverart? I never tried using that one; I started with the latest SVN.

I tried gtkpod as well, but couldn't figure out how to import my cover art from Amarok or download all of them from the web into gtkpod, and did not feel like finding each cover individually. I dont think we are concerned with the Photos directory here. I believe the ipod uses a directory called Artwork to store the album covers and Photos is for other images.

Are you sure that there is no intention to add device support in Amarok2? My impression was that they are working on it and it's just going to take a while. I'm kind of tired of KDE's habit of "releasing" half-done apps (or desktop environments...).

---

### Post by euchrid33 on 2008-12-29
I haven't touched libgpod since I originally installed Amarok.  If it's been updated in the normal slew of Ubuntu updates then I haven't noticed.  I'm not sure which version of it I currently have, but if someone can tell me how to check it out I'd be happy to post it here.

As far as device support in Amarok 2, I'm not 100% sure.  I felt like I read it somewhere, but when I looked just then I couldn't find anything, so maybe I imagined it.  I only had a brief play with it before switching back to the original, so I can't say for sure.

---

### Post by hellz99 on 2008-12-30
There's a [guide]("http://whatwouldnickdo.com/wordpress/?p=15") here that explains fetching cover and moving them to your ipod.  

Amarok will handle fetching all images for music in your Amarok library (don't confuse this with music on your ipod).

I will say this...in Amarok, putting in the correct iPod model is a crucial step.  It won't work without the correct model.  I've got this working with both a Nano 3rd gen 8GB, and my gf's 30GB video (which wasn't listed in Amarok, but I got it working by choosing the closest I could).

---

### Post by BlackHawk1990 on 2009-01-04
Heyho

Sorry for my late answer, but I had much to do the last week (and still have to do). I don't have any good news until now. I tried reinstalling the libgpod SVN-version which didn't help. As you said the problem is that amarok has no option for a 4th gen nano ... And I think it won't work until that is available.

@Muchacho, which ipod model do you have selected? At least cover flow works for me when I select iPod nano 3rd in any color. But my main menu is still ugly ...
Btw: do you see nothing in cover flow or just not the right covers?
-
edit: yes, I tried using the pre-installed libgpod-version, but it has exactly the same results as the svn-version. I wonder if my svn-version is really working, at least I don't feel any difference to before.
And you're right with the "Photos"-directory. It doesn't have anything to do with cover art things. But I just mentioned it to demonstrate gtkpod isn't working as well ;)

Btw: KDE = German = sh*t^^
(I may say that ... I'm german myself and hate everything about germany (except for the language)^^)
-

@euchrid, you can look up which version you have installed by either using synaptic packet manager (hope it's called like that in the english version and you use (k/x/ed)ubuntu) or typing 'apt-cache showpkg libgpod3' in the terminal.

@hellz, thanks for your link, but it isn't helpful at all ... It works all fine with my brother's ipod nano 3rd (and I can select this model in amarok). The problem is just the new nano with which every linux-user has problems ... I'm just wondering why the amarok-media-device-page has listed the 4G as working with the SVN-version when that's not true.

And I think Amarok2 does work on supporting media devices! I read something like that
Has anyone tried to use 'Floola' yet? I'll try that this evening (yes^^ in europe it's already evening)
I have to leave for supper now ... see you!

BlackHawk

---

### Post by BlackHawk1990 on 2009-01-05
Update:
Well, I didn't came to installing Floola yesterday. Instead I tried uninstalling amarok (and the pre-installed libgpod), compiling the libgpod-svn-version, installing amarok (from repos) again. But that led to no result ... I couldn't even installing amarok again without installing the libgpod-version from the repos ... And compiling amarok from source doesn't work for me without KDE-environment (I use xfce). Well, either it's normal that linux doesn't detect the svn-version or I'm too stupid to install libgpod-svn ... (I'd prefer the second, because that would be solvable with a good guide^^)

And I don't think Floola works with the old libgpod-version so I'm currently concentrating on getting the svn-version to work (besides school-things ... it's my last year there ...)

btw: these people here got it working: [http://amarok.kde.org/forum/index.php?topic=16083.0](http://amarok.kde.org/forum/index.php?topic=16083.0)

But I don't think Amarok will have the nano 4th gen-option after updating libgpod ... Seems like we have to install amarok from source which again doesn't work for me ... 
running ./configure returns this error:

[INDENT]checking for KDE... configure: error:
in the prefix, you've chosen, are no KDE headers installed. This will fail. So, check this please and use another prefix!
[/INDENT]

edit: do you see your cover art when playing a game and click on "Listening to" (don't know the exact english expression apple uses, but I think that's the most used^^)

And actually I don't care about my cover art any more ... Would be nice, if I could get it right, but I don't care if not ...
Cover art works, covers in the main menu is now set to 'off' and when playing a track it's just displaying the standard-image, which is not that ugly

Anyway, if anyone has an idea of how to fix that I'd be quite happy :)

Via IRC I talked to a person having problems with the ipod nano 4G under linux too, but he got at least the libgpod-svn-version working ... (he was using the prepared archlinux-package for that ...)
And for him it still doesn't work under amarok. He failed in installing amarok from subversion.

---

### Post by euchrid33 on 2009-01-11
Yes, when I play a game and go to Now Playing or whatever it's called from within the game, the cover does appear.  Frustrating.

---

### Post by Muchacho_Gasolino on 2009-01-14
I don't see any covers at all, anywhere on my ipod. I will have to check out that link when I have a minute, BlackHawk, and see how it goes for me. I'm running KDE 4.

Doch, Deutschland ist ein schoener Staat! Die Sprache, das Land, und das Bier. : )

---

### Post by BlackHawk1990 on 2009-01-15
Heyho!

It works!
I have covers on my ipod!
I got it working with the help of a guy in the #amarok.de-channel. I'm not using the svn-version of libgpod any more, but the libgpod-0.7.0rc2 (that can be found [here]("http://tinyurl.com/0-7-0rc2")). It works well with amarok 1.4.10 and I can select iPod nano 4G in the ipod-model menu now.

Howto:[INDENT]
1) Download the [libgpod-0.7.0rc2]("http://tinyurl.com/0-7-0rc2"), extract it anywhere and cd to this path in the terminal
2) type './configure'
3) type 'sudo make'
4) type 'sudo make install'
5) type 'sudo checkinstall' (I had to install that first!)
6) Download the [amarok_1.4.10.orig.tar.gz]("http://archive.ubuntu.com/ubuntu/pool/main/a/amarok/amarok_1.4.10.orig.tar.gz") (at least that's the one I used), extract it anywhere and go there in the terminal
7) type 'sudo ./configure --with-libgpod' (and optional --enable-mysql if required)
8) check the list of features it will include or not include and if that's acceptable for you then
9) type 'sudo make && sudo make install' (would work splitted up in two commands too, but it will take quite a lot of time and so you don't have to wait for 'make' to finish!)
10) start it and have fun^^ :popcorn:
[/INDENT]

Those are the problems I encountered (and still remember) with solution:

- Qt error => don't remember the package name ... but it was any qt dev package^^
- "configure: error: there are no kde libraries [...]" => kdelibs4-dev (did not work with kdelibs5-dev for me!)
- Ruby missing => ruby-dev
- xine missing => xine-dev

if you get any other errors (as I said: I don't remember all of them) feel free to ask me :)

Hope I could help and you can sync your artwork soon too :)

btw: I like the german language too, that's right ;) but not politics^^ ok, it's not that bad as I presented it in my post. There are quite many things I don't like, but there are also many I DO like
And how come you know german?^^

BlackHawk

PS: it seems that I have to edit every post I write at least one time :D

---

### Post by euchrid33 on 2009-01-16
Thanks a lot for the detailed instructions.  They don't however, work for me.  I all my time with Linux I've never gotten a tarball to work right, and this is no exception.  When I run ./configure all goes well until it finishes, at which point it tells me that it can't find 'glib-2.0' or 'gobject-2.0'.  Presumably as a result of this, the make command fails.

I've looked for these packages, but I can't find them either in Synaptic or via apt-get in the terminal. Any idea which repository they're in?

---

### Post by euchrid33 on 2009-01-16
Never mind, tracked them down.  For the record, glib was here:

[ftp://ftp.gtk.org/pub/gtk/v2.8/](ftp://ftp.gtk.org/pub/gtk/v2.8/)

After that is started asking for libxml-2.0, which I found here:

[ftp://gd.tuwien.ac.at/pub/libxml/](ftp://gd.tuwien.ac.at/pub/libxml/)

I'll update on the rest of the process when I'm done.

---

### Post by euchrid33 on 2009-01-16
First up, sorry for spamming the thread.

I've got the ./configure to complete, but the make isn't working.

Here's the output:

make  all-recursive
make[1]: Entering directory `/home/alex/Documents/libgpod-0.7.0rc2'
Making all in src
make[2]: Entering directory `/home/alex/Documents/libgpod-0.7.0rc2/src'
/bin/bash ../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I.. -I/usr/local/include/glib-2.0 -I/usr/local/lib/glib-2.0/include   -I/usr/local/include/libxml2     -DWITH_INTERNAL_GCHECKSUM -g -O2 -MT libgpod_la-itdb_plist.lo -MD -MP -MF .deps/libgpod_la-itdb_plist.Tpo -c -o libgpod_la-itdb_plist.lo `test -f 'itdb_plist.c' || echo './'`itdb_plist.c
 gcc -DHAVE_CONFIG_H -I. -I.. -I/usr/local/include/glib-2.0 -I/usr/local/lib/glib-2.0/include -I/usr/local/include/libxml2 -DWITH_INTERNAL_GCHECKSUM -g -O2 -MT libgpod_la-itdb_plist.lo -MD -MP -MF .deps/libgpod_la-itdb_plist.Tpo -c itdb_plist.c  -fPIC -DPIC -o .libs/libgpod_la-itdb_plist.o
itdb_plist.c:184:2: warning: #warning GLib > 2.12 required for g_base64_decode(). Working around this problem.
itdb_plist.c: In function 'parse_dict':
itdb_plist.c:264: error: 'G_TYPE_HASH_TABLE' undeclared (first use in this function)
itdb_plist.c:264: error: (Each undeclared identifier is reported only once
itdb_plist.c:264: error: for each function it appears in.)
make[2]: *** [libgpod_la-itdb_plist.lo] Error 1
make[2]: Leaving directory `/home/alex/Documents/libgpod-0.7.0rc2/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/alex/Documents/libgpod-0.7.0rc2'
make: *** [all] Error 2


Any idea what to do with that?

---

### Post by BlackHawk1990 on 2009-01-16
> itdb_plist.c:184:2: warning: #warning GLib > 2.12 required for g_base64_decode(). Working around this problem.

I think that's the point ... I didn't come across this glib-error though

The version of glib seems to be the newest one, but definitely isn't the one I used! I didn't install from any source except for libgpod and amarok!

A similar error is the one I get when trying to install gtkpod (I'm trying that atm). It accepts the version (because it is higher than 1.2.x in your case), but the new one doesn't have the same variables the older had. I'm not sure which package to use instead, but I'd assume it is 'libglib1.2-dev' or 'libglib2.0-dev' (I have both of them installed).

Hope that works for you :)

If my post is nonsense, just ignore it, I'm already half-sleeping^^
And I won't edit it this time :D

BlackHawk1990

---

### Post by BlackHawk1990 on 2009-01-17
ok, now I'm fit enough to answer ;)

don't know ... yesterday I read 1.2 instead of 2.12 :P
and the package you need is the 'libglib2.0-dev' (in synaptic package manager it says I have version 2.18.2-0 of this package installed). It seems your version doesn't have a required variable or function. Try it with that package and it should work, there could still be an error though, if the variable 'G_TYPE_HASH_TABLE' is not defined in this package, but let's see first ;)

As I said I have a similar problem with gtkpod ... This newer libgpod version uses other variables than the older and some of those are missing now. This guy in IRC told me he had the same problem and had to comment out parts of the source code.

Good luck!
BlackHawk :guitar:

---

### Post by avianbc on 2009-01-17
This thread was insanely helpful. Thanks for the help!

However, I have ran into the same problem as euchrid33. I did a "sudo apt-get install libglib2.0-dev" and it still reports this:

> make  all-recursive
make[1]: Entering directory `/home/brad/libgpod-0.7.0rc2'
Making all in src
make[2]: Entering directory `/home/brad/libgpod-0.7.0rc2/src'
/bin/bash ../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I.. -I/usr/local/include/glib-2.0 -I/usr/local/lib/glib-2.0/include   -I/usr/local/include/libxml2     -DWITH_INTERNAL_GCHECKSUM -g -O2 -MT libgpod_la-itdb_plist.lo -MD -MP -MF .deps/libgpod_la-itdb_plist.Tpo -c -o libgpod_la-itdb_plist.lo `test -f 'itdb_plist.c' || echo './'`itdb_plist.c
 gcc -DHAVE_CONFIG_H -I. -I.. -I/usr/local/include/glib-2.0 -I/usr/local/lib/glib-2.0/include -I/usr/local/include/libxml2 -DWITH_INTERNAL_GCHECKSUM -g -O2 -MT libgpod_la-itdb_plist.lo -MD -MP -MF .deps/libgpod_la-itdb_plist.Tpo -c itdb_plist.c  -fPIC -DPIC -o .libs/libgpod_la-itdb_plist.o
itdb_plist.c:184:2: warning: #warning GLib > 2.12 required for g_base64_decode(). Working around this problem.
itdb_plist.c: In function 'parse_dict':
itdb_plist.c:264: error: 'G_TYPE_HASH_TABLE' undeclared (first use in this function)
itdb_plist.c:264: error: (Each undeclared identifier is reported only once
itdb_plist.c:264: error: for each function it appears in.)
make[2]: *** [libgpod_la-itdb_plist.lo] Error 1
make[2]: Leaving directory `/home/brad/libgpod-0.7.0rc2/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/brad/libgpod-0.7.0rc2'
make: *** [all] Error 2


Any ideas?

---

### Post by BlackHawk1990 on 2009-01-17
Wow^^ there's actually a 4th person out there having the same problems. I thought nobody is interested in our thread :)

okay ... I'll tell you which (similar) packages I have installed:
libglib2.0-0
libglib2.0-cil     
libglib2.0-data
libglib2.0-dev

So I'd assume now it has to be either libglib2.0-0 or libglib2.0-data ... Try it out and let's hope that works ...

Another solution would be to edit the source code of this itdb_plist.c in the src-folder, but I would not recommend that (although that's exactly what I did with gtkpod; now it's working perfectly with the [gtkpod-svn-version]("http://tinyurl.com/0-99-13SVN")). Then you would have to comment out every line (or loop) G_TYPE_HASH_TABLE appears. But then you could still come across another error after that. That would just be the last thing to try ;)

Good luck!
BlackHawk (who is half-sleeping again)

---

### Post by avianbc on 2009-01-18
Hmmm.. I've installed all the libglib packages you stated in the post before this and I still get the same error. However, I think I am doing something wrong because when I do a "make install" on libxml, glib, or libgpod, it breaks my Xserver and X freezes and wont start at all. It has something to do with the libraries I believe. I had to log into a root shell and do a "make uninstall" on the 3 mentioned packages to even get back into X, so it could be any of the 3 causing my problem (or my incompetence in what I am doing). I've compiled tons of stuff before so I am comfortable doing so, but I've never once seen this happen before.

Any help would be appreciated. If none is given, no worries. I can use itunes until I get it figured out. (iTunes is such a piece of garbage. Sorry, had to throw that out there.) :(

Oh well, when my Xserver crashed it inspired me to finally upgrade to Intrepid Ibex. I'm loving intrepid now that it is working correctly. :P

---

### Post by avianbc on 2009-01-19
Nice! I finally got it working. I did some research and found out that before you compile amarok, you can just do:

sudo apt-get build-dep amarok

and it will fetch all the dependencies for you automatically (such as ruby, xine , etc). Saved me a lot of trouble.

Thanks for all the help, Blackhawk1990. The album art works beautifully and now I can select my exact model in Amarok (4th gen nano 8gb black to be exact!).

You are oficially my hero, I've googled hours upon hours trying to figure this one out. \\:D/

PS: Amarok is about 500 times better at fetching album covers than itunes is. Kind of sad when you think about it that a third party app does it better.

---

### Post by euchrid33 on 2009-01-19
avianbc, I had the same issues that you did when I tried to follow the instructions.  It took me quite a while to get it all sorted out and get my system running again, so I'm not eager to try again unless I'm sure that it'll work out.

As far as the 'sudo apt-get build-dep amarok' command goes, what would happen if I ran it with amarok already installed?  Would it still bring it up to date?  Or should I remove amarok, run that command and then reinstall it?

---

### Post by BlackHawk1990 on 2009-01-19
avianbc, I'm glad it works for you! I read about that 'sudo apt-get build-dep amarok' too (and it should work for every other package too), but it didn't work for me so I didn't mention it ... I always get an error about a file missing  ("Couldn't open file /var/lib/apt/lists/ppa.launchpad.net_fta_ubuntu_dists_intrepid_ibex_source_Sources (No such file or directory)")

and euchrid33, I forgot to mention that! You should have all previous version uninstalled! Uninstall libgpod (it will also uninstall amarok) and then follow the instructions.

Don't know why you get so strange errors ... I googled for at least an hour and didn't find anything concerning your problems ... and I don't know why it crashed your X-server and what could be responsible for this ...

Hope they'll release their libgpod release candidate soon! It works perfectly with both amarok and gtkpod. So they can make it available in the repos ...

BlackHawk

---

### Post by samp-wallah on 2009-01-25
Do any of you who have managed to get this to work have your ipods formatted with hfs? Would that even make a difference?

I know what it means to compile something from source and have done it, but only once a long time ago. I'm not sure how to go about find the source code for libgpod. Am I missing something, or forgetting something further up the thread? (I've read the thread a few times over the last week and just now decided to post.)

Thanks.

---

### Post by hellz99 on 2009-01-25
> **samp-wallah said:**
> Do any of you who have managed to get this to work have your ipods formatted with hfs? Would that even make a difference?


By this you mean it was originally formatted on mac, correct?
I will say this, the only computer I have runs ubuntu.  I got a new ipod nano for xmas, but I've never plugged it in to itunes (win or mac).  So I'm not sure it will make a difference.  Using amarok it was initialized (I guess that mean formatted) and song management, copying cover art, podcasts, etc was all done in amarok.

---

### Post by samp-wallah on 2009-01-25
That should mean your ipod is formatted in fat32. Type 'mount' in a terminal to find out. 
I used a Mac to set up my ipod b/c I couldn't get iTunes to work with Ubuntu.

---

### Post by BlackHawk1990 on 2009-01-27
Hello samp-wallah,

actually I think you really missed something ...
Though I didn't explain what it means to compile from source, you find a link to the libgpod source code in one of my previous posts (where I explained how to install it)

If I were you I'd consider to initialize your ipod with amarok OR have a look at [Floola]("http://www.floola.com"). It is kind of an alternative for iTunes and you don't even have to install it. I tried it with my ipod but since it was initialized with linux it didn't work (Floola works with Win- or Mac-formatted ipods only)

It has most functions iTunes has and you can open it directly from your iPod on ANY computer, you just have to copy it onto your ipod. (on their site you'll find a how-to ;) )

Hope I could help you,
BlackHawk

edit: I don't think it would make any difference for amarok which file system you use. But I don't know for sure, just try it out ;)

---

### Post by gregharris on 2009-01-27
Hey, i was so glad to see that some people actually managed to make this work, but unfortunately doesn't work with me... when i'm trying to configure amarok here's what i get :

checking for X... configure: error: Can't find X libraries. Please check your installation and add the correct paths!


Help please !


Edit: I've gone further now my problem is this : > checking for KDE... configure: error:
in the prefix, you've chosen, are no KDE libraries installed. This will fail.
So, check this please and use another prefix!



I installed kde-devel as i'm currently using gnome but i keep having this error i think it may be because it is searching for kde in the wrong directory, it's currently in /usr/share/docs/kde 

i tried doing this but it won't work i keep having the same bug again and again :>  sudo /.configure --with-libgpod -L</usr/share/doc/kde>


I could use some help :p 
Thanks

Edit 2 : It works for me ! it took me a couple of hours but that was worth it thank you so much for posting this !

---

### Post by samp-wallah on 2009-01-28
Thanks BlackHawk1990! I should not have posted before bed! 

I have libgpod squared away but now I am stuck on configuring amarok. 
I have tried to install kdelibs5-dev and kdelibs4-dev but both time got this dependency error: 
depends: libpcre3-dev but it is not going to be installed

I will continue to work on it. Thanks everyone for your input!

I made it through the configuration. I would like to add  =   - MP4/AAC Tag Write Support
but have not be able to figure out how. I went ahead with make and make install anyway and this error msg came back:

make[4]: Entering directory `/home/drew/amarok-1.4.10/amarok/src'
/bin/bash ../../libtool --silent --tag=CXX   --mode=link g++  -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wchar-subscripts -Wall -W -Wpointer-arith -O2 -Wformat-security -Wmissing-format-attribute -Wno-non-virtual-dtor -fno-exceptions -fno-check-new -fno-common -DQT_CLEAN_NAMESPACE -DQT_NO_ASCII_CAST -DQT_NO_STL -DQT_NO_COMPAT -DQT_NO_TRANSLATION   -R /usr/lib -R /usr/lib -R /usr/lib  -o libamarok.la -rpath /usr/lib actionclasses.lo app.lo atomicstring.lo atomicurl.lo browserbar.lo clicklineedit.lo collectionbrowser.lo collectiondb.lo columnlist.lo configdialog.lo contextbrowser.lo coverfetcher.lo covermanager.lo cuefile.lo deletedialog.lo deviceconfiguredialog.lo devicemanager.lo directorylist.lo dynamicmode.lo enginebase.lo enginecontroller.lo engineobserver.lo equalizergraph.lo equalizerpresetmanager.lo equalizersetup.lo expression.lo fht.lo filebrowser.lo hintlineedit.lo htmlview.lo iconloader.lo k3bexporter.lo kbookmarkhandler.lo ktrm.lo lastfm.lo mediabrowser.lo mediadevicemanager.lo medium.lo mediumpluginmanager.lo metabundle.lo metabundlesaver.lo moodbar.lo mountpointmanager.lo multitabbar.lo mydiroperator.lo osd.lo pixmapviewer.lo playerwindow.lo playlist.lo playlistbrowser.lo playlistbrowseritem.lo playlistitem.lo playlistloader.lo playlistselection.lo playlistwindow.lo pluginmanager.lo podcastsettings.lo prettypopupmenu.lo queuemanager.lo refreshimages.lo scancontroller.lo scriptmanager.lo scrobbler.lo sliderwidget.lo smartplaylisteditor.lo socketserver.lo starmanager.lo statistics.lo systray.lo tagdialog.lo tagguesser.lo threadmanager.lo tooltip.lo trackpickerdialog.lo tracktooltip.lo transferdialog.lo xmlloader.lo xspfplaylist.lo editfilterdialog.lo Options1.lo Options2.lo Options4.lo Options5.lo Options7.lo Options8.lo dbsetup.lo deletedialogbase.lo firstrunwizard.lo newdynamic.lo organizecollectiondialog.lo podcastsettingsbase.lo scriptmanagerbase.lo tagdialogbase.lo tagguesserconfigdialog.lo trackpickerdialogbase.lo ../../amarok/src/amarokcore/libamarokcore.la ../../amarok/src/analyzers/libanalyzers.la ../../amarok/src/plugin/libplugin.la ../../amarok/src/statusbar/libstatusbar.la ../../amarok/src/metadata/libmetadata.la ../../amarok/src/magnatunebrowser/libmagnatunebrowser.la -lkutils -lkio -lkdeui -lkdecore -lkhtml -lknewstuff -ltag   -lGL  ../../amarok/src/sqlite/libsqlite.la    
/usr/bin/ld: cannot find -lGL
collect2: ld returned 1 exit status
/usr/bin/ld: cannot find -lGL
collect2: ld returned 1 exit status
make[4]: *** [libamarok.la] Error 1
make[4]: Leaving directory `/home/drew/amarok-1.4.10/amarok/src'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/drew/amarok-1.4.10/amarok/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/drew/amarok-1.4.10/amarok'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/drew/amarok-1.4.10'
make: *** [all] Error 2

Any ideas on what I have missed?

---

### Post by BlackHawk1990 on 2009-02-01
Hello samp-wallah,

look at this thread: [http://forum.ubuntuusers.de/topic/usr-bin-ld:-cannot-find-lgl/]("http://forum.ubuntuusers.de/topic/usr-bin-ld:-cannot-find-lgl/"). There's someone that had the same error message and they say which packages you need. (they say libgl1-mesa-dev and libglu1-mesa-dev, but look at the thread ;) )

And did you try to build it with mp4-support or without?

Hope it works for you!

BlackHawk

---

### Post by RevoS on 2009-02-25
you're not the onlyone struggling with the 4G nano. Like mentioned before, the installation of libgpod-0.7.0 didn work. Until I came across [this]("http://procrastiblog.com/2009/02/16/using-an-ipod-nano-on-linux/") site. Added the link to my repositories, reinstalled Amarok and... it works! The artwork on my nano 4G orange is shown!

---

### Post by samp-wallah on 2009-03-02
RevoS,

Thanks for that link. I'm set now. I had chickened out and starting using iTunes a week ago...but I much prefer amarok's interface. Thanks BlackHawk for trying to help me do this manually.

---

### Post by ollie4028 on 2009-04-25
I was getting an error like this:


mtpmediadevice.cpp:611: error: at this point in file
/usr/local/include/libmtp.h: In member function 'void MtpMediaDevice::playlistFromItem(MtpMediaItem*)':
/usr/local/include/libmtp.h:521: error: too many arguments to function 'int LIBMTP_Create_New_Playlist(LIBMTP_mtpdevice_t*, LIBMTP_playlist_t*)'
mtpmediadevice.cpp:916: error: at this point in file
gmake[5]: *** [mtpmediadevice.lo] Error 1
gmake[5]: Leaving directory `/usr/ports/audio/amarok/work/amarok-1.4.10/amarok/src/mediadevice/mtp'
gmake[4]: *** [all-recursive] Error 1
gmake[4]: Leaving directory `/usr/ports/audio/amarok/work/amarok-1.4.10/amarok/src/mediadevice'
gmake[3]: *** [all-recursive] Error 1
gmake[3]: Leaving directory `/usr/ports/audio/amarok/work/amarok-1.4.10/amarok/src'
gmake[2]: *** [all-recursive] Error 1
gmake[2]: Leaving directory `/usr/ports/audio/amarok/work/amarok-1.4.10/amarok'
gmake[1]: *** [all-recursive] Error 1
gmake[1]: Leaving directory `/usr/ports/audio/amarok/work/amarok-1.4.10'
gmake: *** [all] Error 2
*** Error code 2

Stop in /usr/ports/audio/amarok.
*** Error code 1




What fixed it was doing what Blackhawk1990 did in post #14 but step 7 was

"sudo ./configure --with-libgpod --without-arts --without-libmtp"

fyi I was also getting an error about aRts you may not need "--without-arts".

I found this reference: [http://daemonforums.org/showthread.php?p=19321](http://daemonforums.org/showthread.php?p=19321)

I also had to add Ruby 4.2 in the Synaptic Package Manager

I am using Ubuntu 9.0.4 (Jaunty Jackaloupe) and Amarok 1.4.10 with a 4th gen ipod nano 16gb.

---

### Post by Karpah on 2009-04-27
Worked perfectly for me under Jaunty. I now have Amarok 1.4.10 and am quite happy.

I skipped some of Blackhawk1990's steps (compiling libgpod) and just installed libgpod-dev. I then downloaded the amarok-1.4.10 tarball, had to install a couple of extra packages (libxine-dev, x-dev, kdelibs-dev, libtag1-dev, ruby-dev), and then the install worked just fine. Compiled, worked with my iPod nano with artwork, absolutely beautiful. :D

(removed all the extra packages once I had Amarok working fine, because I like keeping a relatively clean system. Still works all good :)

---

### Post by euchrid33 on 2009-04-27
I've actually given up on Amarok, for a variety of reasons, and under Jaunty I've started using Rhythmbox to manage my music.  It loads cover art perfectly onto my iPod 4G nano, and I recommend giving it a try.  Even if you like the rest of Amarok's features, perhaps you could just use Rhythmbox to manage your iPod?

---

### Post by FAJALOU on 2009-06-26
Hi:  It's great that all you guys are getting this to work... but I am still not :'(.  If rythmbox works, hey great, can someone help me get it working.  Or can someone send me the files I need to get it working in Amarok, or Banshee, or GTKPod.

I tried in GTKPod... Failed

Amarok (well I don't know how to do it anymore because of the upgrade to Jaunty...)

Banshee... Fails.

Any help is appreciated. Thanks!

---

