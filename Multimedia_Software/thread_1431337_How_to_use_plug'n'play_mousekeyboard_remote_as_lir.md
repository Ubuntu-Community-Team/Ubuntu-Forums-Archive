---
title: "How to use plug'n'play mouse/keyboard remote as lirc device?"
date: 2010-03-16
forum: Multimedia Software
---

### Post by Redsandro on 2010-03-16
Hi,

I've bought [this remote control]("http://www.amazon.com/Wireless-USB-Remote-Control-Mouse/dp/B001M56DI0/ref=sr_1_1?ie=UTF8&s=electronics&qid=1259362464&sr=1-1") that sais it works in Vista, XP etc. without any driver. Basically it has a bunch of buttons that replace the mouse and a bunch of others that replace basic keyboard functions (arrows, enter, escape).

It has a USB IR receiver so I thought I could simply use it as a lirc remote in Ubuntu.

However, it sais absolutely nothing on it except for "PCremote" so during lirc installation I have no idea what to choose.

And, interestingly, I accidentally discovered that it works in Ubuntu, too, out of the box. Controlling the mouse and acting like a keyboard.

Is there a way I can forfeit current functionality and just get it to work as a customizable lirc remote?

Or even better, keep current functionality but change it only for certain apps (xbmc, vlc etc)?

---

### Post by gobbledigook on 2010-04-06
> **Redsandro said:**
> 
And, interestingly, I accidentally discovered that it works in Ubuntu, too, out of the box. Controlling the mouse and acting like a keyboard.

Is there a way I can forfeit current functionality and just get it to work as a customizable lirc remote?

Or even better, keep current functionality but change it only for certain apps (xbmc, vlc etc)?


Hi there! that looks like a MCE remote clone type thingy ;)

basically its similar to the official media centre remote, and the signals it sends are pretty standard, for controlling apps differently you would need to put a remote config file in your home directory. 

for example for xbmc you need to modify the /usr/local/system/xbmc/keymaps/remote.xml file to reflect your customisations and then save it to your /home/USER/.xbmc/ folder under system/keymaps or userdata/keymaps. can't remember off-hand now...

check the xbmc wiki for ir configuring, it is pretty comprehensive :)

---

### Post by pejcao on 2010-06-21
I'm looking toward the same remote (the only one I can find in Venezuela as "MCE Remote").
Did it work as a standard LIRC remote besides mouse/keyboard?
Cheers!

---

### Post by Redsandro on 2010-06-22
I know it's a while back, but I still haven't found the time to look into it.

**gobbledigook** is right about it being an MCE remote clone thingy, but I don't know any software that supports those keymaps except for XBMC. Because it's XBMC-native.

So I've just been using the mediakeys on the remote so far. I read that it should be possible to set it up as a LIRC device, but I am too afraid it's gonna be one of those linux black holes of time wasting efforts from which there is no escape, if you know what I mean.

This is my 'television'. I don't want to break it. And I usually do that when I work with video cards or remotes in linux. :P

But if you figure it out, please please share your findings!

---

### Post by pejcao on 2010-06-24
OK, It does/can work as an standard lirc remote...as soon as a lirc client (like irexec) starts.

I'm using /usr/share/lirc/extras/more_remotes/generic/devinput.conf as /etc/lirc/lircd.conf (irw does recognizes every key)

The pain in "the lower back" comes 'couse there are some keys that use a lot of Alt's+Ctrl's+Keys+More keys...so you have to write a lot of "button =" lines in yer ~/.lircrc and make that function 3 times for every "Numlock" setting becuse this cheap remote doesnt shows in what "numlock" setting you are currently in.

I'm watching tvtime with all function running via lirc and this cheap "pc-remote" as I write this.

Cheers!

---

### Post by Redsandro on 2010-06-24
That's sweet! I hate that numlock thing, I am always in the wrong mode and whatnot.

Would you mind posting an example of your *pain-in-the-lower-back* **~/.lircrc**?

It will bring some happyness into this topic. :)

**-edit-**

Also, does lirc automatically take over? I mean, if lirc registeres a keystroke, it should no longer also be registered by the keyboard emulation thingie.

---

### Post by pejcao on 2010-06-26
> **Redsandro said:**
> That's sweet! I hate that numlock thing, I am always in the wrong mode and whatnot.

Numlock thig is awwwwwfullll; but heck, it's a cheap remote ;)

