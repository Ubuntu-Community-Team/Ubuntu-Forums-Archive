---
title: "12 monitors Natty Warhal"
date: 2011-09-26
forum: Multimedia Software
---

### Post by tiberiusrex on 2011-09-26
This is my success story for installing 3 ATI Firepro 2260's and 1 Radeon HD 5870 in the same computer.  

I've installed 4 video cards and 12 monitor screens which are used to monitor our networked hosting environment.  I used the radeon drivers.  I tried the proprietary drivers, but they didn't work for me (lines, crashes, and freeze-ups.)


**First, Install Ubuntu 11.4 Natty Warhal and video cards**

root@c1:/etc/X11# uname -a
Linux c1 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

# lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc RV620 [FirePro 2260]
02:00.0 VGA compatible controller: ATI Technologies Inc Radeon HD 5870 (Cypress)
04:00.0 VGA compatible controller: ATI Technologies Inc RV620 [FirePro 2260]
06:00.0 VGA compatible controller: ATI Technologies Inc RV620 [FirePro 2260]


**Create Xorg.conf**

Shutdown X and used Ctrl-Alt 1 to get a console session to run Xorg &#8211;configure.

sudo su
stop gdm
cd 
Xorg &#8211;configure
cp xorg.conf.new /etc/X11/xorg.conf

**XRandR**

Then reboot or start gdm. That will get you close enough that you can see where all your screens are. Don&#8217;t bother re-arranging until you have all your cards in, because they will move every time you put in a card. Best to have all the displays connected as well. Re-arrange the screens using xrandr or by changing where they&#8217;re plugged in. Here&#8217;s my xrandr script which is called at startup:

DISPLAY=:0.1 ; xrandr --output DisplayPort-2 --pos 0x0 --primary --output DisplayPort-3 --right-of DisplayPort-2  \
    --output DisplayPort-4 --right-of DisplayPort-3 --output DisplayPort-5 --below DisplayPort-2 \
    --output DisplayPort-6 --right-of DisplayPort-5 --output DisplayPort-7 --right-of DisplayPort-6

DISPLAY=:0.2 ;  xrandr --output DisplayPort-9 --primary --above DisplayPort-8 --auto --output DisplayPort-8 --auto

DISPLAY=:0.0 ; xrandr --output DisplayPort-0 --auto --below DisplayPort-1 --auto --output DisplayPort-1 --auto --primary

DISPLAY=:0.3 ; xrandr --output DisplayPort-10 --primary --above DisplayPort-11 --auto --output DisplayPort-11 --auto

Xrandr may not be needed if you can arrange the screens by plugging them in to the right ports. Each DISPLAY corresponds to the screens on a card.
Browser Sessions

**Start browsers**

Firefox didn't work very nicely, so we went with Chrome and Opera. Chrome was having problems on the refresh, so I went with 2 Opera screens. Still waiting to see if we still get timeouts.  Here's the monitor_screens.sh file which is called at startup to kill browsers, start browsers, and arrange them with devilspie:

root@c1# cat monitor_screens.sh
#
# Screen 6 needs its own user-data-dir so you can make it bigger without affecting all the other screens.

pidof chrome && kill `pidof chrome` 2>/dev/null
sleep 10

pidof opera && kill `pidof opera` 2>/dev/null
sleep 10

DISPLAY=:0.0 ; export DISPLAY
opera -geometry 1920x1080+0+0    -display :0.0 -newwindow [https://server/noc/write_screen.php?screen=0&](https://server/noc/write_screen.php?screen=0&)
opera -geometry 1920x1080+0+1080 -display :0.0 -newwindow [https://server/noc/write_screen.php?screen=6&](https://server/noc/write_screen.php?screen=6&)

DISPLAY=:0.1 ; export DISPLAY
google-chrome --user-data-dir=~/.config/google-chrome1 --app=https://server/noc/write_screen.php?screen=1&
google-chrome --user-data-dir=~/.config/google-chrome1 --app=https://server/noc/write_screen.php?screen=2&
google-chrome --user-data-dir=~/.config/google-chrome1 --app=https://server/noc/write_screen.php?screen=3&
google-chrome --user-data-dir=~/.config/google-chrome1 --app=https://server/noc/write_screen.php?screen=7&
google-chrome --user-data-dir=~/.config/google-chrome1 --app=https://server/noc/write_screen.php?screen=8&
google-chrome --user-data-dir=~/.config/google-chrome1 --app=https://server/noc/write_screen.php?screen=9&

DISPLAY=:0.2 ; export DISPLAY
google-chrome --user-data-dir=~/.config/google-chrome2 --app=https://server/noc/write_screen.php?screen=5&
google-chrome --user-data-dir=~/.config/google-chrome2 --app=https://server/noc/write_screen.php?screen=11&

DISPLAY=:0.3 ; export DISPLAY
google-chrome --user-data-dir=~/.config/google-chrome3 --app=https://server/noc/write_screen.php?screen=4&
google-chrome --user-data-dir=~/.config/google-chrome3 --app=https://server/noc/write_screen.php?screen=10&

# give the windows time to get their titles set
sleep 20

# devilspie configurations are in the ~/.devilspie directory
pidof devilspie && kill `pidof devilspie` 2>/dev/null
devilspie -a&
sleep 20

#  Do it twice so screens 2 and 3 align with the top edge of the screen
pidof devilspie && kill `pidof devilspie` 2>/dev/null
devilspie -a&

**Devil's Pie**

Devil's Pie is a little utility that resizes, positions and undecorates our browser sessions for us. It reads it's configuration files in the .devilspie directory. We set the title for the windows so Devil's Pie can match on the title. Here's an example:

root@c1# cat screen0o.ds
; 
( if 
  ( begin 
    ( is ( window_name ) "Screen0 - Opera" )
  ) 
  ( begin 
    ( undecorate )
    ( geometry "1920x1080+0+0" )
  )
)


**MANY THANKS!**  To all those that have posted answers to forums which got me to a solution.


**Works, but still has some problems**
a.) The full screen mode for my browsers makes them actually cover all monitors that are attached to that video card.  I've tried several configuration changes which have not worked.  That's why I had to use Devil's Pie.
b.)  The mouse traversal only works on the top row of monitors.  If I try to move the mouse between monitors on the bottom row, it doesn't go beyond the boundary of the monitors on that card.  But it does go from card to card on the top row.  Also, the traversal between cards 3 and 4 is reversed.

Neither of these problems bother me enough in this configuration to pursue them further.  You can see in my xorg.conf that I was trying ZaphodHeads and that didn't help.  Xinerama also seemed to make things worse, rather than better. 

If you're wondering why I attached xorg.conf as a Word document, it's because the .txt file was "too big."

---

