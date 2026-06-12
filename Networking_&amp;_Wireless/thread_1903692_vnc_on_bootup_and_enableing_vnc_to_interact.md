---
title: "vnc on bootup and enableing vnc to interact"
date: 2012-01-03
forum: Networking &amp; Wireless
---

### Post by liquid_legs on 2012-01-03
hey peoples once again.

i did a vnc tutorial on how to make vnc load up on boot but it seem that it dosent seem to be starting at boot anymore, it seemed to have only worked for the next 1 or 2 restarts and now its back to normal. it involved adding a boot up script and giveing it the permissions to be an exe.

also when i connect to a remote computer with vnc it seems to not show any of the icons on the screen neither any of the windows or tool bar, nor does it really allow me to interact with other desktops. i can run make programs run but that about it.
also when i connect to a computer it comes up with a message saying "could not acquire name for session bus" and then another message after that, something about not being able to run unity in right envirment or something like, i cant really remember the last message because it only comes up once.

i thinking that this mabey because im using a very customised version of ubuntu.

the OS im using in pinguy and the desktop envirment i am using in gnome 2 which sadly is dead

---

### Post by liquid_legs on 2012-01-03
oh and in the remote desktop i have enabled the the computer to be able to control the remote computer, + this is all i can see when connected

[http://s8.postimage.org/4zcs0hhl1/Tight_VNC_curnow_s_X_desktop_Titan_1_002.jpg](http://s8.postimage.org/4zcs0hhl1/Tight_VNC_curnow_s_X_desktop_Titan_1_002.jpg)

when see a blank screen, one cant really do much

---

### Post by MidnightJava on 2012-01-03
Try opening ~/.vnc/xstartup and commenting out the two lines under the comment that says "Uncomment the next 2 lines for normal desktop". I use RHEL at work, and I usually uncomment those lines to get a regular (non-X) desktop. But when I did the same thing on my Ubuntu system at home, I got a screen that looks like the one you posted.

---

### Post by liquid_legs on 2012-01-03
hmm i cant seem to find that line to in comment to get a normal desktop, that might be because im not using the default script. the script im using was from a ubuntu tutorial as an example of what youde put on a gnome deskstop. ive used this script cause vnc dosent seem to work if i use the default.

this is the script i used

#!/bin/sh

# Change "GNOME" to "KDE" for a KDE desktop, or "" for a generic desktop
MODE="GNOME"

#Uncommment this line if using Gnome and your keyboard mappings are incorrect.
#export XKL_XMODMAP_DISABLE=1

# Load X resources (if any)
if [ -e "$HOME/.Xresources" ]
then
        xrdb "$HOME/.Xresources"
fi

# Try a GNOME session, or fall back to KDE
if [ "GNOME" = "$MODE" ]
then
        if which gnome-session >/dev/null
        then
                gnome-session &
        else
                MODE="KDE"
        fi
fi

# Try a KDE session, or fall back to generic
if [ "KDE" = "$MODE" ]
then
        if which startkde >/dev/null
        then
                startkde &
        else
                MODE=""
        fi
fi

# Run a generic session
if [ -z "$MODE" ]
then
        xsetroot -solid "#DAB082"
        x-terminal-emulator -geometry "80x24+10+10" -ls -title "$VNCDESKTOP Desktop" &
        x-window-manager &
fi

---

### Post by MidnightJava on 2012-01-03
FWIW I've pasted below the default script from my installation. If that's the same script you used previously, then I guess it's not going to help you.

```
#!/bin/sh

# Uncomment the following two lines for normal desktop:

# unset SESSION_MANAGER

# exec /etc/X11/xinit/xinitrc

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
x-window-manager &

```

---

### Post by liquid_legs on 2012-01-03
its very simmilar. this is my default script

#!/bin/sh

xrdb $HOME/.Xresources
xsetroot -solid grey
#x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
#x-window-manager &
# Fix to make GNOME work
export XKL_XMODMAP_DISABLE=1
/etc/X11/Xsession

ill try your default script out, see if that does anything

---

### Post by liquid_legs on 2012-01-03
thanks midnightjava, your default script works but i still get a blank screen but with a terminal inside. its still not awesome but its an improvement.

when i uncommented the lines it said to uncomment to get a normal desktop i just got the same thing as i started off with.

---

### Post by MidnightJava on 2012-01-03
You're getting the same behavior I did with that script. I had only a terminal without the menus. I determined that for some reason Unity desktop was not working in VNC. (Running '/usr/lib/nux/unity_support_test -p' showed success in regular session and failure in vnc session).

So then I switched to Classic desktop, and eventually the menus showed up in VNC. I thought I re-booted and did not see it working, but then eventually it started working after re-booting several times for other reasons. Maybe you need to reboot twice; but perhaps switching to Classic desktop will make it work for you. I didn't investigate why it didn't work with Unity because I'm having other problems with Unity (failure to show desktop over half the time I boot, occasionally a CPU panic), so I'm glad to stay with Classic.

---

### Post by liquid_legs on 2012-01-04
well the problem may seem harder to solve than i though.
pinguy: a very customized version of ubuntu seems to be running on gnome 2, untiy i think is still there. so im not sure how this is going to work, and i cant enable ubuntu classic cause its either been removed of hidden.

the choices are:

pinguy
pinguy (no effects)
pinguy safe mode
user defined session
recovery console

---

### Post by liquid_legs on 2012-01-04
so anyone have any ideas

---

### Post by MidnightJava on 2012-01-05
I discovered that the problem with running unity in vnc is 3d. If you run ubuntu-2d session, which is unity, or any other 2d session, it will work. In my case I cannot find ubuntu-2d as a session to run. In /usr/share/gnome-session/sessions I see a number of sessions, including '2d-gnome.session'.

So then in xstartup, I put

```
/usr/bin/gnome-session --session=2d-gnome

```Note that you do not include '.session' when you specify the session name. I also have uncommented the line unset SESSION_MANAGER. With this configuration, the gnome desktop comes up in my vnc. Hopefully if you follow this pattern with whatever sessions you have on your system, it will work for you. Don't forget to kill your vnc and restart it after changing xstartup.

---

### Post by liquid_legs on 2012-01-05
im unsure where to place the code youve given me. you did'nt exaclty specify that i was supposted to add it or replace it with something else. i know cant exaclty add it anywhere.

---

### Post by MidnightJava on 2012-01-05
I put that line inside ~/.vnc/xstartup

---

### Post by liquid_legs on 2012-01-05
all well i could find .vnc/startup so i changed it to that path and then added the code for the gnome 2D session. i put the code you gave me in that line but im not sure if im right or not. this is what ive done

#!/bin/sh

# Uncomment the following two lines for normal desktop:

 unset SESSION_MANAGER

# exec /etc/X11/xinit/xinitrc

[ -x /.vnc/xstartup  ] && exec /.vnc/xstartup /usr/bin/gnome-session --session=2d-gnome
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
x-window-manager &

if im not right coul you post the correct script or just tell me what ive done wrong i have.
ive either done it wrong or theres something else i havent done right, cause im still getting the same issue of the terminal only showing up

---

### Post by MidnightJava on 2012-01-05
I made my script slightly different. I have the session setup on a line by itself instead of as an arg for an exec command. Here it is
```
# Uncomment the following two lines for normal desktop:

 unset SESSION_MANAGER

# exec /etc/X11/xinit/xinitrc

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
/usr/bin/gnome-session --session=2d-gnome &
x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
x-window-manager &

```And you have this script at ~/.vnc, right? You didn't have the ~ in the path you posted.

Also, you may need to change the line somewhat to match your environment. I ran 'whereis gnome-session" and found that it was at /usr/bin. You may be looking for session instead of gnome-session, depending on how your system is configured. And likewise I found 2d-gnome.session listed as one of the available sessions at /usr/share/gnome-session/sessions. So whatever value you assign to the --session arg needs to be one of the ones listed on your system (with '.session' removed). I don't know if they will be in the same place as on mine.

Hope that helps. Let me know.

---

### Post by liquid_legs on 2012-01-06
hmm, what command to you use to find out what sessions are available

---

### Post by MidnightJava on 2012-01-06
I happened to see a post that pointed me to the location where I found my session files, so I didn't have to search for them. The only way I can think of to find them is ```
sudo find / -name sessions
``` But I don't know for sure if on your system the folder containing the sessions will be named that way.

---

### Post by liquid_legs on 2012-01-07
hmm well ive tried setting a session but it just dosent seem to be working, i guess find and try out all the sessions and if that dosent work we might have to try something else

---

### Post by MidnightJava on 2012-01-07
Be sure to reboot after you make a change. Maybe even reboot twice. When I made the change I thought it wasn't working, and then ater rebooting a couple times for other reasons, I saw it was working.

---

### Post by liquid_legs on 2012-01-07
this is a quote from another guy who is useing the same customised OS of ubuntu as me, this method apprently worked for him

Hi,

Have you tried from Menu [IMG]http://forum.pinguyos.com/images/smilies/arrow.gif[/IMG] Preferences [IMG]http://forum.pinguyos.com/images/smilies/arrow.gif[/IMG] Remote desktop

[IMG]http://s15.postimage.org/xpr9ut8wp/remotedesktop_opening_mint11.png[/IMG]

*Tick  sharing both , security require user enter password (enter password  there too) & configure network accept connection , if you want  untick that 'you must confirm every...' .
*Also startup applications tick Remote desktop server
*Also open port from your firewall (i opened tcp+udp 5900-5904)
*After all this my PinguyOS required reboot, firewall didnt take the hint to allow all this.[IMG]http://forum.pinguyos.com/images/smilies/smile.gif[/IMG]

this should share your desktop. 


everything he put on here to do was all there by default except open the ports to the firewall which i could seem to figure out how to do, would you have any idea

---

### Post by MidnightJava on 2012-01-08
```
sudo ufw allow 5900
```will allow port 5900 incoming on all interfaces. 

```
man ufw
```will show you other forms of the command, which let you tailor rules for incoming vs outgoing, specific interfaces, protocols, etc. Also google on "ubuntu firewall" will give you some helpful Ubuntu support pages on it.

---

### Post by liquid_legs on 2012-01-08
ok just making sure cause this is what i did and still it did'nt work, even after rebooting 3 or 4 times

---

### Post by MidnightJava on 2012-01-09
Since you can connect to a session, and just don't see the menus, firewall was not likely the culprit; but it makes sense to cover all the bases.

I don't recall if I asked you this already, but are you starting the vnc server on some display other than 0? The system starts a vnc on display 0 that shares your GUI session; so you should be working with other display numbers if you want to change the desktop.

Beyond that, I'm out of ideas. I've only been using Ubuntu a few months, so I'm not much help beyond what I happened to have tried or implemented myself. Hopefully someone more knowledgeable will take note and offer you some further suggestions.

Whatever ideas you may decide to try, it may be good to just try them on the command line of your GUI session. When you find a command that seems to launch some Desktop successfully, then you can put it into the xstartup file. Just to make it easier to try things.

---

### Post by liquid_legs on 2012-01-11
well ive tried all the seesions i could but i just cant get it to run the way i want it to, im pretty much out od ideas

---

### Post by liquid_legs on 2012-01-11
if someone comes up with another idea and it works ill come and tell you just in case you know what to do when having the same problems as me

---

