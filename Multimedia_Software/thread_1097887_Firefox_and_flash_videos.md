---
title: "Firefox and flash videos"
date: 2009-03-16
forum: Multimedia Software
---

### Post by PaulTR on 2009-03-16
Have looked over a few of the other threads I could find on this, but none of their solutions worked so figured I'd post and see if anyone has any other suggestions:

I can't get flash videos to start with firefox online. On things like Hulu it's just a black screen, on youtube and things like the myspace music player it's a circled play button that doesn't do anything when clicked, and on Pandora it just stays blanks. Tried uninstalling and reinstalling flashplayer-nonfree, and moving the flashplayerwhatever.so from a tar.gz into ~/usr/lib/mozilla/plugins (which i can't delete now) and doing a few terminal commands that were suggested but still a no go.

---

### Post by gandaran on 2009-03-16
I beleive you must have installed the swfdec-mozilla flash plugin (and gnash plugin too), find it in synaptic if it's installed mark for complete removal and hit the apply button, check also that you don't have flashblock addon installed, if it is at least disable it.

---

### Post by sp176 on 2009-03-16
Had the same problem.  Your solution was great gandaran

---

### Post by zenithdave on 2009-03-19
Yep removing swfdec-mozilla worked here too :D thanks.

---

### Post by njbill on 2009-06-01
> **gandaran said:**
> I beleive you must have installed the swfdec-mozilla flash plugin (and gnash plugin too), find it in synaptic if it's installed mark for complete removal and hit the apply button, check also that you don't have flashblock addon installed, if it is at least disable it.


Thank you! That solved my issues also. :)

---

### Post by sunoccard on 2009-06-01
i got the picture but sound is still a no go.

---

### Post by rfriedman on 2009-08-29
> **gandaran said:**
> I believe you must have installed the swfdec-mozilla flash plugin (and gnash plugin too), find it in synaptic if it's installed mark for complete removal and hit the apply button, check also that you don't have flash add-on installed, if it is at least disable it.

I can not find any flanh plugin's in my add remove utility, certainly nothing named swf-dec-mozilla.  Any further suggestions?

---

### Post by wojox on 2009-08-29
Look at this post by lovinglinux:

[HTML]http://ubuntuforums.org/showthread.php?t=1193567[/HTML]

---

### Post by Grimhound on 2009-08-29
To be honest the performance of streaming Flash under Linux is the most miserable thing about the use of it. It's poorly fleshed out, and in the two years I've sporadically dipped into Linux has never been improved. No bugs are ever ironed out, and no focus is ever put into the performance. With the prevalence of Flash on the internet, it is one of the biggest things hurting the potential for the adoption of Linux. It lags and drags the system where in OS X or Windows it runs smoothly. It stutters, breaks, is incapable of keeping video synchronized with audio, and has caused more man hours of suffering and more troubleshooting than anything I've ever seen.

Then again, video universally sucks under Linux. It jitters and lags and breaks even without the involvement of Flash.

---

### Post by Ric_NYC on 2009-08-29
> **Grimhound said:**
> To be honest the performance of streaming Flash under Linux is the most miserable thing about the use of it. It's poorly fleshed out, and in the two years I've sporadically dipped into Linux has never been improved. No bugs are ever ironed out, and no focus is ever put into the performance. With the prevalence of Flash on the internet, it is one of the biggest things hurting the potential for the adoption of Linux. It lags and drags the system where in OS X or Windows it runs smoothly. It stutters, breaks, is incapable of keeping video synchronized with audio, and has caused more man hours of suffering and more troubleshooting than anything I've ever seen.


Disable the "Visual effects.
See if it helps!

---

### Post by techiewannabe on 2009-09-03
It solved my problem too!
Thanks.
Tom

---

### Post by grndplane on 2009-09-03
Flash is  a little jumpy. I have found if you scale your display a little closer to the video resolution that performance will increase. ex 1024 x 768 will work better then 1600 x 1024 or 1440 x 900. Also VLC works a lot better then the flash player. Just my 2 cents.

---

### Post by Johny79 on 2009-09-03
As a side note I personally find that it's best to avoid all the flash plugins except the one from the official Adobe site.

I had major flash issues when I first moved to 9.04 but if I just install the one from Adobe everything works great every time (based on dozens of installs on varying hardware).

In fact certain flash based games actually run significantly faster and smoother than under XP/Vista/Win7 :)

---

### Post by jeannacav on 2009-09-10
Well,
On my new install 9.04 I get the same kind of response from attempts to install flash and opera.

It is uninstallable

Error:
dependency is not satisfiable.libqt3-mt (>=3.3.4)

That is for the opera install and something similar for the flashplugin.
Same comment about uninsatisfiable.lib but the number may have been different.

So, no Opera and no flash.


jeanna

---

