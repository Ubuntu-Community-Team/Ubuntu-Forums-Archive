---
title: "Prevent Applications from Resetting PulseAudio Settings?"
date: 2010-08-26
forum: Multimedia Software
---

### Post by mrspacklecrisp on 2010-08-26
Ubuntu Lucid, Asus T101MT tablet netbook.

Background Info: Normally the microphone doesn't work with some applications such as Empathy or the new Google Talk plugin for Linux. The workaround I'm using (and I don't know why this works) is to unlock the left and right channels in Pavucontrol and set one channel to zero, and to boost volume I set the other to max.

Issue: The Google Talk plugin is resetting the channels to be locked together. This is pretty frustrating because now they have free calling and I have no cell reception in my dorm room.

Ideas? Thanks bunches, Ubuntu community. Ask for anything that could help.

---

### Post by mrspacklecrisp on 2010-08-28
Erm, bumpity bump bump?

---

### Post by yaddoshi on 2011-08-03
Better late than never, and this might help someone else searching the forums.  This should also help with Google+ Huddle which uses the same plugin.

Open a terminal session and access the Google Talk plugin folder in your user profile:
```
cd ~/.config/google-googletalkplugin
```

Make a backup of your current config file:
```
cp options options.bak
```

Open the config file with your preferred editor:
```
gedit options #alternatively nano options
```

Change the following line:
```
audio-flags=3
```

So that it reads:
```
audio-flags=1
```

Save and close your editor, then log out and back in or restart your computer.

The Google Talk plugin should no longer adjust your microphone settings automatically, allowing you to set it as preferred using alsamixer or your preferred audio adjusting tool.

---

