---
title: "Preventing Rhythmbox opening by default when MP3 Player connected"
date: 2008-06-10
forum: Multimedia Software
---

### Post by doughnuts64 on 2008-06-10
I am not a fan of Rhythmbox, and have not been using it a whole lot, but with Ubuntu Hoary, Exaile stopped working, and I have not been able to bring it back to life.

Also with Hoary, if I connect a USB device, it automatically loads the application associated with it, so when I connect my MP3 player, Rhythmbox opens. If I am already listening to music, playback stops, and the application lists the files on the MP3 player. All I want to do is charge it. I cannot unmount the device without quitting Rhythmbox completely. I am sure that you will see this is annoying for me.

Does anyone have any ideas of how to stop it loading Rhythmbox, and instead loading Nautilus or something? I have searched the forums and Google, but to no avail!

Thanks!

---

### Post by spyckotic on 2008-08-09
Yeah this was very annoying to me as well. Never use Rhythmbox and it constantly would open up and start loading tracks from my mp3 player.

Uninstall Rhythmbox.... problem solved

---

### Post by cawpin on 2008-08-09
I am still trying to figure this out. I have no multimedia tab on my Removable Drives & Media preference pane as I did when I used 7.10. How do you change the application that launches when you connect an iPod or other mp3 player? It isn't the Preferred Applications preference so don't quote that. It used to be on the Multimedia tab under the app Media Players. This option is no longer there.

---

### Post by OutOfReach on 2008-08-09
Goto System>Preferences>Preferred Applications
Then goto the Multimedia tab and select the media player from the dropdown list.
If the media player is not listed there select Custom from the drop down menu and then in the 'Command' text box, type in the command to start the app, for example 'banshee'

---

### Post by diwas on 2008-08-14
If i dont want any media player to open...what should i do??? It is indeed very very annoyin by the way.

Similarly, the Photo manager loads up...when it is connected. (Iam talking about  the memory card of my cell phone).

I want to prevent both from loading automatically.

---

### Post by altonbr on 2008-08-14
I think I saw a screenshot of them trying to fix this for Intrepid, but I can't confirm this.

---

### Post by fbianconi on 2008-08-16
I'm not sure what solved this for me, what I did was leave the textbox in preferred apps blank and disable rhythmbox ipod plugin, now the icon is displayed as a hard disk, and when I plug it nautilus shows up.

edit
nope false alarm there's rhythmbox again.

edit2
this solution is ugly, but in gconf editor there's a boolean key /desktop/gnome/volume_manager/autoipod 
set it false and that's it.

---

### Post by mc4man on 2008-08-16
The default action for mp3 player ( and other media) is set in file management -> media. Either enable it (file management) in edit menus -> preferences or go places -> home folder -> edit -> preferences -> media. 
The 3rd one down controls ipod's ect.  Set it to do nothing. Worst case hold down shift on keyboard and you'll get choice.

See screen (set to open amarok (amapod)

---

### Post by montoya_007 on 2008-11-02
> **mc4man said:**
> The default action for mp3 player ( and other media) is set in file management -> media. Either enable it (file management) in edit menus -> preferences or go places -> home folder -> edit -> preferences -> media. 
The 3rd one down controls ipod's ect.  Set it to do nothing. Worst case hold down shift on keyboard and you'll get choice.

See screen (set to open amarok (amapod)

It worked perfectly for me! 
Browse home, click Edit-> Preferences in the menu and in the Media tab set your preferred action for music players.

Thank you!!

---

### Post by stripey on 2009-01-26
> **montoya_007 said:**
> It worked perfectly for me! 
Browse home, click Edit-> Preferences in the menu and in the Media tab set your preferred action for music players.

Thank you!!

I have tried this and i the computer is ignoring everything i tell it to do!
Any suggestions why?

---

### Post by stripey on 2009-01-26
> **stripey said:**
> I have tried this and i the computer is ignoring everything i tell it to do!
Any suggestions why?

OK regarding the last post I made, I had seen the same instructions on another forum telling you to perform those steps from nautilus. This is the problem, I have just done it as a normal user and it worked perfectly.

:)

kt

---

