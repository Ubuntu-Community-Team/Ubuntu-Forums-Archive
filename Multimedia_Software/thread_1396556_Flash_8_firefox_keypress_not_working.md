---
title: "Flash 8 firefox keypress not working"
date: 2010-02-02
forum: Multimedia Software
---

### Post by theLured on 2010-02-02
Firefox can't detect any keypresses from the programs I make. I use Macromedia Flash 8.
Make a text box and give it the instance name"txt_test"
add this actionscript code.
```
stop();
KeyListener = new Object();
KeyListener.onKeyDown = function() {
	_root.txt_test.text = "OOOOO";
}
Key.addListener(KeyListener);
```

When running it, it works from flash 8 and in gnash, just not firefox.

I have also tried making a button and adding
```
on (release, keyPress "<Space>") {
	_root.txt_test.text = "OOOOO";
}
```
Pressing the button in firefox works, but not the space bar.

My firefox can take input for flash. Youtube's play and pause with spacebar + exit fullscreen with Esc.
this game also works
[http://www.miniclip.com/games/skywire-2/en/](http://www.miniclip.com/games/skywire-2/en/)

This one doesn't work
[http://www.miniclip.com/games/stunt-pilot/en/](http://www.miniclip.com/games/stunt-pilot/en/)

Any ideas? I want to either fix my firefox or make my program so that it can take input. Is it because I need to build my program with flash CS3 or 4?

---

### Post by theLured on 2010-02-11
bump

---

### Post by theLured on 2010-04-27
I solved it.
It was scim blocking my keyboard for some reason.
I also had the problem of not being able to type in windows that were focused.

It's solved by running
pkill scim

---

