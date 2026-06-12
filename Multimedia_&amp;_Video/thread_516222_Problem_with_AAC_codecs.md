---
title: "Problem with AAC codecs"
date: 2007-08-02
forum: Multimedia &amp; Video
---

### Post by DeadSuperHero on 2007-08-02
Hey all, 
I've been having trouble installing codecs for faad. Unfortunately, it gives me an error saying

"The following packages have unresolvable dependancies:
 faad:
 Depends: libfaad2-0 but it is not going to be installed"

So, I tried getting libfaad2-0 and get:

"The following packages have unresolvable dependancies:
libfaad2-0:
Depends: libfaad0 (>=2.5-2.1cafuego0) but it is not installable"

So, after looking online for it, I find it, try to install it, and I get this message:
"Dependancy Not Satisfied (or something like that): libc6"

So, I look for libc6, and found that I have it installed.
So, how do I fix this? I'm totally stumped on this one. I want to be able to play the music from Itunes in either Banshee or Songbird.
Please help me!

---

### Post by yabbadabbadont on 2007-08-02
faad and faac are both already in the Ubuntu repositories.  Try installing them using Synaptic.

```
/home/daffy $ aptitude search aad
p   egroupware-sambaadmin                                   - eGroupWare Samba administration application                      
p   faad                                                    - freeware Advanced Audio Decoder player                           
p   gstreamer0.8-faad                                       - AAC decoding plugin for GStreamer                                
i   libfaad2-0                                              - freeware Advanced Audio Decoder - runtime files                  
p   libfaad2-dev                                            - freeware Advanced Audio Decoder - development files              
/home/daffy $ aptitude search aac
p   faac                                                    - an AAC audio encoder                                             
p   gstreamer0.8-faac                                       - AAC encodingplugin for GStreamer                                 
p   gtkpod-aac                                              - manage songs and playlists on an Apple iPod                      
p   libfaac-dev                                             - an AAC audio encoder - development files                         
i   libfaac0                                                - an AAC audio encoder - library files                             
p   lisaac                                                  - Object-oriented language base on prototype                       
p   lisaac-common                                           - Arch-independent part for lisaac                                 
p   lisaac-doc                                              - Documentation for lisaac                                         
p   lisaac-mode                                             - Emacs mode for editing Lisaac programs                           

```

---

### Post by AlexFoster on 2007-08-10
What codecs would I need to be able to play iTunes purchased music on Amarok? I'm guessing AAC codecs and will install those with synaptic. Any others?

---

### Post by yabbadabbadont on 2007-08-10
> **AlexFoster said:**
> What codecs would I need to be able to play iTunes purchased music on Amarok? I'm guessing AAC codecs and will install those with synaptic. Any others?

I doubt that they will play at all if they have DRM on them.  Or does Apple sell them unencumbered now?

---

