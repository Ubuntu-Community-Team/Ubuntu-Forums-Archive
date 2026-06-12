---
title: "Open Source on Mac"
date: 2008-04-19
forum: Mac OSX
---

### Post by monomaniacpat on 2008-04-19
In the near future I am likely going to be buying a mac as I want to be able to run a stable and reliable version of Photoshop and Lightroom/Aperture. I have been using Ubuntu as a casual/home user for nearly three years now and have become used to it's admirable versatility and speed. From an ethical point of view, I would like to use an open source system, but it isn't terribly practical. I am tired of using two computers/partitions.

Would you be so kind as to let me know any info regarding the open source elements of mac OSX? What is Darwin? What open source software is available for mac? Particularly ones that have been designed to run natively in OSX... As I say, I am mainly a casual user. My favourite programmes are: Amarok, Evolution Mail, Open Office, Firefox and Pidgin Internet Messenger. I do occassionally like to fiddle around with other programmes and use the terminal a little bit.

I would appreciate any links to info or usergroups/forums.


Thank you.

---

### Post by Winawer on 2008-04-19
That's a bit of a broad question;  there may be somewhat less FOSS for Mac than for Linux, but it's still a *nix-based OS with plenty of native open-source projects.  For instance, I'm using three pieces of free open source software as I write this because I'm in the process of putting together a scientific manuscript:  TeXShop, BibDesk (god, I love this program), and Skim, all of which are native Mac apps.  

Just paging through my applications with Quicksilver (which is a *must-have* piece of software for Mac for many, myself included), I'm also using the following free and/or open source apps on a regular basis:

Adium (IM client)
Aquamacs (native Cocoa port of Emacs)
Cyberduck (FTP/SFTP client)
ffmpegX (video conversion tool)
Octave (open source equivalent to Matlab)
Simple Comic (FOSS comic viewer)
Reggy (a cute little regex tester)
VLC (media player)
Xee (free image viewer / manipulation tool)

And there's probably more that I've forgotten about.  And then there's the paid software that I use, which is a nice option to have at times.  

If you want to find software, you might want to google for Fink, MacPorts, MacUpdate, or even look on Apple's website, where they have a nice little listing of software.

Hope this helps!
Cheers

---

### Post by monomaniacpat on 2008-04-19
Thanks for taking time to respond! Much appreciated.

Someone told me a few years ago about Darwin, in passing. They made it sound like it was another "distribution" (so-to-speak) like Panther, Leopard, etc. Is this the case?

Sorry if the question is too broad. I basically want easy to understand web links that I can read. I'm never sure how much I know about computers, so I guess it's best to stick to straightforward explanations to make things as easy as possible.

Thanks again.

---

### Post by Winawer on 2008-04-19
In short,  Darwin is the "core" of Apple's OS X operating system, based on a Mach kernel crossed tools from one of the BSD flavours (FreeBSD?),  if I recall correctly.  OS X takes Darwin and layers on top things like the Cocoa frameworks, which allow developers to write native Mac apps.  If those last two sentences didn't mean anything to you, then you can forget that you ever heard the name "Darwin" in reference to computers, and you'll never miss it.  Frankly, even if those sentences *did* mean something to you, you could *still* forget about Darwin and almost certainly be none the worse for it.  Darwin is the guts of OS X, but the distributions of OS X like 10.4 - "Tiger" and 10.5 "Leopard" are all that you'll ever worry about.  If you're buying a new Mac, it will have Leopard on it.  

The main concern regarding the distributions of OS X (Tiger and Leopard beings the ones that will be of interest to you) is that the move to Leopard broke some applications which were built for Tiger, and not every single application has been fixed yet.  Having said that, I'm not coming across very many problems these days and 95% of the main consumer applications will either work find out of the box or have already released Leopard updates.  The problem is bigger if you do things like write programs which rely on libraries which you have to build or install yourself, but if you don't then it won't be of much trouble to you.

With regard to software, I would start by going to the Apple website and nosing around their Downloads section ([www.apple.com/downloads/]("http://www.apple.com/downloads/")).   See what looks interesting to you, and go from there.   If you want articles on Macs, OS X and software, you could try the Macworld website ([www.macworld.com]("http://www.macworld.com")).  If you've found a piece of software that interests you, try going to Version tracker ([www.versiontracker.com]("http://www.versiontracker.com")) or MacUpdate ([www.macupdate.com]("http://www.macupdate.com")) and searching for that software so that you can check out the user reviews.  As ever, Google is your friend as well.

Hope that sheds some light!
Cheers

---

### Post by AlphaMack on 2008-04-20
Here's a quick compilation of open source apps on OS X:
[www.opensourcemac.org](www.opensourcemac.org)

(Note that MacLibre installs outdated apps; use the list of apps packaged by those folks to guide you)

---

### Post by cprofitt on 2008-04-21
Apple is nothing more than a blood sucking leech as far as FOSS is concerned. Though I have not looked closely at what they contribute back out; they seem to guard their stuff more closely than Microsoft.

---

### Post by MONODA on 2008-04-21
> Amarok, Evolution Mail, Open Office, Firefox and Pidgin Internet Messenger.
amarok 2 will be installable on mac when it comes out :), leopard comes with Mail and ical which are quite nice (you can also install sunbird and thunderbird if oud like), neooffice is a mac openoffice, firefox and camino are available on mac, adium is like pidgin for mac. +1 for opensourcemac.com

---

### Post by Incense on 2008-04-21
You can get evolution for os x by clicking [here]("http://forge.novell.com/modules/xfcontent/file.php/evolution/builds/osx-evolution-2.6/evolution-2.6.pkg.tar.bz2"). More trouble then it's worth IMO. If you have enough RAM, I would just run a Linux install in a vm or boot camp. You can run most *nix software using FINK, but again, more trouble then it's worth. the opensourcemac link is a great resource.

