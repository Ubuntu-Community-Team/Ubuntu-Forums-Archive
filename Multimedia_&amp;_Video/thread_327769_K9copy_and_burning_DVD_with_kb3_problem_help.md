---
title: "K9copy and burning DVD with kb3 problem help"
date: 2006-12-29
forum: Multimedia &amp; Video
---

### Post by rovernaut on 2006-12-29
I'm having a problem burning the DVD iso image on KB3 after copying with k9copy.
The Iso image is only 3.3 GB, but Kb3 asks for a dual layer media to be inserted. It won't accept the 4.7 Gb single layer -R media.
I can seem to find any settings in KB# that allows me to change anything.
 What am I doing wrong?

---

### Post by pseudonym on 2006-12-29
I can't help you with K3B but I can tell you how you can get your iso burned in the meantime. You will be using the command-line dvd+rw-tools, which gets installed along with K3B. Open up a console and do the following - ```
1. cd <directory_where_your_iso_is>
2. growisofs -dvd-compat -speed=4 -Z /dev/dvd=imageName.iso
3. Pour yourself a beverage and wait about 10-15 minutes
```
Personally, I think you have to be mad to burn DVDs at any higher speed than 4x, but if you think otherwise you can remove the '-speed=4' option.

hth :)

---

### Post by rovernaut on 2006-12-29
> **pseudonym said:**
> I can't help you with K3B but I can tell you how you can get your iso burned in the meantime. You will be using the command-line dvd+rw-tools, which gets installed along with K3B. Open up a console and do the following - ```
1. cd <directory_where_your_iso_is>
2. growisofs -dvd-compat -dvd-video -speed=4 -Z /dev/dvd=imageName.iso
3. Pour yourself a beverage and wait about 10-15 minutes
```
Personally, I think you have to be mad to burn DVDs at any higher speed than 4x, but if you think otherwise you can remove the '-speed=4' option.

hth :)

Thanks for that, it worked a treat.
I'm still learning using non GUI stuff, being a Linux newbie.
Now I need to work on another problem of how to shrink DVDs  like DVD shrink etc does.

---

### Post by pseudonym on 2006-12-30
> **rovernaut said:**
> Now I need to work on another problem of how to shrink DVDs  like DVD shrink etc does.
You can already do that with [k9copy]("http://k9copy.sourceforge.net/"). another tool which is in the Ubuntu repositories is [qvamps]("http://vamps.sourceforge.net/"), but it's no better or worse than k9copy (maybe a *tad* worse in the user interface stakes).

Many people also report success using the windows-based  DVD Shrink with [wine]("http://www.winehq.com/") . Personally, I think that's more trouble than it's worth, but if you want to got that route then have a look at [this howto]("http://www.ubuntuforums.org/showthread.php?t=78611&highlight=dvd+shrink") then head on over to [winehq]("http://wiki.jswindle.com/index.php/Wine_Multimedia#D") for some more reading. :)

---

### Post by rovernaut on 2006-12-30
> **pseudonym said:**
> You can already do that with [k9copy]("http://k9copy.sourceforge.net/"). another tool which is in the Ubuntu repositories is [qvamps]("http://vamps.sourceforge.net/"), but it's no better or worse than k9copy (maybe a *tad* worse in the user interface stakes).

Many people also report success using the windows-based  DVD Shrink with [wine]("http://www.winehq.com/") . Personally, I think that's more trouble than it's worth, but if you want to got that route then have a look at [this howto]("http://www.ubuntuforums.org/showthread.php?t=78611&highlight=dvd+shrink") then head on over to [winehq]("http://wiki.jswindle.com/index.php/Wine_Multimedia#D") for some more reading. :)
Thanks again, yep playing around and delving deeper with K9 again and it does shrink it down.
I want to get away from Wine emulators , I tried VMWARE server and installed stuff that worked, but I want to have my machine Linux dependant only.

DVD fab ( Windoze) works wonderfully  for everything I've thrown at it)

K9 however seems to do strange things for me, I set it to save the files chosen as an ISO image, it works on some files and and others it saves the in a DVD folder with created TS and VOB files. Then I can't burn the image with KB3 as the original problem of dual layer media arises or command-line dvd+rw-tools as it is no longer a ISO.

---

### Post by pseudonym on 2006-12-30
> **rovernaut said:**
> K9 however seems to do strange things for me, I set it to save the files chosen as an ISO image, it works on some files and and others it saves the in a DVD folder with created TS and VOB files. Then I can't burn the image with KB3 as the original problem of dual layer media arises or command-line dvd+rw-tools as it is no longer a ISO.
It's been a long time since I used k9copy, but aren't you able to burn straight to DVD from it? Is there any compelling reason why you are outputting to a .iso image?

btw, if you do end up with just TS folders they are still useable. check that the .vobs are all there, then load them up in k3b as a DVD video project and burn :)

If you still have problems you can convert the TS to an image first. You're a Kubuntu user, right? One way of doing that can be found [here]("http://suprvibes.net/index.php?module=tutorials&act=display&id=48").

:)

---

### Post by rovernaut on 2006-12-30
>  That's just it, I cant unless I get dual layer DVD Media, as this is what Kb3 keeps asking me for.It won't accept a burn on single layer 4.7 GB DVD blanks.

Oh Stupid me, there are 2 options , one for saving Iso to file and and another for selecting an output device. I didn't realize that that I could burn to DVD with the same Input and Output device. I wrongly presumed that I would have to have another DVDR to do it on the fly 
I just tried it and deselected burn with Kb3.
 And selected my DVDRW as my output.
After copying it asked for a blank disk to be inserted.
Thanks for all your help pseudonym.

---

### Post by pseudonym on 2006-12-31
> **rovernaut said:**
> Thanks for all your help pseudonym.

You're welcome, rover. :)

I accept Paypal and all major credit cards. ;)

---

