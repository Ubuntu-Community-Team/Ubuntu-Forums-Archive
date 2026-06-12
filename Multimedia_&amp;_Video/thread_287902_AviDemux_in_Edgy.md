---
title: "AviDemux in Edgy"
date: 2006-10-29
forum: Multimedia &amp; Video
---

### Post by abelthorne on 2006-10-29
It seems that since I updated from Dapper to Edgy, AviDemux doesn't appear anymore in the menu. If I try to run it from a shell I get these errors :

```
Locales for avidemux appear to be in /usr/share/locale

I18N : Fichier 

*******************
  Avidemux 2, v  2.3.0
*******************
 http://fixounet.free.fr/avidemux
 Code      : Mean & JSC 
 GFX       : Nestor Di , nestordi@augcyl.org
 Testing   : Jakub Misak
 FreeBSD   : Anish Mistry, amistry@am-productions.biz
Compiled for X86 Arch.

 LARGE FILE AVAILABLE : 1 offset
Initializing prefs
Instruction illégale (core dumped)
```

I've tried to uninstall and reinstall it (from the repositories).
Is there a problem with AviDemux in Edgy ?

---

### Post by sakis on 2006-11-02
First of all the version 2.3 is not in Edgy and you have to compile it yourself!
[I]
**[SIZE="2"]Edgy Eft[/SIZE]**
Spidermonkey cannot be installed straightforwardly on current Ubuntu 6.10 - and it seems it will not change until 7.04. In order to install it, you need to temporarily uninstall some important GNOME-related files. So it is advisable to save all you work, take a deep breath and do this only if you know what you are doing.[/I]
[http://www.avidemux.org/wki/index.php?title=Compiling_Avidemux#Edgy_Eft](http://www.avidemux.org/wki/index.php?title=Compiling_Avidemux#Edgy_Eft)

I'm not going to do it because it seems risky and complicated to me ](*,)

---

### Post by abelthorne on 2006-11-02
Yes, sorry, it was in fact a version upgraded from a repo. I came back to Edgy version and it works fine.

---

### Post by speedsix on 2006-11-17
So is it not possible to install the latest Avidemux on Edgy? Couldn't quite work out if it is on the avidemux wiki.


Thanks

---

### Post by speedsix on 2006-11-23
Anyone?

---

### Post by jocheem67 on 2006-12-07
Yes, you can.

Use the howto from their site, as in compiling it in Dapper. 
Spidermonkey won't install though but they've got a workaround...It's explained quite well.

I've got the 2.3 up and running with x264/faac/mp4 support and encoded a dvd, it's an amazing quality and the A/V is in sync.

This didn't work with mencoder....

It's an amazing program...

Make sure you've got the codecs you need already installed, with the "dev" packages, otherwise you need to run ./configure again.

---

### Post by abelthorne on 2006-12-23
I've tried to compile AVIDemux 2.3 as explained for Edgy but the compilation seems to fail (I get no executable in the end).

Is there a .deb package available that would work with Edgy ?

---

### Post by SadaraX on 2006-12-27
I will see if I can whip you up a DEB file when I got home. I have been compiling Avidemux from SVN regularly in Edgy, so I know it can be done.

---

### Post by SadaraX on 2006-12-28
[http://students.washington.edu/cdobrich/](http://students.washington.edu/cdobrich/)

There, you can download a deb file with a working copy of the Avidemux for 386/686 architecture. It was created fresh from the stable SVN files this morning.

---

### Post by mrphd on 2006-12-30
> **SadaraX said:**
> [http://students.washington.edu/cdobrich/](http://students.washington.edu/cdobrich/)

There, you can download a deb file with a working copy of the Avidemux for 386/686 architecture. It was created fresh from the stable SVN files this morning.

I downloaded this but when i try and run avidemux i get the error:

```
avidemux: error while loading shared libraries: libmozjs.so: cannot open shared object file: No such file or directory
```

Any ideas?

Thanks.

---

### Post by SadaraX on 2006-12-31
Oops, I forgot to include a library file in the deb file. 

You can just download the library file from my website, and put it into /usr/lib.

I have fixed the deb file. You can grab the file again from the website. 

You may need to remove the old version and install the new one (not sure).

---

### Post by mrphd on 2006-12-31
Thanks. I can run this now. Will give it a try later.

---

### Post by Rumpanzle on 2007-01-02
Thanks a lot for that Pack. I tried to compile earlier, but avidemux wanted gtk, which wanted cairo and pango, which wanted glib (which somehow didn't update the version number) and a hour later it still wouldn't make and made me lose fun in compiling. I gave in, just to find your pack!

---

### Post by SadaraX on 2007-01-02
> **Rumpanzle said:**
> Thanks a lot for that Pack. I tried to compile earlier, but avidemux wanted gtk, which wanted cairo and pango, which wanted glib (which somehow didn't update the version number) and a hour later it still wouldn't make and made me lose fun in compiling. I gave in, just to find your pack!

I am having some problems with my program, mostly related to SpiderMonkey. I am not sure if other people will have problems. If I fix the issue I will post an update

---

### Post by SadaraX on 2007-01-03
Alright I have fixed the SpiderMonkey error I was having and I have updated the files. I am not sure if you will need to reinstall the deb file itself or merely replacing the library into /usr/lib will be enough.

I recommend downloading the deb file and reinstalling it. It should work good now.

---

### Post by psantucc on 2007-01-07
Many thanks for making a .deb of 2.3 available.

---

### Post by mrphd on 2007-01-10
Is there a way of not making this version conflict with that in the repository? It keeps wanting to "update" to the older version...

---

### Post by zazen666 on 2007-01-13
You can use automatrix-that works really well

---

### Post by abelthorne on 2007-01-14
I have this problem too and had to block the repositories package so that it doesn't ask for update anymore.
Maybe it comes from the fact that SadaraX is build from a SVN version ?

---

### Post by SadaraX on 2007-01-14
Well, there is a way to pin a package with APT, however Synaptic does not seem to provide a nice way to do this. I know there are ways to do it, but I do not feel competent enough to describe the process.

The best thing I can do is set up an APT repository for Avidemux. I suppose I could even do builds of the development branch (version 2.4 with QT4) if people wanted. Now I just have to figure out how to setup and run an APT server on my webspace. It is normally port 80 access, and I am pretty sure it can be done. 

Anyone have a tutorial handy?

---

### Post by SadaraX on 2007-01-14
> **abelthorne said:**
> I have this problem too and had to block the repositories package so that it doesn't ask for update anymore.
Maybe it comes from the fact that SadaraX is build from a SVN version ?

I am not sure, but in the DEB control file I probably did not specify the version number correctly, so the other repositories automatically assume they have a more up to date version.

---

### Post by l:x on 2007-01-22
SadaraX: How do you make this debs? Are you using Checkinstall?

Thanks for the deb (I was able to compile it myself and build a deb with Checkinstall though).

---

### Post by SadaraX on 2007-01-22
I manually created the DEB file through using dpkg-build-deb... I never got checkinstall to work.

---

### Post by sakis on 2007-01-25
Here [http://www.getdeb.net/search.php?release=Edgy&keywords=avidemux](http://www.getdeb.net/search.php?release=Edgy&keywords=avidemux) you can download the deb of Avidemux 2.3.0 for Edgy

and here [http://www.getdeb.net/search.php?release=Dapper&keywords=avidemux](http://www.getdeb.net/search.php?release=Dapper&keywords=avidemux) the deb of Avidemux 2.3.0 for Dapper

enjoy :D

---

### Post by lamego on 2007-01-25
The following link is better:
[http://www.getdeb.net/app.php?name=avidemux](http://www.getdeb.net/app.php?name=avidemux)

It will show you the Dapper or Edgy version depending on the system you are browsing with (assuming you are using firefox).

---

### Post by sakis on 2007-01-25
> **lamego said:**
> The following link is better:
[http://www.getdeb.net/app.php?name=avidemux](http://www.getdeb.net/app.php?name=avidemux)

It will show you the Dapper or Edgy version depending on the system you are browsing with (assuming you are using firefox).
I didn't know that... thanks :)

---

### Post by SadaraX on 2007-02-19
Alright everyone, I have updated the Avidemux DEB package. There were no bug fixes or anything, but I found some mistakes I made when I created the DEB original.

First, were two copies of 'avidemux2', one in /usr/bin and one in /usr/share/bin. The 'avidemux2' in /usr/share/bin should be removed, since that is not where is it supposed to be. Sorry about that.

Second, I think I have fixed the version problem, so doing an apt-get upgrade should not give you errors or warnings anymore. 

Lastly, I looked over that file from getdeb.net. It is made by Christian Marillat, who has been around in Linux and Debian a LOT longer than I have. I suspect he knows what he is doing.

The big difference between his build of Avidemux and my build is that he has a lot of dependencies, since he has not built them into Avidemux. This is also the reason why his deb packages are smaller. I built all the dependencies, lame, ogg, libesd, etc into my Avidemux, so my files are larger. 

Either way, use whichever Avidemux file works better for you.

---

### Post by SadaraX on 2007-02-19
Well, I have added one more thing for those who want to try the latest Avidemux. 

[http://students.washington.edu/cdobrich/avidemux_2.4.0_unstable_i386.deb](http://students.washington.edu/cdobrich/avidemux_2.4.0_unstable_i386.deb)

That is current version of the SVN with the GTK interface. The PSP works now. The official statement by the developers concerning non-stable versions is "Do not use if you want to save what you make" basically meaning no there is no guarantee. But you can fool around with it and the PSP has been tested pretty thoroughly recently. We think it is fixed.

---

### Post by jocheem67 on 2007-02-22
Thanks man, gonna test it now.

I love this proggie!

---

