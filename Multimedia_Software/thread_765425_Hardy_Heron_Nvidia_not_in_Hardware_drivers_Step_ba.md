---
title: "Hardy Heron Nvidia not in Hardware drivers: Step back?"
date: 2008-04-24
forum: Multimedia Software
---

### Post by Arlanthir on 2008-04-24
EDIT: Installing DID fix the issue: Nvidia Restricted Driver popped right in after boot. :)

I'm running the release Live CD for Heron and I'm shocked to see that as with it's previous builds, it is unable to detect that I have a Nvidia Go 7400 card. Gutsy did and installed everything automatically.

Is this a step back from Gutsy? Note that I haven't yet installed Hardy (because of this!) so if it "just works" after installation, please point that out.

Basically I go to System > Administration > Hardware Drivers and I get no proprietary options for any drivers. Gutsy found two: Intel wireless and Nvidia Graphics. Now Intel works out of the box whereas Nvidia obviously does not.

I would appreciate if you would not post installation instructions (although I admire your help :)): I think I know which methods to try and it's a matter for another thread. It just pains me to see that in Gutsy everything was automagical and now suddenly I'm back to Feisty or Dapper.

Please, any thoughts on this?

(*Hopes that someone shouts "bah, just a live cd protection thingie, install and it'll work like in Gutsy"*)

---

### Post by overdrank on 2008-04-24
> **Arlanthir said:**
> I'm running the release Live CD for Heron and I'm shocked to see that as with it's previous builds, it is unable to detect that I have a Nvidia Go 7400 card. Gutsy did and installed everything automatically.

Is this a step back from Gutsy? Note that I haven't yet installed Hardy (because of this!) so if it "just works" after installation, please point that out.

Basically I go to System > Administration > Hardware Drivers and I get no proprietary options for any drivers. Gutsy found two: Intel wireless and Nvidia Graphics. Now Intel works out of the box whereas Nvidia obviously does not.

I would appreciate if you would not post installation instructions (although I admire your help :)): I think I know which methods to try and it's a matter for another thread. It just pains me to see that in Gutsy everything was automagical and now suddenly I'm back to Feisty or Dapper.

Please, any thoughts on this?

(*Hopes that someone shouts "bah, just a live cd protection thingie, install and it'll work like in Gutsy"*)

HI and I did not use the live cd for the install (alternate cd) but My onboard nvidia 6100 was detected after installation. :KS

---

### Post by Arlanthir on 2008-04-24
If you ever try the Live CD out could you post the proprietary drivers it finds? 

Thank you for the reply =)

---

### Post by whistlerspa on 2008-04-24
Yeah - I'm using the 8.04 64bit Live CD and also see no Nvidia drivers detected in the restricted drivers panel. I also have onboard 6100 driver chip set. I was going to dual boot this desktop but will hold off for now pending more info I think. 800 x 600 resolution would be hopeless if I got stuck with that, and I'm not prepared to risk an install just to see if it fixes the issue.

---

### Post by overdrank on 2008-04-24
> **Arlanthir said:**
> If you ever try the Live CD out could you post the proprietary drivers it finds? 

Thank you for the reply =)

Ok I found a copy of the beta live cd and it did not so the nvidia driver in the restricted drivers. :( But as I said after installation they did work.

---

### Post by Arlanthir on 2008-04-24
> **overdrank said:**
> Ok I found a copy of the beta live cd and it did not so the nvidia driver in the restricted drivers. :( But as I said after installation they did work.

That's a good sign, maybe I'll try that tomorrow then :) Thank you!

EDIT: As edited on the first post, restricted drivers manager picked up nvidia after install :)

---

### Post by e-mitc2h on 2009-02-14
I just got a fresh installation of Hardy Heron. I installed the NVIDIA driver I need using:

>sudo apt-get install nvidia-glx
>sudo apt-get upgrade
>sudo dpkg-reconfigure xserver-xorg

Well, the last instruction is supposed to let you pick the nvidia driver to tell X server to use it. No such option is offered to me.

I also had a look at System > Administration > Hardware Drivers, and nothing at all is listed there.

The Synaptic package manager confirms that the driver is installed, but it is still like it is not installed at all.

Any ideas?

---

