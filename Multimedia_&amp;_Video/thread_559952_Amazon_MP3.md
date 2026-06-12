---
title: "Amazon MP3"
date: 2007-09-25
forum: Multimedia &amp; Video
---

### Post by sedition on 2007-09-25
Just a quick note: the new Amazon MP3 released today is fully compatible with Linux. Previews play in the browser, downloads are DRM-free MP3 that will go on any player. Me thinks Apple has a run for its money...

---

### Post by blockcipher on 2007-09-25
I was just checking this out, and thought I would search here first.  Thanks :D

---

### Post by madscientist on 2007-09-27
Just a quick note: it's not yet 100% supported under Linux.  You can buy individual songs just fine but in order to buy albums you need their special Amazon MP3 downloader tool, and that's only available for Windows and Mac OSX right now.  They do say on their site that a Linux version is being developed, but they give no other info as to when you might see this.

So, if you're happy with buying songs one a time, this is great.  If you want to purchase albums, you'll need a Windows or Mac system.

However, once you get the files they are, indeed, completely unrestricted, high quality mp3s that sound great on Linux.

---

### Post by blockcipher on 2007-09-27
I am not able to download 'just' the mp3 via their website even on single downloads.  I always get the AMZ files.

---

### Post by jtuchscherer on 2007-09-27
> **madscientist said:**
> Just a quick note: it's not yet 100% supported under Linux.  You can buy individual songs just fine but in order to buy albums you need their special Amazon MP3 downloader tool, and that's only available for Windows and Mac OSX right now.  They do say on their site that a Linux version is being developed, but they give no other info as to when you might see this.

Just on a side note, I tried to install the app under wine. But without spending too much time on it, I wasn't able to start it. Installing went fine, only starting it didn't work.
Maybe somebody else has more luck. If so, please post it here.
Thanks

---

### Post by sedition on 2007-09-28
> **madscientist said:**
> Just a quick note: it's not yet 100% supported under Linux.  You can buy individual songs just fine but in order to buy albums you need their special Amazon MP3 downloader tool, and that's only available for Windows and Mac OSX right now.  They do say on their site that a Linux version is being developed, but they give no other info as to when you might see this.

Ah. Thanks for the annotation. Didn't even try it. Hopefully the client will be developed sooner than the one for WoW...

---

