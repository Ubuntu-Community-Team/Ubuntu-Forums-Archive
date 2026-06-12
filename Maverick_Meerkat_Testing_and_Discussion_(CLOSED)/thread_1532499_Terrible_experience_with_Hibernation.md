---
title: "Terrible experience with Hibernation"
date: 2010-07-16
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by donniezazen on 2010-07-16
I have a real bad experience hibernating Ubuntu. Either it fails or takes forever to recover. And it is not at all smooth. Does Meerkat plans to bring a better hibernation experience? In my opinion, more than faster boot a quick and easy hibernation would be more beneficial. People will not have to shutdown until it's required by an update and we will not have to close the browser, etc.

Thanks.

---

### Post by cariboo on 2010-07-16
I think it really depends on your hardware, My Compaq netbook hibernates and suspends with no problems, It does take as long as a reboot to come out of hibernation though.

---

### Post by laceration on 2010-07-16
Hibernation is something that the kernel does, so Meerkat would only change Hibernation insofar as it would have a different kernel.  There actually is, imo + others, a superior implementation of Hibernation, it is called Tuxonice.  There is some kind of political static with it tho and it is not incorporated into the kernel.  You can install a Tuxonice configured kernel from PPA.  A guide on how to do it is here:

[http://www.ubuntugeek.com/how-to-install-tuxonice-in-ubuntu.html](http://www.ubuntugeek.com/how-to-install-tuxonice-in-ubuntu.html)

Warning--this does take quite a bit of configuration, I'd put aside an afternoon if you want to do it, but this was the only way I ever got Hibernate to work on my laptop and it works great.

---

### Post by cyberkilla on 2010-07-16
My hibernation - on a Sony Vaio - is pretty reliable, but I'm not overly impressed with the resume speed.:p

---

### Post by donniezazen on 2010-07-17
I have a laptop and a netbook. And the hibernation is not impressive on both.

---

### Post by donniezazen on 2010-07-17
> **laceration said:**
> Hibernation is something that the kernel does, so Meerkat would only change Hibernation insofar as it would have a different kernel.  There actually is, imo + others, a superior implementation of Hibernation, it is called Tuxonice.  There is some kind of political static with it tho and it is not incorporated into the kernel.  You can install a Tuxonice configured kernel from PPA.  A guide on how to do it is here:

[http://www.ubuntugeek.com/how-to-install-tuxonice-in-ubuntu.html](http://www.ubuntugeek.com/how-to-install-tuxonice-in-ubuntu.html)

Warning--this does take quite a bit of configuration, I'd put aside an afternoon if you want to do it, but this was the only way I ever got Hibernate to work on my laptop and it works great.

Thanks, Is it moderately safe? I am running couple of nightly build ppa like x-edgers and gnome-shell. I hope it will not interfere with these PPAs.

---

### Post by victorhugo289 on 2010-07-17
Well, so far hibernation is fantastic for me, it loads everything perfectly and fast. I love it.

My computer:     Pentium 4, 2GHz, 1GB ram. 128MB video ATI. Ubuntu 10.04.

---

### Post by ronacc on 2010-07-17
you're in the northen hemisphere it's summer you estivate not hibernate thats your problem .

---

### Post by donniezazen on 2010-07-17
> **laceration said:**
> Hibernation is something that the kernel does, so Meerkat would only change Hibernation insofar as it would have a different kernel.  There actually is, imo + others, a superior implementation of Hibernation, it is called Tuxonice.  There is some kind of political static with it tho and it is not incorporated into the kernel.  You can install a Tuxonice configured kernel from PPA.  A guide on how to do it is here:

[http://www.ubuntugeek.com/how-to-install-tuxonice-in-ubuntu.html](http://www.ubuntugeek.com/how-to-install-tuxonice-in-ubuntu.html)

Warning--this does take quite a bit of configuration, I'd put aside an afternoon if you want to do it, but this was the only way I ever got Hibernate to work on my laptop and it works great.



Thanks for suggesting Tux on Ice. It certainly is better than preset Ubuntu hibernation. I have not done any configuration so far. Does it uses the latest stable kernel as available by default or previous modified versions?

---

### Post by laceration on 2010-07-18
> Thanks for suggesting Tux on Ice. It certainly is better than preset Ubuntu hibernation. I have not done any configuration so far. Does it uses the latest stable kernel as available by default or previous modified versions?
The ppa for karmic has pretty much been keeping pace with the default kernel upgrades.  All the upgrades are a slight pain as they don't update your menu.lst properly.

---

### Post by kyleabaker on 2010-07-18
I haven't tested this in my Ubuntu 10.10 computer yet since its a desktop, but Ubuntu 10.04 Standby and Hibernation both end up crashing my HP Pavilion dv1000. I hope this gets fixed for 10.10 cause I can't conveniently use my laptop with Ubuntu on the go without a stable standby/hibernation ability.

---

### Post by Nigel_C on 2010-09-04
> **laceration said:**
> The ppa for karmic has pretty much been keeping pace with the default kernel upgrades.  All the upgrades are a slight pain as they don't update your menu.lst properly.

Hi.

I'm Nigel Cunningham, the TuxOnIce maintainer. I don't prepare the PPAs anymore, but I'll happily pass on your comment about menu.lst not being properly updated. First though, could you be a bit more specific? What are you getting at the moment and how would you like it to be different?

Thanks!

---

### Post by laceration on 2010-09-04
Hi Nigel, thanks for the great work you have done.  It has made a big difference for me.  I had much frustration and wasted a ton of time until I found Tuxonice.

It's been awhile since a kernel update, so I do not remember 100% clearly, but I believe that the kernel lines in menu.lst got written as so:

```

kernel		/boot/vmlinuz-2.6.32-22-generic-tuxonice root=UUID=5eba2ace-01b7-4877-a827-edd23ec05e23 ro quiet splash

kernel		/boot/vmlinuz-2.6.32-22-generic-tuxonice root=UUID=5eba2ace-01b7-4877-a827-edd23ec05e23 ro  single


```

They need to be written like this for tuxonice to work(red text at end needs to be added):

```

kernel		/boot/vmlinuz-2.6.32-22-generic-tuxonice root=UUID=5eba2ace-01b7-4877-a827-edd23ec05e23 ro quiet splash [COLOR="Red"]resume=swap:/dev/sda3[/COLOR]

kernel		/boot/vmlinuz-2.6.32-22-generic-tuxonice root=UUID=5eba2ace-01b7-4877-a827-edd23ec05e23 ro  single [COLOR="Red"]resume=swap:/dev/sda3 noresume
[/COLOR]

```
of course /dev/sda3 is just one possible value.

Thanks!

---

### Post by Humphreybas on 2010-09-28
On the original topic:

My Toshiba U400 did hibernate on 9.04 but was very slow in resuming.

On 10.10 it is just terrible. 9 out of 10 times the system just freezes with a black screen and only cursor or some error message. Will try to write them down and post them soon.

---

### Post by Quackers on 2010-09-28
> **cyberkilla said:**
> My hibernation - on a Sony Vaio - is pretty reliable, but I'm not overly impressed with the resume speed.:p

That's interesting. My Vaio suspends very well and its recovery from suspend is almost instantaneous. However, if I use hibernate it just does a normal shutdown (and that's using the menu - not a button). 
It does the same in Lucid and Meerkat. I'm wondering if it's a smbios issue, but I'd be surprised if it was.

---

