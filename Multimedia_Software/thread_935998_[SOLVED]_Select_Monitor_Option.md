---
title: "[SOLVED] Select Monitor Option?"
date: 2008-10-02
forum: Multimedia Software
---

### Post by hypergeek14 on 2008-10-02
Was running Xubuntu and recently switched to Mint on XFCE.  I have been having the same problem with both.  I have a laptop with a broken screen, so I plugged in an external monitor.  

Here's the problem: Ubuntu thinks I am using two screens, both the laptop one and the external one.  Odder still, it doesn't register the two screens as next to each other, as in a duel-monitor system, but rather as a smaller display inside of a bigger one.  This means that the desktop background fills the screen, but when I maximize a window, it only maximizes to the size of the smaller screen.  

As for panels, on the "Customize Panel" box, there is an option to select which monitor the panel is displayed on.  If I select monitor one, the panel is limited to th[HTML][/HTML]e mini screen, but if I select the second monitor, the panel uses the full screen length.  

I am looking for a similar option that will make the system know that I am only using the bigger screen.  

I have tried many things all of which have failed: 
[LIST]
[*]Physically removing the laptop screen
[*]Deactivating the laptop screen by pressing fn + CRT/LCD
[*]Putting the laptop screen on, unplugged, but closed
[*]Switching resolutions in the display settings box
[*]Trying to reconfigure through the terminal ("sudo dpkg -reconfigure xserver -xorg")
[/LIST]

Can anyone help me out?  Is there some sort of monitor selection utility I could use?  

I attached a picture of the screen in case there is confusion.

---

### Post by hypergeek14 on 2008-10-08
Anyone?

---

### Post by hypergeek14 on 2008-10-10
After having no replies, I reposed the question on the Mint Forums at [http://www.linuxmint.com/forum/viewtopic.php?f=59&t=17655&p=106441]("http://www.linuxmint.com/forum/viewtopic.php?f=59&t=17655&p=106441").  

This time I had success!  For future reference, typing the following code into the terminal brought up the preferences that I needed.  

```
gksu displayconfig-gtk
```

---

