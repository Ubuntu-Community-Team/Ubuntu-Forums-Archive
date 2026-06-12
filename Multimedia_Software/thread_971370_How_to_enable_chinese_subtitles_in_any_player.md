---
title: "How to enable chinese subtitles in any player?"
date: 2008-11-04
forum: Multimedia Software
---

### Post by powel212 on 2008-11-04
Running Ubuntu 8.10 and love it. Have installed the language packs and Chinese is enabled in all my programs but the subtitles are all garbled when I watch any movie with Chinese Subs on mplayer, totem, and VLC. 
I am the computer geek who speaks english and my girlfriend is the computer illiterate who speaks chinese. So the Chinese forums are of no use to me.
Please help.
Powel

---

### Post by lovinglinux on 2008-11-05
Try adding the following line to ~/.mplayer/config under the [default] section:

```
subfont-encoding="ISO-8859-1"
```

Don't forget to replace ISO-8859-1 with the Chinese character encoding.

---

### Post by powel212 on 2008-11-05
Any idea where i can find this .mplayer folder?

I opened the mplayer.config file but found no line as mentioned;

“subfont-encoding="ISO-8859-1"“

still looking for the folder "~/.mplayer/"

thanks for pointing me in a direction - i'll keep looking.

Powel

---

### Post by lovinglinux on 2008-11-05
Go to your home folder and press CTRL+H to see hidden files and folders. You should see .mplayer folder there. Please notice that ~/ means your home folder and all files beginning with a dot are hidden files.

The line will probably not be there. You will have to add it.

---

### Post by powel212 on 2008-11-06
Thanks for the clarification. Found the config file, added lines to include asian script. Still no joy. Any other ideas?

I've added additional fonts to the system as well but still no joy.

Any help is appreciated.

Powel

---

### Post by lovinglinux on 2008-11-06
> **powel212 said:**
> Thanks for the clarification. Found the config file, added lines to include asian script. Still no joy. Any other ideas?

I've added additional fonts to the system as well but still no joy.

Any help is appreciated.

Powel

Have you tried smplayer?

---

### Post by jill.valentine on 2008-11-06
if i want another language, such as japanese / korean, it would be the same way to do it?

---

### Post by lovinglinux on 2008-11-06
> **jill.valentine said:**
> if i want another language, such as japanese / korean, it would be the same way to do it?

Yes. As I mentioned in the previous post, you could also try smplayer. It has an option in the preferences to choose the character encoding.

---

### Post by powel212 on 2008-11-06
Thank you. Yes I have the smplayer front end and love it. Have tried all the subtitle configuration options available there. Unfortunately still no love.

I am thinking it is something I am missing within the system. For example. When I type Chinese in Open Office I only have the choice of one font. Even though I added new Chinese fonts in Synaptic. So, maybe even though I am setting the options within smplayer, when the app goes to get the font for encoding it can't find it.

But my other programs display Chinese no problem.... arg...

Powel

---

### Post by lovinglinux on 2008-11-06
> **powel212 said:**
> Thank you. Yes I have the smplayer front end and love it. Have tried all the subtitle configuration options available there. Unfortunately still no love.

I am thinking it is something I am missing within the system. For example. When I type Chinese in Open Office I only have the choice of one font. Even though I added new Chinese fonts in Synaptic. So, maybe even though I am setting the options within smplayer, when the app goes to get the font for encoding it can't find it.

But my other programs display Chinese no problem.... arg...

Powel

Did you changed the default font under smplayer properties?

You could also try adding the font path to ~/.mplayer/config like this:

```
font=/usr/share/fonts/truetype/msttcorefonts/arial.ttf
```

If mplayer and smplayer cannot find the font, then this should fix the problem.

---

### Post by powel212 on 2008-11-07
Great, thanks. That sounds good. I'll try is when I get home from work. Thanks for your help.

Powel

---

### Post by powel212 on 2008-11-07
Tried that too. A good suggestion but unfortunately still no love. How about i download a fully Chinese player??? i know in windows I can download a chinese version of VLC. How do I download a chinese version of any software in Ubuntu?

Powel

---

### Post by mc4man on 2008-11-07
You haven't mentioned what it is your trying to playback and the source of your subs. I somewhat doubt it's dvd movies, where display of Chinese,Japanese, Korean subs don't require anything additional vs. english subs.

---

### Post by lovinglinux on 2008-11-07
> **powel212 said:**
> Tried that too. A good suggestion but unfortunately still no love. How about i download a fully Chinese player??? i know in windows I can download a chinese version of VLC. How do I download a chinese version of any software in Ubuntu?

Powel

Don't know about that.

---

### Post by rvm4000 on 2008-11-07
SMPlayer/MPlayer can display Chinese subtitles without problems. All you need is to specify the correct encoding (like BIG5) and have installed appropriate fonts.

