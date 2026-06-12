---
title: "vlc playing random"
date: 2010-11-17
forum: Multimedia Software
---

### Post by squrl on 2010-11-17
ubuntu 10-04  vlc 1.1.4.1  

Is it possible to play a directory and have the contents payed randomly. 

I can handle the directory selection but cant find how to make it random.

---

### Post by sikander3786 on 2010-11-17
Click the playlist button in the bottom next to play, forward buttons and you will see the Random button (2 crossed over arrows).

---

### Post by squrl on 2010-11-17
Went there did that. There are no crossed arrows. The playlist is also in icon mode and no way to change to list that I could find

---

### Post by sikander3786 on 2010-11-17
Icon mode???

Hover you mouse over the buttons and you should find the Random button.

---

### Post by squrl on 2010-11-17
icon mode = the music files are displayed with a large icon in the playlist

Hovering over the different functions doesn't show any selection options

---

### Post by sikander3786 on 2010-11-17
Do you see this?

---

### Post by squrl on 2010-11-17
I give up. 
I dont have the same as you show. at the bottom is a box with the name of the file being played in it. There is no random icon in the row of selectable items. I'll have to find a player that is in step with the rest of the world. The damn playlist with the huge ugly icon has to go to.

Thanks for your help

---

### Post by sikander3786 on 2010-11-17
> **squrl said:**
> I give up. 
I dont have the same as you show. at the bottom is a box with the name of the file being played in it. There is no random icon in the row of selectable items. I'll have to find a player that is in step with the rest of the world. The damn playlist with the huge ugly icon has to go to.

Thanks for your help
Can you please show us your screenshot? For posterity, if possible...

---

### Post by squrl on 2010-11-17
I would if I could.  I have the screenshot on my desktop but don't know how to insert or attach it from there  Sorry Guess an old man shouldn't try to play kids games

---

### Post by sikander3786 on 2010-11-17
> **squrl said:**
> I would if I could.  I have the screenshot on my desktop but don't know how to insert or attach it from there  Sorry Guess an old man shouldn't try to play kids games
No problem if you can't :-)

There is an attachment option next to smilies in the post menu. But that after you click New Reply, not from quick reply from this page.

---

### Post by squrl on 2010-11-17
[http://ubuntuforums.org/attachment.php?attachmentid=175849&stc=1&d=1290025764](http://ubuntuforums.org/attachment.php?attachmentid=175849&stc=1&d=1290025764)

I dont know if this worked or not

---

### Post by squrl on 2010-11-19
bump

---

### Post by sikander3786 on 2010-11-19
That doesn't look like the default VLC interface. At least I haven't seen that before.

Go to Tools > Preferences and select Native and Classic look.

Or try resetting VLC by,

```
rm -rf ~/.config/vlc
```

```
rm -rf ~/.vlc
```

---

### Post by squrl on 2010-11-19
this says its version 1.0.6  and this is listed as the native classic look.

I edited as you showed and there is very little if any difference. Still no random

---

### Post by sikander3786 on 2010-11-19
The screenshot I posted is also version 1.0.6 :confused:

Why that much difference? Don't know.

For a workaround, go to Edit > Preferences > Hotkeys and set a Hotkey for Random.

I know it is not the perfect solution, but I am running out of ideas.

---

### Post by squrl on 2010-11-19
I finally found it after unclicking native on the pref page.

Random is now listed on the playlist page as said its crossed arrows.  Thanks.

---

### Post by sikander3786 on 2010-11-19
Glad you got it working :-)

But I'm a bit confused. Can you help?

> I finally found it after unclicking native on the pref page.

Mean you changed to something other than Native interface? What?

---

### Post by squrl on 2010-11-19
on the preferences page I went to interface. The option for native was checked. I unchecked that. Next the display mode was set to classic so left it that way and went hunting for random. I brought up view > playlist and there was random along with a few other options

---

### Post by sikander3786 on 2010-11-19
> **squrl said:**
> on the preferences page I went to interface. The option for native was checked. I unchecked that. Next the display mode was set to classic so left it that way and went hunting for random. I brought up the playlist page and there was random along with a few other options
Thanks for the explanation. I'm going to try that...

Happy Ubuntu-ing!

---

### Post by Tauqir Ahmad on 2010-11-19
VLC Player have some bugs in it like in Subtitles options . U can do whatever u want but nah it will do nothing may be u r facing some problems of VLC not Ubuntu. I think......

Oh yeah same problem is On Windows Platform too.

Thanks

---

