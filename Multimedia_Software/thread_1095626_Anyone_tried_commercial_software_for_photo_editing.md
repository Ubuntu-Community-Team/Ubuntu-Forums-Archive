---
title: "Anyone tried commercial software for photo editing?"
date: 2009-03-13
forum: Multimedia Software
---

### Post by Buddy's Pal on 2009-03-13
I learned recently that Gimp and Picasa are not the only options for photo editing. The commercial photo editors/RAW converters Lightzone and Bibble are available for Linux.

Has anyone tried either of these? If so, what was your opinion? 

I would prefer to stick with Linux but need viable alternatives for photo editing. I haven't been able to get used to GIMP and its only 8 bit anyway. I'm trying to resist those who say I should just pack it in and go back to Windows/Photoshop.

Hopefully I'm not making a horrible gaffe by daring to mention software that's not open source on this forum?

---

### Post by lovinglinux on 2009-03-14
First you need to ask yourself if you need a image editor or a photography workflow program.

Lightzone and Bibble are workflow programs. These programs are more useful for photographers that shoot images in raw format and use them through the entire process of publishing high-quality photographs. They are comparable to Adobe Photoshop **Lightroom**, not Photoshop itself.

Gimp can also handle raw images like Photoshop and both are used to edit photos too, but they have more functions and tools useful for graphical designers.

If you just need to correct images captured by your camera, then I would choose a RAW Editor instead of GIMP. They are usually developed with the workflow in mind, which means they are designed to provide the better experience possible for editing a large amount of raw photos on a regular basis.

There are several RAW editors for Linux. I will look into this if you want. I haven't been photographing or editing photos for a while, so I will have to download and test a few to recommend the best option. I currently have RawStudio installed, but there are more options with more features out there.

---

### Post by Buddy's Pal on 2009-03-14
Thank you. I am just getting back into photography as a hobby after about 20 years. I have a digital SLR and have been photographing. But I haven't really begun serious processing. The sales people at my local photo shop seem to think that Photoshop is the only option.

My purpose is the improvement of images shot in RAW format. So based on your advice, I should be looking more at workflow software?

Thanks again! I will investigate.

---

### Post by lovinglinux on 2009-03-14
> **Buddy's Pal said:**
> Thank you. I am just getting back into photography as a hobby after about 20 years. I have a digital SLR and have been photographing. But I haven't really begun serious processing. The sales people at my local photo shop seem to think that Photoshop is the only option.

Well, some people still think IE is the only web browser available :D

Photoshop is the most powerful application for image editing, but not necessarily the best option for everyone or every situation. When digital cameras and the RAW formats became mainstream, several applications were developed focusing on the photographer workflow instead of a huge amount of editing tools. Lightroom was the Adobe response to this expanding market. It has some features of Photoshop and can be integrated with it for more complex tasks, but it is primarily designed for photography workflow.

> **Buddy's Pal said:**
> My purpose is the improvement of images shot in RAW format. So based on your advice, I should be looking more at workflow software?

Thanks again! I will investigate.

Yes. You will be much less frustrated and much more satisfied working with this kind of tool than with GIMP or Photoshop.

Some options:

[RawStudio]("http://rawstudio.org/") - open source, in the repos, [deb]("https://launchpad.net/~rawstudio/+archive/ppa")
[RawTherapee](RawTherapee) - proprietary
[blueMarine](blueMarine) - open source, [deb]("https://bluemarine.dev.java.net/files/documents/5150/71709/bluemarine_0.9.RC2b.3244_all.deb")
[UFRaw]("http://ufraw.sourceforge.net/") - converter or GIMP plugin, in the repos, [deb]("http://www.getdeb.net/app.php?name=UFRaw") 
[GTKRawgallery]("http://www.getdeb.net/app/GTKRawgallery") - open source, [deb]("http://www.getdeb.net/app/GTKRawgallery")

I haven't tested all of them. RawStudio works, but is kind of limited. Blue Marine has some really nice features, but has bugs and is not ready for production. RawThereapee looks a good option, but I can't find a deb file and it is closed source. GTKRawgallery have more features than RawStudio, but is not exactly designed for professionals, worth a try tho. UFRaw is a raw converter, but have more options than RawStudio.

