---
title: "frontend restart script"
date: 2011-07-07
forum: Mythbuntu
---

### Post by BloodyIron on 2011-07-07
Okay, how do I disable the frontend restart script? I tried searching for it and couldnt find anything about it.

---

### Post by ktmom on 2011-07-07
I think it's these lines in /usr/share/mythtv/mythfrontend.sh

```
            until /usr/bin/mythfrontend.real --logfile "${MYTHFELOG}" ${MYTHFRONTEND_OPTS}
                  RET=$?
                  [ "$RET" = "0" -o "$RET" = "1" -o "$RET" = "254" ]
            do
                  echo "Restarting mythfrontend.real..." >> "${MYTHFELOG}"
                  notify-send -i info 'Restarting Frontend' "The front-end crashed unexpectedly (exit code $RET) and is restarting. Please wait..." 2>> "${MYTHFELOG}"
            done

```

---

### Post by Slate8 on 2011-07-07
Just tried this by commenting out the lines above and it works. However I needed to reboot for the change to take affect and the mythfrontend no longer auto-starts on boot.

This has resolved an issue I had where a restart frontend button on my remote would cause the frontend to recursively restart so thanks :)

---

