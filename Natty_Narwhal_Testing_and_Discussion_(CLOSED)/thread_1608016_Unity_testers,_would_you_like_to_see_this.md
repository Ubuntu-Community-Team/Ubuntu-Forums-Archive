---
title: "Unity testers, would you like to see this?"
date: 2010-10-28
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Bou on 2010-10-28
I recently proposed the following to Launchpad and the Unity mailing list, but there are a couple rough edges to polish. Please take a look at these mockups first:

[IMG]http://imgur.com/i1pKr.png[/IMG] [IMG]http://imgur.com/aykrO.png[/IMG]

Do you see those purple spaces in the sidebar, containing the launchers? They represent workspaces and are used to handle them:

- By default there is only a workspace, represented by an empty purple square. You can't open a new empty workspace because, why would you want that? You have a perfectly good one, like, right there.

- Once you open an app, its launcher appears inside the purple space and a second purple space (empty workspace) appears in the launcher. That would be the first mockup: in it, I have Firefox and Hamster open so their launchers appear there.

- If you navigate to the second workspace and then open an app, that app's launcher appears on the second purple space, and a third workspace appears. That would be the second mockup, where I navigated to the second workspace and then opened GIMP. The same results would have happened if I had opened GIMP in the first workspace, then dragged its launcher to the second purple space.

- You can easily move windows between workspaces by dragging their launchers to one purple space or another.

- You can easily switch to a workspace by clicking it, since they show an empty space above the launchers in them.

- You can easily call expose on a single workspace if you click again in that empty space.

- You can easily reorder workspaces by dragging them up or down in the sidebar.

- You can easily open an app in a certain workspace by dragging it from the dash to a particular empty space.

- You can easily set in which workspace you want "favourite" apps to open by dragging their "pinned" launcher to its corresponding purple space.

- It allows you to visually separate apps on the active workspace from apps on other workspaces, thus saving you time to find e.g. a particular app you want to restore.

However, there are a couple downsides to it:

- If an app has open windows on more than one workspace, where should its launcher appear? In the active one? In both?

- Also, how would you launch a "general" expose, showing all workspaces, without adding an additional button?

I hope we can get some brainstorming here guys :P

---

### Post by cariboo on 2010-10-28
There already is a workplace switcher in the panel, it doesn't do everything you've specified, and some of them would be nice enhancements.

One thing I would like, it a way to increase the number of workspaces.

---

### Post by MacUntu on 2010-10-28
IIRC Mutter uses /apps/metacity/general/num_workspaces (I definitely had more than four workspaces once).

---

### Post by Bou on 2010-10-28
> **cariboo907 said:**
> There already is a workplace switcher in the panel, it doesn't do everything you've specified, and some of them would be nice enhancements.

Yeah, the question is... would having the workspace thing AND the switcher clutter things up? How would you trigger a general expose *without* that switcher?

> **cariboo907 said:**
> One thing I would like, it a way to increase the number of workspaces.

I might not have made myself clear. This system would ensure that you always have ONE empty workspace. If you use any window inside, another workspace is created. If you close that window, the new workspace disappears.

Always one empty workspace, never more, never less.

---

### Post by donniezazen on 2010-10-28
I would love to have android like widgets pinned down to different workspaces (social, productivity, system, music and movies etc.).  Something that completely minimizes the need to go to nautilus to open the files. Are there any shortcuts to quickly move from 1 workspace to other and take a look of all the spaces.

---

### Post by Decatf on 2010-10-28
I like this idea. It sounds great because you have as many workspaces as you need and only as   many as you need. It is dynamically sized and it is easy to start a new   one. Plus you can have some nice functionality in it. I haven't used Unity much but I've installed it today  after all the hubbub lately. I am not sure if all of this is possible  but I am just throwing this out here for the sake of discussion and/or  brainstorming.


Might it be better to use the existing workplace switcher icon as it is.  Rather make it expandable (on double click?) to show the "workspace  manager" or purple spaces as described in OP.

Single click: Expose all workspaces. (i.e. current behaviour / general expose)
Double click: Expand workspace manager. 

Or it might work better if the activation were reversed:

