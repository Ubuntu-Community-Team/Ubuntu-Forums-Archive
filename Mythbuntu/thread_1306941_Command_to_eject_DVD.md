---
title: "Command to eject DVD?"
date: 2009-10-30
forum: Mythbuntu
---

### Post by gwagchunks on 2009-10-30
Hi

I'd like to use my eject key on my remote to open the DVD tray. When I press the eject button manually I get an error message. The only way I can do it is by using the menu from the gui and selecting eject. I'd like to create a small script to eject the drive and then map this to my remote. Any ideas please? Thanks.

P.S. How is everyone getting on with 9.10?! (I'll think I'll wait a bit before I take the plunge!)

---

### Post by kaibob on 2009-10-30
The following command acts as a toggle to open/close the cd drive. You have to change /dev/scd0 to whatever is appropriate. If you only have one drive, you may be able to omit it entirely. 

```
eject -T /dev/scd0
```

I can't help with the remote.

---

### Post by shocksafe on 2009-10-31
I just did this myself.

This is my script (though if you have more than one optical drive you will need to specify the device as kaibob showed)

~/scripts/eject    or wherever you want to put it
```

#!/bin/bash
eject

```make the above executable

make sure irexec is running at boot and then add the following to 
~/.mythtv/lircrc      or wherever your wanting to put irexec's lircrc file
```

begin
 remote = your mote
 prog = irexec
 button = some eject button
 config = path to your script
end

```

---

### Post by gwagchunks on 2009-10-31
Thanks Kaibob and Shocksafe! Exactly what I was after. Cheers!:D

---

