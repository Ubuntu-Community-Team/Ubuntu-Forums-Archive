---
title: "Youtube not working, frequent problem"
date: 2010-06-22
forum: Multimedia Software
---

### Post by Moustaffa on 2010-06-22
Hi all,

It seems that ubuntu really has trouble with staying up to date with flash.
I've seen several ways of fixing this but not one of them seems to work.

Whenever I load a clip is says that I have to upgrade Adobe Flash Player (I do this by putting libflashplayer.so in the /mozilla/plugins folder), but this doesn't help.

Trying to fix this through Ubuntuzilla also doesn't work for some reason...

Anyone who can help me out?

Thanks

---

### Post by gufide on 2010-06-22
Your machine is 32bit or 64?

---

### Post by gufide on 2010-06-22
Here I found something for for both architecture. go to [http://helpforlinux.blogspot.com/2010/05/install-flash-player-10-on-ubuntu-1004.html](http://helpforlinux.blogspot.com/2010/05/install-flash-player-10-on-ubuntu-1004.html)
and do what he does :wink:

---

### Post by Moustaffa on 2010-06-22
it's 32 bit
(although i should be able to install a 64bit OS. however, this didn't work..it just said i couldn't install the 64bit version)

i'm going to try out your link

---

### Post by irv on 2010-06-22
If you really want to understand videos on the Web, and this includes youtube. Read this:
[http://diveintohtml5.org/video.html]("http://diveintohtml5.org/video.html")

---

### Post by Cavsfan on 2010-06-22
There is no more 64 bit flash. I have a 64 bit system and I used the following link.
These 2 posts will solve your problem most probably:

_[http://ubuntuforums.org/showpost.php?p=9484165&postcount=5](http://ubuntuforums.org/showpost.php?p=9484165&postcount=5)_

Then there is a work around for the buttons not working. I only had to perform step 3 of the workaround.

_[http://ubuntuforums.org/showpost.php?p=9380613&postcount=2](http://ubuntuforums.org/showpost.php?p=9380613&postcount=2)_

---

### Post by Moustaffa on 2010-06-22
> **gufide said:**
> Here I found something for for both architecture. go to [http://helpforlinux.blogspot.com/2010/05/install-flash-player-10-on-ubuntu-1004.html](http://helpforlinux.blogspot.com/2010/05/install-flash-player-10-on-ubuntu-1004.html)
and do what he does :wink:

my god, it worked flawlessly!
Thank you so much for the link!

have a question though: let's say in a year I would have to do this again, will it work? It seems to me that if this conradmiguel.com site goes offline, this method won't work anymore.
How would the problem be solved then?

Thanks again, also thanks to the other poster for the extra documentation

---

### Post by lovinglinux on 2010-06-22
> **Moustaffa said:**
> my god, it worked flawlessly!
Thank you so much for the link!

have a question though: let's say in a year I would have to do this again, will it work? It seems to me that if this conradmiguel.com site goes offline, this method won't work anymore.
How would the problem be solved then?

Thanks again, also thanks to the other poster for the extra documentation

You shouldn't be using the 64bit version of flash, since it has a critical vulnerability and is not supported by Adobe anymore.

Install [FLASH-AID](http://flash-aid-extension.blogspot.com) extension for Firefox. It will remove conflicting plugins and install the proper flash version according to your browser architecture. 

If you don't use Firefox or prefer to fix the problem from command-line, then see the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

To fix the issue with the buttons:

```
gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
```

Add the following line before the last line of the file opened by the previous command:

```
export GDK_NATIVE_WINDOWS=1
```

Save and restart the browser.

---

### Post by Moustaffa on 2010-06-24
> **lovinglinux said:**
> You shouldn't be using the 64bit version of flash, since it has a critical vulnerability and is not supported by Adobe anymore.

Install [FLASH-AID](http://flash-aid-extension.blogspot.com) extension for Firefox. It will remove conflicting plugins and install the proper flash version according to your browser architecture. 

If you don't use Firefox or prefer to fix the problem from command-line, then see the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

To fix the issue with the buttons:

```
gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
```

Add the following line before the last line of the file opened by the previous command:

```
export GDK_NATIVE_WINDOWS=1
```

Save and restart the browser.

I tried it your way, and it allows me to play Youtube videos. However, another problem occurs: I can't interact with the video screen (magnify, pause, fast forward, ...). When I use the terminal again as suggested by the first poster I CAN interact, so I installed it again that way.

---

### Post by Cavsfan on 2010-06-25
> **Spr0k3t said:**
> A quick search came back with this:
[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/410407](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/410407)

WORKAROUND 1: Disable compiz
WORKAROUND 2: Remove flashplugin-nonfree / flashplugin-installer and  install from adobe
WORKAROUND 3: Open a terminal and enter:

gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer

Then add: export GDK_NATIVE_WINDOWS=1 before the last line of  text

Here is the bug report and the fix thanks to Spr0k3t.
This should fix that for you. I only had to do step 3 for all the buttons to work.

---

### Post by lovinglinux on 2010-06-25
> **Cavsfan said:**
> Here is the bug report and the fix thanks to Spr0k3t.
This should fix that for you. I only had to do step 3 for all the buttons to work.

I have already posted that, but for some reason it didn't work for the OP or he/she ignored the fix and installed the 64bit.

---

### Post by Cavsfan on 2010-06-26
> **Cavsfan said:**
> There is no more 64 bit flash. I have a 64 bit system and I used the following link.
These 2 posts will solve your problem most probably:

[http://ubuntuforums.org/showpost.php?p=9484165&postcount=5](http://ubuntuforums.org/showpost.php?p=9484165&postcount=5)

Then there is a work around for the buttons not working. I only had to perform step 3 of the workaround.

[http://ubuntuforums.org/showpost.php?p=9380613&postcount=2](http://ubuntuforums.org/showpost.php?p=9380613&postcount=2)

> **lovinglinux said:**
> I have already posted that, but for some reason it didn't work for the OP or he/she ignored the fix and installed the 64bit.

I had already posted the same solution (above) post #6 on page 1 a day before your 
post which included [COLOR=Red]your[/COLOR] FLASH-AID extension to FireFox fix (the first link in my post). 
The 2nd link is the bug and the workaround for the buttons not working. It may have been 
that I posted at the same time as the OP and he therefore didn't see it and although you posted
the same solution a day later, I guess you didn't see my post either. 

The OP did try going by your post #8 and if you look at post #9:

> **Moustaffa said:**
> I tried it your way, and it allows me to play Youtube videos. However, another problem occurs: I can't interact with the video screen (magnify, pause, fast forward, ...). When I use the terminal again as suggested by the first poster I CAN interact, so I installed it again that way.

Then I seen his post (#9) and posted the workaround again...

It's discouraging - everyone stepping all over each other posting the same solutions to the same problems.  
Sometimes, such as this, days later...
I guess we are all trying to help, but it seems to happen to me constantly...

---

### Post by lovinglinux on 2010-06-27
> **Cavsfan said:**
> I had already posted the same solution (above) post #6 on page 1 a day before your 
post which included [COLOR=Red]your[/COLOR] FLASH-AID extension to FireFox fix (the first link in my post). 
The 2nd link is the bug and the workaround for the buttons not working. It may have been 
that I posted at the same time as the OP and he therefore didn't see it and although you posted
the same solution a day later, I guess you didn't see my post either. 

The OP did try going by your post #8 and if you look at post #9:


Then I seen his post (#9) and posted the workaround again...

It's discouraging - everyone stepping all over each other posting the same solutions to the same problems.  
Sometimes, such as this, days later...
I guess we are all trying to help, but it seems to happen to me constantly...

I saw your post and totally agree with you. Usually, I don't post the same solution if it has already been posted, but I did this time because I had the impression that the OP ignored or missed the workaround, since it should have fixed the problem.

My last post wasn't intended to say "hey, I posted first", but I was trying to say that it seems the fix didn't work, which is unlikely, or that the user missed/ignored the fix and only installed FLASH-AID :)

---

