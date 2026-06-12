---
title: "Is video really this broken at this late stage"
date: 2006-05-27
forum: Multimedia &amp; Video
---

### Post by goneskiing on 2006-05-27
This is really bad.  Video ran fine on Breezy with totem-xine and firefox plug-in.  Now under Dapper with totem-xine I get sound, no picture.  With totem gstreamer I get errors (cannot play....) - totally broken.  

Dapper was originally supposed to be a bug fix release after all the problems with Breezy due to tight release after xorg, gcc4, bad php configs, bad US repositories, etc.   Now Dapper is 6 wks late and wifi, video etc is not working.   Enterprise ready ?  NOT!  

Does anyone have video working ?  If so, what are secrets?

---

### Post by adamkane on 2006-05-27
The issue depends on the formats you're trying to play. Ubuntu does not ship with native support for proprietary formats.

You have to bend/break the law to play these formats, which includes installing proprietary codecs or installing mplayer/gxine with support for proprietary formats.

The fact that Totem was working on breezy was due to the efforts of users in countries with lenient copyright/fair use laws, who then shared their work with the rest of the Ubuntu user community.

---

### Post by nix4me on 2006-05-27
Multimedia will always be a mess.

Use mplayer and mozilla-mplayer and w32codecs.

Its the only working solution.

nix4me

---

### Post by goneskiing on 2006-05-27
I already installed the codecs - I'm simply trying to play wm.. videos off the web - again, same process that worked in Breezy for me.

---

### Post by adamkane on 2006-05-27
Describe in detail what you're trying to do, and we can get you up and running.

---

### Post by Anduu on 2006-05-27
I just followed the instructions on the restricted formats wiki and everything works fine

[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by goneskiing on 2006-05-27
I thought I did - 

totem-xime - okay sound, zero picture(not messed up - nothing)

the error msg from gstreamer was: 
"Totem could not play .... .wmv?MSWMExt=.asf "

---

### Post by adamkane on 2006-05-27
RestrictedFormats isn't always useful for playing web media.

---

### Post by Personatech on 2006-05-27
What's the problem with your WiFi?  I noticed moving to Dapper that my old Orinoco Silver card would no longer work but, lo and behold, my 802.11g Xterasys card now works fine (although it would not work under Breezy).

---

### Post by philetus on 2006-05-27
[QUOTE=goneskiing]This is really bad.  Video ran fine on Breezy with totem-xine and firefox plug-in.  Now under Dapper with totem-xine I get sound, no picture.  With totem gstreamer I get errors (cannot play....) - totally broken.  

Dapper was originally supposed to be a bug fix release after all the problems with Breezy due to tight release after xorg, gcc4, bad php configs, bad US repositories, etc.   Now Dapper is 6 wks late and wifi, video etc is not working.   Enterprise ready ?  NOT!  

Does anyone have video working ?  If so, what are secrets?[/QUOTE]

Do you have a folder in /usr/lib called win32, with essential codecs package:
[http://www.mplayerhq.hu/design7/dload.html](http://www.mplayerhq.hu/design7/dload.html)

---

### Post by philetus on 2006-05-27
I can play  WM9,Quicktime,Real

---

### Post by adamkane on 2006-05-27
The user is trying to get Totem to play his favorite media. It's already been made clear that mplayer and gxine will play most media without difficulties.

---

### Post by philetus on 2006-05-27
[QUOTE=adamkane]The user is trying to get Totem to play his favorite media. It's already been made clear that mplayer and gxine will play most media without difficulties.[/QUOTE]

I can play WM9,Quicktime,Real... in Totem-xine

---

### Post by joshrobinson on 2006-05-27
you wouldnt happen to be running the 64bit version would you? i know there is issues with wm9 with amd64 ubuntu

---

### Post by Anduu on 2006-05-27
I avoid Totem like the plague...nothing but problems.

Mplayer has been very good to me.

---

### Post by adamkane on 2006-05-27
gxine (xine-ui) via easylinux.info for me.

---

### Post by ramiro on 2006-05-28
I use mplayer + w32codecs and I haven't had an issue playing a single media file I've come across (not including flash)

---

### Post by goneskiing on 2006-05-30
thks for info - mplayer did not work for me (I get a beep and blank screen) but by loading the codec essentials package from mplayer site now totem-xine plays the video site I'm interested in.  However gstreamer still didn't work.  

I realize linux distros cannot provide the restrictive/proprietary codecs but it would be helpful if:
1) There is an unofficial main how-to web site for all these issues 
2) Ubuntu sorts out the totem-xine vs gstreamer vs mplayer issue - while it seems they are standardizing on gstreamer, that's the one that didn't work at all on my Dell Inspiron

---

### Post by nodgesoft on 2006-05-31
I went through [http://www.krazypenguin.net/Ubuntu_Dapper_Drake_6.06_Guide](http://www.krazypenguin.net/Ubuntu_Dapper_Drake_6.06_Guide) and video, sound, wifi and everythign else works perfectly.

-Matt

---

### Post by mattisking on 2006-05-31
Packages like Automatix go a long way towards shoring up these kinds of problems. Hopefully it will get released for Dapper soon. (if it's not already)

---

### Post by ramiro on 2006-05-31
automatix is pretty unsafe and dogy. I would recomment using EasyUbuntu instead

[http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/)

---

