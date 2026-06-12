---
title: "How do you compile Linux-Staging drivers??"
date: 2009-07-02
forum: Networking &amp; Wireless
---

### Post by g0rd99 on 2009-07-02
I have an exciting new product: A [SIZE="4"]Belkin Network USB Hub[/SIZE], which I would like to get running in Ubuntu. It is connected to a wireless router, and when booted properly, provides the USB ports (5 of them) to any wifi endowed computer. Great for supplying data to the other coputers.

There are [SIZE="4"]drivers called usbip (USB over IP)[/SIZE], but the latest ones for 9.04 are located in Linux-staging, which was installed on the computer.

My problem is: How do you compile them???? I found almost no info on them, and have been searching for days. I think they would be most useful. It looks like the usbip project is not very popular right now, but there will be a lot of interest, now that there's the Belkin device.

Help! I'm dying to get it going.

---

### Post by ojmc on 2009-07-02
I too would love to get this hardware working. This is the only thing i desperatly miss after recently making the complete switch to linux (ubuntu 9.04) after 15 years of windows.   After countless weeks over 2 years (obsessive i know) of trawling the web for some smart help i have essentially given up. Now every so often i enter a search just for the hell of it and so i've found this post.  Is there any possible chance one of you brillient, full of beans guys in these forums can give some thought to this. If not to make this users dream complete then at least as an FU to those at Belkin who have coldly closed the door on linux.  Any linux threads i have found over the years usually don't have even one reply although there are a lot of people with the same problem.  i need to close the door on this and move on with my life. So please please please comment on this post even if it's only to say it's impossible

---

### Post by ojmc on 2009-07-02
Rubbing my ubuntu laptop in a special way.  Feels dirty, yet kind of....... ummmmmmmbu

---

### Post by g0rd99 on 2009-07-02
HI Ojmc
I'm glad to hear that someone else has one of these hubs. I'm determined to get it up and running. Keeping in line with my previous experiences, I suspect it may take a while, but one little hint from someone will get this project moving again. 
Stay tuned,
Gord

---

### Post by justcop on 2009-09-03
OK, I am by the sounds of it as noob as the two of you but I may be able to point you in the right direction.

I arrived here whilst trying to use a software version of the hardware that you have. It sounds like your hardware is based on [this]("http://usbip.sourceforge.net/") open source software

Now theoretically this can be installed to make a linux pc act as a usb server.

It seems all the clever people that use that software don't seem to have a problem with it but I can't get it to work.

Maybe ask there and they can help you out. It should be a relief to know though that the hardware your using is essentially built for linux! The only problemis they don't like to make things easy.

EDIT: In fact this is a little bit of a Good the The Bad and the Ugly. I have instructions on how to compile the drivers [here ]("http://usbip.svn.sourceforge.net/viewvc/usbip/linux/trunk/drivers/README?view=markup") but I don't know where to get them from. WTF is linux staging, i need it and can't find it in a  google search.

---

### Post by Ackondro on 2009-09-11
linux-staging is a place where drivers can be seen before they have the organization/quality to move into the mainline kernel
They are managed by Greg Kroah-Hartman, your usbip driver is still stuck in staging as of 2.6.31 (released this week) because the developers haven't finished/fixed all the issues.
Location of drivers [http://www.kernel.org/pub/linux/kernel/people/gregkh/staging/2.6/](http://www.kernel.org/pub/linux/kernel/people/gregkh/staging/2.6/)
The drivers there are patch's against the kernel source, I'm sorry to say this, but you may have to recompile your kernel to get it to work
you can find your current kernel by 
```
uname -r
```

---

### Post by ErwinJunge on 2009-11-06
This seems to be fixed in Karmic, see [http://packages.ubuntu.com/karmic/usbip]("http://packages.ubuntu.com/karmic/usbip").

I already have 1 machine (my server) over to Karmic, so I can at least confirm that the usbip driver is in Karmic. I just can't test the stuff till I get Karmic on my other machines as well.

I'm trying to forward some usb joypads over my network btw. I'll post back here after updating my machines to Karmic to say if it worked.

Edit: Well, I updated to Karmic and can confirm that it works perfectly. I managed to forward 4 usb joypads via a wifi connection to my main computer. Latency was not visible at all, we had a blast playing Mario Kart 64.

---

### Post by sim0ne on 2010-12-12
Hi guys!, I have a belkin usb hub too, and my notebook is 100% ubunted.

I've tried to install the belkin windows drive with wine but It faults, then I've tried to use the connect.exe program, also with wine, and it sees all the peripherals connected with the belkin, but it starts to loop, listing the same peripherals a thousand of time and I haven't been able to use them...

I've read your post, and I have visited the site indicated ([http://www.kernel.org/pub/linux/kernel/people/gregkh/staging/2.6/](http://www.kernel.org/pub/linux/kernel/people/gregkh/staging/2.6/)) but honestly I didn't understand how to use the file in there.

If someone have a solution or a "near solution", please post it a mini-guide.

Thanks!!

---

