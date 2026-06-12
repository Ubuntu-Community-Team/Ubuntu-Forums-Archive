---
title: "Flash Problem Jaunty 9.04"
date: 2009-04-28
forum: Multimedia Software
---

### Post by russ5811 on 2009-04-28
I upgraded to 9.04. Flash in only working on some sites. Youtube works fine. Adobe's page that is supposed to play a flash video to tell you what version you're using as a test does not work. My business's website (which uses some flash) does not show up. I have tried uninstalling flash and reinstalling it via synaptic. I downloaded the deb from adobe and installed it that way, then uninstalled and then reinstalled again.  I have tried everything!! What do I do???

---

### Post by psyke83 on 2009-04-29
> **russ5811 said:**
> I upgraded to 9.04. Flash in only working on some sites. Youtube works fine. Adobe's page that is supposed to play a flash video to tell you what version you're using as a test does not work. My business's website (which uses some flash) does not show up. I have tried uninstalling flash and reinstalling it via synaptic. I downloaded the deb from adobe and installed it that way, then uninstalled and then reinstalled again.  I have tried everything!! What do I do???

You probably installed gnash or swfdec, which doesn't have 100% compatibility with Adobe Flash content.

```
$ sudo apt-get remove --purge swfdec-mozilla mozilla-plugin-gnash flashplugin-nonfree adobe-flashplugin
$ sudo apt-get install adobe-flashplugin
```

Note: you'll need to have the Canonical "partner" repository to get access to the adobe-flashplugin package.

---

### Post by Cresho on 2009-04-29
I had the same issues.  what I did was change my hardware drivers from 180 to 173 nvidia drivers.  Now my videos play fine.  It may stutter just a bit at start but when it gets going, its fine.

I did a recheck again, its fine.  when the controls for video manipulation comes up, it slows down, when they hide, its smooth.

Its a driver or flash issue.

---

### Post by Cresho on 2009-04-29
hmm...In you tube with the 173 drivers, i went fullscreen and came back and went fullscreen again to get the video smooth.  It has something to do with the way it captures fullscreen.  Probably sync issue with refresh rate or even pulseaudio but once it gets going, its fine.

---

### Post by psyke83 on 2009-04-29
> **Cresho said:**
> hmm...In you tube with the 173 drivers, i went fullscreen and came back and went fullscreen again to get the video smooth.  It has something to do with the way it captures fullscreen.  Probably sync issue with refresh rate or even pulseaudio but once it gets going, its fine.

The OP probably has a different issue to yours. The open-source Flash implementations work on Youtube, but don't work on many other types of Flash content, such as mentioned by the poster. Having more than one Flash plugin installed tends to cause a conflict (so, installing the Adobe Flash plugin is not enough - you must also uninstall the open-source swfdec or gnash plugins).

---

### Post by Cresho on 2009-04-29
Ya I never installed those plugins you mentioned.  If he has them installed, he should remove them.

Jaunty fixed vsync issues but created new ones such as flash video playback.

In hulu, i need to click on high def and wait till the video is playing and then I click on full screen and once the controls hide, its fine.  There is a problem and patch needed.  I can deal with this like this for now.

---

### Post by iamthemicrowave on 2009-04-29
I am having a flash problem too.  Youtube videos display weird, and flash on many sites causes a crash.  I had no problems until I upgraded to jaunty.  Not sure if it is a flash/firefox/driver issue.

---

### Post by Cresho on 2009-04-29
well, i kept at it and now reverted back to the 180 drivers.  what ever I do, its just plain bad.

---

### Post by mdgo80 on 2009-04-30
> **psyke83 said:**
> You probably installed gnash or swfdec, which doesn't have 100% compatibility with Adobe Flash content.

```
$ sudo apt-get remove --purge swfdec-mozilla mozilla-plugin-gnash flashplugin-nonfree adobe-flashplugin
$ sudo apt-get install adobe-flashplugin
```

Note: you'll need to have the Canonical "partner" repository to get access to the adobe-flashplugin package.

Thanks this actually fixed my problem. I was having troubles with the scroll bar in some flash videos. I strongly recommend this for people who upgraded from Hardy to Jaunty via Updater and start having some issues (pink squares on the video) with Flash.

---

### Post by wisd0m on 2009-05-02
I have a similar issue.

When playing flash video (tested on youtube and hulu), it works ok when embedded but not in fullscreen.

