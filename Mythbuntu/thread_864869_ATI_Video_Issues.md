---
title: "ATI Video Issues"
date: 2008-07-20
forum: Mythbuntu
---

### Post by dsbw on 2008-07-20
OK, my ATI Radeon 1200 issues are making me cuckoo, but I think I have a valuable clue.

If I use any ATI driver but the Mythbuntu default, what happens is that the MythTV interface comes up scrambled. The character of the scrambling depends on the resolution I select. 

So, if I select one resolution, I get half an image on the right, and half on the left. (Every other line, not like top half and bottom half or, heh, right half and left half.) Usually I get a diagonal hash, like:

mythtvmythtv
ythtvmythtvm
thtvmythtvmy
htvmythtvmyt

The actual hash severity depends on resolution, as I say. Regular Ubuntu desktop, VLC, etc. looks fine.

Help?

---

### Post by netslacker on 2008-07-23
change your de-interlacer from bob to something else.

---

### Post by tai1spin on 2008-07-23
Netslacker can you elaborate? I have the same exact problem if I use my native desktop resolution of 1440x900. If I use anything less, I have no problems. 

How do I change the de-interlacer??

---

### Post by netslacker on 2008-07-24
Sorry guys, I didn't mean to get your hopes up... I miss-read the original post to be while playing video and having the garbled screen which the bob de-interlacer produced similar problems for me and was easily remedied by changing the de-interlacer.  But, for me, this was only while watching TV or a recorded program.  If it is the Myth GUI you are having trouble with then I'm not sure I have a suggestion.

Since I have an ATI HD 3200 that I struggled with for several weeks I have encountered just about every issue related to ATI video cards and drivers.  Unfortunately, my resolution came when I decided to abandon ATI and go nVidia just to get decent drivers and my sanity back.  There are a lot of threads on here that talk about the struggles with ATI video cards and drivers and the Bob de-interlacer was one thing that proved to always be an issue.  The de-interlacer is selected when you select the playback profile (cpu++/normal/cpu--/etc).  While on that screen you can edit one of the rules (takes you to a different screen) there you will see the deinterlacer associated with that rule.  You may find it easier just to change the playback profile rather than the individual deinterlacers, try cpu-- then work your way up.

If you continue to struggle with ATI then I suggest you just get a cheap nVidia 7200 or 7300 for ~22.00 from newegg and call it good.  I went this route and was up and running without a problem in 5 mins and all of my previous ATI struggles vanished.  For the 22.00 of a new nVidia card, ATI is not worth the hassle....

---

### Post by SiHa on 2008-07-25
After two weeks of trying to get my on-board ATI X1200 to play ball (I had the exact symptoms you describe). I gave up, bought an old nVidia7200 off eBay for £5.

One clean install of Hardy + Mythtv later (30 mins) I have a perfectly working BE/FE mythbox.

ATI + Linux = ](*,)

Now all I've got to do is figure out how to get composite out of this darned 9-pin S-Video connector! :(

---

### Post by sjitan on 2008-07-28
Has anyone figured out this problem yet.
I can't add a new video card for I have a htpc case that has no space for a card and must use the onboard video of my Asus M2A-VM which has the X1200 family card.
If anyone can point me in the right direction I'd be must appreciated. (Other than ofcourse buy a new motherboard or case )

---

### Post by dsbw on 2008-07-29
Still no solution, sorry.

---

### Post by steg on 2008-10-06
I've also got this exact same problem. 

If myth "automatically" fits to screen or if I set the gui to output at a certain resolution, the gui gets scrambled.

It only occurred after installing Catalyst (both 8.8 and 8.9).

I've got a Gigabyte 780g chipset mobo with a Radeon HD3200 in built - I needed Catalyst to get HDMI audio to work.

If I manually override the gui screensize to +1 the actual screensize & make my tv out the same size as gui, it works correctly

e.g. 720x568 -> 721x568

However, this means I cannot have different resolutions (i.e. no HDTV)

Anyone managed to sort this? It *only* happens in myth!

---

### Post by dsbw on 2008-10-07
I got the interface working briefly, not sure how. I never could resolve the other, performance-related problems, like DVD tearing.

---

### Post by JugeHuge on 2008-10-07
> **steg said:**
> 
It only occurred after installing Catalyst (both 8.8 and 8.9).


I'm currently using repository driver because i have found it currently best. Catalyst 8.6-9 have been causing problems on myth at least on my system. Waiting 8.10 drivers if those would work. :)
 
> **steg said:**
> 
I've got a Gigabyte 780g chipset mobo with a Radeon HD3200 in built - I needed Catalyst to get HDMI audio to work.

I have Asus M3A78-EMH HDMI with 780G chipset and i didn't need catalyst drivers to get HDMI audio work.
Here is what i used to get HDMI audio working: [No sound over HDMI with ga-ma78gm-s2h AMD 780G motherboard]("http://www.gossamer-threads.com/lists/mythtv/users/333112#333112")

---

### Post by EnGorDiaz on 2008-10-07
> **SiHa said:**
> After two weeks of trying to get my on-board ATI X1200 to play ball (I had the exact symptoms you describe). I gave up, bought an old nVidia7200 off eBay for £5.

One clean install of Hardy + Mythtv later (30 mins) I have a perfectly working BE/FE mythbox.

ATI + Linux = ](*,)

Now all I've got to do is figure out how to get composite out of this darned 9-pin S-Video connector! :(


ATI 512 card = ftw!!!

---

### Post by steg on 2008-10-07
> **JugeHuge said:**
> I'm currently using repository driver because i have found it currently best. Catalyst 8.6-9 have been causing problems on myth at least on my system. Waiting 8.10 drivers if those would work. :)
 

I have Asus M3A78-EMH HDMI with 780G chipset and i didn't need catalyst drivers to get HDMI audio work.
Here is what i used to get HDMI audio working: [No sound over HDMI with ga-ma78gm-s2h AMD 780G motherboard]("http://www.gossamer-threads.com/lists/mythtv/users/333112#333112")

Hmm, I don't hold out too much hope for 8.10 if the problems been around since 8.6! I had a bit more of a play last night & it really is v. odd.

When myth starts the screen is scrambled. But if I go into Appearance and change something (anything) on the screensize screen (2nd page? -> e.g. Paint method). Then the change seems to work until myth is restarted. 

Also if I use Catalyst to increase the screen size (e.g. 800x600) and then start myth & then decrease the screen size it works until myth is restarted.

OpenGL instead of QT seems to work (scrambled in init but then ok) but I get the dreaded oversize problem on restart & the menu changes seem a bit laggy.

Using the above workaround also seems to increase the likelihood of a segfault when exiting tv playback.

Thanks for the HD audio suggestion but I think I will stick with +1 pixel & audio working without a asound.conf for now. If 8.10 is the let down I'm expecting I may change my mind.

---

