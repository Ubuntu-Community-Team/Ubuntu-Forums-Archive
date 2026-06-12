---
title: "ATI Stupid Drivers Aren't working!"
date: 2008-04-17
forum: Multimedia &amp; Video
---

### Post by Auctionedllama@gmail.com on 2008-04-17
Hi. I have spent 4 days trying to get my ATI x1650 to run with no success. After 3 clean installs, I finally got the catalyst center to appear in my applications menu, but it can't run. Says no driver is installed, but it is. Also, when I try to edit aticonfig it can't write to the xorg.conf.. it says bad file descriptor. Please help here. Thanks!

---

### Post by Nameless_one on 2008-04-17
Have you seen these?

[http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)
[http://www.thinkwiki.org/wiki/Problems_with_fglrx](http://www.thinkwiki.org/wiki/Problems_with_fglrx)

And generally, include more information in your post. 

I have the same card as you, and have installed the fglrx driver, version 8.2, and it runs just fine. Just follow the instructions on my first link. If there are still problems, then post them here.

---

### Post by miciurin on 2008-04-17
Hi,
I also have the x1650. The only thing that worked for me (besides the driver in the Ubuntu repo) was to use envy. In gutsy it installed automatically the latest catalyst 8.3 and worked flawlessly. I now upgraded to hardy beta and I am using the restricted driver provided. 

I strongly suggest envy if you are in Gutsy.

---

### Post by Auctionedllama@gmail.com on 2008-04-17
Well, it said in order to use catalyst to activate the restricted driver.. so I did.. and I restarted... and now its a black a screen and I can't CTRL+ALT+f1 or anything.. any help would be.. good

---

### Post by miciurin on 2008-04-18
Hmmm,

In this case I think that you have to restart in safe mode (from the grub menu), Xfix, and go back to the vesa driver. After that uninstall the Ati driver and reinstall with envy. YOu might also want to look in this thread:

[http://ubuntuforums.org/showthread.php?t=754980](http://ubuntuforums.org/showthread.php?t=754980)

---

