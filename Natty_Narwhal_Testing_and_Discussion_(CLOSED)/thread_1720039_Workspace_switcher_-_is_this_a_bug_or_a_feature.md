---
title: "Workspace switcher - is this a bug or a feature?"
date: 2011-04-02
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by fabricator4 on 2011-04-02
While playing with the task switcher, I noticed that it always put my Gkrellm window smack bang in the middle of the desktop in the preview.  When I select the workspace it zooms across to it's correct location.  Very strange.

I opened another app and left it as a small window and tried again, it moved the windows around on the preview and actually had them in the reverse order to what they really are on the workspace.  Again, when the workspace is selected the windows zoom around to their proper places.

I kind of get it - it's trying to show all the windowed apps layed out so that none are hidden - even the minimised apps get displayed in the preview window.  This is even more disconcerting as the app zooms to its correct place on the workspace, then disappears.  

I'm sure this sounds like a good idea - it even looks good on paper to me now, but the fact is, this behaviour is sucky beyond belief when you are trying to use it.  When I look at workspaces, I expect them to appear as they did when I left them, not a hotch-potch of windowed apps in random locations.

Should I report a "bug" (probably not) or is there some other way I can voice my displeasure to other users and perhaps to someone who cares.  It's annoying enough to be bug.

Chris.

---

### Post by seeker5528 on 2011-04-02
Did you change some compiz settings?

I'm not seeing what you are seeing.

If I click on the workspace switcher I see my work spaces the way I left them. If I move windows around, they stay where I moved them whether I switch to that desktop or not.

I don't run Gkrellm, so I suppose there could be something specific to that?

Task switching is a whole different, semi-unrelated thing.

If I click on an application icon, it brings that application's window to the foreground and moves me to the desktop where that application window is located.

 If I have multiple windows of a single application on multiple desktops, it seems to almost always bring the window on desktop 1 to the foreground and move me to desktop 1, leaving the windows of that application that exist on other desktops in the background if that is how they were. The exception being if an application's windows are in the background on all but single desktop *and* that application doesn't have a window on the current desktop, it will take be to that desktop even if it is not desktop 1. 

*EDIT* If the application in question has a window on the current desktop, it always brings that window to the foreground instead of switching you to another desktop.

If I have multiple windows of a single app on multiple desktops, along with some individual apps, click on the workspace switcher, select different desktops without actually switching to them, click on different icons of the running apps, which window will be brought to the foreground on which desktop and when becomes unpredictable, which might be considered a bug, but that still doesn't resemble what you describe.

Later, Seeker

---

### Post by r-senior on 2011-04-02
Window placement in Unity has been great for the past couple of weeks but the last couple of days' updates seem to have introduced some odd behaviour for me. Windows insisting on going to the top left corner for example.

I was going to give it a couple of days and a couple of updates before reporting bugs. If you report a bug, could you post the number in this thread?

---

### Post by mc4man on 2011-04-02
"Workspace switcher" - gathering that you're not talking about the  Workspace switcher in the launcher - that does show workspaces as they are
(and no minimized), it is the expo plugin

If referring to the scale function 'window picker for all windows'  - super+w, then you're not looking at a workspace, it a display screen to pick the window you wish
How it lays out I'm not sure, what does it matter

