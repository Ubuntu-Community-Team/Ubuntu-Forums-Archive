---
title: "How Do I Update VLC To The Latest Version? Ubuntu 12.04 (64-Bit)"
date: 2015-09-16
forum: Multimedia Software
---

### Post by alexa3 on 2015-09-16
I click on the deb link on VLC's website and it downloaded 2.0.8. I've tried a number of different repositories and the highest I've gotten is 2.0.10.

---

### Post by papibe on 2015-09-16
Hi alexa3. Welcome to the forum ):P

I would install it from the official VLC ppa: [ppa:videolan/stable-daily]("https://launchpad.net/~videolan/+archive/ubuntu/stable-daily?field.series_filter=precise")

Here's some tips on how to install it: [How to update VLC to the latest version]("http://askubuntu.com/questions/105587/how-to-update-vlc-to-the-latest-version").

Hope it helps. Let us know how it goes.
Regards.

---

### Post by alexa3 on 2015-09-16
Thank you.

I've removed VLC and tried to reinstall it again, fresh install but I get an error:
" vlc : Depends: vlc-nox (= 2.0.8-0ubuntu0.12.04.1) but 2.0.8+git20140326+r49189+4+5~ubuntu12.04.1 is to be installed
       Recommends: vlc-plugin-notify (= 2.0.8-0ubuntu0.12.04.1) but 2.0.8+git20140326+r49189+4+5~ubuntu12.04.1 is to be installed
       Recommends: vlc-plugin-pulse (= 2.0.8-0ubuntu0.12.04.1) but 2.0.8+git20140326+r49189+4+5~ubuntu12.04.1 is to be installed
E: Unable to correct problems, you have held broken packages."

---

### Post by alexa3 on 2015-09-16
I've got it reinstalled and tried the repository you said but it doesn't go any higher than 2.0.10.

I'm trying to get 2.2.1 or is that possible?

---

### Post by mörgæs on 2015-09-17
If you do a fresh install of 15.04 you will automagically get VLC 2.2.0. Is that new enough? 

By the way, please don't double-post. Ask a moderator to jail your other thread.

---

### Post by Bucky Ball on 2015-09-17
> **mörgæs said:**
> By the way, please don't double-post. Ask a moderator to jail your other thread.

As above. Your other thread has been closed. If you are not getting a response after 12 or so hours, simply post 'bump' in your thread or update your progress with the issue. Either will bring your thread to the top of the 'New Posts' list.

Just wondering why you want the very latest possible version of VLC. Is there any particularly reason? The one in the repositories is officially tried and tested to work with your currently installed OS. The one you're installing is not.

If you're running 14.04 LTS, installing 15.04 is not the greatest idea. 14.04 is a long-term support release, supported until 2019, while 15.04 is an interim which is supported for another four months when you will need to upgrade.

---

### Post by shantiq on 2015-09-17
ok well from 12.04   to the latest version is over three years of dependencies so a very long time

You can try do a few things here see if it goes through

FIRST

remove all traces of your current version

```
 sudo apt-get remove --purge vlc
```

then remove the old deb this way OTHERWISE it gets picked up at the install stage

```
cd /var/cache/apt/archives
```

then ```
ls
```

see that you have vlc debs here and run

```
sudo rm *vlc*
```


NOW

use link Papibe indicated

For the master daily (*testing*) that is ppa:videolan/master-daily 
  Add it to your system
```
   sudo add-apt-repository ppa:videolan/master-daily
```
  Update and upgrade / install VLC
```
   sudo apt-get update && sudo apt-get install vlc
```



If it works good   if it does not   you will need to upgrade your distro first to get a higher version of VLC
But frankly what difference does it make? The VLC on 12.04 is fine for 12.04
I don't suppose there are brand-new incredible features in more recent ones that you are missing

Anyway try it and good luck

---

### Post by monkeybrain20122 on 2015-09-17
> **shantiq said:**
> ok well from 12.04   to the latest version is over three years of dependencies so a very long time

You can try do a few things here see if it goes through

FIRST

remove all traces of your current version

```
 sudo apt-get remove --purge vlc
```

then remove the old deb this way

```
cd /var/cache/apt/archives
```

then ```
ls
```

see that you have vlc debs here and run

```
sudo rm *vlc*
```


NOW

use link Papibe indicated

For the master daily (*testing*) that is ppa:videolan/master-daily 
  Add it to your system
```
   sudo add-apt-repository ppa:videolan/master-daily
```
  Update and upgrade / install VLC
```
   sudo apt-get update && sudo apt-get install vlc
```



If it works good   if it does not   you will need to upgrade your distro first to get a higher version of VLC
But frankly what difference does it make? The VLC on 12.04 is fine for 12.04
I don't suppose there are brand-new incredible features in more recent ones that you are missing