### Post by madscientist on 2007-09-28
> **jtuchscherer said:**
> Just on a side note, I tried to install the app under wine. But without spending too much time on it, I wasn't able to start it. Installing went fine, only starting it didn't work.
Maybe somebody else has more luck. If so, please post it here.
ThanksI tried with Corssover (6.0; I don't have 6.1) and got identical results: it installed fine but when I tried to start it both the .exe and the wineserver just ran forever with no display appearing (but they were using plenty of CPU!)

I suspect that maybe the app needs to be started from within a browser.  I was going to test this out by installing IE in my Crossover bottle (AFAIK, FireFox for Windows is not supported by Crossover), but my company recently instituted a new proxy server for all web access and in order to get out I need to log in via Active Directory, and for some reason the IE in my new bottle isn't doing that (although the IE in my old bottle does...!)  So, I need to try this out at home but I haven't gotten around to it yet.

If anyone else tries this (both IE and Amazone MP3 Downloader together) let me know.

---

### Post by madscientist on 2007-10-02
I just installed the newest Crossover, version 6.2 just released today.  Using this I am able to install the Amazon MP3 downloader (which I could do with 6.0 and 6.1 as well), and also launch it so it brings up the downloader window (this didn't work with previous versions).

However, the minute I try to open any menu the program exits/crashes/whatever.

So, still no love!

And, I can't figure out how to install IE in my Windows XP bottle--I get it installed (although Crossover desperately wants to put it into a Windows98 bottle) but there is no way to launch it; nothing shows up in the menus and doing a find for .exe (or .EXE) files in the bottle yields nothing promising.  The ie6setup.exe is there but if I run it again it complains I already have IE installed.  So, I still don't know if the downloader would work when invoked from IE.  Note I can't use a Windows98 bottle because the Amazon downloader checks and won't install in that bottle, saying it requires WindowsXP.

---

### Post by eternalperson on 2007-10-02
I am glad that Amazon MP3 has been established. Now people do not have to be forced  to use the Windows or Mac platform for downloading music. It would be cool to get Amazon MP3 support in Rhythmbox now. :) Now we'll have a real iTunes equivalent or even better: an iTunes killer for Linux.

---

### Post by madscientist on 2007-10-02
Well, you could do streaming music before now on Linux; Real supports Linux with their Rhapsody service, which gives you unlimited streaming for $13 a month (see [http://www.rhapsody.com/](http://www.rhapsody.com/))  The problem with Rhapsody is that you can't BUY music through it, unless you have Windows or Mac.  Just like Amazon and their MP3 downloader, you have to have a special application to purchase music through Rhapsody, and that app is not supported on Linux.  Rhapsody is worse than Amazon in another way: the music you buy (if you have a Windows or Mac box around to use to buy it) is provided in DRM-restricted format that only works with Real's secure player which (as far as I can tell) doesn't work on Linux either.  So, in order to purchase music via Rhapsody and play it on Linux you have to buy it on a Windows or Mac system, then burn it to a CD using Real's DRM-capable software, then rip it from the CD to your system in a portable, DRM-free format that will work on Linux.  Pretty bogus.  But, the streaming does work pretty well on Linux and so that's a useful start.

Although Amazon seems promising, as we've been discussing you still can't buy whole albums on Linux because their downloader application doesn't support LInux.  But at least you can buy single songs, and when you get them (or buy an album on a Windows or Mac system) they're immediately usable on your Linux system without special proprietary applications or need to burn them to CD first.

---

### Post by specvthis on 2007-10-17
I was successfully able to download a full album from the Amazon mp3 site using their amz file.  Installed the windows version of the Amazon MP3 Downloader using wine.  It will NOT restart automatically.  Then download the amz file somewhere.  Navigate to the installed location of the Amazon MP3 Downloader.

cd ~/.wine/drive_c/Program\ Files/Amazon/MP3\ Downloader/

Then simple execute the windows executable but supply it with the amz file from the terminal.

wine AmazonMP3Downloader.exe ~/Desktop/asdf.amz

After doing this it automatically placed itself in my taskbar and proceeded to download the album.  The GUI did not work in the least bit so if I tried to actually open it everything crashed but running in the taskbar it did its business.  Voila! an entire album was placed in my Home directory.  Note: running Gutsy Gibbon RC1 and wine 0.9.46.

---

### Post by FredB on 2007-10-17
Well, this is a good news : no more crappy wma + drm files.

But I prefer free music (like free software). Just look at [http://www.jamendo.com/](http://www.jamendo.com/)

---

### Post by tolremeno on 2007-11-12
Bump.

Anybody found an easy way to use amazon mp3 yet?

---

### Post by jomofo7 on 2007-12-08
I expanded on the post by **specvthis** with step-by-step instructions and screenshots:

[http://assert-false.blogspot.com/2007/12/using-amazon-mp3-downloader-on-gutsy.html](http://assert-false.blogspot.com/2007/12/using-amazon-mp3-downloader-on-gutsy.html)

---

### Post by madscientist on 2007-12-09
Hah!  I just was looking into this today as well!  Jomofo7 did a great job with the basic setup and screenshots etc.  I had written a script that automates this all plus some tips on using it and integrating more tightly with FireFox.  I wrote it up on my website:

[http://mad-scientist.us/amazon.html](http://mad-scientist.us/amazon.html)

Instead of duplicating jomofo7's excellent work I just pointed people at it, then added info about my extra features.  Hope that's OK.

Have fun all--remember if something breaks, you get to keep both halves!

---

### Post by dulles on 2007-12-15
Adding my two cents: I took a risk and installed Wine (I'm running 7.10 Gutsy) and ran it on the Windows XP/Vista Amazon MP3 Downloader Installer. It installed into ~/.wine and I was able to download the .amz file and run it just as described. The window it created was tiny and content-free, but a downloader icon appeared on my Gnome bar and the files appeared in ~/Amazon Mp3/

I'M SO HAPPY!!!! DRM-Free music in Linux!

> **specvthis said:**
> I was successfully able to download a full album from the Amazon mp3 site using their amz file.  Installed the windows version of the Amazon MP3 Downloader using wine.  It will NOT restart automatically.  Then download the amz file somewhere.  Navigate to the installed location of the Amazon MP3 Downloader.

cd ~/.wine/drive_c/Program\ Files/Amazon/MP3\ Downloader/

Then simple execute the windows executable but supply it with the amz file from the terminal.

wine AmazonMP3Downloader.exe ~/Desktop/asdf.amz

After doing this it automatically placed itself in my taskbar and proceeded to download the album.  The GUI did not work in the least bit so if I tried to actually open it everything crashed but running in the taskbar it did its business.  Voila! an entire album was placed in my Home directory.  Note: running Gutsy Gibbon RC1 and wine 0.9.46.

---

### Post by Whiffle on 2007-12-15
> **madscientist said:**
> I just installed the newest Crossover, version 6.2 just released today.  Using this I am able to install the Amazon MP3 downloader (which I could do with 6.0 and 6.1 as well), and also launch it so it brings up the downloader window (this didn't work with previous versions).

However, the minute I try to open any menu the program exits/crashes/whatever.

So, still no love!

And, I can't figure out how to install IE in my Windows XP bottle--I get it installed (although Crossover desperately wants to put it into a Windows98 bottle) but there is no way to launch it; nothing shows up in the menus and doing a find for .exe (or .EXE) files in the bottle yields nothing promising.  The ie6setup.exe is there but if I run it again it complains I already have IE installed.  So, I still don't know if the downloader would work when invoked from IE.  Note I can't use a Windows98 bottle because the Amazon downloader checks and won't install in that bottle, saying it requires WindowsXP.


Same thing with me on Slackware using wine 0.9.5  Hmm.. I did just download "You're a Mean One Mr. Grinch"  Oh yes....

---

### Post by madscientist on 2007-12-17
As I mentioned in post #15, using the downloader with Wine does work but you can't do anything other than download.  I wrote some instructions (and referred to jomofo7's very nice website) and a script to integrate this pretty well.  Give it a whirl!

I tried to post about this to the howto forum but my post was rejected and no reason was provided (that I could see) :confused::cry:

---

### Post by EddieT on 2007-12-27
[FONT="Times New Roman"]Thanks to some great posts I can now get this working, well done!  FYI I e-mailed Amazon about Ubuntu-Linux support and this is what I got.  Sounds like e-mailing them might help put the pressure on so if you get a chance drop them a line[/FONT].

> Hello from Amazon.com.

Thank you for asking about a Linux version of the Amazon MP3 Downloader.

At this time the Linux version is still in development, and we do not
have an estimate for when it will be available.

If you prefer to make your purchases on a Linux platform, you will be
limited to purchasing individual songs. Choose "Skip installation and
continue" if prompted to install the Downloader and choose "Save" when
prompted to download the .mp3 file by your Web browser. Choosing
"Open" will start your default media player but will not save the file
to your computer.

When the Linux version of the Amazon MP3 Downloader is released it
will be available for download on the Amazon MP3 Downloader
Installation page.  I encourage you to check back at this URL in the
future for updates:

[http://www.amazon.com/gp/dmusic/help/amd.html/ref=sv_dmusic_3](http://www.amazon.com/gp/dmusic/help/amd.html/ref=sv_dmusic_3)

I've also passed along your feedback about the availability of the
Linux version of the Amazon MP3 Downloader to the Amazon MP3 Music team.

Thanks for your interest in Amazon MP3 Music Downloads.


Please let us know if this e-mail resolved your question:

---

### Post by CFBauer on 2008-01-06
I sent an email about a month ago to no response.  Please Amazon, take our money!

---

### Post by adamvert on 2008-01-08
Thanks madscientist, yr script works perfectly!

---

### Post by da Wookiee on 2008-01-11
Tried installing using cli and wine and it gave me a popup saying that it required Win XP or later...  Seems to me they caught on to it.

Oh well,  I can get some songs now and wait to buy albums until they make it available.


And I'll email them about a linux downloader.

---

### Post by Kujen on 2008-01-17
> **da Wookiee said:**
> Tried installing using cli and wine and it gave me a popup saying that it required Win XP or later...  Seems to me they caught on to it.

Oh well,  I can get some songs now and wait to buy albums until they make it available.


And I'll email them about a linux downloader.


Open winecfg and change your Windows version to either XP or Vista.

---

### Post by Kujen on 2008-01-22
Well I won't be giving anymore money to these guys. My download failed once and now I'm not able to redownload it. I have to waste time contacting these jackasses by email, with no guarantee that they'll let me redownload it. Amazon, you missed your chance to gain a customer, guess it's back to pirating for me.

There's one question that's always bugged me. Why do I get treated like a piece of **** criminal when I decide to pay for something, but I have no troubles when I pirate it? Amazon is taking a step forward with taking DRM out, but this is just a pain in my ***.

---

### Post by doorknob60 on 2008-01-26
At least they care more than other companies, assuming they're actually wokring on a Linux downloader (unlike Ventrilo :P). And it's DRM free and good quality and price so it's gonna become my main Online Music Source :)

EDIT: Also I found out that this service is still considered in Beta stage, so it's understandable for them to not have a Linux downloader yet :)

---

### Post by MichiganMan on 2008-01-31
Yeah, the incremental upgrade got me too.  The downloader worked before, (using the command line) but didn't after installing the upgrade.  This irritated me since I was in the process of preparing to purchase an album.  The one I wanted had no price advantage over buying each mp3 separately, so I could have taken that route without feeling like a fool, but I wanted Amazon's logs to show an album purchase from a Linux OS.  

The tip to download and install gdiplus.ddl in my ~/.wine/drive_c/windows/system32 from the comments at:

[http://assert-false.blogspot.com/2007/12/using-amazon-mp3-downloader-on-gutsy.html](http://assert-false.blogspot.com/2007/12/using-amazon-mp3-downloader-on-gutsy.html)

got me a functional Amazon downloader again.  Accessing the menu still crashes the app, but I was able to download a full album using the command line method.

---

### Post by milliman on 2008-03-08
Amazon's downloader installed perfectly with Hardy, but it changes the MIME type of MP3 files to application/x-extension-mp3 instead of audio/mpeg like it should be.  This causes a major problem when trying to import the songs into Banshee.  I had to delete the files associated with this new MIME type and rebuild the MIME type cache for my user.

Amazon should stick with the standard MIME types unless they have a reason for changing it.  I see none.

---

### Post by madscientist on 2008-03-08
Whoa!  For those who haven't realized it, Amazon has released its downloader for LInux.  They support Ubuntu 7.10 (Gutsy) as well as Debian Etch, Fedora 8, and SUSE 10.3.

I just installed it and I don't notice it changing my MIME setup.  Milliman, how did you determine that your MIME types were changed?  I checked the properties on my MP3 songs and they were all still reported (by nautilus) as audio/mpeg.

It did add a new MIME type for the AMZ files that it downloads, but that's OK.

Thanks Amazon!

---

### Post by bcrowell on 2008-03-08
I've had a series of problems trying to get the album downloader to work on x64 gutsy.

# apt-get install libboost-signals1.34.1 libboost-iostreams1.34.1
# dpkg --force-architecture -i amazonmp3.deb
$ amazonmp3 
amazonmp3: error while loading shared libraries: libgtkmm-2.4.so.1: cannot open                                                                                                     shared object file: No such file or directory
$ ls /usr/lib/libgtkmm-2.4.so.1
/usr/lib/libgtkmm-2.4.so.1

I don't understand why it's complaining about not finding the gtkmm library, since I have it installed.

---

### Post by argraff on 2008-03-08
I'm SO happy about this! I installed it this morning - no problems so far. :D

---

### Post by madscientist on 2008-03-09
> **bcrowell said:**
> I've had a series of problems trying to get the album downloader to work on x64 gutsy.

# apt-get install libboost-signals1.34.1 libboost-iostreams1.34.1
# dpkg --force-architecture -i amazonmp3.deb
$ amazonmp3 
amazonmp3: error while loading shared libraries: libgtkmm-2.4.so.1: cannot open                                                                                                     shared object file: No such file or directory
$ ls /usr/lib/libgtkmm-2.4.so.1
/usr/lib/libgtkmm-2.4.so.1

I don't understand why it's complaining about not finding the gtkmm library, since I have it installed.
I don't have any 64bit systems running Ubuntu so I can't really help.  However, I expect that those libraries you installed are the 64bit versions.  The amazonmp3 program is probably a 32bit application, which means you need to install 32bit versions of those shared libraries in order to run it.

You can check this by running "file amazonmp3" and "file libgtkmm-2.4.so.1" and seeing what the architecture is listed as.

Maybe someone else with a 64bit system can give some help as to how to install the 32bit versions of these libraries.

---

### Post by madscientist on 2008-03-09
Apropos of nothing, and while giving a big "thanks" to Amazon for their efforts to support Linux, I do have to shake my head a little bit.  The fact that this tool depends on having libboost installed is a pretty good indication that it's written in C++.  I just have to wonder why someone would write a tool like this in C++ in 2007/2008, with all the great scripting languages we have now.  Seems like they could have had this done weeks ago if they'd used something like Python or Ruby or Perl or Java or Mono or...

Don't get me wrong, I program in C++ for my day job... but for a tool like this I wouldn't use it.

---

### Post by joseelsegundo on 2008-03-11
> **bcrowell said:**
> I've had a series of problems trying to get the album downloader to work on x64 gutsy.

# apt-get install libboost-signals1.34.1 libboost-iostreams1.34.1
# dpkg --force-architecture -i amazonmp3.deb
$ amazonmp3 
amazonmp3: error while loading shared libraries: libgtkmm-2.4.so.1: cannot open                                                                                                     shared object file: No such file or directory
$ ls /usr/lib/libgtkmm-2.4.so.1
/usr/lib/libgtkmm-2.4.so.1

I don't understand why it's complaining about not finding the gtkmm library, since I have it installed.

I got it working via *getlibs* using the instructions in [[COLOR="Red"]this thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=474790").  Props be to Cappy.

---

### Post by Rogers on 2008-03-12
I wrote a quick how-to to make it work.

[http://runithard.com/?p=21]("http://runithard.com/?p=21")

---

### Post by bcrowell on 2008-03-12
Thanks, joseelsegundo and Rogers, for your help! I was able to get the amazonmp3 app running on my 64-bit system. One thing that hung me up for a while was that when I was on the amazon web site, and I tried to download an album, it still said I don't have the downloader installed, even though I did. It took me a while to notice where it said, "If you have already installed the Amazon MP3 Downloader, click here to enable it for use with this browser.."

---

### Post by vgrisham on 2008-03-23
I just upgraded to Hardy, and followed the instructions to install with help from getlibs (which worked swell in Gutsy). Unfortunately, I can't get amazonmp3 to launch in Hardy. Has anybody out there on the bleeding edge found a way to make this work?

Here's my output:
> 

vaughn@vaughn-desktop:~$ amazonmp3

(amazonmp3:6067): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so: wrong ELF class: ELFCLASS64
terminate called after throwing an instance of 'Gdk::PixbufError'
Aborted (core dumped)



Oh no! Not the dreaded ELF class error! Help! 

I guess I should've mentioned that I am using 64-bit Hardy. I would have thought that getlibs might have caught the above error. I wonder how one would go about spoofing the ELF class on the file cited above. I'm in over my head here.

---

### Post by Cappy on 2008-03-25
> **vgrisham said:**
> I just upgraded to Hardy, and followed the instructions to install with help from getlibs (which worked swell in Gutsy). Unfortunately, I can't get amazonmp3 to launch in Hardy. Has anybody out there on the bleeding edge found a way to make this work?

Here's my output:


Oh no! Not the dreaded ELF class error! Help! 

I guess I should've mentioned that I am using 64-bit Hardy. I would have thought that getlibs might have caught the above error. I wonder how one would go about spoofing the ELF class on the file cited above. I'm in over my head here.

It's a hardy problem, what I know about it is here:
[http://ubuntuforums.org/showthread.php?t=613087&page=5#41](http://ubuntuforums.org/showthread.php?t=613087&page=5#41)

---

### Post by FloppusMaximus on 2008-03-26
Hi, all.  If you're having trouble with Amazon's downloader, and/or feeling adventurous, you may want to check out Clamz, a program I've just released, which is a free software replacement for amazonmp3.  The project web site is at [http://clamz.googlecode.com/](http://clamz.googlecode.com/) .

A word of warning -- currently it is command-line only, and you have to compile it yourself.  I plan to write a GTK+ user interface for it sometime soon, as well as releasing binary packages, but I thought it more important to get the code out there and get some feedback as soon as possible.  You can contact me at [email]floppusmaximus@users.sourceforge.net[/email].

---

### Post by vgrisham on 2008-04-12
Has anyone had any luck getting this going with 64-bit Hardy yet? While trying to install the etch deb following up with getlibs, I am still getting: 

> 
[email]vaughn@vaughn-desktop:~/.inst[/email]all$ sudo dpkg -i --force-all amazonmp3.deb
[sudo] password for vaughn: 
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 158062 files and directories currently installed.)
Preparing to replace amazonmp3 1.0.3-1 (using amazonmp3.deb) ...
Unpacking replacement amazonmp3 ...
dpkg: amazonmp3: dependency problems, but configuring anyway as you request:
 amazonmp3 depends on libboost-thread1.33.1; however:
  Package libboost-thread1.33.1 is not installed.
 amazonmp3 depends on libboost-iostreams1.33.1; however:
  Package libboost-iostreams1.33.1 is not installed.
 amazonmp3 depends on libboost-signals1.33.1; however:
  Package libboost-signals1.33.1 is not installed.
 amazonmp3 depends on libboost-date-time1.33.1; however:
  Package libboost-date-time1.33.1 is not installed.
Setting up amazonmp3 (1.0.3-1) ...

[email]vaughn@vaughn-desktop:~/.inst[/email]all$ getlibs /usr/bin/amazonmp3
No match for libboost_date_time-gcc-mt-1_33_1.so.1.33.1
No match for libboost_signals-gcc-mt-1_33_1.so.1.33.1
No match for libboost_iostreams-gcc-mt-1_33_1.so.1.33.1
No match for libboost_thread-gcc-mt-1_33_1.so.1.33.1
No packages to install


Thanks for your help.

---

### Post by Cappy on 2008-04-12
Use the ubuntu version instead of the etch version. The etch version uses older libraries.

---

### Post by vgrisham on 2008-04-13
Thanks Cappy. I got it to install now it's throwing the following error:

> 
[email]vaughn@vaughn-desktop:~/.inst[/email]all$ amazonmp3
terminate called after throwing an instance of 'Gdk::PixbufError'
Aborted (core dumped)


---

### Post by kinghowdy on 2008-04-13
I don't mean to sound like a shill for Amazon but I just used this to buy an individual song today. It was fantastic! I downloaded the .deb  and a minute later Amazon had my money and I had my song. I didn't run into any problems I read about in here so kudos to Amazon for this.

---

### Post by Cappy on 2008-04-13
> **vgrisham said:**
> Thanks Cappy. I got it to install now it's throwing the following error:

64-bit Hardy Heroin problem, try this:
> sudo ln -s /usr/lib32 /usr/l32; sudo sed -i -e 's/usr\/lib/usr\/l32/g' /usr/lib32/gtk-2.0/2.10.0/loader-files.d/libgtk2.0-0.loaders; sudo sed -i -e 's/usr\/lib/usr\/l32/g' /usr/lib32/libgdk_pixbuf-2.0.so.0.1200.8
(taken from: [http://ubuntuforums.org/showpost.php?p=4660832&postcount=7](http://ubuntuforums.org/showpost.php?p=4660832&postcount=7) )

---

### Post by vgrisham on 2008-04-14
Thanks again Cappy. 

Here's the reply I get upon executing the previous command: 

> 
ln: creating symbolic link `/usr/l32/lib32': File exists
sed: can't read /usr/lib32/libgdk_pixbuf-2.0.so.0.1200.8: No such file or directory


---

### Post by OCTOG3N on 2008-05-02
> **eternalperson said:**
> I am glad that Amazon MP3 has been established. Now people do not have to be forced  to use the Windows or Mac platform for downloading music. It would be cool to get Amazon MP3 support in Rhythmbox now. :) Now we'll have a real iTunes equivalent or even better: an iTunes killer for Linux.

It's not an iTunes killer unless it has
TV Shows
Movie Rentals and Downloads
Music Videos
Podcasts
ect.

---

### Post by JohnnyC44 on 2008-05-04
Thanks to everyone who contributed to this thread -- Ubuntu rules!  I just read through the posts, installed the Gutsy downloader from Amazon, gave them my money for a test song and I'm listening to it now.
Not bad for a 64 YO Old F*rt.

---

### Post by pofigster on 2008-05-04
Amazon has Unbox which lets you buy movies, rent movies, buy TV shows, etc...
Doesn't work for Linux as far as I'm aware, but I did use it back when I was a drone.

Their music service though is killer - except for the smallish selection.

---

### Post by JPurdy on 2008-05-19
I am having problems w/ the Amazon MP3 downloader since the upgrade to Heron (AMD 64 bit), too, but in my case, it doesn't seem to be able to find the internet. I cross-posted a plea for help on the Networking forum, but thought I'd give it a shot here, too.

[http://ubuntuforums.org/showthread.php?p=4995545](http://ubuntuforums.org/showthread.php?p=4995545)

I did the symbolic links that Cappy recommended to no avail. BTW, that regex/sed cmd didn't work properly. My resulting file had [FONT="Courier New"]**/usr/l3232/...**[/FONT] I fixed that, pointing to the new [FONT="Courier New"]**l32**[/FONT] directory.

Whenever I try to download a song, the downloader says "*Can't connect. Check your internet connection and retry download.*"

---

### Post by Cappy on 2008-05-20
> **JPurdy said:**
> I am having problems w/ the Amazon MP3 downloader since the upgrade to Heron (AMD 64 bit), too, but in my case, it doesn't seem to be able to find the internet. I cross-posted a plea for help on the Networking forum, but thought I'd give it a shot here, too.

[http://ubuntuforums.org/showthread.php?p=4995545](http://ubuntuforums.org/showthread.php?p=4995545)

I did the symbolic links that Cappy recommended to no avail. BTW, that regex/sed cmd didn't work properly. My resulting file had [FONT="Courier New"]**/usr/l3232/...**[/FONT] I fixed that, pointing to the new [FONT="Courier New"]**l32**[/FONT] directory.

Whenever I try to download a song, the downloader says "*Can't connect. Check your internet connection and retry download.*"

Use
```
sudo apt-get install lib32nss-mdns
```

---

### Post by JPurdy on 2008-05-20
That did it! Thanks, Cappy! :) Wonder why getlibs didn't pick that up... oh well.

---

### Post by tuebinger on 2008-06-14
I get the message "error:  wrong architecture 'i386'"

I have 7.10 so it should work, shouldn't it?

---

### Post by vgrisham on 2008-06-15
> **tuebinger said:**
> I get the message "error:  wrong architecture 'i386'"

I have 7.10 so it should work, shouldn't it?

If you're running 64-bit Ubuntu, the message is due to the fact that amazonmp3 is i386 at this point. 

To install, download the amazonmp3 deb and the getlibs script (see earlier in this thread).

Force install amazonmp3:
> sudo dpkg --force-all -i amazonmp3.debThen install the getlibs script following [these]("http://ubuntuforums.org/showthread.php?t=474790") instructions.

Once you've got both packages installed, code:
> ** **sudo getlibs /usr/bin/amazonmp3


After installation, you'll find a shortcut to amazonmp3 under the Internet section of your Application menu (Gnome).

I hope that helps you.

---

