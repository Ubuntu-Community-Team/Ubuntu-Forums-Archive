---
title: "Multimedia keys don't work with rhythmbox in jaunty jackalope"
date: 2009-05-06
forum: Multimedia Software
---

### Post by firesock on 2009-05-06
Hi friends!

I'm having a problem that is driving me crazy (because I listen music a very large amount of time) with rhythmbox in ubuntu 9.04.

I'm using a Dell vostro 1310 and The play, stop, next and previous multimedia keys aren't working. When I had Intrepid Ibex they worked perfect. The problem just started when I updated to 9.04.

I have looked with the console and ubuntu does recognize those keys when I press them, but rhythmbox don't respond to them. By the way, the volume multimedia keys work perfect.

In the keyboard shortcuts configuration those multimedia keys are configured in the right way.

I think it's a rhythmbox problem... a bug of the updated 0.12.0 version. Does anyone have the same problem?

If someone knows anything about this problem Please let me know. I appreciate so much your help...

 Best regards... :)

---

### Post by rx7mazda on 2009-05-07
I am having the same exact problem. Everything worked fine under Ibex, but when I upgraded to Jaunty this (among other things) stopped working. Volume and mute works, but play, ffw, etc don't. I am using a Logitech wireless keyboard.

---

### Post by pradeepjey on 2009-05-10
Sorry all I can add is a "me too" to this. Using a Wiimote with buttons mapped to Multimedia keys. Xev and Gnome Keyboard Shortcuts sees the key presses correctly but I don't get any response from Rhythmbox.

---

### Post by tdietz87 on 2009-05-10
> **pradeepjey said:**
> Sorry all I can add is a "me too" to this. Using a Wiimote with buttons mapped to Multimedia keys. Xev and Gnome Keyboard Shortcuts sees the key presses correctly but I don't get any response from Rhythmbox.

x2 :(

---

### Post by pradeepjey on 2009-05-10
[https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/374526](https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/374526)

---

### Post by firesock on 2009-05-10
> **pradeepjey said:**
> [https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/374526](https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/374526)

Thank you very much for the launchpad report... We hope that they could help us...

Bye!

---

### Post by eladamri on 2009-06-10
I was having a similar problem. I use amarok and had my media keys working prior to Jaunty, but the same solutions did not get them to work after switching to Jaunty.

Before I was able to get them functioning using KeyTouch, but that is no longer working for me. Even with the added flexibility of "System > Preferences > Keyboard Shortcuts" it would not work.

I just fixed them when I ran across "Commands" in the CompizConfig Settings Manager (which needs to be installed via Synaptic or other means). Just go to System > Preferences > CompizConfig Settings Manager > General > Commands, set the desired command and the corresponding key binding.

I hope this addresses your problem as it did mine.

---

### Post by rx7mazda on 2009-06-24
> **eladamri said:**
> I was having a similar problem. I use amarok and had my media keys working prior to Jaunty, but the same solutions did not get them to work after switching to Jaunty.

Before I was able to get them functioning using KeyTouch, but that is no longer working for me. Even with the added flexibility of "System > Preferences > Keyboard Shortcuts" it would not work.

I just fixed them when I ran across "Commands" in the CompizConfig Settings Manager (which needs to be installed via Synaptic or other means). Just go to System > Preferences > CompizConfig Settings Manager > General > Commands, set the desired command and the corresponding key binding.

I hope this addresses your problem as it did mine.

I don't see any commands to change the media key bindings

---

### Post by Halfwalker on 2009-06-30
Hrm, this is sort of an "it works for me, mostly" ...

I have Jaunty 9.04 x64 using a Microsoft Internet Keyboard Pro.  Pretty much all the of the buttons across the top work as one would expect.

My Computer -> Nautilus on home dir
Calculator -> Calculator
Play/Pause -> works for Rhythmbox and/or Totem
Volume up/down, Mute -> work fine
  :
  :

The only one that doesn't seem to work is the Media button.  I want that to bring up Rhythmbox - it does nothing.  In System->Preferences->KeyboardShortcuts under Sound, everything is bound to XF86Audio..... shortcuts.  Launch Media Player is bound to XF86AudioMedia, so I would imagine that that has to be bound to Rhythmbox somewhere.

Any ideas Where ?

DC.

---

### Post by dzyubam on 2009-07-22
I'm using Ubuntu 8.10 so I'm not 100% sure this solution will work fine for other guys.

You can set it up using CompizConfig Settings Manager. Go to General > Commands tab then input the command to be executed "rhythmbox" or "amarok", whichever you use, in the Commands sections. Then you need to assign a key binding to launch that command. If you used "Command line 0" in the Commands section, be sure to use the corresponding "Run command 0" line in the Key bindings section. Click the button on the right to assign the key binding (use your media key). Close the Compiz Settings Manager and you're done.

If you don't use Compiz, there's another way to set this up. Type "gconf-editor" in your terminal. In the configuration window, browse to apps > metacity. You'll need to change the values in global_keybindings (to assign keys) and keybinding_commands (to define the commands to be executed). Be sure to use the corresponding fields. If you assign execution of command "amarok" in keybinding_commands > command_1, change the field "run_command_1" in global_keybindings section in order to assign a key to execute that command.

Hope this helps :)

---

### Post by mff47025 on 2009-08-13
I just installed the LIRC plugin for rhytmbox.  It is for IR remote control.  Now my play, pause, stop, next, prev keys all work.  Still looking for a fix for volume keys but its a start.

---

### Post by dudesurge on 2010-07-10
I know this has been dead for a while but i'm having a similar problem, 
All of my multimedia buttons work just fine, the problem is when i have rhythmbox open and maximized and i use my volume+/- buttons it lags like a snail race and freezes then it goes up or down and displays the one at the top and also displays one at the bottom that i hadn't seen it until i started using Rhythmbox but all the second one does is displays the exact same thing as the one at the top for my desktop volume, it doesn't show up when its minimized or in the notification area, how do i shut the second one off? 

my laptop is
Acer Aspire 5810tz Timeline
Ubuntu 10.04 Gnome/Black Xp Dual partitioned
Intel Pentium 1.3 Ghz 64Mb Vram

---

### Post by yanychar on 2011-01-15
I've just fixed the same problem on Maverick Meerkat. The cause was that system is configured for "minimal" footprint by setting APT::Install-Recommends to "false" in /etc/apt/apt.conf. The solution was simple:

```
sudo apt-get install rhytmbox-plugins
```

@**firesock**:
Could you check if this helps you and update the title to [SOLVED], if it is?

---

