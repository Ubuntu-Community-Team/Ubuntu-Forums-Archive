---
title: "Live TV Annoyance"
date: 2010-10-30
forum: Mythbuntu
---

### Post by uncle hammy on 2010-10-30
I have 3 HDHomeRun units for a total of 6 physical tuners.  I have each physical tuner set up with "Max Tuners" 2 to take advantage of Multi Record (making my total tuners 12).  I Also have Live TV setup to pick the tuner least likely to be used for recording (what ever that setting actually is).

The issue I have is this.  If frontend starts watching live tv, it will use the second tuner of the last HDHomeRun unit.  If a second frontend then starts watching live tv, it will use the "virtual" tuner on the second tuner on the last HDHomeRun unit, effectively locking BOTH frontends to that multiplex.  See the attached mythweb screen shot.  You can see that both livetv sessions are using the same physical HDHomeRun tuner.  Now, I know that all one person has to do is change tuners, however this a WAF thing.

Short of setting all my physical tuners Max Tuners property to 1, can anyone think of a way to have MythTV use a new PHYSICAL tuner for each new live tv session?

[ATTACH]173996[/ATTACH]

---

### Post by nickrout on 2010-10-30
not answering directly, but on either frontend press m (for menu) and then there is a menu item to change cards.

---

### Post by tgm4883 on 2010-10-30
You can either 

A) Set the last tuner (or maybe last 2 tuners depending on how you add it with the hdhomerun) to only have 1 recording at a time

B) When you start livetv, go into the program guide and find a show there, it will change tuners if necessary. I have mine to auto start the program guide when I go into livetv

I would also file a bug if I were you. That sounds like it needs fixed.

---

### Post by nickrout on 2010-10-30
> **tgm4883 said:**
> You can either 

A) Set the last tuner (or maybe last 2 tuners depending on how you add it with the hdhomerun) to only have 1 recording at a time

B) When you start livetv, go into the program guide and find a show there, it will change tuners if necessary. I have mine to auto start the program guide when I go into livetv

I would also file a bug if I were you. That sounds like it needs fixed.

Actually the fix is well documented.

1. in mythtv-setup delete all tuners

2. then add them one at a time with only ONE virtual tuner per real tuner.

3. Then go through and change each one to having 2 virtual tuners.

The secret is the order in which they are created. This has been dealt with in the mailing list many times.

---

### Post by tgm4883 on 2010-10-30
> **nickrout said:**
> Actually the fix is well documented.

1. in mythtv-setup delete all tuners

2. then add them one at a time with only ONE virtual tuner per real tuner.

3. Then go through and change each one to having 2 virtual tuners.

The secret is the order in which they are created. This has been dealt with in the mailing list many times.

Thats the fix :confused:. Ok, yea that works, but it's more of a workaround than an actual fix I would say. Seems like the backend should be able to take livetv requests and only provide them virtual tuners if they are VT1 rather than VT>1. 

What do you do in multiple backend environments?

:EDIT:

Although to be honest, I still prefer the program guide way to the one that I stated above. Would be better if when browsing the channels in LiveTV not though the program guide that it didn't stick to only the channels that the tuner you are on has.

---

### Post by nickrout on 2010-10-30
> **tgm4883 said:**
> Thats the fix :confused:. Ok, yea that works, but it's more of a workaround than an actual fix I would say. Seems like the backend should be able to take livetv requests and only provide them virtual tuners if they are VT1 rather than VT>1. 

What do you do in multiple backend environments?

:EDIT:

Although to be honest, I still prefer the program guide way to the one that I stated above. Would be better if when browsing the channels in LiveTV not though the program guide that it didn't stick to only the channels that the tuner you are on has.

Your point has been made a number of times. Theres more to it han livetv, it's to do with scheduling etc etc. 

The menu button|switch tuners (or is it cards?) is stil the quickest way.

---

### Post by uncle hammy on 2010-10-30
Thanks for the inout folks.  I will probably go the delete / re-add route.  Now that you mention it, I did delete / re-add them a while ago for something else (which I can't remember why at this point), and I set them all to max tuners "2" while adding them in.

---

