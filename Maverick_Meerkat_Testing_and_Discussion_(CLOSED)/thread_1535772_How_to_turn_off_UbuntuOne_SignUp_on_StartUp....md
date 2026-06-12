---
title: "How to turn off UbuntuOne SignUp on StartUp..."
date: 2010-07-21
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by zika on 2010-07-21
It is nice to be offered to sign up to something. But, since I'm not ready to sign up and I want to free my Nautilus from considerable startup delay due to UbuntuOne, I would prefer to be able to skip automatic opening of WEBBrowser with this offer every time i boot any of several machines of mine...
Is is possible to turn it off?
Yes, I've tried to answer "Cancel"...
I'm afraid that, if I were to give all the information, I would not be able to turn it off never...
Any hints?
Update1:
OK, I succumbed... On one machine it stopped after I've sign up, checked and unchecked that machine. Even though , now, have to enter keyring pass every time I boot... :(
On second machine, I can not pass the keyring authentication even though I have proper pass and I'm the only one that have ever seen or touched this machine and this Maverick installation... I've never changed any pass-es on this machine, from the installation... Everything other works with that pass, sudo, gksu, everything...

Weird... :(

Update2:
OK, I've managed to pass the keyring problem with deleting Default keyring...
But, on both machines, now, I have to close keyring authentication on boot... I do not want to have that step on my boot...

Any ideas?

On the + side is that Nautilus is, now, starting much faster...

You loose some, You gain some...

---

### Post by ranch hand on 2010-07-21
I know we are supposed to test these things but Ubuntu One is something I will never use.  I do have it on all but my 2 "main" installs of 10.10 and it is a pain.

If I was not using it, therefore not testing it, on an only installation, I would just remove the bugger and forget it.

There is, as far as I can see, no testing purpose to having it on your box at all.

You could file a bug on Ubuntu One being a pain and give the work around of removing it as a cure.  This might get someones attention.  I thought about it and then decided I just really did not care enough to bother.

If you do I will join in.

---

### Post by andrek on 2010-07-21
I experienced this today, right after a clean install of maverick. Solution? Remove all the ubuntuone packages and use dropbox. :)

---

### Post by ranch hand on 2010-07-21
I could not take it any more.  The crap in nautilus I could take.  The spam on auto opening FF was just to much for me after opening a couple of installs.  That bugger is gone.

Too bad it is.  I may well have used the music store.

If anyone is interested I did file a bug;

