---
title: "How can I get my system tray icons reset to the original set up?"
date: 2009-06-02
forum: Networking &amp; Wireless
---

### Post by coober85 on 2009-06-02
How can I get my system tray icons reset to the original set up? [SOLVED]

I accidentally removed the sys tray icon for wireless internet. How do I get it back? and while you are answering that, how do I get the noatun sys tray icon to reappear? I accidentally removed that too, and now when I use noatun, the only way I can quit the program is to go into the system monitor and do an "end process" for noatun. if I just close the noatun window the audio keeps right on going like nothing even happened.

thank you!

---

### Post by stilling on 2009-06-03
> **coober85 said:**
> How can I get my system tray icons reset to the original set up?

I accidentally removed the sys tray icon for wireless internet. How do I get it back? and while you are answering that, how do I get the noatun sys tray icon to reappear? I accidentally removed that too, and now when I use noatun, the only way I can quit the program is to go into the system monitor and do an "end process" for noatun. if I just close the noatun window the audio keeps right on going like nothing even happened.

thank you!



 
1. # rm -r ~/.gconf/apps/panel or just move the folder elsewhere if you want to back it up. Try better to back it up thinking that you are on gnome.
# Log out of GNOME, then back in.

2. if the first those not work 
restart X, 
then in console: gnome-session-remove gnome-panel
gconftool-2 --recursive-unset /apps/panel
gnome-panel &

---

### Post by coober85 on 2009-06-03
> **stilling said:**
> 1. # rm -r ~/.gconf/apps/panel or just move the folder elsewhere if you want to back it up. Try better to back it up thinking that you are on gnome.
# Log out of GNOME, then back in.

2. if the first those not work 
restart X, 
then in console: gnome-session-remove gnome-panel
gconftool-2 --recursive-unset /apps/panel
gnome-panel &

Thank you for your quick response, but I have no clue what you are talking about. can anyone put this into english for me? also it seems like you are assuming I have the original back up file. I don't

I don't speak linux beyond "sudo apt get install".

---

### Post by pastalavista on 2009-06-03
> **coober85 said:**
> Thank you for your quick response, but I have no clue what you are talking about. can anyone put this into english for me? also it seems like you are assuming I have the original back up file. I don't

I don't speak linux beyond "sudo apt get install".
RIght-click the panel where you want the app to be and select "Add to Panel" and in the list, select "Notification Area" and click add.

---

### Post by coober85 on 2009-06-03
> **pastalavista said:**
> RIght-click the panel where you want the app to be and select "Add to Panel" and in the list, select "Notification Area" and click add.

Haha, I just figured that out myself and was coming here to post the solution! yeah for anyone confused, it will give you notifications for EVERYTHING! banshee player, wireless internet connection, whatever. 

Man I've been looking for that for about a year... like I said, Noatun's whole menu works through the system tray icon (at least the way I had it set up), so if you can't see the tray icon, you can't even pause the video/audio file or turn off the player!

Thanks for your quick response as well Pasta!

---