Anyway try it and good luck

Why do you need to remove the current version, moreover, to do it manually???

Also the master ppa has no package for Precise and the stable ppa only has 2.08 for precise.

---

### Post by monkeybrain20122 on 2015-09-17
I cannot find any ppa that offers vlc beyond 2.1.x for Precise. It is not too difficult to compile vlc from source but I suspect that it  wouldn't work for the current version of vlc because of outdated libraries in Precise (that's why no ppa package)

That is the catch of using a three year old lts. "Stability" comes at a  price. I would suggesting updating to 14.04 (do a clean install instead "upgrade") unless you have really old hardware that won't work with newer Ubuntu releases. While you may not need the latest and greatest but Precise is too much IMO. 3 years is a long time for open source and many applications in Precise are probably long pass end of life upstream (e.g LibreOffice)

---

### Post by mc4man on 2015-09-17
It may be possible to build vlc 2.2 on 12.04 though you'd need to statically link a number of dependant sources at newer versions. Could be a bit of work & trial & error..
As far as the Videolan ppa's - generally  worthless. The Master ppa is 6 months behind 3.x & basically dead, the stable ppa mainly has builds that aren't even upgrades to current Ubuntu repo builds.

---

### Post by alexa3 on 2015-09-22
> **Bucky Ball said:**
> As above. Your other thread has been closed. If you are not getting a response after 12 or so hours, simply post 'bump' in your thread or update your progress with the issue. Either will bring your thread to the top of the 'New Posts' list.

Just wondering why you want the very latest possible version of VLC. Is there any particularly reason? The one in the repositories is officially tried and tested to work with your currently installed OS. The one you're installing is not.

If you're running 14.04 LTS, installing 15.04 is not the greatest idea. 14.04 is a long-term support release, supported until 2019, while 15.04 is an interim which is supported for another four months when you will need to upgrade.

Thanks. I just tried it, unfortunately it gives me version 2.0.10. I wonder if I remove it completely and download ppa directly from VLC. I haven't tried that yet.
I like to have the up to date software. One thing is that VLC messes up when skimming 1080 videos, like there is no sound. I was wondering it it is fixed in the new version.

The only reason I do not upgrade Ubuntu to a newer version is because the folder view isn't available. The files go straight down instead of across if you know what I mean.

---

### Post by monkeybrain20122 on 2015-09-22
> **alexa3 said:**
> Thanks. I just tried it, unfortunately it gives me version 2.0.10. I wonder if I remove it completely and download ppa directly from VLC. I haven't tried that yet.

It wouldn't make a difference. You can check on the ppa's page to see what version is available for 12.04.

> 
I like to have the up to date software. One thing is that VLC messes up when skimming 1080 videos, like there is no sound. I was wondering it it is fixed in the new version.


That is going to be hard if you are using a very old Ubuntu. The dependencies would not be met for up to date software (unless you compile them and link vlc statically to them like mc4man said, but then the dependencies of the dependencies may be missing ..)

> 
The only reason I do not upgrade Ubuntu to a newer version is because the folder view isn't available. The files go straight down instead of across if you know what I mean.

I don't know what you mean. But you may checkout [https://launchpad.net/~mc3man/+archive/ubuntu/nauty-hacks1](https://launchpad.net/~mc3man/+archive/ubuntu/nauty-hacks1) to see if it addresses your problem.

---

### Post by alexa3 on 2015-09-22
> [QUOTE]The only reason I do not upgrade Ubuntu to a newer version is  because the folder view isn't available. The files go straight down  instead of across if you know what I mean.                            I don't know what you mean. But you may checkout [https://launchpad.net/~mc3man/+archi...u/nauty-hacks1]("https://launchpad.net/%7Emc3man/+archive/ubuntu/nauty-hacks1") to see if it addresses your problem.[/QUOTE]

I mean like how it shows them is looks like columns, but they're not columns. You can see more of your file. They dropped this view in Ubuntu 13.10 for some reason. I think that's my only complaint of the new Ubuntu distributions. It's a must have for me.

[ATTACH=CONFIG]264604[/ATTACH]

---

### Post by Bucky Ball on 2015-09-22
Well, 13.10 is dead in the water and no longer supported so you won't be going there anyway. 14.04 LTS is the latest LTS (long-term support) release supported until 2019. 15.04 until January next year.

---

### Post by alexa3 on 2015-09-22
I thought 12.04 was supposed to be support until 2017?

---

### Post by Bucky Ball on 2015-09-22
It is supported until 2017, but that is not going to get you near anything very new. The point I was making is that 13.10 is does not exist anymore so no point using it for comparisons. Things may have changed again in newer, supported versions.

---

