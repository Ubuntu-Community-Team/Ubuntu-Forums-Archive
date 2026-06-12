---
title: "lircrc control to display DVD root menu?"
date: 2009-10-02
forum: Mythbuntu
---

### Post by zymurgist on 2009-10-02
Is there a lircrc control to display the DVD root menu?

When I press the 'menu' button on my remote, I would like to bring up the dvd menu (to select special features, subtitles, etc). I am using the internal dvd player.

Here's what I imagine adding to my lircrc:

```

begin
    remote = mceusb
    prog = mythtv
    button = DVD Button
    config = DVD_MENU <--- what goes here?
    repeat = 0
    delay = 0
end

```

While we're at it .. is there a published list of the commands I can put on the 'config' parameter?

---

### Post by belly917 on 2009-10-02
> **zymurgist said:**
> ```

    config = DVD_MENU <--- what goes here?
```

The sarcastic answer is "Anything you want"

I say that because you have to set up a custom keybinding because there isn't one by default.

Here's what you do,
[LIST]Navigate your web browser to your your mythtv backend's mythweb[/list]
[LIST]hover over the "Settings" menu item and click on "Keybindings"[/list]
[LIST]Scroll down looking for "JUMPTODVDROOTMENU" in the TV Playback section[/list]
[LIST]assign any key of the keyboard that you would like to control this function (make sure it doesn't conflict with any other assigned keys in the tv playback section or jump points section) lets say for this example we use "g".[/list]
[LIST]save the settings at the bottom of the page[/list]
[LIST]go back to your lirc config file and input ```
config = g
```[/list]
[LIST]restart your lirc and your frontend[/LIST]

---

### Post by zymurgist on 2009-10-03
Perfect - just what I was looking for. Thanks!

---

