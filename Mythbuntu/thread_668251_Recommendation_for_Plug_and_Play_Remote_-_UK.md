---
title: "Recommendation for Plug and Play Remote - UK"
date: 2008-01-15
forum: Mythbuntu
---

### Post by reclusivemonkey on 2008-01-15
Hello everyone,

I've finally given up on getting my iMon VFD LCD and remote working with MythTV. Can anyone point me to a link where I can buy a remote which will "just work"TM, preferably under £20? Thanks.

---

### Post by racmar on 2008-01-18
I just bought the snapstream firefly mini.  It is a little different, since it acts like a regular keyboard.  When you press a button on the remote, it sends actual keycodes just like a "real" keyboard.  The nice thing is that you can use a learning remote which can control all your other equipment, then just put the original away. 

See: [http://www.mythtv.org/wiki/index.php/Snapstream_firefly_mini](http://www.mythtv.org/wiki/index.php/Snapstream_firefly_mini)
It's a little under $30 from pcalchemy: [http://www.pcalchemy.com/product_info.php/products_id/516](http://www.pcalchemy.com/product_info.php/products_id/516)


I have the following xmodmap run from the autostart settings:

/home/myuser/fireflymini.xmodmap
```
!Close = 175
!Mute = 160
!Last = no keycode in XEV
!Exit = 234
!VOL+ = 176
!VOL- = 174
!Option = 134
!Firefly = no keycode in XEV
!Menu = 158
!Record = 177
!Guide = no keycode in XEV
!Stop = 164
!Prev|<< = 144
!Play = 179
!Next>>| = 153
!REW<< = 152
!Pause = 110
!FFWD>> = 180 


keycode 164 = Escape
keycode 234 = Escape

keycode 134 = i
keycode 158 = m
keycode 177 = r

keycode 110 = p
keycode 179 = p

keycode 144 = Home
keycode 153 = End

```

/home/myuser/.config/autostart/firefly.desktop
```
[Desktop Entry]
Encoding=UTF-8
Version=0.9.4
Type=Application
Name=firefly mini remote
Comment=add custome keys for firefly mini remote
Exec=xmodmap /home/myuser/fireflymini.xmodmap
StartupNotify=false
Terminal=false
Hidden=false

```

don't forget to change the myuser strings above.


If you really want to get fancy, you can use the lirc section, but the stuff above was easier for me.  Of course the downside is that with my setup ( not using lirc ), mythtv must always have "focus" or it cannot accept input from the "keyboard".  In my experience, it hasn't been a problem.

---

