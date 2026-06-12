---
title: "Help with unusual STB setup?"
date: 2008-04-05
forum: Mythbuntu
---

### Post by grytpype on 2008-04-05
Can anyone help me with the following unusual setup problem?

I have an STB that has good Firewire output for most channels, but there is a block of channels that don't output in Firewire, so I need to use my PVR-250 card for them.

I have the Firewire and PVR card inputs set up, but I am having trouble with two problems:  

1) Schedules Direct doesn't let me set up a second cable lineup (which I would do if I could, with just the PVR channels), so how do I do a special lineup with just the PVR-only channels, and 

2) once I do get the second lineup in my mythbox somehow, how do I prevent the Firewire and PVR inputs from trying to record at the same time (that is, how do I make them mutually exclusive)?

Any help would be appreciated!

---

### Post by volkswagner on 2008-04-05
In schedules direct you can try searching nearby zip codes.  Sometimes they have slightly different lineups.  You can edit in channel editor.  You can also create a second source using the same lineup.  Use a unique name and edit in channel editor.  You can select individual sources in channel editor.  The second option will cause the backend to complain.  You will get a message in the backend log "using digital and analog on same lineup this may be a bad idea"

---

### Post by volkswagner on 2008-04-05
2> ) once I do get the second lineup in my mythbox somehow, how do I prevent the Firewire and PVR inputs from trying to record at the same time (that is, how do I make them mutually exclusive)?

Mythtv is  "smart" enough not to record the same thing twice.  You may want to set priorities in setup.  You may prefer to use firewire or the pvr250.  Which ever you prefer to use first in recording set a higher priority.  When scheduling a recording you can also specify which input to use under "scheduling options".

Note:  When setting up your lineup using the xml code is great.  I made a hard copy of my line up, and the nearby lineup.  Changing the xml code in channel editor, then selecting update info. works great.

---

### Post by majoridiot on 2008-04-05
> **grytpype said:**
> Can anyone help me with the following unusual setup problem?

I have an STB that has good Firewire output for most channels, but there is a block of channels that don't output in Firewire, so I need to use my PVR-250 card for them.

I have the Firewire and PVR card inputs set up, but I am having trouble with two problems:  

1) Schedules Direct doesn't let me set up a second cable lineup (which I would do if I could, with just the PVR channels), so how do I do a special lineup with just the PVR-only channels, and 

2) once I do get the second lineup in my mythbox somehow, how do I prevent the Firewire and PVR inputs from trying to record at the same time (that is, how do I make them mutually exclusive)?

Any help would be appreciated!

not directly related... but i am developing a channel-scanner for stbs that will tune each channel 
one at a time via firewire and make a list of "good" and "bad" channels to help with setting
up alternate firewire-only lineups and custom mythtv rules.  the intent is to integrate it directly
into MCC when it is completed, to make it that much easier.

binaries will be  posted on the firewire guide page when they are completed (hopefully 
next week- the new primer should be about finished).  

i'll post a thread here in the forums to let everyone know when it is available and when 
the firewire guide is updated.  hopefully this will be one more valuable tool to helping folks
set up firewire connections with as little hassle as possible.

---

### Post by grytpype on 2008-04-05
Thanks for all the suggestions.

1.

The only solution I could actually make work was to set up a new listings source on SD using a nearby zipcode.  By pure luck, Cablevision Westchester has the same lineup as Cablevision Bronx.  With two SD lineups it was trivially easy to set up a different channel lineup for the FW and PVR inputs separately.

Really, SD needs to allow multiple lineups from the same source, I don't see any obstacle to doing that.

The problem with deleting channels is that mythfilldatabase is going to add the channels back in the next time it runs.

And if you're going to have the same channel lineups for the two different inputs and fix the overlap by using priorities... good luck with that, I couldn't see a way to make it work.

2.

I believe the way to handle two inputs from the same STB (in .21 at least) is to use input groups.  I haven't tested this, but in 4. Input connections, I created an SA4250 input group and assigned both the FW and PVR input connections to it, that is supposed to take care of it, although as I said I haven't tested this yet.

---

### Post by grytpype on 2008-04-05
OK, here's SD's response to my request:

> [schedulesdirect.org #2043] Other Lineup&#8207;
From: 	Robert Kulagowski via RT (lineups@schedulesdirect.org)
Sent: 	Sat 4/05/08 3:00 PM
Reply-to: 	[email]lineups@schedulesdirect.org[/email]
To: 	[email]XXXXXXXXXx@hotmail.com[/email]

On Fri Apr 04 21:50:48 2008, [email]XXXXXXXX@hotmail.com[/email] wrote:
> 
> Is there any way to set up two lineups based on the same source, i.e.,
> I have a "Cablevision - Digital" lineup, but I want to set up two
> lineups based on that source, to sort out the channels that work with
> Firewire and the ones that don't and that I need to use a capture card
> for.  Any way to do that?  Thank you!
 
Sorry, no.  You can only add each lineup once to your account.

In other words, "screw you subscriber!"  I almost emailed Robert a link to this thread, then I thought better of it lest my account gets deleted due to some perceived abuse!  I must say I don't understand what the problem is.

---

### Post by majoridiot on 2008-04-05
> **grytpype said:**
> In other words, "screw you subscriber!"  I almost emailed Robert a link to this thread, then I thought better of it lest my account gets deleted due to some perceived abuse!  I must say I don't understand what the problem is.

that's kinda harsh.  i realize that it is inconvenient, but as you found there is a workaround that works fine for most people.

if you read the subscriber agreement, etc., there is no guarantee of multiple line-ups for a single account.  if this is a problem, 
maybe a second account there is what you need.  or possibly a constructive comment/suggestion to SD, explaining the situation
and why a second line-up from the same provider would be of real use to people.

IMO, SD provides a great service at an incredibly reasonable price and should be lauded, not flamed because their service limits do
not necessarily match your needs.

---

### Post by grytpype on 2008-04-05
> **majoridiot said:**
>  or possibly a constructive comment/suggestion to SD, explaining the situation
and why a second line-up from the same provider would be of real use to people.

This is in fact what I just did, and I hope SD regards this as a legitimate new feature request.  I think with FW becoming more popular as an input, and the known limitations of FW due to cable company policies, this is an issue that may affect many Myth users.

---

### Post by majoridiot on 2008-04-05
> **grytpype said:**
> This is in fact what I just did, and I hope SD regards this as a legitimate new feature request.  I think with FW becoming more popular as an input, and the known limitations of FW due to cable company policies, this is an issue that may affect many Myth users.

agreed.

---

