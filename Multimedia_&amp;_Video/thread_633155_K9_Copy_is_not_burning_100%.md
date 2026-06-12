---
title: "K9 Copy is not burning 100%"
date: 2007-12-06
forum: Multimedia &amp; Video
---

### Post by CHFFriday on 2007-12-06
I’m using K9Copy to copy DVDs. 

The problem is: K9 ask for a Blank DVD disk then starts the burning process and burns to 99% then reports that the process is “finished”. I can view the finished DVD on my PC but not in ANY DVD burner. I’m sure this is caused by the 99% factor.

I tried to change the size of the DVD file in the Setting but this does not change the 99% problem. 

I believe the size of the DVD file that is created by K9 during the Ripping process is too large to burn to the New Blank DVD. I have not tried the procedure to make an ISO file then burn from the ISO file as I did not have to use this procedure before upgrading to Gusty.

What is causing this?

CHFFriday

---

### Post by ryanVickers on 2007-12-06
I would first just use k9copy to rip to and iso, and then burn it with K3B.  Then, make sure f the disk size is over 4.4GiB that your using DL DVD's

---

### Post by CHFFriday on 2007-12-06
RyanVickers,
Thanks for the quick reply!

I understand what you have stated. What I don't understand is why K9 is doing this now after an upgrade? It was perfect before the upgrade and I'm using the same DVDs. Ripping and burning!

Also this same problem is on NEW installs of Gusty.

Anymore ideas?

CHFFriday

---

### Post by ryanVickers on 2007-12-06
I have had been having some major problems as well with k9copy lately, like, it would not do anything, or even start some times, but I thought that was just because I didn't have the proper libraries and codecs in, but I haven't tested it since I added them in...

---

### Post by CHFFriday on 2007-12-10
OK I will post my own reply. This is NOT a bump!

Here is what I have done this week. I built a new PC with a 40 Gig hard drive thinking that my problems may have been caused by the lack of drive space. Installed Gusty. Did all the updates. Installed all the Codecs.
Install DVD95, K9Copy and K3B.

Here is the Result:

Ripped a Test DL DVD movie using DVD95 to a ISO file. Burned the ISO file using K3B. This Test dvd would Play in all the PCs (5) that I tested it in BUT was very slow to load and start in the home DVD players (2) I tested.

Ripped and made a test DVD using K9Copy. Also played in all the PCs BUT would not play in any of the home DVD players. In fact I had trouble getting the DVD out of the home DVD Players. 

The same DVD movie I used for the test was used in Windows XP to make a DVD and this played just fine in all!

I'm not an expert at this and I don't no why I'm really doing this other than the challenge.I have to many co-harts telling me Linux is dead 
! Don't wast you time on it!

If anyone has been successfull at doing this using just Linux software, let me know how you have done it.

CHFFriday

---

### Post by yabbies on 2007-12-10
dvd shrink and dvd decrypter under wine work just fine
unless you are looking for only open source

vobcopy will rip your entire dvd directory giving you the audio_ts and video_ts folders then you can shrink it with k9 or dvd::rip or whatever you are using

---

### Post by CHFFriday on 2007-12-10
Yabbies,
Thanks for the reply.

So let me understand this DVD shrink and DVD Decrypter break the DL and crack the copy protection. Then makes an ISO? This is run in Wine as these are Windows programs. This ISO will then be Burned by K3b or K9Copy. Then it's not the burning process that is causing the problem.

So something is not right with what I'm using now! What is strange is the fact that I can view the movie with PCs but not with desktop DVD players. 

I wounder if something else is going on?

CHFFriday

---

### Post by yabbies on 2007-12-10
I have only used dvd decrypter and dvd shrink to backup my dvds
I find that it's extremely fast and I have never had a problem

I have fiddled with dvd::rip, k9, DeVeDe but have found that none of these are as easy to use as shrink and decrypter.

my process of backing up a dvd
I use decrpter to rip the dvd to my hard drive it makes the dvd directory with audio and video.
I then use shrink to make a 4.4g iso
and then use decrpter to burn.

I have used k3b to burn the iso and it always works fine.

I am currently at work but when I get home tonight I will see if I can rip a dvd using only open source software and tell you how I get it to work.
Since I have never had a problem with wine, shrink or decrypter I have never had to use anything else.

I am always up for a new challenge so I will keep you posted.

---

### Post by CHFFriday on 2007-12-10
yabbies,

