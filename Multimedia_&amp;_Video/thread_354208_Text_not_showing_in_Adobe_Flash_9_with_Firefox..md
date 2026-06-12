---
title: "Text not showing in Adobe Flash 9
 with Firefox."
date: 2007-02-05
forum: Multimedia &amp; Video
---

### Post by Jasonmrc on 2007-02-05
Hello, I recently downloaded and installed (or atleast followed the installation instructions) and when I start up firefox and go to a page with flash on it then the text shows up, but once I close the browser and reopen it the text won't show untill I go through the installation process again.

When installing it I saw that a command line was not found:

```

    /root/Desktop/install_flash_player_9_linux/flashplayer-installer: line 155: strings: _command not found_
    /root/Desktop/install_flash_player_9_linux/flashplayer-installer: line 161: [: `)' expected, found 9
    /root/Desktop/install_flash_player_9_linux/flashplayer-installer: line 163: [: `)' expected, found 9
    /root/Desktop/install_flash_player_9_linux/flashplayer-installer: line 165: [: `)' expected, found 9
```

Heres what line 155 is in the installer:
```

  MYFPVERSIONSTR=`strings "$1" | grep -e "^Shockwave Flash [.\d+]*" | sed -e "s/Shockwave Flash //g"`
```


Any idea whats wrong and how to fix it?

P.S. I tried the adobe flash support forums but didn't get any answers.

---

### Post by RobotJox on 2007-03-09
I have this problem too - anyone got any ideas??:confused:

---

