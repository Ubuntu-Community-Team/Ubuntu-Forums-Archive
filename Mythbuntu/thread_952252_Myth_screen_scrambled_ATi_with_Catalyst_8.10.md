---
title: "Myth screen scrambled ATi with Catalyst 8.10"
date: 2008-10-18
forum: Mythbuntu
---

### Post by squish102 on 2008-10-18
I have a problem with a new install of mythbuntu. I am running the Ati Catalyst drivers for my video card. Everything works as expected (mplayer full screen) except mythtv-setup and mythfrontend.

They are both scrambled when they start up. I can still see that something is changing on the screen, but it is streched sideways (check picture) 

Please help :)

PS it works fine if i do a 'mythfrontend -w -geometry 1024x768' (bring it up in window smaller than my display)


Relevant info and attachments.

New 8.04.1 mythbuntu installation
Ati HD 3200 onboard video card connected with DVI to Dell 19" lcd 
ATI Catalyst™ 8.10 Proprietary Linux x86_64 

Xorg.cong [link]("http://pastebin.com/m5e5c4ef0")

A picture of my screen [linky]("http://www.flickr.com/photos/78287460@N00/2952413351/")

Output of mythfrontend [linky2]("http://rafb.net/p/WSUMdo25.html")

---

### Post by jetpeach on 2008-10-21
my situation is basically the same, with mythtv being scrambled - although i'm not sure if it's because i switched video cards from an older ATI card to an HD3650, or because I upgraded from catalyst 8.9 to 8.10.... i could downgrade to be sure i suppose.

please let me know what you find out, if anything, i'll be looking for a fix too.

i found that if i ran it from command line using

mythfrontend -w -geometry 1024x768
would let it run right.

so then i could  get to my configuration at least (i couldn't see how to configure it at all when it was scrambled.) now to guess what might fix it in full screen mode...

---

### Post by squish102 on 2008-10-21
I have given up for the time being, which is sad because I bought this mobo for the hdmi, and I am looking for a cheap fanless nvidia card.

I found another interesting thread [http://www.mythtv.org/pipermail/mythtv-users/2008-August/229872.html]("http://www.mythtv.org/pipermail/mythtv-users/2008-August/229872.html")which seems to be the same problem. the -geometry seems to be something that has helped them too. It worked for me to also see my screen and know that the video plays back fine in windowed. I will reply here if I get anything else worked out.

---

### Post by JugeHuge on 2008-10-21
I have had this problem since catalyst 8.6 to 8.10
So i'm using repository version of fglrx

---

### Post by Wintervenom on 2008-10-21
I have the same problems, except with full-screen OpenGL applications and games.  It doesn't matter if I use the new X.org and the beta Catalyst or the old X.org and the current 8.10 Catalyst -- it does the same.

If it put the application into windowed mode, then it will display properly.

---

### Post by ~~MAINFRAIME²~~ on 2008-10-24
I have the same problem with fglrx 8.7 on a x64 system with a onboard x1250 where I have a PAL-TV connected and use a resolution of 800x600 to get fullscreen display of the frontend use the geometry switch like this "mythfrontend.real -geometry 801x601" just add one pixel for x and y resolution this way I have fullscreen and no corruption and the backend setup I can only open it from the mythcontrolcenter else it is not displayed correctly.

Maybe this helps :)

I think I have it since 8.7 but I'm not 100% sure.

---

### Post by codered867 on 2008-10-24
I believe that what finally did to fix this problem for me was defining, in the xorg.conf file exactly what screen resolution I was using. I had a add this to the screen section: ```
Section "Screen"
  Identifier  "Default Screen"
  Device    "780g"
  Monitor   "Generic Monitor"
  DefaultDepth  24
  # Add this section to set the resolution.
  SubSection "Display"
    Depth   24
    Modes   "1366x768"
  EndSubSection
EndSection

```

Let me know if this fixes it for your I'm curious as to if this is the reason it started to work for me or I just got lucky

---

### Post by Wintervenom on 2008-10-24
Nope.  :(

---

### Post by shortyjacobs on 2008-11-02
> **codered867 said:**
> I believe that what finally did to fix this problem for me was defining, in the xorg.conf file exactly what screen resolution I was using. I had a add this to the screen section: ```
Section "Screen"
  Identifier  "Default Screen"
  Device    "780g"
  Monitor   "Generic Monitor"
  DefaultDepth  24
  # Add this section to set the resolution.
  SubSection "Display"
    Depth   24
    Modes   "1366x768"
  EndSubSection
EndSection

```

Let me know if this fixes it for your I'm curious as to if this is the reason it started to work for me or I just got lucky
This didn't work for me.  The Geometry fix worked though, as long as I don't enter my actual screen size.  For example, if I run ```
mythfrontend -w -geometry 1920x1080
```
it scrambles, but if I run
```
mythfrontend -w -geometry 1919x1079
```
it starts up nicely in windowed mode

Is there a way to run it NOT windowed at 1919x1079???

---

### Post by tgm4883 on 2008-11-02
There is a bug in the fglrx driver.  I believe a bug has been forwarded upstream.

---

### Post by JugeHuge on 2008-11-12
Have you tried with this thread solution??

[ATI Drivers - Desktop full HD, Myth garbage]("http://ubuntuforums.org/showthread.php?t=966640")

---

### Post by someth|ng on 2008-11-20
Please add SOLVED to the subject. I believe this post will be helpful for many people using ATI drivers. 


r

someth|ng

---

