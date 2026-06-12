---
title: "Answer: Scanning for channels with HDHomerun in 9.10"
date: 2009-11-29
forum: Mythbuntu
---

### Post by Flecko on 2009-11-29
I am only posting this so that anyone that is having similar problems can find a resolution.

I just did a fresh install of 9.10 on my DVR with an HDHomerun attached, tuning over-the-air stations, and had one heck of a time getting it to scan and find all my channels. I don't know for sure if the channel scanning was drastically changed between 9.04 and 9.10 or not, but it sure as hell didn't work as nicely as it used to. Kept popping up confusing questions, rather than just taking care of adding all the channels.

My symptom is that it just wouldn't find all the channels on one scan. And it would find MPEG channels(??) available. Each time I ran a full scan, I'd get a different partial list of all the channels I'd normally have available to me. Keep in mind, all was working well when I had 9.04 and earlier installed.

So here we go:
1. First, install hdhomerun_config. 
2. Run hdhomerun_config scan 0 and save the results to a file.
3. Look through the file for all the channels it found, and for each one, write down the transport frequency, and the us-bcast number it finds. These will be important later. And be warned, this takes a few minutes.
4. Run the MythTV backend setup program and navigate to the channel editor.
5. Delete any channels you might have, and then run a scan-for-channels. The trick here is, don't run a full scan. Arrow left once, and just scan by individual channel. (See NOTE below about transport frequencies.)
6. Goto the list of channels you wrote down, and start with the first us-bcast number (in MythTV Backend Setup it will say something like ATSC XX...its the same number) and then run the scan.
7. Each time you run the scan, it will complain that you have unused channels, say ignore them, add the new channel(s) it finds, and don't remove unused transports. And be sure that if there are conflicts to manually fix them when asked. 
8. Repeat until all your channels are added, then manually tweak the icons and so on until you're happy.

NOTE: The reason for marking down the transport numbers from the hdhomerun scan is so that if the transport list available to you in MythTV Backend Setup Channel Editor doesn't have all your transport numbers, you can add them manually.

To me, this is a simply awful situation in 9.10 and would be a show-stopper if I was in charge. I mean, I know not everyone usese an HDHomerun or watches OTA broadcasts, but its downright worthless. I spent the better part of 4 hours fixing my setup.

I know my steps weren't down to the tiniest detail, but hopefully it helps someone avoid a timesink like I did.
Best of luck everyone!
-Flecko
7)

---

### Post by cyberqat on 2009-12-04
Is there a better answer for this yet?  i am having the same issues.

"HD HomeRun not supported" should REALLY be listed as a "known defect" on the 9.10 page.  This bug makes my HDHR pretty useless.  I'm dead in the water until this problem is fixed.

---

### Post by meyoda on 2009-12-07
As sad as it is, I am on the same boat.  I wish Silicon Dust come up with the fix soon.  I will post the issue on their site as well.

---

### Post by Flecko on 2009-12-07
Even sadder, its not silicon dust's fault. Their hdhomerun_config utility finds all of my channels just fine. This is a problem with MythTV, as it doesn't seem to parse the scan correctly.

Don't go blaming Silicon Dust. I love my HDHomerun.

---

### Post by BoostFab on 2009-12-09
Thank you for sharing the work-around info. I kept hitting the brick wall trying to configure MythBunty 9.10 with the HDHomerun. This is helpful until the fix is permanent.

---

### Post by Flecko on 2009-12-09
Glad that I could help someone at least.

And not to hijack my own thread, but I've decided to move back to 9.04. I'm having stability and memory leak issues on my frontend, and all the headache just isn't worth it, for basically no new features. I'll wait until 10.04 before I try to upgrade again.

What a nightmare 9.10 has been.

---

### Post by cyberqat on 2009-12-19
Thanks for the advice, I might try 9.04 myself.

---

