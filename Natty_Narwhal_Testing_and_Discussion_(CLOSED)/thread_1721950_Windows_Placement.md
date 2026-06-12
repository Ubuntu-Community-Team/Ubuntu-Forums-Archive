---
title: "Windows Placement"
date: 2011-04-05
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by coffeecat on 2011-04-05
I have the following settings in ccsm:

Ubuntu Unity Plugin > Hide Launcher = Dodge Windows.

Window Management > Place Windows > Centered.

This was working OK until recently, but now new windows open top left and knock the launcher away - which I find irritating. The same happens when I set place windows to smart, which I believe is the ccsm default. I think an update to something must be over-riding the ccsm Place Windows setting.

But not always. Synaptic opened from the launcher opens where I last closed it on the desktop. Its "Mark additional changes" sub-window opens top left knocking the launcher, but the Software Sources window from the Settings menu opens centre screen.

This is not a admin-privilege app thing. Gparted opens consistently top-left.

What are other people getting?

---

### Post by r-senior on 2011-04-05
I was (may still be) getting something similar. I have the launcher set always visible and some programs, notably Terminal and various dialog boxes, were going under the launcher and global menu bar.

I fiddled around with Smart, Center and so on in the Place Windows Compiz plugin and none of them seemed to make any difference. So I turned it off completely. I don't *think* I've had problems with window placement since then. Whether it was turning off Place Windows or recent updates, I have no idea.

I'll turn in back on to Smart and see what happens ...

EDIT: Compiz crashed as soon as I hit the checkbox ;). When it recovered, I re-enabled Place Windows and there was a weird entry in "Windows with Fixed Positions". Blank name, and -32767, -32767. I deleted that. A bit early to say but I tried Synaptic, where the search dialog was one of the known offenders for me, and it seems OK.

---

### Post by coffeecat on 2011-04-05
> **r-senior said:**
> EDIT: Compiz crashed as soon as I hit the checkbox :wink:.

Yes, I get that enabling/disabling any of the ccsm modules. I thought it was part of the Unity experience. :)

> **r-senior said:**
> So I turned it off completely. I don't *think* I've had problems with window placement since then. Whether it was turning off Place Windows or recent updates, I have no idea.

I'll turn in back on to Smart and see what happens ...

Interesting. I tried disabling 'Place Windows' altogether and, apart from the brief compiz crash, I get exactly the same as with it enabled. Curious.

---

### Post by umberstark on 2011-04-05
Please add yourself to this bug

[https://bugs.launchpad.net/unity/+bug/747706](https://bugs.launchpad.net/unity/+bug/747706)

---

### Post by mc4man on 2011-04-05
There is a bug about the launcher getting knocked with windows that open at the left, top left usually (firefox and terminal do that here.
The cause here of the 'bumping' of the launcher is that the window border is not being taken into account
So adjusting the theme to  borderless (ambiance) has stopped that (intended to use borderless anyway whether they decide to or not

There is also some odd placement of synaptic popups that has started recently

'bump' bug
[https://bugs.launchpad.net/unity/+bug/750692](https://bugs.launchpad.net/unity/+bug/750692)

---

### Post by r-senior on 2011-04-05
> **umberstark said:**
> Please add yourself to this bug

[https://bugs.launchpad.net/unity/+bug/747706](https://bugs.launchpad.net/unity/+bug/747706)
Not quite the same problem in that this is more about windows hiding behind the launcher/global menu, but I have added myself.

On the topic of bugs, I reported the one about the crashes when a checkbox is changed:

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/751348](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/751348)

Something weird is going on. When I do a search in Synaptic for example, the dialog appears in the top left corner (not hidden, it's OK where it is). Second and subsequent times I do a search, it appears bang in the middle of the screen. Are GTK dialogs supposed to appear in the middle of their parent?

---

### Post by mc4man on 2011-04-05
> **r-senior said:**
> I was (may still be) getting something similar. I have the launcher set always visible and some programs, notably Terminal and various dialog boxes, were going under the launcher and global menu bar..

Try this when using a 'never' hide launcher mode - 
From a fresh start if windows open correctly (not going under launcher or panel) then move to another workspace. At least here they will then start going under the launcher, again firefox and terminal are good example because they generally open in top left
Moving back to the orig. workspace (ws1) and they behave properly again

I only see this with the never hide launcher
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/749681](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/749681)

---

### Post by coffeecat on 2011-04-05
> **umberstark said:**
> Please add yourself to this bug

[https://bugs.launchpad.net/unity/+bug/747706](https://bugs.launchpad.net/unity/+bug/747706)

I've done a me-too - thanks - but not commented yet because I need to do a bit more investigation. The situation is more complicated than I thought. 

The apps that open top-left and make the launcher retract:

Firefox, Chromium Web browser, terminal, ccsm, Gparted, gconf-editor, gThumb, gedit, System Monitor.

Those that open centred:

LibreOffice, Ubuntu Software Centre, Ubuntu One Control Panel, DeVeDe.

Those that open in last position:

Nautilus, Synaptic, VLC, Gimp.

I'll test some more apps later. Anyone see a pattern? I don't.

=====

Oo-er. My little Ubuntu logo Applications button (top-left - forgotten what it's called) has turned blue. No, seriously. :|

---

### Post by t.rei on 2011-04-06
An I thought I was going nuts. I even created a new user for default settings. Would so love to have the windows open the way it is set to in the ccsm settings. (centered for me).

That and the launcher alt+f2 being really weird when typing a command, sometimes just running the previously used command, or something totally different or whatever. Really disturbing to go "alt-f2 gconf-[enter]" and getting gedit or ccsm even... my workaround is synapse for now.

---

