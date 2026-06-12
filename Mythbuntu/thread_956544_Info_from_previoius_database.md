---
title: "Info from previoius database"
date: 2008-10-23
forum: Mythbuntu
---

### Post by dardack on 2008-10-23
So I have decided to migrate away from Knoppmyth and check out mythbuntu.  One with the past 2 version of knoppmyth i could never get VNC to work even though I did everything that people say should make it work.  SO i was still using an old version of knoppmyth.  As it was I had to manually update mythtv to use schedules direct.  So this has prompted me to test out mythbuntu, and when I found an AppleTV on clearance new for $160.00 it made up my mind.  SO i put my original BE/FE box in basement and made the AppleTV my frontend, both are now running Mythbuntu.  I

 did backup my old database, and following the mythtv instructions pulled in all the old recording data, however, I can't remember my recording profiles settings (like the amount of space used per hour, it's not called that i know, it's like minimum maximum setting, sorry away on business and can't look at it) and now the newly recorded shows don't look as nice as before I think.  (Also, even though I have selected use XV video settings in the setup, nothing happens when I hit F except bringing up change volume, been using nvidia-settings manually, if anyone has a good static picture that I could  use to set up the colors better, that'd be great also), anyways that was a bit OT, but is there anyway to extract the recording profile data from my backup, and import it into my current database?

Thanks for any help, unfortunately away on business and MythWeb doesn't work, should of tested that before leaving I guess.  Says something about:

 Database Access Denied

You are most likely receiving this message because you
have failed to configure mythweb's database login info.

Please see INSTALL for instructions.

I know i set this up in MCC and such, I did change the mythtv database password, because I kept getting user error, so I just made it mythtv like the default (should I change this?) but do I have to change this somewhere for mythweb also?

Sorry for the multiple questions in one post.

---

### Post by uopjohnson on 2008-10-23
You need to change the DB password on the backend in /etc/mythtv/mysql.txt.  
Most of the playback options are frontend specific and it would probably be more trouble than its worth to extract them and use them on your new frontend.  
The reccording profile info is in min/max bitrate.  I haven't played with this much, maybe someone else can give optimal settings.  It does depend on your capture device so you may want to include that.

---

### Post by dardack on 2008-10-23
2 hauppauge pvr-250's and 1 pvr-500.

I thought I had changed the backend as well as the front end, but will have to check.

---

### Post by uopjohnson on 2008-10-23
The only change I ever made on my 250's was to make sure it was recording at 720x480.

---

### Post by dardack on 2008-10-23
> **uopjohnson said:**
> The only change I ever made on my 250's was to make sure it was recording at 720x480.

Yea I did that.  I think i used to get like 2.5gigs per hour,  now it's like 2 even, so I guess i'll just increase it until i find it better.

Again, does anyone have a good test picture to get colors correct on?

---

### Post by newlinux on 2008-10-23
In addition to setting it to 720x480, I also changed the codec to dvd-special 2 I believe, which improved the picture on my 150.

---

### Post by dardack on 2008-10-24
> **newlinux said:**
> In addition to setting it to 720x480, I also changed the codec to dvd-special 2 I believe, which improved the picture on my 150.

Um, i don't know if I've ever in my 4-5 years of using mythtv changed the recording codec, didn't know you could, where is this located?

---

### Post by newlinux on 2008-10-24
it's in the recording profiles, I think the stream type setting. I think it defaults to MPEG TS or MPEG PS, but I found it better on DVD Special 1 and DVD Special 2. MS MCE uses DVD Special 2 with this card.

---

