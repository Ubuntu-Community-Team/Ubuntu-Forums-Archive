---
title: "[SOLVED] [vlc]choosing  .deb packages to install them later offline"
date: 2007-09-07
forum: Multimedia &amp; Video
---

### Post by offline on 2007-09-07
I am totally new to ubuntu. I have the original ubuntu 6.06 LTS cd, a windows pc(online) and a newly set up ubuntu 6.06LTS PC(offline at another location) 

My questions are:

1) is there any version of vlc contained(hidden somewhere) in that original ubuntu 6.06 LTS cd and how can I install it. If I can get it installed will it be sufficient to play dvds or I will have to install some codecs, libraries or "regionset"s? where from and how?

2)If there is no vlcat the cd. Let say I use .deb package files(to install vlc offline) and will get them(with a window machine)  from 

[http://packages.ubuntu.com/dapper/graphics/vlc]("http://packages.ubuntu.com/dapper/graphics/vlc")

Every package has a list(red buttons etc) of --as I understand--prerequisites. But if you choose one of them there are OTHER prerequisites for it **and so on**. A never ending list. Which ones should I choose to be sure that

a)vlc will play dvd, vcd
b)vlc will play **avi with subtitles**
c)vlc show english and greek subtitles

---

### Post by Bablefish on 2007-09-07
You can get it from here [www.getdeb.net](www.getdeb.net)

---

### Post by offline on 2007-09-08
Thanks Bablefish. Although the site you posted doesn't have any version of vlc, it's a nice useful site with many .deb packages(applications) sorted in different categories...I hope they are complete and there is no need of any...dependencies.

For any people in my situation, I will try to use the following links to get over  of my problem and time will tell if I can do it:

[http://packages.ubuntu.com/dapper/graphics/vlc](http://packages.ubuntu.com/dapper/graphics/vlc)

[http://cutlersoftware.com/ubuntuinstall/#installing_a_package_manually](http://cutlersoftware.com/ubuntuinstall/#installing_a_package_manually)

I will use Synaptic Manager and add cd as extra repository. Then try to install the packages(that I've  downloaded to a cd from the first page of the first url) god knows with which order?...And I hope synaptic will tell which .deb packagesare missing?

ps

That didn't work. Probably the cd has to be of a certain "format"(key...).

---

### Post by offline on 2007-09-14
I've tried another way:

I downloaded and then double-clicked one by one every file listed at(the first page(home))

 .[http://packages.ubuntu.com/dapper/graphics/vlc]("http://packages.ubuntu.com/dapper/graphics/vlc")

Not Synaptic but some other application (in ubuntu 6.06) installed them. Whenever there was a dependency, if present in the above list then I installed it. If some .deb package was required as a dependency and wasn't there I searched 

[http://packages.ubuntu.com/]("http://packages.ubuntu.com/")

BUT, in the end there were mainly 2 files to install(hopefully):

wxlvc and vlc.

Whenever I double clicked wxvlc package it asked for vlc. And whenever I clicked vlc it asked for wxvlc .

DEAD END.

This must be what they call circular dependency. Maybe the following link will solve the problem. I'll try.

[http://ubuntuforums.org/showthread.php?p=1890363]("http://ubuntuforums.org/showthread.php?p=1890363")

---

### Post by simosx on 2007-09-16
For codec support see
[http://simos.info/blog/archives/566](http://simos.info/blog/archives/566)

You can add VLC from Synaptic if you add the extra repositories (universe).

There is a Greek Ubuntu community at [http://www.ubuntu-gr.org/](http://www.ubuntu-gr.org/)

---

### Post by offline on 2007-09-18
I did 

dpkg -i vlc wxvlc

vlc program worked but"unconfigured". I couldn't install ANY other programs(broken cache) but terminal said some vlc-ALSA  plugin was needed. So I opened terminal and 

 dpkg -i vlc wxvlc vlc-ALSA( something like that)

Now everything is ALMOST fine vlc is installed ok.:popcorn:


THE PROBLEM:
-------------------

The problem now is I can't get  greek srt subtitles being displayed(same thing with the totem player). I've put some free greek fonts(true type) in the ubuntu  fonts folder. I added ISO8859-7 and greek windows character encoding and utf ... to the text editor, I changed player font settings etc nothing happened.
. I can display english subtitles. These srt files are first saved in my windows machine. I save them as  utf8 or tried greek iso. Then transferred it to ubuntu machine. No displaying. I must add here that my ubuntu pc doesn't have greek support and trying to get it I accidentally removed english support. Now the language selector window(system administration>language support) is blank! I neither have any selection choices in the login screen>languages besides system default and some strange "english something".

---

### Post by saverjack on 2008-06-19
hey guys here is the integrated package of all the dependencies & the dependencies of dependencies of the vlc player you can download it frome here

[http://www.thinkdigit.com/forum/showthread.php?t=73538&highlight=offline](http://www.thinkdigit.com/forum/showthread.php?t=73538&highlight=offline)

have great  fun 
save time by downloading from this link & instead of going to vlc homepage

Bye..

---