Double click: Expose all workspaces.
Single click: Expand workspace manager. With primary focus being your current workspace. 
- Default mode - Expose on current workspace
- Expose on specific app by clicking it's icon in the workspace manager
- Can still drag a single window onto other workspaces.
- Can drag all windows of an application to another workspace (by dragging app icon from one purple space to another)
- Can easily obtain to a new workspace by using the blank one
- Single click another workspace to switch focus of workspace manager to that one
- Double click a workspace to switch to it and close workspace manager

Now the downsides. 
One extra click to switch to another workspace. However it is still two clicks to get to a blank/new workspace. (i.e. Single click workspace switcher. Single click blank workspace.)
Having excessive of workspaces and applications running will crowd up the side bar. This can be solved by having a minimized mode where application icons are collapsed into a stacked mode. All workspaces except the one in focus are in minimised mode.  Hovering over the workspace with your mouse expands it.


I find that more often than not I tend to need to manage workspaces individually. Less often do I need cross workspace management. (i.e. expose all workspaces and windows). Also to me it is too much to going on to expose all windows and workspaces just to switch to another workspace. Both visually and performance wise it is not necessary to do a general expose the majority of the time.

Thoughts? Crap? Like? See a psychiatrist? =P

---

### Post by ranch hand on 2010-10-28
@Decatf
You really need to see the shrink.  You use linux.

I like your ideas a bunch.  The work space management is the week spot for those of us that use them a lot.

The only objection I have is the damned purple but I bet I can change that in a hurry.  Ghastly color.  Better than the ailamentary tract brown in 9.10 though.

---

### Post by dinamic1 on 2010-10-28
warkspaces? NO NO! use only one BIG workspace (virtually infinite) and add some cool paralax wallpaper and some lasers! How cool is that?

---

### Post by Bou on 2010-10-29
> **Decatf said:**
> I like this idea. It sounds great because you have as many workspaces as you need and only as   many as you need. It is dynamically sized and it is easy to start a new   one.

Yes, that was not originally what I had in mind but it turned out to be my favourite feature too :)

> **Decatf said:**
> Might it be better to use the existing workplace switcher icon as it is.  Rather make it expandable (on double click?) to show the "workspace  manager" or purple spaces as described in OP.

Single click: Expose all workspaces. (i.e. current behaviour / general expose)
Double click: Expand workspace manager.

I'd rather not have the workspace switcher, because the workspace headers already take space and I really don't want to clutter the sidebar. Besides, I want to have only the necessary UI elements, so if there is a way to trigger a general expose using only the elements in the mockup.

What I thought is, how about triggering it using the purple spaces themselves? For example:

- You switch to a workspace by clicking its purple space.
- If you click on the active workspace's purple space, you trigger expose for that workspace.
- If you click it again, you trigger expose for all workspaces.

How would that be? That's similar to what you proposed, only without the switcher.

> **Decatf said:**
> I find that more often than not I tend to need to manage workspaces individually. Less often do I need cross workspace management. (i.e. expose all workspaces and windows). Also to me it is too much to going on to expose all windows and workspaces just to switch to another workspace. Both visually and performance wise it is not necessary to do a general expose the majority of the time.

Totally agreed. That's why the primary expose would be workspace expose, not general expose.

> **ranch hand said:**
> I like your ideas a bunch.  The work space management is the week spot for those of us that use them a lot.

The only objection I have is the damned purple but I bet I can change that in a hurry.  Ghastly color.  Better than the ailamentary tract brown in 9.10 though.

Details, details!

> **dinamic1 said:**
> warkspaces? NO NO! use only one BIG workspace (virtually infinite) and add some cool paralax wallpaper and some lasers! How cool is that?

That's a bit out of the scope here, cool nonetheless :P

By the way, here's the link to the Launchpad bug: [https://bugs.launchpad.net/unity/+bug/667245](https://bugs.launchpad.net/unity/+bug/667245) just in case you want to give your 2 cents.

---

### Post by Bou on 2010-10-29
By the way, I thought of a possible solution to this problem:

> **Bou said:**
> If an app has open windows on more than one workspace, where should its launcher appear? In the active one? In both?

First I thought of showing multiple launchers, one for every workspace where the app has a window, but that would be against Unity's approach of "one app, one launcher". So I thought another possibility:

- Imagine you have three workspaces, and you have Firefox windows on WP1 and WP2.
- When you're on WP1, FF's launcher appears on the first purple space.
- When you move to WP2, the launcher has some kind of animation and moves to the second purple space.
- Whenever you move to WP3, the launcher stays in the last purple space where it was. For example, if you move from WP1 to WP3 the launcher stays in the first purple space, but if you move from WP2 to WP3 the launcher stays in the second purple space.

