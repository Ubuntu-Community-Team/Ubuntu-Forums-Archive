---
title: "Need help on Mediacoder"
date: 2009-02-10
forum: Multimedia Software
---

### Post by vshankar on 2009-02-10
hi all
Am a newbie in ubuntu.I read out in the previous threads that mediacoder can be installed on wine.I installed the procedure went well,but now the application has failed to start.the window opens n closes immediately.......!!!:(
plzzzz help guys........

---

### Post by whaevr on 2009-02-10
Try starting the program through the terminal and see what wine is...whining about. hah...:-|

I'm assuming wine made a shortcut on your desktop. Right click on it go into properties and copy the command into terminal and post whats is happening.

---

### Post by vshankar on 2009-02-11
thx for the reply but am getting this error i dont have any idea what it is saying....so thought of showing.

$ env WINEPREFIX="/home/vshankar/.wine" wine "Z:\media\sda5\Wine_installers\MediaCoder\mediacoder.exe" 
I/O warning : failed to load external entity "prefs.xml"
fixme:win:SetLayeredWindowAttributes (0x1005a,0x00000000,0,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1005a,0x00000000,15,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1005a,0x00000000,35,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1005a,0x00000000,55,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1005a,0x00000000,75,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1005a,0x00000000,95,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1005a,0x00000000,115,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1005a,0x00000000,135,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1005a,0x00000000,155,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1005a,0x00000000,175,2): stub!
I/O warning : failed to load external entity "rss.xml"
err:ole:CoGetClassObject class {304ce942-6e39-40d8-943a-b913c40c9cd4} not registered
err:ole:CoGetClassObject no class object {304ce942-6e39-40d8-943a-b913c40c9cd4} could be created for context 0x1
fixme:win:SetLayeredWindowAttributes (0x1005a,0x00000000,195,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1005a,0x00000000,215,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1005a,0x00000000,235,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1005a,0x00000000,255,2): stub!
err:winebrowser:get_url_from_dde Unabled to retrieve URL from string L"\""
err:winebrowser:wmain Usage: winebrowser URL
I/O warning : failed to load external entity "filelist.xml"
fixme:win:SetLayeredWindowAttributes (0x1005a,0x00000000,255,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1005a,0x00000000,235,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1005a,0x00000000,215,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1005a,0x00000000,195,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1005a,0x00000000,175,2): stub!
fixme:win:SetLayeredWindowAt env WINEPREFIX="/home/vshankar/.wine" wine "Z:\media\sda5\Wine_installers\MediaCoder\mediacoder.exe" 
I/O warning : failed to load external entity "prefs.xml"
fixme:win:SetLayeredWindowAttributes (0x1005a,0x00000000,0,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1005a,0x00000000,15,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1005a,0x00000000,35,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1005a,0x00000000,55,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1005a,0x00000000,75,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1005a,0x00000000,95,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1005a,0x00000000,115,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1005a,0x00000000,135,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1005a,0x00000000,155,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1005a,0x00000000,175,2): stub!
I/O warning : failed to load external entity "rss.xml"
err:ole:CoGetClassObject class {304ce942-6e39-40d8-943a-b913c40c9cd4} not registered
err:ole:CoGetClassObject no class object {304ce942-6e39-40d8-943a-b913c40c9cd4} could be created for context 0x1
fixme:win:SetLayeredWindowAttributes (0x1005a,0x00000000,195,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1005a,0x00000000,215,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1005a,0x00000000,235,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1005a,0x00000000,255,2): stub!
err:winebrowser:get_url_from_dde Unabled to retrieve URL from string L"\""
err:winebrowser:wmain Usage: winebrowser URL
I/O warning : failed to load external entity "filelist.xml"
fixme:win:SetLayeredWindowAttributes (0x1005a,0x00000000,255,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1005a,0x00000000,235,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1005a,0x00000000,215,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1005a,0x00000000,195,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1005a,0x00000000,175,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1005a,0x00000000,155,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1005a,0x00000000,135,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1005a,0x00000000,115,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1005a,0x00000000,95,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1005a,0x00000000,75,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1005a,0x00000000,55,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1005a,0x00000000,35,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1005a,0x00000000,15,2): stub!
err:ole:CoCreateInstance apartment not initialisedtributes (0x1005a,0x00000000,155,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1005a,0x00000000,135,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1005a,0x00000000,115,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1005a,0x00000000,95,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1005a,0x00000000,75,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1005a,0x00000000,55,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1005a,0x00000000,35,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1005a,0x00000000,15,2): stub!
err:ole:CoCreateInstance apartment not initialised

---

### Post by vshankar on 2009-02-12
At last the problem is solved... thr was some httpd error,this mediacoder needs httpd to run.I donno y these ppl have not come up with a linux version.

---

