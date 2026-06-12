---
title: "Sill issues with pvr-150 LP suspend/resume"
date: 2009-03-12
forum: Mythbuntu
---

### Post by rodercot on 2009-03-12
Well I though I had this all figured out, but after it being susended for a couple days upon waking up it grabs the tuner in the master instead of it's local tuner in the slave b/e.
 
 I use pm-suspend with a module file in /etc/pm/config.d for supending and resuming the card. I have tried "ivtv" upon testing a couple maybe three times in a row, this works fine, but if the machine is asleep even more than 1 hours ans tries to wake up, info says that tuner 4 is not available. 
 
 I have also tried "v4l2_common" it works well at least when i wake up the system it says the card is "Not Recording" but trying to view live tv just bounces back to the main menu.

 I have to reboot the system to get the card back to full working state.

 I am  wondering if this is a persmissions issue, I have edited the sudoers file and added

 user ALL=(ALL)NOPASSWWD: /usr/sbin/pm-suspend

 My config files that I have created are actually in /etc/pm and when I check the log files I see no errors with any of the suspend or resume scripts I created or the hooks created by default. I am wondering if I need to add /etc/pm* to the list above in the sudoers file.

 Dave

---

### Post by Barry_IA on 2009-11-24
Dave:

FWIW I'm having a similar problem with a HVR-2250 card.  Combination here is an HVR-1600 (tuner 1) with the HVR-2250 (tuners 2 and 3).  If all three tuners record concurrently the 2250 card does not record and I see the "asleep" message.  If only the first two tuners are recording I don't have any problems,

I didn't see any replies to your post; have you found any resolution to this problem?

---