Would that be confusing, having a launcher moving up and down?

---

### Post by dv3500ea on 2010-10-29
I think this is a really good idea and would make workspace management easy. In fact, I think this is better than what we currently get with the workspace switcher applet on gnome-panel. I think the icon moving between workspaces would be fine.

> **Bou said:**
> 
- Also, how would you launch a "general" expose, showing all workspaces, without adding an additional button?


I think it would be good to use the bottom right hand corner as a 'hot' corner. You can currently set up screen corner bindings in compiz. I use the bottom right hand corner in conjunction with compiz scale and it works really well. A corner is a very easy thing to hit with your mouse because it is infinitely large in 2 directions.

I propose this should give an overview of all workspaces equally spaced on the screen and all windows equally spaced on their workspace. It would also be nice if minimised windows were shown, at least by their icon, as scale currently does not have this ability.

There is a problem with this - how would the user know to do this?

I suggest that the corner could be highlighted to show that it actually does something.

---

### Post by Bou on 2010-10-29
> **dv3500ea said:**
> I think this is a really good idea and would make workspace management easy. In fact, I think this is better than what we currently get with the workspace switcher applet on gnome-panel. I think the icon moving between workspaces would be fine.

You mean, when an app has windows in more than one workspace?

> **dv3500ea said:**
> I think it would be good to use the bottom right hand corner as a 'hot' corner. You can currently set up screen corner bindings in compiz. I use the bottom right hand corner in conjunction with compiz scale and it works really well. A corner is a very easy thing to hit with your mouse because it is infinitely large in 2 directions.

I see a big problem with that, new users. I have seen many new users who absolutely do NOT want to use multiple workspaces. They're not used to them, they don't understand them and for them they just get in the way.

I think putting workspaces in the dock is OK for those people, because they actually have to point and click to get to another workspace or trigger expose. But using a hot corner... well, I almost can see my girlfriend triggering it by mistake, hear her yelling at me because her computer is doing weird things and it "sucks".

I think a hot corner is TOO easy to reach.

By the way, there is another advantage to this approach:

When there are too many launchers, some of them will shrink to make space. The problem now is that they don't take into account whether they are apps you may want to return to, they only take into account their position in the dock.

With my proposal, docks could be shrunk according to the workspace they're in: that way, launchers in the active workspace would keep their normal size, while those in inactive workspace would shrink first if needed. This is what I mean:

[IMG]http://imgur.com/fZKd6.png[/IMG]

---

### Post by jerrylamos on 2010-10-29
Workspaces?  I use one.  I'm hardly a new user since I started on the IBM PC in 1982.  Having said that I'm an "ordinary user" with an eye out for Natty bugs that might show up commonly.

For those that like "eye candy" then big fancy pictograms (hieroglyphics) then let them have them.  KDE, Apple, ... certainly have fans.

I do fine with simple buttons on the top line of the screen for common stuff.  Let me have all the rest for applications like Firefox and writer and spreadsheets and digital photography full screen with long drop down lists when needed for Applications > Accessories, System > Preferences, etc.  

I've got over 300 bookmarks in a sorted list which is easy to handle.  Big pictures with a few bookmarks is useless to me.

So I'm all set as is, so hopefully I'll be able to opt out of the eye candy.

Jerry

---

### Post by go7Ul1ai on 2010-10-29
> **jerrylamos said:**
> 
So I'm all set as is, so hopefully I'll be able to opt out of the eye candy.

That should be fine, as Unity for the desktop is being implemented as a Compiz plugin.

---

### Post by dino99 on 2010-10-29
hi great dreamers :)

just read that interesting thread. What i like in this project is the way to split my lcd window into several smaller windows inside the same workplace.
Dont really need eye-candy funky flashy unusabled jumping loaders from numerous workplaces, dont know how others work but i've only two eyes and they can only glance at the same target at once.

Of course a conf file can be built to customize this project with a bunch of settings, as numerous great ideas have been pushed here. In case of switching multiple windows, why not using arrows keys too?

---

