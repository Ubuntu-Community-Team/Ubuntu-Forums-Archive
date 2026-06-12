---
title: "F-Spot -&gt; Shotwell, a move sidways. (rant)"
date: 2010-06-14
forum: Multimedia Software
---

### Post by AKADAP on 2010-06-14
[http://www.techdrivein.com/2010/06/meet-shotwell-f-spot-replacement-for.html?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+techdrivein+%28Tech+Drive-in%29](http://www.techdrivein.com/2010/06/meet-shotwell-f-spot-replacement-for.html?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+techdrivein+%28Tech+Drive-in%29)

I see this as a move sideways rather than a move forward.
I don't use F-Spot, and will probably never use Shotwell. Why? because one must "import" the pictures into their proprietary file structure. What is wrong with using the already existing file system? Why must these programs impose their own idea of how the pictures should be organized? The only program I have so far used that handled this correctly was Zoom Browser on Windows. It was incomplete, but the organization it displayed was the way the pictures were organized in the file system. If you changed directories, or moved photos around outside of the program, they showed up changed the next time you ran Zoom Browser.

My father uses F-Spot. I can not convince him not to use it, and I can not convince him not to move photos around using the file system. This means he is continuously corrupting F-Spots idea of where the photos are, and he keeps calling me to help him straighten out the mess he has made.

What I want out of a photo organizing tool:

1) Use the file system to keep the files organized, and use what the user has already done! There should be no option to "import" files, just point the software at the top level directory and use it in place, the interface should be similar to Nautilus, showing the file system. Zoom Browser would be a good model for this. Doing it this way means that one is not required to use a specific tool to organize or access the pictures.

2) If you allow notes or audio comments, they should be included as part of the photo file itself. I believe that jpeg has the capability to store audio comments & notes, it would be nice if one could actually use this feature. Any other means of storing this information means this data will be lost when your tool becomes obsolete and a new tool comes out.

3) Slide shows should be able to play videos interleaved with the slides. Nearly every camera available today has the capability of recording video. I would very much like to be able to show a slide show with the slides and videos in chronological order.

I want a tool that lets me find pictures easily, setup & view slide shows easily, and does not try and take over control of my pictures.

---

### Post by ajgreeny on 2010-06-14
**Digikam**; it's kde, I admit, but it is very good as long as you don't mind all the kde libs etc etc that are also installed with it.

Or for something very much simpler, have a look at **gthumb**.

---

### Post by AKADAP on 2010-06-14
Shotwell has an option to import without making a copy.
I tried that, it spent about an hour "importing" my 40 GB of photos. It did NOT import any PNG photos, and ignored any videos.
It stores all of its info in a hidden database file. What happens if I move a picture in one of the directories it scanned? does it crash?

---

### Post by AKADAP on 2010-06-14
> **ajgreeny said:**
> **Digikam**; it's kde, I admit, but it is very good as long as you don't mind all the kde libs etc etc that are also installed with it.

Or for something very much simpler, have a look at **gthumb**.

Digikam seems to be more of the same. It still insists on "importing" the files.

gthumb is closer to what I am after, but its file browser could use some work, and the slideshow ignores videos.

Thanks for pointing that out.

---

### Post by ajgreeny on 2010-06-15
Digikam does not "import" in quite the same way as f-spot, and it is possible, though not the default to get it to scan your pictures folder. or even all of /home if you want, every time it is started, it just take a bit longer to start then, but at least it keeps updated with any changes you have made to your files, such as moves or deletes, etc etc.

With f-spot, as far as I can see, you do need to import files every time you have added any photos to the folders, and you also need to uncheck the "Copy files to Photos folder" button or you will end up with two copies of every photo on your system.

---

### Post by AKADAP on 2010-06-15
> **ajgreeny said:**
> Digikam does not "import" in quite the same way as f-spot, and it is possible, though not the default to get it to scan your pictures folder. or even all of /home if you want, every time it is started, it just take a bit longer to start then, but at least it keeps updated with any changes you have made to your files, such as moves or deletes, etc etc.

