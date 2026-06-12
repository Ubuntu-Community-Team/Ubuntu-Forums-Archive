---
title: "iPod issues"
date: 2009-10-26
forum: Multimedia Software
---

### Post by white-zilla on 2009-10-26
I have an 5th gen ipod that I want to sync in ubuntu (9.10).  I used it with no problems on my windows machine.

Rhythmbox doesn't seem to have an extension for syncing but I can listen to my ipod through it.

I'm trying to use banshee but it is not detecting my ipod for some odd reason.  I have it mounted and everything.

Before I spend another hour on this issue can I get some ideas on a possible solution, or another program to use?  I read somewhere that there is a bug with banshee and 9.10 but it was an old report.

Thanks in advance

---

### Post by JugglinPhil on 2009-10-26
I use Songbird, in my eyes the best music player there is for Ubuntu. You can get it from here: [http://www.getdeb.net/app/Songbird](http://www.getdeb.net/app/Songbird)
Once you've installed it you can go to the bookmark 'Songbirf Add-Ons' (on the right panel) and then type ipod in the search bar. Install the one called 'Ipod Device Support' and you should be ready to go. :)
Greetings, JP

---

### Post by motorhead_1 on 2009-10-26
banshee doesn't recognize my ipod too...

---

### Post by iNaitvad on 2009-10-26
Hi, I think that Songbird is the best solution for you, its quite similar to iTunes (personally i think it is better). It has the option of Organize your Library, and that stuff... [http://www.getsongbird.com/](http://www.getsongbird.com/)

You should install de iPod addon to sync your iPod, there are a lot of addons, check them out.
Sorry for my bad english.

---

### Post by white-zilla on 2009-10-26
okay, I have installed songbird and the ipod device support and still no luck.  Songbird seems to have no clue that my ipod exsists.  any more guesses?

---

### Post by motorhead_1 on 2009-10-26
edit

---

### Post by white-zilla on 2009-10-26
gtkpod doesn't even recognize my ipod.  any more ideas?

---

### Post by white-zilla on 2009-10-26
holy crap, outta no-where gtkpod just recognized my ipod and so does songbird.

I simply unmounted the ipod and then re-mounted it when the program was running

I'll let you guys know if the sync is successful or not

---

### Post by motorhead_1 on 2009-10-26
installed songbird but it doesn't recognise my ipod, I've the ipod add-on enabled...

edit: I needed to install these packages and now works fine

```
The Songbird QA team tests Songbird on Ubuntu 8.10 32-bit.
glibc 2.3.4 or later
XOrg 1.0 or later
gtk+2.10 or later
fontconfig (also known as xft)
libstdc++6
```

---

### Post by 5nak3 on 2009-10-28
@white-zilla

May I ask what Songbird version you are using? I noticed you said you have Ubuntu 9.10 running. 

I also have 9.10 but my fathers ipod is not being picked up by songbird. Gtkpod does see the ipod, but I find that program to be poor in comparison to songbird.

If you could give me a few details about your setup and how you got it to work I'd be very thankful.

---

### Post by motorhead_1 on 2009-10-28
> **5nak3 said:**
> @white-zilla

May I ask what Songbird version you are using? I noticed you said you have Ubuntu 9.10 running. 

I also have 9.10 but my fathers ipod is not being picked up by songbird. Gtkpod does see the ipod, but I find that program to be poor in comparison to songbird.

If you could give me a few details about your setup and how you got it to work I'd be very thankful.
I've read there's a problem with the combination 1.2 version+add-on, in fact I'm running the beta 1.4+add-on.

---

### Post by themindfantastic on 2009-10-28
Songbird is nice and I use it, but until someone makes the ability to transfer to an ipod into something other than the music directory (I listen to a lot of audiobooks, and like to have them in the audiobook section on my ipod) it also doesn't (or so I have found) transfer the album art.  I have a 120gb ipod, album art sometimes helps when you got a lot of music on it.  So I have to use GTKPod which tends to crash unexpectedly at various moments while using it.  I have gotten in the habit of doing an action, save, doing another action, save because it seems to crash without rhyme or reason.  Annoying as well... annoying can be.  Apple really could just help out by making Itunes for linux which would solve all the issues but honestly it doesn't seem they are interetested or even care.

---

### Post by white-zilla on 2009-10-31
to answer the question, I'm using the most up to date version of songbird.

I have such a deep hatred for itunes, i'll put up with the BS songbird has

---

### Post by &#1057;&#1090;&#1088;&#1072;&#1085;&#1085;&#1080;&#1082; on 2009-10-31
There is no support for ipod nano 5g in libgpod, so no matter what app you use it will not work. 
You can follow the mailing lists or check their homepage from time to time, hopefully they will support it soon enough

---

### Post by chris.h on 2009-10-31
I got the last nano (chubby one, 3g?) and an ipod 5g, neither of which show up in songbird 1.4 with the latest ipod addon, even after an unmount/mount cycle. just tried 1.5 with the pre ipod addon, won't work either.

any ideas?

---

### Post by nexoncore on 2009-11-05
I am having the same issue, 9.04 detects fine, 9.10 doesnt detect. Using ipod nano 3G ( The Best looking one in my book )

Anyone know a perminent fix for this?

---

### Post by motorhead_1 on 2009-11-07
> **nexoncore said:**
> I am having the same issue, 9.04 detects fine, 9.10 doesnt detect. Using ipod nano 3G ( The Best looking one in my book )

Anyone know a perminent fix for this?
which version of Songbird are you running? have you checked all the required packeges are installed?

---

### Post by theApokalypsis on 2009-11-09
hey...

so going on that I cant connect my ipod with Banshee, Songbird, GTKPod and going from some stuff here...

[http://ubuntuforums.org/showthread.php?t=1304357](http://ubuntuforums.org/showthread.php?t=1304357)

Thinking its a bug, or something of the like :)

---

