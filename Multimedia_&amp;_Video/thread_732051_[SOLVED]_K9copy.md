---
title: "[SOLVED] K9copy"
date: 2008-03-22
forum: Multimedia &amp; Video
---

### Post by anthony2010 on 2008-03-22
Hi all.

Loving this ubuntu and the learning curve is terrific. I have no less come to an impasse with k9copy. whatever video file I try to load, it crashes.

Any ideas anyone? Im running an AMD 2400+ dual core and a motherboard with Nvidia drivers. The OS is ubuntu 7.10.

Ive been going at this for weeks and have only managed to burn one miserly cartoon for my son!

Helllllp! :)

Anthony.

---

### Post by xc3RnbFO8P on 2008-03-22
32 or 64 bit?

---

### Post by anthony2010 on 2008-03-22
Thanks for replying Ringi. To tell the truth, I dont know whether its 32 or 64 bit.

How do I find out?

I feel such a dimmo!

ant.

---

### Post by xc3RnbFO8P on 2008-03-22
First get codecs:
> sudo wget [http://www.medibuntu.org/sources.list.d/gutsy.list](http://www.medibuntu.org/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/medibuntu.list

> wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

> sudo apt-get install w32codecs
> sudo apt-get install libdvdcss2
> sudo apt-get install libdvdread3 libxine1-ffmpeg totem-xine build-essential debhelper fakeroot
sudo /usr/share/doc/libdvdread3/install-css.sh

---

### Post by anthony2010 on 2008-03-22
Hey Ringi.

Thanks for all your work. Unfortunately I havent succeeded. I thought I would paste what happenned in case you have time to help further:

antman@SOS9000:~$ sudo wget [http://www.medibuntu.org/sources.list.gutsy.list](http://www.medibuntu.org/sources.list.gutsy.list) -o /etc/apt/sources.list.d/medibuntu.list
[sudo] password for antman:
antman@SOS9000:~$ wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -o- | sudo apt-key add - && sudo apt-get update
gpg: no valid OpenPGP data found.
antman@SOS9000:~$ darwin1
bash: darwin1: command not found
antman@SOS9000:~$ sudo apt-get install w32codecs
E: Type ‘--20:10:22--’ is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
antman@SOS9000:~$ sudo apt-get install libdvdcss2
E: Type ‘--20:10:22--’ is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
antman@SOS9000:~$ 

I gave up at this point! Maybe its a typo on my part. I will give it another go between now and seeing if you identify the problem.

Thanks for all your help so far.

Ant.

---

### Post by xc3RnbFO8P on 2008-03-22
In Synaptic Package Manager: system>repositories>updates  check all boxes

---

### Post by xc3RnbFO8P on 2008-03-22
I'm wrong again In Synaptic Package manager: System>repositories> Ubuntu Software check all boxes and uncheck cdrom.
Now try it again.

---

### Post by xc3RnbFO8P on 2008-03-22
I can see it now there it is typo > [http://www.medibuntu.org/sources.list.gutsy.list](http://www.medibuntu.org/sources.list.gutsy.list)  should be: > [http://www.medibuntu.org/sources.list.d/gutsy.list](http://www.medibuntu.org/sources.list.d/gutsy.list) 
It is best to copy/paste

---

### Post by anthony2010 on 2008-03-23
Good morning ringi!

Did the copy/ paste thing ( Didnt occur to me to do that!) Lots of things happenned by way of downloads.

It went to 'abort' at the end. Ive copied what happenned at the end here:

The following NEW packages will be installed
  debhelper fakeroot gettext html2text intltool-debian po-debconf totem-xine
0 upgraded, 7 newly installed, 1 to remove and 0 not upgraded.
Need to get 4057kB/4168kB of archives.
After unpacking 8892kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Abort.
antman@SOS9000:~$ sudo apt-get install libdvdread3 libxine1-ffmpeg totem-xine build-essential debhelper fakeroot
Reading package lists... Done
Building dependency tree        
Reading state information... Done
libdvdread3 is already the newest version.
libdvdread3 set to manual installed.
libxine1-ffmpeg is already the newest version.
build-essential is already the newest version.
The following extra packages will be installed:
  gettext html2text intltool-debian po-debconf
Suggested packages:
  dh-make cvs gettext-doc
Recommended packages:
  libmail-sendmail-perl libcompress-zlib-perl
The following packages will be REMOVED
  totem-gstreamer
The following NEW packages will be installed
  debhelper fakeroot gettext html2text intltool-debian po-debconf totem-xine
0 upgraded, 7 newly installed, 1 to remove and 0 not upgraded.
Need to get 4057kB/4168kB of archives.
After unpacking 8892kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Abort.

I tried it a couple of times as you can see. The k9copy still instantly crashes. Im wondering if its worth uninstalling it and re installing it?

Id much rather be doing this than playing in the snow we have here today!

Ant.

---

### Post by xc3RnbFO8P on 2008-03-23
What are the specifications of the computer you are installing on:
Labtop, desktop
Wireless, wired
Old, new
Dualboot?
How did you burn Live disk, did you check md5sum before you burn the disk?

---

### Post by anthony2010 on 2008-03-25
Hi Ringi.

Been away for easter. Last night I did a re install of ubuntu just to make sure I didnt perform some inadvertent task on the system. Once Ive set up my scanner and stuff Im will get back to this k9copy Probably later tonight.

Didn't want you thinking I was ignoring your kindness!

ant.

---

### Post by xc3RnbFO8P on 2008-03-25
I hope it works :)

---

### Post by anthony2010 on 2008-03-26
Hi Ringi.

Ive re installed everything and k9copy is no longer crashing. For some reason it wont open anything other than a .iso file.

Can it be configured to open other formats or do I need to convert the files in another program? My system is a new build desktop with amd dual core 4200+ and a motherboard with an nvidia graphics card on board.

Thanks in advance.

ant.

---

### Post by anthony2010 on 2008-03-26
Oh and reinstalling the scanner was straight forward too :) Well straight forward..ish!

I had a dabble with freespire but felt it was not as versatile a system as ubuntu 7.10. I just could not get the scanner to work in it!

Once this is sorted Im on to the cube!

ant.

---

### Post by xc3RnbFO8P on 2008-03-26
Install in Synaptic Package Manager:

libmad0
libmad0-dev
python-pymad

k3b
k3b-i18n
libk3b2
libk3b2-extracodecs
libk3b2-mp3
libk3b-dev

dvd95
dvdauthor
liba52
liba52  dev
libdvdnav4
mkisofs

See if K9copy opens more than  a .iso

---

### Post by anthony2010 on 2008-03-26
Hey Ringi.

Did what you said except for: libk3b2-extracodecs

This was not in the list of synaptic. Anyway, having installed the other stuff, it still wont open anything other than a .iso image! ( Interestingly I have a .iso image of a movie and i doesnt show on the list at all!)

Do you know of another program that will open and shrink movie files of various formats in ubuntu 7.10?

Hope Im not taking up too much of your time.

ant.

---

### Post by xc3RnbFO8P on 2008-03-26
In k9 settings> dvd is the dvdauthor box checked?

---

### Post by xc3RnbFO8P on 2008-03-26
Reinstall K9 if it do not work you can use:
DVD::RIP (in add/remove all available application)  + [Avidemux]("http://http://www.getdeb.net/app/Avidemux")
AcidRip in add/remove.

---

### Post by mc4man on 2008-03-26
> In k9 settings> dvd is the dvdauthor box checked
It may be the  actions tab  - make sure dvd backup is checked vs. dvd author

---

### Post by anthony2010 on 2008-03-27
Hey.

Done all that. No joy with k9copy. Ive downloaded the other programs you mentioned and will try to figure out how to shrink movies with those. 

If I get stuck, are you ok to help still?

ant.

---

### Post by xc3RnbFO8P on 2008-03-27
Yes, no problem

---

### Post by anthony2010 on 2008-03-27
Hey Ringi.

Is it meant to be this difficult?!

Ive tried everything. All I really want to accomplish is the downloading / shrinking and then burning of a movie.

The other softwares seem mind bogglingly complicated and Ive no idea how to use them. k9copy seems like the best option but it simply will not see anything I download, not even the one .iso file I downloaded.

Im not a giver upper but I have to say Im at a loss now as to what to do next. Fancy remote controlling this pc? Can that be done?

ant.

---

### Post by xc3RnbFO8P on 2008-03-27
Did you try DVD::rip?

---

### Post by anthony2010 on 2008-03-27
Yes.

I have 2 movies which are saved in the video file as .avi. I cant seem to open them with anything and the program 'bittorent' is installed but absent from the drop down menu.

Maybe I am missing something blindingly obvious to an expert!

dvd::rip has no buttons or anything to say 'burn' or 'convert' just loads of jargon tabs at the top! I need something simple and obvious i.e 'click this and x will happen :)

dvd::rip looks like it does what it says and rips from dvd's in the drive. What I need is to burn from downloads.

I feel like 'Rocky' going in for round 5! hehehe

ant.

---

### Post by xc3RnbFO8P on 2008-03-27
Now I have to ask:
Do you need player to play .avi
Do you want to burn .avi on a dvd or cd
Do you want make .avi to dvd (maybe play in dvd player)?

---

### Post by anthony2010 on 2008-03-27
Yes, yes and yes!

although the first one already works.M player plays a .avi no problem. I want to make a .avi play on a dvd player Im guessing it will need converting and shrinking first?

ant.

---

### Post by xc3RnbFO8P on 2008-03-27
To convert .avi to dvd install [Devede]("http://www.getdeb.net/app/DeVeDe")
To be sure did you install this: [http://ubuntuforums.org/showpost.php?p=4565970&postcount=4]("http://ubuntuforums.org/showpost.php?p=4565970&postcount=4")

---

### Post by anthony2010 on 2008-03-27
ok! devede is converting a file! Interestingly, it didnt recognise some files I tried to load in, but it has this one.

The files it didnt recognise say they are .avi though. It will be interesting to see how this works out!

Whilst thats converting, is there a way to get bit torrent visible? Its not in the menu but if I download a torrent it opens.I stopped some downloads, and want to re start them.

ant.

---

### Post by xc3RnbFO8P on 2008-03-27
Did you install Avidemux, if you did, try to open these .avi's with Avidemux.

---

### Post by xc3RnbFO8P on 2008-03-27
> Whilst thats converting, is there a way to get bit torrent visible? Its not in the menu but if I download a torrent it opens.I stopped some downloads, and want to re start them.

In Add/Remove > **KTorrent**

---

### Post by anthony2010 on 2008-03-27
Ringi..

Soooo very close here!

dvede worked and k9copy almost works! It just says there is no recognized drive at the specified location?

I get right to the point of burning but it wont see the disc. I know the drive is recognised because I somehow managed to burn a kids cartoon last week.

Any thoughts?

ant.

---

### Post by anthony2010 on 2008-03-27
Ringi.

The file is 1674.72MB. What should I set the shrink factor to in k9copy?

The dvd+ discs are 4.7GB

so close!!

ant.

---

### Post by xc3RnbFO8P on 2008-03-28
**First K9copy, you got the dvd disk in the dvd drive:**
> In the red circle, opens the dvd.
> In the yellow circle, check box.
> In the blue circle, choose iso (writes dvd as ISO on HD)
> In the green circle, save dvd (as ISO).
**The ISO will fit 1 dvd disk 4.7 GB** (no worry about shrinking)

---

### Post by anthony2010 on 2008-03-28
Ringi.

Success!

THANK YOU SO VERY, VERY MUCH!!!!!!!!

Stay in touch?

ant.

---

### Post by xc3RnbFO8P on 2008-03-28
Yes, and mark it as solved in thread tools. 
Screen shots like a thousand words :)

---

