---
title: "Aqualung doesn't work with multimedia keys?"
date: 2010-05-17
forum: Multimedia Software
---

### Post by Foolishgrunt on 2010-05-17
So I've been dabbling with using Aqualung, the best gapless player I've found for Linux. I like it, except for the fact that it doesn't detect my computer's multimedia keys. I've gone through all the settings menus a few times over and haven't found any options to help it detect them. Can anybody point me in the right direction?

---

### Post by abid_naqvi83 on 2012-01-20
Since any instance of aqualung can be controlled by issuing commands in the terminal one can use xbindkeys to map the multimedia keys to these commands and thereby control aqualung.

The first step is to install the insanely useful xbindkeys program:

```
sudo apt-get install xbindkeys
```

Create an empty ~/.xbindkeysrc file which we will fill up. To find out the keycode and keysym related to a particular multimedia key simply run:

```
xbindkeys -k
```

and press the relevant key to get its keycode/keysym information. For instance on my keyboard pressing the Play/Pause button gives:

```
"NoCommand"
    m:0x10 + c:172
    Mod2 + XF86AudioPlay
```

The explanation is: Mod2 is the modifier keysym for the NumLock key being active, it has keycode m:0x10. The keycode for the Play/Pause key is 172 and it has been mapped by X to the keysym 'XF86AudioPlay' which allows it to control most multimedia applications but NOT aqualung.

Note: The command 'xbindkeys -k' may not work properly if an instance of the xbindkeys daemon is already running. To get the best results use 'ps -A | grep xbindkeys' to get the PID for any instance that is running and kill it using 'kill -9 <PID>' (where you replace <PID> with the number you found using ps -A, without the brackets of course).

Now open up .xbindkeysrc for editing and enter the following lines (as motivated by the result for 'xbindkeys -k'):

```
"aqualung -N0 --play"
XF86AudioPlay
```

These lines tell xbindkeys to issue the bash command 'aqualung -N0 --play' when it detects the keysym 'XF86AudioPlay'.

Note: The '-N0' switch in the command tells aqualung to pass the --play signal to the first (or zeroth) instance of aqualung initiated. If you have more than one you can fiddle around with the number following '-N'.

Note: By default aqualung is set up with separate pause and play keys (which you can see in the GUI) but multimedia keys on keyboards and remotes are not, so you can open aqualung's GUI and navigate to Settings (Right-Click in the Player) >> General >> Main Window and check the 'Combine play and pause buttons'.

A complete .xbindkeysrc file for control of aqualung using Multimedia keys would look like:

```

"aqualung -N0 --play"
XF86AudioPlay

"aqualung -N0 --stop"
XF86AudioStop

"aqualung -N0 --fwd"
XF86AudioNext

"aqualung -N0 --back"
XF86AudioPrev

```

Finally to launch xbindkeys using ~/.xbindkeysrc as the configuration file simply issue the command:

```
xbindkeys
```

from the terminal.

Using the XF86 keysyms in xbindkeys means aqualung will be automatically controlled by any key which issues these keysyms. On my computer this means that I can control aqualung from my keyboard, multimedia keys built in to the case of my laptop and also my Bluetooth Remote Control.

My keyboard only has a Play/Pause button but no Stop, Forward or Reverse buttons. It does however have a bunch of useless keys on the top. I put them to good use by using 'xbindkeys -k' to find their keycodes and mapping them to aqualung commands in addition to the multimedia keys. For example:

```

"aqualung -N0 --stop"
c:194

```

For an excellent tutorial on using xbindkeys use: [https://wiki.archlinux.org/index.php/Xbindkeys]("https://wiki.archlinux.org/index.php/Xbindkeys")

---

