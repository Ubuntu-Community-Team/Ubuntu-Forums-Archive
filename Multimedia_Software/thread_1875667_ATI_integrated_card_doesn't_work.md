---
title: "ATI integrated card doesn't work"
date: 2011-11-05
forum: Multimedia Software
---

### Post by xavierescola on 2011-11-05
It seems like my ubuntu doesn't recognizes my ATI card, I cannot even use desktop normal effects! I've tried ubuntu to search for drivers but it cannot find them.
My motherboard is an Asus
** P5SD2-VM**

Any idea?

---

### Post by pme 72 on 2011-11-05
Welcome to the forums. You did not mention which version of Ubuntu you loaded or the name of your ATI video card. If you would like to search for the video card name open up a terminal and enter this code:

```
lspci -nn | grep VGA
```

---

### Post by xavierescola on 2011-11-05
I have GNU/Linux ubuntu 10.04 LTS and the information of my ATI video card is:

01:00.0 VGA compatible controller [0300]: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter [1039:6351] (rev 10)


Thanks for answering!

---

### Post by pme 72 on 2011-11-05
Do you have an add on ATI card? I ask because the return indicated only that your integrated video chip is an Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter [1039:6351] (rev 10). No mention of ATI. 

I searched Google with your card name and Ubuntu and found several posts that might be informative. Here is the link to a long one that started in October of 2008 and had a last post of 5 days ago. 

[http://ubuntuforums.org/showthread.php?t=958967](http://ubuntuforums.org/showthread.php?t=958967)

---

### Post by xavierescola on 2011-11-05
Your question makes me realize that I don't have an ATI card. 
My mistake was that I saw in another post to do: 
lspci |grep ati
lspci |grep nvidia
lspci |grep intel
to see what video card I have. I only had some feedback from the console with the first order, that's why got wrong.

I'll take a look to he post you mention...

---

### Post by pme 72 on 2011-11-05
That is not the only discussion I found using Google, just the longest. Hope you do not get overwhelmed. I stumbled across a shorter description of installing drivers for your card in 10.04. I can offer no support though as I have no experience with SiS video chips. There are references to that page in the long discussion.   

[http://www.ubuntugeek.com/how-to-install-sis-771671-mirage-3-video-drivers-in-ubuntu-10-04-lucid.html](http://www.ubuntugeek.com/how-to-install-sis-771671-mirage-3-video-drivers-in-ubuntu-10-04-lucid.html)

I have never felt comfortable with long instructions involving complicated terminal commands especially when it involves the display. Another alternative might be to go shopping for a PCI-E add on card, AMD/ATI or Nvidia both seem to be better supported in the forums although you could easily spend weeks investigating the options.

---

### Post by xavierescola on 2011-11-06
I followed the instructions that I founded in the post #371 of the long discussion you mentioned before. They are just the same instructions mentioned on the link of your last post.

And I'm afraid I big problem has appear, when I arrived to the point:
a**nd restart gdm by typing;**
     Code:
     sudo service gdm restart 
my monitor becomes black and says "Frequencies not supported"

Then I have pressed Ctrl+Alt+F1 and I have continued and finished with the instructions, but the problem persists when I reboot.

The problem is that as I don't know what I am really doing when I follow the instructions, I cannot undo what I have done.

It's true I'm a little bit overwhelmed...

At least at this point, I have been able to start ubuntu 10.4 from a live-cd.

I think that I will buy a PCI-E card (AMD/ATI or Nvidia) as you said... meanwhile, any idea of how to fix the "Frequencies not supported" problem? (in the posts I've been looking I have find no solution)

---

### Post by pme 72 on 2011-11-06
Sorry to hear that. The author of the instructions appears to be answering questions about installation issues. Look towards the bottom of the page in Comments. Last post was just 5 days ago. I would try leaving a comment there: 

[http://www.ubuntugeek.com/how-to-install-sis-771671-mirage-3-video-drivers-in-ubuntu-10-04-lucid.html](http://www.ubuntugeek.com/how-to-install-sis-771671-mirage-3-video-drivers-in-ubuntu-10-04-lucid.html)

The long Ubuntu thread also appears to be current so I would post a question there too. 

Check here too:

[https://wiki.ubuntu.com/X/Troubleshooting/BlankScreen](https://wiki.ubuntu.com/X/Troubleshooting/BlankScreen)

Those are your best and safest options for recovery. 

You could also try booting into Recovery Mode from the grub menu (hold down SHIFT during boot to see the grub menu). Use your arrow keys to highlight Recovery Mode, then press ENTER to choose Recovery mode. You will see a window saying Ubuntu is running in low graphics mode. Click OK. At the next screen choose failsafeX. There are a number of options. Choose Reconfigure graphics and then choose use default configuration. That is just a guess though.

---

### Post by xavierescola on 2011-11-07
Before reading your last post, I re-installed ubuntu 10.4. and I did the same steps with similar results. 

This time, when I rebooted appeared a window saying something like "ubuntu is running in low-graphics mode" and the options given had no effect.

Then I re-installed ubuntu again.

Now, as you have suggested me, I have post in the forum you mentioned. In case I have no response I'll try to e-mail ajoliveira asking for help.

I'll remember the trick of booting into Recovery Mode for next time I need it.

If I solve it, I'll post the solution.

Thanks,

---

### Post by MoreOrLess on 2011-11-08
> **xavierescola said:**
> My mistake was that I saw in another post to do: 
lspci |grep ati
to see what video card I have. 

LOL. You should inform that person that grep ati will probably show every kind of video card because most(all?) are prefixed with this:
VGA comp_**ati**_ble controller
;)

---

### Post by xavierescola on 2011-11-09
> **MoreOrLess said:**
> LOL. You should inform that person that grep ati will probably show every kind of video card because most(all?) are prefixed with this:
VGA comp_**ati**_ble controller
;)

Ok, I'll do that. Thanks.

---

