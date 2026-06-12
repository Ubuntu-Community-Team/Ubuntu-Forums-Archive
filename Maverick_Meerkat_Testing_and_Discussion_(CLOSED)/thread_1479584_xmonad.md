---
title: "xmonad?"
date: 2010-05-10
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by ranch hand on 2010-05-10
I remember folks talking about this bugger last round.  As a matter of fact I installed it on the minimal install with gnome desktop environment.

Never could get it to start, couldn't find its files except one in /usr/bin.

Thought I would get serious about it to day.

All I can say is 

How in flinderation do you get this thing to do anything?

I actually found a menu entry for it under "other" which was not selected.  Selected it and tried to start it.  No go.

Added the launcher to the panel and tried to start from there.  No go.

Gave up long ago on the terminal because nothing happens there except to tell me it doesn't exist "no executable file".  The properties of  /usr/bin/xmonad claim it is.

The man page refers to ".xmonad/xmonad.hs" can't locate that.

Also refers to "~/.xinitrc file" as the place to add "exec  xmonad".  Can't find it either.

Now it is obvious that I am doing something really stupid here or this would work.  Have a good laugh, roll on the floor, and then, if you have the energy left, give me a clue.

---

### Post by descendent87 on 2010-05-10
Had a play with it before on Arch linux, never really got tiling window managers though.
[Arch Wiki - Xmonad](http://wiki.archlinux.org/index.php/Xmonad) has a pretty good guide for starting/setting up, might be of some use

---

### Post by alexgenaud on 2010-05-10
I just wrote up a Xmonad tutorial on a clean Lucid installation. If you can endure a weekend learning curve, I'm convince few will ever go back:

[http://genaud.net/2010/05/xmonad-on-lucid-lynx/](http://genaud.net/2010/05/xmonad-on-lucid-lynx/)

---

### Post by ranch hand on 2010-05-10
I copied that bugger and saved it here and over on the install in question.  I will be working on this.  Just curious.

Some one brought it up in the discussion of G-S last round and made me want to see it.

Don't know if I will like it but there is only one way to find out.  It is not on one of my main installs so I can play with it a little here and there until I decide if it is for me or not.  May want to keep it around just as a novelty, who knows.  May just love the sucker too.

Thanks a bunch.

---

### Post by ronacc on 2010-05-10
I just shutdown my mangy install for the night but I'll give it a shot too , tomorrow .

---

### Post by ranch hand on 2010-05-11
Well I had partial success.

I had a failure to load any modules which may have to do with the command
> 
$ gconftool-2 -s  /desktop/gnome/session/required_components/windowmanager xmonad --type  string
which I entered as above while wondering if I needed to change;
> 
--type string
to something that would actually make sense.

I did get the option to use a xmonad session on login.  It somewhat worked.

On rebooting (by tty2), to both a gnome and a failsafe gnome session, I have no panels and can't create a launcher from the desktop right click menu and had no success in launching a CLI any other way.

Here is a screen shot.  The bare spot in upper right is my fault for not moving the screen shot box down but the error message is coherent.

---

### Post by taavikko on 2010-05-11
> **ranch hand said:**
> Well I had partial success.

I had a failure to load any modules which may have to do with the command
```
conftool-2 -s /desktop/gnome/session/required_components/windowmanager xmonad --type string
```
which I entered as above while wondering if I needed to change;
```
--type string
```
to something that would actually make sense.



**--type string** changes the default string "gnome-wm" to "xmonad"

The above command was correct, no need to change it to anything.

You can test this with
```
gconftool-2 --get /desktop/gnome/session/required_components/windowmanager
```
which gives the setting currently active.

```
conftool-2 -s /desktop/gnome/session/required_components/windowmanager im_just_a_test --type string
```
which set's the setting to wanted string, in this case "im_just_a_test"

---

### Post by ranch hand on 2010-05-11
That is kind of what I figured.  I have no idea what to do next.

I wonder if the problem is in my install.  It is an upgraded (last round) 9.10>10.04>10.10 minimal install using the Gnome desktop instead of the Ubuntu desktop.  I will continue to update the bugger for now and maybe just replace it with an install of "normal" 10.10.  Have to think about it some and maybe poke it here and there a bit after looking at the man page again.

It is in the maverick repo so I would think it should work somehow.  I suspect I am just too noobish to see something obvious that I am doing to screw this.

---

### Post by LKjell on 2010-05-11
I use the script below to sort of "install"
Beside you need to install some sort of programs to make it pleasant.

```
sudo apt-get install xmonad xmobar dmenu trayer
```
[B]
Make gnome run xmonad wm[/B]
```
#!/bin/bash
gconftool -t string -s /desktop/gnome/session/required_components/windowmanager "xmonad"
gconftool -t boolean -s /apps/nautilus/preferences/show_desktop false
gconftool -s /desktop/gnome/session/required_components/panel "" -t string 
```

This is my **~/.xmobarrc** I am using labtop so the battery you can sort or remove it.
```
Config { 
	font = "-*-Fixed-Bold-R-Normal-*-13-*-*-*-*-*-*-*", 
	bgColor = "black", 
	fgColor = "#8822FF", 
	position = TopW L 90, 
	lowerOnStart = True, 
	commands = [ 
		Run Cpu ["-L","3","-H","50","--normal","green","--high","red"] 10, 
		Run Network "eth0" ["-L","0","-H","32","--normal","green","--high","red"] 10, 
		Run Memory ["-t","Mem: <usedratio>%"] 10, 
                Run Battery ["-L","30","-H","60","--high","green","--normal","yellow","--low", "red"] 10,
		Run Swap [] 10, 
		Run Date "%V %a %b %_d %H:%M" "date" 10, 
		Run StdinReader
	], 
	sepChar = "%", 
	alignSep = "&&", 
	template = "%StdinReader% && %cpu% | %eth0% | %memory% | %battery% | Week %date% "
}
```

The bread and butter **~/.xmonad/xmonad.hs**.
When you have Tall use alt + shift + x to minimize/hide window. alt + x to restore it. If there are too many windows it will hide the old ones too. You can get those auto hide windows back by moving the order of windows with alt + shift + j/k
```
import XMonad
import XMonad.Actions.CycleWS
import XMonad.Config.Gnome

import XMonad.Hooks.DynamicLog
import XMonad.Hooks.ManageDocks
import XMonad.Hooks.ManageHelpers

import XMonad.Layout.NoBorders
import XMonad.Layout.Minimize
import XMonad.Layout.LimitWindows
import XMonad.Layout.Tabbed
import XMonad.Layout.Named

import qualified XMonad.StackSet as W
import XMonad.Util.Run(spawnPipe)
import XMonad.Util.EZConfig(additionalKeys)
import System.IO

myManageHook = composeAll [
	isFullscreen --> doFullFloat ]

myTabConfig = defaultTheme { inactiveBorderColor = "#FF0000",
				inactiveColor = "#000000",
				inactiveTextColor ="#00FFFF",
				activeBorderColor = "#0000FF",
				activeTextColor = "#00FF00",
				activeColor = "#000000"}

myLayout = tall ||| tab ||| full
	where
		tall = named "Tall" $ limitWindows 4 $ minimize
			$ Tall 1 (3/100) (1/2)
		tab = named "Tab" $ tabbed shrinkText myTabConfig
		full = named "Full" $ Full

main = do
	xmproc <- spawnPipe "xmobar"
	gnomeRegister :: MonadIO m => m()
	xmonad $ gnomeConfig {
		manageHook = manageDocks <+> myManageHook
			<+> manageHook gnomeConfig,
		layoutHook = smartBorders $ avoidStruts  $ myLayout,
		focusedBorderColor = "#0000FF",
		focusFollowsMouse = False,
		logHook = do
			dynamicLogWithPP $ xmobarPP {
				ppOutput = hPutStrLn xmproc,
				ppTitle = xmobarColor "blue" "" . shorten 50
			}
	} `additionalKeys`[
		-- Minimize
		((mod1Mask .|. shiftMask, xK_x),
			(withFocused $ \f -> sendMessage $ MinimizeWin f)
                         >> windows W.focusDown),
		((mod1Mask, xK_x), sendMessage RestoreNextMinimizedWin),
		-- Hide Xmobar
		((mod1Mask .|. shiftMask, xK_h), sendMessage ToggleStruts),
		-- Workspace handling
		---- Using left/right
		((mod1Mask, xK_Right), nextWS),
		((mod1Mask, xK_Left),  prevWS),
		((mod1Mask .|. controlMask, xK_Right), shiftToNext >> nextWS),
		((mod1Mask .|. controlMask, xK_Left),  shiftToPrev >> prevWS),
		---- Using u/i
		((mod1Mask, xK_i), nextWS),
		((mod1Mask, xK_u), prevWS),
		((mod1Mask .|. controlMask, xK_i), shiftToNext >> nextWS),
		((mod1Mask .|. controlMask, xK_u), shiftToPrev >> prevWS),
		-- Gnome Settings
		((mod1Mask .|. shiftMask, xK_q), spawn "gnome-session-save --gui --logout"),
--		((mod1Mask .|. shiftMask, xK_q), spawn "killall5"),
		((mod1Mask .|. shiftMask, xK_comma), spawn "gnome-session-save --gui --shutdown-dialog"),
		((mod1Mask .|. shiftMask, xK_Return), spawn "gnome-terminal"),
		((mod1Mask, xK_Print), spawn "gnome-screenshot"),
		-- Dmenu
		((mod1Mask, xK_p), spawn "dmenu_run"),
		((mod1Mask, xK_m), spawn "update-manager"),
		((mod1Mask, xK_n), spawn "nautilus ~/")]

```

This is my **~/.profile** file to start trayer and volume control. It is not finished yet.
```
#gnome-shell --replace
#gnome-settings-daemon

if [ -x "/usr/bin/xmonad" ]
then
#	gnome-settings-daemon &
	trayer --edge top --align right --SetDockType true \
		--SetPartialStrut true --expand true --width 10 \
		--height 17 --transparent true --tint 0x000000 --alpha 0 &
#	nm-applet --sm-disabled&
	gnome-volume-control-applet &
fi
```

There is a lot to learn when you get into xmonad. I am actually still learning. But if you have any question and I know the answer I will help you. Just let your imagination go.

---

### Post by ranch hand on 2010-05-11
LKjell
I will have to work on this.

I am back on my "production" 10.10 but can do a lot of this in chroot.  I will do what I can now.

It would help if I was better at scripting but I will not learn any younger than I am now.  This will probably take me along a ways.

Thanks a whole big bunch.

I am not sure I really like the concept of xmonad but I need to get it up and running somewhere, sometime to find out.  This seems like the best opportunity to me.

It was mentioned, last round in the G-S thread.  I haven't had GS on anything for a while but what I saw of it was not real exciting.  It looked like it would work but I am not sure that it will, in any way, be better, just different.  And if they do not get a decent menu in it, it will be worse.  Icons have their place but that app menu with all the huge icons is just silly, as is an unsorted text list for a menu.

Xmonad may well be a better way to go or at least give us ideas to present for G-S as opposed to just whining.

Like it or not, it sure does look interesting.  It also looks quite worth the effort to learn something about.  There are things that I do that may well be easier to do in xmonad.

Thanks again.  I think I need to go and fire up my chroot environment for "Mini" and abuse it some.

---

### Post by ranch hand on 2010-05-11
I do not appear to have this file at all.  Should I just create one?
> 
This is my **~/.xmobarrc** I am using labtop so the battery you can  sort or remove it.
 	
The battery part does not bother me.  I have a UPS unit that the power manager assumes is a battery anyway an I keep it in the tray to check when the power flickers or dies.

---

### Post by LKjell on 2010-05-11
You need the file for xmobar and you need to call it in xmonad.hs . If you use my config files you should have it.

---

### Post by ranch hand on 2010-05-11
Is this different than the ~/.xmonad/xmonad.hs?

There seems to have been, through out this process, a shortage of some files.  I wonder if this is caused by doing a lot through chroot to my root partition and having a separate /home.

This type of editing I just do through nautilus.  I can look things over and see what is up and how they fit together.

---

### Post by LKjell on 2010-05-11
The xmobar is the panel which is different from xmonad. So ~/.xmobarrc is the file that tells you how the bar should look like. You cannot have comments in that file. Then you have ~/.xmonad/xmonad.hs that tells you how xmonad behave.

---

### Post by ranch hand on 2010-05-11
Hmm.  I will have to boot in over there, maybe through recovery and see what is up.

I do not have a ~/.xmobarrc file at all.

The config script "~/.xmonad/xmonad.hs" is there and, now, quite commented up.  It did not look a lot like yours so I stuck it all in and commented out the duplicates and things that seemed to conflict.

My drive may explode when I try to boot in, or at least go off in the corner and cry.

---

### Post by knarf on 2010-05-11
May I suggest running Xmonad from within its own session? It is IMnsHO much easier to add gnomes to an empty Xmonad session then it is to remove the unwanted crud from Gnome and still have something resembling a working Gnome desktop. It also has the advantage that you can go back to your well-known Gnome session if Xmonad is not your thing.

I'm running Xmonad with the xmobar 'panel' and a slightly hacked[SIZE=1] [1][/SIZE] trayer 'systray' app. The whole 'panel' is no more than 12 pixels high, on top of the screen. It contains an expanding notification area (centered because of the static nature of xmobar formatting) for those apps which need one.

If you find yourself using keyboard shortcuts in most programs a tiling window manager will suit you well. If you prefer to mouse around you probably will prefer a traditional, rodent-oriented WM.

[SIZE=1][1] trayer thinks a notification area should be at least 16 pixels high. I disagree. 8 pixels should be enough for anyone...[/SIZE]

---

### Post by ronacc on 2010-05-11
on my fresh install of 10.04 , sources changed and updated daily . Followed alexgenaud's tutorial to install xmonad . On logout was not given the choice to switch to a different session , on logging back into my gnome session fusion icon went berserk cloning itself every few seconds killed it by removing from startup list and reboot , on reboot I was given the choice to start an xmonad session , did so and it seems to work , ofcourse since I don't really know what it is supposed to do I can't really tell .

---

### Post by LKjell on 2010-05-11
> **knarf said:**
> May I suggest running Xmonad from within its own session? It is IMnsHO much easier to add gnomes to an empty Xmonad session then it is to remove the unwanted crud from Gnome and still have something resembling a working Gnome desktop. It also has the advantage that you can go back to your well-known Gnome session if Xmonad is not your thing.

I'm running Xmonad with the xmobar 'panel' and a slightly hacked[SIZE=1] [1][/SIZE] trayer 'systray' app. The whole 'panel' is no more than 12 pixels high, on top of the screen. It contains an expanding notification area (centered because of the static nature of xmobar formatting) for those apps which need one.

If you find yourself using keyboard shortcuts in most programs a tiling window manager will suit you well. If you prefer to mouse around you probably will prefer a traditional, rodent-oriented WM.

[SIZE=1][1] trayer thinks a notification area should be at least 16 pixels high. I disagree. 8 pixels should be enough for anyone...[/SIZE]

Well you can do that but you do miss a lot of feature as well. If you really want to hack then you can export WINDOW_MANAGER="xmonad" and clear the gnome-panel from the gconf before calling gnome-session. And when you logout from xmonad you add gnome-panel to the gconf.

Xmonad is nice but not alone.

---

### Post by ranch hand on 2010-05-11
Well I am logging into the xmonad session.  The problem is it doesn't work.

It was improved this time but there is no sign of xmobar that I can find at all.  I think this is not an xmonad problem.  I think this is a problem with this particular installation.

It was the first time I had installed minimal (I like it) and I had a lot of fun playing with it.  I think I may well have buggered something or not have it set up to be compatible with xmonad.

That install was keep on for this round of testing with the intention of replacing it.  I think I am going to do that, with a standard install and try it again.

I know I have a lot of installs but I feel like I can't really test more than one different thing on an install and be able to tell much about it with out wondering if something besides the plain OS is screwing with it.

Xmonad is interesting enough to get its very own installation.  If I do not like it I need to install the test ISOs regularly any way.  May get to it this evening.

---

### Post by ranch hand on 2010-05-11
OK.   I am back.

I installed 10.04, no restricted extras and updated it to current.

Ran through all of LKjells commands.  That seemed to go fine.

I have no ~/.xmonad directory.  I have no ~/.xmobar file.  I logged out and back in.  No such files.

I rebooted and checked and yes I have the xmonad session option.  Logged into gnome, still no files.

Came back here to whine.

Maybe I need to log into the xmonad session to get those files to exist in a form that nautilus can see.  Beats me.

---

### Post by ronacc on 2010-05-11
try logging into an xmonad session and then log out and back into gnome and see if they show up . they did on my install .

---

### Post by ranch hand on 2010-05-11
I will do that little thing directly.   I need to go and check a couple of installs to see if it is safe to upgrade this bugger and the primary backup anyway.

I had decided to do something along that line anyway.  Kind of hard to edit files that are no shows.

I would like to get the bugger upgraded to 10.10 but decided to see if I can get Xmonad working first.

---

### Post by alexgenaud on 2010-05-11
> **ranch hand said:**
> Well I had partial success.

I had a failure to load any modules which may have to do with the command
which I entered as above while wondering if I needed to change;
to something that would actually make sense.

It looks to me as though it worked quite well.
Does Win-Space, Win-Space, Win-Space cycle through about four different layouts?

I don't know how familiar you are with xmonad but it will look bare -- that's the point. There are no window decorations, nothing pretty except maximum content space!

If XMonad.Layout.NoBorders was the only module not loaded, no worries, it's not critical. All it is doing is removing the slight red border around full screen windows - it's a slight annoyance when, for example, watching a video.

If you stick with my config just for now, then modify your ~/.xmonad/xmonad.hs file. You'll need to remove two lines and modify another.

Delete or comment out (--) the line containing "import Xmonad.Layout.NoBorders" 

Delete or comment out the line containing "smartBorders &"

Modify the line "noBorders Full |||" to just "Full |||"

~/.xmonad/xmonad.hs now looks like this:

```

import XMonad hiding (Tall)
import XMonad.Hooks.ManageDocks
import XMonad.Hooks.SetWMName
import XMonad.Layout.ThreeColumns
import XMonad.Layout.HintedTile
--import XMonad.Layout.NoBorders

myLayout = avoidStruts $
--         smartBorders $
         hintedTile Tall |||
         hintedTile Wide |||
--         noBorders Full  |||
         Full  |||
         threeCol

  -- hintedTile listens to application hints, so as not to break gVim.
  where
     hintedTile = HintedTile nmaster delta ratio TopLeft
     threeCol   = ThreeCol nmaster delta ratio
     nmaster    = 1
     delta      = 3/100
     ratio      = 1/2

myManageHook = composeAll
    [ className =? "Gimp" --> doFloat ]

main = do
    xmonad $ defaultConfig
        { 
          -- Left WIN Key as modifying
          -- rather than Left ALT
          modMask = mod4Mask

        , manageHook = manageDocks <+> myManageHook <+> manageHook defaultConfig

        -- I used to use: avoidStruts $ layoutHook defaultConfig
        , layoutHook = myLayout

        -- This hack is necessary to make Java GUIs like NetBeans work.  See the FAQ.
        , logHook = setWMName "LG3D"
        }

```

Then you'll want to test (you should have done this the last time too!)

```

$ ghci ~/.xmonad/xmonad.hs
GHCi, version 6.10.4: http://www.haskell.org/ghc/  :? for help
Loading package ghc-prim ... linking ... done.
Loading package integer ... linking ... done.
Loading package base ... linking ... done.
Ok, modules loaded: Main.
Prelude Main> :quit
Leaving GHCi.

```

Note that 'ghci' compiles and tests your scripts. You'll need to type ":quit" to get out. But what you are looking for is the "Ok, modules loaded: Main." line.

Then iff and only iff the module loads OK, then type Alt-q which will restart Xmonad.

Best of luck to you,
Alex

---

### Post by alexgenaud on 2010-05-11
> **ronacc said:**
> on my fresh install of 10.04 , sources changed and updated daily . Followed alexgenaud's tutorial to install xmonad . On logout was not given the choice to switch to a different session , on logging back into my gnome session fusion icon went berserk cloning itself every few seconds killed it by removing from startup list and reboot , on reboot I was given the choice to start an xmonad session , did so and it seems to work , ofcourse since I don't really know what it is supposed to do I can't really tell .

Hmmm. Sorry. I wonder if a restart is always required. I suppose the session manager needs to be restarted. But, now that it works, you should still be able login to a GNOME window managed session. Do you mind testing that you can switch window managers at login?

---

### Post by alexgenaud on 2010-05-11
> **ranch hand said:**
> 
I have no ~/.xmonad directory.  I have no ~/.xmobar file.  I logged out and back in.  No such files.

Is it possible that those files are just hidden from your view in Nautilus? From your home directory, you can type Control-h to see all dot-files. Maybe you knew that, I dunno.

Cheers,
Alex

---

### Post by ranch hand on 2010-05-11
@alexgenaud

I know nothing about xmonad but would like to.

It did not, in fact go well.

I could not get out of anything.  I did get it to reboot through tty2.  I formated that pair of partitions and did a clean install of 10.04.  Went there and installed xmonad, feh, xmobar, etc.

Once again, this time on 10.04 instead of 10.10, I have no files to show for it at all.  I did go back and try to log in to a xmonad session, the option is there, but I can not do it at all as it gets to the screen where the login should be and freezes.

I can log into a gnome session without trouble.

It is awfully hard to edit files that do not show up in nautilus (yes I have show hidden files checked).

While in the Gnome session I did go to synaptic and reinstall xmonad but got no more results than before.

I am starting to believe that my problem may actually be with libplymouth2 screwing with me.  The problem with that is that I believe that libplymouth2 is the base of all evil (no it does not run well at all on my box for boot or shut down - boot=59.78 (bootchart) and shutdown about 2 minutes on a good day).

I will go over all the advice here again and see what happens.  What ever happens  I have a more usable OS on the test platform.

Geeze I want this to work.

---

### Post by LKjell on 2010-05-12
Ranch those files are just configuration files. You really do not need them. However if you just want to test xmonad and cannot select it from gdm then go to another tty ctrl + alt 1 log in and type ```
xinit -- :1
```

A white box should appear. Then in the box type ```
exec xmonad &
```

You should have xmonad running. If you have no configuration files meta is alt. So alt + shift + enter/return will fire up another terminal.

With this method of starting xmonad the xterm will spit out any errors it encounter.

---

### Post by ranch hand on 2010-05-12
I will have to try some of this tomorrow.  I am whipped.

I am also back in the land of no plymouth on my main internal drive and 9.04 which may not boot real fast but is faster than 10.04.  It also shuts down fast.  It is, of coarse, at this point also very stable and I ca nleave it and its boinc to run even when I am not around to check on it.

I am sure that I will get this xmonad thing to run.  I think I am going to winnow out the things to do with config and soforth from this thread and print it all out so I have a cheat sheet to inspire me.

---

### Post by LKjell on 2010-05-12
Sure. Just remember if you have no configuration files you can just make it. It is not harder than that.

---

### Post by knarf on 2010-05-12
> **ranch hand said:**
> I am sure that I will get this xmonad thing to run.  I think I am going to winnow out the things to do with config and soforth from this thread and print it all out so I have a cheat sheet to inspire me.

Login using the xterm session. You should have nothing but an xterm on an otherwise empty desktop. Now start xmonad from the command line. Does anything happen? Try Alt-Shift-Enter (or Win-Shift-Enter in case your config file remaps the modifier key), this should bring up a terminal. Do you get a terminal? If so, xmonad works.

If Alt-Shift-Enter (or Win-Shift-Enter, ...) brought up a terminal you can use that to try to launch xmobar. Just start it as you would start any other program. Does it appear?

If both xmonad and xmobar work all by themselves you know you have a working config. You can now either try to get it to work within Gnome or do as I did by adding the needed gnome-bits to the xmonad session. The latter is easy as all you have to do is create a startup script (eg. /usr/local/bin/xmonad.start) to launch those bits. Edit the session file (/usr/share/xsessions/xmonad.desktop) to point to your startup script instead of directly to xmonad:

```
[Desktop Entry]
Encoding=UTF-8
Name=XMonad
Comment=Lightweight tiling window manager
**Exec=xmonad.start**
Icon=xmonad.png
Type=XSession
```The startup script can look like this - uncomment the gnome bits you deem necessary:

```
#!/bin/bash

xrdb -merge .Xresources

gnome-settings-daemon

## I don't use these but you might want to. Uncomment when needed...

#gnome-panel &
#gnome-screensaver
#syndaemon -d -t
# feh --bg-scale /path/to/background/image.png &
xsetroot -solid black

# This must be started before seahorse-daemon.
eval $(gnome-keyring-daemon)
export GNOME_KEYRING_CONTROL
export GNOME_KEYRING_PID
export SSH_AUTH_SOCK

## This is all the stuff the original script writer found in "Startup Applications".
## I don't use it but you might want to...

#/usr/lib/gnome-session/helpers/at-spi-registryd-wrapper &
#bluetooth-applet &
#sh -c 'test -e /var/cache/jockey/check || exec jockey-gtk --check 60' &
#sh -c "sleep 60 && python /usr/share/gnome-panel/add-indicator-applet.py" &
#nm-applet --sm-disable &
#sh -c "sleep 1 && gnome-power-manager" &
#sh -c "sleep 31 && system-config-printer-applet > /dev/null 2> /dev/null" &
#seahorse-daemon
#update-notifier --startup-delay=60 &
#xdg-user-dirs-gtk-update

exec xmonad
```The remaining bits (eg. xmobar, trayer) are started by xmonad using the following configuration (~/.xmonad/xmonad.hs):

```
import XMonad hiding (Tall)
import XMonad.Hooks.ManageDocks
import XMonad.Hooks.SetWMName
import XMonad.Hooks.DynamicLog
import XMonad.Layout.ThreeColumns
import XMonad.Layout.HintedTile
import XMonad.Layout.NoBorders
import XMonad.Util.Run(spawnPipe)
import System.IO

myLayout = avoidStruts $
         smartBorders $
         hintedTile Tall |||
         hintedTile Wide |||
         noBorders Full  |||
         threeCol

  -- hintedTile listens to application hints, so as not to break gVim.
  where
     hintedTile = HintedTile nmaster delta ratio TopLeft
     threeCol   = ThreeCol nmaster delta ratio
     nmaster    = 1
     delta      = 3/100
     ratio      = 1/2

myManageHook = composeAll
    [ className =? "Gimp" --> doFloat
    , className =? "MPlayer" --> doFloat ]

main = do
    xmproc <- spawnPipe "xmobar"
    trayproc <- spawnPipe "killall trayer; trayer  --edge top --align center --SetDockType true --SetPartialStrut true  --expand true --widthtype request --transparent true --tint 0 --alpha 0 --height 12 --distance 0 --padding 0"
    xmonad $ defaultConfig
        {
        manageHook = manageDocks <+> myManageHook <+> manageHook defaultConfig

        , layoutHook = myLayout

        , logHook = dynamicLogWithPP $ xmobarPP
                        { ppOutput = hPutStrLn xmproc
                        , ppTitle = xmobarColor "green" "" . shorten 80
                        }
        }
```...and to complete the picture here's my ~/.xmobarrc:

```
Config { font = "xft:Sans-7:bold"
       , bgColor = "black"
       , fgColor = "grey"
       , position = Top
       , lowerOnStart = False
       , commands = [ Run Network "wlan2" ["-L","0","-H","32","--normal","green","--high","red"] 10
                    , Run Cpu ["-t", "c: <total>","-L","10","-H","50","--normal","green","--high","red"] 10
                    , Run Memory ["-H","80","--high","red","-t","m: <usedratio>%"] 10
                    , Run Swap ["-t", "<usedratio>"] 10
                , Run Date "%a %b %_d %Y %H:%M:%S" "date" 10
                    , Run StdinReader
                    ]
       , sepChar = "%"
       , alignSep = "!!"
       , template = "%StdinReader% !! %cpu% %memory%/%swap% %wlan2% | %whoami%@%hostname% | <fc=#ee9a00> %date% </fc>"
       }
```To get *trayer* (the notification area thingy) to behave in this configuration it needs to be rebuilt with a smaller minimum height. You can achieve this by getting the source (apt-get source trayer) and adjusting the value for PANEL_HEIGHT_MIN in *panel.h*. I set this to '8' instead of the default '16'. This seems to work fine with most notification icons even though some get clipped a bit.

If you don't like small fonts you might want to increase the font size in xmobar and the 'height' parameter in the call to trayer in xmonad.hs.

When you login choose the 'Xmonad' session. Don't want to use xmonad? Choose the 'Gnome' session (or whatever session you used to use).

---

### Post by ronacc on 2010-05-12
> **alexgenaud said:**
> Hmmm. Sorry. I wonder if a restart is always required. I suppose the session manager needs to be restarted. But, now that it works, you should still be able login to a GNOME window managed session. Do you mind testing that you can switch window managers at login?

after the first time I can now choose xmonad on a regular logout/login no restart required .

---

### Post by ranch hand on 2010-05-12
> **ronacc said:**
> after the first time I can now choose xmonad on a regular logout/login no restart required .
You lucky devil you.

---

### Post by ronacc on 2010-05-12
too bad I haven't got the foggiest idea what I did right :lolflag:

---

### Post by ranch hand on 2010-05-13
> **ronacc said:**
> too bad I haven't got the foggiest idea what I did right :lolflag:
Yes it is too bad.

I can't get the bugger to run at all now, even on this 10.04 install using the xterm terminal and 
```

exec xmonad &
[
```
claims there  is no such executable file.

I am going to mark this thread solved, as much as I hate to, because there is no more problem.  I have solved it by just giving up for the time being.

It is just silly to be banging my head on the wall for no reason.  I have 15 printed out pages of stuff on this and nothing seems to work so I will upgrade this install and purge the xmonad stuff.

---

