---
title: "different  playback settings on remote frontend"
date: 2010-03-11
forum: Mythbuntu
---

### Post by My Name on 2010-03-11
This one I wasn't expecting.
I have an acer revo that can utilise VDPAU on it nvidia card. but I use a combined frontend/backend that doesn't have this capability.
I was surprised to see that the settings on the remote frontend, have been implemented on the combined frontend/backend.
Is there a way of keeping these playback setting separate?

---

### Post by SiHa on 2010-03-11
They should be separate.

Don't suppose these two have the same hostname? Stuff like this is all stored in the mysql database under the hostname. 

I hadn't appreciated quite how useful this was until I re-installed my remote FE, and all my settings were still there, because I kept the same name.

---

### Post by timconradinc on 2010-03-11
Go to Setup->General->Next->Database Configuration (2/2)

Check the box 'Custom Identifier for Frontend Preference', and a text box will appear. Enter the name you wish to use for the front end.

I found it easier to do this on both of my Front Ends, not just the one that's only a front end.

---

### Post by My Name on 2010-03-12
> **timconradinc said:**
> Go to Setup->General->Next->Database Configuration (2/2)

Check the box 'Custom Identifier for Frontend Preference', and a text box will appear. Enter the name you wish to use for the front end.

I found it easier to do this on both of my Front Ends, not just the one that's only a front end.

This fixed it thanks.

Ah Simon, my guardian angel. You missed it this time but you have another chance... I have more queries...:D

---

### Post by SiHa on 2010-03-12
> **My Name said:**
> This fixed it thanks.

Ah Simon, my guardian angel. You missed it this time but you have another chance... I have more queries...:D

:p

---

