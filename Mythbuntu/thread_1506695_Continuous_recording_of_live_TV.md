---
title: "Continuous recording of live TV"
date: 2010-06-10
forum: Mythbuntu
---

### Post by phroman on 2010-06-10
Hello everyone, I'm having an issue with the live tv function of mythtv and wonder if it can be changed to my liking.  

If I exit live tv to the main menu, it stops recording live tv. I found this in the mythwiki concerning MythTV 0.19 and beyond. 

> If you are watching LiveTV and exit to the menu, MythTV will stop recording to this Live recording. But if you hit record while watching and exit to the menu it will continue recording the show, as one would expect, until it finishes.

Here's what happens:  Your watching show 1 and the episode finishes, show 2 comes on next, and 25 minutes into show 2 you exit live tv.  You now decide you wanted to watch show 2 but you can't because mythtv stopped recording when you exited to the main menu.  The mythtv frontend should ALWAYS be recording a buffer of live tv.  Always.  Having to remember to hit record before exiting live tv is incredibly bad.  This is one of the key issues I had with Snapstream Beyond TV.  Its probably tivo's best feature, no matter what, tivo is always recording a 30 minute buffer.  

Is there a way I can change this for my system? I mean, to me, its hard to see why it doesn't work this way.  How about a consensus as to what others think of this?  Thoughts, opinions...   Thanks!

---

### Post by laffinet on 2010-06-10
I don't really see how this is an issue, nor how there could be a reasonable solution. 

What about channel changes ? Would you want it to record each channel for a further 30min after changing ? Not really practical.

I don't think it's asking too much to remember to hit 'record' when you want to record a program you're watching. MythTV is even smart enought to add the bit you have been watching so far to that recording, not just the bit from when you hit record.

---

### Post by phroman on 2010-06-11
hi laffinet, thanks for the reply.  

> I don't really see how this is an issue, nor how there could be a reasonable solution. 

I thought my example of show 1 and show 2 was pretty descriptive.  That exact thing happened to me with 20 people at my house for the show finale of Sopranos.  25 minutes into Entourage, which followed Sopranos, I exited out to the main menu, not 5 seconds later somebody piped up, "hey let's watch Entourage",  I couldn't because I lost the buffer.  If I hadn't exited live tv, we could have seen the whole show.  With what I'm proposing, if I had restarted live tv, I could have rewound to the beginning of the show and we could have watched the whole thing.  

How many times have you turned on your tv in the middle of a show and wished you could go back to the beginning?  This would allow you to do that. Depending on your setup, you could set a length of time for your recording buffer, and maybe catch an entire show.  

> What about channel changes ? Would you want it to record each channel for a further 30min after changing ? Not really practical  

I think it should record whatever is happening for lets say 30 minutes.  It would be one continuous recording, including channel changes.  I think this would be a little more like the Ring Buffer that myth used in the past.  Is that a better description of what I'm looking for?  Thanks!

---

### Post by nickrout on 2010-06-11
you misunderstand how mythtv works. Record what you want to watch. LiveTV is not a priority for mythtv.


Also if you have a feature request this is not the place for it. Seriously the mythtv devs do NOT read this list.

If you have a feature request WITH a patch, post it to the bug tracker. If you have a feature request without a patch then you need the user mailing list.

Some people have hundreds of channels. Are you suggesting mythtv should maintain a live recording of each defined channel?

---

### Post by phroman on 2010-06-11
Hi nickrout, I understand how mythtv works, my post was to see if something about the way it works could be changed for my needs. If that falls into a feature request I will redirect my focus there.   

Just so I know, do you guys not understand from my example what I would like it to do and why  I'd like it to do that?  I can explain further if nessecary.  

> Some people have hundreds of channels. Are you suggesting mythtv should maintain a live recording of each defined channel?

No, that's ridiculous.  Have you ever used a tivo?  Its always recording, all of the time.  Whatever channel the stb is on is being recorded at all times.  Usually you have a 30 minute recording buffer.  If at any time in live tv, you hit rewind, you can back up, up to 30 minutes worth, even through a channel change.  

Please let me know if I can be more descriptive, or if you understand what I'm trying to accomplish but am simply in the wronf forum.  Cheers

