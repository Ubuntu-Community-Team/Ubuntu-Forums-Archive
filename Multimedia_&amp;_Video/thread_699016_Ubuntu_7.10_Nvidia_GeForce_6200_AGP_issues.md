---
title: "Ubuntu 7.10 Nvidia GeForce 6200 AGP issues"
date: 2008-02-16
forum: Multimedia &amp; Video
---

### Post by tcbetka on 2008-02-16
Hello,

New to the forums and am having a problem. I posted this on the Nvidia forums, but will also post it here as well...

 I have a desk-top machine running Ubuntu 7.10 Gutsy, and two Nvidia cards. The first is a 6200 GeForce AGP card (128mb), and the second is a 5500FX GeForce PCI dual-headed card (128mb). Both are in a 3GHz Pentium 4 machine, with 3GB ram.

While it took quite some time, a friend and I finally managed to get the cards to work in Ubuntu tonight. The 5500 dual-headed card works very well, and both monitors function normally. But the 6200 AGP card, while functional, experiences extremely sluggish performance--almost to the point of that screen being unusable. I am not running Xinerama; simply three monitors. But when the machine starts, the menu bar options in the 6200 screen aren't even completely rendered, and any windows in that screen take a minimum of 20-30 seconds to respond to mouse events; sometimes even longer. But the 5500's two screens seem perfect; in both appearance and functionality.

We downloaded the latest 169.09 driver for the cards tonight, and followed the procedure here described in the NV forums to get things up & running, after the Envy-based procedure did not work despite multiple attempts. Even though we deleted all the files and packages recommended on the NV forums, it did not work initially--that is until we deleted the xorg.conf file and restarted. But then things seemed stable, except for the 6200 issue mentioned above. So we have concluded that there seems to be a problem with the 6200 card (it's 3 years old, but hardly used) and Ubuntu--or maybe it's an AGP issue? I would gladly go and purchase a new AGP card if it will work, as I would like a 256 or 512mb card for a flight simulation project I am working on.

If anyone can offer any assistance it would be greatly appreciated. Also, maybe someone would recommend an AGP card known to work well with Ubuntu? I checked the Ubuntu forums, but haven't yet found any known issues with the 6200 card--nor have I found any obvious issues in the archives here.

Thanks in advance.

TB

EDIT: While researching in the NV forum after posting, I saw a thread about the compiz application, and recalled that when we first experienced this problem we saw tht compiz.real was at about 50%. When we killed that process, the problem resolved completely. But on restart, it re-occurred--although the activity of compiz.real was lass than 20-25%. When this problem first occurred, the 6200 AGP card was the only one in the machine. After installing the 5500 card, compiz.real doesn't seem to get anywhere near 20%--yet there is still a problem with the 6200 card.

---

### Post by tcbetka on 2008-02-18
An update: Still having the same problems, so I ordered an Nvidia GeForce 7600 GS AGP card (512mb). It should arrive tomorrow and I will install it and see if there is any improvement in the behavior.

I am still hoping someone might have an idea as to the cause of this issue--perhaps the 6200 TurobCache AGP card I am currently using is "linux-challenged"? It is on the list of those cards supported, as far as I can tell.

Thanks.

TB

---

### Post by petersonjacob on 2008-02-18
well when i downloaded envy everything went smoothely, try it again, and after you do the reccomended restart, go into failsafe mode with the grub loader and type dpkg-reconfigure xser-xorg and select nvidia driver and fly through the rest of the settings and restart again, hope this helps

---

### Post by petersonjacob on 2008-02-18
sorry *xserver-xorg

---

### Post by tcbetka on 2008-02-19
Well, got the new card...then had to get a *different* new card, lol. I ended up with an Nvidia 8600 GeForce card, with 512MB. So I got it installed, and some of the issues are resolved. I had to uninstall the Nvidia driver with the Envy application, and then reinstall it--as the new card wasn't detected correctly until I did (the Nvidia application still saw the 6200TC card), nor did the mouse buttons work! (I could move the pointer around, but the buttons didn't work.)  But then I restarted in safe mode and ran the 'dpkg-reconfigure xserver-xorg' command, and ran through the set-up. I am not sure I answered all the questions correctly however, but I left the defaults in place wherever possible.

