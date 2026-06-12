---
title: "Opening VIDEO_TS folder"
date: 2011-06-29
forum: Multimedia Software
---

### Post by nomko on 2011-06-29
Some wierd issue here: when i sued verison 10.04 i could right click on the VIDEO_TS an select "open with Vlc". Now i'm running 10.04.2 and that option is gone. And it cannot be fixed either. Right click gives me what is shown in the screenshot (excuse me for the language, it is in Dutch). Does anyone know how to fix it?

---

### Post by coffeecat on 2011-06-29
If you left-click on what you've highlighted, that should open another window in which you can select VLC.

Have a look at my two screenshots, both taken in Lucid/10.04, fully updated, running as a virtual machine in VirtualBox. The first is where I've right-clicked and highlighted "Open with Other Application". ("Met andere toepassing openen" :wink:). The second is where I've left-clicked on "open with..." and I can select and open VLC. Is this not what you get?

---

### Post by nomko on 2011-06-29
Not really, That i know. But what i want is more like this (see screenshot for example). I know i had this under 10.04 (first release of 10.04 LTS). And now with 10.04.2 i don't have this no longer.

The example screnshot was taken from a .avi file in which Vlc is placed at the top as first choice.

---

### Post by haqking on 2011-06-29
> **nomko said:**
> Not really, That i know. But what i want is more like this (see screenshot for example). I know i had this under 10.04 (first release of 10.04 LTS). And now with 10.04.2 i don't have this no longer.

The example screnshot was taken from a .avi file in which Vlc is placed at the top as first choice.

doesnt that appear once you choose to open with a given application.  Once you have done that once then i think it appears on the right click does it not ?

infact yes it does i just tried it

though i cant read dutch so i might be way off mark ;-)

---

### Post by nomko on 2011-06-29
I know what you mean, but it doesn't. I even can't check/uncheck whether Vlc has to be the standard program for opening such folders. As you can see in the screenshot there's no such box to be checked/unchecked or the line "*Remember this application for files of type**'.....'* ". Don't know how/what/where...

---

### Post by coffeecat on 2011-06-29
> **nomko said:**
> I know i had this under 10.04 (first release of 10.04 LTS). And now with 10.04.2 i don't have this no longer.

You are quite right. I hadn't noticed that in Lucid before, if only because I don't use Lucid much theses days. If I open an AVI in VLC with a right-click, then VLC appears as an option in the context menu for AVIs thereafter. But not with VIDEO_TS folders. Whereas it does in Natty.

Sorry - I don't know what the answer is in Lucid.

---

### Post by haqking on 2011-06-29
I am in 10.10

I right clicked a folder (any folder) and chose to open it with vlc, of course it doesnt (and i didnt say remember app) now when i right click a folder again it comes up with VLC in the menu thereafter

---

### Post by nomko on 2011-06-30
> **coffeecat said:**
> You are quite right. I hadn't noticed that in Lucid before, if only because I don't use Lucid much theses days. If I open an AVI in VLC with a right-click, then VLC appears as an option in the context menu for AVIs thereafter. But not with VIDEO_TS folders. Whereas it does in Natty.
 
Sorry - I don't know what the answer is in Lucid.
 
At least it is conformed that it's not only my system with this issue. Why is it removed in the later 10.04 version? Really strange. Could it be a bug?

---

### Post by coffeecat on 2011-06-30
Could it be a bug? Interesting question. It's certainly a usability issue.

Just a theory, but I wonder if this is related to a now-fixed bug. It used to be - and not just in Lucid - that if you right-clicked a VIDEO_TS folder (or other folder) and "opened with" a media player, there was a "remember this application" tickbox which was ticked by default. The consequence of this was that the system then remembered the media player when opening any folder. There used to be regular threads from people who were double-clicking on home or any folder and VLC/Banshee/you-name-it was opening instead of Nautilus.

These threads seem to have declined now and I notice that in Natty the remember tickbox has disappeared for folders but not for other file types. Perhaps by fixing one bug, another has been introduced, at least in Lucid.

One other thing I notice in Natty is that now I have opened a VIDEO_TS folder with VLC, if I right-click on any folder, "Open with VLC Player" appears above "Open With Other Application". Which is convenient for VIDEO_TS folders but mildly disconcerting for other types of folders. But, of course, this is what you want in Lucid and are not getting.

---

### Post by mc4man on 2011-06-30
A few things - 
All folders are treated the same so you should be seeing vlc as a choice from the r. click > open with other application list whether a VIDEO_TS or any other folder (vlc registers inode/directory as a mimetype

Screen 1 shows that on 10.04.2

As far as the nautilus bug fix and in particular the effect in lucid
(I spent 7 months+ getting this fixed for 10.10 and 11.04, was a bit surprised it was also applied to 10.04 where it generally wasn't an issue, and does now create a small new bug in 10.04 only, mentioned below

What you may want to take a look at is ~/. local/share/applications/mimeapps.list
The line in question would be 
inode/directory=
You must have nautilus-folder-handler.desktop; at the front of the line - the first listed in 10.04 is the default
Any additional .desktops will show up directly in the r. click > open with menu, up to 2, after that it will become a drop down list

So if the line was
inode/directory=nautilus-folder-handler.desktop;vlc.desktop;
you'd see screen 2 - only vlc is shown

The issue with lucid post bug fix is .desktops are no longer auto added to the line from the r. click 'open with other application' menu, they must be added manually, screen 3 shows after I added vlc for above, then totem and smplayer
(this is the new 'bug', myself, at this point, will probably not take the time to try to get that 'fixed'

So - first it;s odd that vlc isn't a choice in the main list, maybe open synaptic, mark vlc-data for removal and do so. Then re-install vlc

Also open mimeapps.list, you can post the inode/directory= line or edit it as I have, make sure that nautilus-folder-handler.desktop; is first, then add in vlc.desktop; and any others
(wouldn't know if the file is in English or Dutch, the inode/directory= line should be obvious

---

### Post by nomko on 2011-06-30
That tickbox seems to be missing now. But it's not such a drama for me. Just a few clicks more. It's only very strange that it has gone in 10.04.2 but back in natty....

---

### Post by mc4man on 2011-06-30
> **nomko said:**
> That tickbox seems to be missing now. But it's not such a drama for me. Just a few clicks more. It's only very strange that it has gone in 10.04.2 but back in natty....
I can 100% guarantee you the 'tickbox' (remember..) is not in natty or maverick for folders, that was the whole point of the bug fix.
It is still available and enabled by default on files, so when used the default for that filetype will be changed to app chosen.

---

