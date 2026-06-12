---
title: "Pandora integration with Ubuntu"
date: 2013-09-30
forum: Multimedia Software
---

### Post by filip-rychnovsky on 2013-09-30
I want to announce [B]Pandora integration with Ubuntu v0.1
[/B]It display Rhytmbox style notification about curently played song on [pandora.com]("http://pandora.com").
It has two parts:
[B]Broswer:
[/B]Script for TamperMonkey or greasemonkey:[http://userscripts.org/scripts/show/178920](http://userscripts.org/scripts/show/178920)
Tested Broswers: Chrome, Firefox
[B]Bash part:
[/B]```

#!/bin/bash
O=""
while true
do
    A=$(wmctrl -l | grep "+")
    if [[ -n $A ]]; then
        if [[ $A != $O ]]; then
            B=${A:18}
            TITLE=$(echo $B | cut -d'!' -f1)
            BODY="on "$(echo $B | cut -d'!' -f3)" by "$(echo $B | cut -d'!' -f2);
            wget -q $(echo $B | cut -d'!' -f4 | sed -e 's/\(\ -\ Google Chrome\)*$//g') -O /tmp/pandora.jpg
            notify-send "$TITLE" "$BODY" -i /tmp/pandora.jpg
            O=$A
        fi
    else
        echo "No active tab with Pandora found"
    fi
sleep 5;
done

```

[B]Known limititions:
[/B]Tab with pandora must be active, window dont have to be. (I didnt find way to access other chrome/firefox tabs from bash)
Not very nice title on pandora tab. (I didnt find another way to transfer data betveen js and bash or access pages in chrome/firefox with bash)

---

### Post by mörgæs on 2013-09-30
Thanks for the news, please mark the thread 'solved' using Thread Tools.

---

