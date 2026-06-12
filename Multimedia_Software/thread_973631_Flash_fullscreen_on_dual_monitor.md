---
title: "Flash fullscreen on dual monitor"
date: 2008-11-06
forum: Multimedia Software
---

### Post by ruess on 2008-11-06
Hi there,

Can anyone help me to figure out if there is a way to allow flash to go Fullscreen while I am watching Youtube or Hulu (etc) on a second extended monitor? Currently, even if the web browswer with youtube is on the second extended monitor, the moment I press Fullscreen, it goes fullscreen on my primary monitor.

I have an ATI 3600 with the latest proprietary driver installed. Also, I have Flash 10 installed.

Thanks!

kevin

---

### Post by mk4umha on 2009-05-20
I've got the same problem, i'd like to go full screen on the monitor that i loaded the app with, not the primary one. the primary is the small 12.1" notebook screen and not my 24" LCD

---

### Post by DorianX on 2009-05-31
This is an intentional "security" feature of flash, to stop a mallicious app from trying to trick the user into thinking they're being shown a windows dialogue. Of course, it'd be nice if those of us who aren't liable to fall for that sort of thing could turn it off. 

On Windows, numerous sites document a patch that fixes this mis-feature, but I can't sort out any way to apply this technique to the linux version -- it's just a single-byte change to the dll file -- butI don't know what the offset is in the corresponding so file, or even if thehat part of the code is quite the same.

Seems like the linux community ought to be able to sort out the patch for this, but I haven't seen anything. Has anyone?

---

### Post by dal on 2009-06-14
Interesting - you guys mentioned not being able to get flash to fullscreen on your secondary monitors, but for me I have the reverse situation - everytime I fullscreen flash it pops up on my secondary monitor whether the browser that initiated the fullscreen process is currently on that monitor or not. Might be something to do with me having nvidia-settings/X configured to have my secondary monitor to the left of my primary one, maybe it's just going for the 0,0 coordinates and mapping out its fullscreen size from there?

Anyhow, I'm trying to get fullscreen flash video on my secondary monitor while I continue working on my primary one - the problem I'm having is that when I fullscreen a flash video and then change focus (even just by clicking on the browser window that spawned it) the fullscreen video display disappears. In addition to starting the video in firefox I've tried firing up the video streams in xine, mplayer, vlc, realplay, (stupid perhaps, but I figured that one of them might have flv video support bundled - apparently not) adobe's standalone flashplayer and swfdec-gnome (OSS standalone flash player). The source videos I used were from megavideo.com and youtube.com. Flashplayer and swfdec-gnome both seemed to attempt to load the youtube videos, displaying the control bar for them, but the display never changed from 0:00/0:00, despite the fact that I could easily enough view the videos in firefox. Neither player would even do that much when I tried to get them to display the megavideo.com videostream.

Kinda at my wits end here - does anyone know of another standalone flv player that will work with videos from those two sites or failing that some way of tricking the fullscreen flash window into thinking it still has focus when it doesn't?

Edit: A thought just occured to me - could the standalone flash players have been attempting to load the (rather large) test case videos fully before updating the display on the control bar from 0:00/0:00 and allowing playback to commence? Would mean that at least they work (well for the youtube videos anyhow, altho not the megavideo ones), just not in a way that is useful to me (I'm really looking for a standalone player capable of streaming).

---

### Post by abuelmagd on 2009-06-19
dal, you are the man.

This issue is flash related and your proposed solution simply works. I've seen a lot of ppl with a similar issue. I hope they somehow get to see your post. I put my TV on the left of my LCD and bingo. Tested on Ubuntu 9.04 with S-video out from an Nvidia Geforce 9600 GSO.

Many thanks dal.

---

### Post by dal on 2009-08-06
> **abuelmagd said:**
> dal, you are the man.

This issue is flash related and your proposed solution simply works. I've seen a lot of ppl with a similar issue. I hope they somehow get to see your post. I put my TV on the left of my LCD and bingo. Tested on Ubuntu 9.04 with S-video out from an Nvidia Geforce 9600 GSO.

Many thanks dal.

No problems mate, glad to have been able to help :)

---

### Post by dmoy on 2009-08-15
dal, funny solution to the screen orientation problem :)