### Post by gunashekar on 2010-10-29
i was always a single workspace user and never used a second workspace or clicked on the workspace switcher wherever it was located. 
I installed unity and somehow I started using 4 workspaces. 
Any enhancement to the workspace management should be welcome as long as I am able to view all 4 workspaces or select another workspace with a single click.

---

### Post by teachop on 2010-10-29
> **Bou said:**
> 
With my proposal, docks could be shrunk according to the workspace they're in: that way, launchers in the active workspace would keep their normal size, while those in inactive workspace would shrink first if needed. This is what I mean:


I like this thinking...

---

### Post by zekopeko on 2010-10-29
I like what Apple did for OSX 10.6. They call it Mission control. It is basically a one-stop shop for Expose (Scale on Linux), Workspace switcher and full screen apps that have their own workspace.

The video is on youtube.

---

### Post by juancarlospaco on 2010-10-29
This is not easy to explain to new users, visually confusing...

---

### Post by ronacc on 2010-10-30
anything can be confusing until you get used to it . especially if it is different from what you are already used to .Perhaps we need some short ( 2 or 3 minute ) visual tutorials demonstrating the new and different features , keep them short and only cover one feature each .

---

### Post by Bou on 2010-10-30
Wow, I actually got a reply [from the man himself]("https://bugs.launchpad.net/unity/+bug/667245/comments/10") :-) I'm in nerd bliss right now.

Apparently he wants to keep the current layout (for now, he says politely) but it's pretty cool nonetheless.

I made a final mockup summarizing the idea's main points, because it changed a lot after getting some feedback in the mailing list. So here it is:

[CENTER][IMG]http://i.imgur.com/OWGro.png[/IMG][/CENTER]

I can't help it, I just love the way it looks.

---

### Post by plun on 2010-10-30
> **Bou said:**
> Wow, I actually got a reply [from the man himself]("https://bugs.launchpad.net/unity/+bug/667245/comments/10") :-) I'm in nerd bliss right now.

I can't help it, I just love the way it looks.

Well.... I also like your ideas...:)   
 
And also a reply from "sabdfl" himself....=D>

I must also post this with an interesting discussion included.
[http://www.webupd8.org/2010/10/interesting-unity-concept-for-managing.html](http://www.webupd8.org/2010/10/interesting-unity-concept-for-managing.html)

I hope we will se more ideas from you Bou.... much appreciated !:)

---

### Post by plun on 2010-10-30
Followup from OmgUbuntu

[http://www.omgubuntu.co.uk/2010/10/workspace-representation-in-unity/](http://www.omgubuntu.co.uk/2010/10/workspace-representation-in-unity/)

;)

---

### Post by Bou on 2010-10-31
> **plun said:**
> Followup from OmgUbuntu

Got a lot of retweets too... glad to see so many people did appreciate it.

---

### Post by Bou on 2010-10-31
> **plun said:**
> I hope we will se more ideas from you Bou.... much appreciated !:)

Here's another one, plun. I just sent it to the mailing list:

> Hi,

One of the few problems I have with Unity is that there is no way to perform window-specific actions from the launcher: everything is app-specific. I can press the launcher icon to focus an app's most recent window, but I can't focus a specific window. I can't minimize a window by clicking the launcher icon, see an app's different windows without focusing it, or launch a new window.

I propose replacing Unity's current behaviour when you hover on a launcher icon (where you only get the app's name) with something like this: 

[IMG]http://imgur.com/1cP0B.png[/IMG]

