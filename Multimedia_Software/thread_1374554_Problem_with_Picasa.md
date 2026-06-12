---
title: "Problem with Picasa"
date: 2010-01-06
forum: Multimedia Software
---

### Post by mamboze on 2010-01-06
Hi,

I installed Picasa last year and it worked well but now I've got a problem with it. It will not start, instead giving an error message:
 
Warning
/dev/nvidia0 or /dev/nvidiact1 are not accessible. Picasa will crash if these files are not accessible. To fix, as root, please run
chmod 666 /dev/nvidia0 /dev/nvidiact1

I ran this command from the terminal and got: 

chmod: cannot access `/dev/nvidiact1': No such file or directory

I did a search and nvidia0 is located at /dev, but no nvidiact1

Also, I uninstalled and reinstalled Picasa using Synaptic. Didn't work!!  Just back to the Warning message.

I did a search thru the forums and located some other threads, but the solution seems a bit elusive. 

Any help much appreciated. :P

---

### Post by mamboze on 2010-01-07
Update:

Picasa from the repository removed and Picasa 3 installed. But still doesn't work. I have no idea why. 

I may have to use some other more or less equivalent app but I don't want to do that as I like Picasa.

---

### Post by mamboze on 2010-01-07
It looks as tho nobody can help which is surprising since Picasa is quite popular and I thought that somebody out there might have had the same problem as I have. 

I forgot to mention that I'm running 9.04

Even advice on an alternative would be welcome

---

### Post by Lars Noodén on 2010-01-08
> **mamboze said:**
> Even advice on an alternative would be welcome

Picasa is not yet available on Linux, it has to be run in WINE. Also, it spreads DirectX, which is aimed at replacing OpenGL with a proprietary graphics mode.  Promoting through use something which won't work with Free Software and Linux won't make sense to very many.  So there are strategic reasons for avoiding it, in addition to the practical ones you have yourself run into.  

If you are looking for photo managers, then here are some choices:

[Shotwell](http://www.yorba.org/shotwell/)
[Digikam](http://www.digikam.org/)
[Solang](https://launchpad.net/ubuntu/+source/solang)
[Fotoxx](http://kornelix.squarespace.com/fotoxx-gallery/)
[jBrout](http://jbrout.manatlan.com/)

---

### Post by cajunlibra on 2010-01-08
> **Lars Noodén said:**
> Picasa is not yet available on Linux, it has to be run in WINE. Also, it spreads DirectX, which is aimed at replacing OpenGL with a proprietary graphics mode.  Promoting through use something which won't work with Free Software and Linux won't make sense to very many.  So there are strategic reasons for avoiding it, in addition to the practical ones you have yourself run into.  

If you are looking for photo managers, then here are some choices:

[Shotwell](http://www.yorba.org/shotwell/)
[Digikam](http://www.digikam.org/)
[Solang](https://launchpad.net/ubuntu/+source/solang)
[Fotoxx](http://kornelix.squarespace.com/fotoxx-gallery/)
[jBrout](http://jbrout.manatlan.com/)

Um.  I beg to differ. Picasa 3 is available for Linux in beta:
[http://picasa.google.com/linux/](http://picasa.google.com/linux/)

It works fine for me. I have issues with the photo-printing.

---

### Post by Lars Noodén on 2010-01-08
> **cajunlibra said:**
> Um.  I beg to differ...

Ok.  If that's what floats your boat.  Picasa3 is still Windows-only, just like the earlier versions.  And is still missing OpenGL support, just like the earlier versions. 

Here is what the link says about system requirements for 3b:
[indent]
"*All downloads are approximately 30 MB: Picasa software (13 MB), **Wine (11 MB)** and Gecko engine (6 MB).*"[indent]
--[http://picasa.google.com/linux/download.html#picasa30](http://picasa.google.com/linux/download.html#picasa30)
[/indent]
[/indent]


Myself, I would recommend the new [Digikam](http://www.digikam.org/), but the others look very promising: [Shotwell](http://www.yorba.org/shotwell/), [Solang](https://launchpad.net/ubuntu/+source/solang), [Fotoxx](http://kornelix.squarespace.com/fotoxx-gallery/),and [jBrout](http://jbrout.manatlan.com/).

---

### Post by mamboze on 2010-01-09
Thnx Lars and cajunlibra,

I hadn't realized that Picasa used DirectX and so implicitly supports the MS empire. Given that I'm very happy to give it the toss and try one of the alternatives that Lars mentioned. 

Cheers to you both

---

### Post by Lars Noodén on 2010-01-09
@ mamboze : it's not so much that as it is that DirectX undermines the established graphics capabilities which are open standards based (OpenGL) and, as a result, cross-platform.  I guess that helps explain some possible motivations for the proposal to remove GIMP from Ubuntu 10.04.

---

### Post by volamoot on 2010-01-09
> **Lars Noodén said:**
> Ok.  If that's what floats your boat.  Picasa3 is still Windows-only, just like the earlier versions.  And is still missing OpenGL support, just like the earlier versions. 

Here is what the link says about system requirements for 3b:
[indent]
"*All downloads are approximately 30 MB: Picasa software (13 MB), **Wine (11 MB)** and Gecko engine (6 MB).*"[indent]
--[http://picasa.google.com/linux/download.html#picasa30](http://picasa.google.com/linux/download.html#picasa30)
[/indent]
[/indent]


Myself, I would recommend the new [Digikam](http://www.digikam.org/), but the others look very promising: [Shotwell](http://www.yorba.org/shotwell/), [Solang](https://launchpad.net/ubuntu/+source/solang), [Fotoxx](http://kornelix.squarespace.com/fotoxx-gallery/),and [jBrout](http://jbrout.manatlan.com/).

This is not completely true.
What is True is that Currently Google only Offers Support for Picasa on Windows Based Machines,
BUT... Picasa is available for Ubuntu Linux, due to constant Linux OS Changes Google is Unable to Provide Full-Term Support and there for is still considered "Beta."

As What was Said Earlier It is available at [http://picasa.google.com/linux]("http://picasa.google.com/linux")
(Please Note: Only Install Picasa At your own Risk)
Good Luck

---

### Post by Lars Noodén on 2010-01-09
@ volamoot : [WINE](http://www.winehq.org/) is a useful application which provides a Windows API for legacy applications.  This allows legacy Windows applications to run on Linux or other systems.  Thus, because any program that needs a Windows API to run is a Windows program, it is possible to identify Picasa as being Windows-only.

---

### Post by mamboze on 2010-01-31
> **Lars Noodén said:**
> @ mamboze :it's not so much that as it is that DirectX undermines the established graphics capabilities which are open standards based (OpenGL) and, as a result, cross-platform.  I guess that helps explain some possible motivations for the proposal to remove GIMP from Ubuntu 10.04.

@ Lars, I would have replied earlier but I've just come thru the rigors of a failed 9.04 to 9.10 upgrade and a subsequent clean install of 9.10. A big hassle with nvidia driver issues is still not completely resolved.  

However back to your comment, I'm a longtime GIMP user and I have wondered about the implications of removing it from the Ubuntu installation suite. Many of the posts at [Gimpusers.com]("http://www.gimpusers.com/news/2009-11-27/ubuntu-lucid-lynx-gimp-no-longer-by-default.html") seem unconcerned.

According to the intro to Gimpuser discussion, 'GIMP can of course be easily installed by using Ubuntus easy-to-use new Software Center or simply by typing "aptitude install gimp" in a terminal window'. So has much, if anything, changed?

---

### Post by Lars Noodén on 2010-01-31
> **mamboze said:**
> So has much, if anything, changed?

Yes.  Those without broadband are in effect denied the ability to do digital graphics work and photo editing.  You will find more than a few who are not jut unconcerned but worse over in the [other discussion](http://ubuntuforums.org/showpost.php?p=8712346&postcount=3).  Even for those with broadband, the defaults that come on the CD won't get changed by most and even then the defaults will be seen as an official endorsement.  

Which of the photo managers below did you settle on and what were the factors that raised it above the others?

[list]
[*][Shotwell](http://www.yorba.org/shotwell/)
[*][Digikam](http://www.digikam.org/)
[*][Solang](https://launchpad.net/ubuntu/+source/solang)
[*][Fotoxx](http://kornelix.squarespace.com/fotoxx-gallery/)
[*][jBrout](http://jbrout.manatlan.com/)
[/list]

---

### Post by philip5 on 2010-02-01
> **Lars Noodén said:**
> 
Which of the photo managers below did you settle on and what were the factors that raised it above the others?

[list]
[*][Shotwell](http://www.yorba.org/shotwell/)
[*][Digikam](http://www.digikam.org/)
[*][Solang](https://launchpad.net/ubuntu/+source/solang)
[*][Fotoxx](http://kornelix.squarespace.com/fotoxx-gallery/)
[*][jBrout](http://jbrout.manatlan.com/)
[/list]
If anyone in this thread is interested in the latest Digikam 1.1.0 for Karmic then you find it (and a bunch of other updated goodies) on my PPA on Launchpad. 

Enjoy!

---

