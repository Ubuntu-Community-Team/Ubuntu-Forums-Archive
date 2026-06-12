---
title: "Attempting to get Twinhan Remote to work"
date: 2008-01-15
forum: Mythbuntu
---

### Post by Waistless on 2008-01-15
I'm attempting to get my Twinhan remote working using _[this guide]("http://www.doctort.org/adam/nerd-notes/mythtv-and-the-twinhan-remote.html")_

I have one main problem and a small issue (which a lot of people might be able to solve). I'll start with the smaller issue

I have set up the remote controller for use with lirc as according to the guide, but it appears to already have been set up and is being used with keyboard commands, i.e the number buttons input the number but other buttons such as info/EPG outputs E, other buttons output other letters, and the power button kills X and lands me to a prompt. Is there anyway I can turn this off so I can use my remote only for Lirc? thanks. -----FIXED

Here's the second more major issue:

His remote is different to mine however in that mine is used for digital TV and recording and thus has a lot more buttons ([image here]("http://ecx.images-amazon.com/images/I/51QRQspO5xL._AA280_.jpg")). I'm fetching the commands for each button for the lircd.conf (which are subsequently used by lircrc) by entering:

```
hexdump /dev/input/irremote
```

This outputs the code for each button, for instance it ouputs this when I press 2

```
0000000 9b9f 478c 83ce 0004 **0001 0003** 0001 0000
0000010 9b9f 478c 83d9 0004 0000 0000 0000 0000
20000020 9b9f 478c a309 0004 **0001 0003** 0000 0000
0000030 9b9f 478c a314 0004 0000 0000 0000 0000
```

The hex in the first 5 collumns are dynamic and irrelevant. The bolded numbers are relevant to the command. And thus the button 2 command will be entered in the lircd.conf like so:

```
 2                0x10003 
```

I tried and tested using the buttons already in adam pierce's guide and using that basis added more buttons in. Here's a few I grabbed

```
		RED		 0x10013
		GREEN		 0x10022
		YELLOW		 0x10015
		BLUE		 0x10030
```


Unfortunately I have run into an annoying issue with this method. For certain buttons I am recieving conflicts which have a similar command that I can't simply use 1x00000 for. For instance, the Pause button outputs this:

```
 0000000 9e21 478c ebda 0002 **0001 0014** 0001 0000
0000010 9e21 478c ebe5 0002 0000 0000 0000 0000
t0000020 9e21 478c 0b16 0003 **0001 0014** 0000 0000
0000030 9e21 478c 0b21 0003 0000 0000 0000 0000
```

and the Subtitle/CC button outputs this:

```
0000000 a029 478c bf70 0000 **0001 001d** 0001 0000
0000010 a029 478c bf80 0000** 0001 0014** 0001 0000
0000020 a029 478c bf86 0000 0000 0000 0000 0000
^T0000030 a029 478c fdf7 0000 **0001 001d** 0000 0000
0000040 a029 478c fe06 0000 **0001 0014** 0000 0000
0000050 a029 478c fe0c 0000 0000 0000 0000 0000
```

Here, there's added data for 0014 with 001d. 001d is also shared amongst other buttons as well.

Is there anyone with a good knowledge of hex out there that knows how to enter this in the format 1x00000 for use in lircd.conf? Would it be done by entering it as a compound? (e.g. 0x1001d 0x10014).

Please be understanding as i'm only an intermediate linux user with very little knowledge of hex and complex internal stuff :(

---

### Post by ubnewbie2 on 2008-01-15
> **Waistless said:**
> I'm attempting to get my Twinhan remote working using _[this guide]("http://www.doctort.org/adam/nerd-notes/mythtv-and-the-twinhan-remote.html")_

I have one main problem and a small issue (which a lot of people might be able to solve). I'll start with the smaller issue

I have set up the remote controller for use with lirc as according to the guide, but it appears to already have been set up and is being used with keyboard commands, i.e the number buttons input the number but other buttons such as info/EPG outputs E, other buttons output other letters, and the power button kills X and lands me to a prompt. Is there anyway I can turn this off so I can use my remote only for Lirc? thanks.


I used to have a twinhan card, and the remote does not use a lirc interface. It, effectively, is a remote keyboard, and yes, what you describe, is exactly what it does.  Linux sees it as a keyboard, and I don't know if you can change that.

---

### Post by Waistless on 2008-01-15
Yea, the remote doesn't use the lirc at first, that's the purpose of the guide, to set it up to use it. I shouldn't need to change what Linux sees it as, but I should be able to change whether to enable commands from it or not.

Progress so far: I haven't been able to get lirc to recognise the extra data using different formats, but I have noticed an option in the lircd.conf: Bits 32, would this option make any difference?

EDIT: Ah! I've just got it now, Lirc overrides keyboard in MythTV, i just didn't put the lircrc file in the right place, so that part's fine now. Still no one knows how to fix conflicting buttons on the remote? It's very problematic because Play conflicts with fastfoward and replay and skip and other buttons also conflict

---

### Post by RoboRat on 2008-01-30
I did not have to use lirc to get my remote working.  You'll find that some of the remote keys generates combo keys, e.g. Play is Ctrl+N. You can use xev to confirm which key does what.  I used MythControls to map these keys to Myth functions.  The trick is not to use the actual remote key for combo keys when you get to the "waiting for keypress" screen when binding keys.  Use the keyboard for these.  If you use the remote, it generates something like Ctrl+Square for all combo keys, so they turn up the same for all combo keys.

Hope this helps.

Cheers!
RoboRat

---

### Post by ubnewbie2 on 2008-01-30
but doesn't this remapping mean that your myth install is very awkward to use from a real keyboard?   That's why I gave up on it.

In fact, my solution was to get a real mini IR keyboard.  It even has a joystick "mouse" and I happily operate all my myth functions from it, sitting on the couch.  

It also is useful when I am fixing something or working on something new. I can just ctrl-alt-F1 to a terminal, and log in and work from the couch using the keyboard.

---

### Post by RoboRat on 2008-02-02
I only use my myth and remote in the lounge and therefore this solution (remapping keys) works for me.  IR keyboard will be great but I can't find one here in Australia.

---

### Post by Waistless on 2008-02-06
RoboRat, hmm that would have solved the previous instance where I was using the remote directly without LIRC.

The main disadvantages of that approach though is that nearly all the keys have to be rebinded, for each section, and that just takes too long. I mainly gave up on that because of the square issue, and the fact the power button is binded to Ctrl+Alt+F6 (goes into TTY6), which can't be rebinded per device without the use of LIRC.

And besides, when and if I finally figure out how to resolve these button conflicts, I'll be able to post up the lircd.conf and lircrc and other users won't have to do any rebinds at all.


Edit: Ok, now it appears this issue has already been raised in the mailing lists, thus far ignored. Lirc isn't recognising modifiers, like the Shift key. I guess I'll just have to bug the devs enough to add functionality or to explain how to configure for it.

---

