---
title: "Restricted Driver Problems"
date: 2007-07-06
forum: Multimedia &amp; Video
---

### Post by The last Bert on 2007-07-06
After a completely fresh install of Fiesty (64 bit), things seem to work fine, just the usual tweaking to get graphics, wireless, etc.

After using the restricted drivers manager to turn on the NVidia driver, it downloads something (nvidia-glx I think) then asks for a restart. After the restart, I see the ubuntu splash, but when loading is finished, the screen goes black. I tried using  Ctrl-Alt-F1 etc to get a terminal (I think that key combination is right), but nothing is displayed.

Does anybody know why this is happening? I've seen one or two other ways of getting drivers going on the forums, but how do I get back to a GUI or a terminal? Should I be using the kernel recovery mode, and then editing xorg.conf or something?

My graphics card is a GeForce 6200a.

Thanks for any help, and sorry if I've done something stupid, its been a few years since I've used Linux, and its all a little hazy.

Bert

---

### Post by gmferguson on 2007-07-06
> **The last Bert said:**
> 
After using the restricted drivers manager to turn on the NVidia driver, it downloads something (nvidia-glx I think) then asks for a restart. After the restart, I see the Ubuntu splash, but when loading is finished, the screen goes black. I tried using  Ctrl-Alt-F1 etc to get a terminal (I think that key combination is right), but nothing is displayed.

Bert

We see the same, or a very similar problem with our boxes. As a result I stopped all updates to my own box's OS until this gets resolved. Both our sysadmin and our main Ubuntu guru are stumped after it hosed their machines too, and gave the thumbs down on the current kernel. 

I hate being in this situation - eventually something like a security fix will come along that requires a update, and it'll require the new kernel. If this driver issue isn't identified and fixed I'll have to switch to a different OS.

---

### Post by The last Bert on 2007-07-06
So is there no way to fix this? I assumed the restricted drivers manager was just using the wrong driver for my hardware, so there would be some way for me to get this working, provided I could remove the driver that was installed from the terminal.

Again, any help appreciated

Bert

---

### Post by caled on 2008-01-04
I too am having this issue with gutsy on an nvidia 6200a using the restricted drivers, seemed to work ok with the originally installed drivers. Is there a known fix for this yet?

---

### Post by spyckotic on 2008-01-04
I too am in this same situation.  Ive searched for hours in these and other forums to no avail

There is about 100 different solutions offered up but not a single one has helped.  My problem is with a Nvidia geforce 8600 gts though, but all I get after installing the restricted drivers or the drivers from the nvidia website is the blank screen.  Keyboard is useless, the only thing I can do is turn the power off on my system.  the generic nv drivers work fine.  I am at a loss, all I could ever find was post from people having this problem and thats it, no solutions, just problems.

I have been without ubuntu for a while now and I'm really missing it.  sure I could just use the "nv" drivers but who the hell wants to do that.

I check back often hoping there is a solution for this, but there never is

---

