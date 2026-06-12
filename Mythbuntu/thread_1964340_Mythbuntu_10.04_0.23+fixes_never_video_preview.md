---
title: "Mythbuntu 10.04 0.23+fixes never video preview"
date: 2012-04-23
forum: Mythbuntu
---

### Post by anonymousdog on 2012-04-23
Maybe this will be fixes in 12.04 with mythtv 0.25, but I'm trying to "clean house" in 10.04 and 0.23 before the upgrade.  One nagging (and really irritating) issue that has persisted the whole two years on 10.04 has been the utter failure of video previews to display (on any frontend in the house, even the backend PC).  Logs show previews being generated, and they play just fine in vlc or whatever (on all frontends).  However, the frontend never displays them despite its being requested in the frontend settings.  Frontend logs show the preview being "grabbed"; it just never displays.  I find no tickets for this issue and only a single post about 0.22 not implementing this feature...I skipped from 0.21 to 0.23.

Anyone have thoughts on this?

---

### Post by uncle hammy on 2012-04-23
I believe that as of 0.24, video previews are gone anyways.

---

### Post by anonymousdog on 2012-04-23
Thanks for the quick reply, Uncle.

That's a drag.  That feature had good "wow" factor and didn't seem to cost much in terms of resources on either front or backends.  Probably never re-implemented after 0.21.  <snark>Awesome documentation, Mythtv team!</snark>...the worst recurring bugaboo of open source is poor documentation.

---

### Post by tgm4883 on 2012-04-23
> **anonymousdog said:**
> Thanks for the quick reply, Uncle.

That's a drag.  That feature had good "wow" factor and didn't seem to cost much in terms of resources on either front or backends.  Probably never re-implemented after 0.21.  <snark>Awesome documentation, Mythtv team!</snark>...the worst recurring bugaboo of open source is poor documentation.

You could always fix the documentation...    the worst recurring bugaboo of open source software is people complaining about the work other people aren't doing.

---

### Post by uncle hammy on 2012-04-24
> **tgm4883 said:**
> You could always fix the documentation...    the worst recurring bugaboo of open source software is people complaining about the work other people aren't doing.

+1.  You know it's an issue, so spend the same amount of time you took to complain, and fix it.

Having said that, I am not 100% sure they're gone, I just recall that as of ~0.24, they disappeared from my system in favor of static images and I couldn't find any options to bring them back.

---

### Post by klc5555 on 2012-04-24
> **uncle hammy said:**
> +1.  You know it's an issue, so spend the same amount of time you took to complain, and fix it.

Having said that, I am not 100% sure they're gone, I just recall that as of ~0.24, they disappeared from my system in favor of static images and I couldn't find any options to bring them back.

The animated previews disappeared in favor of static displays back with 0.22. Apparently widgets that would have been necessary to enable old-style animated previews familiar from 0.21 and earlier in the new MythUI in 0.22 and later never got written.

---

### Post by uncle hammy on 2012-04-24
> **klc5555 said:**
> The animated previews disappeared in favor of static displays back with 0.22. Apparently widgets that would have been necessary to enable old-style animated previews familiar from 0.21 and earlier in the new MythUI in 0.22 and later never got written.

