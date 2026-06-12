---
title: "Upgrade MythTV from .24 to .25 on Ubuntu 10.10"
date: 2012-05-24
forum: Mythbuntu
---

### Post by manaesh on 2012-05-24
Hi

Checking the Mythbuntu page - it looks like Ubuntu 10.10 only has repos up until .24

Is there any way I can upgrade my backend from .24 to .25 WITHOUT upgrading ubuntu?

Having got my home server nice and stable with various other appplications, I really am loath to have to rebuild everything that is based on that kernel again!

A lesson learnt though - im always going for the LTS's in future!

Can anyone help? Will mythbuntu do a repo for .25 for 10.10 if there is enough demand? I personally only installed 10:10 just over a year ago! (01/03/11)

Thanks

Mike

---

### Post by thatguruguy on 2012-05-24
> **manaesh said:**
> Hi

Checking the Mythbuntu page - it looks like Ubuntu 10.10 only has repos up until .24


That's because 10.10 is no longer supported, as of April of this year.  Is there a reason you're reluctant to upgrade to 12.04?  It will be supported for 5 years.

---

### Post by manaesh on 2012-05-24
> **thatguruguy said:**
> That's because 10.10 is no longer supported, as of April of this year.  Is there a reason you're reluctant to upgrade to 12.04?  It will be supported for 5 years.

Hi

Yes - I have just got everything working correctly, asterisk complied, the box also hosts Homeautomation and network reporting, and to redo it all again will be a pain.

Also - it is now a "production" system for the family, any downtime has serious implications for the WAF!

A quick upgrade of just mythtv will be alot easier to get past the Wife, but a whole upgrade to 12:04 means serious downtime - and serious personal time to invest, which I dont have at the moment due to a new daughter....

I just though that there might be people in a simliar situation with 10.10 - and if anyone had any ideas on how to go about doing it...

Mike

---

### Post by klc5555 on 2012-05-24
Ubuntu tends to make this type of activity much more difficult than other distros do, which was one reason I ended up just using it on frontend machines, while keeping backends on distros that were more conducive to upgrading the OS and upgrading application/utility suites like Mythtv on separate timetables.

Since you can't use the later binaries for Mythtv because of a myriad of unsolvable dependency issues, your choices would seem to be to try to compile 0.25 yourself, and if successful (a _very_ big if on your Ubuntu version), back up your database, uninstall the Mythtv 0.24 binaries (but not MySQL!), install your compiled 0.25, and run mythbackend whereupon it should update the database.

Or, more reasonably, stand pat on Mythtv 0.24 until you have some real compelling reasons to upgrade the other aspects of your multipurpose server to Ubuntu 12.04, or are ready to move to new hardware. After all, it's not like your Mythtv 0.24.2 stopped functioning when 0.25 came out, and the changes in 0.25 by themselves (even if there were no bugs) are unlikely to be worth nuking a highly-tweaked production server for.

---

### Post by tgm4883 on 2012-05-24
We aren't going to build 0.25 for 10.10, the demand just isn't there and it's unsupported. We do make our build scripts available so you can build it yourself for 10.10. I don't guarantee it will build though. Take a look at [http://mythbuntu.org/wiki/developer-cheatsheet#Building](http://mythbuntu.org/wiki/developer-cheatsheet#Building)

---

### Post by manaesh on 2012-05-25
Hi all

Thanks for all the replies - as stated - i dont need to upgrade to the latest version - so might just leave it for a bit, and migrate over as and when.

That said - if Mythbuntu does feel like doing the repos for 10.10 - id be overjoyed and make a donation for the time spent!

Cheers

Mike

---

