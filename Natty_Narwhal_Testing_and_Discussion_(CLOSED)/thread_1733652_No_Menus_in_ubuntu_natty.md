---
title: "No Menus in ubuntu natty"
date: 2011-04-19
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by mac4rfree on 2011-04-19
Hi Guys,

I am using Ubuntu Natty... I was trying some option in Compiz,, suddenly all windows did not have any close,minimize and expand menus... Also the tab which pops up when you move the mouse to the top left most corner did not came.. 

So, literally i am with only the wallpaper and no menus..

Can somebody help me from dis...

Cheers!!!!!!!!!!

---

### Post by Mark Phelps on 2011-04-19
Ubuntu 11.04 is still in testing.  This thread is reserved for Ubuntu versions that have already been released.

Please post your 11.04 questions to the Natty Development forum.

thanks

---

### Post by bapoumba on 2011-04-19
Moved to natty.

---

### Post by Blasphemist on 2011-04-19
> unity --reset

This option allows the user to reset profile parameters in compiz and restart the Unity shell with default settings.

---

### Post by mc4man on 2011-04-19
Well open up ccsm again and look at what's enabled or not.
Some plugins, when enabled or disabled, will unset ALL the previously enabled plugins, so you should be a bit careful there. 

(if you're not familiar with what the default set is for the Unity or Classic logins then, while a bit late now, make yourself a list. Available in gconf-editor, shown in .xsessions.errors or xsessions.old or simply by starting ccsm from a terminal  - it will print out all loaded plugins.

don't have the default set _for unity_ handy - would be something like this
opengl
composite
wall
unity
animations
compiz library toolbox 
mouse position polling
move window
place window
resize window
window decoration
gnome compatibility 
detection 
bailer
session manag3ement
static application switcher 
regex matching 
scale 
fading windows 
expo  
animation 
viewport switcher 
workarounds
snapping windows (pretty worthless
grid
png
maybe a few more, forget.

---

### Post by mac4rfree on 2011-04-19
thanks guys,,, somehow the unity got uninstalled that is what the problem is.. when i changed some option, it was giving me lot of popups, which i just clicked.. I think that uninstalled unity.. I am installing unity again.. will keep you updated..

---

### Post by mac4rfree on 2011-04-19
I am still facing the issue even after install unity.. now i am not able to connect to internet even in Ubuntu Classic option.. Sorry ia a Windows user for long,, now only trying to get hold of ubuntu.. 
One more annoying thing is, i am not able to get any option to close,minimize or able to switch between the windows.. :(
I know  iam in deep mess,, can somebody help me.. please..
And, even i tried "unity --reset",, but it is asking me to install ccsm, which for some reason unable to install..

---

### Post by LtdEdFred on 2011-04-20
I'm facing the same problem as [mac4rfree]("http://ubuntuforums.org/member.php?u=1216908"). I'm not trying to hijack your thread but since we have the same problem I thought I'd just add to your explanation. 

Stupidly enough I disabled Unity to check out the cube effect (I was asked if I wanted to turn of Unity when I enabled the cube). Now I have no cube, no Unity. I can see my Desktop and the file I have on it. I can open the file, use "Winkey"+D to (not sure what to call this in Ubuntu but you probably know what I'm talking about) minimize windows, bring up help by pressing F1, I was asked for my keyring password upon boot (tried a restart) and I could see the "Connected to "wireless network" succesfull" dialogue. So the system is evidently "alive", but I can't do much else. Alt+F2 does not work so I can't launch any programs.

I'm sure the both of us would be tremendeously happy if anyone had a solution to this :)

---

### Post by wgarcia on 2011-04-20
I had this problem at some point and I think I solved it by entering into the classic version and enabling the Unity plugin in CCSM. Check also that Composite, Gnome Compatibility and OpenGl are checked at the top part. Go out from gnome classic and enter unity to see if everything back to normal. You can disable afterwards the Unity plugin in Gnome Classical if you have to use it again.

---

### Post by Blasphemist on 2011-04-20
I did a similar thing, maybe the same, to myself. I offered the unity reset from what I'd seen from others in hopes it would solve this easier than I did.

I was able to login to classic, are you? I did that, disabled cube and rotate cube, enabled expo and unity plugin. I then restarted and got logged in to "ubuntu" with unity. I know I did have to go back and forth a couple times but don't remember just why, its been a couple weeks. I was using compiz in classic to get back to being able to use unity. 

So the first thing is, can you use classic to try to recover from what you did like I did and wgarcia did? If compiz is no longer in shape to even do that, will any of the other login options get you logged in?

---

### Post by LtdEdFred on 2011-04-20
I have tried hundreds of keyboard short cuts now, but can't find one that opens the log-off dialogue. Since I don't have menus I can't simply press the "System-Log off" button :S

Any pointers? Are there any wizes out there who know how to enable Unity from console?


Edit: I managed to get into the log on dialogue by suspending the machine (it then appeared upon wake up). I have tried all the different methods of logging in and all of them show me my menuless Desktop :(

---

### Post by mac4rfree on 2011-04-20
The problem is i am not able to start CCSM itslf.. earlier it was giving some error but after the patch i applied which was given in the bug,, now it is neither opening nor throwing error...

---

### Post by mc4man on 2011-04-20
> after the patch i applied which was given in the bug,
What patch and what bug?

---

### Post by mac4rfree on 2011-04-20
[https://bugs.launchpad.net/ubuntu/+source/fusion-icon/+bug/192389]("https://bugs.launchpad.net/ubuntu/+source/fusion-icon/+bug/192389")
This is the one i was talking about.. when i tried to open CCSM, the bug took me there saying it was already reported.. and i tried applying the patch mentioned there..

---

### Post by mc4man on 2011-04-20
That patch was for fusion-icon which is just a system tray icon to open ccsm and a few other options 
 There's no real need for it in a Ubuntu (unity) login, I guess one could use in the Classic if desired.
(though if I wanted to run gnome-panel with metacity I would not use the the fusion icon, I'd just log out and log in to Classic (no effects)

Also the current natty fusion-icon package is fixed (as of yesterday), no patch needed

Did the unity login ever work for you?

If so and  I were you I'd either back out of the patch (described in bug report) and then remove fusion-icon or just try purging it, then install compizconfig-settings-manager and reset your compiz profiles back to defaults (there are separate profiles for Ubuntu (unity) and Classic logins
(if compizconfig-settings-manager is already installed then remove and re-install it

You may want to do this from the Classic (no effects) login

Something like - 
```
sudo apt-get purge fusion-icon compizconfig-settings-manager
```
```
sudo apt-get install compizconfig-settings-manager
```

If after that you want to quickly undo any changes to your compiz settings and restore the defaults then open your home folder > view > show hidden files
Open up .gconf > apps
Delete the compiz-1 and compizconfig-1 folders, then restart, log in to whatever you want

---

### Post by lucazade on 2011-04-20
> **mc4man said:**
> ..

If after that you want to quickly undo any changes to your compiz settings and restore the defaults then open your home folder > view > show hidden files
Open up .gconf > apps
Delete the compiz-1 and compizconfig-1 folders, then restart, log in to whatever you want

maybe this is a cleaner way:
```
gconftool --recursive-unset /apps/compiz-1
gconftool --recursive-unset /apps/compizconfig-1
```

---

### Post by mc4man on 2011-04-20
> **lucazade said:**
> maybe this is a cleaner way:
```
gconftool --recursive-unset /apps/compiz-1
gconftool --recursive-unset /apps/compizconfig-1
```
I'd say that would work also - may cause a slight/temp freeze  depending on what login in it's done from.

---

### Post by lucazade on 2011-04-20
> **mc4man said:**
> I'd say that would work also - may cause a slight/temp freeze  depending on what login in it's done from.

ok, good to know! : )

---

### Post by mac4rfree on 2011-04-26
sorry for the late update... i tried both the above solution.. but the unity has not been restored yet... 
Now i am able to start the ccsm.. so can somebody help me in restoring the Unity...

---

### Post by sgage on 2011-04-26
> **LtdEdFred said:**
> I have tried hundreds of keyboard short cuts now, but can't find one that opens the log-off dialogue.

ctl-alt-sysrq-k has always worked for me.

---

### Post by tlcstat on 2011-04-26
Greetings,
I suggest you reboot into safe mode and choose "repair broken packages". 
Just a suggestion. This worked for me with some big Unity screw-up, can't remember what.
tlcstat

---

### Post by mac4rfree on 2011-04-26
Well,, in safemode, i am able to get minimize,maximize and close button.. now the question is how to get it to ubuntu mode????

---

### Post by LtdEdFred on 2011-04-27
I gave up and formatted :P


> ctl-alt-sysrq-k has always worked for me. 	
This only shrunk my current window each I pressed k.

---

