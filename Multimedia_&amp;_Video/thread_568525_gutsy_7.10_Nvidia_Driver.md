---
title: "gutsy 7.10 Nvidia Driver"
date: 2007-10-05
forum: Multimedia &amp; Video
---

### Post by sanddgroper on 2007-10-05
I have been trying to install the Nvidia glx  driver from the synaptic package manager but
without any luck.I can get the Nvidia glx new driver to work but a check of glxgears indicates
that it only runs at about 750fps were as the Nvidia glx driver on fiesty 7.04 runs at around
1150fps.As my graphics card is a fx5200 I think I need the older driver.
I have tried removing all the restricted drivers and then loading the Nvdia glx driver from synaptic and running sudo nvidia-glx-config enable but without success.My last resort which
I have not tried yet is to get the xorg.conf file from fiesty 7.04 and see if it works.
Is anyone else seeing this problem with gutsy 7.10.

Cheers
Sandy

---

### Post by isacvale on 2007-10-06
I've been having the same problem for like the last ten hours or so (trying and trying and trying...) and haven't figured out the answer yet.
I'm sorry this post is not helpful (at all), but I just got to say I have the same problem, with exactly the same video card.
I'm calling it a night and hoping someone will find the answer.

---

### Post by sanddgroper on 2007-10-08
Ok after playing around with this for a few hours I have reached
the limits of my abilities.
I tried using the xorg.conf file that worked for nvidia-glx in 7.04 but each
time I tried to use it the system would default to the xorg.conf.failsafe file.
The funny thing is that if I used the nvidia-glx-new package and the xorg.conf
file from the 7.04 version it worked perfectly.
I will leave it now to someone more qualified than me to determine why the
nvidia-glx package no longer seems to work with 7.10.

Cheers
Sandy

---

### Post by charlieg on 2007-10-08
Try installing the nvidia-glx-new package then restarting.  That worked for me.

---

### Post by dawynn on 2007-10-23
Experiencing similar problems here.  I have an Athlon Classic 1.2 Ghz machine running Gutsy.  I was able to get the Edgy and Feisty nvidia-glx packages working fine.  But Gutsy's packages seem to be borken.

nvidia-glx-new:
I tried to install this.  At first, Xorg recognizes everything just fine, but then later seems to panic and no longer recognizes my card.  I've included my Xorg.0.log file for anyone who wants to see.  I, of course, get stranded at the command prompt when I have this installed.

nvidia-glx:
I can at least do most activities with this package installed.  But anything that requires glx?  Forget it. If I try to run glxgears, I get the following message:

dawynn@66-188-184-101:~$ glxgears
9 frames in 8.8 seconds =  1.022 FPS
Aborted (core dumped)

(Note: the extra window popped up that *should* have shown the moving gears.  But there was no picture.  Just a black window.  Similar reactions with zsnes, pSX, and Neverwinter Nights)

I'm seriously considering envy at this point.  But, why do I *need* to jump over to envy?  These two packages need to be fixed instead.

Cheers!

---

### Post by handy on 2007-10-24
I have an xfx geforce 7950 gt /512mb, that I believe should run the *new* binary drivers from nvidia, they won't work, I tried the next ones down, which won't work either, I then removed the driver & tried envy, which failed to compile the *new* nvidia driver.  So I removed envy which crashed adept manager on its way out & I am thinking seriously of going back to sabayon where this card worked like a dream.

It's always tough at the beginning of a new release...

---

### Post by mhenry676 on 2007-10-24
I hear ya handy. I was once Gentoo or bust! Never tried Sabayon, but it is based off Gentoo. Tried a few distros since, opensuse is my second favorite. Kubuntu is my top choice now, but still new to it & debian.

