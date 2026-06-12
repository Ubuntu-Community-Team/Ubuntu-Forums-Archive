---
title: "swf alternative"
date: 2009-05-28
forum: Multimedia Software
---

### Post by Nima1972 on 2009-05-28
I'm having problems using the swf flash plugin for firefox on ubuntu 9.04.  

Can anyone recommend an alternative?  Thanks.

---

### Post by utnubuuser on 2009-05-28
If licensing isn't an issue, the  non-free plugin works well. - It's available through synaptic.

---

### Post by lovinglinux on 2009-05-28
Open "Applications >> Acessories >> Terminal" then copy and paste this code into the terminal and hit enter:

```
sudo apt-get remove swfdec-mozilla mozilla-plugin-gnash && sudo apt-get install flashplugin-nonfree
```

This will uninstall the swfdec and gnash plugins and install the adobe flash plugin.

---

### Post by Nima1972 on 2009-05-28
Thanks.  

I used the terminal command. Restarted Firefox.  It seemed like it went OK.  However in the Add-ons/plug-ins window Shockwave flash is listed with an option to disable.

Also, it's a bit choppy.  What can I do?

Again, thanks.  This is well appreciated.

---

### Post by lovinglinux on 2009-05-28
> **Nima1972 said:**
> I used the terminal command. Restarted Firefox.  It seemed like it went OK.  However in the Add-ons/plug-ins window Shockwave flash is listed with an option to disable.

That's normal. You can disable Firefox plugins any time you want.

> **Nima1972 said:**
> Also, it's a bit choppy.  What can I do?

Welcome to the "International Ubuntu Choppy Flash Club". Now that you have installed flash, you will receive a lifetime certificate of our club. :)

Seriously, I haven't found a solution yet. There are several threads about this:

[http://ubuntuforums.org/showthread.php?t=1146943](http://ubuntuforums.org/showthread.php?t=1146943)

**Quick links to similar threads:** [Google Site Search](http://www.google.com/search?q=flash+jaunty+site:ubuntuforums.org&hl=en&sourceid=mozilla-search&num=20&start=0&start=0) | [Forum Search](http://ubuntuforums.org/search.php?do=process&query=flash+jaunty)

Do you have a restricted driver for you graphics card installed?

---

### Post by Nima1972 on 2009-05-28
Didn't we just get rid of Shockwave (swf)?

---

### Post by lovinglinux on 2009-05-28
> **Nima1972 said:**
> Didn't we just get rid of Shockwave (swf)?

If you want to get rid of adobe plugin, then you have two options:

```

sudo apt-get remove flashplugin-nonfree mozilla-plugin-gnash && sudo apt-get install swfdec-mozilla 
```

to install the swfdec plugin

or

```

sudo apt-get remove flashplugin-nonfree swfdec-mozilla && sudo apt-get install mozilla-plugin-gnash
```

to install gnash plugin

or

```
sudo apt-get remove flashplugin-nonfree swfdec-mozilla mozilla-plugin-gnash
```

If you don't want any flash plugin. But I don't think you want that, do you?

---

### Post by Nima1972 on 2009-05-28
BTW, with the flash video, maybe if we download it and play it won't be so choppy, though I'm having a bit of trouble figuring out flashgot.

---

### Post by Nima1972 on 2009-05-28
No, no, I was just confused as to why it has an option to remove Shockwave Flash player when we just removed the swf plug-in.

---

### Post by lovinglinux on 2009-05-29
> **Nima1972 said:**
> No, no, I was just confused as to why it has an option to remove Shockwave Flash player when we just removed the swf plug-in.

There are three different versions flash plugins: swfdec, gnash and the one from adobe. If you have more than one installed you will usually get conflicts between them. So we removed two and installed just the one from adobe. That's why you still have it in the plugin list. If you disable it, then you won't be able to see any flash web content.

---

### Post by utnubuuser on 2009-05-29
I don't suppose "swapiness" cures the choppyness?  What about a different cache size for FF?

---

### Post by Nima1972 on 2009-05-29
I appreciate your help :)

That's not what I'm asking.

Why does it list shockwave under plug-ins instead of what we installed?  We removed shockwave so it shouldn't list it there.  It should list the new flash player.

---

### Post by gandaran on 2009-05-29
> **Nima1972 said:**
> I appreciate your help :)

That's not what I'm asking.

Why does it list shockwave under plug-ins instead of what we installed?  We removed shockwave so it shouldn't list it there.  It should list the new flash player.
adobe flash is listed as shockwave flash under plugins, adobe flash plays both shockwave flash (.swf files) and flash videos (.flv files)

---

### Post by Nima1972 on 2009-05-29
Thanks gandaran.

---

### Post by Nima1972 on 2009-05-29
> **utnubuuser said:**
> I don't suppose "swapiness" cures the choppyness?  What about a different cache size for FF?

