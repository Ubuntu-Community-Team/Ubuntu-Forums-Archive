---
title: "Problems with TV Tuner backend setup"
date: 2010-12-30
forum: Multimedia Software
---

### Post by Researcher1 on 2010-12-30
I just installed Mythubuntu 10.10 on my HP Media Center PC 800 desktop.

When I first accessed the backend setup it showed something like a 4VL capture card but I am not sure that is the correct card.  When I use the frontend to watch TV I get a message indicating no TV capture card is setup.

Is there some simple way to know what settings I should use in the Backend setup for 

1. Capture Cards 
2. Video Sources
3. Input connections

I have read the [http://www.mythbuntu.org/wiki/mythbackend-setup](http://www.mythbuntu.org/wiki/mythbackend-setup) guide but I still am not sure what to do.  

I have a simple basic cable package with analog channels 3-99.

I would think there is some terminal command that I can use to tell me the model and chipset of my TV capture card but I can't seem to find any that give me the info I need.

Any help you can give is greatly appreciated.

---

### Post by Researcher1 on 2010-12-31
Here is a bit more detail about my HP PC 800.

It is actually a 863n model with a TV Tuner card that I suspect was assemble by a third party for HP.  The detail on the card shows the HP part number as MAHP-01-000-Rev 1.01 with an Assembly number of MAU-01-000 REV 2002.  So the card is at least 8 years old.  The card itself looks like it has at least one part that was made by Phillips which is the Coax adapter.

The Backend setup shows the first possible Card Type choice as a Analog V4L capture card and this looks like it would be the best choice.  But the Video device field displays as blank and the Probed Info displays "Failed to Open"

I now have kept the Analog V4L as my Card Type but when I go into Watch TV on the frontend I get a message that the system is not able to display anything and it is using all input devices.

Since there are over 100 different input fields to use in setting up the backend server I am not very hopeful that I will ever solve this problem.  If someone knows a better approach to solving this issue, please let me know.

I fear it will be something like "You have to buy a more recent capture card" and if that is the solution I would love to hear about your experience in setting up one that can easily be auto detected and all of these fields would magically display the correct values.

Thanks in advance for any help you can give.

---

