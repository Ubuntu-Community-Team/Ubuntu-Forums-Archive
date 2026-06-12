---
title: "(another) hvr 1600 issue on 9.10"
date: 2009-12-15
forum: Mythbuntu
---

### Post by wesxohio on 2009-12-15
I have a hvr 1600 that has been laying around unused. Decided to put Mythbuntu on my dell dimension 3000 

I went through the mythtv hvr 1600 wiki and did everything it said but using the regular cable coax input I am only getting channels 2-9. I had this working with the programs that came with my tuner on windows but no luck on mythbuntu so far.

The only out of the ordinary thing I noticed was that my signal stays at 0%. Has anyone else had this problem and hopefully a resolution to this problem?

---

### Post by evil_queen_lisa on 2009-12-15
having a similar issue.. trying to install a 1600 on mythbuntu clean install. No luck. Signal strength stays 0%, channel scans get to 5% then freeze and go no further.
Someone please help!
(My 1600 also works in windows, and kinda works in Ubuntu MythTV - It has poor quality video, which is why i decided to try mythbuntu :S)
Thanks for the help anyone!!
*EQL*

---

### Post by nickrout on 2009-12-15
> **evil_queen_lisa said:**
> having a similar issue.. trying to install a 1600 on mythbuntu clean install. No luck. Signal strength stays 0%, channel scans get to 5% then freeze and go no further.
Someone please help!
(My 1600 also works in windows, and kinda works in Ubuntu MythTV - It has poor quality video, which is why i decided to try mythbuntu :S)
Thanks for the help anyone!!
*EQL*

mythbuntu IS ubuntu mythtv. Same packages.

---

### Post by evil_queen_lisa on 2009-12-15
> **nickrout said:**
> mythbuntu IS ubuntu mythtv. Same packages.
well.. i thought i'd try since i only use Ubuntu for MythTV (or would LIKE to anyway :S)
thanks,
*EQL*

---

### Post by wesxohio on 2009-12-16
PROBLEM SOLVED!

Messing around with it a little after the post I clicked the back button when it got held up at 5% then I accidentally clicked to search channels again. Realizing it picked up more channels that time I did that over and over again till it got to the 80 something channels I normally pick up. 

I hope this works for other people 

I'm going to email this to you as well lisa just encase you don't look at this post

---

### Post by evil_queen_lisa on 2009-12-16
> **wesxohio said:**
> PROBLEM SOLVED!

Messing around with it a little after the post I clicked the back button when it got held up at 5% then I accidentally clicked to search channels again. Realizing it picked up more channels that time I did that over and over again till it got to the 80 something channels I normally pick up. 

I hope this works for other people 

I'm going to email this to you as well lisa just encase you don't look at this post


sweeet! thanks a lot.. how long did it take you to get the scan to reach 100%?? is everything working well now? hows the quality?
Also, what scan type did you use? the only one thats been getting me anywhere is us-cable
Thanks,
*EQL*

---

### Post by brplut40 on 2009-12-16
If you are scanning the analog side of the tuner, there is a known bug is mythtv for analog channel scanning. Please see this [http://svn.mythtv.org/trac/ticket/6530](http://svn.mythtv.org/trac/ticket/6530) link for details. I had to manually rebuild my analog turners when I reinstalled.

---

### Post by wesxohio on 2009-12-17
I had to click through maybe 4 or 5 times. the quality isn't as good as my cable. it is maybe vhs quality maybe, a tad better.. have you tried it? did it work for you? I will probably also check out the bug fixes, maybe that will affect the poor quality i have?

---

### Post by evil_queen_lisa on 2009-12-20
> **brplut40 said:**
> If you are scanning the analog side of the tuner, there is a known bug is mythtv for analog channel scanning. Please see this [http://svn.mythtv.org/trac/ticket/6530](http://svn.mythtv.org/trac/ticket/6530) link for details. I had to manually rebuild my analog turners when I reinstalled.

thanks for the help, but unfortunately, I don't have a CLUE how to manually rebuild my analog tuners. This help ticket is just a bunch of jibberish to me. Any help? I'm pretty good at following step by step directions!

Thanks a lot,
*EQL*

---

### Post by matt06 on 2009-12-20
After my recordings run tonight I will check the behavior of the analog scanner on my system.

I have not needed to rescan my analog channels since upgrading to 9.10, but the digital scanner has worked fine a numbers of times.

---

### Post by evil_queen_lisa on 2009-12-20
> **matt06 said:**
> After my recordings run tonight I will check the behavior of the analog scanner on my system.

I have not needed to rescan my analog channels since upgrading to 9.10, but the digital scanner has worked fine a numbers of times.
Thanks

---

### Post by matt06 on 2009-12-21
Ok, it looks like I am seeing the same thing on my system scanning for analog channels.  It filled ch. 6/7/11/12/15 which are channels that I removed before because I don't want them in my guide.  It stopped at 15 and did nothing after that.

[[IMG]http://img121.imageshack.us/img121/9411/mythscan.th.png[/IMG]](http://img121.imageshack.us/i/mythscan.png/)

I cancelled out and didn't try scanning again as I don't want to lose my current lineup :)

---

### Post by evil_queen_lisa on 2009-12-21
> **matt06 said:**
> Ok, it looks like I am seeing the same thing on my system scanning for analog channels.  It filled ch. 6/7/11/12/15 which are channels that I removed before because I don't want them in my guide.  It stopped at 15 and did nothing after that.

[[IMG]http://img121.imageshack.us/img121/9411/mythscan.th.png[/IMG]]("http://img121.imageshack.us/i/mythscan.png/")

I cancelled out and didn't try scanning again as I don't want to lose my current lineup :)

Yep, same issue. What version of Myth were you using? Maybe i'll dl and use that version. Also, do you remember if you did anything with the drivers? People keep saying to do something with the drivers, but i dint know how.
Thanks,
*EQL*

---

### Post by matt06 on 2009-12-21
I am using Mythbuntu 9.10 [Automatic Daily builds]("http://www.mythbuntu.org/auto-builds") '-fixes' branch.  In the system info page in Myth says the version is 'branches/release-0-22-fixes (22594)'.

**EDIT: oops, the above is somewhat wrong.**  This is just a straight 9.10 backend, NO "auto builds".  The version number is correct as 'branches/release-0-22-fixes (22594)'.  Sorry, I don't know of a better way to check it.

To install the drivers for the HVR-1600, I used this [MythTV wiki page]("http://www.mythtv.org/wiki/Hauppauge_HVR-1600#Installation_Guide").  I don't think I've updated it since moving to 9.10, but my driver version is reported as 1.2.0.

> matt@mythtv:~$ dmesg | grep cx18
[   19.384191] cx18:  Start initialization, version 1.2.0
[   19.384288] cx18-0: Initializing card 0
[   19.384295] cx18-0: Autodetected Hauppauge card

---