If you're getting minimized windows thru scale  then you've enabled 'keep previews...' in workarounds, which while it works can cause unexpected behavior
(and is a currently unsupported option

---

### Post by fabricator4 on 2011-04-02
> **seeker5528 said:**
> Did you change some compiz settings?
I'm not seeing what you are seeing.


That's odd.  No I didn't change any settings.  It's a fresh install, using my /home partition (so there's possibly settings carried over, if it's picking up something in /home/username).  All I've done really is to do an update last night.  There's some more updates this morning, but I had the update manager crash before it got the downloads - I'll try again later.

> 
If I click on the workspace switcher I see my work spaces the way I left them. If I move windows around, they stay where I moved them whether I switch to that desktop or not.


I've go this on two machines now, the EeePC, a 900SD which running Unity out of the box, and the 2.8 GHz desktop machine (on it now) which has to run Unity 2D.

It's possible that I've copied some some settings over from the Desktop machine, though I'm not sure.  I think it was just a new install originally when I tried Natty alpha.

> 
I don't run Gkrellm, so I suppose there could be something specific to that?

I wouldn't think so, it's just a system monitor app.  It's just that I noticed it first because it's on all the workspaces, and it's bit obvious in the preview screens seeing as how it's bang in the middle of all of them.  I've closed Gkrellm and the odd behaviour continues - it's layed out four applications on the preview desktop.  This behaviour seems planned and programmed - ie a feature.  


> 
Task switching is a whole different, semi-unrelated thing.

If I click on an application icon, it brings that application's window to the foreground and moves me to the desktop where that application window is located.

No problems there, it works as expected.

>  If I have multiple windows of a single application on multiple desktops, it seems to almost always bring the window on desktop 1 to the foreground and move me to desktop 1, leaving the windows of that application that exist on other desktops in the background if that is how they were. The exception being if an application's windows are in the background on all but single desktop *and* that application doesn't have a window on the current desktop, it will take be to that desktop even if it is not desktop 1. 

*EDIT* If the application in question has a window on the current desktop, it always brings that window to the foreground instead of switching you to another desktop.


This is exactly what was worrying me about the whole launcher thing.  I'm used to finding minimized apps on the bar at the bottom of the screen.  I hadn't got around to testing this yet though.  I'll see how I like it...  and no, this is not the behaviour I'm taking about.

Chris

---

### Post by fabricator4 on 2011-04-02
> **r-senior said:**
> Window placement in Unity has been great for the past couple of weeks but the last couple of days' updates seem to have introduced some odd behaviour for me. Windows insisting on going to the top left corner for example.

For me they try to go to the middle, or if there's more than one they try to group around the middle.  Full screen apps show as windowed, along with any minimised apps.

Edit: I think you're talking about something different here, specifically where the window opens up when you launch a new application.  I'm talking about the preview panes on the task switcher - the preview pane does not resemble the actual layout of the workspace as it tries to show all the applications tiled around the center of the workspace, even if they are actually minimised.

> 
I was going to give it a couple of days and a couple of updates before reporting bugs. If you report a bug, could you post the number in this thread?

Will do.  It seems like planned behaviour though, maybe there's some settings somewhere, but I swear I haven't been messing with Compiz.  Looks like I'll have to try that and see what happens.

Chris

---

### Post by fabricator4 on 2011-04-02
> **mc4man said:**
> "Workspace switcher" - gathering that you're not talking about the  Workspace switcher in the launcher - that does show workspaces as they are
(and no minimized), it is the expo plugin


No, I **_am_** talking about the Workspace Switcher in the launcher.  It's really freaky.

> 
If referring to the scale function 'window picker for all windows'  - super+w, then you're not looking at a workspace, it a display screen to pick the window you wish


I don't know about super-w, but pressing super numbers the icons in the launcher, implying that you can select them with super-1, super-2 etc

> 
If you're getting minimized windows thru scale  then you've enabled 'keep previews...' in workarounds, which while it works can cause unexpected behavior
(and is a currently unsupported option

Not as far as I'm aware.  What's involved in setting this?  I've never tried.  It also works the same (strange) way in Unity 2D, so I think that discounts the likelyhood of this being a setting in compiz or any Unity 3d only features.

Chris.

---

### Post by ranch hand on 2011-04-02
Both Unity and CS CLAIM to be great for work spaces.

I use 6 at all times.  In both Unity and GS I see it as much easier to just use one and for get the work spaces altogether   Neither Unity or GS has any support for them that is in any sense usable to me.

That means that, to me, neither of them are worth the powder and lead to blow them to hell.

---

### Post by mc4man on 2011-04-02
> No, I am talking about the Workspace Switcher in the launcher. It's really freaky.


All that does is call the expo plugin (also super+s), it should just show all your workspaces and _open windows_ in the exact placement they are in. (nothing should be moved

The expo mode is slightly interactive - you can move windows within a workspace or from one to the other.
Also the launcher is active when in expo, any newly opened windows while in expo should open  on the highlighted workspace though that doesn't usually work out. (tend to open on last active space before expo

Ex. (I use rotate instead of wall so am using a 1X4 instead of default 2X2
screen 1 a number of windows open - all are shown exactly where they are.
sceen 2 - while in expo opened audacious in workspace 1, moved the Gkrellm window to ws 4, when returning back to the desktop all windows are where seen in expo

---

### Post by fabricator4 on 2011-04-03
> **mc4man said:**
> All that does is call the expo plugin (also super+s), it should just show all your workspaces and _open windows_ in the exact placement they are in. (nothing should be moved


I couldn't figure out why none of this working for me and then I realised: I'm on the machine running 2D.  Then another bolt of lighting hit, and I realised the eeepc was running 2d also - I must have changed it when fiddling, and forgot to change it back since I didn't use it except to look at the task switcher when I was having trouble.

Changing it back to Unity 3d, and the switcher operates as it should.

Ok, that looks like a bug with the switcher under Unity 2d then, but which do I file the bug under, Unity 2D or the switcher module (whatever it may be called)

My feeling at the moment is that Unity 2D is nowhere near as solid as Unity 3D.  I hope they have it all fixed up by launch otherwise there's going to be lots of confused people running low on memory out there...

Chris.

---

### Post by seeker5528 on 2011-04-04
> **fabricator4 said:**
> My feeling at the moment is that Unity 2D is nowhere near as solid as Unity 3D.  I hope they have it all fixed up by launch otherwise there's going to be lots of confused people running low on memory out there...

Unity-2D is a late comer. From the time it was announced it wasn't expected to be on par with Unity-3D during this development cycle. It's supposed to get more serious work in the next.

I never used Compiz much in the past, but I believe the work space and window switching rely on native compiz plugins.

Looking at the package descriptions in Synaptic it looks like there is something specific to Unity-2D providing the window switching, unity-2d-spread > The Unity 2D spread allows you to display a quick thumbnailed view of open
windows so you can quickly and effectively choose which one you want to
switch to. It is part of Unity 2D and can not run  as a standalone application
outside of the Unity 2D environment

Which would be something written from scratch and I suspect may also be what is providing desktop switching if there is separate workspace switcher on the Unity-2D panel. Since it does have to be written from scratch, I wouldn't expect too much out of it on this development cycle. That's not to say there shouldn't be a bug filed though.

Later, Seeker

---

