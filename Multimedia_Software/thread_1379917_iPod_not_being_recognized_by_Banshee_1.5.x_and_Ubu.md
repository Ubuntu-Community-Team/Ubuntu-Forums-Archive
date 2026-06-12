---
title: "iPod not being recognized by Banshee 1.5.x and Ubuntu Karmic 9.10"
date: 2010-01-13
forum: Multimedia Software
---

### Post by mangasan on 2010-01-13
Hi all,

after upgrading to Karmic I started having problems with ipod and banshee.
 
I have found out this a known problem. You can check it at the [banshee site]("http://banshee-project.org/download/archives/1.5.2/")

> There is a known issue with iPod not being recognized by Banshee on openSUSE 11.2 and Ubuntu Karmic.

mainly because of switching from HAL to device kits, as done with Ubuntu Karmic 9.10. 

Related bug is #**586508** "Underlying distros moving from HAL to DeviceKit breaks Podsleuths ability to mount device"

More details are available at

[https://bugzilla.gnome.org/show_bug.cgi?id=586508](https://bugzilla.gnome.org/show_bug.cgi?id=586508)


At the time of this writing a possible workaround is reported to be the following:

> [...]all I would have to do is disconnect the ipod and
make sure that banshee is closed.  Then open up terminal and run 

```
killall -9 nautilus
```

Then plug in the iPod and wait about 30 seconds, then run nautilus again by hitting Alt+F2.  After I ran this and opened up banshee my iPod worked like a charm.

HTH.

Cheers.

---

### Post by mangasan on 2010-01-27
Hi guys,

this issue has been fixed with 1.5.4 version (formerly "1.5.4~really1.5.2-0ubuntu1~hyper2~karmic"). 

The banshee team released it the 21st of January. You can update your Karmic by using the banshee PPA repository as explained here

[https://edge.launchpad.net/~banshee-team/+archive/ppa](https://edge.launchpad.net/~banshee-team/+archive/ppa)

hth.

cheers.

---

### Post by Fnyar on 2010-01-28
> **mangasan said:**
> Hi guys,

this issue has been fixed with 1.5.4 version (formerly "1.5.4~really1.5.2-0ubuntu1~hyper2~karmic"). 

The banshee team released it the 21st of January. You can update your Karmic by using the banshee PPA repository as explained here

[https://edge.launchpad.net/~banshee-team/+archive/ppa](https://edge.launchpad.net/~banshee-team/+archive/ppa)

hth.

cheers.

Thanks, I found the bug report and then this forum posting about adding the PPA repo to fix the problem. That did it for me, although I had to eject/reconnect my iPod several times and restart banshee several times for the iPod to finally get detected. Thanks for posting this.

Ubuntu should just push these fixes into the normal repositories so people don't have to go hunting around for a fix. This is a pretty serious problem if you are a banshee user and own (and would like to actually USE) your iPod.

---

