---
title: "No &quot;Import DVD&quot; Option"
date: 2010-12-18
forum: Mythbuntu
---

### Post by korgman on 2010-12-18
It used to be there, but its gone.  I haven't tried to rip a DVD in months, but tonight i went to do it and the option is not there.  Does anyone have a suggestion?

---

### Post by chaanakya_chiraag on 2010-12-18
You could try Thoggen.  If you wanna go CLI, you can try using dd if=/dev/cdrom of=~/dvd.iso

---

### Post by williammanda on 2010-12-18
What is the long range status of ripping DVD's in Mythtv?

---

### Post by korgman on 2010-12-18
Yeah, I could do it another way.  that's not the problem.  I'm just wondering where the option went.  Its a conveinience thing.

---

### Post by thatguruguy on 2010-12-18
According to the [mythtv wiki]("http://www.mythtv.org/wiki/DVD_Ripping"), DVD ripping has been removed from .24.  I assume that it will be returned for .25, if the issue concerning storage groups is worked out.

---

### Post by benlyboy on 2010-12-19
Hi all

I just realised that dvd import was now missing and found this thread.

Does this main we can't store and watch videos on myth, or is there some other way to rip them and then have myth view them...?

thanks

---

### Post by thatguruguy on 2010-12-19
Yes, just rip the dvd using your favorite ripping software (I use handbrake), and store the resulting video in whichever directory you have set in your storage groups for videos.

---

### Post by klc5555 on 2010-12-20
> **thatguruguy said:**
> According to the [mythtv wiki]("http://www.mythtv.org/wiki/DVD_Ripping"), DVD ripping has been removed from .24.  I assume that it will be returned for .25, if the issue concerning storage groups is worked out.

Don't rely too heavily on that assumption. As of 18 Nov. the original plan to rewrite the DVD rip UI, with  mtd replaced in whole or in part by the job queue in version .25 or .26 is called "very shaky" over in the talk section of the mythtv wiki [http://www.mythtv.org/wiki/Talk:MTD](http://www.mythtv.org/wiki/Talk:MTD) where it is also stated that regarding the return of DVD ripping support: "There are no plans, just an interest."

Until and unless this return of DVD rip support happens, the recommendations at the wiki are to use Handbrake or VOBcopy.  ...or (I suppose) to stay on 0.23 or earlier.

---

### Post by thatguruguy on 2010-12-20
I'm OK with that.

---

