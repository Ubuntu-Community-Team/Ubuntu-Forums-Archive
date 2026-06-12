---
title: "Rockbox utility"
date: 2008-05-02
forum: Multimedia Software
---

### Post by joshritger on 2008-05-02
I am using rockbox on my mp3 player and love it, my problem is that I haven't been able to find a decent guide on how to install rockbox utility on ubuntu. I used windows to install rockbox on my mp3 player, but it would be nice to be able to use the rockbox utility in ubuntu. Does anyone know of a .deb to install rockbox utility, or a decent how to on how to install it, I have been using ubuntu for about a year, but I haven't really compiled anything from source yet. I was never able to find a decent guide.

Thanks,
Josh

---

### Post by coolen on 2008-05-02
I had it on my iPod for a while. It comes with an install script and instructions on the website.

I see no reason why you can't use it under Linux if it's already on your iPod, though. If you add songs using gtkpod, Rockbox should recognise them in database mode.

---

### Post by joshritger on 2008-05-02
The problem isn't putting the songs on the mp3 player, it is updating the rockbox firmware, there are new versions fairly regularly and I have to boot windows which I very seldomly do to update the firmware. I do not know how to install from source, does anyone know of a guide?

---

### Post by drworm01 on 2008-05-03
Don't you just have to copy over the .rockbox directory currently on your iPod with the latest Rockbox build? Download, unzip, copy. That's all I ever had to do to get the latest firmware. No compiling from source required.

---

### Post by coolen on 2008-05-04
This is true. The installer should only be needed for the boot loader. Once that's in place, it should be as simple as copying the new firmware onto your iPod.

---

### Post by Master's Property on 2008-05-09
So far this is how I understand my problem. Feel free to correct me if I'm wrong. I have read a lot about Ipods being either Winpods or Macpods depending on the chip or format of the internal hard disk...(which I don't see since it's just a 1 gig flash). I have tried to install rockbox several times using terminal with 3 different guides. I even went as far as installing Wine and using the windows installer...(hint: I voided a 3 year warantee to get Windows OFF this machine.). Still no luck, but 1 install attempt did get Rockbox on the boot loader, but wouldn't boot to it. I live for my music, can anyone help me salvage my new paperweight?

Ubuntu 7.10 full
Dell Inspiron 1525 
core2duo
3 gigs 667 DDR2
Intel experimental graphics adaptor

---

### Post by coolen on 2008-05-10
The Windows/Macpods is due tot the way iTunes sets up the disc (fat32 for Windows, I believe, and HFS+ for Macs).

As far as I know, nothing in Linux will be able to do this. However, if you're only planning on using Rockbox, and not the original iPod firmware, I see no reason why you couldn't simply format it to fat32 and use the installer then. Don't trust me on this, but it makes sense to me.

If you can tell us what you've tried before, we may be able to help you. I've never done what you're asking.

---

### Post by Master's Property on 2008-05-10
I have tried to format to FAT32, but still no luck. Since Wine doesn't support Itunes very well, I have no way to restore it. No worries though, it's just a matter of time before someone figures this stuff out in detail. I really would like to get Rockbox on here. I already formated over the Apple firmware. I was fully prepaired to loose the use of my Ipod for a while when I started all this. Doesn't mean it doesn't suck not having it...lol It made sense to me too since I just want Rockbox. There's no point in having 2 OS's on a little 1 gig. And from what I've read Rockbox blows Apple OS away anyway. I've become pretty proficient with fdisk and mounting options through this, and am by far not a novice OR a pro. Any help would me very much appreciated, and I'm even willing to pay a little to whoever can get me through a successful, stable install. I called Geek Squad and they want $200!! I'll paypal $20, but I'm disabled and only get money once a month.

MSN: [email]rebeccalhare411@gmail.com[/email]
YIM: rebeccahare411
AIM: rebeccalhare

---

### Post by sideshowmel on 2008-12-29
Actually as I understand it, the ipod needs a tiny ext3 (or HFS+) partition to load the linux kernel.  the install script should handle this, but this is kindof an old thread, so you've probably figured that out by now...

---

### Post by DarrenCT on 2009-01-02
is he not just asking how to install and use the installation utility?  

Found in the downloads section of the site?

