---
title: "Remote borked after Ubuntu Update"
date: 2009-07-30
forum: Mythbuntu
---

### Post by GuiGuy on 2009-07-30
I despair. It is enough to drive a man to windows

Today  my mythbuntu frontend ran an update. Ostensibly this was to kernel version 2.6.28.14-generic, which the blurb told me was a security update.

Thanks, devs. That's swell. Only problem is my remote no longer works and I haven't got a clue what I'm supposed to do now. 

The hardware seems ok. It's a Microsoft (MCE) Phillips remote. 

Can anyone here help me? 

Thanks

---

### Post by GuiGuy on 2009-07-30
OK, IRW tells me the hardware and lirc are good to go.

It just ain't workin' in MythTV/// :(

---

### Post by jb5 on 2009-07-31
My remote doesn't work after a restart (or more accurately, works for a short time and then stops working). 
If I cold boot, the remote works as normal there-after.

Have you tried a cold boot?

---

### Post by GuiGuy on 2009-07-31
> **jb5 said:**
> 
Have you tried a cold boot?

Hey, thanks for responding. Appreciated. 

I have tried everything short of sacrificing my first born to the gods on Valhalla. It seems that if I want to remove lirc and re-install the whole #$^&@ mythtv frontend has to be uninstalled as well. How crazy is that!?

In any case, IRW and other things indicate lirc is working. It's just not being utilised by mythtv.

No matter. I'm getting rid of mythbuntu from it this weekend and will be installing mythdora instead. It's already driving the backend after I got fed up with the slow SATA issue a few weeks back.  

But, again, thanks.

---

### Post by azmyth on 2009-07-31
Try

$ircat mythtv

then hit some remote buttons. The corresponding myth command in the lircrc file should be echo'd back.

---

### Post by GuiGuy on 2009-07-31
> **azmyth said:**
> Try

$ircat mythtv

Thanks, but irw was already telling me that the remote was working. In any case, the remote was also working in VLC and XINE as I had configured it. It just wouldn't work in mythtv after the ubuntu/kernel update. 

Anyway, no matter, I have changed that frontend to mythdora now and everything is sweet. There are two frontends left in the house running mythbuntu. I'll resist 'updating' them.

---

### Post by azmyth on 2009-08-02
Actually irw proves the remote is working ircat proves the remote works with the specified program.

---