> **Redsandro said:**
> Would you mind posting an example of your *pain-in-the-lower-back* **~/.lircrc**?
So far i'm using it for tvtime only; I use the yellow button to launch tvtime (Ctrl+Alt+F4); I've placed this as "/etc/lirc/lircrc" instead of ~/.lircrc .The first line is supposed to launch lircrcd which starts irexex & irexevent if used in lircrc
```
#! lircrcd
begin
	prog = irexec
	button = LEFTCTRL
	button = LEFTALT
	button = F4
        config = /usr/bin/tvtime &
	mode = tvtime
	once
end
begin
	prog = irexec
	button = LEFTCTRL
	button = LEFTALT
	button = D
        config = /usr/bin/tvtime &
	mode = tvtime
	once
end

begin tvtime
begin
	prog = irexec
	button = VOLUMEDOWN
        config = /usr/bin/tvtime-command LEFT
end
begin
	prog = irexec
	button = VOLUMEUP
        config = /usr/bin/tvtime-command RIGHT
end
begin
	prog = irexec
	button = PAGEUP
        config = /usr/bin/tvtime-command CHANNEL_INC
end
begin
	prog = irexec
	button = PAGEDOWN
        config = /usr/bin/tvtime-command CHANNEL_DEC
end
begin
	prog = irexec
	button = BACKSPACE
        config = /usr/bin/tvtime-command CHANNEL_JUMP
end
begin
	prog = irexec
	button = MUTE
        config = /usr/bin/tvtime-command MIXER_TOGGLE_MUTE
end
begin
	prog = irexec
	button = COMMA
        config = /usr/bin/tvtime-command CHANNEL_1
end
begin
	prog = irexec
	button = A
        config = /usr/bin/tvtime-command CHANNEL_2
end
begin
	prog = irexec
	button = D
        config = /usr/bin/tvtime-command CHANNEL_3
end
begin
	prog = irexec
	button = G
        config = /usr/bin/tvtime-command CHANNEL_4
end
begin
	prog = irexec
	button = J
        config = /usr/bin/tvtime-command CHANNEL_5
end
begin
	prog = irexec
	button = M
        config = /usr/bin/tvtime-command CHANNEL_6
end
begin
	prog = irexec
	button = P
        config = /usr/bin/tvtime-command CHANNEL_7
end
begin
	prog = irexec
	button = T
        config = /usr/bin/tvtime-command CHANNEL_8
end
begin
	prog = irexec
	button = W
        config = /usr/bin/tvtime-command CHANNEL_9
end
begin
	prog = irexec
	button = SPACE
        config = /usr/bin/tvtime-command CHANNEL_0
end
begin
	prog = irexec
	button = LEFTMETA
	button = D
        config = /usr/bin/tvtime-command ENTER
end
begin
	prog = irexec
	button = LEFTALT
	button = LEFTCTRL
	button = ENTER
        config = /usr/bin/tvtime-command TOGGLE_FULLSCREEN
end
begin
	prog = irexec
	button = LEFTALT
	button = LEFTCTRL
	button = 3
        config = /usr/bin/tvtime-command TOGGLE_FULLSCREEN
end
begin
	prog = irexec
	button = TAB
        config = /usr/bin/tvtime-command CHANNEL_1
end
begin
	prog = irexec
	button = UP
        config = /usr/bin/tvtime-command CHANNEL_2
end
begin
	prog = irexec
	button = LEFTMETA
        config = /usr/bin/tvtime-command CHANNEL_3
end
begin
	prog = irexec
	button = LEFT
        config = /usr/bin/tvtime-command CHANNEL_4
end
begin
	prog = irexec
	button = ENTER
        config = /usr/bin/tvtime-command CHANNEL_5
end
begin
	prog = irexec
	button = RIGHT
        config = /usr/bin/tvtime-command CHANNEL_6
end
begin
	prog = irexec
	button = LEFTCTRL
	button = O
        config = /usr/bin/tvtime-command CHANNEL_7
end
begin
	prog = irexec
	button = DOWN
        config = /usr/bin/tvtime-command CHANNEL_8
end
begin
	prog = irexec
	button = ESC
        config = /usr/bin/tvtime-command CHANNEL_9
end
begin
	prog = irexec
	button = LEFTALT
	button = TAB
        config = /usr/bin/tvtime-command CHANNEL_0
end
begin
	prog = irexec
	button = LEFTALT
	button = F4
        config = /usr/bin/tvtime-command QUIT
	mode
end
end tvtime
```

As you can see, there are duplicated configs per button because the numlock thing (might get triplicated eventually)

> **Redsandro said:**
> Also, does lirc automatically take over? I mean, if lirc registers a keystroke, it should no longer also be registered by the keyboard emulation thingie.
Yes; as soon as irexec kicks in. As you see in that config, Ctrl+Alt+F4 launches tvtime and enters that mode instead of throwing me to TTY4, also "irw" does grabs all keystrokes just like irexec
For some reason irxevent ain't working for me. Working on that.

Cheers!

---

