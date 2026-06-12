---
title: "iPhone OS 3.0 Sync"
date: 2009-06-21
forum: Multimedia Software
---

### Post by rdwtux on 2009-06-21
Has anyone tried syncing iPhone OS 3.0 with GTKPOD or other software?

Any luck? tricks?

Thanks.

---

### Post by loveandequality on 2009-06-21
> **rdwtux said:**
> Has anyone tried syncing iPhone OS 3.0 with GTKPOD or other software?

Any luck? tricks?

Thanks.
Check out my guide. Even tho is for the ipod 2g my Ubuntu says is an iphone so it might work. You need to jail breack first to play songs and this is an USB sync. I use ifuse...

---

### Post by IceSheep on 2009-06-21
Unfortunately the hack which worked in Firmware 2.x (changing the DBVersion from 4 to 2) doesn't help anymore. I can still transfer songs using iFuse and Amarok but they won't show up on the iPhone.

Can anybody confirm this behaviour?

---

### Post by rdwtux on 2009-06-21
> **loveandequality said:**
> Check out my guide. Even tho is for the ipod 2g my Ubuntu says is an iphone so it might work. You need to jail breack first to play songs and this is an USB sync. I use ifuse...

I know iPhone OS 2.0 works fine.  I was asking about 3.0

> **IceSheep said:**
> Unfortunately the hack which worked in Firmware 2.x (changing the DBVersion from 4 to 2) doesn't help anymore. I can still transfer songs using iFuse and Amarok but they won't show up on the iPhone.


This is what I'm seeing too.  At first glance it looks like the directory structure has changed quite a bit from OS 2.0.

---

### Post by kingmoffa on 2009-06-22
also have the same problem. 

Firmware 3 was such a let down for me - no a2dp bluetooth audio and now this ****. Will probably downgrade v soon.
Im getting an google android phone sooner or later - hopefully no need to do crap lik this.

---

### Post by teh'p3nsi0n3r on 2009-06-26
Hi folks,

thought i would post some information i have found out. nothing major but just trying to do my best to help out.

I have upgraded my firmware to 3.0 on my iphone (jailbroken also).
Now i use a windows laptop and a ubuntu machine, at the moment have been using mediamonkey on the 2x firmware on windows to sync my tunes as i refuse to use itunes for music. This no longer works and the 3.0 firmware causes mediamonkey to crash.
Doing alittle reading and research i have found out folk had been using itunes in virtualbox / vm ware and whatnot and syncing there iphone that way.
I found out an app i came accross a while back called copytrans manager which worked with my 2x firmware but to transfer tunes i needed to jailbreak my phone.
after looking at there site i decided to try the copy trans suite under wine as it said copy trans and copy trans photo were now 3.0 compatible (zip extracted to folder and the exe install). these did not run under wine. This then made me think! The copytrans suite may work in vitualbox like folks are using itunes?. just a thought.

The only issue with my idea above so far is **copytrans manager** is not yet 3.0 compatible, only copytrans and copytrans photo. 

But the good news is I did test the manager on windows and it gave me the message explaining that it wasn't compatible but i could email them for any info. so i did, here is the response i got.

> Dear X

thank you very much for your email and interest in CopyTrans Manager.

Our developers are working very hard on bring full OS 3 compatibility to
all of our products.
CopyTrans Manager should follow shortly. We are hoping in the next
couple of weeks.

If you allow, I will update you when this is the case.

In the meantime, please let me know if there is anything else I can do.

Best regards,
Stephen

So again coming back to copytrans manager in a virtualbox, this is a lightweight app, and may work in a virtualbox as long as you can get usb/iphone working in a virtualbox, to which i did read someone did. 
I personally will be using windows with this app as most of my music is on my laptop but will most likely give this a go.
But i just thought i would share my 2 cents, maybe it might spark some of you more techy/developer folks ideas. :)

---

### Post by rdwtux on 2009-06-27
I've tried using iFuse and ipod-convenience with firmware 3.0. Both mount the phone fine. 

I'm a bit confused because a few persons on the iFuse/libiphone mailling list are saying it's working fine with firmware 3.0.    It definitely does mount the iphone correctly and I have access to the files, however I can't get any programs to transfer mp3's to the iphone. 

