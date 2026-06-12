---
title: "HandBrake-0.9.3-Ubuntu_GUI_i386 will not launch"
date: 2009-01-10
forum: Mythbuntu
---

### Post by ctucker10 on 2009-01-10
I'm running Mythbuntu 8.10 with all updates. I downloaded HandBrake-0.9.3-Ubuntu_GUI_i386 from Handbrake's website at [http://handbrake.fr/?article=download](http://handbrake.fr/?article=download)

When installing the package with GDebi Package Installer I don't get errors, but when I try to launch Handbrake GUI from the Applications => Multimedia menu nothing happens.

Troubleshooting, I tried to launch it from the command line and got the following error:

user@mythtv-desktop:~$ sudo /usr/bin/ghb
[sudo] password for user: 
/usr/bin/ghb: error while loading shared libraries: libgtkhtml-3.14.so.19: cannot open shared object file: No such file or directory

At this point I'm lost. What should I do next to try to get Handbrake GUI up and running on my mythbuntu 8.10 box?

I want to use Handbrake to transcode mythbuntu recordings to load onto an iPhone/iPod. Any help is appreciated.

---

### Post by rhpot1991 on 2009-01-11
> **ctucker10 said:**
> I'm running Mythbuntu 8.10 with all updates. I downloaded HandBrake-0.9.3-Ubuntu_GUI_i386 from Handbrake's website at [http://handbrake.fr/?article=download](http://handbrake.fr/?article=download)

When installing the package with GDebi Package Installer I don't get errors, but when I try to launch Handbrake GUI from the Applications => Multimedia menu nothing happens.

Troubleshooting, I tried to launch it from the command line and got the following error:

user@mythtv-desktop:~$ sudo /usr/bin/ghb
[sudo] password for user: 
/usr/bin/ghb: error while loading shared libraries: libgtkhtml-3.14.so.19: cannot open shared object file: No such file or directory

At this point I'm lost. What should I do next to try to get Handbrake GUI up and running on my mythbuntu 8.10 box?

I want to use Handbrake to transcode mythbuntu recordings to load onto an iPhone/iPod. Any help is appreciated.

Handbrake isn't really built for what you want to do with it.

I'd recommend having a look at MythExport: [https://help.ubuntu.com/community/MythExport](https://help.ubuntu.com/community/MythExport)

---

### Post by ctucker10 on 2009-01-11
> **rhpot1991 said:**
> Handbrake isn't really built for what you want to do with it.

I'd recommend having a look at MythExport: [https://help.ubuntu.com/community/MythExport](https://help.ubuntu.com/community/MythExport)

Thanks for the heads up to MythExport. I have started the process of getting mythexport installed and configured but it's not working "straight out of the box". I've already scanned one other recent thread on mythexport but don't see a solution to my particular problem.

I'll start a new thread since fixing Handbrake is no longer what I'm trying to figure out.

---

### Post by ctucker10 on 2009-01-11
> **ctucker10 said:**
> Thanks for the heads up to MythExport. I have started the process of getting mythexport installed and configured but it's not working "straight out of the box". I've already scanned one other recent thread on mythexport but don't see a solution to my particular problem.

I'll start a new thread since fixing Handbrake is no longer what I'm trying to figure out.

I guess I don't need to start a new thread after all... after looking at the mythbackend log I found that mythexport couldn't find my /home/mythtv/.mythtv/config.xml file.

The file was in another user's home directory. I copied it to the location where mythexport expected it to be and now MythExport is working!

I haven't had the chance to check out all of its features, but I'm happy with what I see so far. Thanks again.

---

### Post by rhpot1991 on 2009-01-11
> **ctucker10 said:**
> I guess I don't need to start a new thread after all... after looking at the mythbackend log I found that mythexport couldn't find my /home/mythtv/.mythtv/config.xml file.

The file was in another user's home directory. I copied it to the location where mythexport expected it to be and now MythExport is working!

I haven't had the chance to check out all of its features, but I'm happy with what I see so far. Thanks again.

No problem.  That is pretty much the most common problem, there is a little blurb about it in the bottom of the wiki.

---

### Post by zagor on 2009-01-12
> **ctucker10 said:**
> 
/usr/bin/ghb: error while loading shared libraries: libgtkhtml-3.14.so.19: cannot open shared object file: No such file or directory


in case you still want to give HabdBrake a try, check this long thread, especially [page 6]("http://ubuntuforums.org/showthread.php?t=992997&page=6").

also, check out the [mythshelljob ]("http://bentonroberts.com/personal/media-server/code/mythshelljob/")script, myth2ipod and [mythnuv2mkv]("http://web.aanet.com.au/~auric/?q=node/6").
other useful links might be:
[http://en.gentoo-wiki.com/wiki/TIP_MythTV_to_iPod]("http://en.gentoo-wiki.com/wiki/TIP_MythTV_to_iPod")
[http://mysettopbox.tv/phpBB2/viewtopic.php?t=9676&postdays=0&postorder=asc&highlight=m2iweb&start=0]("http://mysettopbox.tv/phpBB2/viewtopic.php?t=9676&postdays=0&postorder=asc&highlight=m2iweb&start=0")

---

### Post by ctucker10 on 2009-01-14
> **zagor said:**
> in case you still want to give HabdBrake a try, check this long thread, especially [page 6]("http://ubuntuforums.org/showthread.php?t=992997&page=6").

also, check out the [mythshelljob ]("http://bentonroberts.com/personal/media-server/code/mythshelljob/")script, myth2ipod and [mythnuv2mkv]("http://web.aanet.com.au/~auric/?q=node/6").
other useful links might be:
[http://en.gentoo-wiki.com/wiki/TIP_MythTV_to_iPod]("http://en.gentoo-wiki.com/wiki/TIP_MythTV_to_iPod")
[http://mysettopbox.tv/phpBB2/viewtopic.php?t=9676&postdays=0&postorder=asc&highlight=m2iweb&start=0]("http://mysettopbox.tv/phpBB2/viewtopic.php?t=9676&postdays=0&postorder=asc&highlight=m2iweb&start=0")

I manually installed Handbrake using the GDebi package installer. How do I uninstall it? I'm thinking it would be a good idea to remove this version before adding the repository and installing the other version... right?

---

### Post by Zack McCool on 2009-01-14
```
sudo apt-get remove handbrake
```

Should do the trick for you.  Then, add the repository and install the new packages

```
sudo apt-get install handbrake*
```

Works great here.

---

