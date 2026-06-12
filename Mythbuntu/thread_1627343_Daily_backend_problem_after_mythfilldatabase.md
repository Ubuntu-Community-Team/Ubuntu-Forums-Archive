---
title: "Daily backend problem after mythfilldatabase"
date: 2010-11-21
forum: Mythbuntu
---

### Post by marek_online on 2010-11-21
I recently upgraded from 0.21 to 0.23-fixes (via an upgrade from Mythbuntu 8.04 to 10.10).

I'm getting strange behaviour daily, that I think is the result of the automated mythfilldatabase run overnight.

Live TV fails to run and programs don't record (though an entry is made into the database for the recordings. 
If I run Mythfrontend from the terminal, with live TV I get dozens of errors like this:

```

Error: Invalid file descriptor in 'safe_read()'
```

...and get dumped back out to the menu.

If I try to play a recording it complains that the file is empty.

Rebooting the machine fixes all of these problems.

A daily reboot isn't the end of the world, but I'd prefer if things just worked. I'm almost certain this is a permissions problem, but I don't know precisely what the problem is, or how to fix it without the reboot (resetting file ownerships and permissions on the recordings directories doesn't seem to work, but maybe it's a database permissions thing?).

If anyone has any suggestions, I'd be grateful.

M

---

