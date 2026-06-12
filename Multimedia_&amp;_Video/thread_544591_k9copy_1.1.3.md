---
title: "k9copy 1.1.3"
date: 2007-09-06
forum: Multimedia &amp; Video
---

### Post by 61811 on 2007-09-06
Novice Ubuntu 7.04 user.

The existing version of k9copy in Feisty is 1.1.0, and gives trouble (in my system) while copying a DVD disc. Hence, wanted to upgrade to the latest version 1.1.3. However, ran into several issues with that.

[http://www.debian-multimedia.org/](http://www.debian-multimedia.org/)
Used this site to add new repositories, and ran into all kinds of problems. Synaptic goes through the process of adding the new version of k9copy, but the Applications list does not show it has been installed. Don't understand the terms "sarge", "oldstable", "stable", "main", "etch", on this site. Have tried a couple w/o success.

From what I read 1.1.3 is stable. If so, why isn't it in the default Ubuntu repository?

Please indicate where to download 1.1.3 from, and if it is not a native Ubuntu package, how to install it.

Thank you.

---

### Post by indytim on 2007-09-07
You can download k9Copy from:

[http://sourceforge.net/project/showfiles.php?group_id=157868]("http://sourceforge.net/project/showfiles.php?group_id=157868")

You might want to list specifics of the problems (other than "unstable")  in your posting for further assistance.  You may have some other hardware issues that are affecting the performance of K9Copy on your system.

As far as installation procedures, search the Ubuntu forums for specifics on "how-to".  It's good practice on a skill you should become familiar with.

IndyTim

---

### Post by distroman on 2007-09-07
[https://help.ubuntu.com/community/BuildingK9CopyfromSource](https://help.ubuntu.com/community/BuildingK9CopyfromSource)
[https://help.ubuntu.com/community/K9Copy](https://help.ubuntu.com/community/K9Copy)
If you want to compile from source. 

Another useful command to know for dependencies. 

 ```
sudo apt-get build-dep k9copy
```

gl

edid
On a side note.
Maybe you want to take a look at winki.
[http://www.winki-the-ripper.de/](http://www.winki-the-ripper.de/)

---

### Post by 61811 on 2007-09-07
Thank you both for your responses. And, sorry if I wasn't very specific w.r.t. the exact nature of the errors I came across.

Background: I have installed quite a few packages in the past with Synaptic, and Update Manager w/o any errors. However, this is the first time via the Terminal.

Problem: Using your links below I downloaded/extracted V1.1.3. When I execute "./configure" in Terminal, I get errors. Please see attachments. Not being a Linux person, I am unable to decipher it. I understand that the problem may lie somewhere else, and not with the package. (FYI - all the development packages installed fine, except that my Synaptic does not list libdvdread3-dev. It has libdvdread-dev instead).

Obviously, w/o "./configure" finishing its job, I have not run "make" yet.

Please let me know what should I look for, to correct the issue with Configure in my setup.

Attachments:
1) File "terminal_debug.txt": Terminal output
2) File "config_debug_1.txt": Config.log (first portion of it to reduce file size)
3) File "config_debug_2.txt": Config.log (second portion of it to reduce file size)

---

### Post by distroman on 2007-09-08
Just a couple of questions :) 

1. Are you running Kubuntu? 2. What task are you trying to accomplish with k9copy?

It's just if you are running gnome there's a good chance for an alternative application for gnome that will do the same job just as good. 
Possibility's  dvd95 or xdvdshrink? Not sure.

If you are using Kubuntu or if you are really set on k9copy try the following.

```
sudo aptitude install docbook2x gettext-kde hspell kdelibs-data kdelibs4-dev kdelibs4c2a kdesdk-scripts libacl1-dev libarts1-dev libarts1c2a libartsc0-dev libaspell-dev libattr1-dev libavahi-qt3-1 libavahi-qt3-dev libjasper-1.701-dev liblua50 liblua50-dev liblualib50 liblualib50-dev libpcre3-dev libsasl2-dev libssl-dev libxml-namespacesupport-perl libxml-sax-expat-perl libxml-sax-perl lua50 libdvdread-dev kdebase-dev libqt3-mt-dev qt3-dev-tools libqt3-headers libjpeg62-dev build-essential checkinstall
```

Then please read the "README" in the k9copy directory. You can still use checkinstall instead of make install.

gl

ps
Think the Community Docs I linked to are outdated, sorry about that.

---

### Post by 61811 on 2007-09-10
1. Not running Kubuntu; Ubuntu (Feisty i386 - Gnome version).
2. Trying to rip DVD with 9 to 5 conversion.

Thanks for your responses. The HowTo at this link - [http://ubuntuforums.org/showthread.php?t=425802&highlight=k9copy](http://ubuntuforums.org/showthread.php?t=425802&highlight=k9copy),
came at the perfect time. It installed like a breeze, and k9copy 1.1.3 now runs smoothly.

I did start with DVD95 first, it being a Gnome application. However, on copying with K3b there were quite a few spots on the burnt DVD with blank images for less than a second, and then back to normal display. Also the picture quality wasn't good. Hence, I was trying to see how k9copy would fare. I would prefer to not use k9copy, because it means unnecessarily loading my system with KDE stuff.

Haven't tried xdvdshrink. Have tried DVD|RIp - not good quality video either.

K9copy gives good copy, but now have another issue. I will start a different thread for that, and close this one as SOLVED.

Thanks again for your suggestions.

---

