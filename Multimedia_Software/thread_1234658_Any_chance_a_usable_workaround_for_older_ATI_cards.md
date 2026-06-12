---
title: "Any chance a usable workaround for older ATI cards under Jaunty to come out ???"
date: 2009-08-08
forum: Multimedia Software
---

### Post by KaYnemO on 2009-08-08
Hey all... AFAIK no one has been able to solve the ATI older cards (mine is radeon mobility x1600) under Jaunty. I am currently under 8.10, since nothing has been done about the Jaunty. Maybe a post for all the people like me (which are true to Ubuntu, needing to upgrade to Jaunty, but not willing to give up the way their cards work under Intrepid :) )should be made sticky IF and WHEN the solution shall be reached ??

Hope someone will crack this nut -  too bad we can't stick an NVidia card in our laptops :) 

Thanks,

K

---

### Post by martinbaselier on 2009-08-08
The solution is here:
[http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue](http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue)

That is, if you prefer the ati driver. In my case the open source one works better, so I reverted the change.

---

### Post by brunolabs on 2009-08-08
My ATI Radeon X700 started working "out of the box" with 9.04.
Always had problems with the previous versions.

Give Jaunty a try.

---

### Post by KaYnemO on 2009-08-08
> **martinbaselier said:**
> The solution is here:
[http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue](http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue)

That is, if you prefer the ati driver. In my case the open source one works better, so I reverted the change.

Thanks a bunch for this solution - I think it should be made a sticky - I haven't tried it myself yet, but I will report after I make backup and upgrade to Jaunty. THX

---

### Post by ssri on 2009-08-08
After checking out the latest git version of the radeon drivers, I was pleased with its improvement over the ones released with jaunty. However, I experienced some tearing and fill problems with my ATI Mobility Radeon x2300. So, I used the tan-com link to downgrade my xserver, installed the necessary packages for the appropriate build environment, installed Catalyst 9.3 packages I built for jaunty (sh ./ati-blahblah-9.3.run --buildpkg Ubuntu/jaunty) and pinned all of the relevant packages in /etc/apt/preferences. Running jaunty and kde 4.3.0 right now. In Jaunty, Catalyst 9.3 experiences a touch more tearing when cycling through menus and windows than with the same version running on intrepid, but nothing like what was seen with the radeon drivers. Thankfully, I experienced no tearing when using googleearth or playing any videos.  Good luck!

---

