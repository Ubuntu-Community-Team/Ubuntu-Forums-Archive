---
title: "mythfrontend options bug in mythbuntu?"
date: 2008-09-03
forum: Mythbuntu
---

### Post by newlinux on 2008-09-03
In attempt to figure out why livetv and recording playback keep becoming nonresponsive to both the keyboard and remote (but not when using the internal player on mythvideo files - see my thread if you have any ideas, please! [http://ubuntuforums.org/showthread.php?t=885337](http://ubuntuforums.org/showthread.php?t=885337)) I wanted to turn up the verbosity by default when I run mythfrontend from the menu and using the --service option. So I tried to modify /etc/mythtv/session-settings
to make
```

MYTHFRONTEND_OPTS="--verbose osd,idle,playback"

```

But that never changed the logging verbosity level when running mythfrontend with the --service option. In fact it gave an invalid option error with the exact arguments specified in MYTHFRONTEND_OPTS.

 So looked into /usr/bin/mythfrontend.

I had to change:
```
exec mythfrontend --logfile "${MYTHFELOG}" "${MYTHFRONTEND_OPTS}"

```

to

```
exec mythfrontend --logfile "${MYTHFELOG}" ${MYTHFRONTEND_OPTS}

```

(Removed the quotes from around the last argument). My Bourne shell scripting skills are long past their prime... so I don't know if there was something else I should have done, but this worked for me.

---