Thanks for the help! From what I have read, I think the problem is there are no really good Linux Decrpter programs out there. Libdvdcss2 is good for viewing but does not help when ripping. So the only way to get the job done on NEW DL DVD movies using Linux is to do as you have been doing!

The Windows program called Anydvd is the best and from what I can tell is produced in China and if so they really do not care what the movie companies around the world are doing to prevent ripping! Anydvd will NOT work in Wine. Check it out.

Hpe to get back to you,
CHFFriday

---

### Post by CHFFriday on 2007-12-11
yabbies,

Found this link. Very interesting.

[http://ubuntuforums.org/showthread.php?t=387009&highlight=dvd](http://ubuntuforums.org/showthread.php?t=387009&highlight=dvd)

CHFFriday

---

### Post by yabbies on 2007-12-13
CHF
I haven't had time to look into this
We were hit by a huge ice storm and I have been without power or communications at home.
We are finally back to normal at work
although I finally have electrical service restored at home I have no communications

When I lost power I was using vobcopy to backup a copy of Death Proof that I have.
I know that vobcopy is very slow and takes about 4 hours to copy a full dvd, I will restart the process tonight(if I still have electricity) keep fingers crossed.

---

### Post by mc4man on 2007-12-13
Unless your iso is slightly oversized (which you've stated as addressed) then your compatibility issues with standalones is probably not related to k9. As posted previously in this thread it's better not to burn directly from k9, let it create the iso then burn with whatever prog. you wish. Due to old habits and because i think it's the best burning app I use Imgburn thru wine. As a test i used k9 to rip,process, and create an iso from 3 popular new titles and used the built in cd/dvd creator to burn. Came out absolutely fine with no standalone(3 different models) issues.
As far sizing 4.4gb may or may not be to big, k9 is fairly accurate, I would leave it a the default 4400mb and certainly not over 4460mb. For example an iso I made was listed as 4.4gb - 4712613888 bytes - this is about 11.5mb to large. I wouldn't exceed 4661411840 or so - about 30mb shy of capacity. There's no image quality to be gained by pushing to the edge and there is overhead needed for dvd rom files.
As far as vobcopy I use it for most rips and find it to be very fast for titles with no structure protection and with slight modifying very efficient on reading/ripping titles with s.p. While I was typing this I did deathproof - 11.5 min.  (can't type for sxxx)

---

### Post by CHFFriday on 2007-12-14
All you guys, a BIG thanks for responding!

Since I have taken on this project I have done allot of research on how DVD movies with copy protection interact with DVD players and Computer DVD players. It is very high technology and most of it is over my head but is very interesting! 

From what I understand and I can be wrong on this, to make a backup copy of your DVD movies the software you use needs to remove all the copy protection schemes and make sure the Region code is the correct one for your Region. This statement is very simplistic! 
This process is NOT very easy and should not be. The software we use is what makes it look easy.

That being said, if the software can do all the above and then Rip the DVD to the hard drive in the form of an ISO file no matter what the size is, then we are one step closer to our goal. Size doesn’t matter as long as in the next step the Burning software can compress the ISO to the correct size. Quality can suffer in this process.

Now for the Linux question. Why are there so many deferent RESULTS from all the different posters on this form and other forms I have visited and they are using the same software and procedures?

I also know that this is a taboo subject and NO software coder is going to post anything on this subject.

SO with all this in mine, my quest is completed! I gave myself three weeks to work on this and to learn. Believe me I have learned! If I need to make a copy of a DVD movie of use on Vacation or something like that, I will fire up a Windows box and use AnyDVD to do the job.

Again, thanks to ALL who have replied to this post.

CHFFriday

---

### Post by CHFFriday on 2007-12-18
Just wanted to add a bit of info to this post. At work I ask a friend of mine if he would try to play one of my copied DVDs. He came back to me and said it played perfect. No problems. WOW what a surprise! So I check into the specs of the stand alone players I used and found the warnings about what they would not play. One of the types of DVD disks that would not play in these players was where the Region code was NOT present on the DVD disk. Other wise Region Free. His player is an older one.

So I check this DVD with AnyDVD to see what the region code was and found that there was none. During the de-encryption the Region code was removed. So I though that this is my problem. Just for fun I decided I would check a different copied DVD that works in  my players for a Region code. BOO! This DVD also had no Region code. But I still think this may have something to do with it.

I was wondering if anyone knows how to get ANY of the DVD rippers to insert or keep the region code in during de-encryption? Is this a function of libdvdcss2?

CHFFriday

---