EDIT: Interesting thread at [http://ubuntuforums.org/showthread.php?t=786445](http://ubuntuforums.org/showthread.php?t=786445)

---

### Post by lovinglinux on 2009-03-15
There is also [DigiKam]("http://www.digikam.org"), which is the most complete so far that I have tested. It has several essential tools for organizing image catalogs and supports raw editing.

The list of features is impressive. I recommend it.

---

### Post by hodge24 on 2009-03-15
I've looked at LightZone before, from [LightCrafts]("http://www.lightcrafts.com/") and was impressed. It handles RAW format from [most if not all modern DSLRs]("http://www.lightcrafts.com/products/raw/index.html"), and has features for handling workflow and photo editing. They also have some nice tutorials - video and PDF, in their [learning centre]("http://www.lightcrafts.com/learning/index.html").

Hope that helps :)

---

### Post by binbash on 2009-03-16
Lightzone is the only one i tried and it is cool

---

### Post by blur xc on 2009-11-21
> **lovinglinux said:**
> Well, some people still think IE is the only web browser available :D

Photoshop is the most powerful application for image editing, but not necessarily the best option for everyone or every situation. When digital cameras and the RAW formats became mainstream, several applications were developed focusing on the photographer workflow instead of a huge amount of editing tools. Lightroom was the Adobe response to this expanding market. It has some features of Photoshop and can be integrated with it for more complex tasks, but it is primarily designed for photography workflow.



Yes. You will be much less frustrated and much more satisfied working with this kind of tool than with GIMP or Photoshop.

Some options:

[RawStudio]("http://rawstudio.org/") - open source, in the repos, [deb]("https://launchpad.net/%7Erawstudio/+archive/ppa")
[RawTherapee]("http://RawTherapee") - proprietary
[blueMarine]("http://blueMarine") - open source, [deb]("https://bluemarine.dev.java.net/files/documents/5150/71709/bluemarine_0.9.RC2b.3244_all.deb")
[UFRaw]("http://ufraw.sourceforge.net/") - converter or GIMP plugin, in the repos, [deb]("http://www.getdeb.net/app.php?name=UFRaw") 
[GTKRawgallery]("http://www.getdeb.net/app/GTKRawgallery") - open source, [deb]("http://www.getdeb.net/app/GTKRawgallery")

I haven't tested all of them. RawStudio works, but is kind of limited. Blue Marine has some really nice features, but has bugs and is not ready for production. RawThereapee looks a good option, but I can't find a deb file and it is closed source. GTKRawgallery have more features than RawStudio, but is not exactly designed for professionals, worth a try tho. UFRaw is a raw converter, but have more options than RawStudio.

EDIT: Interesting thread at [http://ubuntuforums.org/showthread.php?t=786445](http://ubuntuforums.org/showthread.php?t=786445)


I trying to try GTKRawgallery, but my install from source failed, and I can't find that deb on getdeb.net.  I installed the get deb repository, and apt-cache search for gtkrawgallery (and other variations of the name) doens't turn up any results.

I've tried RAW Therapee, RawStudio, and Digikam, and they all suck to the point of begin 100% useless.  Maybe that's a bit harsh, mabye 98.2% useless...

I haven't tried Lightzone, their website is really lacking in showing off what their software looks like and how it works, though they have plenty of examples of "improved" photos (some don't look that great, imo).  I've tried Bibble and was very impressed with its speed and the Noise Ninja plugin.  If nothing better comes along, I'm probably going t plunk down my $$ on that one...  Until now, I've been using Lightroom in Vista to get by, and would live a Linux solution...

BM

---

### Post by punong_bisyonaryo on 2009-12-11
I use BibblePro and I swear by it. I've dried many of the free/open solutions that was mentioned in this thread, but none of them came close to the usability, and completeness of Bibble. I read in one of the benchmarks it's even faster than the standard Windows counterparts (Adobe Lightroom?). Buy it. It's worth the $100.

---

