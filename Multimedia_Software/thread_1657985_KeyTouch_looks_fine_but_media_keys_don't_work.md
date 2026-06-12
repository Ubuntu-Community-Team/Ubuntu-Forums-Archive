---
title: "KeyTouch looks fine but media keys don't work"
date: 2011-01-01
forum: Multimedia Software
---

### Post by bludshot on 2011-01-01
I have a logitech dinovo wireless keyboard with those extra multimedia keys on it like Volume Up, Volume Down, and Mute.

They didn't do anything so I installed KeyTouch. I was able to select my keyboard from the list in KeyTouch, and if everything was working right then at that point all my extra keys would work. But they still didn't do anything.

So I went into the Keytouch editor to make my own custom profile. You click add to add a new key and then it asks you to press a key. So I press the key (Mute) and it recognizes it, and then you select what action you want it to do. I did this for Mute, Volume Up and Volume Down. But yet they still don't work!

Now obviously it detects my key presses (keycode) just fine when I added the new key. So it should do the assigned action when I press that key. What I *want* it to do is mute or change the volume of the Headphones. But as I said that wasn't working at all for some reason.

So to narrow it down I instead set the Mute key to simply launch firefox. But it still doesn't work. So there is some disconnect... in the keytouch editor it's detecting the key just fine, but afterwards when you press Mute it doesn't do the action it's supposed to.

So I have no idea where to go from here

---

### Post by bludshot on 2011-01-02
Well, Keytouch looked great but it just didn't work. So I uninstalled it and found out that I could solve my problem pretty easily.

I just went to the xfce Keyboard settings shortcuts tab and added new items for my special keys. The trick is knowing what the commands are, and they go like this:

amixer set Master toggle
amixer set Master 1+
amixer set Master 1-

(But in my case it's Headphone not Master.)

I got this from here: [http://alvonsius.wordpress.com/2007/01/08/xfce-volume-controlling-with-keyboard/](http://alvonsius.wordpress.com/2007/01/08/xfce-volume-controlling-with-keyboard/)

---

