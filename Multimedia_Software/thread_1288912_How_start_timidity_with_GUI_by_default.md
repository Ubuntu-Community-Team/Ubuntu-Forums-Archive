---
title: "How start timidity with GUI by default?"
date: 2009-10-11
forum: Multimedia Software
---

### Post by michael37 on 2009-10-11
What's the simplest way to start timidity (the best and the most reliable midi player on Linux) with GUI by default?

On my computer, timidity starts in the terminal.  timidity -ig starts a proper GUI... but Nautilus/Firefox file associations have no clue how to pass a flag to the program.

---

### Post by onespeedbiker on 2009-10-12
> **michael37 said:**
> What's the simplest way to start timidity (the best and the most reliable midi player on Linux) with GUI by default?

On my computer, timidity starts in the terminal.  timidity -ig starts a proper GUI... but Nautilus/Firefox file associations have no clue how to pass a flag to the program.I'm only 2 months into ubuntu so forgive me if I don't understand. It sounds to me like your are trying to change a file association, so when you open a file it will open with timidity. If that's the case you can right click on the file and go to Properties>Open With tab. There you can choose a program or terminal command.

---

### Post by barthel on 2009-10-12
Unfortunately, I don't see anything in timidity.cfg which will let you specify a default interface.

There are a few ways to achieve what you want:
[LIST=1]
[*]`alias timidity=/usr/bin/timidity -ig` will take care of launching timidity from the shell
[*]Create an application launcher with "Exec=/usr/bin/timidity -ig"  to take care of launching timidity via Nautilus and the menu
[*]Create a shell script that launches timidity with your option and have programs call that instead.
[/LIST]

Here's a quick & dirty stab at the script:
```

#!/bin/sh

#~/bin/timidity
#    Call timidity with options that aren't covered by ~/.timidity.cfg
/usr/bin/timidity -ig

```

HTH

---

