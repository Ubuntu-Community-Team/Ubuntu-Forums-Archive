---
title: "Black screen during booting up"
date: 2010-03-30
forum: Multimedia Software
---

### Post by logix_caster on 2010-03-30
Hi Friends,
   I've installed Ubuntu 9.10 in my old desktop, i.e.
Compaq Evo D510 e-pc:
Intel Pentium 4 1.7Ghz
1GB 400Mhz RAM
80GB HDD
Intel 845G chipset board
Onboard 4X AGP Intel Video chipset
Onboard audio

The above is my setup and Ubuntu runs perfectly fine when it is being cold booted, i.e. I shut it down during the night and boot it in the morning, it boots perfectly fine.

But while using, it suddenly freezes and I'm only able to move my mouse pointer and nothing else works on the screen.  I tried doing the Ctrl+Alt+(F1/F2/...) but nothing works.

So when I restart it using the power switch, it goes into the black screen and nothing loads up.  I'm stuck over here.
And if I turn it off for around 30mins by removing the power plug, and then reboot it again, Ubuntu loads without any problem and runs for sometime, then again the same freezing problem happens and I have to wait for another 30mins to boot it up again.

I have a 28" monitor connected to it and it runs at 1920 x 1200 (16:10) resolution at 60Hz.

Any help will be highly useful for me.

Thanks in advance.
LoGiX

---

### Post by yetiman64 on 2010-03-30
Rather than risking possible filesystem corruption with a hard power down, you should check out this link to wikipedia, [http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key).
The use of SysRq magic keys should work even when CTRL + ALT + F2 then restarting gdm won't as the key combos are caught at the kernel level. Hope this is some use to you even if it doesn't get to the original cause of your problem.

Edit: you seem to be running very high resolution (1920x1200) for a onboad 4x AGP video chipset. May pay for you to look further into that.

---

### Post by logix_caster on 2010-04-10
Hey guys, after playing around with it for a while, I inferred one thing very prominently, i.e. the computer hangs only when I try to do something like playing videos or do graphically intensive stuff when I had connected it with my 28" monitor.

So does this mean that the CPU is not able to render so much data for the screen and so its getting frozen?

Do guide me guys so that I'll explore and post more results on it.

Thanks everyone.

LoGiX

---

### Post by logix_caster on 2010-04-10
Hi yetiman64,  I'm sorry that I dint notice your edited post, and just like you said, its getting frozen only when I connect it to the monitor and not in anyother condition.

But the only thing that I'm confused is, after its frozen, when I remove the VGA cable and start the pc back again, it still doesn't start back again.  I have to leave it completely unplugged from the power for nearly 15-20mins and then when I start, it works flawlessly.

So this is the only confusion which I'm not able to understand on why its happening.

Please guide.

---

### Post by yetiman64 on 2010-04-10
Hi LoGiX     
I was just checking out the link below and was wandering if you're using the integrated graphics (ie. Intel Extreme graphics) that are original with that board or have you had a 4xAGP card added in (as this chipset supports)?. 

[http://www.informit.com/articles/article.aspx?p=339067](http://www.informit.com/articles/article.aspx?p=339067)

If you're still on the integrated graphics then the above link suggests to me that you're running 64MB of video RAM, and the resolutions quoted do seem extreme and may very well explain what you're seeing (considering you say its OK without the heavy gaming etc). Do you have a smaller monitor for this machine? If so I'd tend to stick with it.
You may be able to dig up a better specced (though still old) 4x AGP card and improve performance with the large monitor or you may have to consider running at lower resolutions (Not very good for games though, I'd guess).

> But the only thing that I'm confused is, after its frozen, when I remove the VGA cable and start the pc back again, it still doesn't start back again.Running a vid (card or chip ?) too overloaded maybe affecting the hardware adversely.

Good luck in sorting this out, though I'm probably not much more use here, sorry.

Cheers,

yetiman64

---

### Post by logix_caster on 2010-04-11
@ yetiman64:
  Just like you said, it was problem with the Video only.  Since the video chipset was not able to deliver so much content, the graphic chipset was getting too hot and I noticed it after putting a temperature sensor next to the chipset.  The temperatures started rising very steeply and at a particular point when I was running Youtube to render flash content, it hung and that time, it was at its maximum temperature.  So until the temperature reduced, the systems was not turning on properly and thats the reason on why I had to wait for 15-20mins before turning it ON back again.

Thanks a ton for your help yetiman64.

PS: Since this is a very small factor CPU with board (i.e. ATX micro cabinet), Compaq has not given me any expansion slots to add any extra Video cards, so I think I'll have to find a small size monitor over craigslist to keep it running I guess :)

Thanks once again.

LoGiX

---

