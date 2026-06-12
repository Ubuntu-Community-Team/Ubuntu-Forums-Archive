---
title: "DSL/pppoe connection script fails"
date: 2010-04-18
forum: Networking &amp; Wireless
---

### Post by kuldeepsidhu on 2010-04-18
i have setup my connection with pppoeconf command ...
i had not started it at boot time..
i make a script like this....

```
[B]#!/bin/bash
echo "Connecting"
$(sudo pon dsl-provider)[/B]
```

but this doesnot work..it gives the error...
```
Connecting
./Connect.sh: line 3: Plugin: command not found
```

where is the problem..?
when i simple try the command sudo pon dsl-provider it works....

---

### Post by Iowan on 2010-04-18
Moved to it's own thread.
You can try the script mentioned:
[http://ubuntuforums.org/showthread.php?t=862992]("http://ubuntuforums.org/showthread.php?t=862992")
(No word whether it worked)

---

