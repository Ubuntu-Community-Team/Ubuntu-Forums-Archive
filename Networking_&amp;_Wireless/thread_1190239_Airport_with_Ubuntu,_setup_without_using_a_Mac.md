---
title: "Airport with Ubuntu, setup without using a Mac?"
date: 2009-06-17
forum: Networking &amp; Wireless
---

### Post by skoolbus on 2009-06-17
Hello,

I'm new to the forums and wanted to ask a really mind-blowing question, does Ubuntu have any utilities (or Linux for the matter) to alter the Airport settings?

I have an Apple laptop that I use to update and alter the settings via the Airport Manager (whatever the app. is called). I'd like to install Ubuntu on the Apple.. but doing so, I'd no longer have access to the Airport Utility... not wanting to create a dual-boot.

So, just need an application to access and update/change/etc. the Airport setup of networks, and whatnot.

I'd be accessing the Airport (if it's possible) thru my other laptop, being a PC with Ubuntu 9.04.

Thanks!!!!!

---

### Post by Joeb454 on 2009-06-17
I haven't found any way to alter the settings without using a Mac either. If you can get the airport utility for Windows, there's a better chance you can change the settings that way.

Other than that, I don't see a way of doing this without dual booting your Apple machine :(

---

### Post by skoolbus on 2009-06-17
Yeah, figured such. I have Win XP on my Vbox within Ubuntu. I've never heard of a Windows app that connects to and is able to configure an Airport.

If anyone knows of such a thing... do tell. I then wonder if you can (thru virtualization) connect to an Airport from a Vbox XP partition thru Linux to an Apple Airport.

---

### Post by skoolbus on 2009-06-17
I just found this:
[http://packages.ubuntu.com/hardy/airport-utils](http://packages.ubuntu.com/hardy/airport-utils)

Going to give it a try. Hopefully there's a GUI, since I'm no command promp pimp.

Anyone who has used this method, love to hear your experiences so I don't kill my PC.

---

### Post by Joeb454 on 2009-06-17
Looks interesting - I'll give it a try as well :)

**Edit:** Note that you can install [airport-utils]("apt://airport-utils") either by clicking that link, or ```
sudo apt-get install airport-utils
``` to make sure you have the latest version :)

---

### Post by skoolbus on 2009-06-17
Cool, we can compare notes. I'll try it tonight... fingers crossed.

---

### Post by slyslug on 2009-06-23
Hello,

I just had this same problem.  What I found was that one can use wine to use the windows airport extreme configuration utility. Here's what I did....

Part 1 (the wine)
$ sudo apt-get build-dep wine
download wine src from winehq (no this is not gonna require a lot of work)
[http://winehq.com](http://winehq.com)
$ tar xf wine-1.1.20.tar.bz2
~/Desktop/wine-1.1.24$ cd wine-1.1.24/
./configure
make depend && make
make install (<-- I actually skipped this step, but it worked just fine)
$ sudo apt-get install cabextract

from there in the wine dir, there's a binary for wine.

Part 2 (Apple's utility)
download the airport express utility
[http://docs.info.apple.com/article.html?artnum=120273](http://docs.info.apple.com/article.html?artnum=120273)
I used 3.2 I don't know if that'll work for you, but I have one of the fancy new dual band airport extreme n jobbies and it seemed to be just fine with it.

Actually that didn't work.  so I downloaded the latest version, 5.4.1 (windows) and used that one's installer.  That was fine but it wrote out the files to the ~/.home/drive_c/program files/apple utility dir/admin.exe
so I used that, and I had to "connect to 'Other'" it did not see the airport using "scan" so fwiw, a little mod but it works fine. just changed a few settings, applied it and it worked.

Part 3 makin' it work...

$ ./wine ../AirPort\ Extreme\ Admin\ Utility\ 3.2/program\ files/Apple\ Computer/AirPort\ Extreme\ Admin\ Utility/Admin.exe 

I did all this as normal user. 

:D

---

### Post by bamajr on 2011-02-02
I've been in and out of this forum for a couple years, but never registered till today. This particular conversation has peeked my interest.

So I've been fighting this issue for quite a while. I have an Apple Airport Extreme Base Station. I originally configured it several months ago, before getting rid of my last micro$oft windoz computer.

Haven't been able to access the Base Station to configure it or make changes, since then.

---

### Post by bamajr on 2011-02-02
I've been fighting with the airport-utils package this whole time. I finally got somewhere with it today. I even posted a blog article "[Kubuntu: Configure an Airport Base Station in Linux]("http://bamajr.com/2011/02/01/kubuntu-configure-an-airport-base-station-in-linux/")" this evening about the steps I've gone through.

I can get the Airport Base Station Utility to launch, but I can't get it to stop looking for the Base Station on the default 10.0.1.1 IP Address.

---

### Post by bamajr on 2011-02-02
Keep in mind, I've been all over the internet looking for a way to access my Airport Extreme Base Station from my Kubuntu workstation. I've had wine installed for quite a while, but never thought to use it for this issue.

I downloaded the A[irPort Utility 5.5.2 for Windows]("http://support.apple.com/downloads/DL954/en_US/AirPortSetup.exe"). I right clicked on the .exe and changed the permissions for Read, Write and Exec to all checked (chmod 777 i believe). I then right clicked on the .exe again and chose "Open with Wine Windows Program Loader" and it immediately began the install.

When the install was completed, all I had to do was change the default IP Address so the AirPort Utility was looking in the right place.

It is now working great, though I haven't tested all the settings and features yet.

---

### Post by bamajr on 2011-02-02
I would still like to get Ubuntu's airport-utils to work correctly.

Also, there is no way I can be the first person to ask/suggest this, but if there is a utility that can be installed directly to Mac OS X, why can't it be ported as a native install for Ubuntu/Kubuntu?

---

### Post by teklife on 2011-02-26
well, for one it's proprietary, closed source software, so apple would have to want to do it themselves. 

what i have always wondered is, if projects like adium are open source, why is there not an adium for linux?? pidgin is what i use, but it's not even close.

---

### Post by leonardo.lenoci on 2011-03-16
I have lucid lynx on my netbook and I managed to use airport-utils to work with my airport extreme base station. Assuming that the wireless station is up and running, you can modify its settings in the following way.
First, you need to install java-gcj because either sun-java6 or openjava seem not to work with the airport utils. Then, you can run 

airport2-config

At this point, I tried to scan for apple devices but failed. Instead, by setting the device address to 10.0.1.1 and by inserting the correct passwd (top of the window), I could retrieve the airport settings and modify them according to my new preferences.

---

### Post by usefree.com.ua on 2012-06-20
The most right way, described by bamajr is useless and finished with [bug]("https://bugs.launchpad.net/ubuntu/+source/airport-utils/+bug/706623"). Ubuntu 12.04 64-bit, airport-utils 2-2, gcj-4.6-jre, retrieve settings well, but when try to update after any settings - in message window appear "error updating settings: null".
 So, the only way to configure airport extreme is to configure it from Windows(Mac) with airport utility installed.
 I just installed Wine with winetrics,
 choose wine simulate Windowx xp,
 download last [airport utility for windows xp]("http://support.apple.com/kb/DL795?viewlocale=ru_RU"),
mark downloaded file executable and install with wine.
 Installed well. I will post soon about how it can configure airport extreme base station.

---

### Post by nothingspecial on 2012-06-20
> **usefree.com.ua said:**
> 
 Installed well. I will post soon about how it can configure airport extreme base station.

Please do it in a new thread. This one is old.

---

