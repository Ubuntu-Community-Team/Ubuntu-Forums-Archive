---
title: "When did PVR-350 become cable-ready?"
date: 2008-04-24
forum: Mythbuntu
---

### Post by ChrisMoose on 2008-04-24
I'm a total Myth and Linux noob, but a buddy of mine talked me into turning an old Athlon box into a Mythbuntu box. He gave me a Hauppauge PVR-350 card that he'd bought in 2006 and wasn't using.

The installation seemed to go without a hitch. I plugged in my cable (Comcast basic analog) and did a Channel Scan, and it only found channels 1-13. When I watch live TV on those channel, I get an image; when I try a channel above that, I get snow.

Now, the Hauppauge product page for the 350 says that it comes with a 125-channel cable-ready tuner, and I know folks with the 150 who had no problems with basic cable. However, the aforementioned buddy said that the Hauppauge cards had not always handled basic cable, and wasn't sure that the one he gave me did.

So, my questions:
[LIST=1]
[*]Does anyone know when the PVR-350 started shipping with a cable-ready tuner?
[*]Does the fact that I can see the 13 broadcast channels mean anything? Does Comcast encrypt (or whatever) the signal for the over-the-air channels?
[*]Is there anything I need to do in the Myth setup? Or is this solely a function of the card?
[/LIST]

If these questions are blazingly obvious, I apologize, but I'd appreciate any help someone might throw my way.

Thanks!

---

### Post by gazer22 on 2008-04-24
I'm pretty sure that the -350 has always been cable ready.

It sounds like you don't have MythTV setup quite correctly.  In fact, it sounds like you have it set up for antenna ("us-bcast") instead of cable ("us-cable").

In MythTV-Setup, go to General, then hit "Next" to get to the "Locale Settings" page.  Ensure that "Channel frequency table" reads "us-cable."

Hit Next a bunch more times and then Finish to get back to the MythTV setup main page.

Ensure that you have a SchedulesDirect account and that it's correctly configured under "Video Sources."

Finally, ensure that under "Input Connections," that "Tuner 1" is associated with your Schedules Direct input.

Exit from MythTV setup and make sure that mythfilldatabase runs.

Should work now...

---

### Post by ChrisMoose on 2008-04-24
Thanks, Gazer22. I'll try it tonight (box is at home, I'm at work -- don't tell) and report back.

---

### Post by ChrisMoose on 2008-04-25
Yep - that did the trick. Thanks!

Now, onto the next problem...

---

