---
title: "error in gutsy dvico mce remote lircrc file"
date: 2007-11-24
forum: Mythbuntu
---

### Post by silentmic on 2007-11-24
I found that with the dvico mce remote in MythBuntu Gutsy, the pause would not work in mythtv. Hitting the play/pause button would just display "play" as though I was pressing the play button. I checked the lircrc file and found that the following section appeared twice for the DVICO_MCE with a prog of mythtv:

begin
    remote = DVICO_MCE
    prog = mythtv
    button = playpause
    config = P
    repeat = 0
    delay = 0
end

Removing one of them and rebooting fixed the problem. Obviously the P key was sent twice because there were two entries, meaning that it was quickly pausing then playing again.

---

### Post by foxbuntu on 2007-11-26
Please file a bug for this so we can track it better. We are working on better remote support. Thanks for reporting this issue.

[https://bugs.launchpad.net/mythbuntu](https://bugs.launchpad.net/mythbuntu)

---

