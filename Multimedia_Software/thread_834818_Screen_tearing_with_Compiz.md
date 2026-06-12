---
title: "Screen tearing with Compiz"
date: 2008-06-19
forum: Multimedia Software
---

### Post by BetterSense on 2008-06-19
I have my everyday computer (Biostar 7050 w/5400+, 4gigs ram, Hardy Heron) hooked up via HDMI to my Sony tube TV, which I use to watch dvds and some downloaded anime movies usually in .mkv.

The video quality is excellent but for some horizontal tearing during certain scrolling shots. I've found out that it doesn't seem to exhibit the tearing if I use metacity. However, I can't live without compiz. Are there any adjustments to my Nvidia settings or anything else that could fix this up?

Or, since I have the Sony set up as a separate X screen (can post xorg if needed), is there any way I could just disable compiz on THAT display, but keep it for my normal computer?

Failing even that, is there some way I could write a 'play movie' script that will basically switch to metacity whenever I use mplayer? I don't know anything about bash scripts but like have a script so when I type playmovie <somefile> it does something like

metacity --replace
mplayer <somefile>
compiz --replace 

would that be practical?

---

### Post by chewearn on 2008-06-20
Things to try:

1. In nvidia-settings, enabled all checkboxes for "Sync to Vblank".


2. With separate X screens

To run compiz on first screen only:
```
DISPLAY=:0.0 compiz --only-current-screen
```

To run compiz on second screen only:
```
DISPLAY=:0.1 compiz --only-current-screen
```

.

---

### Post by BetterSense on 2008-06-20
ooo thanks I'm gonna try that. Do I put those lines in my xorg.conf under SECTION DISPLAY or something?

---

### Post by chewearn on 2008-06-20
> **BetterSense said:**
> ooo thanks I'm gonna try that. Do I put those lines in my xorg.conf under SECTION DISPLAY or something?

No, those are commands you run from the terminal.

---

### Post by BetterSense on 2008-06-20
Will I have to do that every login, that is, should I put it in my bash startup? Or will it stick?

---

### Post by chewearn on 2008-06-20
If you are unsure, just run these commands in the terminal (copy/paste the entire thing):
```
cd ~
cat > start-compiz.sh << EOF
#!/bin/bash
DISPLAY=:0.0 compiz --only-current-screen
EOF
chmod +x start-compiz.sh


```After the above, you get a executable file named start-compiz.sh in your home directory.  Copy it somewhere convenient but out of the way.  Personally, I put all my scripts into a subdirectory called bin.

Then, add the script into:
System > Preferences > Sessions

Snapshot from my system as example.  You would, of course, need to modify the script path to point to where you put it.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=74754&stc=1&d=1213974822[/IMG]

---

