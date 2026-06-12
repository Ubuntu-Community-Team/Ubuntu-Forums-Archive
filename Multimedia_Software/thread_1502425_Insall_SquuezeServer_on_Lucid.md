---
title: "Insall SquuezeServer on Lucid"
date: 2010-06-05
forum: Multimedia Software
---

### Post by pmbsa on 2010-06-05
Hi, I appear to have a package problem when trying to install squeezeserver on my lucid box (squeezeServer 7.5.0)

When I try to run the .deb install I get a package problem looking for libmysqlclient15-dev, when I then try to manually install that package I get the following.
The following packages have unmet dependencies:
  libmysqlclient-dev: Depends: libmysqlclient16 (= 5.1.41-3ubuntu12) but 5.1.41-3ubuntu12.1 is to be installed
E: Broken packages

unfortunately I have no clue how to manage these dependency issues, any help would be most appreciated.

thanks
Paul

---

### Post by BandD on 2010-06-05
Try going to System --> Administration --> Synaptic Package Manager.

Once it opens, in the lower left quadrant click on "Custom Filters"  Then in the scrool down list above the filter options choose "Broken".  It should show you any broken packages you have.  When you click on the packages listed there you should have the option of fixing/re-installing them.

See if that works.

---

### Post by pmbsa on 2010-06-05
Hi,I gave that a go but it tells me nothing is broken (least there is nothing in the list so I assume that means nothing is broken.

thanks
Paul

---

### Post by BandD on 2010-06-05
Well, looking more closely, it looks like the version of libmysqlclient-dev that squeezecenter is looking for is an older version than is available in the Lucid repositories.

How are you trying to manually install the libmysqlclient-dev package?

In a terminal try the following: ```
sudo apt-get install libmysqlclient-dev
```  That should download and install all the dependencies needed...

Then try the squeeecenter install.  I know squeezecenter works on Lucid because I have it up and running.  Though I don't recall having any dependency issues...

---

### Post by pmbsa on 2010-06-06
Hi, thats what I was doing that produced the output from the first post. Its really odd actually. I have lucid on a VM which worked perfectly but for some reason the installation on an actual box is giving me trouble.

---

### Post by BandD on 2010-06-06
I can't seem t find anyone with a similar problem via google.  Maybe try following the instructions from the squeezebox wiki found here  [http://wiki.slimdevices.com/index.php/DebianPackage]("http://wiki.slimdevices.com/index.php/DebianPackage").  

Wish I could help more...

---

### Post by keithweddell on 2010-06-06
> **BandD said:**
> Maybe try following the instructions from the squeezebox wiki found here  [http://wiki.slimdevices.com/index.php/DebianPackage]("http://wiki.slimdevices.com/index.php/DebianPackage").  


I've always installed SqueezeServer using these instructions so hopefully they will work for you too.

Keith

---

### Post by pmbsa on 2010-06-07
Hi, thanks for the attempts to help, I eventually threw in the towel and started from scratch. all seems fine now though, I just installed squeezeserver no problem.

---

