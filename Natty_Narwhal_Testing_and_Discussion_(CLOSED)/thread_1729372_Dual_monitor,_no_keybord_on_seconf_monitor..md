---
title: "Dual monitor, no keybord on seconf monitor."
date: 2011-04-14
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Cerox Rex on 2011-04-14
I'v just don an upgrade from 10.10 to test Natty. First issue i noticed beside tryinbg to figure ut unity is that i cant type on my second monitor.:confused:

In 10.10 i ran seperate desktops on each monitor, now it seems as only my primary monitor is the only one i can work on.

My graphics hw is a GeForce GT 120M, yes its a laptop :)

I'm running nvidias 270.30 drivers.

What would be the best way to again run seperate desktops on both monitors. and get my keybord working on both of em, Kinda wierd issue rally that my keyboard wont work on both desktops :)

---

### Post by Cerox Rex on 2011-04-17
bumbs

I tried a new install of natty from iso. got both monitors working. but second display is preatty much useless as i still cant use it to type.

Further more there no way i can run any programs on it, cant add launcher and no menues besides what my mice has on rigth click :(

please help.

Gonna go and file a bugreport :P

---

### Post by 23dornot23d on 2011-04-17
Have you tried running it using twinview or is that no good to you ......... either.

---

### Post by Cerox Rex on 2011-04-17
Well filed a bug report with launchpad.

and no twin view is useless. seperate desktops are the only way to go :)

Just also found that when trying to add a program launcher by cut and paste, the new shortcut jumps back to primary display.

Conclusion, unity is useless as long as you have more than one monitor...

---

### Post by 23dornot23d on 2011-04-17
There is something odd .... as I tried to move a window into the second monitor it locks in place to the top bar - was going to try to show its ok - but its a bit weird the way it is now.

I use twinview and normally that is good enough for everything that I do ....... in gnome-shell ...... will check in there too cannot remember it having this lock to the top bar before.

Exactly .... works ok as it should do in Gnome-shell ...... Unity is different and as you say not really useable for twin monitors at the moment .......

---

### Post by Cerox Rex on 2011-04-17
hmm, seems to be same issue with "ubuntu-classic" (normal gnome) 

Cant cut/paste/copy or type anything on second monitor. but i'm able to use it for reading stuffs. damn this is a silly little anoying bug!

---

### Post by Blasphemist on 2011-04-17
I'm sorry to say you both are going to have to keep working on a solution, Unity does work with two monitors. See my screenshot. Nvidia does change things from how I configure it. I don't know enough about the Xscreens/Twinview to explain them to you. I do know that people that I believe are using the same driver mentioned are using 2 monitors. And they can type on each from a keyboard. Whichever application has focus, has been clicked in last, is the application that gets keyboard input.

---

### Post by Cerox Rex on 2011-04-17
> **Blasphemist said:**
> I'm sorry to say you both are going to have to keep working on a solution, Unity does work with two monitors. See my screenshot. Nvidia does change things from how I configure it. I don't know enough about the Xscreens/Twinview to explain them to you. I do know that people that I believe are using the same driver mentioned are using 2 monitors. And they can type on each from a keyboard. Whichever application has focus, has been clicked in last, is the application that gets keyboard input.

Twinscreen works, sortof. But when running seperate desktops on both monitors it fails. Have tried evry trick i know, i can only hope that someone who have made this work can tell me how to get seperate desktops working.

---

### Post by Blasphemist on 2011-04-17
As I said earlier I don't have nvidia as you do but here are screenshots of how configured the two monitors. You may have to do this in addition to your nvidia settings. I had to add the multiple display app (grandr) from the software center.

---

### Post by Cerox Rex on 2011-04-17
> **Blasphemist said:**
> As I said earlier I don't have nvidia as you do but here are screenshots of how configured the two monitors. You may have to do this in addition to your nvidia settings. I had to add the multiple display app (grandr) from the software center.