With f-spot, as far as I can see, you do need to import files every time you have added any photos to the folders, and you also need to uncheck the "Copy files to Photos folder" button or you will end up with two copies of every photo on your system.

Shotwell took an hour to scan my 40 GB of pictures, did not import any raw or PNG files, did not even look at the movie files. Would I need to wait an hour every time I started Digikam for it to update its database? Does it handle any picture format or is it stuck with jpg like Shotwell? Does it handle movies? 

gThumb at least lets me play movies even if it won't include them in the slide show.

---

### Post by alphacrucis2 on 2010-06-15
> **AKADAP said:**
> Digikam seems to be more of the same. It still insists on "importing" the files.

gthumb is closer to what I am after, but its file browser could use some work, and the slideshow ignores videos.

Thanks for pointing that out.

If you are using the version of gthumb in the Lucid repos then forget it. For some reason the recent stable version of gthumb wasn't included in Lucid. Install the latest gthumb version instead (I'm assuming you don't already have it). It is a vast improvement.

---

### Post by AKADAP on 2010-06-16
> **alphacrucis2 said:**
> If you are using the version of gthumb in the Lucid repos then forget it. For some reason the recent stable version of gthumb wasn't included in Lucid. Install the latest gthumb version instead (I'm assuming you don't already have it). It is a vast improvement.

Care to point me at a repository that has the current version?
Going to gthumbs home page and clicking on the install button says it is already installed.

The about page on the one I have installed is:
gThumb 2.10.11

---

### Post by alphacrucis2 on 2010-06-16
> **AKADAP said:**
> Care to point me at a repository that has the current version?
Going to gthumbs home page and clicking on the install button says it is already installed.

The about page on the one I have installed is:
gThumb 2.10.11

webupd8 ppa 

[URL="https://launchpad.net/~nilarimogard/+archive/webupd8"]https://launchpad.net/~nilarimogard/+archive/webupd8
[/URL]

Some of their stuff is experimental so take care what you install but I haven't found any issue with their version of gthumb (2.11.3-2) which is a really big feature update over 2.10

---

### Post by AKADAP on 2010-06-17
> **alphacrucis2 said:**
> webupd8 ppa 

[URL="https://launchpad.net/~nilarimogard/+archive/webupd8"]https://launchpad.net/~nilarimogard/+archive/webupd8
[/URL]

Some of their stuff is experimental so take care what you install but I haven't found any issue with their version of gthumb (2.11.3-2) which is a really big feature update over 2.10

The directory tree is a great improvement to what 2.10 had. It still won't play videos as part of the slide show though. Also, a slide show can't span multiple directories.

It seems to handle most video formats, but with very large tif or psd files (not sure which since the directory where this happens has both) it allocates huge chunks of memory (2.5 GB) and hangs with one of my CPUs stuck at 100%. I think it is trying to calculate thumbnails, but it is taking WAY too long. Biggest file in this directory is a 3.4 GB TIF file.

Edit: The problems in the above paragraph were caused by a corrupted 3.4 GB TIF file (it caused the same problem with Nautilus, and other image viewers). That file was from a scanner, recorded at 16 bit color resolution that it appears nothing on Linux can deal with. Gimp also reported other problems with the image, so I deleted it.

gthumbs recognizes that PSD files are pictures, but will not display them.

---

### Post by kevdog161 on 2010-06-17
I really disliked F-Spot because of its importing system of deeply nested directories.  So, I installed Shotwell.  Then I realized that it used the same system.  I was ready to scrap it, but I had discovered that as a program overall, Shotwell was very nice, easy to use, snappy loading, etc.  

So, I did some googling, and came up with this:

