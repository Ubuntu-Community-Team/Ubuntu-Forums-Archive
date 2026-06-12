---
title: "XBMC FUllscreen"
date: 2013-03-28
forum: Multimedia Software
---

### Post by sugarat on 2013-03-28
Hi, 

 I am trying to get XBMC to display fullscreen on my TV.  At the moment however, I get half on my PC screen, and half on the TV screen, so it's stretched across the two devices! How do I get it to only show on the TV please?

My PC is using an Intel graphics adapter with HDMI connection to the television. 

Many thanks

---

### Post by jawilljr on 2013-03-28
Try using [this script.](http://www.rizsilverthorn.net/linux/xbmc-on-dual-monitors/)

It works for me.

You might have to install wmctrl. (sudo apt-get install wmctrl)

Jerry

---

### Post by sugarat on 2013-03-29
Hi, 

 Thanks for the script.  If I set anything other than display 0 or 0.0 on line 5,  I get 'Cannot open Display' and XBMC seg faults and core dumps. 

How do I find out what display number my TV is using?

Many thanks

---

### Post by MacOsX74 on 2013-03-29
Hi!

i have been running this script myself and it works but not very good. You will not get xbmc to run videos perfect when using it. 
The only way to get it to work with two monitors is to set up dual x servers and run xbmc on one and your linux desktop on the other. That way you get xbmc to play videos perfect. You cant use the very important feature of xbmc, adjust refreshrate to match video when your using the script mentioned above. If your using dual x servers you wont even notice that xbmc is running. Just start your tv and its up and running and your pc  screen is free for doing something else.

---

### Post by jawilljr on 2013-03-29
MacOsX74, That script requires seperate X screens...I forgot to add that to the post. The script keeps XBMC from [locking the mouse. ](http://blog.burlock.org/xbmc/77-fullscreen-xbmc-without-locking-the-mouse)

If you want to use twinview then the below script should work.

```
#!/bin/bash

move_and_fullscreen(){
  NAME='XBMC Media Center'

  while [ -z "`wmctrl -l | grep \"$NAME\"`" ]
  do
      sleep 1
  done

  wmctrl -r "$NAME" -b remove,maximized_vert; wmctrl -r "$NAME" -b remove,maximized_horz
  wmctrl -r "$NAME" -e '0,1280,-1,-1,-1'
  wmctrl -r "$NAME" -b toggle,fullscreen
}

move_and_fullscreen &
__GL_SYNC_TO_VBLANK=1 __GL_SYNC_DISPLAY_DEVICE=DFP-1 SDL_VIDEO_ALLOW_SCREENSAVER=0 exec xbmc
```

I got that script from [here](http://wojnickitech.blogspot.com/2011/01/xbmc-and-nvidias-twinview.html), and from [here.](http://forum.xbmc.org/showthread.php?tid=130094&pid=1088558#pid1088558)

I had to modify it slightly by adding the line below:

```
wmctrl -r "$NAME" -b remove,maximized_vert; wmctrl -r "$NAME" -b remove,maximized_horz
```

above this line:

```
wmctrl -r "$NAME" -e '0,1280,-1,-1,-1'
```

Also in  both scripts you need to put XBMC in "windowed" mode.

I do agree with MacOsX74, seperate X screens is the best way to go.

Jerry

---

### Post by MacOsX74 on 2013-03-29
> **jawilljr said:**
> MacOsX74, That script requires seperate X screens...I forgot to add that to the post. The script keeps XBMC from [locking the mouse. ](http://blog.burlock.org/xbmc/77-fullscreen-xbmc-without-locking-the-mouse)

If you want to use twinview then the below script should work.

```
#!/bin/bash

move_and_fullscreen(){
  NAME='XBMC Media Center'

  while [ -z "`wmctrl -l | grep \"$NAME\"`" ]
  do
      sleep 1
  done

  wmctrl -r "$NAME" -b remove,maximized_vert; wmctrl -r "$NAME" -b remove,maximized_horz
  wmctrl -r "$NAME" -e '0,1280,-1,-1,-1'
  wmctrl -r "$NAME" -b toggle,fullscreen
}

move_and_fullscreen &
__GL_SYNC_TO_VBLANK=1 __GL_SYNC_DISPLAY_DEVICE=DFP-1 SDL_VIDEO_ALLOW_SCREENSAVER=0 exec xbmc
```

I got that script from [here](http://wojnickitech.blogspot.com/2011/01/xbmc-and-nvidias-twinview.html), and from [here.](http://forum.xbmc.org/showthread.php?tid=130094&pid=1088558#pid1088558)

I had to modify it slightly by adding the line below:

```
wmctrl -r "$NAME" -b remove,maximized_vert; wmctrl -r "$NAME" -b remove,maximized_horz
```

above this line:

```
wmctrl -r "$NAME" -e '0,1280,-1,-1,-1'
```

Also in  both scripts you need to put XBMC in "windowed" mode.

I do agree with MacOsX74, seperate X screens is the best way to go.

Jerry

Seperate x screens are not the same as dual x servers. You cant use twinview with xbmc. That dosent run well. Add a new user and start an new x session. Then you have dual x servers running. Completly independant from each other. Run xbmc on one user and your desktop on the other user.  Thats the way i have my server setup but with the difference that i use remote desktop for my desktop user. I think its a good way to go. I have xbmc running and my desktop free for any other use. 
Just my two cent.

---

### Post by gordintoronto on 2013-03-30
What version of Ubuntu? What resolution are the two screens? Did you take steps to use them as separate screens?

When I plug my TV into my laptop, the same thing is displayed on both screens. Never a problem of the type you described.

---

### Post by MacOsX74 on 2013-03-30
> **gordintoronto said:**
> What version of Ubuntu? What resolution are the two screens? Did you take steps to use them as separate screens?

When I plug my TV into my laptop, the same thing is displayed on both screens. Never a problem of the type you described.

If you have same picture on both screens then your running twinview. Then you cant use xbmc to adjust refreshrate to match video which is needed for smooth video playback. You need to enable dual monitors which with Nvidia graphics is called seperate x screens. There you setup each screen with the settings you want. If you have Nvidia make sure your using driver 302.xx or newer.

---

### Post by sugarat on 2013-03-31
I have managed to get this sorted with the aid of a kind soul on the XBMC chat room.

The solution is to have a script which uses randr to disable the PC's main screen, allowing XBMC to run fullscreen on the TV output.  In my case, with a Dell XPS One 27, such a script would be along the lines of:

```

#!/bin/sh
xrandr --output eDP1 --off
xrandr --output HDMI1 --mode 1920x1080 --rate 60

```

Many thanks

---

### Post by kylex4 on 2013-11-11
> **MacOsX74 said:**
> Hi!

i have been running this script myself and it works but not very good. You will not get xbmc to run videos perfect when using it. 
The only way to get it to work with two monitors is to set up dual x servers and run xbmc on one and your linux desktop on the other. That way you get xbmc to play videos perfect. You cant use the very important feature of xbmc, adjust refreshrate to match video when your using the script mentioned above. If your using dual x servers you wont even notice that xbmc is running. Just start your tv and its up and running and your pc  screen is free for doing something else.

Hi

Can you share any details on your setup? Do you have it working with one card or are you using two? Nvidia or AMD?

/Kylex

---

