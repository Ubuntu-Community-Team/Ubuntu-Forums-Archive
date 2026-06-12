---
title: "Help getting Video Capture with ATI All-In-Wonder"
date: 2006-07-24
forum: Multimedia &amp; Video
---

### Post by aleska on 2006-07-24
I have an ATI All-In-Wonder.  I'm not sure exact model, but based upon the sticky forum on posting solutions I ran 
```
lspci -n | grep 0300

```
Result is:
> 0000:01:00.0 0300: 1002:4966 (rev 01)

Also ran
```
lspci | grep VGA
```
Result is:
> 0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 If [Radeon 9000] (rev 01)

My display seems to work pretty well, as far as I can tell.  I can view videos on the net, DVD's locally, etc.  However, I can't seem to figure out how to view TV coming in from the attached cable coaxial to the ATI card.  It worked when it was a Windows PC...but not now.
I've google searched, sifted through the forums, etc.  The problem is that I don't know if this is a driver issue, or just a end-user stupidity (or ignorance) issue.  
I've tried installing and running tvtime but I just get a blue screen and the message "No video source"..."No signal"..."No such file or directory: cannot open capture device /dev/video0".  I don't know whether I should have gone through some steps to mount /dev/video0 first, or what.  
Any suggestions on steps I should take are greatly appreciated.  I'd hate to go out and buy a new video card only to learn that I could have used what I have...but, just didn't know what to do.
Thanks!
-aleska

---

### Post by CadetD on 2006-07-31
I've been having the same problem. 

Supposedly, the ATI proprietary drivers allow TV viewing. 

What TV application supports the ATI All-In-Wonder cards?

---

