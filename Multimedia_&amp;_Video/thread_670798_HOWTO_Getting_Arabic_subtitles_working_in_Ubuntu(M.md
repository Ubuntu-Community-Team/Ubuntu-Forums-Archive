---
title: "HOWTO: Getting Arabic subtitles working in Ubuntu(MPlayer)"
date: 2008-01-17
forum: Multimedia &amp; Video
---

### Post by diaa on 2008-01-17
[FONT="Garamond"][CENTER]**[SIZE="4"]Getting Arabic subtitles to work on Ubuntu(MPlayer)[/SIZE]**[/CENTER]


This guide will help you get Arabic subtitles working with MPlayer and the current latest Ubuntu release(Gutsy Gibbon)

[LIST=1]
[*]**Install SMPlayer**
First install the recently released GUI for *MPlayer*, *SMPlayer*.

```
sudo apt-get install smplayer
```

[*]**Optionally remove the default GUI and its skins**
*This step is optional, you can skip it*

```
sudo apt-get install mplayer-nogui
sudo apt-get remove mplayer-skins
```

[*]**Install libfribidi v0.20-1**
To display Arabic properly you need to obtain a recent version of libfribidi, I have only tried 0.20-1 and it worked(and I guess later versions will work too), I'm not sure if anything earlier will work, the currently available version in Ubuntu repositories(0.10.7-4build1) doesn't work.

You can [obtain 0.20-1 from Ubuntu forums]("http://ubuntuforums.org/attachment.php?attachmentid=39554&d=1186008124") and install it by running the file then clicking the *Install Package* button.


[*]**Setup SMPlayer to display subtitles in Arabic**
Run SMPlayer from the Main Menu

```
Applications > Sound & Video > SMPlayer
```

Then press Ctrl+P to open preferences.
In Preferences go to Subtitles page then choose a font that has Arabic support, select *System font* and press *Choose* button.

For compatibility I recommend *Sans serif* since it's available on all systems, but for better looking Arabic I recommend *Arial*.

In *Default subtitle encoding* section, you have to try 3 options, it depends on the subtitles you have, try the following in order

[LIST=1]
          [*] Enter *CP1256*(not in the list)
          [*] Select *UTF-8* from the list
          [*] Select *Unicode* from the list
[/LIST]

Try each of them then close the Preferences dialog then check whether Arabic subtitles are displayed properly or not
To make subtitles larger increase the *Scale* option in the *Size* section on the same page

[CENTER][IMG]http://ubuntuforums.org/attachment.php?attachmentid=56763&stc=1&d=1200623287[/IMG][/CENTER]

[*]Now you can enjoy watching any videos/movies with Arabic subtitles.[/LIST][/FONT]

---

### Post by rvm4000 on 2008-01-18
> **diaa said:**
> In *Default subtitle encoding* section, you have to try 3 options, it depends on the subtitles you have, try the following in order

[LIST=1]
          [*] Enter *CP1256*(not in the list)
[/LIST]


CP1256 was added to the encoding list in smplayer 0.5.61.

---

### Post by oshouip on 2008-01-18
thank you, i will try and come back.

again thank you very much

---

### Post by mauud777 on 2008-01-23
thanks so much ,,, it worked with me like a charm

thanks bro

i will attach pic

---

### Post by zanjabeel5 on 2008-02-09
Thanks diaa.
Do you know how to handle arabic subtitles in avidemux ?
or do you know any other tool to put permanent (hardcoded) subtitles in the movie.

---

### Post by asm2000 on 2008-02-09
nice to see that subtitles working nicely but  i ve a problem and still suferring..cause i can see arabic letters but separated.not continuous as i saw that shot..so dnt know what i do mmore to get it working properly.i ve kaffeine and sm player also....and this my shot from sm player.......hope to find a solution...and thanks for everybody here....

---

### Post by zanjabeel5 on 2008-02-09
@ asm2000 
give vlc a try and make sure to choose CP1256 
and that you have installed new version of libfribidi

Another way which I consider better ( also worked for me) is to convert from CP1256 to the more standard unicode
you convert once your subtitles file:

***iconv -f WINDOWS-1256 -t UTF-8 -o foo-out.txt foo.txt***

and then open it normally with clv or mplayer - without choosing encoding

---

### Post by diaa on 2008-02-09
> **zanjabeel5 said:**
> Thanks diaa.
Do you know how to handle arabic subtitles in avidemux ?
or do you know any other tool to put permanent (hardcoded) subtitles in the movie.

no sorry, I don't

---

### Post by ioluas on 2008-02-13
Thanks, it worked for me fine.

just one favor to ask. could you possibly tell me where i can download the dev package for libfribidi 0.20. you linked directly to the attachment and i couldn't find it anywhere. thanks again

---

### Post by diaa on 2008-02-13
> **ioluas said:**
> Thanks, it worked for me fine.

just one favor to ask. could you possibly tell me where i can download the dev package for libfribidi 0.20. you linked directly to the attachment and i couldn't find it anywhere. thanks again

you mean the development libraries?
well, I don't think they're available as a deb package but I guess you can easily grab the source of libfribidi from its homepage and compile it manually and you'll get the development libraries.

---

### Post by wail on 2008-02-20
Thanks a lot  u help me so much 

and it work very cooooooooooooooool

---

### Post by wail on 2008-02-20
hi but some subtitles scale too small ?????


what i can do?

---

### Post by diaa on 2008-02-20
As I mentioned in the tutorial this is possible using the scale option on the same preferences page

---

### Post by boob11 on 2008-03-18
Tnx
============

---

### Post by wakady on 2008-03-25
thxxxxxxxxxxxx man
u did a great job with this guide

---

### Post by alMubarmij on 2008-04-27
> **asm2000 said:**
> nice to see that subtitles working nicely but  i ve a problem and still suferring..cause i can see arabic letters but separated.not continuous as i saw that shot..so dnt know what i do mmore to get it working properly.i ve kaffeine and sm player also....and this my shot from sm player.......hope to find a solution...and thanks for everybody here....

I have same problem, even I use Windows version !
Arabic letters shows but it's divided and intermittent.
Is there a solution ?

---

### Post by bees2024 on 2008-05-18
Hi Diaa,

Thanks for the great job. In my new asus eee, I can't install the new 2.0 library, and I'm stick with 0.10.7. Installing the new version requires upgrading locales and libc6 packages, I don't wanna go the risk as lib6 is used by the whole system. I have followed your procedure but it resulted in arabic letters being shown but not connected, it was like separate individual characters. Could the old library be the problem, if it's I'm afraid i'll need to wait till asus repository upgrades their packages. Your help is highly appreciated.

Thanks,

---

### Post by diaa on 2008-05-20
> **bees2024 said:**
> Could the old library be the problem, if it's I'm afraid i'll need to wait till asus repository upgrades their packages. Your help is highly appreciated.


Yes, it is
You have to either compile it from source or wait for it to be available in the repos.

---

