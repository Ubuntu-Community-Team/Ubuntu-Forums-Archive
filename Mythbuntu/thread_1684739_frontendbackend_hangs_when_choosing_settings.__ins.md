---
title: "frontend/backend hangs when choosing settings.  installed from 10.10"
date: 2011-02-09
forum: Mythbuntu
---

### Post by TorgnyHellstrom on 2011-02-09
Hi,

I made a fresh install of Mythbuntu 10.10 64-bit and was on my way making things work. TV was duplicated and no sound but it is on its way... However, I tried to change to another theme to make it work more nicely with my old 4:3 LCD monitor. But after my change to that theme I cannot get in to the settings in the frontend or the backend. MythTV hangs. I can stop the freezing with ESC and choose another menu-item. But as soon as I try to enter the Settings Menu it freezes again.

Is there a way to change the theme via command line or is there another way to solve this problem? Except reinstalling everything...

My hardware is:
AMD 64 
1 Tb SATA HD
TV: Sundtek Media TV pro USB stick (use the analog reciever)
Graphics: ATI Sapphire HD 4550

All kinds of ideas and suggestions are very appreciated. 

/Torgny

---

### Post by wyliecoyoteuk on 2011-02-09
Are you sure that it froze, or was it just processing?
Some themes take quite a while to prerender the first time, depending on processor and memory etc.
Perhaps you could uninstall the themes from the Mythbuntu control centre.

---

### Post by TorgnyHellstrom on 2011-02-10
First, thanks for the reply so far. I really appreciate all ideas, and suggestions.

I made some more digging and it isn't working, it just stops. But I managed to make it in to the settings for the frontend and the backend. It was a lucky guess, but here is what I did:
I clicked CTRL+ALT F4 to change to TTY4 so I could get a terminal and see if I could change anything even if the mythTV menu was frozen.
When i Changed back to TTY7 (graphical MythTV-frontend) the menu had popped up.

So, whenever it froze i just changed TTY and back again and then I was in the menu and could do all the editing.

But the original problem do persist although I changed the theme. So when I open the frontend and enter  
Utilities/Setup - Setup. If I choose General or Apperance there, it "freezes". But I can, as mentioned above, enter the menu if I go to another TTY and back again.

It seems a little weird. I have checked the settings I made and tried to change everything to default or Standard, but no luck.

May it be a graphics problem? Any Ideas about how to go further?

EDIT: I Forgot to mention, I did try to uninstall the themes from Mythbuntu Control Centre, but it did not change anything, so I reinstalled it again. And everything did work in the beginning.

---

### Post by nickrout on 2011-02-10
The ATI cards have never been a favourite of mythtv.

To change the theme on startup, try running:

> mythfrontend -O Theme=Arclight  (or whatever theme you wish to use)

---

### Post by Gebakmans on 2011-03-03
Hi,
 
I have exact the same problems. Also 10.10 and an Ati 4870 card.
Is there any solution on this?
 
Thanks

---