- When you hover the cursor over Unity's launcher icon, you get a preview of all the open windows belonging to that app.
- If one of them is the active window, it has some kind of visual indication (in the mockup it has an orange box around).
- You can click the active window to minimize it, or click an inactive window to focus it.
- You can right-click a window to get a contextual menu, where you can perform operations such as minimize, maximize, close, send to another workspace...
- You can click a button (in the mockup, located at the left) in order to open a new window for that app.
- You can drag that specific window, which solves the problem raised by Mark Shuttleworth ([https://bugs.launchpad.net/unity/+bug/667245/comments/10](https://bugs.launchpad.net/unity/+bug/667245/comments/10)) about dragging launcher icons to other workspaces.

I would like the Ayatana team to consider implementing along the lines.

Truth be told, Unity is shaping up to be amazing but, being a new tool, it has lots of room for improvement.

---

### Post by kyleabaker on 2010-11-10
> **ranch hand said:**
> The only objection I have is the damned purple but I bet I can change that in a hurry.  Ghastly color.  Better than the ailamentary tract brown in 9.10 though.

This was my reaction exactly. :P

I do like the ideas floating around here though. :guitar:

---

### Post by pihbar on 2010-11-13
This is an excellent idea that shows clear thinking, as opposed to just copying functionality others have. Most of the time I use one workspace, but when I need to, I want to easily drag an icon to the next one. Your interface makes this trivial.

**Is there a brainstorm for this idea so that I (and others) may vote for it?**

---

### Post by Bou on 2010-11-14
There is a launchpad bug as well as a discussion in the Ayatana mailing list, where your opinion would be welcome. I haven't used brainstorm for a while, but I can start a thread there if you guys think it's worth it.

---

### Post by Bou on 2010-11-23
Wow, it seems that the gnome-shell guys intend to make the shell work [as I suggested]("http://jimmac.musichall.cz/log/?p=1107&cpage=1#comment-55937"), at least regarding the automatic workspace management :D

> **Bou]The idea is that you always have one (but not more) empty workspace. When you boot up your system you only have a workspace, since there are no open windows. But as soon as you open a window, a second empty workspace appears at the end of the workspace sidebar. You can open as many windows as you want on the first workspace and it won&#8217 said:**
> 

[quote=Jimmac]**That is indeed the direction we&#8217;re going with this now**

---

### Post by knarf on 2010-11-24
This is what I'd like to see happen in Unity:

```
$ ps aux|egrep 'CPU|xmonad-i386'
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
frank     1731  0.0  0.3  11820  3012 ?        Ss   Nov19   0:55 /home/frank/.xmonad/xmonad-i386-linux
```A window manager which takes less than 3 MiB in resident memory. It currently manages 9 workspaces, each with their own name and function (**T**erminal, **E**ditor, **G**raphics, **W**eb, **M**ail, e**X**perimental, **A**udio, **V**ideo and remote (**Z**)). Newly opened windows appear in relevant workspaces, eg. a new browser window appears in workspace '**W**eb' while a graphics program like Gimp or a viewer like gqview pops up in the '**G**raphics' workspace. Those workspaces are represented by simple symbols which light up when something interesting happens. You can use the keyboard (alt+workspace number) to switch to a workspace or you can click on those symbols. The little green picture next to the workspace symbols shows the current workspace tiling mode (full-screen in this case). On the right you'll find some system statistics as well as the notification area.

[IMG]http://www.unternet.org/files/dzen2_xmonad.png[/IMG]

A visual application launcher can be added for those who dislike typing 'Alt+P' followed by the first 2 or 3 characters of an application name. There are many candidates for this task (awn, cairo-dock, gnome-do, etc) so I won't elaborate on this. It is of course also possible to integrate that launcher as an *optional* extension in case more intimate interaction between the window manager and the launcher is required.

The beauty of this system is that is takes minimal system resources AND makes for a much more productive system - no more senseless window shuffling needed - but it is still possible for those who prefer it. It can also be customized to the user's exact requirements. Mind, it does not *need* to be customized any more than eg. Gnome Shell or Unity needs to be customized. It *can* be customized - a big difference and a big advantage.

This version of the idea is written in Haskell, including the configuration file. The same things can be done in any other compiled language (eg. Vala) if Haskell seems to daunting a prospect for a noob-focused distribution - but since noobs generally won't mess with their configuration files it should really not matter. Interpreted languages like python, ruby and javascript (viz. Gnome Shell) can also be used but will invariably raise resource requirements and lower performance on lower-spec hardware.

To summarize, it *is* possible to provide excellent functionality in a small footprint system. It does not *require* the use of compositing but of course this can be used if available for more glitzy effects. This opens up the system for lower-spec or older hardware which, for whatever reason (lack of hardware or - more commonly - driver support, absolute low power requirements, etc) can not support compositing while still keeping the door wide open for as flashy a desktop as the user wants. I happen to like my desktop compact and concise so I used simple and small symbols. If you want to see purple squares with smooth sliding icons that can be arranged as well.

---

### Post by madjr on 2010-11-25
> **knarf said:**
> This is what I'd like to see happen in Unity:

```
$ ps aux|egrep 'CPU|xmonad-i386'
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
frank     1731  0.0  0.3  11820  3012 ?        Ss   Nov19   0:55 /home/frank/.xmonad/xmonad-i386-linux
```A window manager which takes less than 3 MiB in resident memory. It currently manages 9 workspaces, each with their own name and function (**T**erminal, **E**ditor, **G**raphics, **W**eb, **M**ail, e**X**perimental, **A**udio, **V**ideo and remote (**Z**)). Newly opened windows appear in relevant workspaces, eg. a new browser window appears in workspace '**W**eb' while a graphics program like Gimp or a viewer like gqview pops up in the '**G**raphics' workspace. Those workspaces are represented by simple symbols which light up when something interesting happens. You can use the keyboard (alt+workspace number) to switch to a workspace or you can click on those symbols. The little green picture next to the workspace symbols shows the current workspace tiling mode (full-screen in this case). On the right you'll find some system statistics as well as the notification area.

[IMG]http://www.unternet.org/files/dzen2_xmonad.png[/IMG]

A visual application launcher can be added for those who dislike typing 'Alt+P' followed by the first 2 or 3 characters of an application name. There are many candidates for this task (awn, cairo-dock, gnome-do, etc) so I won't elaborate on this. It is of course also possible to integrate that launcher as an *optional* extension in case more intimate interaction between the window manager and the launcher is required.

The beauty of this system is that is takes minimal system resources AND makes for a much more productive system - no more senseless window shuffling needed - but it is still possible for those who prefer it. It can also be customized to the user's exact requirements. Mind, it does not *need* to be customized any more than eg. Gnome Shell or Unity needs to be customized. It *can* be customized - a big difference and a big advantage.

This version of the idea is written in Haskell, including the configuration file. The same things can be done in any other compiled language (eg. Vala) if Haskell seems to daunting a prospect for a noob-focused distribution - but since noobs generally won't mess with their configuration files it should really not matter. Interpreted languages like python, ruby and javascript (viz. Gnome Shell) can also be used but will invariably raise resource requirements and lower performance on lower-spec hardware.

To summarize, it *is* possible to provide excellent functionality in a small footprint system. It does not *require* the use of compositing but of course this can be used if available for more glitzy effects. This opens up the system for lower-spec or older hardware which, for whatever reason (lack of hardware or - more commonly - driver support, absolute low power requirements, etc) can not support compositing while still keeping the door wide open for as flashy a desktop as the user wants. I happen to like my desktop compact and concise so I used simple and small symbols. If you want to see purple squares with smooth sliding icons that can be arranged as well.

that looks cool, but probably too geeky/techie for unity.

probably better to create this bar / plugin from scratch.

---

### Post by madjr on 2010-11-25
> **soham_1207 said:**
> I would love to have android like widgets pinned down to different workspaces (social, productivity, system, music and movies etc.).  Something that completely minimizes the need to go to nautilus to open the files. Are there any shortcuts to quickly move from 1 workspace to other and take a look of all the spaces.

kde has this now with "activities", but i find it much less intuitive still than with android.


[http://kde.org/announcements/announce-4.6-beta1.php](http://kde.org/announcements/announce-4.6-beta1.php)

---

### Post by seeker5528 on 2010-11-26
> **madjr said:**
> kde has this now with "activities", but i find it much less intuitive still than with android.

Activities don't work that way in KDE.

Yes you can put different widgets on different desktops, but those are desktops not activities an activity would include all your desktops.

If you wanted to set up 'Video Editing' as an activity, you would create a new activity with that name and then you could set up desktop one with stuff related to the main editing task, desktop 2 for audio related stuff, desktop 3 for image/frame editing stuff, and maybe have desktop 4 for blender and related stuff.

So every time you switch to the 'Video Editing' activity all your desktops will be set up the way they were the last time you were using that activity.

If you switch back to the default desktop activity, all your desktops will be the way they were when you last used the desktop activity.

If you only customize individual desktops without creating a new activity, you are not using activities, just customizing individual desktops.

> **knarf said:**
>  Newly opened windows appear in relevant workspaces, eg. a new browser window appears in workspace '**W**eb' while a graphics program like Gimp or a viewer like gqview pops up in the '**G**raphics' workspace.

They did something like that in Afterstep, I hated it, haven't used Afterstep since, so it may or may not still be that way.

Later, Seeker

---

### Post by knarf on 2010-11-27
> **madjr said:**
> that looks cool, but probably too geeky/techie for unity.

probably better to create this bar / plugin from scratch.
That bar is just a visual gimmick, the window (/workspace) manager works fine without it - or with a gnome panel or a dock instead of the bar. The bar only shows what is happening, it does not have any influence over the window management policy.
The essence of my post is not so much that I want Unity to be replaced by Xmonad or something similar. It is that it would be good if Unity would run on the same hardware as the example I gave. As it stands now it does not, both because of the mandatory compositing - which excludes a whole slew of perfectly capable systems - as well as the substantial resource requirements. It is a window/workspace manager, it should just do its thing and be as invisible as possible - both visually as well as in terms of resource consumption.

---

### Post by knarf on 2010-11-27
> **seeker5528 said:**
> They did something like that in Afterstep, I hated it, haven't used Afterstep since, so it may or may not still be that way.
In this case there are no 'they', there is only 'me'. I configured it this way because it fits the way I work. If you want it to be different, it can. It can be as different as you want it to be.
That configurability is a good thing - choice is good. Beginners don't need to configure it, they can choose the default 'theme' or maybe one of the alternative 'themes'. The theme can contain both visual elements as well as window management policy.
An advantage of the policy I described - where applications live on their own specific workspaces - is that it makes it very easy to switch between them. Instead of alt-tabbing through a stack of windows or mousing your way over a taskbar you press Alt+workspace number. That number is *always the same*. In my configuration Alt-4 **always **leads to the browser window(s). Alt-1 **always** leads to the terminals, etc. This takes the guesswork out of navigation and makes it easy to work with many distinct application types simultaneously.

---

### Post by seeker5528 on 2010-11-27
> **knarf said:**
> Beginners don't need to configure it, they can choose the default 'theme' or maybe one of the alternative 'themes'. The theme can contain both visual elements as well as window management policy.

If you already are using something that does this for you and you choose to use it, that's fine. Why should Unity do it?

And beginners shouldn't *have* to choose. If they *want* to run a specific app on a specific desktop, they can always switch to that desktop, then start the app, or start the app, then move it to that desktop.

> An advantage of the policy I described - where applications live on their own specific workspaces - is that it makes it very easy to switch between them. Instead of alt-tabbing through a stack of windows or mousing your way over a taskbar you press Alt+workspace number.

'Alt'+'Tab'ing your way through a half a dozen open windows doesn't seem that big of a deal, typically they are represented visually so you can tell them apart.

Mousing over a bar showing your running apps doesn't seem like that big of a deal either.

But it *is* nice to be able to use a key combination to switch to a specific desktop as well.

I think people in general would prefer something more activity/task based in a desktop environment. 

For some tasks you may want your email running on the same desktop with one or more other apps, for another task you may want your audio application open on the same desktop with some other apps. And maybe if you are on one desktop doing something and want to preview an image, you want the image program to open the image on the desktop that is in front of you and not the one the image apps are forced to open on, then have to switch there to view the image, and switch back after.

Later, Seeker

---

### Post by knarf on 2010-11-27
> **seeker5528 said:**
> If you already are using something that does this for you and you choose to use it, that's fine. Why should Unity do it?
The 'this' which I am mostly getting at is the ability to run on hardware made more than 4 years ago. The reason as to why Unity should have 'this' capability should be clear.

> And beginners shouldn't *have* to choose. If they *want* to run a specific app on a specific desktop, they can always switch to that desktop, then start the app, or start the app, then move it to that desktop.Who says they *have* to choose? They don't * have* to choose more than in the current situation where they *can* choose to have their desktop look, and to a certain extent behave differently from the default.
> 'Alt'+'Tab'ing your way through a half a dozen open windows doesn't seem that big of a deal, typically they are represented visually so you can tell them apart.

Mousing over a bar showing your running apps doesn't seem like that big of a deal either.7 terminals, 1 web browser, the GIMP, a remote session on the server and a music player. You want to go from terminal number three to the GIMP. Quick, how many times do you need to Alt-tab?
> But it *is* nice to be able to use a key combination to switch to a specific desktop as well.It is. It is even better when you know what that workspace will contain without having to look at icons, pictures, small representations of windows or other such visual aids. Those visual aids can help, of course, but the ability to go there without having to look is even better.
Are you a touch typist? If so, you will understand the benefit of relying on motor memory instead of visual clues to perform common tasks. The same goes for organizing your desktop.
> I think people in general would prefer something more activity/task based in a desktop environment.If only there were a way of finding out what 'people' want... Of course they often don't know what they want before they have seen what is possible.

> For some tasks you may want your email running on the same desktop with one or more other apps, for another task you may want your audio application open on the same desktop with some other apps. And maybe if you are on one desktop doing something and want to preview an image, you want the image program to open the image on the desktop that is in front of you and not the one the image apps are forced to open on, then have to switch there to view the image, and switch back after.You don't have to switch to a workspace when a new program like that image viewer is opened, the computer can do that for you. [SIZE=1][COLOR=Silver]Trust the computer, the computer is your friend[/COLOR][/SIZE]. If, for some reason, you want to switch that program to another desktop that can be done easily, either by drag-dropping (in case you use those visual navigation aids) or by pressing some magic key combination (usually Alt-Shift-<workspace_number>).  Given that you currently have to do this all the time - want program A on workspace B, first switch to B, then start A - this does not seem to be a problem to me.

Anyway... after this long discourse about the pro's and con's of these specific traits of my environment let's bring the discussion back to the essence of my original message: *Unity should run on as wide a range of hardware as possible*.* This means it should gracefully degrade in the absence of compositing and it should be frugal when it comes to resource consumption*.

---

### Post by seeker5528 on 2010-11-29
> **knarf said:**
> The 'this' which I am mostly getting at is the ability to run on hardware made more than 4 years ago. The reason as to why Unity should have 'this' capability should be clear.

If you bought something 4 years ago that would have been considered decent at the time, chances are pretty good that you could run it. If you bought something that was short on RAM or had an off brand video hardware chances are less, which is typically more of a problem with laptops than with desktop systems.

For those cases where compatibility is an issue it is intended to fall back to the old desktop if Unity can't be run.

> You want to go from terminal number three to the GIMP. Quick, how many times do you need to Alt-tab?

How many people have 7 terminals open at once?
And of the people who would have that many terminals, how many would have that many terminal windows open as opposed to having them in tabs within one or two or three windows?

Having 7 of the same thing open is going to present it's issues, whether you have multiple desktops or not.

If things are not visually different enough to tell the difference, then you need some text identification, which I get, and it doesn't take much more time to 'Alt'(once)+'Tab'(7 times) than it does to 'Alt'(once)+'Tab'(once). But in those types of cases, if I could click one time to get a window list, click a second time to bring me to the window I want, I would prefer that over the alternatives.
 
> It is. It is even better when you know what that workspace will contain without having to look at icons, pictures, small representations of windows or other such visual aids. Those visual aids can help, of course, but the ability to go there without having to look is even better.
Are you a touch typist? If so, you will understand the benefit of relying on motor memory instead of visual clues to perform common tasks. The same goes for organizing your desktop.

I'm all for having the ability to customizing individual desktops differently for different tasks, and if you prefer certain applications to be open on certain desktops, you can start them there easily enough. Enforcing a policy of always running a certain program on a certain desktop is a whole different thing. Then you have to start asking if enough people would actually use it to make it worth providing that capability. 

> You don't have to switch to a workspace when a new program like that image viewer is opened, the computer can do that for you. [SIZE=1]Trust the computer, the computer is your friend[/SIZE].

And does it switch back again when you close the program?

> Anyway... after this long discourse about the pro's and con's of these specific traits of my environment let's bring the discussion back to the essence of my original message: *Unity should run on as wide a range of hardware as possible*.* This means it should gracefully degrade in the absence of compositing and it should be frugal when it comes to resource consumption*.

There was talk of having a libxrender backend for Compiz 0.9.x, which would provide compatibility with additional hardware, but whether this happened or not I don't know, and if it did happen I don't know how much duplication of effort this would required on the part of Unity developers to provide libxrender compatibility or even if any duplication of effort is considered worth it.  

Not using a boat load or resources is one thing, but even from a resource standpoint there are limits to how far the devs are willing to go to provide compatibility.

At the base level the devs have some idea of what kind of experience they want to provide and I can't really see them cutting down parts of the experience to appease people that have compatibility issues.

In cases where compatibility issues can be dealt with without cutting the experience, I think the devs will put a reasonable effort in to doing that.

Later, Seeker

---

