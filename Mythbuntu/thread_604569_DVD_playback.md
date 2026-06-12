---
title: "DVD playback"
date: 2007-11-06
forum: Mythbuntu
---

### Post by ghostwalker50 on 2007-11-06
I guys. the dvd playback is working kinda. it will play the intro of the movie. but not the movie it self. is their a way i can reconfig it to just bring my to the dvd menu. so i can chouse to play the movie or the extras.

thanks
Fernando :)

---

### Post by tgm4883 on 2007-11-06
Did you install the necessary codecs from MCC?

---

### Post by ghostwalker50 on 2007-11-07
Frist - What codex do i need to install. 
next - it plays the intro for the dvd so it is working as a dvd player. but it is configed to jst start play chapter 1 and that is a  intro. how can i just config it to bring me to the menu. 

thanks

---

### Post by superm1 on 2007-11-07
Open up mythbuntu control centre and choose the proprietary codecs tab like tgm said.

There is a button for DVD support.

---

### Post by road2elysium on 2007-11-18
I'm having similar issues.  I've been mostly ripping DVDs into isos and watching them via MythVideo.  However, I have enabled the libdvdcss2 and the other proprietary codecs from the Mythbuntu Control Center, and am only able to view the introduction screens to the DVD I used for testing -- "Thank you for smoking".

---

### Post by spinlock99 on 2007-11-23
I've got a simmilar situation.  I've tried watching a DVD (City of God -- awsome movie) and MythTV showed the gov't warning but nothing else.  I haven't configured anything with the special codecs so I'll try that and post back a progress report.

---

### Post by road2elysium on 2007-11-26
> **spinlock99 said:**
> I've got a simmilar situation.  I've tried watching a DVD (City of God -- awsome movie) and MythTV showed the gov't warning but nothing else.  I haven't configured anything with the special codecs so I'll try that and post back a progress report.

Any progress on this?

---

### Post by spinlock99 on 2007-11-27
> **road2elysium said:**
> Any progress on this?

None yet.   I just got the TV tuner working last night so DVD support is on the menu for tonight.

---

### Post by spinlock99 on 2007-11-28
OK, I think there's a bug in MythTV Control Center.  When I tell it to install the non-free codecs it seems to fail and the codecs aren't installed.  I did get it to work by opening synaptic and installing the codecs by hand (just search on the names "w32codecs' and "libdvdcss2").  I was a bit surprised that it asked me to insert the Mythbuntu CD into the drive:confused:

Here's what it looks like:

---

### Post by superm1 on 2007-11-28
> **spinlock99 said:**
> OK, I think there's a bug in MythTV Control Center.  When I tell it to install the non-free codecs it seems to fail and the codecs aren't installed.  I did get it to work by opening synaptic and installing the codecs by hand (just search on the names "w32codecs' and "libdvdcss2").  I was a bit surprised that it asked me to insert the Mythbuntu CD into the drive:confused:

Here's what it looks like:

This bug has already been reported. Either run mcc with the disk in the drive or go to software sources and disable the disk.

---

### Post by road2elysium on 2007-11-29
> **spinlock99 said:**
> OK, I think there's a bug in MythTV Control Center.  When I tell it to install the non-free codecs it seems to fail and the codecs aren't installed.  I did get it to work by opening synaptic and installing the codecs by hand (just search on the names "w32codecs' and "libdvdcss2").  I was a bit surprised that it asked me to insert the Mythbuntu CD into the drive:confused:

Here's what it looks like:

Were you able to play your test DVD after installing the non-free codecs?  I was aware of that particular bug and have previously installed the libdvdcss2/w32codecs with the Mythbuntu CD, but I don't recall being able to play DVDs still.  I'll give it a try later and double-check in Synaptic.

---

### Post by spinlock99 on 2007-11-29
yup, dvd playback works.   I watched "Pan's Labrynth" last night.

---

### Post by road2elysium on 2007-12-01
> **road2elysium said:**
> Were you able to play your test DVD after installing the non-free codecs?  I was aware of that particular bug and have previously installed the libdvdcss2/w32codecs with the Mythbuntu CD, but I don't recall being able to play DVDs still.  I'll give it a try later and double-check in Synaptic.

Update: So I double-checked in Synaptic, and I did have libdvdcss2 / w32 codecs installed already.  So I popped in Lord of the Rings as a test DVD.  No go.  Mythbuntu will auto-detect the presence of the DVD and load to the optical disk section if I specify it to do so in the settings, but it just enters a blank screen and dies back to the optical disk menu.  I'll look into it later maybe when I have some free time and update accordingly.

---

### Post by road2elysium on 2007-12-08
> **road2elysium said:**
> Update: So I double-checked in Synaptic, and I did have libdvdcss2 / w32 codecs installed already.  So I popped in Lord of the Rings as a test DVD.  No go.  Mythbuntu will auto-detect the presence of the DVD and load to the optical disk section if I specify it to do so in the settings, but it just enters a blank screen and dies back to the optical disk menu.  I'll look into it later maybe when I have some free time and update accordingly.

So I finally figured out why my DVD playback didn't work with libdvdcss2 and other codecs correctly installed.  Boy, it's a doozy.

I'm running a mac mini frontend with a Matsushita optical drive.  Turns out that Masushita drives come with hardware CSS and without a region code initially set.  So I had to install OS X and pop in a DVD to auto-set my region code.  Reinstalled Mythbuntu and my DVDs now play.

---

### Post by superm1 on 2007-12-08
> **road2elysium said:**
> So I finally figured out why my DVD playback didn't work with libdvdcss2 and other codecs correctly installed.  Boy, it's a doozy.

I'm running a mac mini frontend with a Matsushita optical drive.  Turns out that Masushita drives come with hardware CSS and without a region code initially set.  So I had to install OS X and pop in a DVD to auto-set my region code.  Reinstalled Mythbuntu and my DVDs now play.
Hate to tell you this now...... there is a 'regionset' utility available in the repos....

---

