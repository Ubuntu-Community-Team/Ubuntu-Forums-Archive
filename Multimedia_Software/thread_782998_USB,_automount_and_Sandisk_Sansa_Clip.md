---
title: "USB, automount and Sandisk Sansa Clip"
date: 2008-05-05
forum: Multimedia Software
---

### Post by LianerGoist on 2008-05-05
In Ubuntu 7.10, my Sandisk Sansa Clip worked perfect. I version 8.04, it does not automount. I am not the first to realize this, but I want to let you know there is a simple workaround, until someone fix the bug. 

All I need to do is take out my usb mouse and plug it in again. Then Ubuntu 'see' the Sansa Clip. I can also run the command 'lsusb' from the terminal. I think I just need to make Ubuntu 8.04 take a look at the attached usb devices one more time and then it will be found. I don't know why it's not found when connected in the first place, but this little workaround works. For me, at least...

Thomas

---

### Post by LianerGoist on 2008-05-07
> **LianerGoist said:**
> In Ubuntu 7.10, my Sandisk Sansa Clip worked perfect. I version 8.04, it does not automount. I am not the first to realize this, but I want to let you know there is a simple workaround, until someone fix the bug. 

All I need to do is take out my usb mouse and plug it in again. Then Ubuntu 'see' the Sansa Clip. I can also run the command 'lsusb' from the terminal. I think I just need to make Ubuntu 8.04 take a look at the attached usb devices one more time and then it will be found. I don't know why it's not found when connected in the first place, but this little workaround works. For me, at least...

Thomas

Follow-up on myself:

If I connect my wifes Creative Zen Stone Plus, it automounts without problems. The icon on the desktop looks like a harddisk with a little orange usb sign. 

When the Sandisk Sansa Clip is connected, the icon looks like an iPod. In Ubuntu 7.10, the icon looked like the one I get when connecting the Creative player. So, it seems like Ubuntu 8.04 does a better job identifying the attached device (?), but somehow also implemented a bug...



So

---

### Post by Ltmboy on 2008-05-07
I too found that unplugging and replugging my usb mouse connects the Sansa clip. I was looking into why it didn't automount as usual and found this thread. Works well, thank you. :)

---

### Post by rzrgenesys187 on 2008-05-19
I don't have a mouse plugged i right now so lsusb worked great for me.  Much Thanks

---

### Post by G@B0 on 2008-05-20
Well I have one of these and in Ubuntu 7.10 worked perfectly but after the upgrade now it seems to not be detected even on a lsusb command.

So when it was connected I accidentaly pressed the center button and wuala:popcorn:. It works!!

The USB mode is set on automatically and you just have to press the center button after connecting the device to the computer and it will suddenly appear as a removable drive.

I hope you guys try it to confirm this.

---

### Post by technologik on 2008-05-26
CONFIRMED...sure enough, pressing the center button connected it right up.  Go figure! :biggrin:  Thanks for stumbling across that.

---

### Post by strungoutfan78 on 2008-06-07
Go figure.  I just ran across this problem this morning and this post helped immensely.  I didn't even have time to get frustrated.  Thanks!:guitar:

---

### Post by compacho on 2008-06-16
Hey everyone. I'm wondering, does your Clip show up in Banshee or Exaile? I set the device to MSC and it shows up as a mass storage device. I have an old Creative Zen Stone and when I plug it in, it shows up as a digital audio player which I like. If I set the Clip to MTP or automatic, Ubuntu recognizes it (just happened recently BTW) as a digital audio player. But when I tell a program to connect to the device, the device unmounts and the program freezes. 

Any ideas?

---

### Post by newtanker on 2008-06-20
My problem is slightly different--it is recognized and the drive appears briefly on the desktop, but then dissapears and brings up rhythmbox.  Had no issues with feisty or gutsy, just now with hardy its a pain in the butt--the work arounds dont seem to work, as its seen with lsusb and pressing the center button on the e250 doesnt do a thing....

---

### Post by Marat89 on 2008-06-28
hi newtanker
i have the same problem. lsusb and pressing the center button Dont work

Have someone an ide?

---

### Post by Can+~ on 2008-07-07
Weird, I had this issue, but now I found that, instead of putting the access icon on the desktop, it places it here, without mounting:

[IMG]http://img.photobucket.com/albums/v517/CanXp/screenshot2-4.png[/IMG]

Clicking there mounts the usb device automatically. I don't know if this is a feature or a bug.

---

### Post by markbellis on 2009-09-06
Pressing the center button worked for me in 9.04 64 bit with a 2gb Clip. Thanks very much for the suggestion... sometimes it did mount upon connection, sometimes it didn't...

---

