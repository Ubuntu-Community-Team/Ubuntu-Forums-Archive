---
title: "can't play dvds?"
date: 2006-09-20
forum: Multimedia &amp; Video
---

### Post by wajvpitt on 2006-09-20
I'm new to Ubuntu / Linux.  

I've got my wirelss internet working (finally) and I've just got the sound going (not so difficult).  

I've just popped a DVD in to see if it works - Totem loads up and says that it can't play it because it doesn't have the right codecs.  

I've made sure that gstreamer is there and tried, just in case they're not, to install codecs - 

```
sudo apt-get install gst-plugins-base
```
and ```
-good
```

this didn't work, but ```
gstreamer0.10-plugins-base
``` and ```
-good
``` did - it said that there were none to update.  As to be expected...

Can it really be that Ubuntu doesn't ship with DVD playing capabilities?  What plugins do I need?

---

### Post by ajgreeny on 2006-09-20
Try libdvdcss2 in the repositories, that should do it for you.

---

### Post by wajvpitt on 2006-09-20
I've tried but it doesn't seem to work.  I enabled (I think!) the universe and multiuniverse repositories but I can't find it.  I looked in the synaptic installer list and did 'sudo apt-cache search libdvdcss' but it didn't come up with it.  

There's a page somewhere on the internet where you can download it manually but there are about a hundred versions and I've no idea which one to pick.  

I'm getting very frustrated by this whole experience - my plan was to learn about linux once I'd set it up.  At the moment I think I'm fumbling in the dark trying to learn as I set things up - not really ideal, especially when I'm never quite sure what the problems are.  

I found 'easyubuntu' to try to get everything done for me, but it doesn't seem to install properly and it won't run.  Story of my ubuntu life so far...


Any ideas.  Can provide specifics, messages etc.

---

### Post by doleslie on 2006-09-20
It seems that every bit of advice leads to additional frustration. The advice always assumes that the requestor has some brains. This may not always be the case. Some of us new users would just like to get past the point of installing what we asked for and then we can go on to bigger and greater things. 

In my case, I've tried to follow at least a half-dozen leads on how to get the dvd player to work. Besides leading me around the world several times, and trying this and that, nothing is still working. 

Can someone provide "true step-by-step instructions" for an absolute beginner using Ubuntu's Version 6.06? 

Thanks,

Dennis

---

### Post by The Warlock on 2006-09-20
DVD playing support isn't included in the Ubuntu repositories because of complicated legal reasons (short version: DVD cartel are a bunch of cocks). You need to enable an extra repository that has them. I use seveas and haven't ever had problems, so here you go. Edit your apt sources by typing in this command at a terminal:

```
sudo gedit /etc/apt/sources.list
```
(sidenote: the sudo command is nessessary when editing system files. It gives the command root (administrator) privleges. That's why you see it a lot here. It's not nessessary for most day-to-day activities, of course.)


Add the following line to the bottom:

```
deb http://mirror.ubuntulinux.nl dapper-seveas extras
```

Now, update your package list.

```
sudo apt-get update
```

Now, you'll need to install a package called libdvdcss2. This contains dvd decryption code. It might be illegal in the US, we're not sure. (note the .nl instead of .org at the end of the repository url above) But hey, who cares, right?

```
sudo apt-get install libdvdcss2
```

There's other interesting stuff there (like w32codecs, to play .wmv files) but we'll ignore it for now.

Also, gstreamer0.10 doesn't have DVD support yet, so let's get the other version of totem.

```
sudo apt-get install totem-xine
```

There, now DVDs should work fine.

EDIT: Someone should make a sticky about this.

---

### Post by doleslie on 2006-09-21
When I use the command: sudo apt-get install libdvdcss2, I get the following response:




hcsuser@Vista-Ubuntu:~$ sudo apt-get install libdvdcss2
Reading package lists... Done
Building dependency tree... Done
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate

What should I do?

Dennis

---

### Post by The Warlock on 2006-09-21
Did you add that line to /etc/apt/sources.list like I told you to? That repository provides libdvdcss2.

Hmm. Try typing in the following and trying (starting from apt-get update) again:

```
wget http://mirror.ubuntulinux.nl/1135D466.gpg
sudo apt-key add 1135D466.gpg
```

---

### Post by doleslie on 2006-09-21
Did you add that line to /etc/apt/sources.list like I told you to? 

     Yes!


That repository provides libdvdcss2.

Hmm. Try typing in the following and trying (starting from apt-get update) again:

Code:

wget [http://mirror.ubuntulinux.nl/1135D466.gpg](http://mirror.ubuntulinux.nl/1135D466.gpg) 

     This seemed to download files onto my system.

sudo apt-key add 1135D466.gpg

      This seemed to work?

Then I entered (again) "sudo apt-get install libdvdcss2"

  and that seemed to work.

I then opened Applications; Sound and Video; Movie Player. I then clicked on Movie and it showed the name of the DVD movie that was in the drive. When I clicked Play Disc 'Family_Favorites_01' on it, the following message appeared:

Totem cannot play this type of media (DVD) because you do not have the appropriate plugins to handle it.

Please install the necessary plugins and restart Totem to be able to play this media.

What might be wrong?

Dennis

---

### Post by ropers on 2006-09-21
Please refer to these pages:

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
[https://help.ubuntu.com/community/FreeFormats](https://help.ubuntu.com/community/FreeFormats)
[help.ubuntu.com/ubuntu/desktopguide/en_GB/common-tasks-chap.html]("https://help.ubuntu.com/ubuntu/desktopguide/en_GB/common-tasks-chap.html")

The short answer is, the makers of Ubuntu would love making everything work out of the box, but corporate obstructiveness, FUD, and legal threats^W^W blackmail prevent them from doing that. Most Linux developers are volunteers and as such don't have a legal department to defend their good rights against preposterous claims, power grabs and intimidation from big bad companies. If you want to do something about that, join the [EFF]("http://www.eff.org/")/[EFF Europe]("http://www.eff-europe.org/") and the [FFII]("http://www.ffii.org/").

--ropers

PS: The above Terminal commands are probably also correct, but doing what is described on the Restricted Formats page might be easier. You can also avoid having to type any Terminal commands at all that way. Click Applications--Add/Remove... and tick "Show unsupported applications" and "Show commercial applications". Or click on Advanced. If you do this and then search for the codecs you should be able to find them. Refer to the aforementioned webpage for more details.

---

### Post by doleslie on 2006-09-21
I've read all about what can't be done and what shouldn't be done. But I'm more interested in what can be done and what will be done. Thanks for the information.

Dennis

---

### Post by ropers on 2006-09-21
> **doleslie said:**
> I've read all about what can't be done and what shouldn't be done. But I'm more interested in what can be done and what will be done. Thanks for the information.

Dennis
Yes, understood. Go to [https://help.ubuntu.com/community/RestrictedFormats#head-74857744ddf74499c6447a19c7e94a2fcb382e0c](https://help.ubuntu.com/community/RestrictedFormats#head-74857744ddf74499c6447a19c7e94a2fcb382e0c)
for a list of codec packages you can install simply by doing what I wrote in my post scriptum (see my previous message).

I agree that it would be much nicer if Ubuntu told the user upfront --after or during the installation procedure-- that these-and-this are the problems and would immediately point the user at the information on how the user can  install the codecs anyway (if they so desire). That's neither endorsing binary blobs nor encouraging the user to install codecs some companies claim to own "intellectual property" rights to, it's just giving information. Unfortunately I'm a complete Linux n00b myself and I wouldn't even know how to properly suggest this to the proper maintainers of Ubuntu.

--ropers

---

### Post by Metacarpal on 2006-09-21
Hi

The basic Ubuntu install starts the Totem movie player off with the totem-gstreamer package.  Gstreamer hasn't quite figured out DVDs yet.  You'll want to:
```
sudo aptitude install totem-xine gxine libxine-main1 libxine-extracodecs w32codecs libdvdread3
```

When you do this, it'll warn you that it needs to uninstall totem-gstreamer and ubuntu-desktop.  Don't panic - the ubuntu-desktop package doesn't actually do anything.  It's just there to make initially installing all of the Ubuntu desktop components easier.  Once they're on, you don't need it anymore.

---

### Post by Metacarpal on 2006-09-21
> **ropers said:**
> Yes, understood. Go to [https://help.ubuntu.com/community/RestrictedFormats#head-74857744ddf74499c6447a19c7e94a2fcb382e0c](https://help.ubuntu.com/community/RestrictedFormats#head-74857744ddf74499c6447a19c7e94a2fcb382e0c)
for a list of codec packages you can install simply by doing what I wrote in my post scriptum (see my previous message).

I agree that it would be much nicer if Ubuntu told the user upfront --after or during the installation procedure-- that these-and-this are the problems and would immediately point the user at the information on how the user can  install the codecs anyway (if they so desire). That's neither endorsing binary blobs nor encouraging the user to install codecs some companies claim to own "intellectual property" rights to, it's just giving information. Unfortunately I'm a complete Linux n00b myself and I wouldn't even know how to properly suggest this to the proper maintainers of Ubuntu.

--ropers

This is something that is, in its own way, being addressed in the next Ubuntu release, due out at the end of October.  In that one, if you go to play a file you don't have plugins for, it'll just tell you so and help you get them if you want them.

---

### Post by ropers on 2006-09-21
> **Metacarpal said:**
> This is something that is, in its own way, being addressed in the next Ubuntu release, due out at the end of October.  In that one, if you go to play a file you don't have plugins for, it'll just tell you so and help you get them if you want them.
Ah. Super. Thanks! :)

---

### Post by wajvpitt on 2006-09-22
That sounds a lot better: if the programs could fetch codecs for the user and the user merely click a box agreeing to doing something possibly naughty.  

I got Automatix to work in the end and I'd hope that it's sorted everything out.  Now Totem and Media player seem to recognise that there is a DVD, try to start playing it, flash a blue screen and then shut down.  This isn't supposed to happen?  

I think I may have installed too many packages - all the ones I could get my hands on (to cover my back).  Can someone explain how to list all the relevant packages?  

At the moment I know how to get one and install it - if it's already there it'll tell me so.  

Thanks for all the help.

I think it'd be very useful for potential new users to have some specific caveats - I think there's a thread that runs something like, 'don't install Ubuntu unless you're willing to spend some time setting it up.' Fair enough, but -  

It'd be nice to have a thread that says:  FAO new users:

a) Wireless support is poor.  *If* you have problems, this is where to look...

b) You need to fetch codecs to play mp3s, DVDs etc.   Here is how to do this...

c) Any (d) other (e) popular and well documented issues

etc. etc.

---

### Post by Metacarpal on 2006-09-22
Interestingly enough, it was the emergence of (and subsequent virtual userbase-wars between) installers like Automatix and EasyUbuntu that made the new codecs-retrieval (Common Customizations) an objective for Edgy.

---

### Post by Monkus on 2006-09-23
Ok, I'm on a Gateway MX6121. I did the old apt-get totem-xine and libdvdcss2 and totem plays DVD just fine. All I had to do was adjust the levels (it was too bright, contrasty, saturated, etc.) and it works just fine.

---

### Post by DarkN00b on 2006-09-23
That is correct.  Totem-gstreamer will not work with libdvdcss.  I could watch DVDs after I installed Totem-xine along with libdvdcss.  Everything worked fine after that.  

The only gripe I have is that whenever watching a movie fullscreen, there are lines in the picture anytime the camera moves quickly.  I assume this is caused by the way the movie is interpolated to higher rez.

---

