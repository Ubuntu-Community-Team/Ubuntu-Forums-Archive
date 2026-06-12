---
title: "Full screen possible?"
date: 2010-06-13
forum: Mythbuntu
---

### Post by jodajen2 on 2010-06-13
Previous I had a good working mythbuntu install 9.xx.  I found it frustrating to not have a full ubuntu setup.  So when I had a hd fail I decided to do a ubuntu from the start and then add mythbuntu.  I have finally got it working again.  I have a question though.  I loved the fact in mythbuntu it was full screen.  Now I have the top and bottom menu bars and can't get figure out how to make mythtv full screen?  Please help if there is a way to fix it.   Thanks.

---

### Post by Mustardo on 2010-06-13
Hi there,

I haven't used the Myth TV application before but the F11 key is commonly used to make an application full screen.

Also you can right click the top and bottom bars and select preferences and check the 'auto hide' option.

Hope this helps

---

### Post by ian dobson on 2010-06-13
Hi,

Have a look here:- [http://ubuntuforums.org/showthread.php?t=296523](http://ubuntuforums.org/showthread.php?t=296523)

You need to tell mythfrontend that it should run fullscreen and not in a window.

Regards
Ian Dobson

---

### Post by tgm4883 on 2010-06-13
OP said it was just the top and bottom bars and that he installed MythTV on top of Ubuntu. Most likely issue is that he has compiz on. Go to System > Preferences > Appearance, click the visual effects tab, and turn the effects to none.

---

### Post by boombox1387 on 2010-06-13
> **tgm4883 said:**
> OP said it was just the top and bottom bars and that he installed MythTV on top of Ubuntu. Most likely issue is that he has compiz on. Go to System > Preferences > Appearance, click the visual effects tab, and turn the effects to none.

@tgm4883, is this a common problem with Ubuntu + MythTV + Compiz?  Is there an open bug report anywhere about this problem?  I ask because when I was using MythTV with Karmic, I ran into the same problem with my panel, and I was hoping to avoid it this time around.

---

### Post by tgm4883 on 2010-06-13
> **boombox1387 said:**
> @tgm4883, is this a common problem with Ubuntu + MythTV + Compiz?  Is there an open bug report anywhere about this problem?  I ask because when I was using MythTV with Karmic, I ran into the same problem with my panel, and I was hoping to avoid it this time around.

Yea it's common if you have compiz, I don't know if there is a bug report for it though.

---

### Post by boombox1387 on 2010-06-13
> **tgm4883 said:**
> Yea it's common if you have compiz, I don't know if there is a bug report for it though.

I found one: [https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/348934](https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/348934)

Strange thing is, it's marked as fixed, but there have been several reports of the issue persisting in 10.04, which was my experience today.  Luckily, a workaround is posted there which worked for me.  (For anyone else with this problem, see Comment 3 in the bug report.)

---

### Post by jodajen2 on 2010-06-16
> **tgm4883 said:**
> OP said it was just the top and bottom bars and that he installed MythTV on top of Ubuntu. Most likely issue is that he has compiz on. Go to System > Preferences > Appearance, click the visual effects tab, and turn the effects to none.


Thanks all for  your thoughts.  I had tried the auto hide before this post.  It just left a small bar at the top and bottom after the menus hid I could see the background image.  

When I turned the effects to none, it moved the myth up to the top of the screen.  It doubled the space at the bottom.  I then went into myth screen setup and set it to the display size.  Height 718 to 768.  Worked great.  Thanks for the help.

---

### Post by boombox1387 on 2010-06-16
> **jodajen2 said:**
> Thanks all for  your thoughts.  I had tried the auto hide before this post.  It just left a small bar at the top and bottom after the menus hid I could see the background image.  

When I turned the effects to none, it moved the myth up to the top of the screen.  It doubled the space at the bottom.  I then went into myth screen setup and set it to the display size.  Height 718 to 768.  Worked great.  Thanks for the help.

If you're interested, there is a one-time fix (workaround) that will allow you to keep desktop effects on, even when watching MythTv.  Assuming you have CompizConfig installed, open the program, open the "Workarounds" option, and check the box next to "enable legacy fullscreen support."  This doesn't seem to work for everybody, but it worked for me.  Personally I prefer this option because my workflow depends on desktop effects, and turning them off every time I want to watch TV on my computer is a hassle.

---

### Post by Woodwa on 2010-10-26
thanks boom box fixed in maverick its goinmg to make happy wife.. ;)

 ```
sudo apt-get install compizconfig-settings-manager 
```

and enable legacy full screen workaround..

---

### Post by LowSky on 2010-10-26
OR just install compix fusion icon and load metacity when using mythtv

---

### Post by seraphimshift on 2010-11-01
> **Woodwa said:**
> thanks boom box fixed in maverick its goinmg to make happy wife.. ;)

 ```
sudo apt-get install compizconfig-settings-manager 
```and enable legacy full screen workaround..

Woodwa - where is this legacy option? I'm having the same problem under mythbuntu 9.10 

thanks,
J

---

### Post by boombox1387 on 2010-11-01
> **seraphimshift said:**
> Woodwa - where is this legacy option? I'm having the same problem under mythbuntu 9.10 

thanks,
J

Open up CompizConfig Settings Manager, scroll down to the "Utility" section, then click Workarounds (should be enabled by default -- if not, enable it).  Legacy Fullscreen Support is the top item on the list -- click the check mark next to it to turn it on.

That should be all you need to do.  After that, every time you open MythTV, fullscreen should automatically cover the panel(s).

---

### Post by seraphimshift on 2010-11-02
> **boombox1387 said:**
> Open up CompizConfig Settings Manager, scroll down to the "Utility" section, then click Workarounds (should be enabled by default -- if not, enable it).  Legacy Fullscreen Support is the top item on the list -- click the check mark next to it to turn it on.

That should be all you need to do.  After that, every time you open MythTV, fullscreen should automatically cover the panel(s).

This is odd, I don't have a "workarounds" section... version 0.8.2 is installed

for what its worth, the auto-hide is working well...

---

### Post by boombox1387 on 2010-11-02
> **seraphimshift said:**
> This is odd, I don't have a "workarounds" section... version 0.8.2 is installed

for what its worth, the auto-hide is working well...

Hmm, either the Compiz plugins got split up into separate packages recently, or they always have been but Ubuntu recently stopped installing one of the packages by default.  Anyway, I'm not sure which package has the Workarounds plugin, but a quick check in Synaptic shows that I have:

compiz-plugins
compiz-fusion-plugins-main
compiz-fusion-plugins-extra

I would guess that -main is installed by default, but Workarounds might be in -extra, which I must have installed separately.  Hope that helps.

---

