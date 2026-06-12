---
title: "Gromit-MPX for Thinkpad Yoga 12, Desktop Annotation, Draw Anywhere on Screen"
date: 2015-12-23
forum: Multimedia Software
---

### Post by maxchen on 2015-12-23
Desktop Annotation, Draw Anywhere on Screen: Gromit-MPX for Thinkpad Yoga 12 on Ubuntu (4 minutes short video): [https://youtu.be/bHmbxI0KvhI](https://youtu.be/bHmbxI0KvhI)

From [https://github.com/maxchendt/gromit-mpx/tree/Yoga12](https://github.com/maxchendt/gromit-mpx/tree/Yoga12)
This version will exit painting when clear screen, and swap shortcut key for "clear screen" and "toggle visibility"


How to install?
First install the package from the repo
```
sudo apt-get install gromit-mpx
```
Then install the tailored version
```

sudo apt-get install git build-essential autoconf
sudo apt-get install libgtk-3-dev
git clone -b Yoga12 https://github.com/maxchendt/gromit-mpx.git
cd gromit-mpx
autoreconf --install
./configure 
make

```
Test if it works
```
[COLOR=#006600][FONT=monospace]./gromit-mpx --key Pause --undo-key Delete[/FONT][/COLOR]
```
On Thinkpad Yoga 12

[LIST]
[*][COLOR=#444444][FONT=Lucida Grande]_Fn+P_[/FONT][/COLOR][COLOR=#444444][FONT=Lucida Grande] painting[/FONT][/COLOR]
[*][COLOR=#444444][FONT=Lucida Grande]_Fn+B_[/FONT][/COLOR][COLOR=#444444][FONT=Lucida Grande] clear screen [/FONT][/COLOR][COLOR=#ff0000][FONT=Lucida Grande]**and exit painting**[/FONT][/COLOR]
[*][COLOR=#444444][FONT=Lucida Grande]_Fn+SHIFT-P_[/FONT][/COLOR][COLOR=#444444][FONT=Lucida Grande] toggle visibility[/FONT][/COLOR]
[*][COLOR=#444444][FONT=Lucida Grande]_Delete_[/FONT][/COLOR][COLOR=#444444][FONT=Lucida Grande]  undo[/FONT][/COLOR]
[*][COLOR=#444444][FONT=Lucida Grande]_SHIFT-Delete_[/FONT][/COLOR][COLOR=#444444][FONT=Lucida Grande]redo last undone stroke[/FONT][/COLOR][COLOR=#444444][FONT=Lucida Grande]
[/FONT][/COLOR]
[/LIST]

"Install " on Ubuntu 14.04.3+mate 1.8.2   ```
[COLOR=#006600][FONT=monospace]sudo cp gromit-mpx /usr/local/bin/gromit-mpx-Yoga[/FONT][/COLOR]
```
Create launch on desktop: [COLOR=#000000][FONT=Lucida Grande]Applications -> Graphics -> Gromit-MPX, right-click ,  Add this launch to desktop.  [/FONT][/COLOR]And change the command to[COLOR=#000000][FONT=Lucida Grande]
[/FONT][/COLOR]```
**/usr/local/bin/gromit-mpx-Yoga --key Pause --undo-key Escape**
```[COLOR=#000000][FONT=Lucida Grande]
[/FONT][/COLOR]Note that this sets the undo to Escape Key, say[COLOR=#000000][FONT=Lucida Grande]
[/FONT][/COLOR]
[LIST]
[*]Esc    undo
[*]SHIFT-Esc: redo last undone stroke
[/LIST]

A example of configure   **~/.config/gromit-mpx.cfg**

```
# added default entries


"red Pen" = PEN (size=2.3 color="#da2832" minsize=2.3);
#"red Pen" = PEN (size=4 color="#da2832");
"black Pen" = "red Pen" (color="black");
"blue Pen" = "red Pen" (color="blue");
"yellow Pen" = "red Pen" (color="yellow");
"green Pen" = "red Pen" (color="green");
"green Marker" = PEN (size=5 color="green" arrowsize=1);      


"Eraser" = ERASER (size = 12);


"default" = "red Pen";
"default"[ALT] = "black Pen";
"default"[CONTROL] = "blue Pen";
#"default"[Button3] = "green Pen";
"default"[SHIFT] = "green Marker";
"default"[3] = "Eraser";



[COLOR=#000000][FONT=Lucida Grande]
[/FONT][/COLOR]
```

---

### Post by maxchen on 2015-12-23
> [COLOR=#333333][FONT=Helvetica Neue]Per default, it grabs the [/FONT][/COLOR]F9[COLOR=#333333][FONT=Helvetica Neue] and [/FONT][/COLOR]F10[COLOR=#333333][FONT=Helvetica Neue] keys, so that no other application can use them and they are available to Gromit-MPX only.

Because of this, I make a bit change for undo keys, for keys as Delete and Escape are so useful! Now in the updated version

[/FONT][/COLOR][COLOR=#333333][FONT=Helvetica Neue][FONT=courier new][SIZE=4]gromit-mpx-git --key F10 --undo-key Pause[/SIZE][/FONT]

then[/FONT][/COLOR]

[LIST]
[*]F10: toggle painting
[*]Ctrl+F10: clear screen **and exit painting**
[*]SHFT+F10: toggle visibility
[*]Fn+P: undo last stroke
[*]Fn+B: redo last undone stroke
[/LIST]
[COLOR=#333333][FONT=Helvetica Neue]In Yoga 12, [/FONT][/COLOR][COLOR=#333333][FONT=Helvetica Neue]Fn+P==Pause, [/FONT][/COLOR][COLOR=#333333][FONT=Helvetica Neue]Fn+B==_Ctrl+Pause_==Break[/FONT][/COLOR][COLOR=#333333][FONT=Helvetica Neue]

[/FONT][/COLOR]

---

### Post by maxchen on 2016-08-08
now ready for building deb package
[https://github.com/maxchendt/gromit-mpx](https://github.com/maxchendt/gromit-mpx)

to build deb package
```
sudo apt-get install --no-install-recommends git build-essential dh-autoreconf libgtk-3-dev
git clone -b Yoga12 [https://github.com/maxchendt/gromit-mpx.git](https://github.com/maxchendt/gromit-mpx.git)
cd gromit-mpx
dpkg-buildpackage -b -us -uc -i
cd ..
sudo dpkg -i gromit-mpx*.deb
```
Then, the hotkey is F10, and undokey is Pause. 

latest release:  [https://github.com/maxchendt/gromit-mpx/archive/1.1.4.tar.gz](https://github.com/maxchendt/gromit-mpx/archive/1.1.4.tar.gz)

---

### Post by maxchen on 2016-08-08
[http://forum.ubuntu.org.cn/download/file.php?id=184462](http://forum.ubuntu.org.cn/download/file.php?id=184462)
the deb file that works for both Ubuntu 16.04 and 14.04

---

