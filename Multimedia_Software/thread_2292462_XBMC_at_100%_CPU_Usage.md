---
title: "XBMC at 100% CPU Usage"
date: 2015-08-28
forum: Multimedia Software
---

### Post by uudruid74 on 2015-08-28
Any help?
XBMC Media Center 12.3 Debian package version:2:12.3+dfsg1-3ubuntu1

OS: Ubuntu 14.04.3 LTS \n \l
Package: xbmc_12.3+dfsg1-3ubuntu1
Hardware: BeagleBone Black
All unmodified from standard "Flasher" install

Problem:  Even at menu, mouse pointer takes about 30 seconds or so to move, keyboard takes at least as long.  Its a good 30s or more to go from menu item to menu item!   I can't get anywhere and the CPU is at 100%.  I want it to sit there on for days, not burn itself up.  I don't know what its doing, but this isn't gonna work!

At this point, its totally unusable.  I was hoping to fire up XBMC to use as a media server (I have an old 750GB drive I plan on connecting via USB - its not plugged in yet, just the Logitech keyboard/mouse recvr and a blank 64GB SD card which has a filesystem but not mounted).  I have tried this with a swap partition on the SD (on), and also tried it without turning on any swap - no difference.  Its not memory bound, its CPU.  After install I have changed nothing except for passwords.  Flashed Ubuntu, apt-get to grab xbmc (kodi wasn't found), and xorg, and I'm running this by running xinit, no window manager, and then running xbmc from the terminal that is in X.  I have tried it with --standalone and it makes no difference.  

I have tried adding this fix:

 ```
<advancedsettings>
  <gui>
    <algorithmdirtyregions>1</algorithmdirtyregions>
    <nofliptimeout>0</nofliptimeout>
  </gui>
</advancedsettings>
```


How can I proceed?

---

### Post by Rob Sayer on 2015-08-28
Beagle Black?  You mean this?

[http://beagleboard.org/black](http://beagleboard.org/black)

... and you have the stock 512Mb RAM?  I think that thing looks cool but if that's the memory you have I'm not surprised you're having problem with xbmc.  See here ...

[http://kodi.wiki/view/Supported_hardware#Linux](http://kodi.wiki/view/Supported_hardware#Linux)

... for minimum xbmc requirements, and I'd want more.

Unfortunately, in a 512Mb computer it gets worse.  You didn't say which 'buntu DE version you installed but the only version that would be *remotely* usable would be lubuntu, and it still wouldn't be a powerhouse.  Unity or KDE would be pretty much unusable.

Their web page says it has ubuntu compatibility but that doesn't mean you'd want to install ubuntu on it.  I'd go for debian lxde or one of the really light distros like puppy.

The next thing I'd try is a different, lighter media program like smplayer or GnomeMplayer.  Xbmc/kodi is *not* lightweight.

All that stuff you find on the web about linux breathing life into older or otherwise less powerful hardware is true.  What they don't tell you is that technically linux is just the kernel.  It doesn't mean that the desktop environment or app software will run properly.  DEs like Unity or Cinnamon need similar hardware spec to Windows 7/8.  And I'd never use Xbmc/Kodi on my 1Gb netbook.

I'd probably recommend Debian LXDE myself for a 512Mb ARM machine because they seem to have good ARM support and it's a light distro that you can tailor to your needs.  But be prepared for a learning experience.

---

### Post by uudruid74 on 2015-08-28
Do you have actual experience running Ubuntu on this platform?  "Stock" 512MB of RAM?  This is a BeagleBone ... do you think it has DIMM sockets?  I didn't say which Ubuntu DE because this isn't x86 and you don't get those sorts of choices.  There is no GUI but what you install.

Only a moron would install Unity on an embedded system.  Think about it.  Its a media server running XBMC ... it should boot to XBMC.  There is no need for any sort of desktop.  You'll see I specifically said there isn't even a window manager running.

As I have mentioned in my post, it is not memory bound, but CPU.  It has free RAM available!!    

So ... this is X going directly to XBMC, which runs on similar hardware, even THIS hardware (check YouTube), but something is going wrong.  I am NOT a new Linux user.  I've been using Linux since before Ubuntu existed, but this particular distribution has OpenGL and DRI support out of the box, which wasn't available for BeagleBone's GPU just a couple months ago.

Think about it.  I already said its CPU bound, not memory, with CPU at 100%.  You wouldn't see 100% CPU usage if it was swapping.  And if the swap is off, it won't lag when the memory is low.  The OOM killer won't just kill stuff or it would die.  Slow response at low RAM comes from swap activity which doesn't show up as CPU.  XBMC had a very OLD bug related to CPU usage, which shouldn't affect this version.  A couple versions back, the fix I mentioned was supposed to stop this, but that was supposed to be default behavior by this release, but I tried it anyway.  No dice.  Besides, it was supposed to still be usable and responsive, just a huge CPU load.  So, its something else I'm not seeing.  What I need is someone with actual experience with this platform.

---

### Post by QIII on 2015-08-28
I would say that you would be more likely to get better assistance with a less abrasive response -- even though you edited it.

It is likely that your respondent realizes this is a PoP device, so that remark was unwarranted.

---

### Post by Yellow Pasque on 2015-08-28
> but this particular distribution has OpenGL and DRI support out of the box, which wasn't available for BeagleBone's GPU just a couple months ago.

You should double check to make sure OpenGL ES 2.0 is working correctly, or else the xbmc interface is going to function like a CPU-hogging slideshow (which sounds like what you're describing):
```
sudo apt-get install mesa-utils-extra
es2_info
```

---

### Post by uudruid74 on 2015-08-28
> **Temüjin said:**
> You should double check to make sure OpenGL ES 2.0 is working correctly,  or else the xbmc interface is going to function like a CPU-hogging  slideshow (which sounds like what you're describing):
Well, you are right about it not supporting hardware rendering, its all software.  I thought this was supposed to be fixed in the 4.x kernel releases, so I'll have to look into that.

However, its not a CPU hogging slideshow.  Its a CPU hogging NOTHING.  Literally you press a key and it can take up to a minute for the menu item to change.  This box isn't that slow.  I can understand poor frame-rates, like even as bad as 5 frames per second, or less ... but 60 seconds per frame to update the menu? And thats not doing mpeg encoding or anything.   This sounds like something is seriously wrong to me.

> **QIII said:**
> I would say that you would be more likely to get better assistance with a less abrasive response -- even though you edited it.

It is likely that your respondent realizes this is a PoP device, so that remark was unwarranted.

In spite of the fact that I specifically mentioned there was no window manager and it was not a memory issue because swap was off, I was told some mess about Unity not running well with limited RAM (which would be a swap issue).   WTF?   No idea what was or wasn't warranted cause that hit me from nowhere, and it was an insulting suggestion.   Perhaps it was abrasive, but I really felt like someone just called me the stupidest noob ever, they just hid it behind a condescending message instead of being direct.

I'll try to be less direct.

---

### Post by QIII on 2015-08-28
There is a subtle difference between direct and rude.  Take care to mind the line, please.

I have already moved one post in this thread out of public view for that reason.

---

### Post by uudruid74 on 2015-08-28
> **QIII said:**
> There is a subtle difference between direct and rude.  Take care to mind the line, please.

I have already moved one post in this thread out of public view for that reason.

Yeah I hear ya :)   My friend Bacardi just showed up, so I should be much friendlier for awhile.  I know I shouldn't take things personally, and I apologize to everyone.   Certain things just hit me sideways sometimes, like the comment about Linux just being the kernel.   Linux has become so popular these days that I'm not used to seeing advice like that.  There weren't people using Linux that didn't know things like that 15-20 years ago.  I haven't gotten used to the fact that Linux is no longer the elitist hacker OS, and I suppose Ubuntu is probably the distribution that attracts the most new users.  So, I'm just a bit out of my element and was expecting that a Ubuntu based distribution would magically make things work.  10-12 years ago, Ubuntu got its popularity because so much worked right out of the box without having to tweak with it.   I was attempting to avoid with this thing for too long and just wanted it to work out of the box.

I'm wondering if an strace will show anything weird from XBMC.   I just need to finish ... well ... a million other things before looking into why this stupid software is caught in a CPU loop.

---

