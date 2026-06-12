---
title: "Photo workflow"
date: 2011-01-17
forum: Multimedia Software
---

### Post by juju43 on 2011-01-17
Hello,


I'm trying to make a quick workflow for my travels and I want it to be mostly scripted.
It will be done on a Netbook (ubuntu 10.10 for now)

Here, the steps I have
1-copy picture from SD card to Image/yyyymmdd-text
either manually
either through rapid-photo-downloader.

The latter seems better but I have cases where it crashes with a 16G SDHC full of NEF+JPG

2- sorting with digikam: tag+rating, see the ones to generate pano with hugin

3- identify pictures without tag or without rating and put them aside.
no tools found. maybe exiflow, but have not found the right command.

4- add credits/location/country with exiv2

5- upload picasa/flickr/ftp/sftp depending on rating 


any ideas how to do this ? mainly step 3 ?

Thanks a lot

---

### Post by ngaio on 2011-01-17
> **juju43 said:**
> 
Here, the steps I have
1-copy picture from SD card to Image/yyyymmdd-text
either manually
either through rapid-photo-downloader.

The latter seems better but I have cases where it crashes with a 16G SDHC full of NEF+JPG


Report bugs here: [https://bugs.launchpad.net/rapid](https://bugs.launchpad.net/rapid)
Run the program from the command line with the -d option. Specify if you are downloading using a card reader or from the camera.

Thanks.

---

### Post by PhilGil on 2011-01-18
> **juju43 said:**
> any ideas how to do this ? mainly step 3 ?
You can search for untagged and/or unrated images using DigiKam's Advanced Search tool (at least you can in version 1.2.0).

---

### Post by juju43 on 2011-01-18
For the bug report, I already try to run with -dv but it crashes silently so I got nothing to help solving this bug ...

As  for digikam search, is there a way to script it in order to select/move pictures ? and launch it through cli ?

Thanks

---

### Post by ngaio on 2011-01-18
> **juju43 said:**
> For the bug report, I already try to run with -dv but it crashes silently so I got nothing to help solving this bug ...


Are you downloading from a camera or direct from the memory card using a card reader?

---

### Post by juju43 on 2011-01-18
Directly from a memory card with integrated reader in samsung n230

---

### Post by ngaio on 2011-01-18
> **juju43 said:**
> Directly from a memory card with integrated reader in samsung n230

Ok that sounds serious. Please report a bug with as much information as you can possibly provide. If necessary I can modify the code to output more information to help identify the cause. 

Thanks.

---