Could be.  I reinstalled Ubuntu Jaunty and I'm not sure it's using the designated swap partitioned area.  I think it's using the Ubuntu partition.  I have no idea how to check though.

---

### Post by lovinglinux on 2009-05-29
> **Nima1972 said:**
> Could be.  I reinstalled Ubuntu Jaunty and I'm not sure it's using the designated swap partitioned area.  I think it's using the Ubuntu partition.  I have no idea how to check though.

This has nothing to do with swap or Firefox cache and both has nothing to do with each other. Swap is used when you haven't enough RAM. If you have a swap partition, then Ubuntu will use it. It won't use the Ubuntu partition to store swap data. Nevertheless, swap is slower, so if you haven't enough ram your system will eventually run slower when it needs to read/write the data from/to the swap partition, but this would affect all programs, no only Firefox or flash behavior.

I have 2 Gb of RAM and my system rarely use the swap, but flash still sucks even with more than half of the ram available and swap not being used.

I also don't think Firefox cache is the culprit, because I have enough of it and flash still sucks. Flash videos are choppy in my machine, even when the entire video is cached. Is not Firefox, because flash sucks with Opera, Epiphany and other browsers. The only situation when flash videos are not choppy is when I download the video and play it with gnome-mplayer or VLC. Additionally, if I replace the flash player from YouTube with gecko-mediaplayer using a greasemonkey script, then it plays perfectly. So the problem is the flash plugin, which makes the browser use much more CPU then it should.

Unfortunately, I don't have a solution for you. I'm still trying to find one for myself. I have tried lots of tweaks, but the result is always the same. Nevertheless, you should check if you have the newest drivers for you graphics card installed and if your graphics card is not one of the problematics (Intel for example).

---

### Post by Nima1972 on 2009-05-30
So gecko-mediaplayer solved the choppiness problem?  If so, what's the best way to install it?

---

### Post by Nima1972 on 2009-05-30
BTW, is there a way of increasing the buffer in flash?  Maybe have it finish downloading completely before it starts playing?  Would that effect the choppiness?

---

### Post by lovinglinux on 2009-05-30
> **Nima1972 said:**
> So gecko-mediaplayer solved the choppiness problem?  If so, what's the best way to install it?

Follow this tutorial: [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Keep in mind that gecko-mediaplayer cannot replace flash player by itself. You need to use [Greasemonkey](https://addons.mozilla.org/en-US/firefox/addon/748) with [this script](http://userscripts.org/scripts/show/41722), but this doesn't work on all web sites, just a few, like YouTube.

> **Nima1972 said:**
> BTW, is there a way of increasing the buffer in flash?  Maybe have it finish downloading completely before it starts playing?  Would that effect the choppiness?

I don't think it would make it any better. As I said, I still have the same issues even when the entire video is already buffered. I guess you can hit the pause button and wait for the video to download before playing it.

---

### Post by Greedo on 2009-05-30
I've had this problem with the flash nonfree alternative for the past few years and was wondering if anyone is having this same issue or has a suggestion (I can't remember if gnash had this issue but I remember that gnash didn't seem to play movies right at all) 

if I've played a sound in movieplayer / totem or vlc then any flash movie will have no sound, or if have all of those things closed and play a flash movie which has sound (or some stupid ad comes up on a page that I'm viewing) then before I can get sound on totem then I have to totally shut down my firefox process so that the sound driver will be released. 

This is one thing that never happened when I used windows, is that you could have multiple applications using multiple ways of accessing the sound card without conflicts. (not that I'm going back, but it is annoying sometimes)

---

### Post by gandaran on 2009-05-31
> **Greedo said:**
> I've had this problem with the flash nonfree alternative for the past few years and was wondering if anyone is having this same issue or has a suggestion (I can't remember if gnash had this issue but I remember that gnash didn't seem to play movies right at all) 

if I've played a sound in movieplayer / totem or vlc then any flash movie will have no sound, or if have all of those things closed and play a flash movie which has sound (or some stupid ad comes up on a page that I'm viewing) then before I can get sound on totem then I have to totally shut down my firefox process so that the sound driver will be released. 

This is one thing that never happened when I used windows, is that you could have multiple applications using multiple ways of accessing the sound card without conflicts. (not that I'm going back, but it is annoying sometimes)
fix [pulseaudio]("http://ubuntuforums.org/showthread.php?t=789578&highlight=pulseaudio+fixes") and you wont have this problem

---

### Post by Nima1972 on 2009-07-23
Thanks lovinglinux.

BTW, I'm having a small problem if anyone has any idea:  Once in a while, after a flash video has already come up the flash screen will blank out meaning it'll turn completely white with no access to controls.  

Thanks.

---

