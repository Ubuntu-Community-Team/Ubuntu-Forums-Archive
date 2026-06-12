---
title: "smplayer - flipped subtitles"
date: 2012-06-07
forum: Multimedia Software
---

### Post by Spitted on 2012-06-07
Hello

I'm trying to watch a video with hebrew subtitles on smplayer.

I have fribidi compiled into mplayer. 
Watching the movie with the command:
```
mplayer -flip-hebrew -sub subfile.srt videofile.mkv
```works great!

But on smplayer the hebrew subtitles are always flipped.
I tried putting -flip-hebrew on Prefrences -> Advanced -> Options for MPlayer -> Options
But still doesn't work...

What can I do?

Thank you

---

### Post by andrew.46 on 2012-06-07
Do you have a link to a sample video so I can experiment?

---

### Post by Spitted on 2012-06-08
It happens with every video file and every .srt file

---

### Post by andrew.46 on 2012-06-08
Hmmm.... I must apologise as I am obviously a few steps behind you as I cannot get hebrew subtitle display at all with MPlayer :(. Can you tell me how you achieved this? And hopefully I can work on the flipping with SMPlayer :).

---

### Post by shantiq on 2012-06-08
ok so had a play with Hebrew sub and the only problem was when downloading one on
my computer.   it shows as this  [some of this might answer your question Andrew]






> 5
00:01:28,140 --> 00:01:29,540
.ìòæàæì

6
00:01:31,340 --> 00:01:32,500
?äéëï äåà

7
00:01:34,300 --> 00:01:35,940
.àðé öøéê ìæåæ

8
00:01:44,900 --> 00:01:52,340
- àåùï 13 -

9
00:02:09,900 --> 00:02:14,580
îä äçãùåú? -ùåí ãáø, äí
.àåîøéí ùä-24 ùòåú... -ðëåï



this is easily  corrected   by going to Libre Office and opening as Hebrew.  

[ATTACH]219392[/ATTACH]


 Then cut and paste into original text editor then you have this

> 
00:01:28,140 --> 00:01:29,540
.&#1500;&#1506;&#1494;&#1488;&#1494;&#1500;

6
00:01:31,340 --> 00:01:32,500
?&#1492;&#1497;&#1499;&#1503; &#1492;&#1493;&#1488;

7
00:01:34,300 --> 00:01:35,940
.&#1488;&#1504;&#1497; &#1510;&#1512;&#1497;&#1498; &#1500;&#1494;&#1493;&#1494;

8
00:01:44,900 --> 00:01:52,340
- &#1488;&#1493;&#1513;&#1503; 13 -

9
00:02:09,900 --> 00:02:14,580
&#1502;&#1492; &#1492;&#1495;&#1491;&#1513;&#1493;&#1514;? -&#1513;&#1493;&#1501; &#1491;&#1489;&#1512;, &#1492;&#1501;
.&#1488;&#1493;&#1502;&#1512;&#1497;&#1501; &#1513;&#1492;-24 &#1513;&#1506;&#1493;&#1514;... -&#1504;&#1499;&#1493;&#1503;   but of course written on the right of the page. 


[B] Site here shows it on the wrong side when i paste but no bother it is fine in the original text editor
[/B]

SMplayer was happy.  had to set to Hebrew  see below and see times and script match **and not flipped**


[ATTACH]219389[/ATTACH]


also happy on vlc  [i used random video here so no worries :::]]]

[ATTACH]219390[/ATTACH]

==================================================================

**Spitted** I would suggest save the file that is giving you a problem as a new file and to make sure the codes are right in the save   .  I use Mousepad but i guess any text editor will do same


Hebrew seems to be ISO-8859-8

i attach one converted with Libre office as attach   [does not matter which film it is for  just for trial]


If you know all this already   sorry for wasting your time....   it might be something else altogether...     all i can say is that it is working as should on SMplayer here     so it might be your srt file that is the problem in this case [or not :]]

maybe try saving as one as all three choices here see if one of them works better 
1. Open your existing srt in Libre Office in each of 3 options then copy and paste into text editor and save
If saved in LibreOffice directly   it does not usually work as it becomes a mere text file and no longer an srt in my experience.

[ATTACH]219392[/ATTACH]

---

### Post by Spitted on 2012-06-08
Maybe I should have clarified that the .srt files are just fine. They work with both mplayer and totem, just smplayer is causing problems.

Here is what I get when I use the .srt file you attached to your message:
[http://i.imgur.com/Qz0F3.jpg](http://i.imgur.com/Qz0F3.jpg)
As you can see, the subtitle text is flipped...
[]("http://imgur.com/Qz0F3")

---

### Post by andrew.46 on 2012-06-08
I am having no great luck with Hebrew but perhaps SMPlayer respects MPlayer configuration, in which case place the following in your ~/.mplayer/config:

```
flip-hebrew=yes
```

It will save some commandline line typing for MPlayer anyway :).

---

### Post by Spitted on 2012-06-09
I have already tried that also, no luck...

What I can't understand is - MPlayer works just fine, so if SMPlayer uses it directly, why are the results different?
It is obvious SMPlayer doesn't disregard the mplayer options I give him (giving -nosound works, for example) - the only option that is being disregarded is -flip-hebrew :(

---

### Post by andrew.46 on 2012-06-09
In the SMPlayer subtitle preferences try unchecking 'Freetype Support'.

---

