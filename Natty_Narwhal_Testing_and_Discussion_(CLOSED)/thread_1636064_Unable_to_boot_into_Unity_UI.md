---
title: "Unable to boot into Unity UI"
date: 2010-12-02
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Tellyviision on 2010-12-02
So pretty much, I have 11.04 fromt he daily build.

I can boot into classic desktop just fine, but when i boot into desktop session, none of the panels load.

Can anyone help me?

---

### Post by howefield on 2010-12-02
Moved to Natty Narwhal.

---

### Post by amano on 2010-12-02
What's your graphics card?
What's your driver?
Do the compiz effects (wobbly windows and company) work from within the Classic Gnome session?

---

### Post by Tellyviision on 2010-12-02
> **amano said:**
> What's your graphics card?
What's your driver?
Do the compiz effects (wobbly windows and company) work from within the Classic Gnome session?

1. ATI Mobility HD Radeon 5470

2. The default one that I installed from "additional drivers"

3. No.

---

### Post by cariboo on 2010-12-02
If you just want the panels, press Ctrl-Alt-T to open a terminal and type:

```
gnome-panel &
```

If you want Unity, type:

```
compiz --replace
```

I had the same problem this morning, after removing Unity so I could get gnome shell running.

---

### Post by Tellyviision on 2010-12-02
I tried that, and i got some weird unable to load applet error.
I can't copy paste the code since I can't access the internet in Desktop Session.

edit: do i type gnome panel & compiz --replace?

i only typed compiz --replace

---

### Post by wilee-nilee on 2010-12-02
You also have the choice of the classic desktop at login if you want until you get it set up. The classic desktop on my computer doesn't show the panels as well I just open a terminal and run killall gnome-panel this command wont work in unity though.

Thanks to cariboo907 I know ctrl-alt-t=a terminal.

---

### Post by efflandt on 2010-12-02
Those are 2 separate lines.  **gnome-panel &** should run gnome-panel forked into the backgrount and **compiz --replace** usually starts compiz and unity after a pause.  However, if you close the terminal after running the last command, that will also close compiz and unitiy.  So you either need to leave the terminal running (can be minimized).  Or if instead you do **nohup compiz --replace**, you can close the terminal and unity will appear to wink out, but should return shortly.  At least that is how it seemed to be as of Dec 1 build with nvidia proprietary drivers.

I just got home, so have not tried Dec 2 updates yet.

---

### Post by Tellyviision on 2010-12-02
> **efflandt said:**
> Those are 2 separate lines.  **gnome-panel &** should run gnome-panel forked into the backgrount and **compiz --replace** usually starts compiz and unity after a pause.  However, if you close the terminal after running the last command, that will also close compiz and unitiy.  So you either need to leave the terminal running (can be minimized).  Or if instead you do **nohup compiz --replace**, you can close the terminal and unity will appear to wink out, but should return shortly.  At least that is how it seemed to be as of Dec 1 build with nvidia proprietary drivers.

I just got home, so have not tried Dec 2 updates yet.

So I have to run gnome-panel & first, and then compiz --replace?

When I did compiz --replace I got an Unable to Load error.

---

### Post by cariboo on 2010-12-02
> **Tellyviision said:**
> So I have to run gnome-panel & first, and then compiz --replace?

When I did compiz --replace I got an Unable to Load error.

It sounds like you don't have the proper driver loaded to run compiz. What driver are you running with your ATI/AMD graphics card?

---

### Post by Tellyviision on 2010-12-03
Yea, like I said above I'm just using the default one that was with "additional drivers".

---

### Post by Anduu on 2010-12-03
I have never been able to get Unity running by normal means...ie logging into an Ubuntu Desktop session and enabling the plugin. A compiz --replace will ether segfault or just hang.

The only way I can run Unity is by building from source and running it as per the wiki.

I am running a Radeon X1300 via the opensource drivers and Compiz works fine otherwise.

---

### Post by cecilpierce on 2010-12-03
How can I get this panel to stay gone ?
The delete panel opt is grayed out and pkill makes it go away but comes right back, also everybody says Ctrl+Alt+T brings up a terminal but not for me ??? hmmmm !!!
Help, I'm getting another head ache :p

