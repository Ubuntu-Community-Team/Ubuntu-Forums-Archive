---
title: "xset dpms force on no longer working"
date: 2009-04-18
forum: Mythbuntu
---

### Post by gizmobay on 2009-04-18
I just noticed that the xset dpms force on no longer works. I have a script tied to the power button that kills the frontend and blanks the screen. Once I hit the power button again the front starts and the screen comes live well it use to. I'm just using a computer monitor so I don't use the power button very often but I just tried and it failed as I'm moving my system to a flat panel. The monitor button goes green versus orange but I have to hit a button to wake the screen up.

I saw this bug posted else where.

[http://www.novell.com/support/search.do?cmd=displayKC&docType=kc&externalId=7001933&sliceId=1&docTypeID=DT_TID_1_1](http://www.novell.com/support/search.do?cmd=displayKC&docType=kc&externalId=7001933&sliceId=1&docTypeID=DT_TID_1_1)

Anyone have any ideas on how to fix?

---

### Post by gizmobay on 2009-04-19
Solved by adding xset s reset to the command after xset dpms force on.

---

### Post by Clive McCarthy on 2010-12-22
Thanks for posting that. I have been thrashing about trying to get **[COLOR="Blue"][SIZE="3"]xset dpms force on[/SIZE][/COLOR]** to actually show what is on the screen to no avail. It turns on the fluorescent tubes but the screen stays blank -- not very forceful.

Adding **[COLOR="Blue"][SIZE="3"]xset s reset[/SIZE][/COLOR]** does the trick.

From within my C code I can now get the equivalents of the WinXP controls and I can monitor the state with the scroll lock LED too.

[COLOR="Green"]// turn the display off
#ifdef WIN_XP_PORT
[INDENT]SendMessage(HWND_TOPMOST, WM_SYSCOMMAND, SC_MONITORPOWER, MONITORPOWER_OFF);[/INDENT]
#endif
#ifdef UBUNTU_PORT
[INDENT]system("xset dpms force off");	// turn the display off 
system("xset s on");			// turn the screen saver on
system("xset s activate");		// activate the screen saver
system("xset led named \"Scroll Lock\""); // turn on scroll lock LED
[/INDENT]#endif


// turn the display back on
#ifdef WIN_XP_PORT
[INDENT]SendMessage(HWND_TOPMOST, WM_SYSCOMMAND, SC_MONITORPOWER, MONITORPOWER_ON);[/INDENT]
#endif
#ifdef UBUNTU_PORT
[INDENT]system("xset dpms force on");
system("xset s reset"); // reset (deactivate) the screen saver
system("xset s off");	// turn the screen saver off
system("xset -led named \"Scroll Lock\""); // turn off scroll lock LED
[/INDENT]#endif
[/COLOR]

Thanks again.

---

