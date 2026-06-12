---
title: "Problems due to upgrading XGL Compiz"
date: 2006-09-05
forum: Multimedia &amp; Video
---

### Post by suhaib on 2006-09-05
**EDIT:  Sorry, maybe this should've been posted in the Desktop support section.**

I recently installed XGL Compiz and I must say, it's effects are great!

However, today I was prompted to install some updates for it, so I accpeted them.  After the update/upgrade process had completed.  I was left with some problems.

1)  I cannot enter the text-based console, that is, when you hit ctrl + alt + f1-f6.  What happens is the screen appears black, I can't see nothing.  So I just hit ctrl + alt + f7 to exit.

2)  My XGL Compiz effects have dissapeared, Ubuntu is how it use to be! I didn't expect updates to disable the package lol.

3)  Whenever I open an app or folder, the tool and menu bars don't appear.  So I can't minimize/maximise or quit anything.  I can only use the alt + f4 method of closing programs.

Can anyone kindly help me with the matter.  has this happened to anyone before in the past?

All help/information is highly appreciated as always.

Thank you!

---

### Post by cneil on 2006-09-05
The exact same thing has happened to me.
Control+alt+backspace still seems to work.

---

### Post by suhaib on 2006-09-05
Wow.  I forgot that shortcut.  I tried restarting the Xserver but everything was just black.  Had to manually kill my laptop's power.

This is strange.  Hopefully a solution will come quick.  What happened when you pressed ctrl + alt + backspace?

---

### Post by cneil on 2006-09-05
your computer gets a login terminal.

---

### Post by suhaib on 2006-09-05
> **cneil said:**
> your computer gets a login terminal.

Well that's a start!

So what method did you use to install xgl and compiz?

---

### Post by cneil on 2006-09-05
I don't know if this will work on your computer, but I found a fix on mine. 
Go to System>Preferences>Sessions>Startup Programs and then click edit.  
Change "startcompiz" to "compiz-start".  It was pretty easy.

You might have to login and do a regular gnome session instead of an XGL session. Also, if you can't get to a terminal because your desktop program doesn't work, right click on your desktop and click create launcher.  Type "bash" into all of the panes and it will bring up a terminal for you.
From there you can do sudo apt-get update and upgrade and it will help get your computer working again.

I hope some of this helps.

---

### Post by suhaib on 2006-09-05
Ok thanks, I'll try this when I boot Ubuntu.  I'm using XP right now, but I'll give you feedback on what the outcome is.

Thanks again.

---

### Post by shat on 2006-09-05
Thanks cneil, I had this problem too and changing /usr/bin/startcompiz to /usr/bin/compiz-start was a perfect fix (and installing the new packages).

Thumbs up!:KS

---

### Post by TasKiNG on 2006-09-05
Worked for me -Thanks
Using Kubuntu 6.06

I just start in kde now and then run compiz-start

Just got to try and stop my start menus wobbling now.

---

### Post by emarcellus on 2006-09-06
Thanks. That change worked for me too. Also my workspace switcher was broken. Now all is well. 
Any idea why the updates broke xgl?
I do not recall how I installed xgl.
Is one install method better than another?

Thanks
Ed

---

### Post by aluxito on 2006-09-06
I'm upgrade compiz packages too, but i have some troubles:

1) all my plugins configurations dissapears, i don't have anything in /apps/compiz (gconf-editor)
 
2) when i tryed to activate GL -Desktop in tray icon i only get windows with no borders and none plugin effect.

3) after a lot of hours, i get some results doing this: i put in System -> Preferences -> Sessions /usr/bin/compiz-start in the startup programs tab (due to changed in the main script, i think)

4) after all that above mentioned, aparently, all go well, but al effects are VERY SLOW. my old configuration was perfect (it was working very good). ](*,)

---

### Post by suhaib on 2006-09-06
> **cneil said:**
> I don't know if this will work on your computer, but I found a fix on mine. 
Go to System>Preferences>Sessions>Startup Programs and then click edit.  
Change "startcompiz" to "compiz-start".  It was pretty easy.

You might have to login and do a regular gnome session instead of an XGL session. Also, if you can't get to a terminal because your desktop program doesn't work, right click on your desktop and click create launcher.  Type "bash" into all of the panes and it will bring up a terminal for you.
From there you can do sudo apt-get update and upgrade and it will help get your computer working again.

I hope some of this helps.

Yeah it worked fine!  Thanks for that.  The window problem got sorted in the process.  By the look of things, I haven't got xgl now though.

---

### Post by galileon on 2006-09-06
cheers, that worked for me...

but the plugin wobbly window has come back (i originally removed the plugin in the list undet app>compiz>general>allscreens>options>active_plugins in gconf-editor...)

does anyone know how to remove it now, please? because the name isnt listed in the gconf-editor now...strange...

---

### Post by suhaib on 2006-09-07
Unfortunatley, although my GUI appears to be fine, I still cannot access a text based terminal by pressing ctrl + alt + f1:6.  The gui shutsdown, but the screen is totally black and I can't do (or at least see what I'm doing) anything except exit it.  Maybe this is another problem as a whole, and has nothing to do with Compiz?

---

### Post by Vlatko on 2006-09-07
[QUOTE=cneil]I don't know if this will work on your computer, but I found a fix on mine. 
Go to System>Preferences>Sessions>Startup Programs and then click edit. 
Change "startcompiz" to "compiz-start". It was pretty easy.[/QUOTE]i already had compiz-start, not startcompiz. what can i do? after th update all compiz effects are gone and i have no title bars!! lol

---

### Post by suhaib on 2006-09-07
> **Vlatko said:**
> i already had compiz-start, not startcompiz. what can i do? after th update all compiz effects are gone and i have no title bars!! lol

Exactly the same with me lol.  Maybe this will help you...

[http://www.ubuntuforums.org/showthread.php?t=131267&page=139]("http://www.ubuntuforums.org/showthread.php?t=131267&page=139")

---

### Post by dannyboy79 on 2006-09-07
i know that if you at least want to get your window borders back etc etc around open apps just go a terminal and type in "metacity" and then your open apps won't stick to the upper left corner and your borders with the x in the upper right corner will be back. as far as a permanent fix, not sure. I install xgl and compiz and chose to make xgl a seperate session so that if something did go wrong I could always go to a normal session. I most of the time work in a normal session and haven't gone into my xgl and compiz session for a while. I have seen a lot of updates to cwd-themes, etc etc so I am sure when I go into my xgl session I will be in for troubleshooting! it is just changing so much I don't know if it's worth using it quite yet hence why I installed it as a seperate session!

---

### Post by evillawngnome on 2006-09-07
You need to set some kernel parameters at boot, something like vga=xxx where xxx is the code for your display. Mine, i think, is 0x317 because i have a 1280x768 widescreen. Do a google search for kernel options, vga= and see if that gets you going.

---

### Post by Vlatko on 2006-09-08
this worked for me. locate the file /usr/local/bin/compiz-start and edit it as in the following:

[QUOTE=Kephren from Compiz.net]CGWD is loading but your decorator settings are not, Compiz is going through a heavy developement process and gconf settings have been discontinued in the later builds so make sure your start script has been updated.

mine used to be:
"cgwd &
compiz --replace gconf &"

my new one looks like this

"cgwd &
compiz --replace dbus csm & "

The decorator comes back and everything should work.
Do not forget that all of your move, cube, decorator funtions are all plugins and if those are not intializing you will first believe that Compiz is not fuctioning when the truth of the matter is you need to make sure your plugins are loading.[/QUOTE]

---

