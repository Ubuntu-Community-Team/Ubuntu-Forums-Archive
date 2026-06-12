---
title: "cannot find xserver-xorg-driver-ati"
date: 2010-10-03
forum: Multimedia Software
---

### Post by jgw on 2010-10-03
I am trying to following directions in Radeon_9200/9250_(RV280)_and_DVI Ubuntu documentation.  I am failing.  I requires the recomilation of the xorg driver.  It begins with:
$ sudo apt-get install build-essential fakeroot
$ sudo apt-get build-dep xserver-xorg-driver-ati

The first works fine but the second:
don@don-desktop:~$ sudo apt-get build-dep xserver-xorg-driver-ati
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to find a source package for xserver-xorg-driver-ati

So I did:
don@don-desktop:~/Build$ apt-get source xserver-xorg-driver-ati
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to find a source package for xserver-xorg-driver-ati

Then I went to synaptic - no such thing.
Then I searched the forum - no luck.

Thoughts?

---

### Post by Claus7 on 2010-10-03
Hello,

just a simple one: why don't you open synaptic and find the packages from there? Also do we know that these packages have the same name to all the versions of ubu? Just a query...

EDIT: to maverick it is xserver-xorg-*video*-ati ...

Regards!

---

### Post by jgw on 2010-10-03
I did goto synaptic.  No such package.  The closest was for an s3 board which is no fit at all.

I should probably add that I have installed all packages, from synaptic, that start with xserver-xorg except two that will not apply (radeon r6 & 7 I think)

Thanks for the reply!

---

### Post by Claus7 on 2010-10-04
Hello,

give us please the version of your ubu machine. That way we will be able to verify the packages in question and if something is missing. I guess that the radeon package is the one you want, yet we will see. 

Regards!

---

### Post by jgw on 2010-10-04
Sorry, should have sent that off the bat.  Anyway, its 10.04, 32 bit, installed the week before last and kept updated.

Thanks for the response!

---

### Post by Claus7 on 2010-10-04
Hello,

then there:
[http://packages.ubuntu.com/lucid/x11/](http://packages.ubuntu.com/lucid/x11/)

you will find all the packages having to do with xserver.

Notice once again that there is no package having the string driver! Are you sure that in the search box you are typing the correct string of characters concerning the name of what you are looking for?

If affirmative then something is missing...

You do not have to thank,
glad if I will be able to give a hand.

Regards!

---

### Post by jgw on 2010-10-07
First, thanks may not be necessary but, I think, deserved AND good manners.  Now, second, I seriously screwed up - I did NOT ready my screen!  At the very top of the referenced documentation I now find the following:
Prerequisites

This HOWTO was written for Edgy. The problem still exists in Feisty, however the name of the package has changed. Please change every instance of "xserver-xorg-driver-ati" with "xserver-xorg-video-ati" for this to work on Feisty.

I have been looking for the WRONG damned thing!  Its pretty hard to help the lame (me).  I have been gone for  a couple of days but tomorrow I am going to make another run at this thing!

Hopefully the documentation remains current and will apply to 10.04

My apologies and thanks!!

I have now taken a look.  It is installed.  The debug info was not.  I am going to install the debug stuff and reinstall the package and then I will be able to see where I am at.

---

### Post by Claus7 on 2010-10-07
Hello,

I think that I have come across the thread you are mentioning about (at least this is what I get).

Sometimes, because things evolve, old tricks stop functioning.

It is easy to get the wrong impression especially in cases where you look desperately for an answer cause you know that something is supposed to work, yet not working for some unknown reason.

I repeat that I'm glad if I can provide any help. 

Concerning your issue hope you will be able to find the best solution. If not, me or someone else will hopefully be able to give some advice. If you will be able to solve it entirely, do not forget to post what went wrong and what you did to solve it. This might help others as well even if the whole thing sounds trivial (which links you found helpful, what went wrong, what you did to solve the problem).

Regards!

---

### Post by jgw on 2010-10-08
I have up on this one and simply reinstalled the system.  The system recognized the board and the board works perfectly.  I suspect I had things so screwed up that it was unlikely that I could bail out.

I appreciate all the help I was offered.

---