Long story short, my XFX 7950gt 512 PCI-E is working fine. 1440x900, 3D and all. Using the nvidia-glx-new driver. Try the restricted driver manager. Works fine for me. I can't seem to find the manual method but don't use the one in the driver description (it's pre 7.04/7.10)

:guitar:

---

### Post by kris kincaid on 2007-10-24
I got fed up with it to and wound up using Envy : [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) . I even paypal-ed him $30 because it worked so well and I was so happy.

---

### Post by handy on 2007-10-24
> **kris kincaid said:**
> I got fed up with it to and wound up using Envy : [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) . I even paypal-ed him $30 because it worked so well and I was so happy.

Yep, my time is worth more than $30- a day too, unfortunately as stated, envy won't work for me either.  I removed & reinstalled it, tried the auto install twice & the manual once. :lolflag:

---

### Post by handy on 2007-10-24
> **mhenry676 said:**
> I hear ya handy. I was once Gentoo or bust! Never tried Sabayon, but it is based off Gentoo. Tried a few distros since, opensuse is my second favorite. Kubuntu is my top choice now, but still new to it & debian.

Long story short, my XFX 7950gt 512 PCI-E is working fine. 1440x900, 3D and all. Using the nvidia-glx-new driver. Try the restricted driver manager. Works fine for me. I can't seem to find the manual method but don't use the one in the driver description (it's pre 7.04/7.10)

:guitar:

Thanks for the feedback on the xfx, mine is an AGP job.  I can't know why it is disliked by the driver?  Too many variables for my tiny brain...

---

### Post by handy on 2007-10-24
I've just installed Sabayon, the LiveCD saw my graphics card & installed the latest binary nVidia drivers. It installed in 20 minutes max' & set my card & monitor up correctly.

I was here a week or so ago, when I started chasing alternatives to Sabayon (perhaps only for the time being) because beagled.helper was eating a lot of cpu cycles, & I don't even use it!

I could do everything satisfactorily on Sabayon even with cpu cycles being wasted, so it must of been the environmentalist in me that has had me wasting all this energy for the last week or so!

Anyway, as it was, again it shall be! :-D  No, I should say IS.

---

### Post by dawynn on 2007-10-24
Can we stop already with the "solutions" that are suggesting that the way to "fix" ubuntu is to jump ship and go to a completely different distribution?  This is entirely unhelpful.  Last I checked, this is a Ubuntu forum, not a general Linux forum.  You've made your case, things have worked better in other distros.  Frankly, things were working beautifully for me in Feisty, which is at least still a Ubuntu release.  But that doesn't help us fix Gutsy.

Thanks!

---

### Post by sanddgroper on 2007-10-24
Hi Guys
As I said before I have given up and just used the nvidia glx new drivers with
the resulting lower frame rate.
I have not downloaded the final release of Gutsy so would be interested if anybody
else is seeing this with the new release.
I can live quite happily with fiesty but would be nice if the nvidia glx drivers worked
with gutsy.Maybe they do now, as I say, I have not tried the final release version.

Cheers
Sandy

---

### Post by dawynn on 2007-10-24
Nvidia on Feisty works fine for me.  I still have Gutsy installed, but I'm setting grub to make Feisty the default on my machine.  I'll check back in a month or two....

I went ahead and tried envy.  I was able to get it "working" -- as much as nvidia-glx already was.  But since that still meant no glx, it wasn't very helpful.  I have not had luck with either nvidia-glx-legacy or nvidia-glx-new -- but prevented the GUI and gave me the errors you see in the Xorg log I posted earlier.

Cheers!

---

### Post by mhenry676 on 2007-10-24
I agree. Handy, don't jump ship. I considered going back to opensuse cause YAST is very nice, but the number of packages, and the community support keep me here. 

I did consider getting the AGP, but decided to upgrade to 939 from socket a. Also, the drivers for that card specifically, I read, were a pain as they were from XFX not nvidia, and behind in versions of nvidia (but that was 3-4 months ago) 

I do have a suggestion to help. I did this with suse, as I think it does a better job with xorg.config/nvidia and my monitor. For my laptop, suse/fedora also does a better at cpu throttling, where kubuntu, freezes my mouse with the freq. changes (WIP).

Grab a flash drive. Copy your working xorg.conf from Sabayon (or whatever), output of lsmod, and anything else you need. and use that as a basis for help configuring Kubuntu. 

:guitar:

---

### Post by buntunub on 2007-10-24
> **mhenry676 said:**
> I agree. Handy, don't jump ship. I considered going back to opensuse cause YAST is very nice, but the number of packages, and the community support keep me here. 

I did consider getting the AGP, but decided to upgrade to 939 from socket a. Also, the drivers for that card specifically, I read, were a pain as they were from XFX not nvidia, and behind in versions of nvidia (but that was 3-4 months ago) 

I do have a suggestion to help. I did this with suse, as I think it does a better job with xorg.config/nvidia and my monitor. For my laptop, suse/fedora also does a better at cpu throttling, where kubuntu, freezes my mouse with the freq. changes (WIP).

Grab a flash drive. Copy your working xorg.conf from Sabayon (or whatever), output of lsmod, and anything else you need. and use that as a basis for help configuring Kubuntu. 

:guitar:

Although I understand the logic, its basicly just saying that Fabio (the Sabayon Lead Developer) got it all right where the Ubuntu Devs cant. This is absolutely true in this one particular case. Give this suggestion a try as a test, and if the Sabayon configs work, then we have the proof positive. If it is in fact true, then IMO, Canonical should get on the phone with Fabio with a nice sweet offer for a Lead Developer spot in the X server department LOL!

---

### Post by mhenry676 on 2007-10-24
Now that's just mean! :twisted:

---

### Post by handy on 2007-10-24
> **dawynn said:**
> Can we stop already with the "solutions" that are suggesting that the way to "fix" ubuntu is to jump ship and go to a completely different distribution?  This is entirely unhelpful.  Last I checked, this is a Ubuntu forum, not a general Linux forum.  You've made your case, things have worked better in other distros.  Frankly, things were working beautifully for me in Feisty, which is at least still a Ubuntu release.  But that doesn't help us fix Gutsy.

Thanks!

Hey, don't get so head up?  I'm still running 7.10 on my other machine, the one I'm typing this on, ok?  Every new release is bug ridden, that's not a problem, that's just life in software.

Also, there are many regulars on this forum that aren't using Ubuntu, but they have Linux smarts, & Linux smarts jump distro's.

---

### Post by handy on 2007-10-24
> **sanddgroper said:**
> Hi Guys
As I said before I have given up and just used the nvidia glx new drivers with
the resulting lower frame rate.
I have not downloaded the final release of Gutsy so would be interested if anybody
else is seeing this with the new release.
I can live quite happily with fiesty but would be nice if the nvidia glx drivers worked
with gutsy.Maybe they do now, as I say, I have not tried the final release version.

Cheers
Sandy

I think it all comes down to your hardware in the end.  People have had my graphic card work, when nothing I do will make it work for me...  Just how it is, too many variables to be able to pin it down at this point, for me anyway.

---

### Post by handy on 2007-10-24
> **mhenry676 said:**
> I agree. Handy, don't jump ship. I considered going back to opensuse cause YAST is very nice, but the number of packages, and the community support keep me here. 

I did consider getting the AGP, but decided to upgrade to 939 from socket a. Also, the drivers for that card specifically, I read, were a pain as they were from XFX not nvidia, and behind in versions of nvidia (but that was 3-4 months ago) 

I do have a suggestion to help. I did this with suse, as I think it does a better job with xorg.config/nvidia and my monitor. For my laptop, suse/fedora also does a better at cpu throttling, where kubuntu, freezes my mouse with the freq. changes (WIP).

Grab a flash drive. Copy your working xorg.conf from Sabayon (or whatever), output of lsmod, and anything else you need. and use that as a basis for help configuring Kubuntu. 

:guitar:

As I said previously, all my hardware is acknowledged & setup properly when the Sabayon LiveCD boots.  I have installed Sabayon on the most troublesome machine (troublesome with regards to 7.10) that I own, & that is where I was a week ago anyway.  My other machine is stumbling along, it has shown multiple bugs in Kubuntu 7.10, but I think I can live with them.  This machine is mostly used as a web reference & occasionally plays a DVD, so it's life is easy.

As far as jumping ship is concerned, I have been using a variety of distro's, often not a *buntu, over the last year or more.  I still frequent the Ubuntu forums most everyday, because its such a nice community to be a part of. :-)

Also, I think your idea about copying the Sabayon xorg.conf is a good one.  If you want I'll email it to you, including any other files you wish?  I might have to do ***another*** install myself! :lolflag:

---

### Post by handy on 2007-10-24
> **buntunub said:**
> Although I understand the logic, its basicly just saying that Fabio (the Sabayon Lead Developer) got it all right where the Ubuntu Devs cant. This is absolutely true in this one particular case. Give this suggestion a try as a test, and if the Sabayon configs work, then we have the proof positive. If it is in fact true, then IMO, Canonical should get on the phone with Fabio with a nice sweet offer for a Lead Developer spot in the X server department LOL!

Leave  Fabio where he is!  I really like Sabayon. :-)  But I like your logic.

---

### Post by dawynn on 2007-10-24
Eureka!!!  Success!!!

See this post in the Kubuntu forums: [http://kubuntuforums.net/forums/index.php?topic=3087867.0](http://kubuntuforums.net/forums/index.php?topic=3087867.0)

Please understand, this is very much one of those YMMV type of things.  Everyone's settings may need to be a bit different.  Try this command: 'man nvidia-xconfig'.

In my case, I had had problems in previous installations that presented as a freeze up on the sign-in screen.  This was solved in Feisty and earlier installs by adding the line 
[INDENT]Option   "NvAGP"  "0"[/INDENT]
to the "Screen" section of xorg.conf.  So, my nvidia problems were solved in Gutsy by typing "sudo nvidia-xconfig --nvagp=0".  The post above lists solutions that worked for other people.

glxgears, Neverwinter Nights, and pSX now work for me.  Zsnes seems to be another issue altogether.

I may stick with Gutsy after all.  Cheers!

---

### Post by sanddgroper on 2007-10-26
I have found the fix for the problem I was having.It
appears that when you try to install the nvidia glx
driver in place of the nvidia glx new driver a file gets
left behind that causes a mismatch with the nvidia glx driver.
The file nvidia_new_installed in /lib/linux-restricted-modules
needs to be removed.See bug 106217 in launchpad for more
details.
Removing this file fixed the problem of X launching in failsafe
for me.
The reduction in frame rate seems to be because of Compriz.Turning
Compriz off returns my frame rate to normal.
Guess I need a better computer if I want to run all the eye candy::-)

Cheers
Sandy

---

### Post by inversekinetix on 2007-10-26
i just enabled the eye candy and ubuntu told me it needed the restricted drivers, loaded them went to vga mode, one restart later I got all the bells and whistles going at 2800fps!  get a little tearing during rotation but other than that its fine.

---

### Post by ehnar on 2007-10-26
My FX5200 was installed fine from start, but as in Feisty the problem was to get the tv-out funktion to work. Sadly this problem is persistant in gutsy, despite the nice GUI for that. And... the xconfig file also looks different, at least for me as a newbie. Any solutions to fix the tv-out funktion in a easy way?

---

