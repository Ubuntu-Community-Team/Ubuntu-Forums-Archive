---
title: "Internet Sound Issue."
date: 2008-05-02
forum: Multimedia Software
---

### Post by nothingspecial on 2008-05-02
I`m running Hardy on a Compaq presario C700.
My sound card is  Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
I`m learning to play the bass. I`ve found this groovy website that has audio lessons on it.
[http://www.activebass.com/default.asp?iTarget=/lessons/lessdir.asp](http://www.activebass.com/default.asp?iTarget=/lessons/lessdir.asp)
My problem is I can`t hear the lessons.

The site says - 
WARNING: ActiveBass has not been able to determine how to play MIDI for your operating system and browser. The OS and browser configurations we support are:
• Windows - Netscape Navigator 4.x, Microsoft Internet Explorer 4.x/5.x.
• Macintosh - Netscape Navigator 4.x, Microsoft Internet Explorer 4.x/5.x.
If your system does match one of the configurations above, then please send an e-mail to ActiveBass and we will help to correct your situation.

It also says -
NOTE: Sound at ActiveBass is designed for standard installations of Netscape Navigator 4.x and Microsoft Internet Explorer 4.x/5.x for Windows and Macintosh. If this does not match your operating system and browser, then we cannot offer any support or guidance in helping you resolve your sound issues. Also note that Shockwave is not required to hear sound at ActiveBass. 

Is this fixable?
Thanks

---

### Post by nothingspecial on 2008-05-02
It seems the problem is I can`t play midi files -

 Your Computer MUST Be Able to Play Local MIDI Files
When we say "local", we refer to a MIDI file located on your hard drive. If your computer cannot play a MIDI file from your hard drive, then it will not be able to play MIDI files from a website such as ActiveBass.

Is there a way to play midi files?

---

### Post by Tomatz on 2008-05-02
Try this firefox extension (media player connectivity). I have hacked it to work with firefox 3.

Download the **extension** (attachment) and extract it to your desktop.

In **firefox** goto **tools, addons** then the **extensions** tab

Drag the downloaded **extension** (attachment) into the **extensions** box.

50 50 it will work though as the site might require a special plugin :(

---

### Post by nothingspecial on 2008-05-02
Thanks for helping. Your instructions were great. Unfortunately I still can`t hear the lessons. I`ll keep trying.:)

---

### Post by Tomatz on 2008-05-02
You could try ies4linux its basically internet explorer run on wine.

In a terminal:

```
sudo apt-get install cabextract wine
```

Then in a terminal:

```
wget http://www.tatanka.com.br/ies4linux/downloads/ies4linux-latest.tar.gz
tar zxvf ies4linux-latest.tar.gz
cd ies4linux-*
./ies4linux

```

[COLOR="Red"]*Instructions taken from here* => *[http://www.tatanka.com.br/ies4linux/page/Installation](http://www.tatanka.com.br/ies4linux/page/Installation)*
[/COLOR]
It will take care of the installation by its self although you will have to answer a few simple questions e.g which version of ie you want (i recommend 6 don't bother with 7)

Hope it helps ;)

---

### Post by nothingspecial on 2008-05-02
Thanks. I`ve solved it by installing timidity and configuring the extension you gave me to play midi files using the path usr/bin/timidity.
 The lessons won`t play just by clicking on them - you have to right click and select "MediaPlayerConnectivity" the select "open http://blahblahblah", but thats good enough for me.
 Thanks alot for taking the time to help. I`ll try and pass it on when I can.:)

                        :guitar:

---

### Post by Tomatz on 2008-05-02
Cool :)

Glad i could help.

You can mark the thread as solved then anyone else who has the same (or similar) issue can resolve it easily.

---

### Post by nothingspecial on 2008-05-02
I used to know how to do that. The mark thread as solved thing was in the thread tools wasn`t it. Seems to have disappeared.

---

### Post by Sabaki on 2008-05-05
> **nothingspecial said:**
> I`m running Hardy on a Compaq presario C700.
My sound card is  Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
I`m learning to play the bass. I`ve found this groovy website that has audio lessons on it.
[http://www.activebass.com/default.asp?iTarget=/lessons/lessdir.asp](http://www.activebass.com/default.asp?iTarget=/lessons/lessdir.asp)
My problem is I can`t hear the lessons.

The site says - 
WARNING: ActiveBass has not been able to determine how to play MIDI for your operating system and browser. The OS and browser configurations we support are:
• Windows - Netscape Navigator 4.x, Microsoft Internet Explorer 4.x/5.x.
• Macintosh - Netscape Navigator 4.x, Microsoft Internet Explorer 4.x/5.x.
If your system does match one of the configurations above, then please send an e-mail to ActiveBass and we will help to correct your situation.

It also says -
NOTE: Sound at ActiveBass is designed for standard installations of Netscape Navigator 4.x and Microsoft Internet Explorer 4.x/5.x for Windows and Macintosh. If this does not match your operating system and browser, then we cannot offer any support or guidance in helping you resolve your sound issues. Also note that Shockwave is not required to hear sound at ActiveBass. 

Is this fixable?
Thanks

I am having a very similiar problem. I found a great site for learning piano and guitar at [http://www.looknohands.com/chordhouse/piano/](http://www.looknohands.com/chordhouse/piano/)
and they have a nifty page to play scales, chords, etc. but I can't hear them. I can download the files but for some reason they have a .pl extension, such as 'ch_midi.pl'. 

I can rename the downloaded file to 'ch_midi.mid' for instance and then play it with TiMidity just fine, but this is a pain. TiMidity doesn't seem to want to play them with the .pl extension. How do I set up either Firefox, a plugin, or TiMidity or maybe some MIME configuration file somewhere to play these '.pl' files as midi files?

Chuck Bell

PS. I'm running the x64 Ubuntu 8.04 /w Ubuntu Studio

---

### Post by JuBeZ on 2008-07-15
I use activebass.com, rock on fellow bassist!

I tried the extension Tomatz posted but sadly it doesn't work on Firefox 3.0. Is there any other alternative or will I have to just use Firefox 2.0 when I use activebass.com? (which I'd prefer not to)

---

### Post by Tomatz on 2008-07-15
> **JuBeZ said:**
> I use activebass.com, rock on fellow bassist!

I tried the extension Tomatz posted but sadly it doesn't work on Firefox 3.0. Is there any other alternative or will I have to just use Firefox 2.0 when I use activebass.com? (which I'd prefer not to)

What version of firefox 3 are you using?

In firefox click **Help, About Firefox**

Tell me the **full version number**. Then i can hack the** max version check** in the extension so you will be able to use it ;)

---

### Post by JuBeZ on 2008-07-15
In Help-->About I get "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9) Gecko/2008061015 Firefox/3.0" 

I went to mozilla.com, searched for the mediaplayerconnectivity addon and installed that (version 0.9.1) but on activebass.com it doesn't sense any media. 

I'll give your version a try to see if that works better. Thanks Tomatz!

---

### Post by sven 22 on 2008-08-03
Hey, that's so coincidental.

:lolflag:


I was just at activebass.com as well, when I found out that Hardy doesn't support midi files in firefox 3.

So, having read the posts above, to play midi files should I install timidity, or the hacked media player connectivity file, or both?

Thanks,

Sven
Ibanez 885
Fender Zone
and others

---

