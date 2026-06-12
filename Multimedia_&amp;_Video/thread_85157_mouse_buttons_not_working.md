---
title: "mouse buttons not working"
date: 2005-11-01
forum: Multimedia &amp; Video
---

### Post by iH8forcedRegistration on 2005-11-01
I've recently purchased a new mouse. This mouse works 'ok' using the following in my xorg.conf: 

```

Section "InputDevice"
    Identifier   "Configured Mouse"
    Driver       "mouse"
    Option      "CorePointer"
    Option      "Device"                "/dev/input/mice"
    Option      "Protocol"              "ExplorerPS/2"
    Option      "ZAxisMapping" "4 5"
    Option      "Buttons" "24"
EndSection

```

By 'ok,' I mean the main three buttons and the scrollwheel work correctly. My new mouse, however, has 11 buttons, and many of the buttons are interpreted incorrectly. Specifically, there's one extra button below the scrollwheel that's supposed to be button 8, but instead is interpreted identically to button 1.

By running
```
hexdump < /dev/input/mice
```

I was able to determine that the mouse driver was outputting exactly the same codes for button 8 as it was for button 1, however, this mouse also has another device associated with it, /dev/input/event6, which had distinctly different output codes for each button.

What I'd like to try to do to correct this is add another InputDevice to my xorg.conf that can handle the data from /dev/input/event6 as mouse clicks, then find a way to suppress the button-related data coming from the "ExplorerPS/2" device.

However, i would have to specify an Option "Protocol" that would be able to actually interpret those codes, but, after 4 solid hours of googling, i've found myself unable to find any documentation on xorg whatsoever that was not just an html-fyed version of a manpage I already read. So, I was wondering whether anyone had any idea how to write a new Protocol for xorg, or whether anyone knows of some secret xorg documentation area somewhere.

Thanks

---

### Post by iH8forcedRegistration on 2005-11-02
I _think_ I may be able to accomplish what I want using a wonderful program called [evrouter]("http://www.bedroomlan.org/~alexios/coding_evrouter.html"), but it still leaves the problem of disabling buttons in X11.

In order for evrouter to transmit an XButton event, that XButton must be 'valid,' so I can't have
```
Option "Buttons" "0"
```
in my xorg.conf because then I wouldn't be able to simulate button events.

Enter xmodmap, a tool for remapping buttons. I set the number of buttons to 12 in my xorg.conf, then used xmodmap to map the buttons that were being interpreted incorrectly by the /dev/input/mouse1 driver to logical buttons that didn't do anything.

The problem is, KDE still interprets them as clicks, just clicks that do nothing, so if I press a button that isn't actually supposed to do anything (yet), focus shifts to whatever's under the pointer.

That would be fine, except it prevents KDE from recognizing doubleclicks as double clicks, since the buttons it sees are 1, 12, 1, 12 in quick succession.

So, my question is now whether it's possible to use xmodmap to make it so that all of the physical buttons on my mouse do nothing.

I tried this:
```
xmodmap -e "pointer = 0 0 0 0 0 0 0 0 0 0 0 0"
```
but it didn't work. Please help.

---

