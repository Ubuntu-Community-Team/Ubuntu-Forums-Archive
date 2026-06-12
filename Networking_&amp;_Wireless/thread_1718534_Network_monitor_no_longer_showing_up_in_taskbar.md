---
title: "Network monitor no longer showing up in taskbar"
date: 2011-03-31
forum: Networking &amp; Wireless
---

### Post by vopilif on 2011-03-31
My network monitor seems to have disappeared from the taskbar.

I tried right clicking and "Add Pannel" however I do not see "Network Monitor" in the list.

I tried running 

```
nm-applet --sm-disable
```

But this gave me the error
I figure this because it's already running so I tried to killall and try it again
This time I get

```
** Message: applet now removed from the notification area
** Message: applet now embedded in the notification area
** (nm-apoplet:4498): old state indicates that this was not a disconnect 0
```

I see a 1-2 pixel sliver of something appear briefly in my taskbar and then it disappears, I assume this was the network monitor attempting to appear and then going away.

I can't paste the output if "ifconfig" here since I would have to type it all out, but it looks like wlan0 is up.

wlan0 also shows up under "iwconfig"

I'm stumped and searching has turned up threads where the above was the solution. The only thing I did that I can imagine was related to this is I recently installed tshark (curses-based version of wireshark)

---

### Post by vopilif on 2011-04-04
bump

---

