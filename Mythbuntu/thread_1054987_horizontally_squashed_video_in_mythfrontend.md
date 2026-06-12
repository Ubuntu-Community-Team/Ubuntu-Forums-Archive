---
title: "horizontally squashed video in mythfrontend"
date: 2009-01-30
forum: Mythbuntu
---

### Post by alderion on 2009-01-30
not sure if this is the correct forum as i'm not running mythbuntu but mythfrontend install on ubuntu so if it isn't, let me know and i'll post somewhere else.  thanks.

i installed ubuntu-mythtv-frontend on a vanilla hardy box.  whenever i start mythfrontend and play a recording, it is about an inch wide in the middle of the screen.  the height seems to be ok.  can someone help me out and tell me what i need to change in order to get full screen video?

if it matters, my video card is:

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)

i didn't do any configuration aside from the package installation and to point at my backend.

thanks,

-peter

---

### Post by liquidhot on 2009-01-30
In your frontend go to util/setup > setup > appearance and then on the third page at the top there is a checkbox labeled: Separate video modes for GUI and TV playback. Is that checked? If it is, that could be causing your problem. If you want it to be enabled, then it could be you have the settings here wrong.

Also, since you have an Intel graphics card, it could be OpenGL causing problems for you. On the first page of the same screen try changing your rendering engine to qt.

Are you using PC monitor when connecting to the video card? What resolution are you running in?

---

### Post by alderion on 2009-01-30
thanks for the help.  the checkbox you mention is unchecked.  also, the paint engine on the first screen is already qt.

this is actually on a laptop with an lcd that'll do 1280x800 and that is what i have my resolution set to.

any other ideas?

-peter

---

### Post by liquidhot on 2009-01-30
Another menu setting you could try looking at is under Setup/Util>Setup>TV Settings>Playback, on the 2nd page there are values you can input to adjust the scaling and displacement. Also, video aspect override and zoom.. You can try playing with those.

When you're in the watch tv mode, hit M and you will get a menu that should have options for manual zoom mode and similar settings. These do the same as in the menu above, but they're not permanent.

---

### Post by alderion on 2009-02-03
finally found the answer to my question.  it turns out that fixing another problem of mine (huge fonts on the login screen) fixed this as well.  the solution is to add the following to the "device" section of /etc/X11/xorg.conf:

Option "DDC" "No"

thanks to everyone who tried to help.

-peter

---

### Post by liquidhot on 2009-02-03
Cool, thanks for posting your solution.

---