---

### Post by SiHa on 2010-06-11
If it's really that important to you, why not just leave it in LiveTV, and turn the set off instead when you want to stop. You can set it to time out after a programmed period (say 1 hr), but seriously, how can this be a bug?
What are the chances of you deciding that you want to watch the same channel. I used to use a PVR that had the constant 30min buffer, and yes it proved useful very occasionally but it's certainly not a showstopper not having it.

---

### Post by LowSky on 2010-06-11
I actually see this idea as a problem. And having MythTV constantly writing data, even when your not recording a preferred show is going to put heavy wear on the hard drive. Also how does it know what channel to record? The last one you were on? That is fine if you only watch one channel but its does nothing if you wanted to watch something you just missed on another.

Best idea is to buy an extra tuner card, preferably one with 2 inputs (HVR-2250, or HDhomerun), and schedule more shows to record, even one you might not be interesting too much, and set those programs to auto-expire earlier than normal recordings.

---

### Post by tgm4883 on 2010-06-11
> **phroman said:**
> Hi nickrout, I understand how mythtv works, my post was to see if something about the way it works could be changed for my needs. If that falls into a feature request I will redirect my focus there.   

Just so I know, do you guys not understand from my example what I would like it to do and why  I'd like it to do that?  I can explain further if nessecary.  



No, that's ridiculous.  Have you ever used a tivo?  Its always recording, all of the time.  Whatever channel the stb is on is being recorded at all times.  Usually you have a 30 minute recording buffer.  If at any time in live tv, you hit rewind, you can back up, up to 30 minutes worth, even through a channel change.  

Please let me know if I can be more descriptive, or if you understand what I'm trying to accomplish but am simply in the wronf forum.  Cheers

I'll just re-echo things already said.

Constant recording - unneeded wear on the hard disk

For shows you want to watch, why not set a schedule and have it record? Then you get the benefit of commskipping as well. LiveTV is something that is low priority for upstream. I am 90% sure that if you suggest that idea, you will need a patch attached as well.

---

### Post by phroman on 2010-06-11
Hi everyone

SiHa: I never said it was a bug of any kind, I simply wanted to know if I could change one of the ways mythtv functioned for my needs.  If my description of my situation had a tone of discontent, its slight, I can assure you.  This is not a deal breaker in any way for me to use mythtv.  

LowSky:   > And having MythTV constantly writing data, even when your not recording a preferred show is going to put heavy wear on the hard drive

Not really a concern for me, it seems more an imagined potential problem than a real one.  I buy good hard drives, and if one did fail, they're just tv shows..  :)

> Also how does it know what channel to record? The last one you were on? That is fine if you only watch one channel but its does nothing if you wanted to watch something you just missed on another.

Once you exit out to the main menu it would just continue to record whatever channel you left it on, so yes, it would definitely miss something on another channel.  If you went back into live tv at let's say 2:15, and hit rewind, it would backup through the change in shows from 1:00 to 2:00.  Just one continuous recording.  

tgm4833:  I'm not a programmer, so I wouldn't be able to provide a patch.  As SiHa said:

> I used to use a PVR that had the constant 30min buffer, and yes it proved useful very occasionally but it's certainly not a showstopper not having it. 

I'll definitely say its in the occasional use category, but maybe for me its one of those things in life where you never need it till you need it, but then you need it. But its no show-stopper not having it for me either.  I'm not going to stop using mythtv.  I haven't used an actual tivo in many years, but I remember if you exit to the main menu, where you can browse you stored shows, and you click back to watch live tv, you can still rewind because it kept recording, that's what I'm after.

I think the tone of my post may have come off as more of a complaint than I intended, I'm sorry about that if it did.  I'll be interested to see if this thread can last a bit and see if any others think what I'm after would be useful to them as well.  Thank you for all the input and suggestions everyone.  Cheers ):P

---

### Post by nickrout on 2010-06-11
yes you ARE in the wrong forum. Feature requests go to the users mailing list, unless you have actually written a patch in which case you post it to trac.

---

### Post by phroman on 2010-06-11
Thanks nickrout, I didn't initially intend this post to be a feature request but its definitely turned into one...  Great, I'll check out the user mailing list, thanks.

---

