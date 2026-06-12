---
title: "Remote connection keyboard &amp; mouse problems after certain actions."
date: 2013-06-01
forum: Networking &amp; Wireless
---

### Post by impalerau on 2013-06-01
I have several machines running Xubuntu 12.04.  They all have dual (logical) keyboards; US (default) and Russian phonetic.  One of the macines is used as a file server.  It has no keyboard, mouse or screen.  I connect to it from any of the other machines using Remmina.

When accessing the file server, I expeience the following problems after switching to the Russian phonetic keyboard OR pressing ENTER on the Password Authentication dialogue (starting Synaptic):


[LIST=1]
[*]ENTER key is not recognised in Password Authentication and other dialogue windows (eg. delete confirmation, search in Synaptic etc.).  I have to click on OK. 
[*]Pressing ENTER or double-clickiing on a folder in file manager opens the folder in a new tab instead of the current tab.  My default is set to open in current tab.  Right-click/open works correctly. 
[*]Most annoying of all is the behaviour in list windows, be it file manager, Synapric or anywhere else.  If I click on a line and then another line, instead of highlighting just the second line, all lines from the first to the second are highlighted as if I had pressed SHIFT+Left Click.  The same thing happens if I Ctrl+Left Click on the second line. 
[*]Up/Down arrows cause the line above or below to be either highlighted or unhighlighted depending on whether travelling away or towards the originally highlihted line. 
[*]The same selection behaviour occurs when editing text in gedit or leafpad and is extended to Left/Right arrow keys.  Makes editting configuration files very difficult. 
[*]Up/Down arrows do nothing in terminal emulator. 
[*]Left/Right arrows type "D" and "C" respectively in terminal emulator. 
[/LIST]

This behaviour continues even if I switch back to the default US layout.  I have tried both with and without the the Russian phonetic keyboard installed on the file server, rebooting each time.  It makes no difference.  The only way I hagve found to fix it is to reboot the file server and not switch to the Russian keyboard, and remember not to press ENTER on the Pasword Authentication dialogue.  Problem is, I need to type in Russian on the server at times (and I'm in the habit of hitting ENTER after typing my password).

There may be other actions that cause the problem but the 2 mentioned are the only ones I have noticed and can confirm for sure. 

Has anyone else experienced this?  Does anyone have a solution?

---

### Post by impalerau on 2013-06-02
Bump.  Am I really the only one in the whole world who has ever had this problem or have I posted in the wrong forum?

---

