---
title: "Zalman HD135 VFD using lcdproc mplay problems"
date: 2009-02-21
forum: Mythbuntu
---

### Post by rodercot on 2009-02-21
Hey all,

 I have a question about my main machine. 

 I have the VFD running via the current CVS version of lcdproc (actually the only one that will run with mplay as the connections type) BUT my issue is this.

 when I boot up it loads the server and connects to myth as the client then mythfront end opens and I get nothing but a single line to the very left of the screen on the top row only, no date time or otherwise. When the opening myth and the frontend is setting itself up to display I see the that with the progress bar as soon as myth is open it goes back to just the single bar on the left. no errors when I restart LCDd at all. 

 If I open up live tv I do get channel info - show info - and a solid bar across the bottom row. 

 It also kills my remote when I start to watch live tv and then if I issue an LCDd stop from ssh my liveTV becomes very garbled and completely useless.

 Any Thoughts. This case has the VFD hd44780 using the mplay driver I have installed and removed most of the lcdproc version I can find and have tried with the lis2 connection type as well as that is a complete no go. This was working perfectly in XBMC as client. 
 but I have switched now to loading XBMC as an app from the myth frontend instead.


 Thanks,

 Dave

---

### Post by rodercot on 2009-02-22
**Update** - this is now OK, I had to recompile LCDproc 0.5.2 with the CVS mplay-final.patch with patch -p0 and all is fine now and my conflicts with myth seem to go away after a reboot so I am happy and I now have the fan controller options in the LCDd.conf file that works with this VFD.

 Dave

---