I've also been trying to solve your stated problem and had basically no luck :\  I believe it would work easier if you ran separate X screens, but I really don't like that setup as much.  Having the extended desktop feels a lot more natural, but has the problem of fullscreen flash losing focus like a 6 year old with ADD.

The fact that [this solution](http://www.youtube.com/watch?v=qwH_-C2-93E) for windows exists is mildly infuriating... I don't want to boot into Windows just to watch stuff.

---

### Post by jastonas on 2010-06-14
No fix yet for this?

---

### Post by zigford on 2010-06-18
I have this same problem and my feeling is thank god html5 is coming along.
Sorry, I know this comment adds nothing to the thread.

---

### Post by ansil on 2010-07-12
hey guys i am new to the forum but have been using linux a while i am running ubuntu 10.04  and every version since 9 has had fullscreen flash problems frame by frame. nothing i have done has worked.  fresh install new drive video card replacement. i have gone through nearly every tutorial i can find could some one help.  it worked on ubuntu eight. do i need to go back to that as i do quite a bit of online video hunting and i hate windows.

---

### Post by darthpenguin on 2010-07-14
Just like to add; I have this problem also (Ubuntu 10.04). Setting up dual screen on Linux has been a challenge. It's almost working. I suffer video tearing on the secondary screen (left) and flash videos (from firefox, chrome, and problem other web browsers) open on the secondary monitor and stretch off the screen (if that makes sense). Is this a bug with flash or nVidia drivers? Is there a fix for this? both these problems are major annoyances.

Any help would be great. Thanks.

---

### Post by Zoharc on 2010-07-21
I am using Ati Radeon x1250. 

I get the flash on the desired window by setting new windows to spawn where the mouse is. I am also able to keep flash on full screen (megavideo) on my extended screen, while typing this message.  I believe that what fixed it was setting the focus to follow the mouse using Openbox window manager. 

The full screen remains as long as the mouse/focus stays out of the extended screen, where the full screen flash is.

-----
edit: Having just tested this out, compiz resorts to the usual annoying flash  at main display. However, it is now definite that open box and new spawn  settings are what allowed me (and now allows me once more) to get full screen flash and control over  spawn of full screen flash.

---

### Post by v_krishna on 2010-07-24
> **Zoharc said:**
> I am using Ati Radeon x1250. 

I get the flash on the desired window by setting new windows to spawn where the mouse is. I am also able to keep flash on full screen (megavideo) on my extended screen, while typing this message.  I believe that what fixed it was setting the focus to follow the mouse using Openbox window manager. 

The full screen remains as long as the mouse/focus stays out of the extended screen, where the full screen flash is.

-----
edit: Having just tested this out, compiz resorts to the usual annoying flash  at main display. However, it is now definite that open box and new spawn  settings are what allowed me (and now allows me once more) to get full screen flash and control over  spawn of full screen flash.

is there any way to get a similar setting in gnome, though? not being able to get flash fullscreen in my secondary monitor is annoying - and losing fullscreen when the flash window loses focus is more than annoying - but i'm not about to switch window managers just to fix this...

---

### Post by Zoharc on 2010-07-25
Switching Window Manager does not entail leaving Gnome, it just changes the windows decorations.

I still use gnome, and I found that I am able to get full screen on secondary screen using Metacitym (Gnome's default Window Manager), but it is a gamble -- at any rate, it is not possible to keep the full screen full while working on other screen. 

If you want to get a taste of it and choose for yourself, run in terminal the following:

sudo apt-get update
sudo apt-get install openbox & sudo apt-get install obconf

You can now log in through gnome/openbox session, or (if still confronted with metacity) run in terminal:

openbox --replace

Once you have these packages installed, go to System/Preferences/Openbox Configuration Manager. Select the windows tab, place new windows under mouse pointers and  prefer to place new windows in the monitor where the mouse is. 

in mouse tab select focus windows when mouse moves over them. 

This does this for me on two versions of Ubuntu.

---

### Post by Peter Jenkins on 2010-08-06
Just want to share my way of working around the issue. Maybe some don't use Compiz yet, and maybe those who use it already haven't tried out the Enchanced zoom features (see Accessibility category in settings manager). 

They allow to zoom the desired area of screen via shortcuts and mouse actions (make sure to disable focus following though). This way you can get any video to fill the desired monitor.

---

### Post by enerone on 2010-08-17
GENIUS!!!!! Peter, thanks a bunch,  the use of compiz Zoom dissabling de mouse sync works like a charme, you don't even need to use the fooll screen, you just need to center the browser window with the video and zoom it, this way you leave it in your second monitor !!!!

---

### Post by harry2harry2harry on 2010-08-17
My solution to the matter (under Linux Mint):

1. Uninstall Flash via synaptic package manager

2. Install Lightspark (flash alternative) via terminal:
      sudo add-apt-repository ppa:sssup/sssup-ppa
      sudo apt-get update
      sudo apt-get install lightspark

3. Install openbox via terminal:
      sudo apt-get install openbox

4. Put 2 launchers on your desktop,
   one with the command to start openbox:
      openbox --replace

   and a second with the command to start compiz again:
      compiz

The playback under lightspark is still a little buggy, but I read it reached beta status about 3 months ago.

---

### Post by mjones41 on 2010-08-21
Definitely a Compiz issue, turning desktop effects off fixed the problem for me.  

Just right clicking the desktop -> change Desktop Background -> Visual Effects -> None

Now I can watch Youtube on either screen (even both screens) in full screen no problem.

Ah well, someone will fix one day (Ubuntu 10.04 Flash 10.1.82.76)

---

### Post by Lucky75 on 2010-09-17
Yep, turning off desktop effects makes the video fullscreen on the correct monitor. I wonder what is causing it? I've tried disabling options in compiz one by one, but couldn't find it.

I still have a poorly scaled video though. Youtube is the worst, though others such as megavideo don't work exactly right either. Perhaps because my monitors are different resolutions. Example is attached.

---

### Post by SauCiSSoN on 2010-10-10
> **Lucky75 said:**
> Yep, turning off desktop effects makes the video fullscreen on the correct monitor. I wonder what is causing it? I've tried disabling options in compiz one by one, but couldn't find it.

I still have a poorly scaled video though. Youtube is the worst, though others such as megavideo don't work exactly right either. Perhaps because my monitors are different resolutions. Example is attached.

Same problem here.

The only bad workaround i got for youtube is to click on the "PopOut" button and maximized the window...

---

### Post by 3dmidi on 2010-10-15
I've gotten full-screen flash on one of my dual monitors, and I have focus in the other monitor. I'm using Kubuntu 10.4 on my laptop w/ external monitor. I use:

  [LIST]
[*]KDE
[*]Nvidia-Settings Twinview
[*]Chromium Browser
[/LIST]

and under *Window Behavior* in *System Settings* I set 

[LIST]
[*]Focus            > Policy: focus follows mouse
[*]Titlebar Actions > Titlebar & Frame, Active, Right button: Lower
[*]Titlebar Actions > Titlebar & Frame, Inactive, Right button: Lower
[/LIST]

I don't know if any of these settings are the default, but I think they're the most pertinent. To get fullscreen I do:
[LIST=1]
[*]open chromium in a window that's not maximized
[*]play the video and select fullscreen
[*]if the original chromium window isn't still on top, exit fullscreen and reselect it
[*]the chromium window is now on top of the fullscreen video,
[INDENT][*]so without moving the mouse out of the chromium window[/INDENT]
[*]**right click** the titlebar of the chromium window to send it to the back
[*]Focus doesn't flow to the fullscreen video, because the mouse didn't select a new window
[*]move the mouse to the other monitor, and don't move it back over the fullscreen video until the video is over
[/LIST]
I'll admit that this is pretty hackish, both
[LIST][*]because flash exits fullscreen if you move the mouse to the video and back out, or it starts a new video segment on its own (ie commercial) and
[*]it's based on flash behaving incorrectly. specifically, it doesn't raise the fullscreen window when it goes to fullscreen mode.
[/LIST]Good luck on gnome. I don't know how to get comparable setting. Nor have I tried this with firefox.
Drew

PS - did anyone mention hulu desktop? that plays fullscreen for me no problem and stays there.
PPS - sometimes this doesn't work the second time, and I have to move the chromium window and try again. go figure?

---

### Post by Lucky75 on 2010-10-16
Bump. Does anyone have any more ideas?

---

### Post by mrdengue on 2010-10-30
FINALLY!, I just installed Ubuntu 10.10 and it's fixed!:guitar:

---

### Post by gustav... on 2010-11-03
> **mrdengue said:**
> FINALLY!, I just installed Ubuntu 10.10 and it's fixed!

I installed Ubuntu Ubuntu 10.10 and it is not fixed. If I deactivate Compiz it`s ok, but with Compiz there is still the same problem.

I use AMD mobile Radeon with fglrx driver.

---

### Post by darude on 2010-11-11
> **Lucky75 said:**
> Perhaps because my monitors are different resolutions. Example is attached.

I experience the exact same problem. One monitor is on 1680x1050, the other on 1280x1024. The one way I can achieve full screen is to run it in a Virtual Machine! This problem has been around for ages, can't believe no one managed to fix this yet!

---

### Post by darude on 2010-11-11
Related thread and a workaround in the last few comments
[http://ubuntuforums.org/showthread.php?t=1009461&page=4](http://ubuntuforums.org/showthread.php?t=1009461&page=4)

---

### Post by amomentarylegacy on 2011-07-28
My solution is just to put the browser in fullscreen mode (usually f11) and place the window on the monitor of my choosing. Then I simply ctrl-+ to zoom in (or view > zoom in) until the image takes up most of the screen. It's not pretty but it works, and doesn't un-full screen if i click into a chat window on another monitor. Hope this helps somebody.

---

### Post by wissamshaar on 2011-08-03
> **abuelmagd said:**
> dal, you are the man.

This issue is flash related and your proposed solution simply works. I've seen a lot of ppl with a similar issue. I hope they somehow get to see your post. I put my TV on the left of my LCD and bingo. Tested on Ubuntu 9.04 with S-video out from an Nvidia Geforce 9600 GSO.

Many thanks dal.


Dal's trick worked for me too, Ubuntu 11.04. Thanks!

---

### Post by stealz on 2011-08-20
I am working on a different approach on fixing this issue using xdotool and wmctrl to move and resize the fullscreen flash video. It works perfectly if both monitors have the same size but needs some tweaking on different resolutions. Also, it seems that there could be a way to fix the losing fullscreen when not focused issue, but needs further testing. See [http://ubuntuforums.org/showthread.php?p=11170277](http://ubuntuforums.org/showthread.php?p=11170277) and would appreciate any help or input

---

### Post by pbritoferreira on 2011-08-25
I don't know if this works also for youtube videos, but I have a few flash video files in my computer and when I opened one, it went straight to fullscreen on the first screen and then I opened the second one and it got fullscreen on the second screen, then I was able to close the first one and keep working on the first screen with no focus problem.

I'm running Ubuntu 11.04 in an asus laptop.

I will try with youtube videos and then I'll post a response later tonight.

---

### Post by pbritoferreira on 2011-08-26
It didn't work, it worked only with downloaded flash videos. When I played youtube, when the monitor lost focus the video was not in fullscreen anymore =(

---

### Post by glide on 2011-09-28
Same problem with Ubuntu 10.04, Xinerama, Chromium.
Fullscreen is lost when focusing another window :(

---

### Post by ubunt12 on 2011-10-21
Bump, right click on youtube vid and select pop out from the menu

---

### Post by plasmafusion on 2011-10-21
@amomentarylegacy
that's a nice quick and dirty tip...wasted too much time on this already in the past. that works well enough for me.

---

### Post by goldaryn on 2012-09-06
People who have the "extra-widescreen bug" - check out this site

[http://al.robotfuzz.com/workaround-for-flash-on-linux-multihead-desktops/](http://al.robotfuzz.com/workaround-for-flash-on-linux-multihead-desktops/)

People whose fullscreen YouTube loses focus when you try to click on the other screen:

Workaround: right click on the video, press Pop Out, drag to correct monitor, maximise, press F11 to go Firefox fullscreen. :KS

Workaround for other sites: Try using [flash game maximiser]("https://addons.mozilla.org/en-US/firefox/addon/flash-game-maximizer/") to get a pseudo pop out.

---