Thanks for confirming.  I knew I remembered them disappearing (though I didn't realize it was that far back).

---

### Post by anonymousdog on 2012-04-24
> **tgm4883 said:**
> You could always fix the documentation...    the worst recurring bugaboo of open source software is people complaining about the work other people aren't doing.
...in your opinion.  In the end, I feel vindicated because there was nothing to do and nothing to document (although the feature removal should be in MythTV changelogs).

I've used a lot of open source and contributed where I can...time, skills, money.

When I criticize the lacking documentation, I'm sure it feels good to counter with what feels like an incontrovertable ethic, but it's totally inappropriate in this case: This was not an "issue" that should be ticketed. It was a feature removal that got no mention anywhere I can find.  It's impossible to document that (the unknown) except via the method I've chosen here.

Prior to posting, I had spent many hours on it (over the course of two years), trying to find something of meaning in logs...nope.  Entry in change logs...nope.  Any discussion anywhere of the feature's passing/breaking/whatever...nothing.  I tried to ensure nothing in my setup was causing the loss of this feature.

So, please, folks -- you who are so eager to pile on and blame the one with a little, light-hearted criticism -- explain how I could have fixed this or documented what I didn't know.  There are many times that the answer should be, "Well, contribute the thing you're missing," but, when I'm not a programmer nor do I have knowledge of what happened to the feature, there's no way for me to contribute except to ask the question.  Neither is it untoward or inappropriate to note how often documentation gets left behind in the development shuffle.

Moreover, I am of the strong opinion that coders should document; no one is in a better position to do it...no one.  It's not thrilling or sexy, but it needs to get done and can only really be adequately done by the coders most knowledgeable about their product.  Editors can clean it up, make it flow nicely, but they can't produce the content.

The one time I did a very minor and surely horrific rewrite of anything r/t MythTV was to get the mythstreamtv plugin working in 8.04/0.21.  I documented plenty as I should have, as no one else was in a position to do (because they hadn't done the rewriting).

So, please, I know I stepped on a sensitive area, but demonstrate some discretion before reacting so strongly; your first reaction ("well, contribute!") isn't always right or even sensible.

---

### Post by tgm4883 on 2012-04-25
> **anonymousdog said:**
> ...in your opinion.  In the end, I feel vindicated because there was nothing to do and nothing to document (although the feature removal should be in MythTV changelogs).

I've used a lot of open source and contributed where I can...time, skills, money.

When I criticize the lacking documentation, I'm sure it feels good to counter with what feels like an incontrovertable ethic, but it's totally inappropriate in this case: This was not an "issue" that should be ticketed. It was a feature removal that got no mention anywhere I can find.  It's impossible to document that (the unknown) except via the method I've chosen here.


I did 5 minutes of researching on the mythtv website, and while I didn't find when exactly it was removed I now know that it definitely wasn't available in 0.24 (found in the release notes for 0.24) and also the commit referencing that it is currently unavailable.

> "Generate Preview image remotely" - All are generated remotely now (Hide additional settings until video previews are re-introduced) [25435]

> **anonymousdog said:**
> 
Prior to posting, I had spent many hours on it (over the course of two years), trying to find something of meaning in logs...nope.  Entry in change logs...nope.  Any discussion anywhere of the feature's passing/breaking/whatever...nothing.  I tried to ensure nothing in my setup was causing the loss of this feature.


Again, 5 minutes

> **anonymousdog said:**
> 
So, please, folks -- you who are so eager to pile on and blame the one with a little, light-hearted criticism -- explain how I could have fixed this or documented what I didn't know.  There are many times that the answer should be, "Well, contribute the thing you're missing," but, when I'm not a programmer nor do I have knowledge of what happened to the feature, there's no way for me to contribute except to ask the question.  Neither is it untoward or inappropriate to note how often documentation gets left behind in the development shuffle.


5 minutes

> **anonymousdog said:**
> 
Moreover, I am of the strong opinion that coders should document; no one is in a better position to do it...no one.  It's not thrilling or sexy, but it needs to get done and can only really be adequately done by the coders most knowledgeable about their product.  Editors can clean it up, make it flow nicely, but they can't produce the content.


You are correct, it isn't thrilling or sexy. But since most developers aren't paid, I think you will find them not wanting to spend time writing documentation. Some do, and that is great. Now, there are changelogs and people that use the software (and have been for a very long time) that can write documentation. There are some people that do nothing else than write documentation. So before you tell me that it is completely impossible for non-developers to write (not edit) documentation, explain to me how non-developers are doing it right now.

> **anonymousdog said:**
> 
The one time I did a very minor and surely horrific rewrite of anything r/t MythTV was to get the mythstreamtv plugin working in 8.04/0.21.  I documented plenty as I should have, as no one else was in a position to do (because they hadn't done the rewriting).


Weird. I looked here [http://www.mythtv.org/wiki/MythStreamTV](http://www.mythtv.org/wiki/MythStreamTV) and it says that it doesn't work on mythtv versions after 0.20.2. Did they delete your documentation?

> **anonymousdog said:**
> 
So, please, I know I stepped on a sensitive area, but demonstrate some discretion before reacting so strongly; your first reaction ("well, contribute!") isn't always right or even sensible.

Your comment was 

> <snark>Awesome documentation, Mythtv team!</snark>...the worst recurring bugaboo of open source is poor documentation.

I was merely stating that if you have a problem with the documentation that you have the full rights to fix it. As I've previously stated, I found it was removed after 5 minutes of searching.

---

### Post by anonymousdog on 2012-04-25
tgm, you're attacking a position I didn't take and responding abrasively to the most minor of slights; I am not the enemy.

I wrote that documentation was *best* done by the coder, not that it *couldn't* be done by the coder.

Neither is this (original topic) an issue with remote generation of a preview *image* nor any feature (or lack thereof) in 0.24.  This was a change in preview video in 0.23 that was seemingly left about half-implemented with the preview video file actually still being generated and "grabbed" by the frontend then ignored.  I see that you didn't find any notation of this in 0.23 changelogs either.  Never the less, I must assume that, as an Ubuntu developer, your skills at finding these clues would completely eclipse my own (which makes your "5 minutes" refrain only repetitive instead of persuasive).

My MythStreamTV minor rewrite/hack was totally unofficial as the original project was not being maintained at the time; there was nothing passed back to the project on sourcefourge.  I didn't pass it back to the unofficial plugin page because it was IMHO a hack (at least my part)...never better than beta and lacking functionality.  You'll find my only other thread start on this forum on this very thing.

I appreciate all you and the other team members do.  I recognize your screen name from your many, many posts here...usually solving someone else's problem...even those areas covered well in the documentation.  I am not an interloper; I do not disrespect the effort; I am not your enemy.  Please, try to be less defensive.  I know my remark seemed like a direct affront to your work (or the principles that drive it), but it wasn't intended that way.

Thanks everyone for helping me check an item off the pre-upgrade to do list!

---

### Post by uncle hammy on 2012-04-26
> **anonymousdog said:**
> ...in your opinion.  In the end, I feel vindicated because there was nothing to do and nothing to document (although the feature removal should be in MythTV changelogs).

If there was nothing to document, why would you say something like.....?

> <snark>Awesome documentation, Mythtv team!</snark>...the worst recurring bugaboo of open source is poor documentation.

> **anonymousdog said:**
> When I criticize the lacking documentation

Again, if, as you claim, it can't be documented, why were you criticizing the "lack of documentation?  Seems a little childish to me.

> **anonymousdog said:**
> So, please, folks -- you who are so eager to pile on and blame the one with a little, light-hearted criticism -- explain how I could have fixed this or documented what I didn't know.

Your comment was hardly "lighthearted", it was actually kind of offensive, especially to people who work on all this stuff for free.  

> **anonymousdog said:**
>  -- explain how I could have fixed this or documented what I didn't know.

Ummm, after we told you about it, you knew......

---

### Post by anonymousdog on 2012-04-27
Then, allow me to start with an apology.  I looked back at the original post and do agree that the comment inside snark tags should have been omitted and didn't add anything to the discussion.  I apologize for any offense taken from that remark.

> **uncle hammy said:**
> If there was nothing to document, why would you say something like.....?

Again, if, as you claim, it can't be documented, why were you criticizing the "lack of documentation?  Seems a little childish to me.

Are we really resorting to characterizations and name calling?  It CAN be documented where it belongs: in the changelogs.  If there WERE a wiki page on 0.23 changes that could still be edited, I would be tempted to put it there, but there isn't -- that page is locked, even the discussion section.

> **uncle hammy said:**
> Your comment was hardly "lighthearted", it was actually kind of offensive, especially to people who work on all this stuff for free.

I do see how it could be offensive.  However, I strongly disagree with the prevailing ethic that criticism is not allowed.  I'm afraid that, "I do this work for free," all too often becomes a chip on one's shoulder and means that any criticism is met with sharp rebuke instead of consideration (and it turns people away from whatever venues where that rebuke occurs -- in this instance, the otherwise wonderful forums).  It's as if all that volunteer effort turns the project into one's own child.  That's good in many ways but also makes the volunteer react like a protective mother when her child is criticized (no matter how much it might be deserved).

My intent with my remark was to point out a recurring documentation issue with open source projects (where it manifests more strongly than some proprietary projects only because those [proprietary project] team members are paid to do it and because there is a management mandate that it be done.  Failure to document creeps up everywhere documentation is part of the job: Health Care, Architecture, all manner of Construction trades, all areas of Computer Science, etc.  It's really a "human nature" issue, and THAT was where my head was at the time of my original post.  Reading the comment fresh, I see that I did a very poor job of communicating that and how it could offend those who volunteer their efforts on the project (but not really other people, Hammy...that's a stretch).

---

