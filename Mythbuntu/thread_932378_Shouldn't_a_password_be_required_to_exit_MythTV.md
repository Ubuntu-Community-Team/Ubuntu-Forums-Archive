---
title: "Shouldn't a password be required to exit MythTV"
date: 2008-09-28
forum: Mythbuntu
---

### Post by Caps18 on 2008-09-28
This isn't a problem with my system since I'm the only one with access to the computer in my house.  But, is it a problem if I can exit without giving my password, but if I want to get to mythbuntu through the setup menu, I have to enter my password.

I do have to enter my password to run the control center either way, and that may be why going through the setup menu asks for my password.  

Or is there a setting hidden away to turn on this password that I have missed?

Or is this a issue that is pointless since there would be other ways to get a terminal prompt besides these two methods?

---

### Post by tgm4883 on 2008-09-28
Pointless.  There are other ways to get a terminal, not that it matters cause you still need the password to do anything detrimental.  You shouldn't need a password to start the mythtv frontend though.

---

### Post by t3chn0b0y on 2008-10-25
when someone can continously press the esc key to exit the
frontend, and the frontend is in the main room where little
hands etc can get a hold of it, and one doesn't have a keyboard &
mouse attached too it, then i would see a need for a password to
exit.. So I would have to agree with the first post in stating 
that there should be a password requirement to get out & there
is numberous other area's I would like to see passwords also.
perhaps the digits to level 4 could be used...

---

### Post by tgm4883 on 2008-10-26
> **t3chn0b0y said:**
> when someone can continously press the esc key to exit the
frontend, and the frontend is in the main room where little
hands etc can get a hold of it, and one doesn't have a keyboard &
mouse attached too it, then i would see a need for a password to
exit.. So I would have to agree with the first post in stating 
that there should be a password requirement to get out & there
is numberous other area's I would like to see passwords also.
perhaps the digits to level 4 could be used...

Don't forget if the frontend ever crashes.  I'd recommend setting a key on the remote (like the power key) to start mythfrontend.  I can show my code that does that if requested.  If you still think that a password to exit is necessary please fill out a blueprint (feature request) at [https://blueprints.edge.launchpad.net/mythbuntu](https://blueprints.edge.launchpad.net/mythbuntu)

---

### Post by volkswagner on 2008-10-26
God no.  It is an appliance.  I hate having to enter my password as it is.  I ended up changing it (password) to all numbers, so I can easily enter it from the remote.  I think the confirmation to exit is adequate (for accidental exits).

What can go wrong if Mythfrontend exits anyway?  The next user will be forced to start it?

Often, since I am not running MythWelcome, I like to exit mythfrontend without turning on the display.  With a few remote key strokes, I can exit mythfrontend, and let the machine auto shutdown.  I don't want to short cycle the TV display (power on/power off).

My $.02

---

### Post by KillerKiwi on 2008-10-27
You could just change the exit to no key, if you want to exit then you need to turn it back on under settings.

That will work fine if you dont have a keyboard attached

---

### Post by fryed_1 on 2008-10-27
I changed the exit key to something that was on the keyboard, but not reflected on the remote.

I have wireless keyboard and mouse that spends most of it's time in a drawer under the TV, so the chance of something going wrong and exiting out because of unintentional keypresses is very slim.

---

### Post by issih on 2008-10-27
Does it really matter? the backend will still record anything its meant to, thats the point of the client server architecture. All it means is you have to restart the front end to view tv, if that is keyed to a button on the remote then that seems fine to me...am I missing something?

---

### Post by Caps18 on 2008-10-28
> **issih said:**
> am I missing something?

I was looking at this from a security perspective if I set this type of system up outside of my house.  For instance, if I set this up at my parents house, I wouldn't want them to be able to exit Mythbuntu (although they should be able to shut down the system a little easier than ctrl-alt-delete -> shutdown).  If I used this a few years ago in college, I wouldn't want my roommates to be able to adjust any settings or exit out of Mythbuntu unless they had a good reason too.

I know that it doesn't need to be secure for everyone, I'm the only person at my house... but I could see where making it a little more secure might be beneficial in some cases.  

(The alt-tab feature would also have to be disabled since the desktop appears for a few seconds on boot-up and is long enough to open another window)  I use that trick a lot right now to prevent entering my password when I need to get to the file manager or terminal.

---

### Post by t3chn0b0y on 2008-10-29
Quiet a few tips here from removing the exit from the remote, making it so its just associated with the keyboard.. those two seem to be the quickest means to fix the
situation, and the easiest to put back if one chooses too.. thanks..

---

### Post by Archmage on 2008-10-30
How about changing the exit option to shutdown/reboot only?

---

