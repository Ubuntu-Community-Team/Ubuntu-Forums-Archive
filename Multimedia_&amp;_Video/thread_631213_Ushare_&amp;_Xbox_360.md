---
title: "Ushare &amp; Xbox 360"
date: 2007-12-04
forum: Multimedia &amp; Video
---

### Post by edwardandtubs on 2007-12-04
Now that the xbox360 can play DivX/Xvids (since Fall update 04/12/07) I thought I'd install ushare so that I can see the media files on my linux box (the windows machine is sharing divx just fine). 

So I installed it, and I can browse the files on the 360, but cannot play them...

I've turned verbose mode on and get the following...

Found 37 files and subdirectories.
ServiceID: urn:microsoft.com:serviceId:X_MS_MediaReceiverRegistrar
actionName: IsAuthorized
CtrlPtIP: 192.168.2.6
ServiceID: urn:upnp-org:serviceId:ContentDirectory
actionName: Browse
CtrlPtIP: 192.168.2.6
Missing action request argument (ObjectID)
Looking for entry id 15
Not Found
Looking for entry id 100000
Found at 0x8069118

Can anybody shed any light on this....

---

### Post by pjriot on 2007-12-04
+1 (sorry to get your hopes up, I'd love to see this working too)

---

### Post by havchr on 2007-12-04
I'm in the same situation, though I havn't tried using windows software to share my divx/xvids.. I guess they would work, but they don't work on ushare.

Previously I've been looking for other solutions and I came across fuppes, but I coudln't compile it because it with transcoding support (which was I was looking for atm), because it required another ffmpeg-lib version to what was in the ubuntu-repo.
Now that the 360 supports xvid/divx I'm gonna try it without transcoding support and see if fuppes can share the vids.

Here is link to fuppes.
[http://fuppes.ulrich-voelkel.de/](http://fuppes.ulrich-voelkel.de/)

---

### Post by edwardandtubs on 2007-12-04
> **havchr said:**
> I'm in the same situation, though I havn't tried using windows software to share my divx/xvids.. I guess they would work, but they don't work on ushare.

Previously I've been looking for other solutions and I came across fuppes, but I coudln't compile it because it with transcoding support (which was I was looking for atm), because it required another ffmpeg-lib version to what was in the ubuntu-repo.
Now that the 360 supports xvid/divx I'm gonna try it without transcoding support and see if fuppes can share the vids.

Here is link to fuppes.
[http://fuppes.ulrich-voelkel.de/](http://fuppes.ulrich-voelkel.de/)

I've given up with ushare and installed twonkymedia server instead....this works more or less out of the box (zip file)...woohoo..

Couple of links :-
[http://www.twonkyvision.com/](http://www.twonkyvision.com/)
[http://www.twonkyforum.com/viewtopic.php?t=3797&highlight=](http://www.twonkyforum.com/viewtopic.php?t=3797&highlight=)

---

### Post by havchr on 2007-12-04
costs money I see, but if it works out of the box, then I'll be inclined to pay for it.

edit:
Tested now. It seems to work just fine. :)
Better go get them 30 or so euros out of my virtual pocket.

---

### Post by notwen on 2007-12-04
> **edwardandtubs said:**
> I've given up with ushare and installed twonkymedia server instead....this works more or less out of the box (zip file)...woohoo..

Couple of links :-
[http://www.twonkyvision.com/](http://www.twonkyvision.com/)
[http://www.twonkyforum.com/viewtopic.php?t=3797&highlight=](http://www.twonkyforum.com/viewtopic.php?t=3797&highlight=)

Works as in streams mp3s and divx/avi? =]  With this latest update enabling divx playback I'm even more compelled to fork out for a -just works- solution.

---

### Post by edwardandtubs on 2007-12-04
> **notwen said:**
> Works as in streams mp3s and divx/avi? =]  With this latest update enabling divx playback I'm even more compelled to fork out for a -just works- solution.

I've tested divx/avi's and they stream just fine...

TwonkyMedia can be tried for free for 30days (handy for xmas!), just give it a try....:)

---

### Post by notwen on 2007-12-04
Good to hear, 30 days may be enough for me to use some holiday cash on a present for myself.  Thanks for the reference.

---

### Post by realityisok on 2007-12-04
alright. thanks for suggesting TwonkyVision, but i'd rather stay with the free alternative that is uShare...

so far what i get is:

it shows and play all every .wmv files from my shared folders. the problem is that it doesn't show any .avi files and show the folders containing only .avi as empty.

---

### Post by Protoss on 2007-12-04
> **realityisok said:**
> alright. thanks for suggesting TwonkyVision, but i'd rather stay with the free alternative that is uShare...

so far what i get is:

it shows and play all every .wmv files from my shared folders. the problem is that it doesn't show any .avi files and show the folders containing only .avi as empty.

Alright my attempt at a hack-ish solution didn't work....

---

### Post by RdKetchup on 2007-12-04
A new version of uShare (1.1) as just been released.  If it doesn't show, hit refresh once on the [http://ushare.geexbox.org/](http://ushare.geexbox.org/) page.

I don't know if it fixes the problem with Divx/Xvid support for the 360, I'll have to compile it and try it out later tonight.

---

### Post by reference2myself on 2007-12-04
i'm using ushare v1.1 and get the same results, seems the -x that makes it 360 compliant also blocks avi.

---

### Post by realityisok on 2007-12-04
> **reference2myself said:**
> i'm using ushare v1.1 and get the same results, seems the -x that makes it 360 compliant also blocks avi.

i'm came to that conclusion also after installing v1.1.

---

### Post by Hubris2 on 2007-12-04
Agreed - it seems to agree with what some of the Mac folks have been suggesting, which is that the app streaming data often will restrict the files to the ones it 'knows' can be played by the Xbox 360....even though that info is outdated.

So now....we try lobby the creator of Ushare to update his app?  :)

---

### Post by cgipro on 2007-12-04
I made a quick hack to the ushare source code to make this work.  No guarantees, but it worked fine for me.  If you want to make this change, you will need to compile ushare from source code.  Edit the mime.c file on line 38 - it should look like this:

```
{ "avi",   UPNP_VIDEO, "http-get:*:video/x-msvideo:"},
```

Change it to this:

```
{ "avi",   UPNP_VIDEO, "http-get:*:video/x-ms-wmv:"},
```

This basically just tricks ushare into thinking the avi files are wmv files so they will be shared with the xbox.  The Xbox still can read them as AVI files and plays them fine.  I've tested with a few xvid movies, and they work great.

**EDIT** This is with version 1.1 that I am testing.  Good luck

---

### Post by falz on 2007-12-04
Created an account just to chime in and say that that fix worked for me as well. I was messing with that line earlier, but I guess I didnt guess the right mime type! In my case it was using Ushare 1.0 on FreeBSD, but all works perfectly well. I emailed the author with that info, a link to this thread, and a note that that's probably not the 'correct' mime type, but it works.

--falz

---

### Post by otherdave on 2007-12-04
I'm not sure if any of you tried this, but renaming my .avi files to .wmv or .mov worked :)

It's a little more low-tech than re-compiling but it worked with version 1.0. 

I've only tried it with a DIVX avi (no xvid yet) but both the .mov and .wmv extension worked with:

$ ushare -x -c /path/to/stuff -v -i eth0

Also, symbolic links work too (if you don't want to rename all of your files)

---

### Post by Hubris2 on 2007-12-04
Renaming files is working for me.

Question....I'm using the version 1.0 from the repository.  One thing I'm noticing tonight....dvd rips that are letterboxed are coming out as 4:3 on my (4:3) television, even when I select letterbox mode in the dashboard.  Is there a workaround?

---

### Post by falz on 2007-12-04
> **Hubris2 said:**
> One other thing I'm noticing tonight....dvd rips that are letterboxed are coming out as 4:3 on my (4:3) television, even when I select letterbox mode in the dashboard.  Is there a workaround?
Does this happen from other sources? Is your TV 480p only, or higher? I know some of the older 4:3 hdtv's (I guess the only ones are old) has issues like that, but it was generally related to the TV.

---

### Post by Hubris2 on 2007-12-04
It's an old tv, it's only 480p - but shouldn't it be showing with black bars for letterboxing?

---

### Post by nate010111 on 2007-12-04
Can someone throw up some quick instructions on how to compile ushare from source on a fresh gutsy install.  When trying to configure I get something like "Error, can't find libixml".  I need to compile this so I can make the change that will let my Xbox see .avi files.  Thanks.

---

### Post by Protoss on 2007-12-04
> **cgipro said:**
> I made a quick hack to the ushare source code to make this work.  No guarantees, but it worked fine for me.  If you want to make this change, you will need to compile ushare from source code.  Edit the mime.c file on line 38 - it should look like this:

```
{ "avi",   UPNP_VIDEO, "http-get:*:video/x-msvideo:"},
```

Change it to this:

```
{ "avi",   UPNP_VIDEO, "http-get:*:video/x-ms-wmv:"},
```

This basically just tricks ushare into thinking the avi files are wmv files so they will be shared with the xbox.  The Xbox still can read them as AVI files and plays them fine.  I've tested with a few xvid movies, and they work great.

**EDIT** This is with version 1.1 that I am testing.  Good luck

Sweet. This works perfectly, thanks.

---

### Post by nosscire on 2007-12-05
> **nate010111 said:**
> Can someone throw up some quick instructions on how to compile ushare from source on a fresh gutsy install.  When trying to configure I get something like "Error, can't find libixml".  I need to compile this so I can make the change that will let my Xbox see .avi files.  Thanks.

Same problem here... Anyone know?

---

### Post by belboz on 2007-12-05
Install the two requirements first before building ushare and you shouldn't have any problems.

I got the libixml error, but I compiled and installed the libupnp, and the libdlna first and then compiled ushare with no problems.

If you get the error about libupnp being an older version (it isn't) just do an "sudo apt-get install pkg-config" then re-run ./configure

I have it working with my xbox 360 (after making the change noted previously so avi files stream fine).

Pretty much all my new stuff works, but I do have some avi files from 2-3 years back that won't play.  All and all it works well.

Only problem I haven't ironed out yet is I have three drives I have various videos stored on (all on the linux box).  I ran ushare like this...

ushare -x -c /drive1/path -c /drive2/path -c /drive3/path -i eth0

But the xbox only sees the first share.

My DirecTV receiver sees all three directories. I may be missing something, but I think I am going to have to create a directory that aliases to the three drives and point ushare to that one directory.

---

### Post by edwardandtubs on 2007-12-05
> **cgipro said:**
> I made a quick hack to the ushare source code to make this work.  No guarantees, but it worked fine for me.  If you want to make this change, you will need to compile ushare from source code.  Edit the mime.c file on line 38 - it should look like this:

```
{ "avi",   UPNP_VIDEO, "http-get:*:video/x-msvideo:"},
```

Change it to this:

```
{ "avi",   UPNP_VIDEO, "http-get:*:video/x-ms-wmv:"},
```

This basically just tricks ushare into thinking the avi files are wmv files so they will be shared with the xbox.  The Xbox still can read them as AVI files and plays them fine.  I've tested with a few xvid movies, and they work great.

**EDIT** This is with version 1.1 that I am testing.  Good luck

I'm glad I didnt rush out and buy TwonkyMedia...will try this out later.....

Can anyone post an idiots guide on compiling ushare for those that don't know how to?

---

### Post by cmoz on 2007-12-05
Easy solution to all this is that if you rename your xvid/divx files to have a .mov extension instead of a .avi extension they show up and play perfectly no compiling from source needed

---

### Post by nosscire on 2007-12-05
Yeah, I hadn't installed libupnp properly. When I did that that part worked.
Still couldn't get it to compile though, got an error on libdnla (which I have installed properly), so after a while I just disable'd dlna, as it doesn't seam to be nessesary for X360. What is DLNA anyway?

Anyway, now it's working smoothly :) Too bad the xbox has no subtitle support though. Guess i'll have to live with that.

Thanks for a great hack!

---

### Post by Crube on 2007-12-05
I haven't even been able to test this yet. I've tried compiling ushare and installing it from the repos but for some reason it's broken. All i get is:
bash: /bin/ushare: No such file or directory :)

---

### Post by realityisok on 2007-12-05
> **belboz said:**
> Only problem I haven't ironed out yet is I have three drives I have various videos stored on (all on the linux box).  I ran ushare like this...

ushare -x -c /drive1/path -c /drive2/path -c /drive3/path -i eth0

But the xbox only sees the first share.

I got the same problem.

---

### Post by falz on 2007-12-05
Ushare wants its shares in comma separated format. At least it does if you use a config file. Create a config file such as:

```
USHARE_NAME=ushare
USHARE_IFACE=eth0
USHARE_PORT=
USHARE_DIR=/opt/files/videos,/opt/files/mp3
USHARE_OVERRIDE_ICONV_ERR=
```


..and point ushare to this file with **-f**

```
ushare  -x -v -f /path/to/ushare.conf
```

---

### Post by un_dave on 2007-12-05
Could someone explain to me exactly how i'm meant to get my 360 to see my pc at all?

I run this command, 
```
dave@hades:~$ ushare -x -c /home/dave/Storage/
uShare (version 1.1), a lightweight UPnP Media Server.
Benjamin Zores (C) 2005-2007, for GeeXboX Team.
See http://ushare.geexbox.org/ for updates.
Listening on telnet port 1337
Initializing UPnP subsystem ...
Starting in XboX 360 compliant profile ...
UPnP MediaServer listening on 10.1.1.103:49152
Sending UPnP advertisement for device ...
Listening for control point connections ...
Building Metadata List ...
Looking for files in content directory : /home/dave/Storage/
Found 32069 files and subdirectories.

```

and it all seems to be working fine from the that side of things, but when I go to my 360, with the fall update applied, the 360 doesn't see the pc in the videos/computers section, or as a media center...

Am i missing something here?

---

### Post by belboz on 2007-12-05
Well when I did multiple share locations on the command line (they show this on their web site as an example) the 360 would only see the first share, but my DirecTV receiver would see all three shares.

So I don't think it was an issue of using commas since the DirecTV receiver saw everything through ushare, but the 360 didn't.

Regardless last night I created a directory and put aliases to my video drives and set ushare to share that directory and the 360 saw everything.


> **falz said:**
> Ushare wants its shares in comma separated format. At least it does if you use a config file. Create a config file such as:

```
USHARE_NAME=ushare
USHARE_IFACE=eth0
USHARE_PORT=
USHARE_DIR=/opt/files/videos,/opt/files/mp3
USHARE_OVERRIDE_ICONV_ERR=
```


..and point ushare to this file with **-f**

```
ushare  -x -v -f /path/to/ushare.conf
```

---

### Post by Ejoc on 2007-12-05
> **Hubris2 said:**
> Renaming files is working for me.

Question....I'm using the version 1.0 from the repository.  One thing I'm noticing tonight....dvd rips that are letterboxed are coming out as 4:3 on my (4:3) television, even when I select letterbox mode in the dashboard.  Is there a workaround?

Have you made any progress on this Hubris2?  I'm in the same boat.


I do not know if this is related, but one of the first things I tried was renaming one of my .avi DivX files to .mov and the 360 could not play it.  I encoded all of the videos myself using mencoder using the standard DVD resolution of 720x480 with an aspect ratio of 16:9.  I'm wondering if the hack to have the avi mime info appear as a wmv is causing the aspect ratio info to be ignored...

---

### Post by havchr on 2007-12-05
> **belboz said:**
> Install the two requirements first before building ushare and you shouldn't have any problems.

I got the libixml error, but I compiled and installed the libupnp, and the libdlna first and then compiled ushare with no problems.

If you get the error about libupnp being an older version (it isn't) just do an "sudo apt-get install pkg-config" then re-run ./configure

I have it working with my xbox 360 (after making the change noted previously so avi files stream fine).

Pretty much all my new stuff works, but I do have some avi files from 2-3 years back that won't play.  All and all it works well.

Only problem I haven't ironed out yet is I have three drives I have various videos stored on (all on the linux box).  I ran ushare like this...

ushare -x -c /drive1/path -c /drive2/path -c /drive3/path -i eth0

But the xbox only sees the first share.

My DirecTV receiver sees all three directories. I may be missing something, but I think I am going to have to create a directory that aliases to the three drives and point ushare to that one directory.


For this issue, I've made a folder called "SUPERMEDIA" with symlinks to my ntfs disk, some directories in my home folder, etc.. Works good with twonky, probably works good with ushare too.

---

### Post by jsnwtsn on 2007-12-05
I made a short How-To for this... hope it helps

How to make Ubuntu 7.10(Gutsy), uShare and xBox 360 play nice.

Requirements:
* ubuntu 7.10(gutsy)
* ushare 1.1
* xbox 360 w/ fall 2007 update applied

Finally with the xbox 360 fall update it is possible to play divx/xvid videos. Using the latest ushare and re-associating the ".avi" mime type, it will be possible to stream divx media to the xbox 360. Making the xbox 360 the media center it should have always been.

1. Update your xbox 360. By connecting to "xBox Live" it should prompt you to download the update.

2. Install uShare. 

uShare requires the lib "libdlna", so we will download that and install first:

```
wget http://www.geexbox.org/debian/pool/main/libdlna/libdlna0_0.2.3-0ubuntu1_i386.deb
```

```
sudo dpkg -i libdlna0_0.2.3-0ubuntu1_i386.deb
```

Now download and install uShare:

```
wget http://www.geexbox.org/debian/pool/main/ushare/ushare_1.1-0ubuntu1_i386.deb
```

```
sudo dpkg - ushare_1.1-0ubuntu1_i386.deb
```

3. Configure ushare

Edit the file "/etc/ushare.conf" to your liking(you need to set your content directory):

```
sudo nano /etc/ushare.conf
```

4. Change mime type for ".avi" files

```
sudo nano :/usr/share/mime/packages/freedesktop.org.xml
```

edit the line:
```
<mime-type type="video/x-msvideo">
```

to this:
```
<mime-type type="video/x-ms-wmv">
```

5. Restart Gnome
 
Restart Gnome by logging out or simply reboot.

6. Start ushare

to start ushare with xbox compatibility:
```
ushare -x
```

7. Watch your divx videos.
On your xbox, go to the "Media" blade, then select "Video", then press the "X" button to select your media source. The xbox should find your ushare server at this point. 

Enjoy!

---

### Post by belboz on 2007-12-05
Yes, if you check my post a few before yours, you will see I made a directory and put some aliases in it to my various drives.  Worked fine.  

360 sees everything.

> **havchr said:**
> For this issue, I've made a folder called "SUPERMEDIA" with symlinks to my ntfs disk, some directories in my home folder, etc.. Works good with twonky, probably works good with ushare too.

---

### Post by Khyber on 2007-12-05
Creating aliases also worked for me. I didn't bother to edit the mime.c file and instead just changed the .avi extension to .wmv and doing that worked. The only real bug I have is that my 360 won't play certain mp3's. I need to spend some more time and see what could be causing the issue.

---

### Post by colin winters on 2007-12-05
Like others, I'm unable to get the 360 to detect the ushare.  I have the 360 connected to a windows laptop through a CAT cable, and the linux server is connected to the same wireless router that the laptop is.

The 360 can use the internet fine, and the laptop can access the ushare web interface on the server, yet the 360 won't detect the ushare server.  What am I missing here?

---

### Post by un_dave on 2007-12-05
I'm in the same situation colin, 

Everything is connecting to the net fine, and the network is otherwise working, but maybe it has something to do with this:

From the ushare website:
> 
At first you need to be sure that you have setup a multicast route for UPnP messages. If you don't but have a default route attributed, then this later will be used. Otherwise, simply declare a new route for UPnP multicasts (for example using eth0 interface) :

route add -net 239.0.0.0 netmask 255.0.0.0 eth0


I have two switches between my 360 and the ushare server, so maybe something isn't forwarding multicasts?

---

### Post by stormchas3r on 2007-12-05
Sup guys.  I ran across this thread, thank God.  I followed all the directions which are awesome.  I have a couple of probs.  I cannot play any mp3's at all.  It simply just doesnt play.  But I did the hack to rename the msvideo to ms-wmv, and that worked well.  How are we suppose to get mp3's or any audio file to play.

Anyway, great tutorial.  I have been waiting for something like this, so we don't have to use MCE.  

L8:guitar:

---

### Post by otherdave on 2007-12-05
Will setting the mime type to wmv cause any problems elsewhere? 

Also, will the X-Box play a video with the DIVX mime-type? I haven't tried this yet (not near my XBox), but I was wondering if instead of using wmv we used "video/x-divx" instead. Any thoughts? Anyone have time to try it?

Since the XBox update lets it play DIVX, why not use the DIVX mime type?

---

### Post by Ejoc on 2007-12-05
> **Ejoc said:**
> Have you made any progress on this Hubris2?  I'm in the same boat.


I do not know if this is related, but one of the first things I tried was renaming one of my .avi DivX files to .mov and the 360 could not play it.  I encoded all of the videos myself using mencoder using the standard DVD resolution of 720x480 with an aspect ratio of 16:9.  I'm wondering if the hack to have the avi mime info appear as a wmv is causing the aspect ratio info to be ignored...


Did some testing and it seems to lose the aspect information and goes for a 4:3 aspect ratio.  I encoded a test piece of video and scaled it to 854x480 (16/9) and that plays as letter box, and changing the display settings on the 360 actually works.  While this is not a solution it does shed some light on the issue.

---

### Post by Timsy321 on 2007-12-05
I tried following the instructions as above in how to install ushare and how to enable the avi support, but it didnt seem to work. When i went in to edit the freedesktop mime file, there was nothing of relevance. I read somewhere else that you need to compile ushare from source code in order to be able to edit the mime.c file. But i do not know how to do that. If someone could show me how that would be awesome! Thanks!

---

### Post by Timsy321 on 2007-12-05
So i figured out how to edit the config file now, what i was wondering is if i want my avi files to play,  i have to rename them to wmv. I was wondering if there was a way to get avi files to show up on the xbox? and if not....is there a way to rename multiple files. I have a couple full season avi's and i would like to be able to just change the extension on all of them to .wmv. thanks!

---

### Post by notwen on 2007-12-05
I've played w/ uShare all night and have video streaming w/lo issue as long as I change file extensions to .wmv.  Is uShare filtering the .avi, shouldn't my divx/xvid files be showing up regardless of extension?  I know they work perfectly fine off a USB drive.  Also I cannot stream mp3s, they show up but when I choose to play, nothing happens.  Any thoughts and/or recommendations would be appreciated.

---

### Post by bartoni on 2007-12-06
Decided to give up on fuppes and try ushare... but any chance of a nice simple how to? I'm struggling to just install it let alone get it to play anything.

Tried following this earlier post with no success : 

> **jsnwtsn said:**
> I made a short How-To for this... hope it helps

2. Install uShare. 

uShare requires the lib "libdlna", so we will download that and install first:

```
wget http://www.geexbox.org/debian/pool/main/libdlna/libdlna0_0.2.3-0ubuntu1_i386.deb
```

```
sudo apt-get insstall libdlna0_0.2.3-0ubuntu1_i386.deb
```

Now download and install uShare:

```
wget http://www.geexbox.org/debian/pool/main/ushare/ushare_1.1-0ubuntu1_i386.deb
```

```
sudo apt-get install ushare_1.1-0ubuntu1_i386.deb
```

etc. etc.


the 'apt-get install' on deb files seems wrong for a start, changed these to 'dpkg -i'

but get a dependency error on ushare : 
"ushare depends on libupnp2; however: Package libupnp2 is not installed."

Fallen at first hurdle.  Downloaded libupnp source from geexbox link, compiled... with success, but now what? Probably haven't installed it properly as ushare still complains.

Ahh... the joys of Linux eh?

---

### Post by otherdave on 2007-12-06
> **bartoni said:**
> Decided to give up on fuppes and try ushare... but any chance of a nice simple how to? I'm struggling to just install it let alone get it to play anything.

You can use the installation instructions from uShare's site:

[http://ushare.geexbox.org/#Download](http://ushare.geexbox.org/#Download)

Edit your /etc/apt/sources.list and put the following line at the bottom:
```
deb [http://www.geexbox.org/debian/](http://www.geexbox.org/debian/) unstable main
```

Then you can run:

apt-get update && apt-get install ushare

This worked for me a few days ago and yesterday the packages was updated to version 1.1 so I'm running that.

---

### Post by jsnwtsn on 2007-12-06
A Better " How to make Ubuntu, uShare(from source) and xBox 360 play nice."


Apologies to everyone for my previous "How-To", it was more of a "How-Not-To". A lot of people where having problems, and my "How-To" only worked if you changed the file extension...which is lame. 

So here is the corrected way to get Ubuntu, uShare & your xbox 360 to play nice. Once installed you should be able to stream divx video files that have the ".avi" extension to your xbox 360. 

Some folks have asked about streaming mp3 files, i have yet ti figure this out, when/if i do i will post how.

Requirements:
* ubuntu 7.10(gutsy)
* xbox 360 w/ fall 2007 update applied
* libupnp
* libdlna
* ushare 1.1 source

Update your xbox 360. By connecting to "xBox Live" it should prompt you to download the update.

Install required libs

Install the UPNP dev libs
```
sudo apt-get install libupnp-dev
```

Download and install the DLNA libs
```
wget http://www.geexbox.org/debian/pool/main/libdlna/libdlna0_0.2.3-0ubuntu1_i386.deb
sudo dpkg -i libdlna0_0.2.3-0ubuntu1_i386.deb
``` 

Download and extract uShare source
```
wget http://ushare.geexbox.org/releases/ushare-1.1.tar.bz2
tar -xvf ushare-1.1.tar.bz2
```

Edit mime.c file. This makes ushare present .avi files to the xbox as a mime type it can play
```

cd ushare-1.1/

nano src/mime.c

```

Change this line:
```
{ "avi",   UPNP_VIDEO, "http-get:*:video/x-msvideo:"},
```
to this:
```
{ "avi",   UPNP_VIDEO, "http-get:*:video/x-ms-wmv:"},
```


Now configure, make and install.

```
./configure --log --prefix=/usr --sysconfdir=/etc --disable-dlna
make
sudo make install
```

Edit the file "/etc/ushare.conf" to your liking(you need to set your content directory):
```
sudo nano /etc/ushare.conf
```

start ushare with xbox compatibility:
```
ushare -x
```

On your xbox, go to the "Media" blade, then select "Video", then press the "X" button to select your media source. The xbox should find your ushare server at this point.

hopefully this time it works! ... have fun ;)

---

### Post by ieatkittens on 2007-12-06
> **jsnwtsn said:**
> 
Now configure, make and install.

```
./configure --log --prefix=/usr --sysconfdir=/etc --disable-dlna
make
sudo make install
```



I get:


Error, can't find libixml !

And the ./configure fails

---

### Post by colin winters on 2007-12-06
> **jsnwtsn said:**
> 
On your xbox, go to the "Media" blade, then select "Video", then press the "X" button to select your media source. The xbox should find your ushare server at this point.

hopefully this time it works! ... have fun ;)

Thanks for the updated tutorial.  Everything goes smoothly, until the 'should find your ushare server.'  I access ushare through the web interface, so I know it's working, but this is very confusing on why the 360 won't find it.

---

### Post by jsnwtsn on 2007-12-06
ieatkittens;  do you have "libupnp-dev" installed? it supplies the libixml libs.

---

### Post by colin winters on 2007-12-06
For my problem, it must be something to do with being connected through a laptop to the wireless.  I just installed and tried out twonkymedia, again I was able to use the web interface, but the 360 wouldn't find the server.

---

### Post by jsnwtsn on 2007-12-06
does your router support forwarding multicasts?

if not you might want to look here:
[URL="http://ushare.geexbox.org/#Usage"]
http://ushare.geexbox.org/#Usage[/URL]

---

### Post by colin winters on 2007-12-06
> **jsnwtsn said:**
> does your router support forwarding multicasts?

if not you might want to look here:
[URL="http://ushare.geexbox.org/#Usage"]
http://ushare.geexbox.org/#Usage[/URL]

Yeah, I'd set up that multicast even though I'm not really sure what it does :)

I also did find that I needed to uncheck 'filter multicast' in the router settings, but that didn't appear to make a difference.

---

### Post by ieatkittens on 2007-12-06
> **jsnwtsn said:**
> ieatkittens;  do you have "libupnp-dev" installed? it supplies the libixml libs.

I installed it but after doing an apt-get remove, apt-get update and then another apt-get install it appears to work fine now!

---

### Post by jsnwtsn on 2007-12-06
colin winters; are you sure that you started ushare with the "-x" flag ?

like so:
ushare -x

---

### Post by colin winters on 2007-12-06
> **jsnwtsn said:**
> colin winters; are you sure that you started ushare with the "-x" flag ?

like so:
ushare -x

Yep, sure did.  I'm wondering if the server's working right.  How can I connect to the ushare (or twonky) server, and play the files, from an XP laptop that I have?  That way I could confirm it's the 360 not seeing it.

---

### Post by bitshifter1001 on 2007-12-06
> **colin winters said:**
> Yeah, I'd set up that multicast even though I'm not really sure what it does :)

I also did find that I needed to uncheck 'filter multicast' in the router settings, but that didn't appear to make a difference.

Actually, I had to turn "Filter Multicast" on for uShare. I have also tested Twonky but didn't need the filtering for it. I haven't done any packet sniffing, but I would guess they are doing uPnP multicasting differently.

My advice, take the network out of the picture, and connect your uShare server directly to the 360. Make sure you use a crossover cable. Then test. If it works, then its your router.


[Edit]
I just tested Twonky again, and I needed "Filter Multicast" on for that as well. Sorry for the confusion.

---

### Post by pointfivezero on 2007-12-06
As a matter of interest, does anyone know how to get the system service to work correctly? I have modified the /etc/ushare.conf file to match what I would normally use from the commandline but alas, no dice.

Here is my  fully-working command line:

```

ushare -x -D -i br0 -p 49200 -n SharedPC -c /media/hdd1/supershare

```

And the corresponding /etc/ushare.conf which does not register as a computer on the xbox 360 BUT can be accessed via the http://localhost:49200/web/ushare.html web control:

```

# /etc/ushare.conf
# Configuration file for uShare

# uShare UPnP Friendly Name (default is 'uShare').
USHARE_NAME=SharedPC

# Interface to listen to (default is eth0).
# Ex : USHARE_IFACE=eth1
USHARE_IFACE=br0

# Port to listen to (default is random from IANA Dynamic Ports range)
# Ex : USHARE_PORT=49200
USHARE_PORT=49200

# Port to listen for Telnet connections
# Ex : USHARE_TELNET_PORT=1337
# USHARE_TELNET_PORT=

# Directories to be shared (space or CSV list).
# Ex: USHARE_DIR=/dir1,/dir2
USHARE_DIR=/media/hdd1/supershare

# Use to override what happens when iconv fails to parse a file name.
# The default uShare behaviour is to not add the entry in the media list
# This option overrides that behaviour and adds the non-iconv'ed string into
# the media list, with the assumption that the renderer will be able to
# handle it. Devices like Noxon 2 have no problem with strings being passed
# as is. (Umlauts for all!)
#
# Options are TRUE/YES/1 for override and anything else for default behaviour
#USHARE_OVERRIDE_ICONV_ERR=

# Enable Web interface (yes/no)
ENABLE_WEB=yes

# Enable Telnet control interface (yes/no)
#ENABLE_TELNET=

# Use XboX 360 compatibility mode (yes/no)
ENABLE_XBOX=yes

# Use DLNA profile (yes/no)
# This is needed for PlayStation3 to work (among other devices)
#ENABLE_DLNA=

```

Any ideas?

---

### Post by pointfivezero on 2007-12-06
Also, to get the ushare system service to work, I had to modify (!) the /etc/init.d/ushare script and add a change the line

```

start-stop-daemon --start --quiet --background --oknodo \
        --make-pidfile --pidfile $PIDFILE \
        --exec $DAEMON -- $USHARE_OPTIONS

```

To make it load the /etc/ushare.conf file (and thus succeed in binding):

```

start-stop-daemon --start --quiet --background --oknodo \
        --make-pidfile --pidfile $PIDFILE \
        --exec $DAEMON -- $USHARE_OPTIONS -f $CONFIGFILE

```

Hmmm!

---

### Post by pointfivezero on 2007-12-06
> **pointfivezero said:**
> Also, to get the ushare system service to work, I had to modify (!) the /etc/init.d/ushare script and add a change the line

```

start-stop-daemon --start --quiet --background --oknodo \
        --make-pidfile --pidfile $PIDFILE \
        --exec $DAEMON -- $USHARE_OPTIONS

```

To make it load the /etc/ushare.conf file (and thus succeed in binding):

```

start-stop-daemon --start --quiet --background --oknodo \
        --make-pidfile --pidfile $PIDFILE \
        --exec $DAEMON -- $USHARE_OPTIONS -f $CONFIGFILE

```

Hmmm!

Of note also is when I add the following line just below my modifications above;

```

log_daemon_msg "Debug: Echoing USHARE_OPTIONS '$USHARE_OPTIONS'"

```

Nothing useful is echoed;

```

$ sudo /etc/init.d/ushare start
 * Starting uShare UPnP A/V & DLNA Media Server: ushare                             [ OK ]
 * Got ''

```

Any help would be appreciated!

---

### Post by theelk801 on 2007-12-06
> **jsnwtsn said:**
> -snip-

It almost worked, up until I did make. It had some sort of error. The rest was great, though.

---

### Post by bitshifter1001 on 2007-12-06
> **pointfivezero said:**
> As a matter of interest, does anyone know how to get the system service to work correctly? I have modified the /etc/ushare.conf file to match what I would normally use from the commandline but alas, no dice.

Here is my  fully-working command line:

```

ushare -x -D -i br0 -p 49200 -n SharedPC -c /media/hdd1/supershare

```

And the corresponding /etc/ushare.conf which does not register as a computer on the xbox 360 BUT can be accessed via the [http://localhost:49200/web/ushare.html](http://localhost:49200/web/ushare.html) web control:

```

# /etc/ushare.conf
# Configuration file for uShare

# uShare UPnP Friendly Name (default is 'uShare').
USHARE_NAME=SharedPC

# Interface to listen to (default is eth0).
# Ex : USHARE_IFACE=eth1
USHARE_IFACE=br0

# Port to listen to (default is random from IANA Dynamic Ports range)
# Ex : USHARE_PORT=49200
USHARE_PORT=49200

# Port to listen for Telnet connections
# Ex : USHARE_TELNET_PORT=1337
# USHARE_TELNET_PORT=

# Directories to be shared (space or CSV list).
# Ex: USHARE_DIR=/dir1,/dir2
USHARE_DIR=/media/hdd1/supershare

# Use to override what happens when iconv fails to parse a file name.
# The default uShare behaviour is to not add the entry in the media list
# This option overrides that behaviour and adds the non-iconv'ed string into
# the media list, with the assumption that the renderer will be able to
# handle it. Devices like Noxon 2 have no problem with strings being passed
# as is. (Umlauts for all!)
#
# Options are TRUE/YES/1 for override and anything else for default behaviour
#USHARE_OVERRIDE_ICONV_ERR=

# Enable Web interface (yes/no)
ENABLE_WEB=yes

# Enable Telnet control interface (yes/no)
#ENABLE_TELNET=

# Use XboX 360 compatibility mode (yes/no)
ENABLE_XBOX=yes

# Use DLNA profile (yes/no)
# This is needed for PlayStation3 to work (among other devices)
#ENABLE_DLNA=

```

Any ideas?


If you are running the init script in /etc/init.d/ try adding the following after the variable CONFIGFILE. On the next line. 

USHARE_OPTIONS="-x"

---

### Post by pointfivezero on 2007-12-07
> **bitshifter1001 said:**
> If you are running the init script in /etc/init.d/ try adding the following after the variable CONFIGFILE. On the next line. 

USHARE_OPTIONS="-x"

Bingo, good suggestion! It works by adding the line:

```

USHARE_OPTIONS="-x -f $CONFIGFILE"

```

below CONFIGFILE=/etc/ushare.conf


Thanks heaps

---

### Post by I922sParkCir on 2007-12-07
> **jsnwtsn said:**
> A Better " How to make Ubuntu, uShare(from source) and xBox 360 play nice."


Apologies to everyone for my previous "How-To", it was more of a "How-Not-To". A lot of people where having problems, and my "How-To" only worked if you changed the file extension...which is lame. 

So here is the corrected way to get Ubuntu, uShare & your xbox 360 to play nice. Once installed you should be able to stream divx video files that have the ".avi" extension to your xbox 360. 

Some folks have asked about streaming mp3 files, i have yet ti figure this out, when/if i do i will post how.

Requirements:
* ubuntu 7.10(gutsy)
* xbox 360 w/ fall 2007 update applied
* libupnp
* libdlna
* ushare 1.1 source

Update your xbox 360. By connecting to "xBox Live" it should prompt you to download the update.

Install required libs

Install the UPNP dev libs
```
sudo apt-get install libupnp-dev
```

Download and install the DLNA libs
```
wget http://www.geexbox.org/debian/pool/main/libdlna/libdlna0_0.2.3-0ubuntu1_i386.deb
sudo dpkg -i libdlna0_0.2.3-0ubuntu1_i386.deb
``` 

Download and extract uShare source
```
wget http://ushare.geexbox.org/releases/ushare-1.1.tar.bz2
tar -xvf ushare-1.1.tar.bz2
```

Edit mime.c file. This makes ushare present .avi files to the xbox as a mime type it can play
```

cd ushare-1.1/

nano src/mime.c

```

Change this line:
```
{ "avi",   UPNP_VIDEO, "http-get:*:video/x-msvideo:"},
```
to this:
```
{ "avi",   UPNP_VIDEO, "http-get:*:video/x-ms-wmv:"},
```


Now configure, make and install.

```
./configure --log --prefix=/usr --sysconfdir=/etc --disable-dlna
make
sudo make install
```

Edit the file "/etc/ushare.conf" to your liking(you need to set your content directory):
```
sudo nano /etc/ushare.conf
```

start ushare with xbox compatibility:
```
ushare -x
```

On your xbox, go to the "Media" blade, then select "Video", then press the "X" button to select your media source. The xbox should find your ushare server at this point.

hopefully this time it works! ... have fun ;)

I tried this and it worked great with only minor problem: wmv's show up on my 360 with the red circle with a cross through it, and are unplayable. My config file is very standard. and I start ushare with the standard -x option.

Any advice would be greatly appreciated.

Much thanks,
-Jai

---

### Post by Hubris2 on 2007-12-07
I'm having problems with the video being streamed to the Xbox....hopefully this is an OK place to ask.

I can play .avi files encoded with the .AC3 codec, however they are not being detected by my receiver as 5.1 audio....although they play with 5.1 on my computer, and the Xbox plays dvd discs in 5.1 just fine.

Any thoughts?

edit - I just found one that played with 5.1 - it didn't claim to use the AC3 codec.  Obviously there must be video out there that use codecs that act differently.

So, is there no way to make Ushare 1.1 play avi files using the version from the respository - you have to rebuild it from source?

---

### Post by realityisok on 2007-12-09
There is a new version of ushare available now (1.1a). The avi problem has been fixed.

[http://ushare.geexbox.org/](http://ushare.geexbox.org/)

---

### Post by notwen on 2007-12-09
> **realityisok said:**
> There is a new version of ushare available now (1.1a). The avi problem has been fixed.

[http://ushare.geexbox.org/](http://ushare.geexbox.org/)

Anyone had a opportunity to test the new version out yet?

---

### Post by tobiasgideon on 2007-12-09
> **pointfivezero said:**
> Bingo, good suggestion! It works by adding the line:

```

USHARE_OPTIONS="-x -f $CONFIGFILE"

```

below CONFIGFILE=/etc/ushare.conf


Thanks heaps

Many thanks to all people in this forum, especially **jsnwtsn** as you have all helped me and now I can happily watch AVIs on my Xbox360 from my Ubuntu box!!!!!

Many Thanks To All

Tobias

---

### Post by realityisok on 2007-12-09
> **notwen said:**
> Anyone had a opportunity to test the new version out yet?

it works great, i can see all of my divx and avi!

---

### Post by Nico0020 on 2007-12-10
Been following your guide but i'm getting a problem when i confi, make and install.  here is what happens and what the terminal spits out.

```
Checking for compiler available...
gcc is unable to create an executable file.
If gcc is a cross-compiler, use the --cross-compile option.
C compiler test failed.
See file "config.log" produced by configure for more details.
onestar@onestar-laptop:~/ushare-1.1$ make
Makefile:2: *** "config.mak is not present, run configure !".  Stop.
onestar@onestar-laptop:~/ushare-1.1$ sudo make install


```

so what is going wrong, im still new to linux so be gentle, lol.  thanks.

---

### Post by notwen on 2007-12-10
> **realityisok said:**
> it works great, i can see all of my divx and avi!

Great, looking forward to trying this new version once I get home. =]

---

### Post by pointfivezero on 2007-12-10
> **pointfivezero said:**
> Bingo, good suggestion! It works by adding the line:

```

USHARE_OPTIONS="-x -f $CONFIGFILE"

```

below CONFIGFILE=/etc/ushare.conf


Thanks heaps

I found out where my real problem was by looking at the source code. 

What the ushare.conf looks like:
```

---snip---

# Enable Web interface (yes/no)
ENABLE_WEB=

# Enable Telnet control interface (yes/no)
ENABLE_TELNET=

# Use XboX 360 compatibility mode (yes/no)
ENABLE_XBOX=

# Use DLNA profile (yes/no)
# This is needed for PlayStation3 to work (among other devices)
ENABLE_DLNA=
---snip---

```

When it should look like:

```

---snip---

# Enable Web interface (yes/no)
USHARE_ENABLE_WEB=

# Enable Telnet control interface (yes/no)
USHARE_ENABLE_TELNET=

# Use XboX 360 compatibility mode (yes/no)
USHARE_ENABLE_XBOX=

# Use DLNA profile (yes/no)
# This is needed for PlayStation3 to work (among other devices)
USHARE_ENABLE_DLNA=
---snip---

```

Which also affects the scripts/ushare file needs the line (with amendments for above fixes):

```

USHARE_OPTIONS="-f $CONFIGFILE"

```

I hope this is useful for somebody, at least I think this corrects the problem I was having.

Cheers

---

### Post by notwen on 2007-12-10
> **Nico0020 said:**
> Been following your guide but i'm getting a problem when i confi, make and install.  here is what happens and what the terminal spits out.

```
Checking for compiler available...
gcc is unable to create an executable file.
If gcc is a cross-compiler, use the --cross-compile option.
C compiler test failed.
See file "config.log" produced by configure for more details.
onestar@onestar-laptop:~/ushare-1.1$ make
Makefile:2: *** "config.mak is not present, run configure !".  Stop.
onestar@onestar-laptop:~/ushare-1.1$ sudo make install


```

so what is going wrong, im still new to linux so be gentle, lol.  thanks.

Same issue here.  Any suggestions?

---EDIT---

Try 'sudo apt-get install build-essential' to remedy this problem.  The ./configure line should work after you install the build-essential package.  Hope this helps.

---

### Post by Nico0020 on 2007-12-10
Thanks alot, that worked.  Now I followed the instructions, yet my 360 still fails to find my computer.  Though my 360 and my laptop are both running on wireless, could that have an effect on it?  Here is what the terminal says when I start up ushare.  


```

onestar@onestar-laptop:~$ ushare -x
uShare (version 1.1), a lightweight UPnP Media Server.
Benjamin Zores (C) 2005-2007, for GeeXboX Team.
See http://ushare.geexbox.org/ for updates.
Listening on telnet port 1337
Initializing UPnP subsystem ...
Starting in XboX 360 compliant profile ...
UPnP MediaServer listening on 68.94.202.178:49152
Sending UPnP advertisement for device ...
Listening for control point connections ...
Building Metadata List ...
Looking for files in content directory : /home/onestar/Torrents
Found 25 files and subdirectories.

```

any ideas this time?

---

### Post by lighty14 on 2007-12-10
I'm also having difficulties seeing my uShare on my Xbox. For reference, the web interface is accessible on my computer, and I don't have problems when sharing through Windows XP with TVersity. When I start ushare, if I have my Xbox on the Video sources list, the Computer button will change to uShare, but it is unable to connect. I'm getting no events triggered on my firewall implying it is being blocked, and no errors in uShare, even when using verbose mode. Thoughts?

** EDIT **

Here's some more details: I'm using a wired connection, my linux desktop also serves as my router, hosting DHCP for my Xbox. Here is my ushare command, with output:
```

$ ushare -x -c /media/megafiles/videos/ -i eth0 -t -w
uShare (version 1.1), a lightweight UPnP Media Server.
Benjamin Zores (C) 2005-2007, for GeeXboX Team.
See http://ushare.geexbox.org/ for updates.
Initializing UPnP subsystem ...
Starting in XboX 360 compliant profile ...
UPnP MediaServer listening on 192.168.0.1:49152
Sending UPnP advertisement for device ...
Listening for control point connections ...
Building Metadata List ...
Looking for files in content directory : /media/megafiles/videos/
Found 275 files and subdirectories.

```

My Xbox fails the "PC Connection" part of the Media Connection test.

*** EDIT 2 ***

I am lead to believe my issue is because my Ubuntu box is also my internet router. I'm going to "steal" my parent's old router and see if it resolves my issue. If it does, I'm going to email the ushare dev to see what can be done to resolve this without using an external router.

---

### Post by lighty14 on 2007-12-11
> **Nico0020 said:**
> Thanks alot, that worked.  Now I followed the instructions, yet my 360 still fails to find my computer.  Though my 360 and my laptop are both running on wireless, could that have an effect on it?  Here is what the terminal says when I start up ushare.  


```

onestar@onestar-laptop:~$ ushare -x
uShare (version 1.1), a lightweight UPnP Media Server.
Benjamin Zores (C) 2005-2007, for GeeXboX Team.
See http://ushare.geexbox.org/ for updates.
Listening on telnet port 1337
Initializing UPnP subsystem ...
Starting in XboX 360 compliant profile ...
UPnP MediaServer listening on 68.94.202.178:49152
Sending UPnP advertisement for device ...
Listening for control point connections ...
Building Metadata List ...
Looking for files in content directory : /home/onestar/Torrents
Found 25 files and subdirectories.

```

any ideas this time?

UPnP MediaServer listening on 68.94.202.178:49152

That doesn't look like the correct interface to share on, it should be on your local network, and that looks like it's sharing on your internet connection. Check to see which network interface is your local (ifconfig) and call ushare with the -i flag indicating this interface (e.g. ushare -x -i eth0).

---

### Post by soniclava on 2007-12-11
I am having an problem that sounds very close to your issue.  I am running 7.10 and the Gusty ushare 1.1 specific package.  I am able to install and run the server but my xbox can't see it 90% of the time.  The other 10% of the time I am able to see ushare under the Xbox select source menu but unable to connect.

I have verified my firewall and both IPs are on the same network. 

I am using this cmd:
ushare -c /media/sdb1/Documents\ and\ Settings/soniclava/ -x -t -w -i eth0


My server output:
> $ ushare -c /media/sdb1/Documents\ and\ Settings/soniclava/ -x -t -w -i eth0
uShare (version 1.1), a lightweight UPnP Media Server.
Benjamin Zores (C) 2005-2007, for GeeXboX Team.
See [http://ushare.geexbox.org/](http://ushare.geexbox.org/) for updates.
Initializing UPnP subsystem ...
Starting in XboX 360 compliant profile ...
UPnP MediaServer listening on 192.168.1.62:49154
Sending UPnP advertisement for device ...
Listening for control point connections ...
Building Metadata List ...
Looking for files in content directory : /media/sdb1/Documents and Settings/soniclava/
Found **** files and subdirectories.



*Note: I added the *** for files:popcorn:

Any have this issue before?

---

### Post by Nico0020 on 2007-12-11
well I changed my network device to advertise on "lo", which now that gives it a local address.  Here is what it says now.  Though my 360 still does not find my laptop though :(  My laptop is in DMZ mode so i would assume the port does not matter really correct?  Anything else I would have set wrong?

```

uShare (version 1.1), a lightweight UPnP Media Server.
Benjamin Zores (C) 2005-2007, for GeeXboX Team.
See http://ushare.geexbox.org/ for updates.
Listening on telnet port 1337
Initializing UPnP subsystem ...
Starting in XboX 360 compliant profile ...
UPnP MediaServer listening on 127.0.0.1:49152
Sending UPnP advertisement for device ...
Listening for control point connections ...
Building Metadata List ...
Looking for files in content directory : /home/onestar/Torrents
Found 25 files and subdirectories.

```

---

### Post by lighty14 on 2007-12-11
> **soniclava said:**
> I am having an problem that sounds very close to your issue.  I am running 7.10 and the Gusty ushare 1.1 specific package.  I am able to install and run the server but my xbox can't see it 90% of the time.  The other 10% of the time I am able to see ushare under the Xbox select source menu but unable to connect.

I have verified my firewall and both IPs are on the same network. 

I am using this cmd:
ushare -c /media/sdb1/Documents\ and\ Settings/soniclava/ -x -t -w -i eth0


My server output:


*Note: I added the *** for files:popcorn:

Any have this issue before?

Your issue is identical to mine. After doing some looking around, I seem to be having some sort of routing issue. My Xbox is trying to connect to 239.255.255.250 for UPnP, not sure why, and I imagine yours is doing the same. I don't know where to go from here, will let you know when I find a solution.

> **Nico0020 said:**
> well I changed my network device to advertise on "lo", which now that gives it a local address.  Here is what it says now.  Though my 360 still does not find my laptop though :(  My laptop is in DMZ mode so i would assume the port does not matter really correct?  Anything else I would have set wrong?

```

uShare (version 1.1), a lightweight UPnP Media Server.
Benjamin Zores (C) 2005-2007, for GeeXboX Team.
See http://ushare.geexbox.org/ for updates.
Listening on telnet port 1337
Initializing UPnP subsystem ...
Starting in XboX 360 compliant profile ...
UPnP MediaServer listening on 127.0.0.1:49152
Sending UPnP advertisement for device ...
Listening for control point connections ...
Building Metadata List ...
Looking for files in content directory : /home/onestar/Torrents
Found 25 files and subdirectories.

```

It shouldn't be advertising on lo. What is your networking setup? Have you ever been able to share media with your Xbox through Windows on your current network?

---

### Post by Nitro805 on 2007-12-11
I don't know if this is the right place to ask this.

I have a strange problem with my ushare (or xbox?).  When I use handbrake to encode to h.264 it makes a .mp4 file which I like.  This .mp4 file will play fine off a CD or flash-drive on the xbox360.  When I use ushare to stream it it has a red circle with a line through it and it won't play.

If I change the .mp4 to .m4v it works perfectly.  I don't really want it in .m4v because my apple will open it with itunes and add it to my itunes library (which I don't want because of the way things are organized).

Anybody else have this issue?

---

### Post by Pulshion on 2007-12-11
Does anyone know if there is a way to stream the videos using Ushare to another computer instead of xbox? Preferably windows or even putting them on net using ushare?

---

### Post by nukie77 on 2007-12-11
> **Pulshion said:**
> Does anyone know if there is a way to stream the videos using Ushare to another computer instead of xbox? Preferably windows or even putting them on net using ushare?

Why would you use Ushare to do that?  That is really more of a job for samba or ssh.

---

### Post by lighty14 on 2007-12-11
> **Nitro805 said:**
> I don't know if this is the right place to ask this.

I have a strange problem with my ushare (or xbox?).  When I use handbrake to encode to h.264 it makes a .mp4 file which I like.  This .mp4 file will play fine off a CD or flash-drive on the xbox360.  When I use ushare to stream it it has a red circle with a line through it and it won't play.

If I change the .mp4 to .m4v it works perfectly.  I don't really want it in .m4v because my apple will open it with itunes and add it to my itunes library (which I don't want because of the way things are organized).

Anybody else have this issue?

I'm not sure, but I think your issue could be resolved in a similar way to the mime-type hack people were using before.

> **Pulshion said:**
> Does anyone know if there is a way to stream the videos using Ushare to another computer instead of xbox? Preferably windows or even putting them on net using ushare?

You'd probably be better off just sharing the folder(s) using samba, which is accessible by Windows, Linux, and Mac computers on your local network. Sharing over the internet is not a good idea for a large variety of reasons, and probably wouldn't work very well with ushare as it doesn't compress or alter the bitrate.

Samba can be easily set up in Ubuntu using System->Administration->Shared Folders. The process is pretty straightforward from here. Any questions you have using it would be best addressed in the Networking forum.

---

### Post by NoiseBOX on 2007-12-11
I have still not been able to get ushare install on Feisty. here is the output

$ find /usr -name ixml.h
/usr/include/upnp/ixml.h

$ whereis libixml
libixml: /lib/libixml.so /usr/lib/libixml.so

$ ./configure
Checking for compiler available...
Checking for locales ...
Checking for ifaddrs ...
Checking for langinfo ...
Checking for iconv ...
Checking for libixml ...
Error, can't find libixml !
See file "config.log" produced by configure for more details.

configure refuses to see ixml anywhere. is there any solution to this other than upgrading to gutsy?

---

### Post by lighty14 on 2007-12-11
> **NoiseBOX said:**
> I have still not been able to get ushare install on Feisty. here is the output

$ find /usr -name ixml.h
/usr/include/upnp/ixml.h

$ whereis libixml
libixml: /lib/libixml.so /usr/lib/libixml.so

$ ./configure
Checking for compiler available...
Checking for locales ...
Checking for ifaddrs ...
Checking for langinfo ...
Checking for iconv ...
Checking for libixml ...
Error, can't find libixml !
See file "config.log" produced by configure for more details.

configure refuses to see ixml anywhere. is there any solution to this other than upgrading to gutsy?

I would try adding
```
deb http://www.geexbox.org/debian/ unstable main
```
to your /etc/apt/sources.list, followed by
```
sudo apt-get update
sudo apt-get install ushare

```
The latest version does not have the mime-type bug (the author corrected this).

---

### Post by spanning on 2007-12-11
I keep getting "500 Internal errror"! when im trying to access the web interface ... The xbox doesnt recognize ushare either. Im advertising ushare on the same subnet as the xbox (eth2) . What to do !?
Ive tried the bin package as well as the newest source. ushare is perfectly accesible via Telnet and it is binding the 49152 port (nmap) as well, but its returning this http packet:

HTTP/1.1 500 Internal Server Error
SERVER: Linux/2.6.22-14-server, UPnP/1.0, Portable SDK for UPnP devices/1.4.3
CONNECTION: close
CONTENT-LENGTH: 60
CONTENT-TYPE: text/html

<html><body><h1>500 Internal Server Error</h1></body></html>

the ushare doesnt log anything (even with the verbose flag on).

ps. Twonkymedia is working like a charm :-)

---

### Post by Squizz on 2007-12-11
I've tried installing on Gutsy 64 to no avail.

Can anyone provide a walkthrough?

Many thanks

---

### Post by Ejoc on 2007-12-11
> **spanning said:**
> I keep getting "500 Internal errror"! when im trying to access the web interface ... The xbox doesnt recognize ushare either. Im advertising ushare on the same subnet as the xbox (eth2) . What to do !?
Ive tried the bin package as well as the newest source. ushare is perfectly accesible via Telnet and it is binding the 49152 port (nmap) as well, but its returning this http packet:

HTTP/1.1 500 Internal Server Error
SERVER: Linux/2.6.22-14-server, UPnP/1.0, Portable SDK for UPnP devices/1.4.3
CONNECTION: close
CONTENT-LENGTH: 60
CONTENT-TYPE: text/html

<html><body><h1>500 Internal Server Error</h1></body></html>

the ushare doesnt log anything (even with the verbose flag on).

ps. Twonkymedia is working like a charm :-)

Are you accessing the correct URL when you go through a web browser? ie:   [http://YOURIP:49152/web/ushare.html](http://YOURIP:49152/web/ushare.html)
I know that if you go to just YOURIP:49152 you will get the Internal Server Error message.

---

### Post by M0nk3Ee on 2007-12-11
> **NoiseBOX said:**
> I have still not been able to get ushare install on Feisty. here is the output

$ find /usr -name ixml.h
/usr/include/upnp/ixml.h

$ whereis libixml
libixml: /lib/libixml.so /usr/lib/libixml.so

$ ./configure
Checking for compiler available...
Checking for locales ...
Checking for ifaddrs ...
Checking for langinfo ...
Checking for iconv ...
Checking for libixml ...
Error, can't find libixml !
See file "config.log" produced by configure for more details.

configure refuses to see ixml anywhere. is there any solution to this other than upgrading to gutsy?

I am having exactly the same problem on Fiesty....

Checking for compiler available...
Checking for locales ...
Checking for ifaddrs ...
Checking for langinfo ...
Checking for iconv ...
Checking for libixml ...
Error, can't find libixml !
See file "config.log" produced by configure for more details.

:/opt/ushare-1.1a$ find /usr -name ixml.h
/usr/include/upnp/ixml.h

:/opt/ushare-1.1a$ whereis libixml
libixml: /usr/lib/libixml.so

I managed to get the old version installed but then realised it didn't have the -x parameter which i  means that it wont work with the xbox 360.  Would be great if anyone has any ideas......

---

### Post by M0nk3Ee on 2007-12-11
> **lighty14 said:**
> I would try adding
```
deb http://www.geexbox.org/debian/ unstable main
```
to your /etc/apt/sources.list, followed by
```
sudo apt-get update
sudo apt-get install ushare

```
The latest version does not have the mime-type bug (the author corrected this).

When i try adding the repo you mention i get the following.....

/opt/ushare-1.1a$ sudo apt-get install ushare
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  ushare: Depends: libavcodec1d (>= 0.cvs20070307) but it is not installable
          Depends: libavformat1d (>= 0.cvs20070307) but it is not installable
          Depends: libavutil1d (>= 0.cvs20070307) but it is not installable
          Depends: libc6 (>= 2.6-1) but 2.5-0ubuntu14 is to be installed
          Depends: libdlna0 but it is not going to be installed
          Depends: libupnp2 but it is not installable
E: Broken packages

I guess it is because i am using fiesty and not gutsy.

---

### Post by blueorder on 2007-12-11
> **M0nk3Ee said:**
> When i try adding the repo you mention i get the following.....

/opt/ushare-1.1a$ sudo apt-get install ushare
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  ushare: Depends: libavcodec1d (>= 0.cvs20070307) but it is not installable
          Depends: libavformat1d (>= 0.cvs20070307) but it is not installable
          Depends: libavutil1d (>= 0.cvs20070307) but it is not installable
          Depends: libc6 (>= 2.6-1) but 2.5-0ubuntu14 is to be installed
          Depends: libdlna0 but it is not going to be installed
          Depends: libupnp2 but it is not installable
E: Broken packages

I guess it is because i am using fiesty and not gutsy.

I had the same issue when I tried installing through that repo.

I am on Feisty also and upgrading to Gutsy is not really an option.

---

### Post by eon123 on 2007-12-11
Hi,
Still getting to grips with Ubuntu, though going well except this issue has me baffled.  I've followed the updated how-to on this thread to install and config uShare for streaming to xbox360, but I'm getting the following interface adaptor error on start-up: -

------------<snip>------------------
<username>:~$ ushare -x
Interface eth0 is down.
Recheck uShare's configuration and try again !
uShare (version 1.1a), a lightweight UPnP A/V and DLNA Media Server.
Benjamin Zores (C) 2005-2007, for GeeXboX Team.
See [http://ushare.geexbox.org/](http://ushare.geexbox.org/) for updates.
Listening on telnet port 1337
Initializing UPnP subsystem ...
Starting in XboX 360 compliant profile ...
UPnP MediaServer listening on 192.168.0.3:49152
Sending UPnP advertisement for device ...
Listening for control point connections ...
Building Metadata List ...
Looking for files in content directory : /media/USB-HDD/Video/Video_Store
Found 4 files and subdirectories.
Building Metadata List ...
Looking for files in content directory : /media/USB-HDD/Video/Video_Store
Found 4 files and subdirectories.
------------<snip>------------------

Thing is, it's a wired connection to a router, which is all fully functioning (i.e. pingig across the LAN and WAN, valid IP etc.)

I've returned the two ushare config files back to default, but still no luck.  Any ideas anyone as there nothing on the netabout this particular error in uShare?

Cheers.

---

### Post by Nico0020 on 2007-12-11
I used to share using windows media center, but it was using internet connection sharing before I ahad the 360 wireless adapter.  I use a 2wire modem, which also is my router.  both my 360 and my laptop are on wireless. 

> 
It shouldn't be advertising on lo. What is your networking setup? Have you ever been able to share media with your Xbox through Windows on your current network?

---

### Post by Hubris2 on 2007-12-11
I've installed from the Geexbox repository, and I'm only running version 1.1 - not the version 1.1a which includes the mime update.  My Xbox still can't play .avi files until I rename them to something compatible.

Are you sure the author has updated the repository, or have you installed it from source and are assuming it's updated?

---

### Post by pointfivezero on 2007-12-12
> **M0nk3Ee said:**
> I am having exactly the same problem on Fiesty....

Checking for compiler available...
Checking for locales ...
Checking for ifaddrs ...
Checking for langinfo ...
Checking for iconv ...
Checking for libixml ...
Error, can't find libixml !
See file "config.log" produced by configure for more details.

:/opt/ushare-1.1a$ find /usr -name ixml.h
/usr/include/upnp/ixml.h

:/opt/ushare-1.1a$ whereis libixml
libixml: /usr/lib/libixml.so

I managed to get the old version installed but then realised it didn't have the -x parameter which i  means that it wont work with the xbox 360.  Would be great if anyone has any ideas......

Hmm, looks different from gutsy if that matters.

```

whereis libixml
libixml: /usr/lib/libixml.so /usr/lib/libixml.la /usr/lib/libixml.a

```

:(

---

### Post by pointfivezero on 2007-12-12
> **eon123 said:**
> Hi,
Still getting to grips with Ubuntu, though going well except this issue has me baffled.  I've followed the updated how-to on this thread to install and config uShare for streaming to xbox360, but I'm getting the following interface adaptor error on start-up: -

------------<snip>------------------
<username>:~$ ushare -x
Interface eth0 is down.
...


Could you please check to be sure that you have the correct network interface (might be something other that eth0) - if you are unsure, send your ifconfig.

---

### Post by spanning on 2007-12-12
> **Ejoc said:**
> Are you accessing the correct URL when you go through a web browser? ie:   [http://YOURIP:49152/web/ushare.html](http://YOURIP:49152/web/ushare.html)
I know that if you go to just YOURIP:49152 you will get the Internal Server Error message.

AHH!  me stupid .. very stupid ... now I can access the web interface ... so ushare seems to be up and running ok .. now I just need the xbox to recognize it :-) thanks for the enlightenment !

cheers
søren

---

### Post by spanning on 2007-12-12
> **eon123 said:**
> Hi,
Still getting to grips with Ubuntu, though going well except this issue has me baffled.  I've followed the updated how-to on this thread to install and config uShare for streaming to xbox360, but I'm getting the following interface adaptor error on start-up: -

------------<snip>------------------
<username>:~$ ushare -x
Interface eth0 is down.
Recheck uShare's configuration and try again !
----


Did you compile it from the src package yourself!? had the same problem and I stumbled upon some oddity in the code (ushare.c) when using the ifaddrs library. The following condition doesnt make sense (to me after all)


(ushare.c - l.461)
if (itf->ifa_flags & IFF_UP) && !strncmp (itf->ifa_name, interface, IFNAMSIZ))
    ... print "interface ... is down."
   return true; <---- 
...
return false;


this condition has to be true orelse the function (has_iface) will return false and ushare will stop ... so "interface ethX is down." is actually (as i see it) a good sign and will keep ushare running!? ... maybe the author could comment on this!

søren

---

### Post by SoerenV on 2007-12-12
I get the same error as M0nk3Ee and Blueorder. Does anyone know how to solve this please?

---

### Post by crasian on 2007-12-12
I have everything installed and ready to go but my problem is that EVERYTHING is not sort out right.  My music and video are all jumbled together in the same directory (it didn't before) and my music is not listed in albums anymore.

Is there something I'm suppose to set up to see everything in their right directory (like videos in the video blade and music in music blad).  Everything is all thrown in to videos.

---

### Post by theelk801 on 2007-12-12
It worked great for a while and now when I start it it sats "Error: no content directory to be shared"
It was fine before, and now it just stopped. Also I have to rename all of my files to wmv from avi.

---

### Post by Hubris2 on 2007-12-12
The renaming issue will go away when you get version 1.1a - it has the mime types updated.  I don't believe the Geekbox repository has been updated....I know I have to rename my .avi as well.

---

### Post by belboz on 2007-12-12
You can edit that mime file to fix it.  Ushare is setup to share mp4 as audio files.  You can take the line out associating it with an audio format and add a line associating mp4 as a video format and it should work fine. 

> **Nitro805 said:**
> I don't know if this is the right place to ask this.

I have a strange problem with my ushare (or xbox?).  When I use handbrake to encode to h.264 it makes a .mp4 file which I like.  This .mp4 file will play fine off a CD or flash-drive on the xbox360.  When I use ushare to stream it it has a red circle with a line through it and it won't play.

If I change the .mp4 to .m4v it works perfectly.  I don't really want it in .m4v because my apple will open it with itunes and add it to my itunes library (which I don't want because of the way things are organized).

Anybody else have this issue?

---

### Post by wilbur d on 2007-12-13
> **crasian said:**
> I have everything installed and ready to go but my problem is that EVERYTHING is not sort out right.  My music and video are all jumbled together in the same directory (it didn't before) and my music is not listed in albums anymore.

Is there something I'm suppose to set up to see everything in their right directory (like videos in the video blade and music in music blad).  Everything is all thrown in to videos.

i'm having the same problem. everything seems to work fine but nothing is being "sorted"

my mp3's show up in the video blade and vice versa. also in the music blade it shows every song under all categories. ie. every song shows up under albums instead of listing by album. if i go to genre it shows every song as well. 

anyone have an idea what might cause this? i'm running ushare 1.1a and gutsy

---

### Post by eon123 on 2007-12-13
> **pointfivezero said:**
> Could you please check to be sure that you have the correct network interface (might be something other that eth0) - if you are unsure, send your ifconfig.

Yep, one network adaptor and the loopback...

----------<snip>---------------
:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:40:--:--:--:--  
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7389 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4765 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3513000 (3.3 MB)  TX bytes:642699 (627.6 KB)
          Interrupt:11 Base address:0xe800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:175 errors:0 dropped:0 overruns:0 frame:0
          TX packets:175 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:16756 (16.3 KB)  TX bytes:16756 (16.3 KB)
----------<snip>---------------


> **spanning said:**
> Did you compile it from the src package yourself!? had the same problem and I stumbled upon some oddity in the code (ushare.c) when using the ifaddrs library. The following condition doesnt make sense (to me after all)


(ushare.c - l.461)
if (itf->ifa_flags & IFF_UP) && !strncmp (itf->ifa_name, interface, IFNAMSIZ))
    ... print "interface ... is down."
   return true; <---- 
...
return false;


this condition has to be true orelse the function (has_iface) will return false and ushare will stop ... so "interface ethX is down." is actually (as i see it) a good sign and will keep ushare running!? ... maybe the author could comment on this!

søren

I just followed **jsnwtsn's** how-to on post #48.  You lost me with the coding, but hopefully someone can help. Thanks.

---

### Post by Hubris2 on 2007-12-14
I just pulled down version 1.1a from the repository as an update....so you should all have the mime-type issue dealt with shortly.

---

### Post by theelk801 on 2007-12-15
It works perfectly now. I couldn't be happier!

---

### Post by DumberDrummer on 2007-12-15
theelk:

what did you do to fix it?

---

### Post by theelk801 on 2007-12-16
When I started it, I typed: ```
-x -c /insert-video-directory-here
```

---

### Post by kexodusc on 2007-12-19
> **wilbur d said:**
> i'm having the same problem. everything seems to work fine but nothing is being "sorted"

my mp3's show up in the video blade and vice versa. also in the music blade it shows every song under all categories. ie. every song shows up under albums instead of listing by album. if i go to genre it shows every song as well. 

anyone have an idea what might cause this? i'm running ushare 1.1a and gutsy

Count me as the 3rd having this problem.  Weird thing is the video menu sorts everything by folder like I might expect, but the music blade just has one huge list of everything being shared, no sorting of any type. 
Would love to hear of a fix for this if there is one.

---

### Post by Squizz on 2007-12-19
Is there an alternative for amd64 users?

I've only tried via the HOWTO earlier in this thread but thats i386.

Many thanks.

---

### Post by Squizz on 2007-12-19
I get as far as

```

simon@gutsy64si:~/Desktop/ushare-1.1$ ./configure --log --prefix=/usr --sysconfdir=/etc --disable-dlna
Checking for compiler available...
Checking for locales ...
Checking for langinfo ...
Checking for iconv ...
Checking for libixml ...
Error, can't find libixml !
See file "config.log" produced by configure for more details.

```

So I installed from

[http://http.us.debian.org/debian/pool/main/libu/libupnp/libupnp0_1.2.1-2_amd64.deb](http://http.us.debian.org/debian/pool/main/libu/libupnp/libupnp0_1.2.1-2_amd64.deb)
[http://mirrors.kernel.org/ubuntu/pool/universe/libu/libupnp/libupnp-dev_1.2.1-2_amd64.deb](http://mirrors.kernel.org/ubuntu/pool/universe/libu/libupnp/libupnp-dev_1.2.1-2_amd64.deb)

and it still gives the same error, even though

```

simon@gutsy64si:~/Desktop/ushare-1.1$ whereis libixml
libixml: /usr/lib/libixml.so /usr/lib64/libixml.so

```

---

### Post by SyntheticXTC on 2007-12-19
Yes TwonkyVision does work great (in windows)...I haven't tried in my linux box yet. Now that I know that it works with ubuntu I will have to give it a shot.  If I remember correctly it was $30.   Winamp Remote is free but I doubt we will see a linux port any time soon. :(

---

### Post by kexodusc on 2007-12-19
> **Squizz said:**
> Is there an alternative for amd64 users?

I've only tried via the HOWTO earlier in this thread but thats i386.

Many thanks.

I just added:
deb [http://www.geexbox.org/debian/](http://www.geexbox.org/debian/) unstable main
to my /etc/apt/sources.list

and then installed it with apt-get.
Works for me other than the messed up menus...

---

### Post by Swordcast on 2007-12-20
Fix for libxml or libupnp configuration error for Ushare.

More than likely, pkg-config cannot find the libupnp or the libxml?(whatever it is :P) configuration files for pkg-config.  What you need to do is type this:

export PKG_CONFIG_PATH=/usr/local/lib/pkgconfig

then execute this:

pkg-config --libs --cflags libupnp

If you get directories of where it's at, then you're good.  If not, search for the libupnp.pc file and tell PKG to look in that directory.  Anyways, after you export the PKG_CONFIG_PATH, try recompiling ushare, and it should work for you.

---

### Post by blueorder on 2007-12-20
> **Swordcast said:**
> Fix for libxml or libupnp configuration error for Ushare.

More than likely, pkg-config cannot find the libupnp or the libxml?(whatever it is :P) configuration files for pkg-config.  What you need to do is type this:

export PKG_CONFIG_PATH=/usr/local/lib/pkgconfig

then execute this:

pkg-config --libs --cflags libupnp

If you get directories of where it's at, then you're good.  If not, search for the libupnp.pc file and tell PKG to look in that directory.  Anyways, after you export the PKG_CONFIG_PATH, try recompiling ushare, and it should work for you.

I tried doing this but the Feisty libupnp-dev package does not have a libupnp.pc. I looked in [http://packages.ubuntu.com](http://packages.ubuntu.com) at the files libupnp-dev and libupnp0 install and neither installs libupnp.pc

---

### Post by blueorder on 2007-12-21
I got it to compile on **Feisty**.

I stopped messing with libupnp from the repository and compiled [libupnp 1.6.2]("http://pupnp.sourceforge.net/") from SourceForge

```
tar jxvf libupnp-1.6.2.tar.bz2
cd libupnp-1.6.2/
./configure --prefix=/usr
make
sudo make install

```

Downloaded [ushare 1.1a]("http://ushare.geexbox.org/") and compiled it:

```
tar jxvf ushare-1.1a.tar.bz2
cd ushare-1.1a/
./configure --prefix=/usr
make
sudo checkinstall

```

And then ran it with this:

```
ushare -n servname -p 49153 -c /dir/to/share/ -x
```

It seems to be working as I can play avi, mp3 and wmv on my 360.

Again, this was on **Feisty**.

---

### Post by onehotcutey on 2007-12-21
> **kexodusc said:**
> Count me as the 3rd having this problem.  Weird thing is the video menu sorts everything by folder like I might expect, but the music blade just has one huge list of everything being shared, no sorting of any type. 
Would love to hear of a fix for this if there is one.

I'm a fourth.  With this problem (all music files being listed in one huge list).  

Running 1.1a - 

Videos - work great
Pictures - work great
Music - Not being sorted properly and won't play.

---

### Post by Swordcast on 2007-12-21
> **blueorder said:**
> I tried doing this but the Feisty libupnp-dev package does not have a libupnp.pc. I looked in [http://packages.ubuntu.com](http://packages.ubuntu.com) at the files libupnp-dev and libupnp0 install and neither installs libupnp.pc

Download the source and compile it.  Libupnp.sourceforge.net I believe.  Download the file, unzip/tar it.

Goto the shell, and type this in:

cd /path/to/libupnp
su
./configure
make
make install

This will install the libraries in /usr/local/lib folder.  pkgconfig should be at /usr/local/lib/pkgconfig and that's where they put the libupnp.pc file.

---

### Post by circuitjump on 2007-12-22
Okay TwonkyMedia works perfect out of the box. I was messing with uShare but honestly for this type of thing, I'd rather dish out a few bucks so I can get back to the more important parts of Geekin! 

Anyway, thank you Edwardandtubs for the reference. Great app and well worth the price.

---

### Post by niiiick on 2007-12-29
no mp3s show up in my media tab, and all the movies show up under movies and music.

this is my config file; i run with with simply "ushare"

```
# /etc/ushare.conf
# Edit this file with 'dpkg-reconfigure ushare'
# Configuration file for uShare

# uShare UPnP Friendly Name (default is 'uShare').
USHARE_NAME=uShare

# Interface to listen to (default is eth0).
# Ex : USHARE_IFACE=eth1
USHARE_IFACE=eth1

# Port to listen to (default is random from IANA Dynamic Ports range)
# Ex : USHARE_PORT=49200
USHARE_PORT=

# Port to listen for Telnet connections
# Ex : USHARE_TELNET_PORT=1337
#USHARE_TELNET_PORT=

# Directories to be shared (space or CSV list).
# Ex: USHARE_DIR=/dir1,/dir2
USHARE_DIR=/home/nick/Videos,/home/nick/Music

# Use to override what happens when iconv fails to parse a file name.
# The default uShare behaviour is to not add the entry in the media list
# This option overrides that behaviour and adds the non-iconv'ed string into
# the media list, with the assumption that the renderer will be able to
# handle it. Devices like Noxon 2 have no problem with strings being passed
# as is. (Umlauts for all!)
#
# Options are TRUE/YES/1 for override and anything else for default behaviour
#USHARE_OVERRIDE_ICONV_ERR=

# Enable Web interface (yes/no)
#USHARE_ENABLE_WEB=

# Enable Telnet control interface (yes/no)
#USHARE_ENABLE_TELNET=

# Use XboX 360 compatibility mode (yes/no)
USHARE_ENABLE_XBOX=yes

# Use DLNA profile (yes/no)
# This is needed for PlayStation3 to work (among other devices)
#USHARE_ENABLE_DLNA=
```

and this is what i get when i run ushare -v

```
Interface eth1 is down.
Recheck uShare's configuration and try again !
uShare (version 1.1a), a lightweight UPnP A/V and DLNA Media Server.
Benjamin Zores (C) 2005-2007, for GeeXboX Team.
See http://ushare.geexbox.org/ for updates.
Listening on telnet port 1337
Initializing UPnP subsystem ...
Starting in XboX 360 compliant profile ...
UPnP MediaServer listening on 192.168.1.111:49152
Sending UPnP advertisement for device ...
Listening for control point connections ...
Building Metadata List ...
Looking for files in content directory : /home/nick/Videos
----------then it lists everything i have in those folders...
***************************************************
**             New Action Request                **
***************************************************
ServiceID: urn:microsoft.com:serviceId:X_MS_MediaReceiverRegistrar
ActionName: IsAuthorized
CtrlPtIP: 192.168.1.103
Action Request:
<?xml version="1.0"?>
<u:IsAuthorized xmlns:u="urn:microsoft.com:service:X_MS_MediaReceiverRegistrar:1">
<DeviceID></DeviceID>
</u:IsAuthorized>

Action Result:
<?xml version="1.0"?>
<u:IsAuthorizedResponse xmlns:u="urn:microsoft.com:service:X_MS_MediaReceiverRegistrar:1">
<Result>1</Result>
</u:IsAuthorizedResponse>
***************************************************

***************************************************
**             New Action Request                **
***************************************************
ServiceID: urn:microsoft.com:serviceId:X_MS_MediaReceiverRegistrar
ActionName: IsValidated
CtrlPtIP: 192.168.1.103
Action Request:
<?xml version="1.0"?>
<u:IsValidated xmlns:u="urn:microsoft.com:service:X_MS_MediaReceiverRegistrar:1">
<DeviceID></DeviceID>
</u:IsValidated>

Action Result:
<?xml version="1.0"?>
<u:IsValidatedResponse xmlns:u="urn:microsoft.com:service:X_MS_MediaReceiverRegistrar:1">
<Result>1</Result>
</u:IsValidatedResponse>
***************************************************

```

i know it says "interface eth1 is down" but it's not and it still connects, so i ignored that...

---

### Post by Mitch on 2007-12-29
For me, I've got uShare working (1.1 on Gutsy).  However, only 50 mp3's show up on the xbox (out of about 700 recognized by uShare).  Also I have weird problems where sometimes the music won't progress onto the next song.  I'd love to find a way to have all of my mp3's show up.

---

### Post by antoniuk on 2007-12-30
If I am going to pay $40 just to hook up to my xbox360, I would rather pay an extra $60 and get Vista. 

Are there any alternatives aside form ushare that work? I am not about to pay $40 just to hear music on my xbox

---

### Post by soniclava on 2008-01-03
I am also having a issue with ushare not seeing my eth0 interface.  

> ~$ ushare -c /media/sdb1/Documents\ and\ Settings/soniclava/ -x
Interface eth0 is down.
Recheck uShare's configuration and try again !
uShare (version 1.1a), a lightweight UPnP A/V and DLNA Media Server.
Benjamin Zores (C) 2005-2007, for GeeXboX Team.
See [http://ushare.geexbox.org/](http://ushare.geexbox.org/) for updates.
Listening on telnet port 1337
Initializing UPnP subsystem ...
Starting in XboX 360 compliant profile ...
UPnP MediaServer listening on 192.168.1.62:49152
Sending UPnP advertisement for device ...
Listening for control point connections ...
Building Metadata List ...
Looking for files in content directory : /media/sdb1/Documents and Settings/soniclava/
Found 39334 files and subdirectories.


I know its up and working.
> ~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:50:8D:7D:7F:51  
          inet addr:192.168.1.62  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::250:8dff:fe7d:7f51/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:792246 errors:0 dropped:0 overruns:0 frame:0
          TX packets:665391 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:840066585 (801.1 MB)  TX bytes:211775531 (201.9 MB)
          Interrupt:19 Base address:0xc000 

My xbox can see ushare from the select source menu but when I try selecting ushare it gives me an error saying it could be behind a firewall.  Port 14592 is open and listening.

I have read that some people closed other programs that were using the ushare port and it worked.  I have closed all my programs besides ushare and still having the issue.  Has anyone resolved the eth0 error?

---

### Post by Rainz3 on 2008-01-04
I was able to install ushare properly without a hitch using the guide in I belive post 48 but when I go to start ushare using ushare -x I get

```
jeremy@Desktop:~$ ushare -x
Interface wlan0 is down.
Recheck uShare's configuration and try again !
uShare (version 1.1a), a lightweight UPnP A/V and DLNA Media Server.
Benjamin Zores (C) 2005-2007, for GeeXboX Team.
See http://ushare.geexbox.org/ for updates.
bind: Address already in use

```

wlan0 is up and working as thats how I am posting this right now.

my ifconfig is as follows

```
jeremy@Desktop:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:66 errors:0 dropped:0 overruns:0 frame:0
          TX packets:66 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:20394 (19.9 KB)  TX bytes:20394 (19.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:06:F4:0C:14:77  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::206:f4ff:fe0c:1477/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15800 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11023 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:15659672 (14.9 MB)  TX bytes:1465306 (1.3 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-06-F4-0C-14-77-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

and my config file is


```

# /etc/ushare.conf
# Edit this file with 'dpkg-reconfigure ushare'
# Configuration file for uShare

# uShare UPnP Friendly Name (default is 'uShare').
USHARE_NAME=uShare

# Interface to listen to (default is eth0).
# Ex : USHARE_IFACE=eth1
USHARE_IFACE=wlan0

# Port to listen to (default is random from IANA Dynamic Ports range)
# Ex : USHARE_PORT=49200
USHARE_PORT=

# Port to listen for Telnet connections
# Ex : USHARE_TELNET_PORT=1337
#USHARE_TELNET_PORT=

# Directories to be shared (space or CSV list).
# Ex: USHARE_DIR=/dir1,/dir2
USHARE_DIR=/home/nick/Videos,/home/nick/Music

# Use to override what happens when iconv fails to parse a file name.
# The default uShare behaviour is to not add the entry in the media list
# This option overrides that behaviour and adds the non-iconv'ed string into
# the media list, with the assumption that the renderer will be able to
# handle it. Devices like Noxon 2 have no problem with strings being passed
# as is. (Umlauts for all!)
# 
# Options are TRUE/YES/1 for override and anything else for default behaviour
#USHARE_OVERRIDE_ICONV_ERR=

# Enable Web interface (yes/no)
#USHARE_ENABLE_WEB=
# Enable Telnet control interface (yes/no)
#USHARE_ENABLE_TELNET=

# Use XboX 360 compatibility mode (yes/no)
USHARE_ENABLE_XBOX=yes

# Use DLNA profile (yes/no)
# This is needed for PlayStation3 to work (among other devices)
#USHARE_ENABLE_DLNA=

```


Any clues hints or tips?

---

### Post by jmadero on 2008-01-05
A fifth with the music issue, has anyone reported a bug to the ushare developers? I love the program as a whole, videos stream nicely and music work but the way they are divided between categories (music, video, pictures) is an issue. I also have realized that mine maxes at 1000 songs despite me having about 3000. One suggestion that I have come up with and seems to work is to share video only through ushare and to use one of the other programs that you can share music with (I believe amarok and a few others you can), this way videos are shared through ushare and music doesn't get mixed up.

---

### Post by ahh_dee on 2008-01-24
I am having the same problem with USHARE not saying that my eth1 or eth0 is down.  Does anyone have a fix on that ?

---

### Post by StubbsPKS on 2008-01-28
I just installed TwonkyVision, but I've heard the trial doesn't actually expire :-P

---

### Post by Flupke on 2008-02-08
uShare looks like a dead project to me, source taken from their repository wont even compile (API mismatch between libdlna and ushare, despite the fact both belong to the same project), it did not work at all with my ps3 and seemed to offer no other way to fix the problem but rewrite the code myself. Also I was unable to find a mailing list or bug tracker on their site ...

[Fuppes](http://fuppes.ulrich-voelkel.de/) worked out of the box and offers just what I need, has a comprehensive documentation and looks like a real project. Although I was not able to test it also seems to support [the 360](http://fuppes.ulrich-voelkel.de/wiki/index.php/Microsoft_Xbox_360). My advice is to give up on ushare and use Fuppes, unless you want to pay and go for TwonkyVision :) (but if you really do give money to fuppes' developper, just because he did not ask in the first place :P )

---

### Post by Hubris2 on 2008-02-09
Funny.....I was just thinking of posting on the TVersity forums that their port to Linux seems to be dead because Ushare and other applications works so well.  I haven't compiled from source, so I can't comment there - but the repository versions work pretty well.  Only complaint is the organization on music....but for videos it's great.

---

### Post by WebBuddha on 2008-02-09
hi there,

so I've tried ushare also, but the the xbox compatibility wasn't listed when i'm starting ushare and my xbox360 can't find my PC.

> Interface eth1 ist down.
Überprüfe uShare's Konfiguration und versuche es erneut!
uShare (version 1.1a), a lightweight UPnP A/V and DLNA Media Server.
Benjamin Zores (C) 2005-2007, für das GeeXboX Team.
Für Updates gehe auf [http://ushare.geexbox.org/](http://ushare.geexbox.org/).
Listening on telnet port 1337
Initialisiere UPnP Subsystem ...
UPnP MediaServer lauscht auf 192.168.1.10:49152
Sende UpnP Advertisement für Gerät...
Lausche auf Control Point Verbindungen...
Building Metadata List ...
Looking for files in content directory : /media/NEU/Video/AAO
Found 13 files and subdirectories.

my config file looks:
> # /etc/ushare.conf
# Edit this file with 'dpkg-reconfigure ushare'
# Configuration file for uShare

# uShare UPnP Friendly Name (default is 'uShare').
USHARE_NAME=uShare

# Interface to listen to (default is eth0).
# Ex : USHARE_IFACE=eth1
USHARE_IFACE=eth1

# Port to listen to (default is random from IANA Dynamic Ports range)
# Ex : USHARE_PORT=49200
USHARE_PORT=

# Port to listen for Telnet connections
# Ex : USHARE_TELNET_PORT=1337
USHARE_TELNET_PORT=

# Directories to be shared (space or CSV list).
# Ex: USHARE_DIR=/dir1,/dir2
USHARE_DIR=/media/NEU/Video/AAO

# Use to override what happens when iconv fails to parse a file name.
# The default uShare behaviour is to not add the entry in the media list
# This option overrides that behaviour and adds the non-iconv'ed string into
# the media list, with the assumption that the renderer will be able to
# handle it. Devices like Noxon 2 have no problem with strings being passed
# as is. (Umlauts for all!)
#
# Options are TRUE/YES/1 for override and anything else for default behaviour
USHARE_OVERRIDE_ICONV_ERR=

# Enable Web interface (yes/no)
ENABLE_WEB=

# Enable Telnet control interface (yes/no)
ENABLE_TELNET=

# Use XboX 360 compatibility mode (yes/no)
ENABLE_XBOX=yes

# Use DLNA profile (yes/no)
# This is needed for PlayStation3 to work (among other devices)
ENABLE_DLNA=

where is the mistake on this?

Greetz
WebBuddha

---

### Post by Hubris2 on 2008-02-09
I'm not sure if the "xbox compatibility" setting works.....you can actually pass ushare the command-line parameter -x and it will start in the correct mode.  How did you install it....does it run automatically, or do you execute it manually when you want it?

---

### Post by WebBuddha on 2008-02-09
I've installed the deb package from [http://ushare.geexbox.org/#Download](http://ushare.geexbox.org/#Download) and I'm starting the script manually if needed.

---

### Post by WebBuddha on 2008-02-09
I've tried it now with the parameter -x and that's working for me. very strange that this will not work out of the config file. thanks a lot

---

### Post by drazmo on 2008-02-16
I had the same problem...I noticed that in the ushare.conf the default setting is "ENABLE_XBOX=yes"  but it should be "USHARE_ENABLE_XBOX=yes"  then it started working without -x in the command line using the settings in the ushare.conf file.

---

### Post by dopplerdeffect on 2008-02-21
For anybody that can play the .avi's and other video files but cannot get .mp3's to work, perhaps you are doing what I did and are trying to play them as albums. Ushare seems to share all your files in every catagory. One mp3 will show up as an album, an artist, a playlist and finally a song. When picking the mp3, just scroll down to "song" and choose your file there.

---

### Post by kronictokr on 2008-03-14
anyone find anything yet
?

---

### Post by szandor on 2008-03-16
i can get all files to play and if i convert a vob to another container it plays fine. avi, mpg, etc. is there something special that needs to be done for vob files? ushare/xbox doesn't need the ifo or bup files does it?

---

### Post by kronictokr on 2008-03-16
the 360 plays h.264 so why convert them?  i had it sharing with xp before, and wmp11 wasnt even on half the time and couldnt read the h.264 files(even read 0data in file) but the 360 played it seemless. the xbox360 only needs a path to access the file.  now i have to re learn this in linux.  ....

---

### Post by chanman on 2008-03-16
> **WebBuddha said:**
> 
```

# Enable Web interface (yes/no)
ENABLE_WEB=

# Enable Telnet control interface (yes/no)
ENABLE_TELNET=

# Use XboX 360 compatibility mode (yes/no)
ENABLE_XBOX=yes

# Use DLNA profile (yes/no)
# This is needed for PlayStation3 to work (among other devices)
ENABLE_DLNA=

```

where is the mistake on this?

Greetz
WebBuddha

The mistake is that the repo's config file is wrong.
it should be:
```

# Enable Web interface (yes/no)
USHARE_ENABLE_WEB=
USHARE_ENABLE_TELNET=
USHARE_ENABLE_XBOX=
USHARE_ENABLE_DLNA=

```

---

### Post by denisesballs on 2008-03-24
Has anyone refined how files are displayed? All my movies and music shows up for both Videos and Music and the Music tags are not read at all.

---

### Post by homeofpoe on 2008-04-12
I tried the above, and even tried compiling from source, and I'm just not having any luck. I can see the uShare web from my computer, but my x360 has absolutely no recognition of the uShare.

I use Firestarter to grant the x360 access through my laptop's wireless (I run an ethernet cable from the x360 to the computer, which works fine).

this is what I get from a "ushare -x"
```
homeofpoe@home:~/ushare-1.1a$ ushare -x
Interface eth0 is down.
Recheck uShare's configuration and try again !
uShare (version 1.1a), a lightweight UPnP A/V and DLNA Media Server.
Benjamin Zores (C) 2005-2007, for GeeXboX Team.
See http://ushare.geexbox.org/ for updates.
Listening on telnet port 1337
Initializing UPnP subsystem ...
Starting in XboX 360 compliant profile ...
UPnP MediaServer listening on 192.168.2.1:49152
Sending UPnP advertisement for device ...
Listening for control point connections ...
Building Metadata List ...
Looking for files in content directory : /home/homeofpoe/videos/
Found 152 files and subdirectories.

```

My ifconfig of eth0:
```
eth0      Link encap:Ethernet  HWaddr 00:15:C5:76:D0:8A  
          inet addr:192.168.2.1  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::215:c5ff:fe76:d08a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:479254 errors:0 dropped:0 overruns:0 frame:0
          TX packets:914677 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:31605092 (30.1 MB)  TX bytes:1249056325 (1.1 GB)
          Interrupt:17 

```

and finally, the ushare.conf (basically the stock):
```

# /etc/ushare.conf
# Configuration file for uShare

# uShare UPnP Friendly Name (default is 'uShare').
USHARE_NAME=

# Interface to listen to (default is eth0).
# Ex : USHARE_IFACE=eth1
USHARE_IFACE=eth0

# Port to listen to (default is random from IANA Dynamic Ports range)
# Ex : USHARE_PORT=49200
USHARE_PORT=

# Port to listen for Telnet connections
# Ex : USHARE_TELNET_PORT=1337
USHARE_TELNET_PORT=

# Directories to be shared (space or CSV list).
# Ex: USHARE_DIR=/dir1,/dir2
USHARE_DIR=/home/homeofpoe/videos/

# Use to override what happens when iconv fails to parse a file name.
# The default uShare behaviour is to not add the entry in the media list
# This option overrides that behaviour and adds the non-iconv'ed string into
# the media list, with the assumption that the renderer will be able to
# handle it. Devices like Noxon 2 have no problem with strings being passed
# as is. (Umlauts for all!)
#
# Options are TRUE/YES/1 for override and anything else for default behaviour
USHARE_OVERRIDE_ICONV_ERR=

# Enable Web interface (yes/no)
ENABLE_WEB=

# Enable Telnet control interface (yes/no)
ENABLE_TELNET=

# Use XboX 360 compatibility mode (yes/no)
USHARE_ENABLE_XBOX=yes

# Use DLNA profile (yes/no)
# This is needed for PlayStation3 to work (among other devices)
ENABLE_DLNA=

```

Not sure what else could be causing this. I couldn't get the "route add" command to work - would that be the reason why? (I'm unsure just how to use it).  I can see it from my computer fine, though. Is there a way to set what the x360 looks for?

Thanks in advance for the help!

---

### Post by homeofpoe on 2008-04-13
I used the route command, didn't seem to do anything other than a duplicate:

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     *               255.255.255.0   U     0      0        0 eth0
192.168.2.0     *               255.255.255.0   U     0      0        0 eth0
192.168.1.0     *               255.255.255.0   U     0      0        0 eth1
link-local      *               255.255.0.0     U     1000   0        0 eth1
default         192.168.1.1     0.0.0.0         UG    100    0        0 eth1
```

I can access the web interface fine, still. I've restarted my x360/uShare in all sorts of patterns to no avail. Whenever I do a 'Test Media Connection,' it invariably fails on "PC Selected." When I browse for it in the Media/Video (or Media/Music) tabs in the Dashboard, it lists Console and Computer (the latter saying "No computers found.")

My router accepts UPnP. Could it be an issue since the x360 doesn't go through the router at all?

Router <- - - wireless - - -> computer <---wired---> x360

---

### Post by mvavrik on 2008-04-17
So, I have installed Ubuntu 8.04 and am attempting to install **UShare** in order to stream movies to my **Xbox** **360**. I'm new so bear with me and please let me know if I fail to include any relevant information.

I will be attentive of my post and will try to respond to your responses immediately because I know there will be questions.


**I have UShare and have attempted to configure it, receiving this output:**

user@Ubuntu:/root/ushare-1.1$ sudo ./configure
Checking for compiler available...
gcc is unable to create an executable file.
If gcc is a cross-compiler, use the --cross-compile option.
C compiler test failed.
See file "config.log" produced by configure for more details.
user@Ubuntu:/root/ushare-1.1$

**I have downloaded the latest release of GCC and attempted to configure that:**

user@Ubuntu:~/Desktop/gcc-4.3.0$ sudo ./configure
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking target system type... i686-pc-linux-gnulibc1
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln works... yes
checking whether ln -s works... yes
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

**Some relevant information from "config.log" seems to be the following:**

Thread model: posix
gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
configure:3166: $? = 0
configure:3168: gcc -V </dev/null >&5
gcc: '-V' option must have argument
configure:3171: $? = 1
configure:3194: checking for C compiler default output file name
configure:3197: gcc conftest.c >&5
/usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status

---

### Post by another_joe on 2008-04-17
> **denisesballs said:**
> Has anyone refined how files are displayed? All my movies and music shows up for both Videos and Music and the Music tags are not read at all.

I am also getting quite annoyed with this, its fun after 5 mins of searching for a song realizing you are in the artist or album section and then the song does not play,

---

