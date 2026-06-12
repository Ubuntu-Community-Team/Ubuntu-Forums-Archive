---
title: "need help booting back to Ubuntu from XBMC"
date: 2009-10-08
forum: Multimedia Software
---

### Post by ritche on 2009-10-08
hi, 

does anyone know how I can boot myself back to Ubuntu? I installed XBMC and it installs and loads fine. I followed these instructions in how to boot straight to XBMC by changing the windows login default. Now it goes to XBMC and I cannot find a way to boot to Ubuntu. 

I'm a newbie, so please be forgiving! there has to be some keystroke? 

any help would be much appreciated?

thanks!

---

### Post by Statecowboy on 2010-05-24
Hi guys, I'm having the exact same problem and have been scouring the forums for an answer.  I'm sure it's easier than I'm making it, but dont seem to be getting anywhere.
 
I've seen a couple of threads regarding similar issues where you need to open up a terminal in XBMC and edit the config file for startup, at least that's as far as I've gotten.  I am brand new to Linux, but really dig Ubuntu so far.

---

### Post by roundhay on 2010-05-24
> **ritche said:**
> hi, 

does anyone know how I can boot myself back to Ubuntu? I installed XBMC and it installs and loads fine. I followed these instructions in how to boot straight to XBMC by changing the windows login default. Now it goes to XBMC and I cannot find a way to boot to Ubuntu. 

I'm a newbie, so please be forgiving! there has to be some keystroke? 

any help would be much appreciated?

thanks!

What instructions did you follow? There is no link here

Did you install xbmc on top of a normal Ubuntu installation or did you follow one of the guides that recommends installing xbmc on a minimal Ubuntu install (Ubuntu server)?

---

### Post by kelvin spratt on 2010-05-24
A lot of the tutorials are not very practical I presume you used the minimal cd and installed XBMC with no login manager.
You should be able to log out of XBMC and drop back and manually login.

---

### Post by Statecowboy on 2010-05-24
> **kelvin spratt said:**
> A lot of the tutorials are not very practical I presume you used the minimal cd and installed XBMC with no login manager.
You should be able to log out of XBMC and drop back and manually login.
 
This is the tut. I followed:
[http://wiki.xbmc.org/index.php?title=HOW-TO_install_XBMC_for_Linux_on_Ubuntu,_a_Step-by-Step_Guide](http://wiki.xbmc.org/index.php?title=HOW-TO_install_XBMC_for_Linux_on_Ubuntu,_a_Step-by-Step_Guide)
 
Specifically, this part is what got me into this situation:
 
**Autostart XBMC (optional)**
 

By following these instructions, your system will boot directly into XBMC rather than your desktop from now on. **It is advised that you delay this step until XBMC is setup as you'd like it.** 
[LIST]
[*]From the desktop click System -> Administration -> Login Window
[*]From the "Security" tab choose "Enable Automatic Login" and select your username.
[*]Click "OK" to exit.
[*]Logout of your system.
[*]From the Login screen choose "Select Session"
[*]Choose "XBMC" and click "Change Session"
[/LIST]You're finished. Next time you login you should be greeted with XBMC. 
------------------------------------------------------------------------------------
This works like advertised, but I can't figure out how to get back into my X screen (gnome). If I try to quit xbmc, it goes back to ubuntu log in screen and autostarts xbmc again.

---

### Post by farbird on 2010-05-25
sudo rm /usr/share/xsessions/XBMC*

---

### Post by roundhay on 2010-05-25
> Autostart XBMC (optional)


By following these instructions, your system will boot directly into XBMC rather than your desktop from now on. It is advised that you delay this step until XBMC is setup as you'd like it.

    * From the desktop click System -> Administration -> Login Window
    * From the "Security" tab choose "Enable Automatic Login" and select your username.
    * Click "OK" to exit.
    * Logout of your system.
    * From the Login screen choose "Select Session"
    * Choose "XBMC" and click "Change Session"

You're finished. Next time you login you should be greeted with XBMC. 

If you have followed these instructions you should be able to get back to a gnome desktop but doing the following.

1. choose to exit xbmc, this should drop you back to the login window
2. click on your user name, other options should now appear somewhere on the login screen (depending on the version of ubuntu you are using)
3. Look for the option 'Session' this should say xbmc, click on this and choose GNOME, then login in as normal and you should get the normal desktop

---

### Post by Statecowboy on 2010-05-25
> **farbird said:**
> sudo rm /usr/share/xsessions/XBMC*
 
Perfect!  Thanks man.  
 
Roundhay, I see what you're talking about now also, looks like that may be a good way to be able to choose whether or not to launch XBMC from the log in screen.  
 
Thanks guys, very much appreciated.

---

### Post by johngerardi on 2010-08-21
> **farbird said:**
> sudo rm /usr/share/xsessions/XBMC*
 
I used this solution to the same problem of recovering the desktop after Autostarting to XBMC and it worked fine. Now I can't figure out how to Autostart XBMC again since it is no longer an option in the Login Screen dialog. I am using Ubuntu 10.4 and I thought I might use Roundhay's solution in reverse, but when I log in there is no Session option. How can I restore the usr/share/xsessions/XBMC* information so I can Autostart XBMC?
 
Any help would be appreciated.

---

