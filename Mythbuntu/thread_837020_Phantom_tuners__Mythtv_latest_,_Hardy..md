---
title: "Phantom tuners ? Mythtv latest , Hardy."
date: 2008-06-22
forum: Mythbuntu
---

### Post by drifting on 2008-06-22
Hi.
My backend server has become rather a frankenstein, it must be on it's 3 OS upgrade as well as many of bolt on's. Now this is not really a problem as the old girl works really well, and has upward of 1TB of recoded TV sitting there waiting for me to get round to watch it! 
Anyway, back to the problem. For some unknown reason under myth tuners it has only two showing (Nova-T 500) which is fine. However on the myth information page on the any front end it has them listed as tuners 3 & 4 ? what happened to 1 & 2 ? It used to list them as 1 & 2 but somewhere in my upgrading frenzy it seemed to get it's knickers in a twist. What is concerning me is that I will be ditching the Nova-T 500 (Lousy Freeview signal) And going over to two Freesat based Hauppauge. And wondered if I might mess things up with the tuner order ? No idea why it should do this, wonder where it has stored the info for the none existing ones ?


Regards Paul.

---

### Post by jb5 on 2008-06-23
OK - I can't comment on all your questions/problems, but....

I had some trouble getting the virtual tuners to work on a nova-t-500, in my numerous attempts I deleted the tuners and re-configured them in the BE setup. 

As a consequence I am now on tuners 9,10,11 & 12 as seen in myth FE!  So this type of behaviour is replicated in my setup, and thus hopefully 'normal'.

Certainly my machine functions properly now and the virtual tuners work well. So with luck when you replace your dvb-t card with a dvb-s card it will work as expected.

---

### Post by bah1976 on 2008-06-23
I'll add my two cents - the tuner number doesn't mean much of anything, as long as the number is unique.  One of the tables in the database has the cards listed, and each subsequent add/delete of card increases the index by one.  In fact, after messing around with my tuner setup to get it just right, my tuners are 29 & 31. (I had to edit the table manually in order to get my kworld115 to be able to use both the ATSC & the QAM input) They don't even have to be sequential.  The cardinput is then linked to that card by that number, and then the schedule is further linked to the input.

So there's no cause for worry if the numbers aren't 1 & 2 - as long as they are there and unique.

---

### Post by drifting on 2008-06-24
Thanks guys much appreciated. Now all I need to find is a guide on how to install the Nova-S's for UK FreeSat :-)

Regards Paul.

---

