---
title: "Temp Solution for LightScribe in Ubuntu"
date: 2007-02-24
forum: Multimedia &amp; Video
---

### Post by Jeff59 on 2007-02-24
Even through I hate using Windows and it's software I have relented in order to use my light scribe burner.  This is only until Ubuntu, the best destro ever figures out how to support it in Edgy and beyond. 

The way I have chosen to do it is with VMware (this is as close to having it in a Linux environment as I could get).  I downloaded the following free software and can label the disc with ease.  If you want to purchase software, Nero 7 works well for picture scribing.  I'm currently using the 30day trial.  

[http://www.lightscribe.com/downloadSection/windows/index.aspx?id=810]("http://www.lightscribe.com/downloadSection/windows/index.aspx?id=810")
[http://www.lightscribe.com/downloadSection/windows/index.aspx?id=811]("http://www.lightscribe.com/downloadSection/windows/index.aspx?id=811")
[http://www.lightscribe.com/downloadSection/windows/index.aspx?id=812]("http://www.lightscribe.com/downloadSection/windows/index.aspx?id=812")

I hope for the day when I can be 100% Linux

---

### Post by Mike'sHardLinux on 2007-02-24
Hi. I am just curious why you think the burden to support Lightscribe is on Ubuntu? Any developer should be just as capable to write the necessary software. HP is just as capable of  supporting Linux as windows. 

**You** could learn to program and develop something useful for the Linux world :) . (instead of expecting others to do it for you)

---

### Post by disturbed1 on 2007-02-24
Why not just use the native Linux lightscribe software? :)

[http://www.lacie.com/products/product.htm?pid=10803](http://www.lacie.com/products/product.htm?pid=10803)

---

### Post by Mike'sHardLinux on 2007-02-25
disturbed1, Thank you so much for that link!!!!!! As soon as I read your post, I ran out and got a Lightscribe burner.

I am in Edgy, and unfortunately, the LaCie software does no support Edgy, BUT, po0f has made a how-to to set up Dapper in a chroot and run 4L-gui and 4L-cli in that chroot environment, and this works great for me! Here's the link:
[http://www.ubuntuforums.org/showthread.php?t=322829]("http://www.ubuntuforums.org/showthread.php?t=322829")

Thanks po0f!!!

jeff59, have you tried this yet? As I said, it worked for me. :) 

I swear, Linux gets better every day!

---

### Post by disturbed1 on 2007-02-25
chroot? Huh? What?

All I did was download the 2 rpm's converted with alien and installed. Presto it works. This was with Dapper, and Fiesty.

---

### Post by Mike'sHardLinux on 2007-02-25
:)   I am in Edgy. It is known to not work in Edgy.

---

### Post by Jeff59 on 2007-02-25
When I said ubuntu I meant the communality seeing there is not a ubuntu singular getting rich.  As far as doing something useful I try to let others know what I have learned.  (How about you?)  I am learning to program but it will not be an overnight thing.  But when I come up with something it will be shared.  As far as chroot option.  I tried it last week and crashed my machine.  I'll wait for a better solution.

---

### Post by Mike'sHardLinux on 2007-02-25
> **Jeff59 said:**
>  ... As far as doing something useful I try to let others know what I have learned.  (How about you?) ..

I am also learning to program. Also, I was trying to help you with the links. :) 

Are you sure you followed the chroot how-to exactly?

---

### Post by Jeff59 on 2007-02-26
Thanks I  know you trying to help but I really screwed up my machine the first time and I had to reload everything. I'm a little gun shy at trying again.  I'm still new to linux although I have learned a lot in the past couple of months.  Is there a way to backup my current setup if I trash it again trying the chroot method. ?  Should I create a new user and try it on that account first, that should protect my current set up right?:)

---

### Post by fjm03 on 2007-02-26
I don't see anything wrong Jeff with utilizing Windows to operate popular peripherals. Just keep it off a WAN.

Installing a VMware server or player on Edgy is a breeze and any copy of XP can be used to operate toys. Total cost $0, plus a little time.

If Fiesty final contains virtualization features comparable to VMware  with the native support rumored to be in the upcoming 2.6.20 kernel, operating a Lightscribe burner via XP on Fiesty will be no different than bringing up K3b on Dapper.

---

### Post by mgmiller on 2007-03-04
Try using the driver software from lightscribe.com with the gui application from lacie.  It's a newer driver than Lacie provides and is rumored to work with Edgy.  (it's .rpm, so you will need alien to install it)

[http://www.lightscribe.com/downloadSection/linux/index.aspx?id=814]("http://www.lightscribe.com/downloadSection/linux/index.aspx?id=814")

---

### Post by watson540 on 2007-03-06
It wont work, I tried it. I am, however burning a label right now under edgy, but no without a bit of work. Poof has written an excellent howto on how to do thisunder edgy. Just search the forums for lightscribe. Good luck :)

---

### Post by ubromtoo on 2007-04-23
I downloaded Lightscribe, converted it with alien and installed it with 

   GDebi Package Installer.  It simply disapeared !  it is not found under Applications

  under any heading.  I'm running 6.06 Dapper dual-boot with Windows XP SP2.

     when I'm in XP, Lightscribe works fine.

   Any suggestions, anyone?    :-k

---

### Post by Mike'sHardLinux on 2007-04-23
I don't think it install any icons by default. The command I use to run the gui is:
```
4L-gui
```

Try that in a terminal window. If that works, you can make a launcher on your desktop, or where ever you want it.

---

### Post by ubromtoo on 2007-04-23
Mike'sHardLinux :

         Thanks ! :)

---

