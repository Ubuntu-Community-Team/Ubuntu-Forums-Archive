---
title: "Full screen flash video in Firefox - screensaver popping up"
date: 2008-11-02
forum: Multimedia Software
---

### Post by 1awesomeguy on 2008-11-02
Every time I play videos on websites like hulu.com in full screen mode, my screensaver pops up. I then need t get up off my bed and move the mouse (oh the drama... I know, but every ten minutes gets annoying). I can change my screensaver settings to to make it only go off after 120 minutes or more, but then I feel as there is almost no point to the screensaver.

Any suggestions or is this a technical issue with my computer?

Thanks in advanced.

---

### Post by mikeym on 2009-01-06
Hi, I'm having exactly the same issue. 

I found this [thread]("http://ubuntuforums.org/showthread.php?p=6318328#post6318328") but I would like it to work without a manual 'fix'.

Any ideas out there?

---

### Post by mikeym on 2009-01-06
Sorry double post!

---

### Post by lodp on 2009-02-15
I agree, this is annoying. Is this an issue with the Adobe Flash Player? Other applications seem to be able to suppress the screen saver just fine, when running full-screen.

---

### Post by 1awesomeguy on 2009-10-08
Many months later, I still have not been able to find a good solution to this problem. Hopefully the new Ubuntu will fix it automatically :)

---

### Post by erilidon on 2009-12-15
This is still an issue in 9.10, and I would like to see something done about it as well. Like you said the main time it is annoying is when watching videos on hulu. This is a matter of the mouse just not being moved, not a flash application issue and someone earlier had asked.

I remember having some issues with this while running windows 95 and some one had come up with a program that would make the computer think someone was moving the mouse or pressing a key on the keyboard every few mins, it worked.

But I think the simplest way would be to somehow tell the computer not to turn on the screen saver if a full screen app is running, or for me just if flash is running.

---

### Post by lodp on 2009-12-15
> **erilidon said:**
> But I think the simplest way would be to somehow tell the computer not to turn on the screen saver if a full screen app is running, or for me just if flash is running.

That's what's happening if you play a video full-screen in some application other than flash (like mplayer or vlc). It suppresses the screen saver. Flash doesn't.

Does anybody have a clue what package we have to file a bug for to get this fixed? I've known the problem since back in '06 when I switched to ubuntu.. it just never received any attention.

---

### Post by Dennis N on 2009-12-15
You can set the time before screensaver kicks in.

System > Preferences > Screensaver

Adjust slider at: "Regard the computer as idle after:" to the desired number of minutes (probably want an hour or more).

---

### Post by lodp on 2009-12-15
Yeah.. but you lose a lot of the energy saving potential by having the setting that high. I think 5-10min is a typical good value. I hardly have the computer idle for longer than 45min - I set it to sleep or switch it off in those cases.

I suspect that flashplayer is just missing a feature that other media players have (i.e. the ability to communicate with the screensaver and prevent it from being triggered when playing fullscreen).

---

### Post by Charkel on 2009-12-23
> **erilidon said:**
> This is still an issue in 9.10, and I would like to see something done about it as well. Like you said the main time it is annoying is when watching videos on hulu. This is a matter of the mouse just not being moved, not a flash application issue and someone earlier had asked.

I remember having some issues with this while running windows 95 and some one had come up with a program that would make the computer think someone was moving the mouse or pressing a key on the keyboard every few mins, it worked.

But I think the simplest way would be to somehow tell the computer not to turn on the screen saver if a full screen app is running, or for me just if flash is running.

Yup still an issue :( Same thing with auto sleep of display.
Someone should write some script that automatically moves the mouse a few pixels every 9 minutes :) (I would but I'm not familiar with Linux programming)

---

### Post by Seamyst on 2009-12-31
I have this problem with VLC in Karmic, too.

---

### Post by alopex on 2010-07-10
I realize this is an old thread, but this affects me too using Ubuntu  Lucid Lynx 10.04. This bug made me turn off my screensaver: not the  optimal/desired solution at all! 
I can confirm that this bug only appears in the flashplayer's fullscreen  mode. 
Does anybody know whether this is a bug in GNOME or in flashplayer?  Where can I file a bug report?

/alopex

---

### Post by erilidon on 2010-07-10
> **alopex said:**
> I realize this is an old thread, but this affects me too using Ubuntu  Lucid Lynx 10.04. This bug made me turn off my screensaver: not the  optimal/desired solution at all! 
I can confirm that this bug only appears in the flashplayer's fullscreen  mode. 
Does anybody know whether this is a bug in GNOME or in flashplayer?  Where can I file a bug report?

/alopex

I too have resorted to turning the screensaver off all together. I just fond this, but have not yet tried it

[http://www.ubuntu-inside.me/2009/03/howto-disable-screen-saver-while-flash.html](http://www.ubuntu-inside.me/2009/03/howto-disable-screen-saver-while-flash.html)

---

### Post by alopex on 2010-07-11
It says
> Before the start, you should know that, this is not only for youtube  video, this is for all kind of flash including the advertisements.So do  not forget to close firefox or be sure there is no flash at that page  before going out etc  : )

Quite a dirty hack in that case. But the comments suggest different solutions. Please let me know if that workaround worked for you. 

Meanwhile, I found this bug report on Adobe from November 2008. That bug report doesn't seem to get any attention at all. 
[https://bugs.adobe.com/jira/browse/FP-997](https://bugs.adobe.com/jira/browse/FP-997)

I wasn't able to find a GNOME bug report on this and I still wonder whether this is an issue in the flashplayer itself or in the GNOME screensaver. Maybe someone can help on this? 

/alopex

---

### Post by erilidon on 2010-07-25
> **alopex said:**
> It says


Quite a dirty hack in that case. But the comments suggest different solutions. Please let me know if that workaround worked for you. 

Meanwhile, I found this bug report on Adobe from November 2008. That bug report doesn't seem to get any attention at all. 
[https://bugs.adobe.com/jira/browse/FP-997](https://bugs.adobe.com/jira/browse/FP-997)

I wasn't able to find a GNOME bug report on this and I still wonder whether this is an issue in the flashplayer itself or in the GNOME screensaver. Maybe someone can help on this? 

/alopex


It couldn't get it to work correctly. Just kept the screensaver off all together - even when I was done watching flash movies. I don't see it as a solution, does the same thing as disabling the screensaver manually.

I have switched my main computer to Windows 7 now - for this and the fact that Linux does not have good silverlight support which is needed for netflix.

I would be more interested in ubuntu if these were added. Let me know if you do find a fix for the flash issue though as I still run ubuntu on my laptops.

---

### Post by lodp on 2010-07-25
Yeah. This bug or 'missing feature' has annoyed me since 2005 when I first ran ubuntu. At this point I'm just waiting for Flash to die.

Here's something that might cheer you up:

[IMG]http://imgs.xkcd.com/comics/command_line_fu.png[/IMG]

---

### Post by ytsurk on 2010-08-07
run this command in the terminal

> gnome-screensaver-command -i

or even add it to your panel,
right click
add custom application launcher
choose type applicaiton in terminal
name it,
type the command in there
choose a nice icon !

---

### Post by exactt on 2010-11-10
Just for the record:

[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/120896](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/120896)

---

