---
title: "[SOLVED] Volume control on headset controls speaker volume, not headphone volume"
date: 2008-04-23
forum: Multimedia Software
---

### Post by noerrorsfound on 2008-04-23
I've got a Microsoft LifeChat LX-3000 headset, and on the cord is a remote to control the volume. The volume control works, but it controls the main speaker volume, not the headphones I'm using. How can I change the device it controls?

Also, no matter what I've got the headphone volume set at using the volume control application, when I plug them into the USB port, the Ubuntu login sound plays really loudly.

Now I've got another problem: The volume control won't let me turn up the left speaker of the headphones, so I can only hear out of the right. I "link" them together but it undoes itself. I can slide the bar up and hear, but it automatically goes back down to the bottom before I even let go.

---

### Post by noerrorsfound on 2008-05-21
Is this not a simple config file change or menu option?:(

---

### Post by wasper17 on 2008-05-31
there is a option to link what the volume buttons controls. if you look in the options, there is a list of what the buttons control, you can select more than one option.... took me about 3 days to figure that out! lol

---

### Post by A. Situs on 2008-06-27
> The volume control works, but it controls the main speaker volume, not the headphones I'm using. How can I change the device it controls?

Here's what worked for me.
Go to System>Preferences>Sound. Under Default Mixer Tracks, the "Master" should be highlighted. Now if you Ctrl+click on "Headphone", it should link your headphone volume with the main.

Edit: Oh sorry, I misread wasper17's advice, so the solution didn't work for me. Now I realize that our solutions are the same.

--Brad

---

