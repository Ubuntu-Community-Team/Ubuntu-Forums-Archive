---
title: "Couple of issues"
date: 2009-06-09
forum: Mythbuntu
---

### Post by kadafi69 on 2009-06-09
The first problem is, when I choose to exit I get the exit menu with several options: No. Yes, Exit Now. Yes, Exit and Reboot. Yes, Exit and Shutdown.

The problem is, when I choose the option to 'Yes, Shutdown' it just takes me to the desktop. The other options work fine. As far as I can tell my settings are all correct.

The second issue is, when I start the music player, it always starts with the 'Active Playlist Que' but I would like it to start with the Active Directory. I cant seem to find any option for this.

Thirdly, I have a Streamzap Remote. It just plugged in and pretty much worked straight away. However, I have noticed 4 of the buttons arent working, these being the skip forward/backwards and fast forwards/backwards.

Any ideas on how to resolve these problems?

---

### Post by ian dobson on 2009-06-09
Hi,

1) You need to configure the shutdown command to be issued by myth-frontend and add the user thats running myth-frontend to the sudoers list for that shutdown command. 
Use visudo to edit the file. 
Have a look here:- [http://www.gossamer-threads.com/lists/mythtv/users/333865](http://www.gossamer-threads.com/lists/mythtv/users/333865) for more info.

2) I don't play music from my frontend so I'm not sure.

3) You should be able to reprogram the actions to be performed on for the "missing" keys. I'm note quite sure were it is, but theres a configuration file for lirc that lists applications/functions to be called.

Regards
Ian Dobson

---