In fullscreen, the video will freeze, shutter and flicker. The audio works ok. I tried letting the video play a little first, no change.

I have tried with visual effect on and off, no change.

This is an annoying little issue.:(

---

### Post by ralphwroberts on 2009-05-02
I'm having the same problems with Flash on 9.04. .... upgraded to the latest version of NVidia, tried all the little tricks in the various threads here, Flash still plays only a few seconds and locks in Firefire ... full screen apps like Hulu won't work.

Does anyone PLEASE have a definite fix?

---

### Post by coblenis on 2009-05-03
I have the same problem too.  Flash will work on a few sites for the first session that I run firefox, but it seems like either an extended session of a firefox restart sets off the program.  Youtube's about the only site that consistently works.  I have tried all the advice in here, including switching my nvidia drivers from 180 to 173, but no luck.

---

### Post by oregonbob on 2009-05-03
I have the partner repository enabled, but it says adobe-flashplugin not found?

---

### Post by dddw on 2009-05-04
> **ralphwroberts said:**
> 
Does anyone PLEASE have a definite fix?

I have the same issue, but with my intel-videocard

I followed [this]("http://ubuntuforums.org/showthread.php?t=1130582"), and it works for me :KS

---

### Post by mtm_king on 2009-05-13
> **psyke83 said:**
> You probably installed gnash or swfdec, which doesn't have 100% compatibility with Adobe Flash content.

```
$ sudo apt-get remove --purge swfdec-mozilla mozilla-plugin-gnash flashplugin-nonfree adobe-flashplugin
$ sudo apt-get install adobe-flashplugin
```

Note: you'll need to have the Canonical "partner" repository to get access to the adobe-flashplugin package.

Dude - You solved a problem that I must have 30 hours of work on. What can I say but - Thank you.

Good Karma to you, mtm

---

### Post by Regele IONESCU on 2009-05-13
[COLOR="Red"]> **psyke83 said:**
> You probably installed gnash or swfdec, which doesn't have 100% compatibility with Adobe Flash content.

```
$ sudo apt-get remove --purge swfdec-mozilla mozilla-plugin-gnash flashplugin-nonfree adobe-flashplugin
$ sudo apt-get install adobe-flashplugin
```

Note: you'll need to have the Canonical "partner" repository to get access to the adobe-flashplugin package.[/COLOR]

I had problems with flash and firefox ever since I installed Ubuntu for the first time. I had no idea at all that swdec could conflict with the rest.

Now it works fine, I just checked all the sites that have not been working but head-aching me. **Thank you very much!**

God help us all!
Honestly,
Christian I. Ionescu

---

### Post by ddalley on 2009-05-13
OK, so why, after I installed the Adobe Flash plugin *directly through the Adobe site*, YouTube videos didn't work, but when I installed (presumably) the same plugin through the Synaptic repository, it worked?

At least I can **see** the video now, but now I have to figure out why there is no audio. So what else is new...

---

### Post by raydar on 2009-05-13
Thank you, psyke83!

Hulu wouldn't even load the embedded player for me, in Ubuntu Studio 9.04.

After I followed your advice, it's back to working just fine like it did before I installed 9.04.

---

### Post by williamson389 on 2009-05-14
I have the same problem as oregonbob.  after runing sudo apt-get install adobe flaash plugin, it "Couldnt Find package adobe flash plugin"  i have medibuntu and the partner repositores enabbled so im not sure what is stopping the installation.
thanks

---

### Post by psyke83 on 2009-05-14
> **ddalley said:**
> OK, so why, after I installed the Adobe Flash plugin *directly through the Adobe site*, YouTube videos didn't work, but when I installed (presumably) the same plugin through the Synaptic repository, it worked?

At least I can **see** the video now, but now I have to figure out why there is no audio. So what else is new...

Always use the Ubuntu Flash packages when possible. The advantages are better integration with the system (such as nspluginwrapper hooks for 64-bit users) and the capability for the plugin to update itself (as it's part of the official repository).

Using the Adobe .deb is alright, but you'll have to remember to update it manually. Installing from the tar.gz is plain evil - you can possibly end up with multiple versions of the plugin loaded into Firefox, causing conflicts.

---

### Post by ralphwroberts on 2009-05-16
nothing above or anywhere else in these forums help -- Flash appears to be seriously broken in Ubuntu 9.04. A very annoying problem ... I've even installed the new kernel from jaunty-proposed ... nothing works.

can anyone tell us what's going on? When will Flash be fixed for 9.04??????

thanks.

---

### Post by Poalman on 2009-05-18
I had playback problems when flash was fullscreen since upgrading, found a solution here (solution 3 fixed it for me);

[http://www.ubuntugeek.com/fix-for-flash-not-working-after-jaunty-upgrade-64bit.html](http://www.ubuntugeek.com/fix-for-flash-not-working-after-jaunty-upgrade-64bit.html)

I don't run the 64bit version either but it worked :)

---

### Post by ralphwroberts on 2009-05-18
> **Poalman said:**
> I had playback problems when flash was fullscreen since upgrading, found a solution here (solution 3 fixed it for me);

[http://www.ubuntugeek.com/fix-for-flash-not-working-after-jaunty-upgrade-64bit.html](http://www.ubuntugeek.com/fix-for-flash-not-working-after-jaunty-upgrade-64bit.html)

I don't run the 64bit version either but it worked :)

thanks but, yep, tried that one also and did not work.

9.04 just does not like Flash.

---

### Post by iamthemicrowave on 2009-05-19
The fixes posted have not worked for me.  I still get pink squares and stuff on youtube vids.  HQ vids do not work for me.  Also, the volume control on youtube does nothing.  Stays at 100% no matter what.

---

### Post by TheAmishSlayer on 2009-06-01
I too had been struggling with the Flash problem for a while now. Did a fresh install of Jaunty, installed the Flash plugin from th Adobe.com site, and still I would get nothing but the javascript disabled / or upgrade to Flash Player 10 message. I installed the NoScript addon for Firefox like I always do, and suddenly all Flash started working. Go figure? No clue why.

---

### Post by mindbucket on 2009-06-02
Poalman  Thank you...! I have been trying to fix this problem for weeks.
Solution 3 worked for me as well.

---

### Post by Goddard on 2009-06-02
Thanks..this help ...Flash runs great now...although my video card doesn't run as good as it does on windows.

---

### Post by Zach-Warlock on 2009-06-03
I am having problems playing videos on youtube but reading this forum has made me realize that I have gnash installed.
 
Thakns for the posts, as soon as I get home I will uninstall gnash and let you all know if it worked for me.

---

### Post by Zach-Warlock on 2009-06-04
sorry I took so long with the post.
 
uninstalling the gnash worked for me and now I am able to watch all my fave video web pages. I guess flash player cant play well with others.;)
 
thanks for the help:p

---

### Post by HobbitTR on 2009-08-01
> **psyke83 said:**
> You probably installed gnash or swfdec, which doesn't have 100% compatibility with Adobe Flash content.

```
$ sudo apt-get remove --purge swfdec-mozilla mozilla-plugin-gnash flashplugin-nonfree adobe-flashplugin
$ sudo apt-get install adobe-flashplugin
```

Note: you'll need to have the Canonical "partner" repository to get access to the adobe-flashplugin package.
psyke83 Thank you, this worked just fine for me. I did my system updates from 2.6.28-14 to 2.6.28-15 and after restart I saw that gtk-gnash was consuming almost 100% of CPU. I killed gtk-gnash and started to see what was the problem. After several forum chases, I found this one and noticed that I had both Gnash and Adobe Flash plugins installed. I used solution #2 [http://ubuntuforums.org/showpost.php?p=7173670&postcount=2](http://ubuntuforums.org/showpost.php?p=7173670&postcount=2) , closed Firefox, restarted FF and all works GREAT! Thank you.

---

### Post by BlocknBleed on 2009-08-03
Seem to have got mine working again for now. 

In Firefox go Tools>Add-ons>Plugins

I had 2 versions of Shockwave Flash installed so I just disabled v9.0 and kept v10.0.

A simple solution but I tried many of the others with no success. Hopefully this will keep working for me.


Okaaaaayy.  That worked for a day then quit on me.
Next suggestion?

---

### Post by BlocknBleed on 2009-08-04
> **TheAmishSlayer said:**
> I too had been struggling with the Flash problem for a while now. Did a fresh install of Jaunty, installed the Flash plugin from th Adobe.com site, and still I would get nothing but the javascript disabled / or upgrade to Flash Player 10 message. I installed the NoScript addon for Firefox like I always do, and suddenly all Flash started working. Go figure? No clue why.

Worked for me too. We'll see how long this lasts.

---

### Post by petenz on 2009-08-07
> **psyke83 said:**
> You probably installed gnash or swfdec, which doesn't have 100% compatibility with Adobe Flash content.

```
$ sudo apt-get remove --purge swfdec-mozilla mozilla-plugin-gnash flashplugin-nonfree adobe-flashplugin
$ sudo apt-get install adobe-flashplugin
```

Note: you'll need to have the Canonical "partner" repository to get access to the adobe-flashplugin package.

This solved my problems with Flash. Thank you very much.

---

### Post by minimustangs on 2009-08-08
I have also had the flash issue - some flash doesn't play. Tried eveything in this thread to no avail until this:
[http://www.ubuntugeek.com/fix-for-flash-not-working-after-jaunty-upgrade-64bit.html](http://www.ubuntugeek.com/fix-for-flash-not-working-after-jaunty-upgrade-64bit.html)
Flash currently working ( my "test" site: ctv.ca, any episode....)

Thanks!
S~

---

### Post by Janzuka on 2009-08-08
This seems to be a common problem, luckily there are people who have found the answers :)

---

### Post by axel1973 on 2009-08-22
if i try this remove line mentioned, ill get an error like this

```
root@freiburg2:~# sudo apt-get remove --purge swfdec-mozilla mozilla-plugin-gnash flashplugin-nonfree adobe-flashplugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package mozilla-plugin-gnash is not installed, so not removed
Package flashplugin-nonfree is not installed, so not removed
E: Couldn't find package adobe-flashplugin
root@freiburg2:~# 
```

if i remove the last package name it seems to go further, but wants to remove GNOME and so pretty much ANYTHING that depends on gnome. 

```
root@freiburg2:~# sudo apt-get remove --purge swfdec-mozilla mozilla-plugin-gnash flashplugin-nonfree 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package mozilla-plugin-gnash is not installed, so not removed
Package flashplugin-nonfree is not installed, so not removed
The following packages were automatically installed and are no longer required:
  menu-xdg gnome-network-admin planner gthumb gnome-accessibility gnome-backgrounds libaiksaurus-1.2-data abiword-help python-numpy
  python-4suite-xml nspluginwrapper latex-xft-fonts libswfdec-0.8-0 link-grammar-dictionaries-en cheese libots0 hardinfo
  python-reportlab gthumb-data gnome-desktop-environment abiword gnome-themes-extras abiword-common python-uniconvertor python-lxml
  liblapack3gf python-renderpm dasher gnome-games-extra-data p7zip abiword-plugin-grammar liblink-grammar4 gdm-themes libwv-1.2-3
  gnome-vfs-obexftp dasher-data gok libgdome2-0 libaiksaurusgtk-1.2-0c2a libwmf-bin libgtkmathview0c2a desktop-base
  abiword-plugin-mathview libblas3gf gnumeric-common liferea gnome-core gnumeric libgfortran3 libaiksaurus-1.2-0c2a gnome-office
  python-4suite-doc inkscape swfdec-gnome libsoup2.2-8 gnumeric-doc serpentine python-reportlab-accel libgdome2-cpp-smart0c2a
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  gnome* swfdec-mozilla*
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 360kB disk space will be freed.
Do you want to continue [Y/n]? 

```

WTF ?!?
how did this worked for all you guys without removing other packages ??!

---

### Post by aggen on 2009-08-23
I had the same problem as the one with the original post, but now Flash in Firefox is running like it should, thanks to psyke83. I'm also playing around with Chromium, and Flash still won't work there. Does anyone know how I can fix that problem?

---

### Post by ciamele on 2009-08-23
I was experiencing Flash problems too (couldn't see any flash), but I'm using 8.10. I discovered it was my FoxyTunes add-on in Firefox. After disabling it, I'm able to see flash again.

---

### Post by dip huda on 2009-09-15
> **psyke83 said:**
> You probably installed gnash or swfdec, which doesn't have 100% compatibility with Adobe Flash content.

```
$ sudo apt-get remove --purge swfdec-mozilla mozilla-plugin-gnash flashplugin-nonfree adobe-flashplugin
$ sudo apt-get install adobe-flashplugin
```

Note: you'll need to have the Canonical "partner" repository to get access to the adobe-flashplugin package.




I did this. but i still have the problem for some sites such as [http://www.doridro.com]("http://www.doridro.com"). 

help me plz.

thanks

---

### Post by abhi.datt on 2009-10-10
Thanks a lot, can vouch that it worked for my Dell latitude e6400, nvidia quadro nvs 160m. Any one with same card should also use the solution 3, should work

---

### Post by marcelo_gomes on 2009-11-16
> **psyke83 said:**
> You probably installed gnash or swfdec, which doesn't have 100% compatibility with Adobe Flash content.

```
$ sudo apt-get remove --purge swfdec-mozilla mozilla-plugin-gnash flashplugin-nonfree adobe-flashplugin
$ sudo apt-get install adobe-flashplugin
```

Note: you'll need to have the Canonical "partner" repository to get access to the adobe-flashplugin package.

I had the same problem: all worked well in 8.10 but when I upgraded to 9.04 youtube stopped working. This solution proposed by psyke83 worked like a charm, thanks!

---

### Post by marcelo_gomes on 2009-11-16
> **axel1973 said:**
> if i try this remove line mentioned, ill get an error like this

```
root@freiburg2:~# sudo apt-get remove --purge swfdec-mozilla mozilla-plugin-gnash flashplugin-nonfree adobe-flashplugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package mozilla-plugin-gnash is not installed, so not removed
Package flashplugin-nonfree is not installed, so not removed
E: Couldn't find package adobe-flashplugin
root@freiburg2:~# 
```

if i remove the last package name it seems to go further, but wants to remove GNOME and so pretty much ANYTHING that depends on gnome. 

```
root@freiburg2:~# sudo apt-get remove --purge swfdec-mozilla mozilla-plugin-gnash flashplugin-nonfree 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package mozilla-plugin-gnash is not installed, so not removed
Package flashplugin-nonfree is not installed, so not removed
The following packages were automatically installed and are no longer required:
  menu-xdg gnome-network-admin planner gthumb gnome-accessibility gnome-backgrounds libaiksaurus-1.2-data abiword-help python-numpy
  python-4suite-xml nspluginwrapper latex-xft-fonts libswfdec-0.8-0 link-grammar-dictionaries-en cheese libots0 hardinfo
  python-reportlab gthumb-data gnome-desktop-environment abiword gnome-themes-extras abiword-common python-uniconvertor python-lxml
  liblapack3gf python-renderpm dasher gnome-games-extra-data p7zip abiword-plugin-grammar liblink-grammar4 gdm-themes libwv-1.2-3
  gnome-vfs-obexftp dasher-data gok libgdome2-0 libaiksaurusgtk-1.2-0c2a libwmf-bin libgtkmathview0c2a desktop-base
  abiword-plugin-mathview libblas3gf gnumeric-common liferea gnome-core gnumeric libgfortran3 libaiksaurus-1.2-0c2a gnome-office
  python-4suite-doc inkscape swfdec-gnome libsoup2.2-8 gnumeric-doc serpentine python-reportlab-accel libgdome2-cpp-smart0c2a
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  gnome* swfdec-mozilla*
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 360kB disk space will be freed.
Do you want to continue [Y/n]? 

```

WTF ?!?
how did this worked for all you guys without removing other packages ??!
axel1973:
I received the same warning but said yes anyway, it worked and didn't messed up my gnome environment. "gnome-core" package is what you really should be scared if anything tries to remove, I think (altough not sure, can anyone clear this out for us?).
I've checked the 'gnome' package discription in synaptic, along with several other entries which had gnome on their names or descriptions and tought it wouldn't hurt to remove this one, despite the suggestive name....

---

### Post by acho on 2009-11-25
Flash player is working as well for me....i'm using Jaunty with flashplayer 10...

I had problem with action script when i playing flash game...pop up screen with error message like this:

> An ActionScript error has occurred:
Error #2044: Unhandled StatusEvent:. level=error, code=

What should i do???any idea....thx

---

### Post by Denton Larson on 2009-11-27
Your message worked for me too! THANK YOU! Denton Larson


> **psyke83 said:**
> You probably installed gnash or swfdec, which doesn't have 100% compatibility with Adobe Flash content.

```
$ sudo apt-get remove --purge swfdec-mozilla mozilla-plugin-gnash flashplugin-nonfree adobe-flashplugin
$ sudo apt-get install adobe-flashplugin
```

Note: you'll need to have the Canonical "partner" repository to get access to the adobe-flashplugin package.

---

