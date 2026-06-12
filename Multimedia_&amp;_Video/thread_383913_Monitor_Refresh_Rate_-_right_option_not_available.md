---
title: "Monitor Refresh Rate - right option not available"
date: 2007-03-13
forum: Multimedia &amp; Video
---

### Post by cosmofunk on 2007-03-13
I am looking for a solution in the forums for weeks but get nothing...

The problem: I want to configure my resolution as 1152x864@60Hz, but when I choose this resolution (in the System>Preferences>Screen Resolution menu) the only refresh rate available is 75Hz (not supported by my Samsung 794MB Monitor). If it helps, the videoboard is a Nvidia 6800XT.

Thanks for any help!

---

### Post by Dr. Nick on 2007-03-13
One way to try and fix this is by opening a terminal and typing

[B]sudo dpkg-reconfigure xserver-xorg
[/B]
[COLOR=#0000DF][COLOR=#000000]You can usually safely accept the defaults until[/COLOR][/COLOR][COLOR=#0000DF]** **[/COLOR][COLOR=#0000DF][COLOR=#000000]you come to the monitor configuration select[/COLOR][/COLOR][COLOR=#0000DF]**[COLOR=#000000] [/COLOR]**[/COLOR]**"medium"** not "simple" Doing this allows you to choose a monitor that supports your desired resolution and refresh rate, Follow the wizard to the end and then restart. That should fix it all for you.

---

