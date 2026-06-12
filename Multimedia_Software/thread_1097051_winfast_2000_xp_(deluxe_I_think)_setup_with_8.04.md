---
title: "winfast 2000 xp (deluxe I think??) setup with 8.04"
date: 2009-03-15
forum: Multimedia Software
---

### Post by moparcrazy on 2009-03-15
I am hoping that I can get better help here then on the other forum I tried.  I have not gotten any help yet.  I have a home build desktop with a 2.0 Ghz Celeron prosessor, 1 Gig Ram, ATI 9600 (128 mb) and a winfast 2000 xp.  I have been doing a lot of reading over the last 4 or 5 months trying to figure out what is wrong with my computer but I have not had any luck.  I think that I have narrowed it down to my computer does not see the hardware but I am not sure.  I have done several walkthroughs that were even posted on this forum.  I am needing someone that could help me try and diagnose this problem.  

I think that I am going to need to start from scratch on install the winfast card.  I have made changes to my xorg.conf file I have tried rmmod t878, tuner and I don't remember what the 3rd one was but I tried that walkthrough.  

One of the other things that I hope will help is when I try and open up tvtime I just get the window for it for about 1 second and then it closes. I also have tried mythtv and I cant seem to get passed setting up the server.  I don't have a server and I don't know how to set it up.  I have also tried VLC player and it says that Unable to open 'dvb://'.  I have tried Zapping and that does not work either.  I have tried My Tv and it says there is no tuner device (this is why I don't think that Ubuntu is seeing my card).  #-o](*,)

[-o<[-o<[Please help this is really the only that is keeping me booting to XP and I don't like windows.  I am loving ubuntu with everthing else that I do. [-o<[-o<

Thank in advance.

---

### Post by 73ckn797 on 2009-03-15
Have you tried opening terminal?

Applications/Accessories/Terminal

Enter:
```
sudo lspci
```Does the card show up there?

Your previous steps are not described so I can only guess what exactly you have tried.
Did you post this in multimedia section?

---

### Post by moparcrazy on 2009-03-15
Here is the result of that command. It looks like it shows up I am assuming that it is the Brooktree corporation one.

00:00.0 Host bridge: VIA Technologies, Inc. P4M266 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:05.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
00:05.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AP [Radeon 9600]
01:00.1 Display controller: ATI Technologies Inc RV350 AP [Radeon 9600] (Secondary)

I also have not posted in the multimedia section.  I was not sure were to post.

PS thank you for the fast response.  I didn't even get a response on the other forum.

---

### Post by 73ckn797 on 2009-03-15
Yep, it does appear to be recognized by the system.

Go to this part of the forums: [http://ubuntuforums.org/forumdisplay.php?f=334](http://ubuntuforums.org/forumdisplay.php?f=334)

There are sticky posts that may help. 

General community help here: [https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)

I do not use the device you inquire about but at least we can get you moving towards a solution.

---

### Post by moparcrazy on 2009-03-15
Thanks I will try it.

---