[http://www.damonlynch.net/rapid/index.html](http://www.damonlynch.net/rapid/index.html)

Now I have Ubuntu set to launch this program whenever I attach my camera.  I set everything up to import images into my own directory structure.  Afterwards, I just go into Shotwell and click to import from folder and select the 'Pictures' directory.  It scans it and figures out what I added.

---

### Post by ajgreeny on 2010-06-18
I tend to use f-spot in a similar but not quite the same way.

I always import photos into my computer using a card reader and nautilus, into my own directory structure for photos with subdirectories for holidays, family, etc, and then use f-spot to import from that Pictures folder.

I find that much more manageable than just letting f-spot import and deal with everything.

---

### Post by Flash858 on 2010-06-18
Kevdog - Fspot dosen't really nest that deeply, rather it organizes by date. Personally, I find it a perfect solution. With the DCIM structure, if it did not do this, I would have to either rename every file on every import, or {shudder} never reset my numbering system. 

Being a professional photographer ([www.az1photo.com](www.az1photo.com) <-- shameless plug), I restart my numbering system from 001 on every single job for the convenience of the client. Fspot handles this PERFECTLY by filing batches of photos by date. That also makes it easy for me to find photos from a prior job.

I have tried Shotwell, and it should be called shotpoorly :(. Fspot is a mature, robust application, while shotwell is a fledgling. It needs some SERIOUS work for it to be even remotely viable.

I believe its inclusion in 10.10 at the expense of the exclusion of Fspot is a serious mistake, and a disservice to new users. So was the removal of Gimp and the inclusion of pitivi. I have zero use for a video editor, and it got apt-removed after the first boot. While I am ranting, so did Gwibber, which does not work at all. Back to TweetDeck for me, and the dreaded Adobe Air...

It would appear that all apps using mono are being targeted for removal from Ubuntu (is Tomboy next?), and I think that is a mistake. Who cares if it fits on a bloody CD or not? CDs won't even be around in 10 years, and frankly blank ones cost as much as blank DVDs theese days. Just give us the best apps, and give the users the best experience...

---

### Post by kevdog161 on 2010-06-20
Flash - I can see where you're coming from and I do agree that F-Spot is a more robust program than Shotwell.  However, I think that different users have different needs.  I am only a casual, point-and-click photographer - parties, sporting events, holidays, etc.  Further, I don't want the directories nested at all.  I'm also using XBMC as a media center for the television and when I click to view my photos, I don't want to have to click through multiple levels - I want to be dropped into one large directory with thumbnails of all the subdirectories which contain the actual photos.  I am sure this is not a priority for most, but every nested level makes for that many more clicks on XBMC, and makes it much *harder* to find the photos I want to view there.

I think Shotwell is perfect for very casual photo organization and presentation.  Fspot does more, but I don't think I (or some others) need it.  Regardless, I'm glad I solved the nesting issue as it pertained to me.

---

### Post by Flash858 on 2010-06-21
Frankly, if they want to do it right in Meercat, they could take a pointer from the venerable Puppy Linux. In Puppy 5.0, when you first click the "Browse" icon (which is a sym link to whatever the default browser is on the system), it pops up with a list of choices, and when you select from Firefox, Opera, Chromium, or the native Puppy Browser, it downloads, installs, and makes that browser the default.

It would be great to see a software selector in the installer, so you can pick from default browsers, photo managers, music players, word processors, etc. and/or install more than one per category, but set one as default during the process (i.e. I want Firefox and Opera, but make Opera the default).

I'm not saying they should put the entire repository in the ISO, but some popular choices would certainly be doable I would think.

Now that would be superb, and no one could really complain about default programs. Again, the only argument I can see is the size of the ISO, but I firmly believe that has to be tossed aside. Neither Windows 7 nor OSX fits on a CD...

---

### Post by Garthhh on 2010-07-14
What  about picasa?
I would love to here opinions
It displays either format
[date or folders tree]
does all the basic editing functions
& backs up to cd dvd flash...
installs from synaptic

---

### Post by BeRA on 2010-07-15
> **Garthhh said:**
> What  about picasa?
I would love to here opinions
It displays either format
[date or folders tree]
does all the basic editing functions
& backs up to cd dvd flash...
installs from synaptic

Picasa is not an option. And (shortly) this is why:
> 
[http://picasa.google.com/linux/faq.html]("http://picasa.google.com/linux/faq.html")

scroll to the end and than you'll see this:
> Q: Is Picasa for Linux open source?

Picasa for Linux isn’t open source; it uses a carefully tested version of Wine to run the current Windows version of Picasa. Wine itself is an open-source implementation of the Windows API. It runs on top of the X Window System and Linux or Unix.

---

### Post by Garthhh on 2010-07-15
> **BeRA said:**
> Picasa is not an option. And (shortly) this is why:


scroll to the end and than you'll see this:

ahh a purist,

the op had specific technical requirements, which may or may not be handled by picasa
I understand how google makes money [selling ads, business apps & storage], which pays for all sorts of online toys
for me operationally picasa is superior to F-Spot or Shotwell
on the negative side picasa is slow loading the pictures off my camera

---

### Post by TorreyKite on 2010-07-16
> **Garthhh said:**
> ahh a purist,

the op had specific technical requirements, which may or may not be handled by picasa
I understand how google makes money [selling ads, business apps & storage], which pays for all sorts of online toys
for me operationally picasa is superior to F-Spot or Shotwell
on the negative side picasa is slow loading the pictures off my camera


Hey Garthhh,
For those of us who are not purists(yet)... have you installed Picasa for linux?  if so which version and method?  I saw they have a v2.7 and a v3.0  also there was an option for downloading a .deb file vs using a repository.... 
lastly for OS compatibility it mentions Ubuntu Fiesty...   not Lucid. 

thoughts?

Thanks,
TK ;)

---

### Post by Garthhh on 2010-07-16
I tried to install directly from the site & never did get it to work  very well
I had a look & it comes up through the software manager

I just installed using synaptic on this computer took about 2 minutes
listed as version
3.0.5744-02
works fine my wife has been using it on her laptop, which is running mint9, for months [years if you count windows]
does all the minor tweaks
integrates with my google account & webalbums
the only negative I've noticed is no progress bar during import from a camera
I was transferring 600 jpgs a couple of days ago
I got very frustrated, I didn't think it was working, came back in an hour & it was done:KS

I didn't even realize it was using wine, until BeRa pointed it out...

as user friendly applications go I'd say that picasa is the goal to aspire to

on the music front I used Itunes for many years, 
I was looking for a replacement & found the choices available for Ubuntu lacking
until I found
the Guayadeque player
[http://ubuntuforums.org/showthread.php?t=1380811](http://ubuntuforums.org/showthread.php?t=1380811)

---

### Post by Flash858 on 2010-07-18
I have recently discovered XNView. It is one of the best photo managers I have seen. It has been ported for Linux, but it does not seem to run for mestatus bar ( I tried several distros on 3 computers with no luck), or at least not as it does in Windows. 

In Windows, it is very much like ACDSee (albeit just a hair slower), and does just a phenomenal job of viewing and managing photos, converting file formats, and integrating all sorts of actions into the shell.

This is the project that Cannonical and other major distros should be looking at IMHO. If it could run in Linux as it does in Windows, the debate over all the other photo programs would come to a screeching halt.

---

### Post by AKADAP on 2010-07-19
> **Flash858 said:**
> I have recently discovered XNView. It is one of the best photo managers I have seen. It has been ported for Linux, but it does not seem to run for mestatus bar ( I tried several distros on 3 computers with no luck), or at least not as it does in Windows. 

In Windows, it is very much like ACDSee (albeit just a hair slower), and does just a phenomenal job of viewing and managing photos, converting file formats, and integrating all sorts of actions into the shell.

This is the project that Cannonical and other major distros should be looking at IMHO. If it could run in Linux as it does in Windows, the debate over all the other photo programs would come to a screeching halt.

Two questions:
1) Will it play videos as part of slide shows?
2) Will it access the pictures in place so I can use my own directory structure?

---

### Post by sierraindigo on 2010-08-08
> **AKADAP said:**
> Digikam seems to be more of the same. It still insists on "importing" the files.

only just started experimenting with digikam but as far as i can see it would meet your needs best. on first run it lets you choose a directory for photos, if you choose what you've already set up it should show the structure you've already got when you use album view.

---

### Post by ullix on 2010-08-09
Akadap,

I share your thoughts on what a photo tool must do, and have similar experiences and impressions on the programs mentioned in this thread.

Give gthumb another try, and you might enjoy it. I just installed gThumb 2.11.6 under ubuntu lucid, and it is almost there!

Videos are shown within a slide show. The 'almost' is because you need to recognize it (the first frame of it) as a video, and take manual action to start it (move the mouse to see tools). And take manual action again to show the next slide. But much improved for sure.

Be aware: ( I had many catalogues, which were stored under /home/user/.gnome2/gthumb/collections/... as plain txt files. They are now stored as xml files under /home/user/.local/share/gthumb/...)

---

### Post by AKADAP on 2010-08-10
> **ullix said:**
> Akadap,

I share your thoughts on what a photo tool must do, and have similar experiences and impressions on the programs mentioned in this thread.

Give gthumb another try, and you might enjoy it. I just installed gThumb 2.11.6 under ubuntu lucid, and it is almost there!

Videos are shown within a slide show. The 'almost' is because you need to recognize it (the first frame of it) as a video, and take manual action to start it (move the mouse to see tools). And take manual action again to show the next slide. But much improved for sure.

Be aware: ( I had many catalogues, which were stored under /home/user/.gnome2/gthumb/collections/... as plain txt files. They are now stored as xml files under /home/user/.local/share/gthumb/...)

I am using gthumb. Every time I see an update go by, I open it up, select a few pictures and a video, and start a slidshow. So far, every attempt has resulted in the slides being shown, and the video ignored.

---

### Post by ullix on 2010-08-10
> **AKADAP said:**
> I am using gthumb. Every time I see an update go by, I open it up, select a few pictures and a video, and start a slidshow. So far, every attempt has resulted in the slides being shown, and the video ignored.

Yes, but I said 'almost'!

Indeed, when you start a slideshow by the slideshow command (function key F5) any video in the sequence is ignored. But when you start a (manual) slide show using fullscreen mode (function key F11) then you need to manually step through the slideshow (PgDn/PgUp), but at least the video is shown as a full screen slide, and by mouse-clicking on it (no keys seem to work) you can play the video full screen and then continue with the next slide.

There are still some bugs, resulting in occasional crashes, but this is the best option so far for including a video in a slide show

---

### Post by AKADAP on 2010-08-10
> **ullix said:**
> Yes, but I said 'almost'!

Indeed, when you start a slideshow by the slideshow command (function key F5) any video in the sequence is ignored. But when you start a (manual) slide show using fullscreen mode (function key F11) then you need to manually step through the slideshow (PgDn/PgUp), but at least the video is shown as a full screen slide, and by mouse-clicking on it (no keys seem to work) you can play the video full screen and then continue with the next slide.

There are still some bugs, resulting in occasional crashes, but this is the best option so far for including a video in a slide show

Definitely an improvement over what I had. I can reliably get it to crash by clicking on the play button, must click on the image to get a video to play.

---

### Post by mjc1 on 2010-08-11
> **AKADAP said:**
> Definitely an improvement over what I had. I can reliably get it to crash by clicking on the play button, must click on the image to get a video to play.

Please file a bug report at [http://bugzilla.gnome.org/enter_bug.cgi?product=gthumb](http://bugzilla.gnome.org/enter_bug.cgi?product=gthumb)

I do not believe this has been reported, so the developers won't fix it unless you report it.

- Mike

---

### Post by AKADAP on 2010-08-13
> **mjc1 said:**
> Please file a bug report at [http://bugzilla.gnome.org/enter_bug.cgi?product=gthumb](http://bugzilla.gnome.org/enter_bug.cgi?product=gthumb)

I do not believe this has been reported, so the developers won't fix it unless you report it.

- Mike

I did, and they claim it is already fixed, just hasn't made it into a released version.
I usually like to wait and see if the bug gets fixed in the next version before I report them, since if it is obvious, they will fix it without having to deal with a bug report.

---

### Post by mechanic on 2010-09-15
Shotwell is in rapid development (see their mailing list) with some rough edges but much better overall than F-Spot; that's why it's in 10.10. Files don't have to move, just read the information dialog when you start up which explains that you can leave files in place. The concern for me with Shotwell is that everyone clamours for new features at the expense of fixing known issues, and it will turn out too bloated.

---

### Post by h0bbe on 2010-10-01
I'm looking for a photo management tool that writes XMP tags to the actual picture file and uses the same folder structure that I've set upp without making any copies into a new structure. My primary use is for tagging pictures on a NAS. I also want other users on other platforms, in my case Mac OS, to have the possibilty to view and edit the tags.

Is this possible? Is Shotwell for me?

Thanks.

---

### Post by Garthhh on 2010-10-01
found this for Picasa
[http://www.anvo-it.de/wiki/avpicfacexmptagger:main](http://www.anvo-it.de/wiki/avpicfacexmptagger:main)

---

### Post by AKADAP on 2010-10-01
> **h0bbe said:**
> I'm looking for a photo management tool that writes XMP tags to the actual picture file and uses the same folder structure that I've set upp without making any copies into a new structure. My primary use is for tagging pictures on a NAS. I also want other users on other platforms, in my case Mac OS, to have the possibilty to view and edit the tags.

Is this possible? Is Shotwell for me?

Thanks.

Look at gthumb. It claims to have XMP support though I have no idea how to use XMP with gthumb. It does let you access your pictures where you put them, and does not insist on making its own copies.

---

### Post by h0bbe on 2010-10-01
Thanks!

I'm trying out Geeqie now. Looks promising...

---

### Post by AKADAP on 2010-10-02
> **h0bbe said:**
> Thanks!

I'm trying out Geeqie now. Looks promising...

It looks like Geeqie is a bit better for viewing and editing XMP stuff.

I like gthumb because they are attempting to integrate videos into their slideshow. I really want the videos I record to be interspersed with the photos I take in chronological order when I view a slide show. One must still manually start the videos with gthumb, but it is the first tool I've found that even tries to do this.

---

### Post by nlsthzn on 2010-10-02
Glad I stumbled upon this thread (was playing around today with fspot and after that shotwell then even picasa and none of these seemed to do what I wanted)... will definitly give gthumb a try!!

---

### Post by AKADAP on 2010-10-03
> **nlsthzn said:**
> Glad I stumbled upon this thread (was playing around today with fspot and after that shotwell then even picasa and none of these seemed to do what I wanted)... will definitly give gthumb a try!!

You might need to use a newer version of gthumb than is available directly from the ubuntu repositories. Somewhere in this thread is instructions on how to set that up.

Also the movie within a slideshow is not in the slideshow, but in the fullscreen view instead, (in full screen, you must manually step through the pictures, and manually start the video when you get to a video file. Not perfect, but better than anything else I've found.)

---

### Post by nlsthzn on 2010-10-04
Thanks for the heads up... I have installed the gThumb that is in the official repo's and it is working very well for me (I have/had more than 3700 duplicate photos and video clips and have been spending the better part of two days deleting them... thanks to gThumb it is easy to find, pity it still takes manual intervention to delete...)

---

### Post by AKADAP on 2010-10-16
I updated to Ubuntu 10.10. I was rather annoyed to find that it had uninstalled gthumb.

In retaliation I uninstalled both F-Spot and Shotwell and re-installed gthumb

---

### Post by mechanic on 2010-11-16
> **h0bbe said:**
> I'm looking for a photo management tool that writes XMP tags to the actual picture file and uses the same folder structure that I've set upp without making any copies into a new structure. My primary use is for tagging pictures on a NAS. I also want other users on other platforms, in my case Mac OS, to have the possibilty to view and edit the tags.

Is this possible? Is Shotwell for me?

Thanks.

Not in the current version (0.7...) such features are promised for 0.8 or 0.9; I only hope Shotwell won't get too bloated with all these features people dream up...a simple catalogue/album was what we started out with...

---

### Post by alroger on 2011-07-08
> **AKADAP said:**
> 
I see this as a move sideways rather than a move forward.
I don't use F-Spot, and will probably never use Shotwell. Why? because one must "import" the pictures into their proprietary file structure. What is wrong with using the already existing file system? Why must these programs impose their own idea of how ...

Took the words right of my mouth.

---

### Post by alroger on 2011-07-08
And now I'm looking for a way to stop nautilus from displaying the stupidiest thing ever: The media contains digital photos. Open Shotwell Photo Manager. 
That and the Banshee Media Players warning right below takes up half of my nautilus display and has no option for removing it.
I don't even know what Shotwell or Banshee are... why bother me with those?

PS: removing them showed a new message, from VLC! DAMN!

[IMG]http://farm7.static.flickr.com/6150/5919935366_5ee3180a05.jpg[/IMG]

---

### Post by eric-yorba on 2011-07-08
> **alroger said:**
> And now I'm looking for a way to stop nautilus from displaying the stupidiest thing ever: The media contains digital photos. Open Shotwell Photo Manager. 
That and the Banshee Media Players warning right below takes up half of my nautilus display and has no option for removing it.
I don't even know what Shotwell or Banshee are... why bother me with those?

PS: removing them showed a new message, from VLC! DAMN!

In Nautlius, go to edit, preferences, media tab.  If you never want it to prompt, just check the second checkbox from the bottom and you're done.

---

### Post by AKADAP on 2011-07-09
> **eric-yorba said:**
> In Nautlius, go to edit, preferences, media tab.  If you never want it to prompt, just check the second checkbox from the bottom and you're done.

Unfortunately, that only prevents the annoying autorun selector box from coming up, it does not prevent Nautalis from "Suggesting" I start shotwell whenever it sees a memory card that has ever been in a camera.

---

### Post by SamTzu on 2011-10-22
> **eric-yorba said:**
> In Nautlius, go to edit, preferences, media tab.  If you never want it to prompt, just check the second checkbox from the bottom and you're done.


There is no such thing as "media tab" in there.

---

### Post by AKADAP on 2011-10-22
> **SamTzu said:**
> There is no such thing as "media tab" in there.

There used to be...

But you are right, it is gone now.

Still no way to turn off the annoying "suggestions" that waste a large part of the viewable directory window.

Seems Nautilus is following the trend of Linux these days: removing configurablity, and forcing unwanted options on us.

---

### Post by grahamhawkins on 2011-11-10
> **AKADAP said:**
> There used to be...

But you are right, it is gone now.

Still no way to turn off the annoying "suggestions" that waste a large part of the viewable directory window.

Seems Nautilus is following the trend of Linux these days: removing configurablity, and forcing unwanted options on us.

I un-installed shotwell. That fixed the pointless banner telling me the SD card from my camera had pictures on (has it? really??) and inviting me to start an application I have no use for...

It's OK putting that sort of thing into the UI (I suppose), but to remove any configuration options to stop it shows a real lack of consideration to users.

---

