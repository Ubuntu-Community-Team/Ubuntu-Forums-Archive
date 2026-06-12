---
title: "Nova-hd-s2 video stuttering."
date: 2009-11-11
forum: Mythbuntu
---

### Post by byronmyth on 2009-11-11
Hi Folks. 
 
I'm running a MythBuntu 9.10 TV setup with Nova-T dual and Nova-HD-S2 cards. Terrestrial TV is fine. DVB-S transmissions from both Astra 1 (19.2) and Astra 2 (28.2) are fine. HD transmissions from Astra 2 are perfect, HD transmissions from Astra 1 using dvb-s are fine, however transmissions from dvb-s2 suffer from stuttering and breakup. The signal strength is displayed as 82% (same as the transmissions that work ok). I'm running firmware v1.22.82.0 with a Nvidia Geforce 9600 (tried a 8300 too) with v185 drivers (latest that MythBuntu support). Whilst monitoring CPU usage during the issue, CPU's run at around 35%, memory usage is around 45% suggesting that the PC isn't being overworked. 
 
Anyone help please?

---

### Post by mymythtv on 2009-11-11
ahh - glad to hear that, then I'm not alone :-)

I have the same problem, but due to danish broadcasters changed to mpeg4 recently, I didn't have time to investigate yet....

Upgraded mythtv from 0.21 to 0.22 just around the change from analog to mpeg4, so I just startet HD / DVB-S2 watching at that time...

Have a Hauppauge NOVA-S2-HD working just fine as you described, but playback of HD channels stutter...

I tried to play HD recordings outside mythtv ( mplayer ), and it seems to work a lot better !?!

HW is fine here to, so I think it's mythtv having the problem....
Also tried to play with different profiles, but no luck...

Mythbuntu 9.10, 3.16Ghz Dualcore, 2Gb memory, Nvidia 8400 GS, VDPAU

---

### Post by SiHa on 2009-11-11
Post removed

---

### Post by byronmyth on 2009-11-11
In which way should I forget it? DVB-S2 is supposed to be supported by both Myth and the hardware?

---

### Post by SiHa on 2009-11-11
Sorry, I posted a suggestion, and then re-read your OP and realised it wasn't helpful. I meant forget my post - it wasn't clear, sorry.

---

### Post by byronmyth on 2009-11-11
No problem SiHa. 
 
