---
title: "Set tuners to certain channels"
date: 2008-09-25
forum: Mythbuntu
---

### Post by iitywygms on 2008-09-25
I have 3 tuners on my system.  2=hdhomerun, 1=pvr150
When I tune to a channel, how can i make mythtv know that it has to use a certain tuner for that channel?  Like when I tune to a analogue channel, make it use the pvr150.  When I tune to a digital channel, make it use the hdhomerun?
Do I need to configure the cards with different sources?
Thanks.

---

### Post by volkswagner on 2008-09-25
Yes, you will need separate input sources for each tuner.

Are all tuners using the same lineup from SchedulesDirect?

Mythweb has a channel editor.  You can delete the channels that you don't want included for each input source.  

Then run mythfilldatabase.

---

### Post by iitywygms on 2008-09-25
> **volkswagner said:**
> Yes, you will need separate input sources for each tuner.

Are all tuners using the same lineup from SchedulesDirect?

Mythweb has a channel editor.  You can delete the channels that you don't want included for each input source.  

Then run mythfilldatabase.

Yes, they are all using the same lineup from schedules direct.

Should I create a different lineup for each card from schedules direct?
Do I edit the schedules direct linups?

I only have one input source for all cards. (comcast cable).  If i use that source and re-name it, is that considered a new input source?

I thought the channel editor was a global editor.  I did not know I could edit a channel for each card.  I am not home now but will take a look when I get back.
Thank you for the help.

---

### Post by newlinux on 2008-09-25
In your situation I created a separate lineup in schedules direct and separate video sources for my analog cable stations and digital cable stations (but there is some overlap in the stations). I use the basic cable lineup for my analog stations, and digital cable lineup for my digital stations. Once you have different video sources you can modify the channels on a per source basis. I find it easier to modify channels in mythweb than in the channel editor in mythtv-setup.

---

### Post by iitywygms on 2008-09-25
"modify the channels on a per source basis"

I think that is the key.  Is that done thru mythweb?  I am new to mythtv and I have not seen where that function is available.

Thank you.

---

### Post by newlinux on 2008-09-25
YOu can modify channels per source in the mythtv-setup or in mythweb. If you use mythweb, you have to know which id of the video source you want to change (it doesn't use the name). I have 3 lineups with SourceIDs 1, 2, and 3. But to me it is an easier interface to use than mythtv-setup's, especially if you end up doing a lot of editing, since you can do it all on one page.

The channel modification in mythweb is in the settings menu

Settngs->TV->Channel info

or ```
http://mythwebserverhostname/mythweb/settings/tv/channels
```
replace mythwebserverhostname with yours of course.

---

### Post by iitywygms on 2008-09-25
> **newlinux said:**
> YOu can modify channels per source in the mythtv-setup or in mythweb. If you use mythweb, you have to know which id of the video source you want to change (it doesn't use the name). I have 3 lineups with SourceIDs 1, 2, and 3. But to me it is an easier interface to use than mythtv-setup's, especially if you end up doing a lot of editing, since you can do it all on one page.

The channel modification in mythweb is in the settings menu

Settngs->TV->Channel info

or ```
http://mythwebserverhostname/mythweb/settings/tv/channels
```
replace mythwebserverhostname with yours of course.

In order to do this, I have to make different sources correct?  That means making one source for my analogue card and one for my hdhomerun.
And to make a new source, I just make a new one with a different name, since they both use comcast cable.
Is my thinking straight?

---

### Post by newlinux on 2008-09-25
> **iitywygms said:**
> In order to do this, I have to make different sources correct?  That means making one source for my analogue card and one for my hdhomerun.
And to make a new source, I just make a new one with a different name, since they both use comcast cable.
Is my thinking straight?

Yes that should work. 2 of mine are comcast but they actually use two different schedules direct lineups because comcast has a different analog lineup here than they do digital here (.e.g. the HD versions of the stations are only available on the digital lineup - so If I want the guide info that is specific to HD channels I need to use their digital lineup in schedules direct as tthe source). But if all the channels you want for both tuners are in your lineup, you should just be able to create two different sources to the same schedules direct lineup and be able to modify the channels in each source differently. I haven't tried it that way, but it should work. if not, you could just create a separate schedules direct lineup and do it that way. you can have up to 4 I think with one account...

---

### Post by iitywygms on 2008-09-25
It appears I have two ways of accomplishing what I want.
1.  Go to schedules direct, edit the account and delete the channels I do not want to show, go to the backend and tell it to "retrieve channels from sourcing list" for each separate card.
or
2.  Do nothing with schedules direct except make sure I have a lineup source.
Go to back end and have each card scan for all channels, then use mythweb to map each channel to the correct card.

Have I got it?  I think option one is the best.  I will try that.
Thanks for the help.

---

### Post by iitywygms on 2008-09-26
Still having the same issue.  If I am watching a channel with my analogue tuner, then switch to a digital channel, I have to manually switch tuners.  What am I not getting?  How do I set up mythtv to know which tuner to use on each channel?

---

### Post by volkswagner on 2008-09-26
You should verify in Myth-setup>Channel editor.  Make sure you don't have any overlapping channels.  I had trouble with getting my input sources just the way I want.

---

### Post by iitywygms on 2008-09-26
Re-did everything in the backend.
All works as should now.
I dunno.....................

---