I think they're just referring to the fact that connectivity is achieved and after that it's gtkpod/rhythmbox/libgpod territory??  Not sure. 

Still searching....  I also tried downgrading back to firmware 2.0 but haven't had luck yet.

---

### Post by eugenevdm on 2009-06-27
This post presents a reason why iPhone 3.0 and Ubuntu does not work any more:

[https://help.ubuntu.com/community/PortableDevices/iPhone#Firmware%203.0](https://help.ubuntu.com/community/PortableDevices/iPhone#Firmware%203.0)

---

### Post by kingmoffa on 2009-07-03
I cant seem to downgrade to version to of my firmware. So now I have a phone that isnt working. 
God I hate apple - their greed will come and bite them.

---

### Post by xrecar on 2009-07-05
Ugh, I hate this. Why are they so focused on leaving us out? Aren't we consumers as well?

I'm looking at these posibilites:

[http://www.gsmarena.com/samsung_i7500-review-351.php](http://www.gsmarena.com/samsung_i7500-review-351.php)
[http://www.htc.com/www/product/hero/overview.html](http://www.htc.com/www/product/hero/overview.html)
[http://www.palm.com/us/products/phones/pre/](http://www.palm.com/us/products/phones/pre/) (GSM VERSION)

---

### Post by philcamlin on 2009-07-05
hmm thats why i use my dads laptop for iods :)

kinda makes me mad how mac was based off unix but they offer no support :(

whats the deal:popcorn:

---

### Post by teh'p3nsi0n3r on 2009-07-10
[http://ubuntuforums.org/showthread.php?t=1208906](http://ubuntuforums.org/showthread.php?t=1208906) :p

---

### Post by Breakbone on 2009-07-14
Hello all,

I have read through the posts on this subject, and am saddened to read that the only known to work solution requires the install of windows and itunes. Why go back to two campanies that treat us so bad. I have no desire to go crawling back there. That is why I have Ubuntu installed. If I have to never sync my iphone again, than so be it. That is not to say that I wouldn't love to be able to under Linux, but right now it is just not worth it. Whom ever figures it out how to do it right will be my hero, i'll wait till then.

---

### Post by blamc on 2009-08-30
Having the same issues.... including not being able to downgrade my firmware.  A possible solution is to install pwnplayer lite on your iphone/ipod touch (must be jailbroken).  Once pwnplayer is installed you can use ssh to copy mp3 files directly to the iphone and play them with pwnplayer.  Make sure to use the lite version because the regular pwnplayer is broken on the 3.0 firmware.  Simply open pwnplayer and check to see where it wants you to store those mp3's.  Pwnplayer isn't perfect but it gives you another option!

---

### Post by faxm0dem on 2009-10-29
At the time of writing, libgpod is almost ready for the new hash.
Also, you've gotta take a look at this:

[http://marcansoft.com/blog/2009/10/iphone-syncing-on-linux/#](http://marcansoft.com/blog/2009/10/iphone-syncing-on-linux/#)

I tested it and it works great.

---

### Post by TDFZ on 2009-11-08
> **blamc said:**
>   Pwnplayer isn't perfect but it gives you another option!

PwnPlayer is cool.  I have the newest iPhone Firmware on my 3g and it works great with PwnPlayer.

---

### Post by taranfx on 2010-04-02
I had written a guide for [Sync iPhone on Ubuntu]("http://www.taranfx.com/sync-iphone-linux")  with Amarok. Worked pretty well for most on Ubuntu 9.1

---

### Post by Chronon on 2010-04-02
Here's the community help page:
[https://help.ubuntu.com/community/PortableDevices/iPhone#Firmware%203.0](https://help.ubuntu.com/community/PortableDevices/iPhone#Firmware%203.0)

---

### Post by eugenevdm on 2010-04-03
> **taranfx said:**
> I had written a guide for [Sync iPhone on Ubuntu]("http://www.taranfx.com/sync-iphone-linux")  with Amarok. Worked pretty well for most on Ubuntu 9.1

I have added your link to the community page. Could someone from the community please start splitting up that page, it's getting too long now.

---

