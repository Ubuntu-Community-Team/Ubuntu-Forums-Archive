---
title: "Natty Installer crashes when run from USB key"
date: 2011-02-04
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by recluce on 2011-02-04
I decided to try natty alpha2 again, after alpha1 crashed during installation for me. Turns out, it still does (about 75% complete).

The bug is reported here: 

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/684921](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/684921)

And bottom line is: nobody cares. Two months old, confirmed, unassigned, 3 subscribers. 

This is a show-stopping problem for anybody who relies on a USB key and still, nobody cares? What is wrong with the community nowadays?

---

### Post by mc4man on 2011-02-04
Not probably the intent of this thread, (it should work directly from 'install .."),  more out of curiosity - have you tried running the installer from the live cd desktop instead? (first pick 'try ubuntu...', then use the desktop icon

I've also  had more than a number of failed installs when going directly to 'install..', when using the desktop installer it always works

---

### Post by cariboo on 2011-02-04
I found several other bugs about the same problem:

[lpbug]684921[/lpbug] - yours
[lpbug]703552[/lpbug]
[lpbug]710992[/lpbug]
[lpbug]712546[/lpbug]
[lpbug]706193[/lpbug]

Give it some more time.

---

### Post by recluce on 2011-02-04
> **mc4man said:**
> Not probably the intent of this thread, (it should work directly from 'install .."),  more out of curiosity - have you tried running the installer from the live cd desktop instead? (first pick 'try ubuntu...', then use the desktop icon

I've also  had more than a number of failed installs when going directly to 'install..', when using the desktop installer it always works

I tried that, same result.

---

### Post by recluce on 2011-02-04
> **cariboo907 said:**
> I found several other bugs about the same problem:

[lpbug]684921[/lpbug] - yours
[lpbug]703552[/lpbug]
[lpbug]710992[/lpbug]
[lpbug]712546[/lpbug]
[lpbug]706193[/lpbug]

Give it some more time.

Thanks for looking that up. 703552 seems to be a duplicate of 684921, but doesn't seem to generate much more attention either. With the rest, I don't see the connection, as they seem to be about problems installing proprietary drivers (NVidia).

Other than that, I will certainly give it more time. As things are going, I might even stay with Lucid (backported natty kernel) until the next LTS.

---

### Post by cariboo on 2011-02-04
I know the devs are well aware of the problems, they've had it way to easy over the last couple of years, and now they're paying for it :)

---

### Post by rbrick49 on 2011-02-04
yes i had the same problem with alpha 1 and alpha2 last night the error came up as something to do with casper and also  I think and initrams not sure of my spelling as I couldnt see it properly this is on a amd system

---

### Post by nowin4me on 2011-02-04
I think you have to do it thought the "Try Ubuntu" option, it worked for me that way, just having other issues now.

---

### Post by rbrick49 on 2011-02-04
> **nowin4me said:**
> I think you have to do it thought the "Try Ubuntu" option, it worked for me that way, just having other issues now.

aw geez mate its only alpha2 it will get better soon

---

### Post by teachop on 2011-02-05
Yes.  Crashed part way thru for me too, attempting to install from the USB.  Then it dumped me out into Try Ubuntu, I did the install from there, and it completed.  (not much *AT ALL* works in the resulting system - but that is another alpha story...)

---

### Post by rebootme on 2011-02-05
Same here.  Fails when you select install at the try/install screen.  But works when you click the install link on the desktop once you boot into "try".

---

### Post by recluce on 2011-02-06
So far, it seems that there is way more than one bug at work here. Ancedotal evidence from the bug tracks posted by cariboo907 and the posts here point in at least three directions:

1.) Installer only crashes when run from Splash screen, but not when run from Live CD Desktop.

2.) Installer always crashes

3.) Installation of proprietary drivers (eg NVidida) crashes.

It seems that the developers have their work cut out. Hopefully there is more activity regarding these issues than the launchpad tickets suggest at this time.

---

### Post by ronacc on 2011-02-06
for me it always crashes right at the end of the install process just before home is populated and grub installed .

---

### Post by julianb on 2011-02-06
i tried Ubuntu Natty alpha 1, and Kubuntu natty alpha 2, both from USB key. I did not try to install to hard drive, just used "try Ubuntu without installing". Ubuntu alpha 1 was fine. Kubuntu alpha 2 seemed to run into some kernel-related problem after I had been using it for half an hour and tried to find a way to zsync to update the Ubuntu Natty alpha 1 image.

---

### Post by nm_geo on 2011-02-07
> **ronacc said:**
> for me it always crashes right at the end of the install process just before home is populated and grub installed .

The current daily Natty build did not install for me either.  Tired both ways from the Install Ubuntu and from the Try Ubuntu then install from desktop.  The crash report said my HD might have a problem move to cooler environment (not about to take it outside right now LOL)... The HD is brand new so I know that is not a problem and if it is I have a clone of it ready to go.

Will keep testing the current daily builds every day or two just for kicks.  
I know you are too ronacc.

---

### Post by cariboo on 2011-02-07
@nm_geo you can install hddtemp from the repositories to monitor hard drive temps.

---

### Post by nm_geo on 2011-02-07
> **cariboo907 said:**
> @nm_geo you can install hddtemp from the repositories to monitor hard drive temps.

Yeah cariboo, I have them installed in Lucid and Maverick.  I am sure this laptop is not running too hot.  In fact I am going to try the install again and capture some of the information.

---

### Post by nm_geo on 2011-02-08
Okay, I just tried to install Natty from today's current build and it again did not like my HD.   So I fished around and found a USB with Maverick 10.10 on it and installed it in the same partition that was set up for Natty.  Maverick installed just fine but now I have more Mavericks than I want.  So I will remove it and try another Natty install from another direction in a few days, hours or minutes.
:lolflag:

---

