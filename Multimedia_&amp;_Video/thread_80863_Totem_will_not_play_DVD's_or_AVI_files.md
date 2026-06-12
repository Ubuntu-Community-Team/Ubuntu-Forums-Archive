---
title: "Totem will not play DVD's or AVI files"
date: 2005-10-23
forum: Multimedia &amp; Video
---

### Post by Oren on 2005-10-23
Hi all

A complete noob here (how many times have you heard this one before?
I have installed 'libdvdcss2' but I get the following eror:
"Could not read title information for DVD".

Then if I try and play the MPG file from the TS folder i get :
"There were no decoders found to handle the stream, you might need to install the corresponding plugins"

When I try AVI:
"There were no decoders found to handle the stream, you might need to install the corresponding plugins".

Help?????

Thanks, Oren

---

### Post by jasmuz on 2005-10-23
My recomendation is to ditch Totem, i never liked it anyways.
I personally use Xine or Mplayer...both are extremely good.

---

### Post by Vlammetje on 2005-10-23
Havn't got Mplayer to work myself (keeps hammering on about a font???) but Xine is a defenite recommendation.

Also, did you reboot after you installed dvdlibcss? If not, reboot first! ;)

---

### Post by lisje on 2005-10-23
[QUOTE=Oren]Hi all

A complete noob here (how many times have you heard this one before?
I have installed 'libdvdcss2' but I get the following eror:
"Could not read title information for DVD".

Then if I try and play the MPG file from the TS folder i get :
"There were no decoders found to handle the stream, you might need to install the corresponding plugins"

When I try AVI:
"There were no decoders found to handle the stream, you might need to install the corresponding plugins".

Help?????

Thanks, Oren[/QUOTE]


try installing the w32codecs && totem-xine

---

### Post by strongmantim on 2005-10-23
[QUOTE=lisje]try installing the w32codecs && totem-xine[/QUOTE]

I installed totem-xine fine. It uninstalled totem-gstreamer when I did this. It begins playing the DVD (Family Guy: Season 2, Disc 4), gets through the disclaimers (stupid FBI), and stops right before getting to the menu with a message like "Are you trying to run an encrypted DVD without libdvdcss?" I checked Synaptic Package Manager to see if I could get it from there, but it wasn't listed. Ideally, I'd rather have VLC or MPlayer working, but neither of those wants to do what I tell it, so I guess I will take what I can get.

---

### Post by JollyRoger on 2005-10-23
What is libdvdcss and where do I get it?  I also can't get dvds to play

---

### Post by Oren on 2005-10-23
Well....

I am afraid that untill this minute I still cannot get any joy.
I am trying to build MPlayer. It is so lengthy that I stopped for the moment.
Only so much terminal work I can stand for one evening.

What I do not understand is why, if I have all the codecs, will Totem not play the files? If only there was a way to say to Totem: " Here you are matey! The codecs are here - /xxx/bladibla/codecs. Now fetch them you M:-# rf:-# er. and :-# do as you are :-#  told!!!"

Also, I found lots of repositories but none seem to do the job... Oh well.
It is all fun and games isn't it girls? :razz:

---

### Post by John.Michael.Kane on 2005-10-23
[http://wiki.ubuntu-fr.org/doc/plf](http://wiki.ubuntu-fr.org/doc/plf)

has what you need

---

### Post by strongmantim on 2005-10-23
[QUOTE=SD-Plissken][http://wiki.ubuntu-fr.org/doc/plf](http://wiki.ubuntu-fr.org/doc/plf)

has what you need[/QUOTE]
Got anything like that for Hoary?

---

### Post by John.Michael.Kane on 2005-10-23
[https://wiki.ubuntu.com/RestrictedFormats?action=show&redirect=Codecs](https://wiki.ubuntu.com/RestrictedFormats?action=show&redirect=Codecs)


Search for the forum and the wiki for any other issues as most have been answered...

---

### Post by Oren on 2005-10-23
[QUOTE=SD-Plissken][http://wiki.ubuntu-fr.org/doc/plf](http://wiki.ubuntu-fr.org/doc/plf)

has what you need[/QUOTE]

Sorry, but no......
Downloaded, installed, rebooted! Totem says: "No way Andre...."

So.... has anyone got any other ideas how to get Totem to work?

Is there a config. file for Totem where you can point to the right codecs?

By the way I get the same problem wit the musoc player. When I try to play MP3 files.
mmmmmmm

---

### Post by John.Michael.Kane on 2005-10-23
install totem-xine . dont use totem-gstreamer.

---

### Post by Oren on 2005-10-24
Got VLC and it is working fine.

Next, can I uninstall Totem?

Thanks

---

### Post by strongmantim on 2005-10-25
I got VLC working, too. It's the only one that seems to be able to use all the codecs properly *and* provide sound. I have been loving VLC on OSX. Now I love it on Ubuntu!

---

### Post by Tech Provider on 2008-01-18
1.Just use XINE.
2.Determine your DVD-ROM DRIVE using : sudo lshw -short | grep DVD
3.Make a SimLink 

/dev/hda -> /dev/dvd

HDA = is the IDE DVD ROM ( it can be HDA/HDB/HDC )

---

### Post by ubuntu-freak on 2008-01-18
I wrote a how-to which includes help with DVD playback. You can play encrypted DVD's and make VLC the default DVD player. It has the best menu support.
 
[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)
 
Nathan

---