Anyone say if this is an issue with Myth or Hauppauge (I've emailed them too)?

---

### Post by sperwer on 2009-11-11
Hoping in to listening on this thread.

Same problem here with Hauppauge HVR4000.
by the way also a Dane.

Sperwer

---

### Post by byronmyth on 2009-11-12
I'll let you all know if I get anything back from Hauppauge.

---

### Post by byronmyth on 2009-11-12
[SIZE=2]That's helpful:[/SIZE]
 
[SIZE=2]Hi Brian[/SIZE]
[SIZE=2] [/SIZE]
[SIZE=2]I am sorry but we do not support the linux platform but this website might give you some tips [/SIZE][[SIZE=2][COLOR=#800080]http://www.linuxtv.org/wiki/index.php/Main_Page[/COLOR][/SIZE]]("http://www.linuxtv.org/wiki/index.php/Main_Page")
[SIZE=2] [/SIZE]
[SIZE=2] [/SIZE]
[SIZE=2] [/SIZE]
[SIZE=2]Many Thanks, [/SIZE]
[SIZE=2] [/SIZE]
[SIZE=2] [/SIZE]
[SIZE=2] [/SIZE]
[SIZE=2]Sajid Khan[/SIZE]
[EMAIL="S.Khan@hauppauge.co.uk"][SIZE=2]S.Khan@hauppauge.co.uk[/SIZE][/EMAIL]
[SIZE=2]Technical Support[/SIZE]
[SIZE=2]Hauppauge Digital SARL[/SIZE]
[SIZE=2](UK) London [/SIZE]

---

### Post by byronmyth on 2009-11-15
It would appear that I get several lines of the following logged when I try try view the DVB-S2 channels, anyone comment please?
 
[h264 @ 0x131c6c0]number of reference frames exceeds max (probably corrupt input), discarding one

---

### Post by byronmyth on 2009-11-23
There is a fix to solve this issue :
 
(The solution was a patch to ffmpeg ( [[COLOR=#444444]r20504[/COLOR]]("http://svn.mythtv.org/trac/changeset/20504"))
See history here

[[COLOR=#444444]http://svn.mythtv.org/trac/ticket/7522[/COLOR]]("http://svn.mythtv.org/trac/ticket/7522"))
 
I've no idea how to implement it, but it would seem that it might be released into "fixes" in a couple of weeks anyhow.

---

### Post by jensk on 2009-11-23
Sorry for hijacking this thread but i am trying to get my HVR-4000 to work on danish DVB-T and i read that Sperwer is using the new Danish DVB-T MPEG4 channels - which i can't get to work under 9.10 with HVR-4000. They work under my 9.04 + avenards patches although not very stable.

Could you sperwer tell me how you got your HD-S2 og HVR-4000 card to work under 9.10 and if you got all the free Danish channels (MPEG4).

Again - sorry for hijacking but i have posted several times in this forum without getting usable replies.
/jensk

---

### Post by sperwer on 2009-11-23
jensk

I'm sorry jensk, I don't believe i can help as I am using the satellite part of HVR-4000 and not the terrestrial part.


Im using the Frontend with the onboard nvidia HD8200 to benefit of vdpau.

I have reduced the stuttering a lot, however it is still not acceptable.
In the playback settings i have unchecked audio buffering, in generel settings I have unchecket extensively use of audio buffering. I have installed cpufreqd and running in performance mode fixed at 2.5 Ghz, that one helped a lot.

My setup consist of a:
Backend PC:
ASUS M4A78-Pro (ATI HD3200)
Athlon 5050e 2.6 Ghz
2 x Hauppauge HVR-4000 (DVB-S2)
1 x Skystar 2 USB (DVB-S)
Mythbuntu 9.10

Frontend PC
ASUS M4N78-Pro (Nvidia HD8200)
Athlon 4850e 2.5 Ghz
Grundig 42" Tv
Mythbuntu 9.10

All connected by 100 mbit wired network

Sperwer

---

### Post by pootle1 on 2009-11-23
I'm using a nova s2 card (although with only the S1 transmission from astra for freesat in the UK), I had stuttering problems with the 185 drivers, but these were resolved by moving to nvidia drivers 190.42,  these are working fine on my laptop and desktop, to a 3rd pc which is the backend. (all karmic with myth 0.22)

I tried 190.42 originally as I am using a nvidia gt220 card, and needed this version to get the card properly suported, but went so well I upgraded my laptop as well.

I'm running mythfrontend with vdpau on both machines (although with lower spec de-interlacing on the laptop as it can't keep up otherewise.

Also using nvidia-settings to check that your card is running at full speed once TV is running (especially if you are running with adaptive powermizer settings).  I run both machines in adaptive mode and it works very well

---

### Post by jensk on 2009-11-23
Thanks for the answer Sperwer

Jensk

---

### Post by byronmyth on 2009-11-24
No problem (for me) with hijacking the thread, but the issue I'm refering to has little to do with performance. There is a bug in the code for MPEG4 transmissions that has been fixed:
 
There is a fix to solve this issue :

(The solution was a patch to ffmpeg ( [[COLOR=#444444]r20504[/COLOR]]("http://svn.mythtv.org/trac/changeset/20504"))
See history here

[[COLOR=#444444]http://svn.mythtv.org/trac/ticket/7522[/COLOR]]("http://svn.mythtv.org/trac/ticket/7522"))

 
Now, if someone could tell me how to implement that patch so I don't have to wait for the fix to appear?

---

### Post by byronmyth on 2009-12-03
That ticket is locked now, does that mean anything at all? Will the patch get applied to the fixes? Christmas gets closer, would like this sorted by then :)

---

### Post by byronmyth on 2009-12-11
So what gives? A patch is available, I ask a simple question, the thread gets locked! 
 
How do these things work, if folks have confirmed that the simple couple of lines of code fixes an issue, why doesn't it get released?

---

### Post by Juergen. on 2010-01-20
Hi all,

i have the same Problem. I can see there is a ticket on Mythtv and they have a fix. 
But I can't see how to do it on my mythbuntu

Jürgen

mythbuntu 9.10
mythtv 0.22 trunk 23193

---

### Post by byronmyth on 2010-01-25
From what I've read it will get fixed the next time FFMPEG upstream is updated. No idea how long that will take. Can't watch any of the German HD channels until it is fixed :(

---

### Post by dibuntux on 2010-01-25
Same here in Italy: all terrestrial channels went digital and we have same 3 channels in HD, using H264. LiveTV is stuttering and sometimes I get strange black&blocky artifacts. On playback recordings the stuttering is gone, but still I get the black&blocky artifacts.
I'm using VDPAU Normal with standard settings.

Mythbuntu 9.10 AMD64
Gigabyte GA-M720 2GB DDR2-800
Athlon X2 4800+
Nvidia 9400GT 1GB
WD Sata2 CaviarGreen
Skystar 2 DVB-s
Nova T-500 dual DVB-t

---

### Post by Juergen. on 2010-02-19
Good news. I think it's updated now on trunk-version 23565

It runs perfect on my machine

Jürgen:popcorn:

---