---

### Post by PartisanEntity on 2008-04-22
> **Incense said:**
> You can get evolution for os x by clicking [here]("http://forge.novell.com/modules/xfcontent/file.php/evolution/builds/osx-evolution-2.6/evolution-2.6.pkg.tar.bz2"). More trouble then it's worth IMO. If you have enough RAM, I would just run a Linux install in a vm or boot camp. You can run most *nix software using FINK, but again, more trouble then it's worth. the opensourcemac link is a great resource.

I looked at the installation instructions for Fink, it was basically compile and then install. Where does the hassle part start? I am interested to know since I was planning on setting it up.

---

### Post by Incense on 2008-04-22
> **PartisanEntity said:**
> I looked at the installation instructions for Fink, it was basically compile and then install. Where does the hassle part start? I am interested to know since I was planning on setting it up.

Maybe it really isn't a hassle, I just never really got it to work properly. I can get FINK running just fine, and I can see the software in the repo, but I can never get anything to run after I install it. So maybe you'll have more luck then I do. I just run openSUSE in a VM under OSX, and that gives me everything I want. Let us know if it works out for you. Maybe I'll give it another go if I see some results from someone.

---

### Post by stream303 on 2008-04-23
I started to go the fink route a few years ago, and then thought, why not run the real thing without all the apple-weirdness?

Now I solely run Ubuntu Hardy on my G5 ppc iMac..

[http://cdimage.ubuntu.com/ports/](http://cdimage.ubuntu.com/ports/)

---

### Post by PartisanEntity on 2008-04-23
> **stream303 said:**
> I started to go the fink route a few years ago, and then thought, why not run the real thing without all the apple-weirdness?

Now I solely run Ubuntu Hardy on my G5 ppc iMac..

[http://cdimage.ubuntu.com/ports/](http://cdimage.ubuntu.com/ports/)

Do you know of any good tutorials for installing Ubuntu on a MacBook? (intel).

---

### Post by frootloop on 2008-04-23
Hi, don't know if this is helpful or not, but you dont need to buy a Mac if its just Photoshop and a few other things yo need to run.

Have a look here:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=1815&iTestingId=22395](http://appdb.winehq.org/objectManager.php?sClass=version&iId=1815&iTestingId=22395)

Apparently the new version fixes even the minor issues mentioned.

---

### Post by monomaniacpat on 2008-04-23
Thanks for all the new responses - I will review them later today. :)

---

### Post by Kobalt on 2008-04-23
> **PartisanEntity said:**
> Do you know of any good tutorials for installing Ubuntu on a MacBook? (intel).

With Hardy and Leopard it's really easy, just fire up Boot Camp to partition your drive and set the double boot through the EFI (just a couple of clicks actually), and then launch your Ubuntu install on the created partition. 
Regarding drivers you shouldn't worry either, I've had no problem with wifi or touchpad... only the webcam I don't know of, I don't quite use it.

---

### Post by PartisanEntity on 2008-04-23
> **Kobalt said:**
> With Hardy and Leopard it's really easy, just fire up Boot Camp to partition your drive and set the double boot through the EFI (just a couple of clicks actually), and then launch your Ubuntu install on the created partition. 
Regarding drivers you shouldn't worry either, I've had no problem with wifi or touchpad... only the webcam I don't know of, I don't quite use it.

What's the EFI? I am a complete OSX newb :)

---

### Post by Jackster on 2008-04-23
> **PartisanEntity said:**
> What's the EFI? I am a complete OSX newb :)

EFI is kinda like a replacement for BIOS. I think it was developed by Intel and as far as I know only Apple use it currently.

As for open source on the Mac, keep an eye out for openoffice.org 3, hopefully it will bring a good, fast, open source office suite to the Mac. Right now the only reasonable office apps for OS X are MS Office and iWork, the others are either slow or nasty to use or both. Of course the problem with Office and iWork is there's no ODF support which is not so great.

Actually, the lack of a good office suite which supports ODF was my main reason for installing Ubuntu on my Macbook ^_^

---

### Post by swisscow on 2008-04-24
> **Jackster said:**
> 

As for open source on the Mac, keep an eye out for openoffice.org 3, hopefully it will bring a good, fast, open source office suite to the Mac. Right now the only reasonable office apps for OS X are MS Office and iWork, the others are either slow or nasty to use or both. Of course the problem with Office and iWork is there's no ODF support which is not so great.

Actually, the lack of a good office suite which supports ODF was my main reason for installing Ubuntu on my Macbook ^_^

I have been searching for a good office suite and have resorted to NeoOffice, which is an offshoot of openoffice (I imagine it may die out when OO3 is ported to the Mac, but in the meantime...).

It does what I need, isn't too sluggish at all, and of course is open source.

---

### Post by stream303 on 2008-05-14
> **PartisanEntity said:**
> Do you know of any good tutorials for installing Ubuntu on a MacBook? (intel).

Run, don't walk, to the Ubuntu Apple forum.  I don't have any experience with the Intel Macs, but the forum and wikis are super active for both PPC and Intel alike.

---

### Post by PartisanEntity on 2008-05-14
> **stream303 said:**
> Run, don't walk, to the Ubuntu Apple forum.  I don't have any experience with the Intel Macs, but the forum and wikis are super active for both PPC and Intel alike.

Thanks, since posting my last post here, I managed to install Hardy on my Mac next to Leopard.

**Btw, those of you who have decided to go the Fink path, how do the Linux applications react? Are they sluggish? Any weirdness?**

---