[http://www.rockbox.org/twiki/bin/view/Main/RockboxUtility#Download](http://www.rockbox.org/twiki/bin/view/Main/RockboxUtility#Download)

1) click the link to download the linux version of the util
2) extract the contents into something like /opt
3) create a startup link under Sounds (right click on the "applications" menu, and click on "edit menus").  
4) go to Sound and Video (or choose another one if you like) 
5) click "new item"
6) give it a name ie. "RockBox Utility"
7) browse for the command, and look under the "/opt" directory you extracted to (i.e. /opt/rbutilqt-v1.0.8/rbutil) and select the file listed there).
8) test the link from the Applications menu.


Please correct me if I am wrong on what is needed here.  I am using the utility with no problems running 8.10.

---

### Post by inspired on 2009-01-14
> **DarrenCT said:**
> is he not just asking how to install and use the installation utility?  

Found in the downloads section of the site?

[http://www.rockbox.org/twiki/bin/view/Main/RockboxUtility#Download](http://www.rockbox.org/twiki/bin/view/Main/RockboxUtility#Download)

1) click the link to download the linux version of the util
2) extract the contents into something like /opt
3) create a startup link under Sounds (right click on the "applications" menu, and click on "edit menus").  
4) go to Sound and Video (or choose another one if you like) 
5) click "new item"
6) give it a name ie. "RockBox Utility"
7) browse for the command, and look under the "/opt" directory you extracted to (i.e. /opt/rbutilqt-v1.0.8/rbutil) and select the file listed there).
8) test the link from the Applications menu.


Please correct me if I am wrong on what is needed here.  I am using the utility with no problems running 8.10.

Thanks Darren,
I was also looking for this info you have provided. Reading through this thread I started to get the impression no one was going to cotton on to what the actual question was and thus provide a solution. :popcorn:

I am grateful for your attention to the original question and for providing a useful answer. Cheers mate. :)

Jonathan

PS. I am also happy I don't have to go through some long-winded process of creating an installable DEB from the archive provided from the rockbox site. Although, it's probably about time I learnt (I have just needed to yet).

---

### Post by DarrenCT on 2009-01-14
Glad to help!

---

### Post by msohn88 on 2009-03-01
Just a quesition.

After you download rockboxutility, do you extract it on desktop and choose the rockboxutilty as command or what?

I am a n00b for Linux.

thanks for advance.

---

### Post by msohn88 on 2009-03-01
Just a quesition.

After you download rockboxutility, do you extract it on desktop and choose the rockboxutilty as command or what?

I am a n00b for Linux.

thanks for advance.

> 
Failed to execute child process "/home/min/Desktop/rbutilqt-v1.0.7-64bit" (Permission denied)


---

### Post by coolen on 2009-03-01
chmod +x /home/min/Desktop/rbutilqt-v1.0.7-64bit

That command will hopefully remedy your problem.

---

### Post by msohn88 on 2009-03-01
Do I type that in Terminal, sir?

Oh, when I click on that application, it won't start at all too!

---

### Post by coolen on 2009-03-02
Yes, type that in the terminal.

All files on Linux have three permission types, at three levels (basically): read, write, and execute, for the owner, the group, and anyone else.

That command just sets the execute bit so Linux knows this is an executable.

---

### Post by moosenl on 2009-03-25
> **DarrenCT said:**
> is he not just asking how to install and use the installation utility?  

Found in the downloads section of the site?

[http://www.rockbox.org/twiki/bin/view/Main/RockboxUtility#Download](http://www.rockbox.org/twiki/bin/view/Main/RockboxUtility#Download)

1) click the link to download the linux version of the util
2) extract the contents into something like /opt
3) create a startup link under Sounds (right click on the "applications" menu, and click on "edit menus").  
4) go to Sound and Video (or choose another one if you like) 
5) click "new item"
6) give it a name ie. "RockBox Utility"
7) browse for the command, and look under the "/opt" directory you extracted to (i.e. /opt/rbutilqt-v1.0.8/rbutil) and select the file listed there).
8) test the link from the Applications menu.


Please correct me if I am wrong on what is needed here.  I am using the utility with no problems running 8.10.

Thanks a million.  I feel like a spaz, ive been trying to compile that rockbox utility for hours now.  Too funny. your "guide" had me up in 12 seconds.

---

### Post by DarrenCT on 2009-03-25
You are welcome ... I'm glad that the util is working for you!

---