Tried it, unfortantly randr wont detect my second monitor :( ```
hallvar@Olga:~$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 175, current 1600 x 900, maximum 1600 x 900
default connected 1600x900+0+0 0mm x 0mm
   1600x900       50.0* 
   1360x768       51.0     52.0  
   1152x864       53.0     54.0  
   1024x768       55.0     56.0     57.0     58.0     59.0  
   960x600        60.0  
   960x540        61.0  
   840x525        62.0     63.0     64.0     65.0  
   832x624        66.0  
   800x600        67.0     68.0     69.0     70.0     71.0     72.0     73.0     74.0  
   800x512        75.0  
   720x450        76.0  
   720x400        77.0  
   700x525        78.0     79.0     80.0     81.0  
   680x384        82.0     83.0  
   640x512        84.0     85.0     86.0  
   640x480        87.0     88.0     89.0     90.0     91.0     92.0  
   640x400        93.0  
   640x350        94.0  
   576x432        95.0     96.0     97.0     98.0     99.0    100.0    101.0  
   512x384       102.0    103.0    104.0    105.0    106.0  
   416x312       107.0  
   400x300       108.0    109.0    110.0    111.0    112.0  
   360x200       113.0  
   320x240       114.0    115.0    116.0    117.0  
   320x200       118.0  
   320x175       119.0  

```

---

### Post by Blasphemist on 2011-04-17
> **Cerox Rex said:**
> Tried it, unfortantly randr wont detect my second monitor :( ```
hallvar@Olga:~$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 175, current 1600 x 900, maximum 1600 x 900
default connected 1600x900+0+0 0mm x 0mm
   1600x900       50.0* 
   1360x768       51.0     52.0  
   1152x864       53.0     54.0  
   1024x768       55.0     56.0     57.0     58.0     59.0  
   960x600        60.0  
   960x540        61.0  
   840x525        62.0     63.0     64.0     65.0  
   832x624        66.0  
   800x600        67.0     68.0     69.0     70.0     71.0     72.0     73.0     74.0  
   800x512        75.0  
   720x450        76.0  
   720x400        77.0  
   700x525        78.0     79.0     80.0     81.0  
   680x384        82.0     83.0  
   640x512        84.0     85.0     86.0  
   640x480        87.0     88.0     89.0     90.0     91.0     92.0  
   640x400        93.0  
   640x350        94.0  
   576x432        95.0     96.0     97.0     98.0     99.0    100.0    101.0  
   512x384       102.0    103.0    104.0    105.0    106.0  
   416x312       107.0  
   400x300       108.0    109.0    110.0    111.0    112.0  
   360x200       113.0  
   320x240       114.0    115.0    116.0    117.0  
   320x200       118.0  
   320x175       119.0  

```

Here is the result of xrandr on my machine.

> jim@jim-Satellite-L505:~/Documents$ xrandr
Screen 0: minimum 320 x 200, current 2966 x 900, maximum 8192 x 8192
LVDS1 connected 1366x768+0+0 (normal left inverted right x axis y axis) 353mm x 198mm
   1366x768       60.0*+
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 connected 1600x900+1366+0 (normal left inverted right x axis y axis) 443mm x 249mm
   1600x900       60.0*+
   1280x800       59.8  
   1152x864       75.0  
   1280x720       60.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1  
DP1 disconnected (normal left inverted right x axis y axis)
TV1 unknown connection (normal left inverted right x axis y axis)
   848x480        30.0 +
   640x480        30.0 +
   1024x768       30.0  
   800x600        30.0  
LVDS1 is my laptop monitor and VGA1 is my external monitor. It will depend on your connections used which your second monitor should show on. Try this. issue this command in a terminal-
> xrandr --auto
The manual for xrandr says that for connected but disabled outputs, this will enable them using their preferred mode. I see this looking at the manual this way from the terminal.
> man xrandr
The manual shows many other options but please start with this. Depending on what if anything changes more may need done. Examples at the end of the manual text shows how to more that may be helpful.

---

### Post by Cerox Rex on 2011-04-22
Unfortantly, xrandr us UNABLE to see my second monitor no matter what i tried. It only sees my laptops "internal" monitor.

---

### Post by Blasphemist on 2011-04-22
Can you pass any results from what you tried? Have you tried another cable. I'm sure there is a logical problem somewhere.

---

### Post by Cerox Rex on 2011-04-22
I'v tried to pass following commands

"xrandr --auto" and "xrandr -q"

both gives same output as i'v already posted. 
I'v tried this with a bunch of difrent nvidia drivers, nouvau driver and with no drivers.

---

### Post by Cerox Rex on 2011-04-22
hmm, this must be somthing with compiz!

When running in "ubuntu-classic (no effects)" Both monitors work flawless, configured easy peasy with nvidia-settings.

Wish it was as easy when running with compiz and unity! 
What is really going on! It really shouldnt be neccesary to do it the hard way with xrandr to get two monitors working with seperate desktops in a top modern os these days! I really hope theres a better sulution to this when 11.10 comes out! hehe :)

---

### Post by Blasphemist on 2011-04-22
That's some progress, very good! So what does xrandr output now in classic no effects? Retry that and some of the other stuff discussed and we may get further.

---

### Post by onlymee on 2011-04-24
I don't think it really counts a progress if you have to go back to "Ubuntu Classic (no effects)".  I have been running 10.10 with Compiz and two monitors very happily and upgrading to Natty had simply trashed my second screen.  I don't care about Unitym but Compiz Ubintu Classic should be working.

What was the number of the bug report you posted?

Antony

---

### Post by onlymee on 2011-04-24
I made some small progress.  I simply ran "compiz --display :0.1" from my other screen.  That got me my window decorations back and lets me use the keyboard, but my Gnome panel applets (Window List, Notification area etc.) still won't load on the second screen.

Anybody know what I need to edit to make compiz start up on both screens in the first place?

---

### Post by Cerox Rex on 2011-04-25
> **onlymee said:**
> I don't think it really counts a progress if you have to go back to "Ubuntu Classic (no effects)".  I have been running 10.10 with Compiz and two monitors very happily and upgrading to Natty had simply trashed my second screen.  I don't care about Unitym but Compiz Ubintu Classic should be working.

What was the number of the bug report you posted?

Antony

[https://bugs.edge.launchpad.net/ubuntu/+source/compiz/+bug/764051](https://bugs.edge.launchpad.net/ubuntu/+source/compiz/+bug/764051)

---

### Post by Cerox Rex on 2011-04-25
> **Blasphemist said:**
> That's some progress, very good! So what does xrandr output now in classic no effects? Retry that and some of the other stuff discussed and we may get further.

I'm still unable to make xrandr recognice my second monitor. 
Output is still the same as always! no diffrence.

---

