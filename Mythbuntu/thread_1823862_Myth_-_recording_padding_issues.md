---
title: "Myth - recording padding issues"
date: 2011-08-12
forum: Mythbuntu
---

### Post by ceejay on 2011-08-12
I know this question has been raised before, not least because I've just spent the last two hours reading incomplete, out of date or just confusing threads in various places - some help would be much appreciated!!

I thought it would be easy: when I set a program to record, from the program guide, I want Myth automatically to start 2 minutes early and finish 5 minutes late. This is to make sure I don't miss anything - broadcast times just aren't that accurate.

So I go to Setup - TV Settings - General and on page 4 I see Time To Record Before Start/Past End.  I set them to 120 and 300 seconds.  I do understand that if one tuner is recording adjacent shows then something may have to give - this is not the case with my examples.

What seems to be happening is that the early start is being honoured, but the late finish is not. Any idea why?

One of the many threads I've read is here: [http://www.gossamer-threads.com/lists/mythtv/users/435181](http://www.gossamer-threads.com/lists/mythtv/users/435181)  where there is some discussion of these as being "soft" padding options, and that there are also "hard" padding options. I know I can set them on a per-rule basis, but that isn't really usable for the (frequent) usage where one points and selects an item off the guide. I infer that there is somewhere I can set the default for new recording rules, but can't for the life of me find it in the menus anywhere.  

Can anyone give me a pointer or two?

TIA
Ceejay

NB: Using MythTV 0.24fixes on Ubuntu 11.04 in a split front/backend, with a Hauppauge DVB-T dual tuner.

---

### Post by nickrout on 2011-08-12
you need to use hard padding

---

### Post by ceejay on 2011-08-13
> **nickrout said:**
> you need to use hard padding

That was my second question - where is it?  

To be more precise: I know I can individually set hard padding on each recording rule, but where can I set a default that is applied to each new recording rule that is created subsequently?

Ceejay

---

### Post by nickrout on 2011-08-13
> **ceejay said:**
> That was my second question - where is it?  

To be more precise: I know I can individually set hard padding on each recording rule, but where can I set a default that is applied to each new recording rule that is created subsequently?

Ceejay

I don't believe you can, but it is not hard to set up whenever you set up a new recording. It's in schedule options.

---

### Post by jensk on 2011-08-14
You can set this value via the mythweb interface. 
Go to Settings - MythTV - Settings table. Find the value DefaultEndOffset and set it to the number of minutes that you like to have recorded extra on each recording rule. 
Press Save at the bottom of the screen.

I believe that the extra minutes are only added to rules defined after this setting have been done.

---

### Post by ceejay on 2011-08-14
> **jensk said:**
> You can set this value via the mythweb interface. 
Go to Settings - MythTV - Settings table. Find the value DefaultEndOffset and set it to the number of minutes that you like to have recorded extra on each recording rule. 
Press Save at the bottom of the screen.

I believe that the extra minutes are only added to rules defined after this setting have been done.

Jensk - excellent, thank you very much! I've spent a long time looking for options that aren't there, trying to follow guidance in outdated threads/documentation!!  I hadn't set up Mythweb, but I can see it's a useful management tool as I can keep an eye on what it's up to without getting in the way of anyone watching TV!

I've now set up the defaults I want - it really wasn't reasonable to ask other users to press a bunch of extra buttons every time they set a one-off programme to record.

Thanks again
Ceejay

---