So I got things running again, and the menus are now rendered in each screen and the mouse buttons work correctly. But for the most part, the commands come up very slowly. For example, selecting the Nvidia Settings application option from Applications > System Tools takes 10-15 seconds! All of the menu options start very slowly, for the most part.

So while some of the problems have resolved, there are still other issues that remain. Maybe this information will trigger an idea from someone, as this is getting somewhat frustrating...

Thanks in advance. 

TB

---

### Post by Presto123 on 2008-02-19
Wow...you are trying to install several different cards all at one time. That could be the BIG issue here. Conflicting drivers...

---

### Post by Presto123 on 2008-02-19
Try running this command (resets your video) and reconfigure to what you want:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by tcbetka on 2008-02-19
Well, there's only one driver... version 169,09, and two cards. The latest driver from Nvidia is dated January 28th (2008). That's the only driver I know of--for any of these cards. It literally works for all of them. I don't know what you mean by "several cards." I only have two cards in the machine; a 512mb PCI-e, and a 128mb PCI card--although the PCI card is dual-headed.

So I am not sure I see how there would be a conflicting driver issue when both cards use the same driver. But I can certainly remove one of the cards and try the system, then re-install it and remove the other card, and repeat. 

I will try it and re-post.

TB

---

### Post by tcbetka on 2008-02-24
Well, I installed a new card but there hasn't been a total improvement.

I installed a GeForce 8600 GT card, with 512mb ram. The menu rendering issue resolved, but there are still three issues:

1) When trying to select menu items, the choices execute very slowly most of the time. This seems to be on both of the cards, but certain applications are worse than others--but all applications execute slowly. The 'glxgears' application runs at about 5000 fps on the screen with the 512mb 8600 GT card, and only about 1000 fps on the 128mb 5500 FX card.

2) The features provided by Compiz do not seem to be applied to both cards. For example, Ubuntu recognizes the 5500 FX card as the primary one, and when I open windows on that monitor (say a terminal view, for instance), I get a nice title bar and I am able to drag the window any where on the screen. However when I try to open a terminal on the other card's screen, the window opens but it is anchored to the top menu bar in the upper left corner of the screen (ie; typical non-Compiz appearance). I cannot move it around the screen at all.

3) When I modify the xorg.conf file as sudo (by running nvidia-settings from a terminal), and save the changes to the file and restart--the changes are gone. It seems as as the Nvidia application never even wrote them to the file

Incidentally, I also have Fedora Core 8 installed in another partition on this machine and used the same procedure to modify the xorg.conf file as 'su', and it writes the changes to the file and they are set on restart. So for some reason it seems that the Nvidia application is unable to do in Ubuntu, what it can in FC8. Also, any application I choose seems to start quickly in FC8, and they run more efficiently than with Ubuntu.

Note, the issues with Ubuntu were seen after installing the Nvidia 169.09 driver via the Envy application, and then running 'dpkg-reconfigure xserver-xorg' from the command line as sudo. I now see the '-phigh' part in the above post--but I didn't include that. A friend advised me of the rest of the command, but didn't mention the -phigh part; what does that part do?

On FC8, I installed the driver in basically the same manner, but didn't have to run the 'dpkg-reconfigure...' command. I even tried a reinstall without that utility in the Ubuntu partition, but the result was identical--so I do not believe it's an issue with that utility, unless it's specific to Ubuntu?

Thanks in advance for any help...

TB

---

### Post by PmDematagoda on 2008-02-24
About the reset of the changes the fix is to do this:-

1) Open a modules file for editing:-
```
gksudo gedit /etc/default/linux-restricted-modules-common
```

2) Edit the DISABLED_MODULES line to make it look like this:-
```
DISABLED_MODULES="nv nvidia_new"

```
save the file and then reconfigure the X-Server according to your needs and restart. Your problem should then be solved.

---

### Post by tcbetka on 2008-02-24
Thank you. I will retry this in an hour or so, and report back on my progress. 

I appreciate your post!

TB

---

### Post by tcbetka on 2008-02-24
OK, the line in that file was already set as you described. So I made no changes...

TB

---