---

### Post by Quackers on 2010-12-03
In my Natty install which was upgraded from Maverick ctrl-alt-t does not do anything. But in my alpha 1 install it brings up a terminal. (Alt + F2 does nothing now :-) )

---

### Post by cecilpierce on 2010-12-03
> **Quackers said:**
> In my Natty install which was upgraded from Maverick ctrl-alt-t does not do anything. But in my alpha 1 install it brings up a terminal. (Alt + F2 does nothing now :-) )

Same thing here, A1 works and Maverick upgrade don't ! Guess I will just fiddle with A1, Thanks

---

### Post by Tellyviision on 2010-12-03
Sorry for the bump, but still no one knows?

---

### Post by Tellyviision on 2010-12-03
i got a copy/paste of my error for when I run compiz --replace

> ** (<unknown>:2193): WARNING **: Unable to load GDesktopAppInfo for 'ubiquity-gtkui.desktop'

** (<unknown>:2193): WARNING **: Unable to load GDesktopAppInfo for 'ubuntuone-control-panel-gtk.desktop'
Segmentation fault


---

### Post by nm_geo on 2010-12-04
I get the same responses Tellyviision...

---

### Post by efflandt on 2010-12-04
Tellyviision, which daily build are you using?  When I booted Dec 1 build iso from USB, it would not work with default ATI or Intel drivers (nothing installed from Additional Drivers, since that never works from iso).  Unity would come up for a few seconds, then it and all panels would disappear.

But alpha1 (probably same as Dec 2 build, since same file size) seems to boot fine on both of those (including desktop ATI X1300).  Although, double tap or mousepad buttons do not work on a Toshiba laptop with Intel video from 2006.

With nvidia, unity does not run unless it is a regular installation with nvidia drivers installed, then unity comes up automatically (with earlier builds I had to do the compiz --replace thing).  Although, the first time I tried classic, the panel applets crashed, and I had to do **sudo restart gdm** from a console (Ctrl+Alt+f1) which I had to do blind because that seems to be broken (login on lower right and does not scroll).

So maybe you need to try updating or a newer build, because things seem to be progressing (or sometimes regressing) daily.

---

### Post by Tellyviision on 2010-12-05
So heres what I did: (typing this from iPod, mehhh).

- deleted and reinstalled everything compiz/unity/nautilus/gnome related in synaptic. Didn't work. Same error for compiz --replace.

- reinstalled 10.10. Changed my sources to natty and upgraded it. Still didnt work

So I just gave up and switched back to 10.10. Hopefully on future builds this won't happen.

---

### Post by youoh on 2010-12-05
start ubuntu and dont log in:
switch to anaother tty with ctl+alt+F1 for example

delete: 

rm -r ~/.compiz-1
rm -r ~/.config/gnome-session

reboot

does the trick for me

---

### Post by rajeev1204 on 2010-12-17
Same issue since last 2 weeks after install . Havent seen the unity desktop yet .

But from a terminal i get these:

** (<unknown>:3253): WARNING **: Unable to load GDesktopAppInfo for 'ubiquity-gtkui.desktop'

** (<unknown>:3253): WARNING **: Unable to load GDesktopAppInfo for 'ubuntuone-control-panel-gtk.desktop'

segmentation fault,(core dumped)


Now i read somewhere these files are found in favorites folder but where is this folder ? 
[https://bugs.launchpad.net/unity/+bug/682345](https://bugs.launchpad.net/unity/+bug/682345)

Where are these .desktop files ?

---

### Post by cariboo on 2010-12-17
the file you are looking for is in /usr/share/glib-2.0/schemas

---

### Post by rajeev1204 on 2010-12-17
No luck editing that, seems like the crash is unrelated though. 

I get a seg fault in the end. Unity just cannot be enabled.

---

### Post by rajeev1204 on 2010-12-17
ook.

Found the problem. Unity works with the open source drivers and not the proprietary ATI drivers.Just found a bug report about the same and after removing fglrx i have unity back again.


[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/685682](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/685682)

---

### Post by goldsniper on 2010-12-18
Workaround.

Right click and create a new launcher. Put "unity" in the command box. And Save.

Click the launcher.

---

