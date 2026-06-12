---
title: "Problem with WMA playback"
date: 2008-03-30
forum: Multimedia &amp; Video
---

### Post by ademsig on 2008-03-30
Hi

I have just moved to Ubuntu from XP but still have a large collection of music files ripped using  Windows Media Player and so are in the wma format. I have successfully installed the relevant codecs required as per the advice found on this forum. Whilst the files can be opened without a problem, playback is full of skips and jumps making the music fairly unlistenable - although not all files seem to be as affected as severely as others. I have some music in MP3 format and this all plays without a problem. I have the same issue using either the Movie Player and Rythmbox applications.

Does anyone have any idea of what may be causing the problem? I am new to Linux/Ubuntu so if you have a suggested fix then please just assume that I know nothing and explain it in step by step manner. :)

---

### Post by balaknair on 2008-03-30
you need to install the restricted extras package and extra codecs(plus non free packages from medibuntu if you want to play Real media and Quicktime files as well) for wma playback.
To instal the restricted extras package, open a terminal(Applications Menu> Accessories> Terminal) and paste this command
sudo apt-get install ubuntu-restricted-extras

 You can also use the GUI (Synaptic) to install
System menu> Administration> Synaptic Package Manager---> Search for Ubuntu restricted extras and select install--->Apply


For more info, check this link
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by balaknair on 2008-03-30
If you have any trouble just post a reply here.

---

### Post by Guiyas on 2008-03-30
I have a similar problem, but WMAs only skip the first 3-4 seconds. It's really irritating on albums where the tracks blend together. I'm on a fully updated Gutsy machine and I'm using Amarok. I have those restricted drivers and I'm at a loss as to where to go from here.

---

### Post by ademsig on 2008-03-30
> **balaknair said:**
> If you have any trouble just post a reply here.
Thanks for the advice about the restricted extras package but I have already done this plus the packages from Mediabuntu. It's not that I cannot open the files its just that I experience small skips and glitches in the music during playback, often throughout the whole track. I don't have this problem with any other type of media file.

---

### Post by balaknair on 2008-03-30
Yeah I know what you mean. I still have that problem with amarok and wma tracks skipping the first 2-3 seconds. I'm not really sure how to fix that, but then I just converted most of the wma files to ogg with sound converter, and it seems to be fine(the ogg files seem to be complete). Another option, which I haven't tried, is to get codecs from fluendo.com. A cousin of mine bought the Dolby AC3 codec pack from them and is using them with Linux(I think it's Arch Linux though, not Ubuntu), and I know he's got a huge collection of wma music and recordings, so I'm guessing it must work for him. The link is given below.
[https://shop.fluendo.com/](https://shop.fluendo.com/)

---

### Post by ademsig on 2008-03-30
> **balaknair said:**
> Yeah I know what you mean. I still have that problem with amarok and wma tracks skipping the first 2-3 seconds. I'm not really sure how to fix that, but then I just converted most of the wma files to ogg with sound converter, and it seems to be fine(the ogg files seem to be complete). Another option, which I haven't tried, is to get codecs from fluendo.com. A cousin of mine bought the Dolby AC3 codec pack from them and is using them with Linux(I think it's Arch Linux though, not Ubuntu), and I know he's got a huge collection of wma music and recordings, so I'm guessing it must work for him. The link is given below.
[https://shop.fluendo.com/](https://shop.fluendo.com/)
Thanks for the suggestions. I was trying to avoid converting them due to having so many (around 30 albums worth) but if it might be the best solution in the long run.

I was thinking about trying to install windows media player using WINE - do you have any experience of this and do you think it would solve the playback issue?

---

### Post by granny6989 on 2008-03-30
Quick FYI - 

   I recently started some posting about trying to convert WMA files, which works quite well with SoundConverter. The big problem I had is that it drops all of your ID3Tags, so after you're done, you need to use Easytag to re-mark your files,.which does alot of the work for you which is nice. It's a glitch with SoundConverter that has not been worked out yet, and only seems to happen when changing files from WMA to whatever. Just thought I'd give you a heads up on that, since I spent the last week trying to work out that bug......

S*

---

### Post by balaknair on 2008-03-31
@Granny6989:
OK thanks, that was a useful piece of info. I didn't have to worry about ID3 tags on my wma files earlier because theren't any tags. Amarok automatically created most of the info in the ID3 tags on the Ogg files based on the filename when I used the 'organise' option. But I think I'll give Easytag a go(I still have some wma files I haven't converted to ogg yet), it sounds pretty useful.

---

### Post by balaknair on 2008-03-31
@ademsig: I haven't had too much success with any program with Wine, I doubt if it'll solve the issue. I do remember when I first installed Ubuntu(not that long ago- in May 2007, Feisty Fawn) I tried something similar- Winamp under Wine. Needless to say, it bombed.

Even with 30 albums worth of wma files, I think it'll still be fairly easy to convert the files to ogg with soundconverter(at least, easier than running WMP under Wine). If you do try WMP I hope you could let me know how it went. Just curious.
All the best either way.

---

### Post by Hutom on 2008-03-31
With ubuntu-restricted-extras installed I can play all my WMA files perfectly both in totem gstreamer and vlc. So you should also be able to. May be it is an installation problem. 

Converting all files seems to be an escapist solution. One should be able to play all kinds of files in linux.

---

### Post by ellalan on 2008-04-04
Hi
I have installed Ubuntu Restricted Extras in Synaptic Package Manager but I am unable to play WMA music files in any of the players I have installed, any help gladly appreciated. Thank you..

---

