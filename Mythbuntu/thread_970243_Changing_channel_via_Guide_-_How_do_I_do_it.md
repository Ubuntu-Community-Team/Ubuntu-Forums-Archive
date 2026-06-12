---
title: "Changing channel via Guide - How do I do it?"
date: 2008-11-04
forum: Mythbuntu
---

### Post by hozhead on 2008-11-04
Can anyone tell me what configuration or setting to change so that I can go to a channel from the guide (instead of going to the recording options) by clicking the "OK" button on an MCE remote?

I've been able to edit the lirc files and MythTV button mappings to get most of the buttons working the way I want but I absolutely cannot click "OK" to change the channel.  I've removed the check for "use select to change channels in the program guide" in the configuration and yet it still goes to the recording options.

---

### Post by SiHa on 2008-11-04
AFAIK the only way to do this is to go to Watch TV, then bring up the EPG from within that - I think the key is 's'. The EPG available from the menus is just for scheduling recordings.

If you look at the keybindings in the 'Edit Keys' setup, I think there is a jumppoint that you can define a key for that will take you straight to 'EPG within Live TV', or something like that. If you have a remote with a 'Guide' button, you could map this to the jumppoint, then it would always take you there, whether you are watching TV or not.

---

### Post by hozhead on 2008-11-04
First off, THANK YOU for pointing me in the right direction!


I did have the guide button on my remote set to be the equivalent of clicking "S" to reach the guide [EPG] but I was unaware that there are two separate guides for scheduling and for viewing.

The two jump points are "Live TV in Guide" and "Program Guide".  I was using the "Program Guide" jump point and have switched to "Live TV in Guide" instead.  
This actually addressed another item I was looking to address which is to continue watching live tv while viewing the guide though I still need to address linking the Live TV sessions together to allow for rewinding prior to clicking the guide button if I didn't actually change the channel.


Edit: It now occurs to me that the reason for two guides is because of the backend/frontend roles.  The scheduling guide is for the master backend to handle the tuner schedule for all backends and the other guide is for selecting channels on the front end.

---