[https://bugs.launchpad.net/ubuntu/+source/ubuntuone-client/+bug/608509](https://bugs.launchpad.net/ubuntu/+source/ubuntuone-client/+bug/608509)

---

### Post by stevetxt on 2010-07-22
This thread might be related:

[http://ubuntuforums.org/showthread.php?t=1523309](http://ubuntuforums.org/showthread.php?t=1523309)

---

### Post by cariboo on 2010-07-22
Has anyone created a bug about this problem?

---

### Post by VMC on 2010-07-22
> **cariboo907 said:**
> Has anyone created a bug about this problem?
Post  #4 above.

---

### Post by cariboo on 2010-07-22
Oops :)

---

### Post by ratcheer on 2010-07-22
> **ranch hand said:**
> I could not take it any more.  The crap in nautilus I could take.  The spam on auto opening FF was just to much for me after opening a couple of installs.  That bugger is gone.

Too bad it is.  I may well have used the music store.

If anyone is interested I did file a bug;

[https://bugs.launchpad.net/ubuntu/+source/ubuntuone-client/+bug/608509](https://bugs.launchpad.net/ubuntu/+source/ubuntuone-client/+bug/608509)

Thank you. I have added myself as affected.

Tim

---

### Post by 23meg on 2010-07-22
> **ranch hand said:**
> I could not take it any more.  The crap in nautilus I could take.  The spam on auto opening FF was just to much for me after opening a couple of installs.  That bugger is gone.

Too bad it is.  I may well have used the music store.

If anyone is interested I did file a bug;

[https://bugs.launchpad.net/ubuntu/+source/ubuntuone-client/+bug/608509](https://bugs.launchpad.net/ubuntu/+source/ubuntuone-client/+bug/608509)

It would help with the utility of your bug reports to avoid potentially derogatory terms such as "this crap" in your descriptions, as well as veiled threats of not using the software, especially before you know whether a particular behavior is intentional or not. Changes such as this are often due to bugs in the development branch, as has been the case here.

---

### Post by ranch hand on 2010-07-22
> **23meg said:**
> It would help with the utility of your bug reports to avoid potentially derogatory terms such as "this crap" in your descriptions, as well as veiled threats of not using the software, especially before you know whether a particular behavior is intentional or not. Changes such as this are often due to bugs in the development branch, as has been the case here.
I decidedly do not like to disagree with you as you are too often right and a great mod.

However, in this case, I do not believe that auto opening FF can be anything but intended.  There are a lot of very good reasons not to open a resource hungry app like FF, in any version, on startup.  This is just bad.

This is nothing but a hijack of the way the user wants to set up on startup and advertising spam.

I did not like this in MS and do not like it here.  There is no way that I will use this software with behavior like this and I do not think that I am alone in this.   Could be, though, I guess.

Having things suddenly not work or work strangely in testing I do not mind a bit.  Being forced to deal with advertising for a feature, if I like it or not, is not something that I am prepared, in any way, to put up with.

---

### Post by 23meg on 2010-07-22
> **ranch hand said:**
> However, in this case, I do not believe that auto opening FF can be anything but intended.  There are a lot of very good reasons not to open a resource hungry app like FF, in any version, on startup.  This is just bad.

This is nothing but a hijack of the way the user wants to set up on startup and advertising spam.

> **ranch hand said:**
> Being forced to deal with advertising for a feature, if I like it or not, is not something that I am prepared, in any way, to put up with.

Rodrigo Moya, an Ubuntu One developer, has [confirmed]("https://bugs.launchpad.net/ubuntu/+source/ubuntuone-client/+bug/608509/comments/5") in a comment to the bug report that the behavior is not intentional, and is apparently due to a bug, which is to be investigated.

That leaves no doubt that the change was not intended, your setup isn't being hijacked, you aren't being intentionally spammed on startup, and that the world isn't coming to an end.
 
It would really contribute to a higher quality of discussion and bug dialogue if you refrained from forming conspiracy theories around changes you're not sure about the reason of, especially in the development branch, which is in flux most of the time, and prone to changes of this nature that may or may not be intentional.

---

### Post by zekopeko on 2010-07-22
> **ranch hand said:**
> I decidedly do not like to disagree with you as you are too often right and a great mod.

However, in this case, I do not believe that auto opening FF can be anything but intended.  There are a lot of very good reasons not to open a resource hungry app like FF, in any version, on startup.  This is just bad.

This is nothing but a hijack of the way the user wants to set up on startup and advertising spam.

I did not like this in MS and do not like it here.  There is no way that I will use this software with behavior like this and I do not think that I am alone in this.   Could be, though, I guess.

Having things suddenly not work or work strangely in testing I do not mind a bit.  Being forced to deal with advertising for a feature, if I like it or not, is not something that I am prepared, in any way, to put up with.

Apparently you were wrong as usual.

[https://bugs.launchpad.net/ubuntu/+source/ubuntuone-client/+bug/608509/comments/5](https://bugs.launchpad.net/ubuntu/+source/ubuntuone-client/+bug/608509/comments/5)

Just to be clear Rodrigo Moya is an UbuntuOne dev.

The plan for marketing UbuntuOne is far less "in your face" then your ranting suggests. 
The plan is to replace the first Evolution email and the first Tomboy note with something informing the user about the benefits of U1.
In Unity (not sure if in 10.10 or 11.04) you can expect a U1 icon in the launcher by default.
This all is on top of the installer slideshow which should have a mention of U1.

---

### Post by jerrylamos on 2010-07-22
I have System > Preferences > Startup Applications > UbuntuOne set to off.  I tried using UbuntuOne a while back and it was too many steps all the time.  Too much bother.  I just copy over our local net.  I'll try UbuntuOne again when the Meerkat Alpha & Beta bugs get down to a dull roar.

In the meanwhile I would appreciate any hints on how to keep UbuntuOne from coming up on startup since I've got it set to off.

Thanks, Jerry

---

### Post by ktp on 2010-07-22
> **jerrylamos said:**
> I have System > Preferences > Startup Applications > UbuntuOne set to off.  I tried using UbuntuOne a while back and it was too many steps all the time.  Too much bother.  I just copy over our local net.  I'll try UbuntuOne again when the Meerkat Alpha & Beta bugs get down to a dull roar.

In the meanwhile I would appreciate any hints on how to keep UbuntuOne from coming up on startup since I've got it set to off.

Thanks, Jerry

Have you tried following:

[http://ubuntuforums.org/showpost.php?p=9544559&postcount=5](http://ubuntuforums.org/showpost.php?p=9544559&postcount=5)

---

### Post by zika on 2010-07-23
If anyone had the idea how to turn off this keyring pop-up, that I have now, asking me for the password, at every boot, I would be grateful.
I'll be off-line next ~30 days, so do not be angry on the absence of my answer to the possible solution...

---

### Post by dino99 on 2010-07-23
have done it: synaptic remove/purge everything about ubuntuone

---

### Post by andrewabc on 2010-07-23
Pretty sure a machine of mine is affected by this.
Parent was using computer and asked what this was, and I had no idea why firefox was opened to ubuntuone signup page. google is the homepage so not sure how it got there. Although I started computer today and it didn't bring it to ubuntu one page. So not sure if fixed or if random.

Glad this feature will be removed according to bug report.

I have to agree that bug report was not very professional or courteous, although I'm sure I feel the same way if firefox opened up on me to something I didn't want.

EDIT:
Just did updates and restarted and firefox opened up to ubuntuone sign up page. :(

---

### Post by VMC on 2010-07-23
> **zika said:**
> If anyone had the idea how to turn off this keyring pop-up, that I have now, asking me for the password, at every boot, I would be grateful.
I'll be off-line next ~30 days, so do not be angry on the absence of my answer to the possible solution...

As someone suggested, this turned it off:
```
sudo apt-get purge ubuntuone-client-gnome
```

---

### Post by mc4man on 2010-07-23
If you wish to use ubuntuone or test it, then the fix is to wait for the update which should be available shortly.

I happen to think it works very well for what it's best at - filesharing, and can be a useful thing in that regard.

---

### Post by cariboo on 2010-07-23
This doesn't happen running UNE for me. 

On my desktop installs, I usually open chromium first, stop it starting automagically isn't a bother, I just close the ubuntuone tab, I never even see it.

---

### Post by 23meg on 2010-07-23
> **zika said:**
> If anyone had the idea how to turn off this keyring pop-up, that I have now, asking me for the password, at every boot, I would be grateful.
I'll be off-line next ~30 days, so do not be angry on the absence of my answer to the possible solution...

That sounds off-topic, and [a thread]("http://ubuntuforums.org/showthread.php?t=1533830") was started asking the same question very recently.

---

### Post by mc4man on 2010-07-23
Well it's been patched to negate the unintended behaviour so if one leave it installed or re-install in maverick it should be fine now.

(if you were using it then there was no issue to begin with and the patch doesn't seem to have had any ill effect.

---

### Post by VMC on 2010-07-23
> **23meg said:**
> That sounds off-topic, and [a thread]("http://ubuntuforums.org/showthread.php?t=1533830") was started asking the same question very recently.

LOL. Your right ,and embarrassingly I responded to his post as though he was asking about the Ubuntu One popping up?!

---

### Post by kansasnoob on 2010-07-23
For what it's worth I think I kind of understand where "Ranch Hand" is coming from. Many things that one might generally consider "options" are now installed by default.

And many of those things don't quite work as one might expect ;) Particularly Ubuntu-one :(

Should you "try" it the process of "disabling" it is certainly less than intuitive and simply purging it altogether seems to be the only way to truly clear the kind of errors you might encounter after trying it out.

Right now I've been too busy to participate much but I plan this fall on pursuing a "Pure Gnome" version of Ubuntu to get away from some of the eye candy and bling that turns some of us off.

Something more like Debian, but with the newness of Ubuntu. I think it should be fairly simple, and maybe fun :D

---

### Post by 23meg on 2010-07-23
> **kansasnoob said:**
> 
Right now I've been too busy to participate much but I plan this fall on pursuing a "Pure Gnome" version of Ubuntu to get away from some of the eye candy and bling that turns some of us off.

Something more like Debian, but with the newness of Ubuntu. I think it should be fairly simple, and maybe fun :D

Try installing the [gnome-stracciatella-session]("apt://gnome-stracciatella-session") package, and selecting "GNOME (without Ubuntu specific components)" as your session in GDM.

---

### Post by ktp on 2010-07-23
> **23meg said:**
> That sounds off-topic, and [a thread]("http://ubuntuforums.org/showthread.php?t=1533830") was started asking the same question very recently.

maybe i am being to picky, but the question asked was related to this thread (see very first post).

---

### Post by MarkieB on 2010-08-02
no longer participating in ubuntuforums.org

---