I don't speak Chinese, but this looks like Chinese to me:

[[IMG]http://img511.imageshack.us/img511/4651/chinesexq3.th.jpg[/IMG]](http://img511.imageshack.us/my.php?image=chinesexq3.jpg)[[IMG]http://img511.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

---

### Post by lovinglinux on 2008-11-07
> **rvm4000 said:**
> SMPlayer/MPlayer can display Chinese subtitles without problems. All you need is to specify the correct encoding (like BIG5) and have installed appropriate fonts.

I don't speak Chinese, but this looks like Chinese to me:

[[IMG]http://img511.imageshack.us/img511/4651/chinesexq3.th.jpg[/IMG]](http://img511.imageshack.us/my.php?image=chinesexq3.jpg)[[IMG]http://img511.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

Since we are talking about subtitles on smplayer/mplayer and you are the developer of smplayer, I would like to ask why I can't make the subtitles align at the top of the screen using smplayer preferences? I have changed the slider position, but it doesn't have any effect on the subtitle position.

My apologies to powel212 if I'm hijacking the thread, but I couldn't waste the opportunity to ask the developer about this.

---

### Post by rvm4000 on 2008-11-07
> **lovinglinux said:**
> Since we are talking about subtitles on smplayer/mplayer and you are the developer of smplayer, I would like to ask why I can't make the subtitles align at the top of the screen using smplayer preferences? I have changed the slider position, but it doesn't have any effect on the subtitle position.

That option in preferences specifies the position of the subtitles by *default* and only works if the SSA/*** library is disabled. It's used when you open a video which you never played before. For videos you already played, the position they had before is kept, but it can be changed with the options **Up** and **Down** in the Subtitles menu.

Remember this only works with the SSA/*** library disabled and with subtitles in srt or sub formats. 

If you want subtitles on the top of the screen with the SSA/*** library enabled, it's possible, but you need to get the latest version of smplayer from svn (you can get packages [here](ftp://ftp.berlios.de/pub/smplayer/ubuntu/)), it allows further customization of SSA/*** subtitles, including the possibility to display them on the top of the screen.

[[img]http://img368.imageshack.us/img368/8959/subtitlesfr1.th.png[/img]](http://img368.imageshack.us/my.php?image=subtitlesfr1.png)[[img]http://img368.imageshack.us/images/thpix.gif[/img]](http://g.imageshack.us/thpix.php)

---

### Post by powel212 on 2008-11-07
Well what you have there is not just Chinese but Traditional Chinese. Which is exactly what I want. Arg. What am I doing wrong. The video is an MKV and the sub file is an SRT. When I boot into Vita and use the same files in GOM it works. I'm pretty sure i have my system somehow set up wrong. As it won't work in VLC or mplayer or Totem. What did you do to your system before trying the chinese subs on your box?

Thanks again

Powel

---

### Post by lovinglinux on 2008-11-07
@rvm4000

Thanks a lot, but it still doesn't work. I have created a new thread to discuss this [[COLOR="Red"]**here**[/COLOR]]("http://ubuntuforums.org/showthread.php?p=6128097")

> **powel212 said:**
> Well what you have there is not just Chinese but Traditional Chinese. Which is exactly what I want. Arg. What am I doing wrong. The video is an MKV and the sub file is an SRT. When I boot into Vita and use the same files in GOM it works. I'm pretty sure i have my system somehow set up wrong. As it won't work in VLC or mplayer or Totem. What did you do to your system before trying the chinese subs on your box?

MKV's can have embedded subtitles, so maybe the players are displaying another subtitle from the file and not the srt. Just guessing.

---

### Post by powel212 on 2008-11-08
Based on all the information you provided I was able to get it working in Totem. Thanks. I will continue to try smplayer. And will post if I get it sorted.

Thanks again

Powel

---

### Post by lovinglinux on 2008-11-08
> **powel212 said:**
> Based on all the information you provided I was able to get it working in Totem. Thanks. I will continue to try smplayer. And will post if I get it sorted.

Thanks again

Powel

I'm glad you did it. Would be nice if you could post what exactly solved the problem with Totem and mark the thread as solved, so other users can easily browse the thread for a solution.

---

### Post by rvm4000 on 2008-11-08
Mmm, it seems it's necessary to enable the SSA/*** library. Without it I've got lines instead of Chinese characters.

With the SSA/*** library enabled Chinese is displayed properly (I think).

My config:

[[IMG]http://img90.imageshack.us/img90/4610/chinese1zb6.th.png[/IMG]](http://img90.imageshack.us/my.php?image=chinese1zb6.png)[[IMG]http://img90.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

[[IMG]http://img90.imageshack.us/img90/5975/chinese2bb4.th.png[/IMG]](http://img90.imageshack.us/my.php?image=chinese2bb4.png)[[IMG]http://img90.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

Font related packages I have installed:
```

ii  console-setup                              1.21ubuntu8                                 Set up the font and the keyboard on the cons
ii  console-terminus                           4.20-6                                      Fixed-width fonts for fast reading on the Li
ii  console-tools                              1:0.2.3dbs-65ubuntu7                        Linux console and font utilities
ii  defoma                                     0.11.10-0.2                                 Debian Font Manager -- automatic font config
ii  fontconfig                                 2.5.0-2ubuntu3                              generic font configuration library - support
ii  fontconfig-config                          2.5.0-2ubuntu3                              generic font configuration library - configu
ii  gsfonts                                    1:8.11+urwcyr1.0.7~pre43-1                  Fonts for the Ghostscript interpreter(s)
ii  libconsole                                 1:0.2.3dbs-65ubuntu7                        Shared libraries for Linux console and font
ii  libfontconfig1                             2.5.0-2ubuntu3                              generic font configuration library - runtime
ii  libfontconfig1-dev                         2.5.0-2ubuntu3                              generic font configuration library - develop
ii  libfontenc1                                1:1.0.4-2                                   X11 font encoding library
ii  libfreetype6                               2.3.5-1ubuntu4.8.04.1                       FreeType 2 font engine, shared library files
ii  libfreetype6-dev                           2.3.5-1ubuntu4.8.04.1                       FreeType 2 font engine, development files
ii  libfs6                                     2:1.0.0-4ubuntu2                            X11 Font Services library
ii  libxfont1                                  1:1.3.1-2                                   X11 font rasterisation library
ii  libxft-dev                                 2.1.12-2ubuntu5                             FreeType-based font drawing library for X (d
ii  libxft2                                    2.1.12-2ubuntu5                             FreeType-based font drawing library for X
ii  msttcorefonts                              2.4                                         Installer for Microsoft TrueType core fonts
ii  ttf-arabeyes                               2.0-1ubuntu1                                Arabeyes GPL TrueType Arabic fonts
ii  ttf-dejavu-core                            2.23-1                                      Vera font family derivate with additional ch
ii  ttf-dejavu-extra                           2.23-1                                      Vera font family derivate with additional ch
ii  ttf-freefont                               20060501cvs-12                              Freefont Serif, Sans and Mono Truetype fonts
ii  ttf-kochi-gothic                           1.0.20030809-4ubuntu2                       Kochi Subst Gothic Japanese TrueType font wi
ii  ttf-kochi-mincho                           1.0.20030809-4ubuntu2                       Kochi Subst Mincho Japanese TrueType font wi
ii  ttf-lao                                    0.0.20060226-2                              TrueType font for Lao language
ii  ttf-malayalam-fonts                        1:0.5.0-0ubuntu1                            Free TrueType fonts for the Malayalam langua
ii  ttf-opensymbol                             1:2.4.1-1ubuntu2                            The OpenSymbol TrueType font
ii  ttf-thai-tlwg                              1:0.4.8-1                                   Thai fonts in TrueType format
ii  ttf-unfonts-core                           1.0.1-6ubuntu1                              Un series Korean TrueType fonts
ii  x-ttcidfont-conf                           27                                          TrueType and CID fonts configuration for X
ii  x11-xfs-utils                              7.3+1                                       X font server utilities
ii  xfonts-100dpi                              1:1.0.0-4                                   100 dpi fonts for X
ii  xfonts-75dpi                               1:1.0.0-4                                   75 dpi fonts for X
ii  xfonts-base                                1:1.0.0-5                                   standard fonts for X
ii  xfonts-encodings                           1:1.0.2-3                                   Encodings for X.Org fonts
ii  xfonts-scalable                            1:1.0.0-6                                   scalable fonts for X
ii  xfonts-utils                               1:1.0.1-2ubuntu1                            X Window System font utility programs
```

---

### Post by powel212 on 2008-11-08
How I got it working was. In Totem main preference drop down changed encoding to Chinese (BIG5) and used the default font "Sans Bold"

So now it works in Totem but still haven't got it sorted in Mplayer. If I do get it sorted I will post what made it work.

one thing of note is... In vista GOM player I can drop any .srt file into the window and it will sort out the encoding on it's own. But Totem it seems I have to change the encoding if one time i use Traditional Chinese and next time i use simplified Chinese. I prefer traditional but i can't always get them so i use simplified in these cases. It would be nice to have one encoding that could handle all Chinese. Maybe i'm just over zealous. haha.

Thanks again

Powel

---

### Post by rvm4000 on 2008-11-08
In smplayer and mplayer there's the possibility to try to autodetect the encoding.

In smplayer (from 0.6.4) just check the option "Try to autodetect for this language" and select chinese.

In mplayer, use the option **-subcp enca:zh:BIG5** (the encoding at the end will be used if autodetection fails)

I don't know about totem, I don't have it installed.

---

