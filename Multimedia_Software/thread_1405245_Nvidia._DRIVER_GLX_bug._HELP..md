---
title: "Nvidia. DRIVER GLX bug. HELP."
date: 2010-02-12
forum: Multimedia Software
---

### Post by bhencetotozo on 2010-02-12
Hello guys,

My system runs 100% good with 173 Nvidia driver.
My system runs 70% good with 185 Nvidia driver.
Tryed 190, I regret. 190 runs as bad as 185. 173 is best.


I was having trouble with CEDEGA Direct Rendering with my Gforce 7950 GX2. I was in panic, so I uninstalled the X server, Nvidia module, Nvidia driver, Envyng everything...

Then, I went to tty1 and installed the 190 driver from Nvidia. it Works but system runs very bad... as bad as 185 driver.(173 is best) ... 

Now, I reinstalled envyng, i type envyng -t , i install driver 173, but then the driver does not apply correctly! ... I can not apply Extra Desktop Effects. ... 

I went to the terminal and typed sudo nvidia-settings

... It gives me an error in the terminal and it opens the program fine. (GLX DISPLAY 0 0 error)
Then i save the config to xorg.conf file... it saves OK.

I rebooted pc, I still can not use Extra Desktop effects... I went to sypnatic and installed nvidia-dev-173 ...still not working... Before this problem, if I clicked on System/Hardware Drivers, It would give me 3 driver options. 96,173,and 185 ... U could apply them from there... Now I do not see any nvidia drivers to try to apply anymore .....

I am about to restore my system backup ... I will be very upset if I cant resolve this problem the hardcore way... That's the only way I can be interested, if I can resolve annoying issues.

I obviously aint the Linux Expertest, but i've resolved many bad issues with this beautiful community, and I do believe some one will be kind to help me.

I will be writing C apps for us and ubuntu soon... I jst need to adapt because the only language i know alot of is C# ... and I will study and soon you guys will be hearing from me and I will be supporting us all for a happyer expanded community..


Thank you guys. I hope I dont have to restore my backup. :( 

Im in panic !!!! WTF? ...

 THANKS GUYS.

---

### Post by dabl on 2010-02-12
Yikes -- sounds like a mess!

I think you've got mixed-versions of the driver, or parts of it, or the related modules.  I will tell you what I would do, if I had that problem, but I'm sure there are alternative methods, so you might want to wait and see if there are other suggestions.

1. Download whichever driver you want from here:

[http://www.nvnews.net/vbulletin/showthread.php?t=122606](http://www.nvnews.net/vbulletin/showthread.php?t=122606)

It says 190.53 should run your 7950.  I'm personally running 196.36 on my GTX260.  But if you are confident that 173.14.25 is best on your system, go for it.


2. Follow the guidance under #2 here:

[http://kubuntuforums.net/forums/index.php?topic=3107406.0](http://kubuntuforums.net/forums/index.php?topic=3107406.0)

See the bold **NOTE** -- those are the items that need removed before you run the installer.


Note, your editor is "gedit" in Ubuntu, instead of "kate" in Kubuntu.

Hope this helps!

---

### Post by bhencetotozo on 2010-02-12
> **dabl said:**
> Yikes -- sounds like a mess!

I think you've got mixed-versions of the driver, or parts of it, or the related modules.  I will tell you what I would do, if I had that problem, but I'm sure there are alternative methods, so you might want to wait and see if there are other suggestions.

1. Download whichever driver you want from here:

[http://www.nvnews.net/vbulletin/showthread.php?t=122606](http://www.nvnews.net/vbulletin/showthread.php?t=122606)

It says 190.53 should run your 7950.  I'm personally running 196.36 on my GTX260.  But if you are confident that 173.14.25 is best on your system, go for it.


2. Follow the guidance under #2 here:

[http://kubuntuforums.net/forums/index.php?topic=3107406.0](http://kubuntuforums.net/forums/index.php?topic=3107406.0)

See the bold **NOTE** -- those are the items that need removed before you run the installer.


Note, your editor is "gedit" in Ubuntu, instead of "kate" in Kubuntu.

Hope this helps!

Hhahahhahah yeah i agree with you I made a big mess in my system.
But to tell you the truth this is the fun part :)

First of all thank you for your sugestion, I will try that as soon as I get home from work.

I have a question for you...

When I run driver 173, the animations of compiz run at about 90 FPS or more... very very smooth...

When I run driver 185 OR 190, the animations run at about 20 FPS.

* Do you know Why did the FPS lowered so much with a newer driver? ...
* I will try 195. do you receive CEDEGA DIRET RENDERING error too?

I am very confused about the frame rate drop with the new drivers. Only 173 was able to partialy make me happy ....

Thank you so much once again. I will edit this post and tell you the results. 

Thank you Thank you.

---

### Post by bhencetotozo on 2010-02-12
WOW !!!!

Thank you so much man.. I love you (no homo).

Driver 195 BETA is AWESOME !!!! i wish i knew about it's existance before !!! It is PERFECT ! [http://www.nvnews.net/vbulletin/showthread.php?t=122606]("http://www.nvnews.net/vbulletin/showthread.php?t=122606")


HHAHAHAHAHHAHAHAHAH


 I hope your genious post helps every1 else too.
-----------------------------------------------------
How I did it:
1) Control+ALT+F1
2) sudo /etc/init.d/gdm stop
3) cd Desktop
4) su     (sudo did not let it work, so I did SU)
5) password (password for su (root))
6) sh ./NVIDIA-Linux-x86-195.36.03-pkg0.run
-----------------------------------------------------
My Video Card : Nvidia Gforce 7950 GX2
My personal Driver Rating for my video card.
100% good. Version 195
70% good.  Version 173
60% good   Version 96
40% good   Version 185
Tested and measured by EYE.(no software used I mesured by EYE experience)
-----------------------------------------------------
You have no idea im about to rip my cheeks with my smile....
^^ Driver 195 FTW !!!

Fixed Cedega Errors TOO !!! HAHAHAHAHAH WOW !...
WHy are the official nvidia drivers so bad? ... this 195 driver you hooked me up with (NVIDIA-Linux-x86-195.36.03-pkg0.run) is 100% perfect ...

Wow man ... I am glad you sent me that link...

Thank you thank you thank you thank you
Thank you thank you thank you thank you
Thank you thank you thank you thank you
Thank you thank you thank you thank you
Thank you thank you thank you thank you
Thank you thank you thank you thank you
...

How do I mark thread as solved? ... Gutsy 7.10 was so perfect that I desappeared from here for a while, now I dont remember how to THank people and how to mark as SOLVED...

Once again. Thank you.

---

### Post by dabl on 2010-02-13
> **bhencetotozo said:**
> WOW !!!!


Once again. Thank you.

Great -- glad that fixed it!

Now, can you please edit the TITLE of your original post to add "SOLVED" -- that way it will show "SOLVED" in the forum.

;)

---

