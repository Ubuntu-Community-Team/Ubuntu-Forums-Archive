---
title: "nvidia problems driving  me crazy!"
date: 2012-06-10
forum: Multimedia Software
---

### Post by eulu on 2012-06-10
I am running 12.04 x64 and have an nvidia 7950GT and cannot get it running stable. For one glorious day I had it stable and it was so nice. The only nvidia driver set I can even get to install is 295.49 and it's still buggy as hell and I can't even run full resolution.. Trying to install anything else I get the held broken packages error. 

My recourse in the past has been  to install my old ATI X1650 but that is much slower and it's buggy too on Ubuntu (causes system lockups at times)..

I'm getting really sick of this. Anybody have any suggestions? Is there an affordable video card I can buy that will for sure run reliably on Ubuntu? 

Why is video support so weak with Ubuntu? Is it ever going to get better?

---

### Post by gordintoronto on 2012-06-10
Do you know how to specify "nomodeset"?

My elderly Nvidia 9400 GT works fabulously.

---

### Post by wabbalee on 2012-06-10
I bought two nvidia geforce 210 not long ago (for around 50 bucks each ebay) and both systems are running perfect. xonotic looks/works awesome.

how do you go by installing your drivers? I mean, ubuntu's built in facilities for installing additional driver's has worked well for me, especially when it came to nvidia. ati on the other hand is giving problems, depending what cards, i cant get it to work on my aspire laptop for example, whereas it works fine on an older travelmate with different ati graphics.

---

### Post by eulu on 2012-06-11
> **gordintoronto said:**
> Do you know how to specify "nomodeset"?

My elderly Nvidia 9400 GT works fabulously.

I am not familiar with nomodeset... I will look into it.. Thanks 

I came across a page earlier on askubuntu that said there are some driver issues for the  6x and 7x cards specifically.. 

I lost unity 3D earlier and couldn't get it back and then my ATI card wasn't running 3D either when I tried to move back to it, so I ended up reinstalling the OS. (UGH).. 

Now I am back with the open source Nvidia and am not going to install anything until I get to something workable. 

Right now my 1280 resolution LCD will only go to 1152 and if I try to enable dual monitor the system starts locking up. Such fun..

---

### Post by eulu on 2012-06-11
> **wabbalee said:**
> I bought two nvidia geforce 210 not long ago (for around 50 bucks each ebay) and both systems are running perfect. xonotic looks/works awesome.

how do you go by installing your drivers? I mean, ubuntu's built in facilities for installing additional driver's has worked well for me, especially when it came to nvidia. ati on the other hand is giving problems, depending what cards, i cant get it to work on my aspire laptop for example, whereas it works fine on an older travelmate with different ati graphics.

Previously I installed by following instructions... The drivers that become available from adding the xorg ppa don't install for me (173/96).. I get a message about held broken packages.. Last time I tried installing the latest drivers (I don't remember how but found instructions somewhere) got me installed to the 295.49 set but it was no better than the nouveau, except that sometimes it would detect my monitor properly. But it would invariably lock up and get fussy at inopportune moments... 

This time I am trying to be patient before I do anything to see if I can find something different to try than all the things I tried last time that mucked up my system and didn't work.

If I can't get this going after a while, I'll go back to my ATI card, but this 7950GT is a much nicer experience when it's running properly.

---

### Post by D0natell0 on 2012-06-11
Some modern motherboards have on-board graphics, which apparently can  conflict with your GPU. This results in poor performance you're  experiencing.

Usually you can turn off the motherboard graphics from the BIOS. I've proved this works with an Intel core-i7 and nVidia GPU.

Re-start the system and enter the BIOS settings (usually hitting the DEL  key repeatedly will do the trick). Then tab through the BIOS pages  until you find the [FONT=&quot]Chipset->North Bridge section, and [/FONT][FONT=&quot]turn off the internal video. Hit F10 to save and exit.
HTH.:wink:[/FONT]

---

### Post by eulu on 2012-06-11
> **D0natell0 said:**
> Some modern motherboards have on-board graphics, which apparently can  conflict with your GPU. This results in poor performance you're  experiencing.

Usually you can turn off the motherboard graphics from the BIOS. I've proved this works with an Intel core-i7 and nVidia GPU.

Re-start the system and enter the BIOS settings (usually hitting the DEL  key repeatedly will do the trick). Then tab through the BIOS pages  until you find the [FONT=&quot]Chipset->North Bridge section, and [/FONT][FONT=&quot]turn off the internal video. Hit F10 to save and exit.
HTH.:wink:[/FONT]

Thanks but I don't have onboard video.. Actually, I ended up installing the 295.53 driver set late last night and today, so far so good, other than compiz crashing after I first boot up and load my multi monitor config.. I couldn't get this driver set to install  before I reloaded the OS so I am hoping for some smooth sailing.. ;-)

---

### Post by eulu on 2012-06-11
I take it back. One time I boot up and it detects my main monitor and allows the right resolution, and lets me go multi monitor. The next time I boot it doesn't... Back to only allowing 1152 max res and thinking my LCD is a CRT.

---

### Post by eulu on 2012-06-12
Well I was still having issues so upgraded to the 295.59 release. Now my secondary monitor is just a white screen no matter what settings I prescribe. Even if I disable the second monitor it shows as a white screen with a black x for the mouse cursor when I move the mouse over to that monitor. Other than that things seem fine! :mrgreen:

EDIT: Second try of enabling twin view caused the second monitor to start working again so things are working at the moment.. 

ALSO, if anybody reads this who plans to install the 295.59 set, I tried manually installing 295.59 last night using the sh command to install from the run file. I got to the black screen after a reboot and couldn't get past it, and had to find commands to uninstall nvidia and start over... Today I found [these instructions]("http://www.upubuntu.com/2012/06/how-to-install-nvidia-linux-display.html") and got the drivers installed successfully.

---

### Post by kksharma1618 on 2012-08-15
> **gordintoronto said:**
> Do you know how to specify "nomodeset"?

My elderly Nvidia 9400 GT works fabulously.

Hey,

I have nvidia 9400 GT too. I think I can manage to activate nomodeset. [[http://askubuntu.com/questions/38780/how-to-set-nomodeset-for-installation]](http://askubuntu.com/questions/38780/how-to-set-nomodeset-for-installation])

I am just confirming how you get your card to working. Shall I just enable nomodeset permanently using the above approach (see url)? Will I need to install some driver too with nomodeset? If not, then should I blacklist it so that ubuntu additional drivers doesn't ask me to install it?

I have screen resolution issue too. In windows I get 1600x900 with the same monitor. Here I am getting 1024x768. But I guess that's because of graphic card issue. 

Please help. I am really stuck here :)

---

### Post by gordintoronto on 2012-08-15
> **kksharma1618 said:**
> Hey,

I have nvidia 9400 GT too. I think I can manage to activate nomodeset. [[http://askubuntu.com/questions/38780/how-to-set-nomodeset-for-installation]](http://askubuntu.com/questions/38780/how-to-set-nomodeset-for-installation])

I am just confirming how you get your card to working....


What brand is your video card?

My MSI 9400 GT has always worked perfectly, with many, many versions and distros of Linux. I generally install Additional Drivers, Version Current, but it always "just works."

---

