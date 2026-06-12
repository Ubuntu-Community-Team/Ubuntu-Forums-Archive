---
title: "Mythbuntu channel problems"
date: 2012-01-19
forum: Mythbuntu
---

### Post by rem48g on 2012-01-19
Hi I have a clean install of Mythbuntu 10.10 32 bit. I also have the HD Homerun prime. When I use the HD homerun Prime utility I can find the channels fine, but when I use the channel scan in Channel setup in myth backend. It scans and finds over 300 channels, but most don't have any info woth them and I cann't view on the frontend.

So I started adding channels manually and have some questions:

The std cable channels seem to work fine, but the HD channels appear like bad reception. I have the channel list from ShedulesDirect loaded on the HD Homerun prime and all looks good there. I'm not sue what I should be putting in the frequency fiend on page 3 od the channel editor (myth backend). I've tried 

the channel # i.e. 93
the channel # with feed # i.e. 93-3
the frequency in GHz i.e. 639000000

What is the preferred entry here? Channel number or frequency or both. Can someone please give me the correct format of the field.

What am I missing?

Also in the myth backend General section, should I use "US Broadcast" or "US Cable"? I've been using "US Cable"

The last thing is I tried repeatedlt yo upgarde Mythbuntu to .25 ,but it hangs on the update and it doesn't get applied.

Thanks,
-Russ

---

### Post by nickrout on 2012-01-19
There is no 0.25 released yet.

---

### Post by rem48g on 2012-01-19
I was following the directions here:

[http://www.mythbuntu.org/repos](http://www.mythbuntu.org/repos)

As I read somewhere that with the .25 MythTV backend I could setup all three of my HD Homerun Prime tuners using their ID as opposed to the IP address. What am I missing?

Thx,
-Russ

---

### Post by nickrout on 2012-01-19
> **rem48g said:**
> I was following the directions here:

[http://www.mythbuntu.org/repos](http://www.mythbuntu.org/repos)

As I read somewhere that with the .25 MythTV backend I could setup all three of my HD Homerun Prime tuners using their ID as opposed to the IP address. What am I missing?

Thx,
-Russ

The mythbuntu 0.25 repo is in fact the development code and is not release quality. Use at your own risk. Join the dev and commit mailing lists and be prepared for frequent breakage.

---

### Post by iamlindoro on 2012-01-19
> **rem48g said:**
> Hi I have a clean install of Mythbuntu 10.10 32 bit. I also have the HD Homerun prime. When I use the HD homerun Prime utility I can find the channels fine, but when I use the channel scan in Channel setup in myth backend. It scans and finds over 300 channels, but most don't have any info woth them and I cann't view on the frontend.

Your configuration steps are way off.

Start over (meaning delete your video sources COMPLETELY, don't attempt to reuse them, or your card definitions) and configure properly from scratch.

[http://www.mythtv.org/wiki/Configuring_MythTV_for_the_HDHomeRun_Prime](http://www.mythtv.org/wiki/Configuring_MythTV_for_the_HDHomeRun_Prime)

---

### Post by iamlindoro on 2012-01-19
(and of course, you must absolutely be on latest .24-fixes from the repository)

---

### Post by rem48g on 2012-01-20
Thanks, iamlindoro.

I am all set now. I tried those same directions several times, but for some reason I never was able to get it to let me select a starting channel for the HD Homerun Prime tuners. Then I read all of the stories about scanning utilities people were using and entering in the settings manually. I'm glad I didn't have to go that route. I also had a problem with the HD channels having very poor quality, but that was a separate issue. I haven't installed MythTV in a few years and there's a lot that's changed. Got my old PVR150 remote working and I'm back in business. 

Thanks again for your help!

---

