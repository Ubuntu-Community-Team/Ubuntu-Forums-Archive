---
title: "Should my Dash be in fullscreen"
date: 2011-03-17
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by go7Ul1ai on 2011-03-17
I'm running Natty with the latest updates on a laptop with a 17" screen and a resolution of 1366 x 768, I thought that this would be sufficient for a non-full screen dash. Is this a bug or is the Dash meant to default to fullscreen at this resolution/screen size?

Lee

---

### Post by mc4man on 2011-03-17
A few weeks ago on a 1280x800 (13"), dash was opening fullscreen
(I had to redo unity with a cutoff @ 85 % to keep windowed.

That install and redone unity is long gone - using iso's of the last week or so and dash no longer opens fullscreen on that laptop, dash appears to have been made slightly smaller (somewhere around 1180x560 on that laptop inc. the dash 'border'

---

### Post by kerry_s on 2011-03-18
i heard if it takes 75% of the screen it defaults to full.

my screens only 1024x768, i've always only had full screen.

---

### Post by go7Ul1ai on 2011-03-18
Hmm, before Places were implemented and there was a place holder dash, that wasn't in full screen and it didn't take much screen space at all really. Guess Ill see what happens!

---

### Post by mc4man on 2011-03-18
> Guess Ill see what happens!
I'm not sure it matters much if the 3 lens are maxed or not - you can't do anything outside of then anyway.
As far as other windows the 75% should work out ok for most screens, uses, users, ect  
I guess the value used could (or may ) be revisited at some point.

---

### Post by Sashin on 2011-03-18
Mine defaults to full screen on my 14" laptop even though I really think it shouldn't be.

---

### Post by Framli on 2011-03-18
The 75% thing is not for the Dash, but for applications. If an opening window takes more than 75% of the screen, it's automatically maximized.

The resolution for the Dash to go fullscreen is a height < 800px.
You can customize it via dconf-editor or with:

$ gsettings set com.canonical.Unity form-factor Desktop # Force resized mode
$ gsettings set com.canonical.Unity form-factor Netbook # Force fullscreen
$ gsettings set com.canonical.Unity form-factor Automatic # Default

---

### Post by mc4man on 2011-03-18
> **Framli said:**
> The 75% thing is not for the Dash, but for applications. If an opening window takes more than 75% of the screen, it's automatically maximized.

The resolution for the Dash to go fullscreen is a height < 800px.
You can customize it via dconf-editor or with:

$ gsettings set com.canonical.Unity form-factor Desktop # Force resized mode
$ gsettings set com.canonical.Unity form-factor Notebook # Force fullscreen
$ gsettings set com.canonical.Unity form-factor Automatic # Default

Yep - that's it exactly now. (wasn't in dconf-editor a few weeks back.
The dconf-editor is an interesting thing to ck. out after updates to see if anything has been added and what is or isn't configurable from there.

---

### Post by MacUntu on 2011-03-18
> **Framli said:**
> The resolution for the Dash to go fullscreen is a height < 800px.
You can customize it via dconf-editor or with:

$ gsettings set com.canonical.Unity form-factor Desktop # Force resized mode
$ gsettings set com.canonical.Unity form-factor Notebook # Force fullscreen
$ gsettings set com.canonical.Unity form-factor Automatic # Default

Yeah, but does it work for you? I tested this a couple of days ago and I've seen no change - 900px height and it's never maximized.

---

### Post by mc4man on 2011-03-18
> **MacUntu said:**
> Yeah, but does it work for you? I tested this a couple of days ago and I've seen no change - 900px height and it's never maximized.

It works here  by editing directly  in dconf-editor, can be changed to any of the 3 values on any screen here. (1280x800, 1920x1080

 One of the posted commands above isn't accepted " ...form-factor Notebook" - ("The provided value is outside of the valid range") if trying to change from Desktop or Automatic to Notebook on a 800 or greater screen from the cli

---

### Post by cariboo on 2011-03-18
I think I saw something on the Ayatana about this, the dash is designed to run in full screen mode on screens with less than 1280X800 resolution. On the system I'm using right now with 1280X1024 resolution the dash isn't full screen, while on my netbook with 1024X600 it is.

---

### Post by mc4man on 2011-03-18
dconf (gsettings and dconf-editor) seem to be where many of the settings are heading.
checking out man gsettings is very informative, the schema names can be had w/
gsettings list-schemas

So for instance the schema in this thread - com.canonical.Unity

keys avail.
> gsettings list-keys com.canonical.Unity 
form-factor
home-expanded


present settings
>  gsettings list-recursively com.canonical.Unity
com.canonical.Unity form-factor 'Desktop'
com.canonical.Unity home-expanded 'Expanded'

values avail for form-factor key
> gsettings range com.canonical.Unity form-factor
enum
'Automatic'
'Desktop'
'Netbook'





---

### Post by beew on 2011-03-18
> **cariboo907 said:**
> I think I saw something on the Ayatana about this, the dash is designed to run in full screen mode on screens with less than 1280X800 resolution. On the system I'm using right now with 1280X1024 resolution the dash isn't full screen, while on my netbook with 1024X600 it is.


Why? That is yet another example of lack of customizability. I have one small laptop and the dash is always in  full screen. That annoys me to no end, with the menu I can open new applications unintrusively but with the dash I have to leave the screen or move to another desktop.

---

### Post by Framli on 2011-03-18
I've corrected my previous post, it's not "Notebook" but "Netbook" to obtain a fullscreen Dash.

$ gsettings set com.canonical.Unity form-factor Netbook

---

### Post by Sashin on 2011-03-18
you can customise it with dconf-editor

---

### Post by cariboo on 2011-03-18
> **beew said:**
> Why? That is yet another example of lack of customizability. I have one small laptop and the dash is always in  full screen. That annoys me to no end, with the menu I can open new applications unintrusively but with the dash I have to leave the screen or move to another desktop.

Doesn't clicking the Home button close the dash? Home button = Ubuntu logo.

---

### Post by mc4man on 2011-03-18
> **beew said:**
> Why? That is yet another example of lack of customizability. I have one small laptop and the dash is always in  full screen. That annoys me to no end, with the menu I can open new applications unintrusively but with the dash I have to leave the screen or move to another desktop.

I guess i'm really missing the point here - pick an app from the gnome menu - the menu disappears, the app opens
pick an app from dash - the dash lens disappears, the app opens

As far as customization, this thread explores a couple of the various ways for just 1 thing, there are many things that can be customized and I'm sure more to follow in natty and 11.10. (and a more 'visible' means to some i'm sure.

While not the topic here while  ccsm plays a big part in natty, I'm not to sure they'd be inclined to include it as a default, but something is needed, maybe a slimmed down version of sorts.

---

### Post by mc4man on 2011-03-19
Sorta in the vein of this thread (gsettings)  - 
I use vlc and do miss the min to notification (systray) area. Atm vlc doesn't use libindicators (or whatever it's called) or integrate into the sound menu.
So using the various gsettings commands added vlc to the systray-whitelist key. 
Whether this _is advisable to do_ don't know, but does work quite fine in a limited test frame (at some point dev testing can include how to modify to suit along w/ how does the shipping default work
screen - a couple of px where cut off in taking the screenshot

Edit: also  the osd of vlc  now works - a 'keeper' here.

---

### Post by MacUntu on 2011-03-19
> **cariboo907 said:**
> I think I saw something on the Ayatana about this, the dash is designed to run in full screen mode on screens with less than 1280X800 resolution. On the system I'm using right now with 1280X1024 resolution the dash isn't full screen, while on my netbook with 1024X600 it is.

D'oh! I thought it should work the other way around. :D

---

