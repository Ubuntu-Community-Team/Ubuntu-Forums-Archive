---
title: "Turn your computer into a free phone with Gmail/Google Voice"
date: 2011-04-24
forum: Multimedia Software
---

### Post by patrick_the_fat on 2011-04-24
This guide helps you to integrate the calling features of Gmail/Google Voice into your operating system so that you can make/receive phone calls without first opening Gmail.  It is actually easy to set up using this tutorial, so I recommend it to any Linux user, regardless of their user experience.

All you need is a standard Linux installation, a speaker, and a microphone.

This tutorial assumes you have Compiz enabled (if not, please search Google for more info as it is beyond the scope of this article.. FYI, you can also use this guide without Compiz, but you will not have a show/hide the call window functionality by pressing F9.)

To get started, open a terminal window, then paste the following command:

sudo apt-get install screenlets screenlets-pack-all xdotool && sudo ccsm && screenlets

In Compiz Config, type 'wid', turn on Widget Layer but clicking the checkbox. Now click on the Widget Layer button, make sure Behaviour > End Widget Mode on Click is checked, then turn the brightness and saturation all the way up and the fade-in time all the way down.

Close the Compiz Config window, and when the Screenlets Manager comes up, scroll to the bottom, single-click Webframe, then click the Options button on the left and set the options to Sticky, Widget, and Keep Above.

Click OK to save the Webframe settings, then click the checkboxes next to 'Auto Start at Login' and then 'Start/Stop'.

Close the Screenlets Manager, press F9 to hide the Webframe (or you can just click on this web page if the End Widget Mode on Click setting is enabled), then pull up the following address in a new tab/window:

[http://mail.google.com/mail/?ui=html](http://mail.google.com/mail/?ui=html)

Sign in if you aren't already signed in, then copy the link that says "Standard View" at the bottom of the page to the clipboard.

Close the Gmail tab you just opened, press F9 again to show the Webframe, then right-click the border and click Properties/Options/Webframe and paste the web address you just copied into the Home page field.

Close the Properties window.  Double-check that the Sticky, Widget, and Keep Above settings applied to the current frame by right-clicking the border and moving the mouse over "Window".

Now, for the auto-login script (this part is optional, however without it you will have to enter your username and password every time you turn on your computer--good for computers where security precautions are necessary, but your computer will not ring like a telephone upon startup unless you do this every time.)

To create the startup script, return to your terminal and paste:

gedit ~/gtalk-screenlet.sh && chmod a+x ~/gtalk-screenlet.sh

Now, paste the following into the text editor and edit your username/password:

#/bin/bash
sleep 40 &&
xdotool key "F9" &&
sleep 1 &&
xdotool type "gmail-username" &&
xdotool key "Tab" &&
xdotool type "gmail-pw" &&
xdotool key "Return" &&
sleep 4 &&
xdotool type "gp" &&
sleep 6 &&
xdotool key "F9"

Save it, close it, then click System > Preferences > Startup Applications and add the command "sh ~/gtalk-screenlet.sh" with whichever name you may choose.  This is meant for very personal computers, until somebody comes up with an idea to make it more secure.. I will be brainstorming the best way to do this, and changing the directions accordingly.)

Restart your computer, and wait for the script to do its magic!  You have to give your computer a few extra seconds of boot time for the script to log you into Gmail and hide the webframe.  The Gmail frame will log itself in, pull up the dialpad, and disappear when it is done.  You should be able to press F9 and see numbers to place a call.  If your machine is not filling out the Gmail log-in information correctly, you may have to edit the startup script (you can re-run the last command to open it) and increase the "sleep 40" command to "sleep 45", or something more appropriate.

To use, just remember that F9 brings up the call window, escape typically ends a phone call, and "gp" (_g_o to _p_hone) brings up the dialpad in Gmail when it's closed (you will typically end up doing this between phone calls).  If "gp" is not working, sometimes you have to click on the background of Gmail (I think Google does this on purpose), then press "gp".

This modification allows your computer to ring like a telephone when somebody calls you, and it starts working immediately when you turn on your computer.  The Webframe screenlet is a little buggy, but you can use Page Up/Page Down to scroll, because sometimes it's more convenient to click "Call Phone" in Gmail to bring up the dialpad.  Sometimes you can also click the border to refresh the display, because it often looks funny when you try to scroll using the scrollbars.  However, all the core functionality works, and it works great!

Have fun!  Free calling with Gmail and Google Voice until 2011.  It's very useful if you need to make a lot of calls while multitasking on the computer.  I honestly haven't paid my cell phone bill in the past four months since I came up with this!  Tell me what you think, or if you have any problems during setup, please post so that I can make corrections.

---

### Post by oracle2b on 2011-04-24
Thanks for this, I'll try this later.

---

### Post by patrick_the_fat on 2011-05-06
Any results? Let's bump this thread a little bit, please!

---

