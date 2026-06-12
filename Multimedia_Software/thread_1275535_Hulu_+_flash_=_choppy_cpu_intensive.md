---
title: "Hulu + flash = choppy cpu intensive"
date: 2009-09-25
forum: Multimedia Software
---

### Post by homy06 on 2009-09-25
ever since adobe came out with a flash for linux i've really had no problems with watching flash videos online. That is up to a month or so ago. watching hulu now has become unbearable. I didn't change anything, and even when I upgraded to jaunty everything was fine, up until a couple of months ago. 

first it begins with the videos being cut off because by default the "show all" button isn't selected. so I have to right click, then click "show all" on every video. 

next, the videos start out ok for about 5 minutes then it begins to get a little choppy and I can hear my cpu ramp up. 10 minutes into the video it gets so choppy the video/audio goes out of sync and I hear the cpu fan constantly. The cpu usage doesn't drop below 50%. 


I tried a lot of different things, from making sure all flash non-free were not installed, to installing the medibuntu repo. nothing has worked. every other flash app works fine, just hulu is going insane. 

any help? btw, i have cable modem so I know the lag isn't from the network, i've even paused the video and let the status bar load all the way, still gives me errors.


edit:

I forgot to mention that full screen crashes the browser. I even tried switching to swiftfox. I'm using swiftfox 3.5

---

### Post by homy06 on 2009-09-25
ok so I just used google chrome and I didn't get the problem of having the videos cutoff and needing to right-click "show all" function to fix it, and I could full screen. But it is still seriously cpu intensive and choppy

---

### Post by homy06 on 2009-09-26
bump

---

### Post by martinbaselier on 2009-09-26
Have you tried running top, to see which program/process is so cpu intensive?
Do you have compiz enabled? (visual effects on desktop settings) Try disabling all visual effects.

---

### Post by homy06 on 2009-09-27
compiz is taking relatively little cpu, in the 4%-5%, while swiftfox is taking anywhere from 80 to over 120% cpu usage. This occurs once the video begins. 

I can't believe no one else is having this problem. having to click the "show all" box is odd on its own, never experienced that.

---

### Post by wojox on 2009-09-27
Open Synaptic and search for 

```
gnash
```

If installed remove it.

---

### Post by homy06 on 2009-09-27
gnash isn't installed. I definitely went through and uninstalled things I didn't need, thank you for the suggestion though. 

now even other flash videos are eating up cpu.

---

### Post by homy06 on 2009-09-29
figured it out. dusty pc. cleaned the desktop up, got rid of the dust, and it's ok now.

---

### Post by mburgoon on 2009-11-02
I was having issues with fullscreen Flash 10 in 9.10 and 9.04. I only experienced choppiness when in fullscreen, no problems with flash video when embedded in the browser.

My workaround was to use Enhanced Zoom Desktop feature in the Accessibility section of CompizConfig. Mine was mapped to the windows key and the mouse scroll wheel. This works rather well for me on sites like hulu, youtube, etc.

---

