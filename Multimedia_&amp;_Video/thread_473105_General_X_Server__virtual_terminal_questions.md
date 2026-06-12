---
title: "General X Server / virtual terminal questions"
date: 2007-06-13
forum: Multimedia &amp; Video
---

### Post by JoSch on 2007-06-13
I now played a bit with new x servers in my virtual terminals and found out a lot through crawaling the inet but I still have a few questions.

I figured out that by switching to tty1 with STRG+ALT+F1 and doing the following I can create a new X server with a xterm in tty9:
```
X :1 &
export DISPLAY=:1
xterm
```
This way I can even add more than 4 new servers but since there is no F13 key I can use `chvt n` from tty1 to switch to any virtual terminal I created a new Xserver on.

All this gets a little tricky if I want to do this in my existing X session in tty7.
1. To run chvt I need sudo but I did a sudo chmod +s /usr/bin/chvt and now I can chvt without being root.
2. I can not creat a new X server fro the gnome terminal. I found out, that I have to change allowed_users=anybody in /etc/X11/Xwrapper.config and now this works too.
strangly enough this new Xservers wont show up when I do a ps -e | grep Xorg in tty1 - in my gnome terminal they do.
3. I cannot run applications from the gnome terminal in a specific X session.  Even after I do a export DISPLAY=:1 this error message will show up:
```
X: client 1 rejected from local host (uid 1000)
Xlib: connection to ":1.0" refused by server
Xlib: No protocol specified

xterm Xt error: Can't open display: :1.0

```
I cannot even do this from tty1 now, if the x session was created by the gnome terminal.
I found the xhost + command but it didn't change anything. Can you help?

---

