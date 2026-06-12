---
title: "Re sizing Banshee"
date: 2011-09-08
forum: Multimedia Software
---

### Post by bookcrazy on 2011-09-08
I have just updated to 11.04 (but can't change my personal info because I don't have 50 posts yet) and I'm having problems with banshee.

Here's what happens: I open banshee, I click on a song, and the window maximizes/minimizes so that it spreads across two desktops. 

I have tried uninstalling banshee several times (including purging the ppa) and yet when I reinstall it the same thing keeps happening.

If anyone has any advice I would love to hear it.

Cheers!

---

### Post by coffeecat on 2011-09-08
With the Banshee window minimised, can you get to the bottom right-hand corner to resize it? If you can resize it down to a sensible size and then close the window, it *should* reopen the same smaller size.

If you can't get to the bottom of the window (if it's spilling off the bottom of the screen), position the mouse cursor anywhere within the window, press and hold the alt key, and use left-click and mouse to move it up. Or you can use alt-F7 to tether the hand mouse icon to the window and use the mouse (without clicking) to move the window to be able to get to the bottom-right corner.

---

### Post by bookcrazy on 2011-09-09
> **coffeecat said:**
> With the Banshee window minimised, can you get to the bottom right-hand corner to resize it? If you can resize it down to a sensible size and then close the window, it *should* reopen the same smaller size.

If you can't get to the bottom of the window (if it's spilling off the bottom of the screen), position the mouse cursor anywhere within the window, press and hold the alt key, and use left-click and mouse to move it up. Or you can use alt-F7 to tether the hand mouse icon to the window and use the mouse (without clicking) to move the window to be able to get to the bottom-right corner.
Thank you for your reply! 

I tried to resize it by grabbing the bottom right corner and then just shrinking it but it doesn't work - it just won't get any thinner than about a workspace-and-a-half. 

Do I just need to completely remove banshee and purge all it's settings and how do I do that? 

Cheers

---

### Post by coffeecat on 2011-09-09
> **bookcrazy said:**
> Do I just need to completely remove banshee and purge all it's settings and how do I do that? 

I've just noticed you mentioned a ppa in you OP. Is that for Banshee? Any reason for not using the default Banshee in 11.04?

Create a new account and log into that. Open Banshee and see if you get the same problem. If you do, then it's a problem with the ppa version of Banshee or global settings. If you don't then it's a problem in your personal settings and re-installing Banshee will not help.

To purge your personal settings, you need to search the hidden folders in your home folder for anything Banshee-related and delete them. When you next start Banshee in your account it will open with default settings.

---

### Post by bookcrazy on 2011-09-10
> **coffeecat said:**
> I've just noticed you mentioned a ppa in you OP. Is that for Banshee? Any reason for not using the default Banshee in 11.04?

Create a new account and log into that. Open Banshee and see if you get the same problem. If you do, then it's a problem with the ppa version of Banshee or global settings. If you don't then it's a problem in your personal settings and re-installing Banshee will not help.

To purge your personal settings, you need to search the hidden folders in your home folder for anything Banshee-related and delete them. When you next start Banshee in your account it will open with default settings.
You are a legend! I logged in as a guest and I didn't suffer any of the problems I have been describing so it is definitely in my settings. Now I just need to search them out and delete them. 

Thanks a million for your help with this :D

---

### Post by coffeecat on 2011-09-10
I'm glad to hear the guest account was able to clarify things.

Sorry I was a bit vague about hidden Banshee configurations. That's because I'm a bit vague about exactly where they are. :)

Good luck with that!

---

### Post by bookcrazy on 2011-09-17
Good news bad news:

Bad news: I erased all the documents in my home folder because I typed the command in the terminal wrong (and that is why deja dup is my friend).

Good news: I definitely erased the settings for banshee because it is working just fine now! 

Thanks again for your help Coffeecat!

---

### Post by coffeecat on 2011-09-17
Well - there's a silver lining in the bad news. You've learnt something important from experience, namely that the terminal does what you tell it to do, not what you want it to do! :wink:

I'm glad you've sorted Banshee out. Good luck!

---

