---
title: "RipOff not working properly"
date: 2012-04-20
forum: Multimedia Software
---

### Post by jukingeo on 2012-04-20
Hello,

There is a CD ripping utility that I would like to use in Ubuntu Studio called RipOff.  I was able to download this from Synaptic and overall I like the interface, but there is a problem.

If I rip one or two songs at a time, everything works fine.   If I try to rip several songs, i.e. an entire album, then the program will 'hang'.  The hard drive light keeps flashing and the program does nothing.

I don't know if anyone else experienced this problem before.  I tried searching here, but didn't come across this issue.  I am wondering if I may have an isolated case.

Rebooting the machine doesn't help either.

Edit:  I just tried to reinstall the program and that didn't work either.  Also another thing I noticed is that the indexing of ripping each song goes off too.  Meaning after the first song rips and gets indexed the second song will run into the third song, and somewhere in the middle it gets indexed. 

I tried this using both .ogg AND mp3 formats and it does the same thing.

I am curious if there is some kind of limitation as to the size file that can be ripped?
If not and this is a true issue with RipOff then I would like some suggestions as to a different ripping program.

Thanx in advance,

Geo

---

### Post by anejo on 2012-04-20
I can't comment on ripoff!
What about trying 'sound-juicer'--a classic--or 'asunder'?

---

### Post by shantiq on 2012-04-20
just tried ripoff   never had heard of it before


ran fine on an album   so no problem there   

no mp3 option on mine [Oneiric repo version] tho

oh i see plugin is in synaptic





===================

rubyripper is very good too but way more complex

---

### Post by jukingeo on 2012-06-23
> **shantiq said:**
> just tried ripoff   never had heard of it before


ran fine on an album   so no problem there   

no mp3 option on mine [Oneiric repo version] tho

oh i see plugin is in synaptic





===================

rubyripper is very good too but way more complex

I don't know if it is because I am using Ubuntu Studio, but RipOff hangs in the middle of ripping an album.  If I rip individually then I am fine.  But that is useless to me.  So Ruby Ripper is good?  perhaps I will check that out.  For now I went back to that 'other' operating system and been using iTunes for ripping.  Or I use a program called EAC, but that too is a Windows program.

Overall, I am on a mission to to satisfy my computer needs entirely within the Linux domain.  The only thing I want to use Windows for is to run games and other specialized programs that do not run in Linux.

The good thing is that with most of my everyday 'office' housekeeping work (letter writing, emails, on-line work).  I am good.  It is just the games and specilized tasks, such as my games and video/audio editing I am still using Windows for them.  It kind of bums me out that I am ALMOST there.  But for now I am still using a dual boot system.

Ok, so I will give Ruby Ripper a look see.

Edit:  I just came back from the Ruby Ripper site and downloaded the program.  However, instead of a quick install, it has this elongated procedure that seems to require several dependencies.   May I asked how you installed it?  

I am somewhat interested in the program after reading that the inspiration for the program was the very same EAC I am using in Windows. 

Thank You,


Geo

---

### Post by VMC on 2012-06-23
> **anejo said:**
> I can't comment on ripoff!
What about trying 'sound-juicer'--a classic--or 'asunder'?

First time I heard of Ripoff, but [**_RubyRipper_**]("http://wiki.hydrogenaudio.org/index.php?title=Rubyripper") works very well.

---

### Post by jukingeo on 2012-06-23
> **VMC said:**
> First time I heard of Ripoff, but [**_RubyRipper_**]("http://wiki.hydrogenaudio.org/index.php?title=Rubyripper") works very well.


Is there an easy way to install Rubyripper?  It looks like it requires quite a few dependencies.  Is there a site that has it all pre-packaged in a self extraction or .dep file?

Thanx,

Geo

---

### Post by mc4man on 2012-06-23
There aren't that many dep's, you likely have many installed already.

