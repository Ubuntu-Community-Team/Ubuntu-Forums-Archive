---
title: "2d Unity Based on QT"
date: 2011-01-15
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by NightwishFan on 2011-01-15
Did anyone try the new Unity? I am using it on Maverick with the PPA release and it is lightning fast. I think it is in Natty main by now. I made a video of it here:
[http://www.youtube.com/watch?v=HWYSgTiRe-0](http://www.youtube.com/watch?v=HWYSgTiRe-0)

Click to install on Natty:
[apt://unity-qt-default-settings]("apt://unity-qt-default-settings")

Here is the PPA if you desire for Mav/Natty
[https://launchpad.net/~unity-2d-team/+archive/unity-2d-daily](https://launchpad.net/~unity-2d-team/+archive/unity-2d-daily)

How to add:
```
sudo add-apt-repository ppa:unity-2d-team/unity-2d-daily && sudo apt-get update
```

---

### Post by kaldor on 2011-01-16
This is out already? That's awesome...

How's the performance on 2d Unity compared to GNOME 2.x?

---

### Post by NightwishFan on 2011-01-16
Its pretty lightning fast and does not lag when searching the launcher like the 3d netbook unity in Maverick. I have been using it all day and the only problem I have encountered is the sidebar quits and you have to open a terminal and run:
```
unity-qt-launcher & exit
```

I also am checking for memory leaks, which it might be doing. So, do not use this on production systems obviously but it is better than I expected by far.

---

### Post by exploder on 2011-01-16
I am glad to see 2D Unity, this overcomes major obstacles for Unity for many users. :D

---

### Post by Ichtyandr on 2011-01-16
why does it require gwibber and indicator-me?

---

### Post by scradock on 2011-01-16
> **NightwishFan said:**
> Did anyone try the new Unity? I am using it on Maverick with the PPA release and it is lightning fast. I think it is in Natty main by now. I made a video of it here:
[http://www.youtube.com/watch?v=HWYSgTiRe-0](http://www.youtube.com/watch?v=HWYSgTiRe-0)

Click to install on Natty:
[apt://unity-qt-default-settings]("apt://unity-qt-default-settings")

Here is the PPA if you desire for Mav/Natty
[https://launchpad.net/~unity-2d-team/+archive/unity-2d-daily](https://launchpad.net/~unity-2d-team/+archive/unity-2d-daily)

How to add:
```
sudo add-apt-repository ppa:unity-2d-team/unity-2d-daily && sudo apt-get update
```

That looks very interesting - how do you get the horizontal bands of launchers on the desktop? Looks more like Gnome Shell than Unity3d.

As far as I can see, if this is Unity2d then the one we're offered in Natty is Unity1d - only a single left-hand bar of launchers, and no working menus.....

---

### Post by MARP1961 on 2011-01-16
Yes I've installed it on 10.10 in Virtual Box. I think I like it. I know I'd like it if I could fully customise by changing icon design on the side dock and the colour of the awful top panel. Not everyone wants a browny-purple interface.

---

### Post by MARP1961 on 2011-01-16
Yes I've installed it on 10.10 in Virtual Box. I think I like it. I know I'd like it if I could fully customise by changing icon design on the side dock and the colour of the awful top panel. Not everyone wants a browny-purple interface.

---

### Post by scradock on 2011-01-16
Well, I've tried adding the ppa, but the unity-qt-default-settings package won't install because some other packages are unavailable at the moment.

Similarly in the standard Natty repos, where the packages seem to be named unity-2d-????? rather than unity-qt-???

Shame - looking forward to trying this out......

---

### Post by NightwishFan on 2011-01-16
It will sort itself out on Natty, natty is a moving target :) Do not worry. It does work on Maverick. It seems to leak memory until each component is using around 80mb though, so I stopped using it day to day for now.

---

### Post by Queue29 on 2011-01-17
This looks so much better than Gnome Shell it's not even funny.

---

### Post by Yellow Pasque on 2011-01-17
> **Queue29 said:**
> This looks so much better than Gnome Shell it's not even funny.
Needs more work, but yeah, I have good hopes for Unity/2D.

---

### Post by zekopeko on 2011-01-17
This isn't installable at the moment in Natty, correct?

---

### Post by zekopeko on 2011-01-17
This isn't installable at the moment in Natty, correct?

---

### Post by Yellow Pasque on 2011-01-17
> **zekopeko said:**
> This isn't installable at the moment in Natty, correct?
I installed it by searching for 'unity' in Synaptic and installing the appropriate packages. GDM will then give you a Unity2D login option.

---

### Post by kaldor on 2011-01-17
Trying it right now, replying to this post on Unity-qt.

It's rough and buggy, but I have a good view of it. I'll keep using it and report bugs as I go. I love this; it's just what I wanted in a GUI... a native, non-3d dock and global menu that won't suck performance.

---

### Post by jerrylamos on 2011-01-17
O.K., so Unity 2D is running on this embedded i845G video graphics which Unity 3D is blacklisted from.  Thanks for the posts and directions.

Now how do I do autohide?  That's a lot more real estate lost to my applications than gnome...

On gnome I delete the bottom panel so I only lose the top line.

Thanks much, Jerry

---

### Post by NightwishFan on 2011-01-17
I am not sure the 2d one can autohide yet. It is probably planned though.

---

### Post by rg4w on 2011-01-17
What is "2D" and what is "3D" when referring to Unity?

---

### Post by zekopeko on 2011-01-17
> **rg4w said:**
> What is "2D" and what is "3D" when referring to Unity?

Unity (3D) uses OpenGL acceleration. Unity 2D does not.

---

### Post by Jonny87 on 2011-01-18
I installed the notebook edition into my standard maverick awhile ago so that I could try out the unity interface. I like it, but so far I haven't found a way to customize it in any way, i.e. move bar to top or bottom or change the theme on it (at the moment it doesn't match the theme of my nautilus). minor issue I know but I find it annoying.

Also conky doesn't seem to show up in it.

Anyone got any solutions to the above. If I could sort this I'd be willing to try upgrade to the testing version of natty.

---

### Post by MARP1961 on 2011-01-18
I agree. There needs to be at least an option to change the background colour of the side dock and top panel. It would also be desirable to be able to have a choice of icon style on the dock and an ability to move, change, add or delete the items on the top panel as well.  Some people really like symmetry and a side dock arguably spoils this. Perhaps a dock on both sides at once would look better and enable more applications to show without scrolling. The ability to move the dock to the top or bottom would also be good. I am however impressed with the excellent and quick 'search' facility. Everything seems to work quickly and smoothly on my old desktop pc. I thought I might miss not being able to place icons on a desktop background too but so far I haven't.

---

### Post by kaldor on 2011-01-18
> **MARP1961 said:**
> Some people really like symmetry and a side dock arguably spoils this.

Yep, but I find the way that I barely even notice I am using Unity when maximized makes up for it :)

I agree though about the launcher colour; it's pretty ugly. But then again, it'll probably change... they can't let a 2 second Gradient job be in the final product ;)

---

### Post by jerrylamos on 2011-01-18
> **MARP1961 said:**
> It would also be desirable to be able to have a choice of icon style on the dock and an ability to move, change, add or delete the items on the top panel as well.  
Yay!  A Unity type launcher that works!  At Alpha time, the Unity-3D:
1.  Unity-3D won't ever run on two of my pc's, they don't have the video hardware needed.  Will try Unity-2D soon.
2.  On another, Unity-3D hardware is there but Unity dies as soon as wallpaper comes up.  IBM Thinkpad T40 ati radeon mobility 7500.  Compiz crashes.  Bug submitted.
3.  On the third, Unity-3D can be made to run but with a lot of gymnastics at the command line to get it up.  Compiz crashes on both Unity and Gnome unless the new option gnome-desktop no effects is used.  Bug submitted.  ati radeon xpress 200.  I have hopes Unity-3D may run, but Unity-2D is BAM fast!

I do make changes on gnome top panel and hope Unity-2D will add that capability.

Jerry

---

### Post by Yougo on 2011-01-18
good stuff!

here i was getting slightly unimpressed by the progress on 3d Unity (unity/compiz dies when resizing the desktop, no dash yet, still a fixed top panel), and then they pass me on the right with 2d Unity! And it has the dash running, judging by the youtube clip. 

looks like i've got something to do tonight
i wonder how it handles multiple desktops and resizing monitors

actually it looks so slick that i wonder what advantages 3d has over 2d when it comes to the unity interface.

it'd be hilarious if Gnome-shell spits out a 2d version tomorrow!

---

### Post by kaldor on 2011-01-18
I'm beginning to find that using Unity helps me get things done faster. I find the window management and file browsing is much quicker than using regular GNOME 2.3x. 

And like I said in previous posts, I feel like I have much more room working on my Laptop than I did on GNOME. 

I'm quite content with this and I cannot wait for it to develop further. I've been using it as my main DE since last night, and I have only experienced one launcher crash.

---

### Post by Yellow Pasque on 2011-01-18
> **kaldor said:**
> I'm beginning to find that using Unity helps me get things done faster. I find the window management and file browsing is much quicker than using regular GNOME 2.3x.
I feel the same way about xfce ;)

---

### Post by knarf on 2011-01-18
I just installed U2D (snazzy acronym, not?) on my Thinkpad T23 and got it to run, mostly. 

 - The launcher thingy - unity-2d-places - only manages to launch chromium-browser, the other buttons (Music, etc) do not work.
 - nautilus, which is installed as default file manager in the dock, does not work. Even when launched from a terminal it only shows a grey window.
 - talking about terminals... I had to start one by going to a console, logging in and starting 'DISPLAY=:0 xterm' because there does not seem to be a way to start applications by name from the shell.
 - no global menu - at least it does not work here...
 - all the stuff mentioned before which is probably being worked on, from theming to panel extensibility.
 - it is quite resource intensive compared to my default Xmonad session as all components take between 20 MB and 30 MB in resident memory.

The interface is clean and the workflow seems to be logical. Given some further development (including the **[COLOR="Red"]absolutely mandatory[/COLOR]** (where is the BLINK tag when you need it?) autohide for the dock) it certainly shows promise.

It could even be developed into a [tiling window manager]("http://xmonad.org/") for the masses as it is already halfway there. It - or rather metacity - would need some more smarts when it comes to window placement as well as better keyboard control so the mouse can be left alone if so desired.

All in all this is a good development which can extend the development of Ubuntu to a large class of older hardware.

---

### Post by donato roque on 2011-01-18
> I'm beginning to find that using Unity helps me get things done faster. I find the window management and file browsing is much quicker than using regular GNOME 2.3x.

And like I said in previous posts, I feel like I have much more room working on my Laptop than I did on GNOME.

I'm quite content with this and I cannot wait for it to develop further. I've been using it as my main DE since last night, and I have only experienced one launcher crash.

They hit the jackpot here.  Unity 2d, using Qt, is the breach we've been waiting for.

---

### Post by Yougo on 2011-01-19
ok i got it to work, had to juggle around some libunity dependencies apparently. at a glance it's pretty much the maverick netbook version. it wouldn't take the menu bar into the panel, so it left my windows without menus :-/. as mentioned in above post, the dash was a bit of a stump. i guess content for that is in the future?

also i filled the 3d launcher with random apps to make it compress the icons, but none of these were in the 2d launcher. do they look for content in different places?

also like above mentioned, when i needed a terminal, Unity couldn't give me one. luckily i keep an AWN panel and a Gnome Panel around, so i still have a menu, window and desktop switcher and ALT+F2 run dialog when the shell fails.

speaking of the Gnome-panel, it shows a window-resize grip, which does change the cursor to 'resize', but doesn't resize anything. AFAICT it does belong to the panel... weird. does anyone know what that's about?

---

### Post by kaldor on 2011-01-19
> **donato roque said:**
> They hit the jackpot here.  Unity 2d, using Qt, is the breach we've been waiting for.

I've wanted something like this for a long time; my wish came true :)

---

### Post by rvchari on 2011-01-19
hi..
i installed as mentioned in the 1st page. but in my case, the top panel just displayed global menu. i had main menu button in the desktop edition and awn for dock. but side dock is not to be seen, i even issued the command as mentioned....
anything wrong here ? i got the wallpaper i had in desktop edition along with top panel global menu and other tweaks as it is... i felt i logged on to me desktop edition, i confirmed that it was unity only after the usual right click option gave a null return !!!
anything else i need to configure ?

---

### Post by rvchari on 2011-01-19
hi..
i installed as mentioned in the 1st page. but in my case, the top panel just displayed global menu. i had main menu button in the desktop edition and awn for dock. but side dock is not to be seen, i even issued the command as mentioned....
anything wrong here ? i got the wallpaper i had in desktop edition along with top panel global menu and other tweaks as it is... i felt i logged on to me desktop edition, i confirmed that it was unity only after the usual right click option gave a null return !!!
anything else i need to configure ?

---

### Post by espenfjo on 2011-01-20
Is it just me, or does [http://ppa.launchpad.net/unity-2d-team/unity-2d-daily/ubuntu/dists/natty/main/binary-amd64/Packages](http://ppa.launchpad.net/unity-2d-team/unity-2d-daily/ubuntu/dists/natty/main/binary-amd64/Packages) not include any unity-packages?

I am not able to install unity-2d-* since there are no packages.

---

### Post by espenfjo on 2011-01-20
Is it just me, or doesnt [http://ppa.launchpad.net/unity-2d-team/unity-2d-daily/ubuntu/dists/natty/main/binary-amd64/Packages](http://ppa.launchpad.net/unity-2d-team/unity-2d-daily/ubuntu/dists/natty/main/binary-amd64/Packages) contain any unity packages?

I am not able to install unity-2d because of this

---

### Post by espenfjo on 2011-01-20
Is it just me, or doesnt [http://ppa.launchpad.net/unity-2d-team/unity-2d-daily/ubuntu/dists/natty/main/binary-amd64/Packages](http://ppa.launchpad.net/unity-2d-team/unity-2d-daily/ubuntu/dists/natty/main/binary-amd64/Packages) contain any unity packages?

I am not able to install unity-2d because of this

---

### Post by espenfjo on 2011-01-20
Is it just me, or doesnt [http://ppa.launchpad.net/unity-2d-team/unity-2d-daily/ubuntu/dists/natty/main/binary-amd64/Packages](http://ppa.launchpad.net/unity-2d-team/unity-2d-daily/ubuntu/dists/natty/main/binary-amd64/Packages) contain any unity packages?

I am not able to install unity-2d because of this

---

### Post by espenfjo on 2011-01-20
Is it just me, or doesnt [http://ppa.launchpad.net/unity-2d-team/unity-2d-daily/ubuntu/dists/natty/main/binary-amd64/Packages](http://ppa.launchpad.net/unity-2d-team/unity-2d-daily/ubuntu/dists/natty/main/binary-amd64/Packages) contain any unity packages?

I am not able to install unity-2d because of this

---

### Post by espenfjo on 2011-01-20
Is it just me, or doesnt [http://ppa.launchpad.net/unity-2d-team/unity-2d-daily/ubuntu/dists/natty/main/binary-amd64/Packages](http://ppa.launchpad.net/unity-2d-team/unity-2d-daily/ubuntu/dists/natty/main/binary-amd64/Packages) contain any unity packages?

I am not able to install unity-2d because of this

---

### Post by espenfjo on 2011-01-20
Is it just me, or doesnt [http://ppa.launchpad.net/unity-2d-team/unity-2d-daily/ubuntu/dists/natty/main/binary-amd64/Packages](http://ppa.launchpad.net/unity-2d-team/unity-2d-daily/ubuntu/dists/natty/main/binary-amd64/Packages) contain any unity packages?

I am not able to install unity-2d because of this

---

### Post by espenfjo on 2011-01-20
Is it just me, or doesnt [http://ppa.launchpad.net/unity-2d-team/unity-2d-daily/ubuntu/dists/natty/main/binary-amd64/Packages](http://ppa.launchpad.net/unity-2d-team/unity-2d-daily/ubuntu/dists/natty/main/binary-amd64/Packages) contain any unity packages?

I am not able to install unity-2d because of this

---

### Post by espenfjo on 2011-01-20
Is it just me, or doesnt [http://ppa.launchpad.net/unity-2d-team/unity-2d-daily/ubuntu/dists/natty/main/binary-amd64/Packages](http://ppa.launchpad.net/unity-2d-team/unity-2d-daily/ubuntu/dists/natty/main/binary-amd64/Packages) contain any unity packages?

I am not able to install unity-2d because of this

---

### Post by espenfjo on 2011-01-20
Is it just me, or doesnt [http://ppa.launchpad.net/unity-2d-team/unity-2d-daily/ubuntu/dists/natty/main/binary-amd64/Packages](http://ppa.launchpad.net/unity-2d-team/unity-2d-daily/ubuntu/dists/natty/main/binary-amd64/Packages) contain any unity packages?

I am not able to install unity-2d because of this

---

### Post by espenfjo on 2011-01-20
Is it just me, or doesnt [http://ppa.launchpad.net/unity-2d-team/unity-2d-daily/ubuntu/dists/natty/main/binary-amd64/Packages](http://ppa.launchpad.net/unity-2d-team/unity-2d-daily/ubuntu/dists/natty/main/binary-amd64/Packages) contain any unity packages?

I am not able to install unity-2d because of this

---

### Post by espenfjo on 2011-01-20
Is it just me, or doesnt [http://ppa.launchpad.net/unity-2d-team/unity-2d-daily/ubuntu/dists/natty/main/binary-amd64/Packages](http://ppa.launchpad.net/unity-2d-team/unity-2d-daily/ubuntu/dists/natty/main/binary-amd64/Packages) contain any unity packages?

I am not able to install unity-2d because of this

---

### Post by espenfjo on 2011-01-20
Is it just me, or doesnt [http://ppa.launchpad.net/unity-2d-team/unity-2d-daily/ubuntu/dists/natty/main/binary-amd64/Packages](http://ppa.launchpad.net/unity-2d-team/unity-2d-daily/ubuntu/dists/natty/main/binary-amd64/Packages) contain any unity packages?

I am not able to install unity-2d because of this

---

### Post by rvchari on 2011-01-20
did u add repository ?
if not then issue the following command as mentioned in the 1st post of this thread...

sudo add-apt-repository ppa:unity-2d-team/unity-2d-daily && sudo apt-get update

---

### Post by zika on 2011-01-21
> **rvchari said:**
> did u add repository ?
if not then issue the following command as mentioned in the 1st post of this thread...

sudo add-apt-repository ppa:unity-2d-team/unity-2d-daily && sudo apt-get updateAre we talking about Natty?
I do not see any unity-2d packages in that ppa (for Natty) either...
(This is a Natty thread...)

---

### Post by rvchari on 2011-01-21
if u read the first post in this thread, u ll know that this works for natty as well as maverick.
in my case it worked but with a additional terminal command to start unity-2d-launcher and unity-2d-panel.
my previous compiz settings worked fine in this. i got tired of issuing these 2 terminal commands every now and then so i removed it and m feeling happy with my desktop edition and unity-netbook that i already had...
hope u could achieve ur goal...

---

### Post by zika on 2011-01-21
> **rvchari said:**
> if u read the first post in this thread, u ll know that this works for natty as well as maverick.
in my case it worked but with a additional terminal command to start unity-2d-launcher and unity-2d-panel.
my previous compiz settings worked fine in this. i got tired of issuing these 2 terminal commands every now and then so i removed it and m feeling happy with my desktop edition and unity-netbook that i already had...
hope u could achieve ur goal...
Following the first post I went to PPA mentioned... No Natty packages except old metacity...
I'll stay with Metacity/FluxBox...
Have a nice day...

BTW is it apt://unity-qt-default-settings or apt://unity-2d-default-settings ?

---

### Post by espenfjo on 2011-01-21
> **zika said:**
> Following the first post I went to PPA mentioned... No Natty packages except old metacity...
I'll stay with Metacity/FluxBox...
Have a nice day...

BTW is it apt://unity-qt-default-settings or apt://unity-2d-default-settings ?

This is my experience also,
A simple check of the Packages file in that PPA will confirm both our statements.

---

### Post by NightwishFan on 2011-01-21
The QT Unity is already in Natty without the PPA. Just be patient I already said Natty is a moving target it is not meant for normal desktop use yet.

---

### Post by zika on 2011-01-21
> **NightwishFan said:**
> The QT Unity is already in Natty without the PPA. Just be patient I already said Natty is a moving target it is not meant for normal desktop use yet.
Yes, for some time, now... unity-2d...
Anybody in Natty-testing, I'm afraid, could not be called &#8222;patient&#8220;... :)

Update: OK, You've made me impatient: It works (Unity-proper works but doesn't refresh the screen after I close app.) and I could live with it... Just to get hold of short-cut-keys (much of them from Metacity work) as I miss Alt-F2 and such...

---

### Post by NightwishFan on 2011-01-21
You have a point with the "patient" thing and Natty users. :D However I just meant it will sort itself out more as the alphas and release candidates come around.

Alt+f2 is a product of the Gnome Panel. I hope they invent a clever replacement for it. As an alternative download and install Gnome Do. It will bind itself to Super+Space by default. (Super is the flag key) [Install Gnome Do]("apt://gnome-do")

---

### Post by zika on 2011-01-21
> **NightwishFan said:**
> You have a point with the "patient" thing and Natty users. :D However I just meant it will sort itself out more as the alphas and release candidates come around.

Alt+f2 is a product of the Gnome Panel. I hope they invent a clever replacement for it. As an alternative download and install Gnome Do. It will bind itself to Super+Space by default. (Super is the flag key) [Install Gnome Do]("apt://gnome-do")I do know where Alt-F2 comes from, that is why I was pointing that out..
I do not have a Super key... I'll stay with FluxBox (without gdm started...) and make occasional trips to Ubuntu-Classic-Desktop(No Effects)... :)
I'm happy that I have more and more choices... :)

---

### Post by cariboo on 2011-01-21
Alt-f2 is being worked on, gmrun will be integrated as a replacement for the gnome-panel functionality

---

### Post by lucazade on 2011-01-21
> **zika said:**
> I do know where Alt-F2 comes from, that is why I was pointing that out..
I do not have a Super key... I'll stay with FluxBox (without gdm started...) and make occasional trips to Ubuntu-Classic-Desktop(No Effects)... :)
I'm happy that I have more and more choices... :)

Alt+F2 official bug (also for unity-3d)
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/580295](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/580295)

bug report for unity-2d:
[https://bugs.launchpad.net/unity-2d/+bug/703499](https://bugs.launchpad.net/unity-2d/+bug/703499)

temporary fix: install synapse or gmrun

sudo apt-get install gmrun

then open gconf-editor

apps/metacity/global_keybindings and set "panel_run_dialog" to "disable". 
in the same folder "run_command_1" to "<Alt>F2"
apps/metacity/keybinding_command" and set key "command_1" to "gmrun"

this will hook gmrun to Alt+f2

---

### Post by zika on 2011-01-21
> **lucazade said:**
> Alt+F2 official bug (also for unity-3d)
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/580295](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/580295)

bug report for unity-2d:
[https://bugs.launchpad.net/unity-2d/+bug/703499](https://bugs.launchpad.net/unity-2d/+bug/703499)

temporary fix: install synapse or gmrun

sudo apt-get install gmrun

then open gconf-editor

apps/metacity/global_keybindings and set "panel_run_dialog" to "disable". 
in the same folder "run_command_1" to "<Alt>F2"
apps/metacity/keybinding_command" and set key "command_1" to "gmrun"

this will hook gmrun to Alt+f2Yes, I have gmrun installed already, due to excursions to OpenBox and other...
I, even, use it in FluxBox instead of fbrun...
Run_command are all, already, used... :)
Thank You!

---

### Post by zika on 2011-01-21
> **lucazade said:**
> Alt+F2 official bug (also for unity-3d)
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/580295](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/580295)

bug report for unity-2d:
[https://bugs.launchpad.net/unity-2d/+bug/703499](https://bugs.launchpad.net/unity-2d/+bug/703499)

temporary fix: install synapse or gmrun

sudo apt-get install gmrun

then open gconf-editor

apps/metacity/global_keybindings and set "panel_run_dialog" to "disable". 
in the same folder "run_command_1" to "<Alt>F2"
apps/metacity/keybinding_command" and set key "command_1" to "gmrun"

this will hook gmrun to Alt+f2Yes, I have gmrun installed already, due to excursions to OpenBox and other...
„Run_command“ are all, already, used... :)
Thank You!

---

### Post by Maupertus on 2011-01-22
I installed U2D after the OMGUbuntu post, it works pretty nice on my EEEPc 904HA. One question though...am I the only one where the sidebar doesn't scroll?

---

### Post by NightwishFan on 2011-01-22
I think it only scrolls when it needs to.

---

### Post by Maupertus on 2011-01-22
Ah! I found out, I was still used to the 3d launcher of the 'regular' Unity Launcher. This one needs to be dragged.

(I feel a bit ashamed and n00bish now)

---

### Post by Jonny87 on 2011-01-24
Not sure where else to post this but I just have a quick question. As I mentioned earlier I quite like unity but not ready to use fully until I can customise the themes etc. However, I love the menu style and was wondering if anyone know if its possible to get it for the gnome desktop (if so where and what's it called), or if there's an alternative that looks much the same?

---

### Post by pauljwells on 2011-04-14
Are you referring to the way the application menus appear in the top panel rather than in the app window bars? If so then this is easy - right click the panel and choose 'add to panel' in the options that show up you want to add the indicator applet that says 'displays application menus' or something similar. I think it works better if you delete the ubuntu menu applet and add the gnome default one instead to give more room on the panel.

---

