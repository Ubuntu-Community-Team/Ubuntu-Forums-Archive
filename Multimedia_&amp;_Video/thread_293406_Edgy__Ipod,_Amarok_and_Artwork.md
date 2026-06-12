---
title: "Edgy : Ipod, Amarok and Artwork"
date: 2006-11-05
forum: Multimedia &amp; Video
---

### Post by tristure on 2006-11-05
Hi,

I'm using a fresh install of Kubuntu Edgy. I use Amarok to manage my Ipod, but I encounter a fatal showstopper : AMAROK DOESN'T TRANSFER THE COVER ARTWORK TO THE IPOD.

So I don't have the sexy tiny images on the iPod when I play songs. :-)

OK, it's not THAT serious, but man... I hate this :-).

What bugs me most is that I'm quite certain that it transferred them in Dapper... The image are there on some files I transferred on my wife's iPod with Dapper.

I don't really see what's going wrong here, but it's bugging me, so any help will be greatly appreciated. Thanks !

---

### Post by HeyGabe on 2006-11-06
I am in much the same position as you, however, it has been my experience that Amarok does indeed transfer the album arts, but not the ones that iTunes downloads. 
Use the Cover Manager (tools --> Cover Manager) to associate album artwork with song flies.  Be warned, however, that most of the Automagically discovered artworks (especially those based on incomplete or wrong tags) are going to be wonky.

---

### Post by Lord Illidan on 2006-11-06
My Ipod Nano does detect the cover art with Amarok in Edgy.

---

### Post by Bananenrepublikaner on 2006-11-08
I just had the same problem. I am using Dapper at the moment, but I think the solution will be pretty much the same. You have a 5.5G iPod, I assume?

To make Artwork work with Amarok - which is pretty convenient, as you can automatically import all the covers etc. - and one of the latest iPods you need:

- the latest version of gtkpod (0.99.8)
- the latest version of libgpod (0.4.00)
- you will need to meet the following requirements:
[http://amarok.kde.org/wiki/Media_Device:IPod#Artwork_not_working](http://amarok.kde.org/wiki/Media_Device:IPod#Artwork_not_working)

The error is quite simply that the 5.5G models don't create the Artwork DB themselves, as far as I understand. 

Now you need to:
1.) compile libgpod
2.) compile gtkpod
3.) if you want to: compile the latest version of Amarok
4.) open gtkpod and initialise your iPod, now recreate the file structure
5.) you will get asked the model type, chose your weapon ;)
6.) save, exit gtkpod
7.) open amarok and there you go, rightclicking the files and importing covers to your iPod should work

---

### Post by tristure on 2006-11-09
I don't know which Generation it is, but it's a fairly recent 80GB model... I assume the artwork DB exits because I already added artwork for some albums via iTunes.

Maybe it's related to that bug :" bug within libgpod makes artwork fail as soon as iPodControl/Artwork/ArtworkDB grows to more than 2 MB (~5000 songs)".

Yet the artwork db file is only 30kb... I don't know.

---

### Post by padre999 on 2006-11-21
I have the suspicion that this problem might be related to the latest Ipod Firmware Update...

Until yesterday I was happily adding albums with cover art to my Ipod 5G using amarok. But then yesterday somehow the Itunes Database File went corrupt and I ended up initialising my Ipod with Itunes.

For that I updated Itunes from version 6 to version 7.02. With the initialisation Itunes also upgraded the Ipod firmware (the updater seems to be integrated into Itunes now since version 7).

Ok. My Ipod worked again. Went back to Linux, added albums as usual. But... No artwork anymore. So I added some files with Itunes. There it works with the covers. Back to amarok, still same issue.

It seems to me that apple has changed the way artwork is saved and read on the Ipod, Therefore everybody else will have to adopt to the new "standard".:evil: 

Also that this thread came up just two weeks ago supports my suspicion.

If this should be true: Thank you Apple for trying so hard to convince me that your software is the only and best one.

---

### Post by ricesteam on 2007-01-17
I'm having similar problems. I went here to try to solve the problem:

[http://amarok.kde.org/wiki/Media_Device:IPod](http://amarok.kde.org/wiki/Media_Device:IPod)

which mentioned this point:

Recent iPod firmware versions (newer than mid 2006, and the firmware on 2nd gen iPod nanos, 5.5 gen iPods and the 2nd gen iPod shuffle) only create an empty iPod_Control/Device/SysInfo file. But this is used by libgpod for determining the kind of iPod you have. And libgpod has to know your iPod model for transferring artwork correctly. A work-around is to use a recent version of gtkpod for setting the iPod model manually (this sets the model version string in the SysInfo file).

But I'm not sure how to do that.  I installed the gtkpod from the repository for my Ubuntu 6.10.

---

### Post by njee on 2007-01-24
I was having a similar problem with my ipod that I updated to 1.2.1 I think I managed to find a fix.

Your sysinfo file is probably blank like mine, so you can manually type in the build number that will allow it to be recognised by libgpod and therefor add the artwork.

Go to this link

[http://ipodlinux.org/SysInfo](http://ipodlinux.org/SysInfo)

and copy the sysinfo for your model of ipod to your sysinfo file on your ipod. Add in your serial number and try adding the songs again.

I found I was able to have music with covers on the newest ipod firmware usting gtkpod, but i think it and amarok use the same backend.

---

### Post by enigma_0Z on 2007-02-04
> **ricesteam said:**
> I'm having similar problems. I went here to try to solve the problem:

[http://amarok.kde.org/wiki/Media_Device:IPod](http://amarok.kde.org/wiki/Media_Device:IPod)

which mentioned this point:

Recent iPod firmware versions (newer than mid 2006, and the firmware on 2nd gen iPod nanos, 5.5 gen iPods and the 2nd gen iPod shuffle) only create an empty iPod_Control/Device/SysInfo file. But this is used by libgpod for determining the kind of iPod you have. And libgpod has to know your iPod model for transferring artwork correctly. A work-around is to use a recent version of gtkpod for setting the iPod model manually (this sets the model version string in the SysInfo file).

But I'm not sure how to do that.  I installed the gtkpod from the repository for my Ubuntu 6.10.

Tis not too hard, but not for the faint of heart either...

You need to compile gtkPod 0.99.8 and libgpod 0.4.0 from source, if you can do that on your own, then the rest of the instructions are on my blog at [http://blog.pause.homelinux.net/index.php?/archives/8-Linux-+-Amarok-+-iPod-Nano-2nd-Gen-or-others-w-updated-firmware-+-WORKING-album-art.html](http://blog.pause.homelinux.net/index.php?/archives/8-Linux-+-Amarok-+-iPod-Nano-2nd-Gen-or-others-w-updated-firmware-+-WORKING-album-art.html)

---

### Post by peteraldred on 2007-02-10
Seems this may all be automatic now. Today I installed Amarok 1.4.5 from the Kubuntu repository here:

deb [http://kubuntu.org/packages/amarok-145](http://kubuntu.org/packages/amarok-145) edgy main

(More details and GPG key here: [http://kubuntu.org/announcements/amarok-1.4.5.php]("http://kubuntu.org/announcements/amarok-1.4.5.php") )

It brought with it libgpod 4.2, and since the upgrade it's been able to transfer album art.

Note: I had installed gtkpod 0.99.8 previously and used that to 'create ipod directories', which created the Sysinfo file, but this may not be necessary as Amarok itself now offers the option to change the model of the iPod. I haven't checked this as my iPod's working now and I don't want to jinx it!)

Note 2: Using gtkpod to generate the Sysinfo file, it wouldn't create it when there was already a sysinfo file in the directory (an earlier failed attempt had put it there). I renamed the old sysinfo file and gtkpod and Amarok were happy.

---

### Post by DNAspark99 on 2007-02-12
I've got a 2GB nano. Updated amarok to 1.4.5, libgpod to 4.2, and no matter what i try, I can not get album art working... wtf!

---

### Post by enigma_0Z on 2007-02-19
Does the "Ipod_Control/Device/SysInfo" exist?

---

### Post by ghandi69_ on 2007-02-19
> **HeyGabe said:**
> I am in much the same position as you, however, it has been my experience that Amarok does indeed transfer the album arts, but not the ones that iTunes downloads. 
Use the Cover Manager (tools --> Cover Manager) to associate album artwork with song flies.  Be warned, however, that most of the Automagically discovered artworks (especially those based on incomplete or wrong tags) are going to be wonky.

I have over 500 albums on my computer... and Amarok got every single album cover right on the money....

but then again... my tags are all correct.

---