What you do need to post is what release of Ubuntu you are on, currently you show Hardy (8.04

---

### Post by jukingeo on 2012-06-26
> **mc4man said:**
> There aren't that many dep's, you likely have many installed already.

What you do need to post is what release of Ubuntu you are on, currently you show Hardy (8.04

Whoa! Nice catch! Can't believe I haven't changed that yet!  LOL.  Yeah, I am on Lucid right now.

---

### Post by shantiq on 2012-06-27
many easy to install debs [**here**]("http://www.linuxappfinder.com/package/rubyripper")  i have used them often and fine


both 32 and 64 for Lucid

---

### Post by mc4man on 2012-06-27
As a remainder - 
the ruby gtk used in 10.04, 10.10, & 11.04 is slightly borked - it will cause the RR gui to hang between tracks for 5-10 min.

There are 2 ways around (install ruby 1.9 from ppa & then build a 1.9 ruby gtk, or set up RR in the gui, then rip from the command line which isn't affected

Also the DEbian & Get Debs packages don't install cd-discid which is needed to make RR useful, a flaw in their packaging though you may already have installed

---

### Post by jukingeo on 2012-06-27
> **mc4man said:**
> As a remainder - 
the ruby gtk used in 10.04, 10.10, & 11.04 is slightly borked - it will cause the RR gui to hang between tracks for 5-10 min.



Really?  I wonder if that could be similar to the issue I had with RipOff.  That program would hang up too...however, I never tested it past 5 mins.  I just took it as being 'locked up" and I just rebooted my machine.

---

### Post by shantiq on 2012-06-28
hmmmm    surprised you experience that Mc    those getdebs have worked very well on my last 2 or 3 installs    but hey maybe not on Lucid    i cannot remember now

[ATTACH]220364[/ATTACH]


anyway   help is at hand if it does not




[URL="http://www.getdeb.net/updates/Ubuntu/12.04/?q=rubyripper"]**another getdeb**
[/URL]



[**and from**]("http://wiki.hydrogenaudio.org/index.php?title=Rubyripper")




[B]Manual Installation on Ubuntu/Debian
[/B]

> It is strongly recommended you use Ubuntu 10.04 (Lucid Lynx) or greater when compiling from the source! 
These instructions were tested with Ubuntu 9.04 ("Jaunty Jackalope&#8220;), Gnome 2.26.1, and Rubyripper 0.5.7.
Make sure Rubyripper has these dependencies as a bare mininum. They can be installed by typing in the terminal window:
 $ sudo apt-get install cd-discid cdparanoia
as a bare mininum or
 $ sudo apt-get install cd-discid cdparanoia flac lame mp3gain normalize-audio ruby-gnome2 ruby vorbisgain
to get the most out of the currently available distros.
For internationalization: instead of the mentioned ruby-gettext install gettext and libgettext-ruby1.8.
Download the Rubyripper archive (see above) from the official website.
Extract the files in the Rubyripper archive (bzipped tarball) into a temporary directory.
Navigate to the directory in which you extracted the Rubyripper archive (Most likely which will be your desktop) or the directory in which you extracted the archive in, e. g. by typing in terminal window:
 $ cd /home/USERNAME/Desktop/rubyripper-0.x.x/
Rubyripper needs to know what features need to be installed. Install both the GUI and command-line version for to get the most out of the application by typing in the terminal window:
 $ ./configure --enable-lang-all --enable-gtk2 --enable-cli
Note: This only prepares/&#8203;configures installation.
In order to install the application, type in the terminal window:
 $ sudo make install
Rubyripper should now be installed with your applications under Applications -> Sound & Video
If it runs according to your needs you may remove the temporary directory.

---

### Post by mc4man on 2012-06-28
> **jukingeo said:**
> Really?  I wonder if that could be similar to the issue I had with RipOff.  That program would hang up too...however, I never tested it past 5 mins.  I just took it as being 'locked up" and I just rebooted my machine.
Wouldn't be for the same reason, ripoff doesn't use ruby

---

### Post by jukingeo on 2012-07-15
> **shantiq said:**
> hmmmm    surprised you experience that Mc    those getdebs have worked very well on my last 2 or 3 installs    but hey maybe not on Lucid    i cannot remember now

[ATTACH]220364[/ATTACH]


anyway   help is at hand if it does not




[URL="http://www.getdeb.net/updates/Ubuntu/12.04/?q=rubyripper"]**another getdeb**
[/URL]



[**and from**]("http://wiki.hydrogenaudio.org/index.php?title=Rubyripper")




[B]Manual Installation on Ubuntu/Debian
[/B]

Hello all,

I tried the manual installation of Rubyripper this afternoon.  Nope, didn't work.  I had a funny feeling it didn't when I executed the sudo make install and it was done in a few seconds.

In the terminal it says:

ruby-gettext is not found.  Translations are disabled.


Supposedly when finished, I am supposed to see it in the Sound & Video menu.  It isn't there, so something went wrong.

Geo

---

### Post by mc4man on 2012-07-15
If you wish to, copied this from my post here for 10.10 because it needed an edit for 10.04 & we can no longer edit posts anymore
(hope I got right, copying posts is a pita - post 174
[http://ubuntuforums.org/showthread.php?t=799621&page=9](http://ubuntuforums.org/showthread.php?t=799621&page=9)

This should configure & install the latest release, (the git clone can be used but not installed) & Fix the gui delay
Should be good if you follow exactly, read the blue & red carefully 

(Make sure you see what I've shown in quote boxes

====================================================================

While several ways to provide the proper ruby and ruby-gtk this is one easy way, - will use a ppa to provide ruby1.9.2 as an alternative and you need to build the gtk lib's
On a fresh install didn't have to remove anything - in existing [COLOR="Red"]remove existing rubyripper and ruby1.8-dev, libgtk2-ruby1.8, if installed.[/COLOR]

[COLOR="Blue"]Quote boxes below should match up.[/COLOR]

```

sudo add-apt-repository ppa:pratikmsinha/ruby192+bindings 
sudo apt-get update
```

```

sudo apt-get install libruby libruby1.8 \
libruby1.9.2 ruby ruby1.8 ruby1.9.2 ruby1.9.2-dev \
build-essential checkinstall libgtk2.0-dev git-core
```

You should see an alternative set at end of install - like this

> ..........
Setting up ruby1.9.2 (1.9.2.z1-1ppa1~lucid) ...
update-alternatives: using /usr/bin/ruby1.9.2 to provide /usr/bin/ruby (ruby) in auto mode.
Setting up ruby1.9.2-dev (1.9.2.z1-1ppa1~lucid) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Then go here and dl [COLOR="Blue"]ruby-gtk2-0.19.4.tar.gz[/COLOR] (last one listed
[http://sourceforge.net/projects/ruby-gnome2/files/ruby-gnome2/ruby-gnome2-0.19.4/](http://sourceforge.net/projects/ruby-gnome2/files/ruby-gnome2/ruby-gnome2-0.19.4/)

Create a build folder (I used rubyr) and extract the above to it, then cd to [COLOR="Blue"]ruby-gtk2-0.19.4[/COLOR]
This at the prompt
```
ruby extconf.rb
```

Should not error, will start out like this
> 
doug@doug-alienware:~/rubyr$ cd ruby-gtk2-0.19.4
doug@doug-alienware:~/rubyr/ruby-gtk2-0.19.4$ ruby extconf.rb
extconf.rb: Entering directory `glib'
checking for GCC... yes
checking for rb_define_alloc_func() in ruby.h... yes
checking for rb_block_proc() in ruby.h... yes
........
and end like this, check

> extconf.rb: Leaving directory 'gtk'

-----
Target libraries: glib, gdkpixbuf, pango, atk, gtk
-----
Done.
When finished
```
make
```

make should end as such

> SUCCEEDED: glib gdkpixbuf pango atk gtk
FAILED: NONE
if good then
```
sudo checkinstall --fstrans=no --default --deldoc  && sudo ldconfig
```

After ruby-gtk2 is installed [COLOR="Blue"]from same prompt[/COLOR]
```
cd .. && wget http://rubyripper.googlecode.com/files/rubyripper-0.6.2.tar.bz2
```
```

tar xvjf rubyripper-0.6.2.tar.bz2 && cd rubyripper-0.6.2
```

```
sudo apt-get install cdparanoia eject cd-discid libgettext-ruby-util \
lame flac vorbis-tools [COLOR="Navy"]mp3gain vorbisgain normalize-audio[/COLOR]
```

Blue are quite optional - if normalize-audio is installed then run this or rubyripper will not find


```
sudo ln -s /usr/bin/normalize-audio /usr/local/bin/normalize
```

Then configure and install rubyripper - note that translations will not work w/ the 1.9.2 ruby libs so hopefully english will do

In same terminal at rubyripper prompt

```

./configure --enable-lang=de,hu --enable-gtk2 --enable-cli --prefix=/usr/local
```

Ex. configure - red must be same, if not then some persistence will fix

> doug@doug-alienware:~/rubyr/rubyripper$ ./configure --enable-lang=de,hu --enable-gtk2 --enable-cli --prefix=/usr/local
ruby-gettext is not found. Translations are disabled!
Checking the NEEDED dependencies....
cdparanoia found...

Checking the OPTIONAL dependencies...
Testing support for the graphical frontend...
[COLOR="Red"]ruby-gtk2 bindings found[/COLOR]

Testing support for freedb metadata fetching...
cd-discid or discid found...

Testing support for ejecting the disk tray...
eject or disktutil found...

Testing support for different codecs on your system...
flac found...
oggenc (vorbis) found...
lame (mp3) found...

Testing support for replaygain...
wavegain NOT found.
vorbisgain found...
mp3gain found...

Testing support for normalize...
normalize found...
Creating the Makefile...
A summary of your settings:

Using the following locations for install:
* Executables: /usr/local/bin
* Localization files: /usr/local/share/locale
* Icon file: /usr/local/share/icons/hicolor/128x128/apps
* Desktop file: /usr/local/share/applications
[COLOR="Red"]* Ruby library: /usr/local/local/lib/site_ruby/1.9.2[/COLOR]

[COLOR="Red"][COLOR="Red"]Gtk2 frontend will be installed[/COLOR][/COLOR]
Cli frontend will be installed


If configure looks good then this 

Code:

```
sudo checkinstall --fstrans=no --default --deldoc  --pkgversion 0.6.2

```

That should do it ...


Note on the ruby alternative - if needing to switch temporarily for something run this, self explanatory


```
sudo update-alternatives --config ruby
```

---

