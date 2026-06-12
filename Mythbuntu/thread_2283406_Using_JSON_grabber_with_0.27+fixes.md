---
title: "Using JSON grabber with 0.27+fixes"
date: 2015-06-21
forum: Mythbuntu
---

### Post by MoebusNet on 2015-06-21
I corresponded with Schedules Direct support about why my Programming Guide looked so scrambled with my digital cable provider. Here's what he told me:

"Right, so that's QAM.

There are two choices. If you stay on the XMLTV grabber (the default
in MythTV), you'll need to manually update the XMLID for each
channel, because it doesn't have QAM support. (You'd add the
SD40415:X to your account at Schedules Direct and get rid of
SD40415). Then as you tune each channel you'd use something like the
lineup editor in MythWeb to put in the XMLID for that station. So if
VH1 has xmlid "20454" (it doesn't), then you'd put that in. That's
how MythTV will know which schedule to apply to that physical
channel.

If you want to use the JSON service from Schedules Direct, then it
has built-in support for QAM. You'd run a different grabber program
than mythfilldatabase, and we'll do most of the work to create the
lineup."

My question to the community is, will I be better off staying with XMLTV grabber and doing the manual editing required (~100 channels), or can I use the JSON grabber with 0.27.4+fixes so that the editing is done by Schedules Direct? I have read that JSON may be built into 0.28, but that it is not yet a default choice for 0.27.4.

I welcome recommendations. TIA.

---

### Post by aelfric55 on 2015-06-22
I'd tend to take the mythtv developers at their word from the wiki: **"Warning:** There is a Schedules Direct grabber available which uses an alternate JSON feed. **This grabber is not supported**  by the MythTV team. It inserts data directly into the MythTV database,  bypassing MythTV's ability to sanity check, correct and act upon  information at a single point of insertion. We will be unable to assist  users who run this grabber if they encounter bugs or broken features as a  result."

From a more practical standpoint, even if the JSON feed really does become supported, with mythtv 0.28 or whenever, in whatever month or year 0.28 is released, you'll certainly spend more time trying to configure and debug the newer system now in its initial adoption phase than the 30-45 minutes you'll spend entering XMLTV ID numbers into your channel editor under the current mature system, where the procedure hasn't changed much in the 8 years since Schedules Direct went online.

---

### Post by MoebusNet on 2015-06-23
@aelfric55 - Thank you for your advice. I believe your recommendation will be what I'll be using. I had seen the warning about non-supported JSON grabbers, but I was under the apparently mistaken impression that 0.28 had a developmental but supported JSON grabber, so I upgraded to 0.28. I was clearly wrong, since 0.28 is still using *mythfilldatabase* by default with no supported JSON grabber available.

Rather than attempt a backup-and-restore/ reinstall 0.27, I guess I'll try to edit the XMLTV ID numbers in 0.28 (it seems to be fairly stable so far). I can always do a clean install if I muck it up too much.

Can you recommend a link to a how-to identify and edit XMLTV ID numbers in Myth? My admittedly limited search on the issue was not helpful so far.

I very much appreciate the help and advice.

**EDIT** I found how to obtain the XMLTV ID numbers from Schedules Direct at: [https://www.mythtv.org/wiki/XMLTV_ID](https://www.mythtv.org/wiki/XMLTV_ID)

I'm still looking for a good how-to for edit the XMLTV ID numbers in Myth; I'll try out using the Channel Editor if it is straight-forward as it appears. Thanks again.

---

### Post by aelfric55 on 2015-06-23
As long as you have already identified what the physically received channels actually are, and what virtual channel number they're listed on in your mythtv guide (I always end up writing them down in a long list), then the simplest way is to open up the channel editor, bang the numbers in on the appropriate line of the form one channel after the other, close up the channel editor and mythtv-setup, and  run mythfilldatabase to start filling in schedule data. If you don't know what the physical channels actually are, then you end up having to do things like go channel-by-channel in live-tv and enter the xmltv-id number for the channel on your screen in mythweb (I don't think the on-screen edit menu exists any longer), and then run mythfilldatabase.  A pain, but the only way I've ever been able to get schedule data set up with Schedules Direct and Comcast.

---

### Post by MoebusNet on 2015-06-23
I used this: [https://www.mythtv.org/wiki/Frontend_Channel_Editor](https://www.mythtv.org/wiki/Frontend_Channel_Editor)  as a guide; the 'Probe" command not only didn't work but locked up Myth, requiring a power-off shutdown then cold-boot for every channel edited. Instead, I basically inserted the XMLTV ID in backend setup - Channel Editor then selected 'OK' for each channel after editing. BTW, Channel Editor can only display 4 integers (ie, 83-11) even though I came across some channels that needed 6 integers (ie, 113-113). Pressing 'Enter' will display the complete channel info.

I've got everything in the lineup setup now,  but Midcontinent has about 6 channels that aren't in Schedules Direct's lineup - now I need to figure out how to get an XMLTV ID for them (they're mostly local OTA Channels like PBS).

Other than that, i think I can call this 'Solved'.

---

