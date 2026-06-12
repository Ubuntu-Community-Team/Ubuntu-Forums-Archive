---
title: "Vertical Hold Issue through S-video out"
date: 2009-02-28
forum: Mythbuntu
---

### Post by Unstablist on 2009-02-28
OK, Hello Everyone, I am a Linux Virgin, using MythBuntu because as soon as I can afford it I'm going to add a capture card.  Right now, my computer has this ( [http://www.newegg.com/Product/Product.aspx?Item=N82E16814102792&nm_mc=TEMC-RMA-Approvel&cm_mmc=TEMC-RMA-Approvel-_-Content-_-text-_-](http://www.newegg.com/Product/Product.aspx?Item=N82E16814102792&nm_mc=TEMC-RMA-Approvel&cm_mmc=TEMC-RMA-Approvel-_-Content-_-text-_-) ) video card, and the S-Video out works but it seems to be black and white, while having no vertical hold (Like a nonstop slot machine).  I tried to modify video settings but that just made the cmonitor go fuzzy with no change on the tv screen.

Additionally I was wondering what I should do to trouble shoot a lack of sound output, one of my friends who helped put the computer together insists that she plugged in headphones and they worked, but today, for love nor money can I get speakers to work

I really appreciate all the help I can get.

*edit* Audio out problem was addressed, problem was caused by the fact volume control somehow didn't get installed, still no luck on the vertical hold problem

---

### Post by scary_jeff on 2009-03-02
It sounds like the TV out on your graphics card isn't the same format as the TV is expecting. It sounds like you are giving half of an s-video signal to a composite video input. A lot of graphics cards have a Y-lead to split the tv-out into s-video and composite video, have you tried all possible plug combinations? Perhaps your TV has to specifically select s-video as opposed to composite (like mine does).
Is the socket on the TV composite (a single pin inside a round shield), or s-video (a round multi-pin connector that looks a bit like a ps/2 keyboard socket)?
There might be a flag you can put in your Xorg.conf for your video driver (I know there is for nvidia) to set the tv out format to one of these two, which could solve your problem. I just saw its an ATI card. I don't know what Xorg flags this has, but _[this page]("http://www.mythtv.org/wiki/ATI_Proprietary_Driver")_ seems to have a lot of intormation that might help you

Altering any of the video timings won't have any effect on most tv-out sockets, as they use a tv-out chip, which does not provide many timing adjustment. this explains your comment about your efforts only altering the monitor and not the TV.

---

