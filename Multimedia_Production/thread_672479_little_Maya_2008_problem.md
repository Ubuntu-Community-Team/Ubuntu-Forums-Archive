---
title: "little Maya 2008 problem"
date: 2008-01-19
forum: Multimedia Production
---

### Post by devix91 on 2008-01-19
I've searched everywhere but I couldn't find no-one with the same problem that i have.
   I have been using Maya mainly on mac, but then i switched to ubuntu, installed maya 2008 with no problem. It does work fine but there are few little things that really get on my nerves.
   So basicaly what happens is that when i press space and that quick menu appears, if i then click on any of those buttons the maya freezes as well as ubuntu, then the only resolution is rebooting the whole PC, and exactly the same thing happens when i right click an object and select one of the option from the drop-down menu that appears, however the top options work fine, it is only the ones under the top ones (vertex mode, polygon, edge etc...)
   Surprisingly the same thing also happens quite randomly, for example sometimes when i quickly press right mouse button and left mouse button the PC freezes. :confused:
   I am really desperate to fix this problem, its happened many times, and i even forgot to save my work several times ...
   Once I had to REDO UVs on a really complicated model of a robot.
I thought that i was gonna kill myself when i accidentaly accessed the 'space quick menu' and clicked on the create option. That happened right after i finished the UVs on the model.
   I mean man this really sucks. 

My graphics Card is GForce 8800
I have AMD 64bit
And about 2gb ram

Thank you for any respond, I am very grateful for any help :)

---

### Post by banda on 2008-01-27
i am sailing in the same boat...
i do not know the solution for your problem, but i have installed a script that prompts me to save my work every 5 min [link]("http://www.highend3d.com/maya/downloads/mel_scripts/interface_display/Auto-Save-3962.html")

---

### Post by Keilious on 2008-02-01
Hmm... Same problem here, any solution to this yet?

---

### Post by eye208 on 2008-02-02
If X freezes and does not even react to Ctrl-Alt-Backspace, it is most likely due to a bug in the display driver.

You're not running Compiz, are you?

---

### Post by okiniko on 2008-02-02
I had this problem as well. I found that Compiz was causing the problem. To fix it what I did was create another user account especially for Maya, and disabled all desktop effects on that account. Since then no more freezes, and the text in the UI is rendered correctly as well. Give that a go, see how it works.

---

### Post by devix91 on 2008-02-03
Thanx for the suggestions (especially for the scripts that saves your work every 5 mins.). Unfortunately I am not running any kompiz whatsoever, but my desktop effects are on medium, so that might be the problem. Thank you again. :)

---

### Post by eye208 on 2008-02-03
> **devix91 said:**
> Unfortunately I am not running any kompiz whatsoever, but my desktop effects are on medium
Desktop effects = Compiz

---

### Post by leif3d on 2008-02-07
So, did turning off effects fix the issue?
I also have a couple of questions if you guys don't mind...I'm trying to avoid windows as much as possible :)
How did you get Maya running? Did you have to convert the Redhat package to run on Ubuntu?
Also, what video card driver version are you running? did you have to do a manual install?

Thanks guys.

---

### Post by wawarren on 2008-02-07
> **leif3d said:**
> So, did turning off effects fix the issue?
I also have a couple of questions if you guys don't mind...I'm trying to avoid windows as much as possible :)
How did you get Maya running? Did you have to convert the Redhat package to run on Ubuntu?
Also, what video card driver version are you running? did you have to do a manual install?

Thanks guys.

search this forum for "install maya" and you'll find a guide written for Maya 7.0.  It's been updated for all versions of Maya so it should cover everything.  

Use alien to convert your rpm, and use Envy with the latest drivers.  

xorg.conf requires Option "CIOverlay" "on" in your video card device section,  and you also must disable Composite. 

Like most high-end software, Maya includes it's own libraries, so make sure it's using them instead of your own in /usr/lib.  You can set LD_LIBRARY_PATH in the maya.env file, or you can export it from /etc/profile.  Maya's lib's are in /usr/autodesk/maya8.5-64/lib

---

### Post by Arijan on 2008-02-16
I'm using Maya on ubuntu for a long time and, by the way, I never had to install it in proper way with all redundant things : I copy aw folder from an archive into the /usr and in /var/flexlm I copy aw.dat which I generated since Maya 6.0. Never had any problems running it like that. Most important is not to use any apps which provide desktop effects. I once tried to run Maya with beryl and it was all black interface without menus. Also when I tried to run Houdini under the same conditions, it just forgot the installed licenses along with the popup warning: graphic card is not set up properly.  Anyway, there is one little bug I'm experiencing under Maya 2008 and that's due to still bad fglrx drivers for ATI: once when right click is pressed cursor changes into an ugly black cross and it stays like that until some other app is lunched, but again, each time right click pressed, it comes again (uncomfortable for the visual sensitive ones).
The other issue I remember now from previous Maya 8.0 on my old  pc with nvidia and proper drivers(no effects), was hotbox: if I press space quickly couple of times, it's not ubuntu that crashes - it's x server that encounter error and the result is frozen desktop.  So at that time I just kept  my space button easy...
All this is like on lottery. For some it'll work, for some not.(for instance I have shake installed on my notebook (ati card) and it has totally smudged menus and node editor - impossible to work! But it worked on my old pc (nvidia) perfectly. With Maya, it's straight opposite)

Take it easy, and patience my friends.

---

### Post by devix91 on 2008-02-16
> **eye208 said:**
> Desktop effects = Compiz

Oh, erm.... thanx it would work now, but unfortunately i tried upgrading my Nvidia Driver, i nstalled it in "init 1" everything was fine but then when i tried actualy running it it now alsways goes to low-graphics mode. Also everytime that i go to the restricted modules manager and turn NVIDIA one ON, it turns itself off once the pc restarts. Any suggestions ?

---

