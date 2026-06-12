---
title: "flash player + nspluginwrapper (64bit): all problems"
date: 2010-06-11
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by yelo3 on 2010-06-11
Now that adobe officially closed the 64bit linux version of flash player 10.1 (but a future release is expected [*]), we can only use (in the mean time) the 32 bit version through nspluginwrapper.

This topic is intended to collect all issues caused by this software, so we can help each other to report and fix bugs!

**NOTE: this thread is _ONLY_ to discuss about how to _improve nspluginwrapper_ (and not to complain about things).**


[*] [http://forums.adobe.com/community/labs/flashplayer10_64bit](http://forums.adobe.com/community/labs/flashplayer10_64bit)

---

### Post by yelo3 on 2010-06-11
I'll start!
youtube fullscreen does not work: only the first video frame is shown, but the audio goes on
launchpad bug: [https://bugs.launchpad.net/bugs/592715](https://bugs.launchpad.net/bugs/592715)

---

### Post by Slug71 on 2010-06-11
What the hell did they do that for? I freakin hate nspluginwrapper.
The 64bit version worked well.

---

### Post by Slug71 on 2010-06-11
Update: Your thread makes it seem like the project is dead. Only 10.1 is.
They still plan an official 64 bit release with a later version. 
Hopefully 10.2.

---

### Post by yelo3 on 2010-06-11
Thanks for the tip, I'll add it in the description

---

### Post by taavikko on 2010-06-11
> **Slug71 said:**
> Update: Your thread makes it seem like the project is dead. Only 10.1 is.
They still plan an official 64 bit release with a later version. 
Hopefully 10.2.

Browsing through adobes website and cannot find such an statement.
Link please.

---

### Post by Gavin77 on 2010-06-11
> **taavikko said:**
> Browsing through adobes website and cannot find such an statement.
Link please.

[http://forums.adobe.com/community/labs/flashplayer10_64bit](http://forums.adobe.com/community/labs/flashplayer10_64bit)

Click on show details.

---

### Post by taavikko on 2010-06-11
> **Gavin77 said:**
> [http://forums.adobe.com/community/labs/flashplayer10_64bit](http://forums.adobe.com/community/labs/flashplayer10_64bit)

Click on show details.

That doesn't state anything else that 10.1 x86_64 version is "dead"
Nothing about 10.2/11/100

---

### Post by yelo3 on 2010-06-11
I hope this won't turn in a completely off topic discussion...

---

### Post by xebian on 2010-06-11
So what is the alternative to 64-bit flash?  I hope Google comes to the rescue.

---

### Post by Merk42 on 2010-06-11
> **xebian said:**
> So what is the alternative to 64-bit flash?
32bit flash using nspluginwrapper

---

### Post by SevenMachines on 2010-06-11
how is 32 bit/nspluginwrapper these days? i'm just trying it out again after using the 64 bit plugin and it seems stabler than i remember. are there any major outstanding problems that need work?

---

### Post by LiquidMeson on 2010-06-11
> **xebian said:**
> So what is the alternative to 64-bit flash?  I hope Google comes to the rescue.

No install, no frustration, high quality, fast loading webm

crosses fingers and prays for better javascript / webgl games

Note: I see flash as an optional (removable) layer on top of open technologies that makes it incredibly simple to add content.

---

### Post by Merk42 on 2010-06-11
> **LiquidMeson said:**
> No install, no frustration, high quality, fast loading webm

Really? Webm can run those flash games and flash websites??

---

### Post by cariboo on 2010-06-11
If we are using the 64-bit version now, why do we have to stop using it if it is no longer available. :) I've archived a couple of copies of the tgz file for when I need it.

---

### Post by xebian on 2010-06-11
> **Merk42 said:**
> 32bit flash using nspluginwrapper

We are talking 'about Maverick' 64-bit.

---

### Post by taavikko on 2010-06-11
> **xebian said:**
> We are talking 'about Maverick' 64-bit.

Yes we are. The only alternative is to use 32bit flash with nspluginwrapper or the previous beta 10.42*
Latter fixes the CVE but is/has been almost unusable on x86_64

---

### Post by yelo3 on 2010-06-11
So today I installed nspluginwrapper and I'm currently testing it in some sites, with the aim of finding bugs and opening tasks in launchpad.
Can you help me?

---

### Post by SevenMachines on 2010-06-11
> **yelo3 said:**
> So today I installed nspluginwrapper and I'm currently testing it in some sites, with the aim of finding bugs and opening tasks in launchpad.
Can you help me?
i'll certainly be trying to do that, it would be nice to have an open web standard though, this current flash mess being a prime example. ah well, c'est la vie

[EDIT] i belive sorting these nspluginwrapper problems is the point of this thread

---

### Post by Slug71 on 2010-06-11
> **taavikko said:**
> That doesn't state anything else that 10.1 x86_64 version is "dead"
Nothing about 10.2/11/100

[http://labs.adobe.com/technologies/flashplayer10/64bit.html](http://labs.adobe.com/technologies/flashplayer10/64bit.html)

I just said hopefully it will be ready 10.2. Its not related to anything.

---

### Post by yelo3 on 2010-06-11
> **SevenMachines said:**
> 
[EDIT] i belive sorting these nspluginwrapper problems is the point of this thread

That's what I'm trying to do!

---

### Post by SevenMachines on 2010-06-11
> **yelo3 said:**
> That's what I'm trying to do!
i know! me too! depending on the amount of time the world cup allows me of course :)

---

### Post by yelo3 on 2010-06-11
youtube controls sometimes don't work:

[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/410407](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/410407)

* WORKAROUND IN THE BUG DESCRIPTION *

---

### Post by krazyd on 2010-06-12
[http://lightspark.sourceforge.net/](http://lightspark.sourceforge.net/)

Needs work, but holds promise..

---

### Post by ranch hand on 2010-06-12
> **krazyd said:**
> [http://lightspark.sourceforge.net/](http://lightspark.sourceforge.net/)

Needs work, but holds promise..
This is currently just 32bit isn't it?  Or do I need to learn to read?

Could be both.

---

### Post by Linuxforall on 2010-06-12
I was quite afraid of using nsplugin with x32 flash but the latest one works out quite well. My previous experience in Intrepid and x32 flash was quite bad so when alpha x64 flash came out, I used that solely till the current security issue made me reconsider. Full screen works well, flash works fine on Opera and FF as well as Chrome.

---

### Post by Linuxforall on 2010-06-12
> **ranch hand said:**
> This is currently just 32bit isn't it?  Or do I need to learn to read?

Could be both.

The ppa has it for both x64 and x32.

---

### Post by ranch hand on 2010-06-12
> **Linuxforall said:**
> The ppa has it for both x64 and x32.
Ah, so it is both.  Man, I really must be getting senile.

Thanks, I think I may slap that bugger on one of my 10.04 installs.

---

### Post by Linuxforall on 2010-06-12
> **ranch hand said:**
> Ah, so it is both.  Man, I really must be getting senile.

Thanks, I think I may slap that bugger on one of my 10.04 installs.

[https://edge.launchpad.net/~sssup/+archive/sssup-ppa/+packages](https://edge.launchpad.net/~sssup/+archive/sssup-ppa/+packages)

mozilla-plugin-lightspark Experimental high-performance SWF (Adobe Flash) player 
Package files
lightspark_0.4.1-0ubuntu1.diff.gz (20 bytes) 
lightspark_0.4.1-0ubuntu1.dsc (2.1 KiB) 
lightspark_0.4.1-0ubuntu1_amd64.deb (3.4 MiB) 
lightspark_0.4.1-0ubuntu1_i386.deb (3.4 MiB) 
lightspark_0.4.1.orig.tar.gz (217.4 KiB) 
mozilla-plugin-lightspark_0.4.1-0ubuntu1_amd64.deb (3.5 MiB) 
mozilla-plugin-lightspark_0.4.1-0ubuntu1_i386.deb (3.5 MiB)

Bear in mind that most flash don't work yet and youtube doesn't work at all.

---

### Post by ranch hand on 2010-06-12
Yup, just curious and I have 10.04 installs just sitting around anyway waiting to be over written by some thing that boots better (almost anything) so I can see what it looks like.

Might be the wave of the future.

Until moving to town I really never used flash as 4.4kb down load speed is not real good with flash.  I have read for years that folks are not real happy with it however.

This current business with Adobe may very well be a good thing.  May be just the spark some developer(s) need to jump on this.

---

### Post by llawwehttam on 2010-06-12
I was using the 64 bit plugin, had problems and went to flashplugin-installer, got the update yesterday and it seems to be working better for me in 64 bit than the 64 bit plugin did!

It also works on my main 9.10 rig.

---

### Post by Merk42 on 2010-06-12
So I got rid of the 64bit figuring it would default to the 32bit one that it gave in the updates.

Now any site with Flash either makes Firefox unresponsive, or completely crashes it.

---

### Post by yelo3 on 2010-06-13
You could try to change the file /usr/lib/nspluginwrapper/i386/linux/npviewer in this way

> #!/bin/sh
TARGET_OS=linux
TARGET_ARCH=i386[B]
export GDK_NATIVE_WINDOWS=1[/B]
. /usr/lib/nspluginwrapper/noarch/npviewer

Thak solved most problems (well fullscreen does not work yet)

---

### Post by ronacc on 2010-06-13
I'm using 64bit flash , it still works with Opera . Just watched a You Tube video of the reentry of the Hayabusa probe over Austraila .

---

### Post by Merk42 on 2010-06-13
> **ronacc said:**
> I'm using 64bit flash , it still works with Opera . Just watched a You Tube video of the reentry of the Hayabusa probe over Austraila .

I don't think anyone is saying the 64bit alpha doesn't work, just that it's [not secure](http://www.adobe.com/support/security/advisories/apsa10-01.html).

---

### Post by ronacc on 2010-06-13
I never assumed any flash was secure .I only enable it for very specific purposes and then disable it immediately after .

---

### Post by Merk42 on 2010-06-13
> **ronacc said:**
> I never assumed any flash was secure .I only enable it for very specific purposes and then disable it immediately after .
Well I don't think most people would want to do that, plus you still run the risk of getting infected through even a trusted site.

Anyway, back on topic, using the 32bit plugin via nspluginwrapper, I noticed when viewing a lot of Youtube videos, scrubbing won't work.  Clicking on the timeline doesn't move the button over.

---

### Post by Colonel Kilkenny on 2010-06-14
> **Merk42 said:**
> I don't think anyone is saying the 64bit alpha doesn't work, just that it's [not secure]("http://www.adobe.com/support/security/advisories/apsa10-01.html").
Yes, but that doesn't really matter with Opera as 64bit Opera can use both 64bit and 32bit plugins.
 
And not responding to clicks: GDK_NATIVE_WINDOWS trick should fix that.

---

### Post by philinux on 2010-06-14
Normal screen size works here and buttons work as they should. Only problem is full screen. Laggy and about 2 frames/second.

---

### Post by Milos_SD on 2010-06-14
Here works everything, but I'm still on Lucid. Flash 10.1 32bit on 64bit Ubuntu.

---

### Post by yelo3 on 2010-06-14
In the launchpad bug about buttons not working in youtube, some users say that in lucid they don't need the "use native windows" trick.
I still need it.

---

### Post by nanog on 2010-06-14
> Jun 13 17:48:16  kernel: [441677.598776] npviewer.bin[22798]: segfault at 418 ip 00000000f6108a56 sp 00000000ffdbf8b8 error 6 in libflashplayer.so[f5eba000+b04000]

Gaaaaaah! I lost some work due to inadvertant installation of 32 bit! Its good to know that nspluginwrapper locks up the kernel every 10 minutes like it used to. I really respect that kind of reliability. 


solution:

```
sudo apt-get remove --purge nspluginwrapper flashplugin-installer\
#Die nspluginwrapper!
```

```
mkdir ~/.mozilla/plugins ; cp libflashplayer.so ~/.mozilla/plugins
```

---

### Post by yelo3 on 2010-06-15
I also have these segfaults, and I think that when I get them all flash object become blank and I have to refresh the page.
I'll file a bug immediately!

PS: the other part of your message is really off topic (read the first topic post)

**EDIT:**
This is the bug link [https://bugs.launchpad.net/ubuntu/+source/nspluginwrapper/+bug/462433](https://bugs.launchpad.net/ubuntu/+source/nspluginwrapper/+bug/462433)

---

### Post by yelo3 on 2010-07-02
Could someone be able to fix the fullscreen issue?

---

### Post by philinux on 2010-07-02
> **yelo3 said:**
> Could someone be able to fix the fullscreen issue?

[http://ubuntuforums.org/showpost.php?p=9468193&postcount=4](http://ubuntuforums.org/showpost.php?p=9468193&postcount=4)

There you go.

---

### Post by yelo3 on 2010-07-02
that won't work. it fixes buttons only

---

### Post by VastOne on 2010-07-02
> **cariboo907 said:**
> If we are using the 64-bit version now, why do we have to stop using it if it is no longer available. :) I've archived a couple of copies of the tgz file for when I need it.

Same here..

And on Alpha 2 I could not get Flash Aid to load any of the ndiswrapper stuff so I had to resort to the 64 bit Alpha flash

Working great with the only issue being full screen choppiness when moving the mouse.

When I resolve the flash aid issues, I will report back.

---

### Post by philinux on 2010-07-02
> **yelo3 said:**
> that won't work. it fixes buttons only

Fixed full screen for me.

---

### Post by yelo3 on 2010-07-02
Lucky you! Maybe it's a graphic card problem. I have an intel x4500hd

---

