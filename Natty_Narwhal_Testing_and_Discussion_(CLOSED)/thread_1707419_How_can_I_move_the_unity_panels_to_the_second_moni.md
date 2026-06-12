---
title: "How can I move the unity panels to the second monitor?"
date: 2011-03-15
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by t.rei on 2011-03-15
Hello.

I am really wanting to give unity a fair chance. But there's something that makes it close to unusable: I can't figure out how to move the unity bars (the top one, and the launchers) to my second monitor. Without doing that fullscreen applications, which I like to run on the larger screen, keep me from seeing my clock, my launchers, my notifications.

In classic gnome environment, that was as easy as "alt+dragging" the panel to the screen I want it on.

I'd be gratefull for any hints. :)

---

### Post by ELD on 2011-03-15
You can set either monitor to be the main one on the monitor settings and the panel that goes to that monitor, if that helps at all. You can't move them otherwise though.

---

### Post by cariboo on 2011-03-15
As has been stated elsewhere in the subforum, the dual-monitor problem is being worked on.

---

### Post by t.rei on 2011-03-15
Thanks for the answers. I tried switching the "make this screen the default ..." setting in nvidia-settings around. Here is what seems to work:

turn on second screen -> hit the make this screen default checkbox for second screen -> apply -> cancel -> go to first screen -> now mark hits on as default -> apply again -> panel moves to second screen.

yeah... a bit weird, to say the least.

Good to hear this is getting worked on - there is still sooo much changing, and so much needing change. I'm seriously impressed at the progress.

---

### Post by The Yump on 2011-04-09
```
xrandr
```  to get a list of your video outputs, then:  ```
xrandr --output $monitor_you_want_from_previous_step --primary
```

---

### Post by Roasted on 2011-04-16
> **t.rei said:**
> Thanks for the answers. I tried switching the "make this screen the default ..." setting in nvidia-settings around. Here is what seems to work:

turn on second screen -> hit the make this screen default checkbox for second screen -> apply -> cancel -> go to first screen -> now mark hits on as default -> apply again -> panel moves to second screen.

yeah... a bit weird, to say the least.

Good to hear this is getting worked on - there is still sooo much changing, and so much needing change. I'm seriously impressed at the progress.

This did not work for me.

I hope it gets worked on and fixed. It's ironic that the idea behind Unity is to utilize horizontal space for ease of use. But the fact is, with me having two widescreen monitors with my right monitor being my main, it is a TOTAL pain in the *** to have to swing my mouse over across both monitors to do my thing. Having the unity bar on the left side of the main monitor (in the area in between the two monitors) would be completely ideal...

I'll hang on to hope for it to change. If not, it's Linux - there's endless alternatives. :)

---

### Post by Roasted on 2011-04-23
Any update on this? I'm curious if it'll be available during its initial release.

---

