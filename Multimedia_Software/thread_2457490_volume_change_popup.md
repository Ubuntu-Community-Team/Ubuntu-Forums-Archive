---
title: "volume change popup"
date: 2021-02-03
forum: Multimedia Software
---

### Post by cmcanulty on 2021-02-03
I've tried a few things to stop the annoying volume popup box whenever I change the volume-to get rid of it I have to click on the popup every time. I did this fix from a mate discussion with no result first:

"I’ve never seen an option that does this neither. :confused: There is a way! This involves changing what the keyboard shortcuts do.

In the Keyboard Shortcuts options, disable the shortcuts for “Volume up” and “Volume down” by clicking on them and hitting Backspace.

At the bottom, create two new custom shortcuts with these commands:
```

    Decrease Volume

      amixer -D pulse sset Master 5%-

    Increase Volume

      amixer -D pulse sset Master 5%+
```

You can change 5% to a different number if you like.

Now bind the new commands to your multimedia keys. :slight_smile:
Solution
veganux
Jun '16

This works like a charm ! Thank you very much !"

Also I right clicked the volume icon in the top panel and selected properties. Then I unchecked "show notifications when volume changes"  also with no result. I am attaching a screenshot of that box.

---

### Post by Holger_Gehrke on 2021-02-03
If the [xubuntu] tag in the heading is not a mistake and you're talking about the notification with a loudspeaker symbol followed by a bar graph of the currently set volume I get whenever I hit the volume control keys or rotate the mouse wheel over the loudspeaker icon in the tray then the solution is very simple: in settings there is an applet for the notifications settings (you can also call this in a terminal with xfce4-notifyd-settings). Hit the button labeled 'Applications' to get a list of all applications known to send notifications. Scroll down to 'XFCE volume daemon' and switch it off. Done. At least on my XUbuntu 18.04 system, if you're running something newer (or older ...) this might have changed ...

Holger

---

