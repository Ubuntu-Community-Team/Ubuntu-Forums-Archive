---
title: "Compiz with Full screen applications causes choppy video"
date: 2011-04-15
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by defconoii on 2011-04-15
When running FPS games like openarena or quakelive with compositing enabled, you get choppy video playback because of the compositing overlay, previously  metacity --replace then compiz --replace remedied the issue but since unity relies on compiz to run, it seems its impossible to temporarily disable compiz.  Anyone know of a good way to temporarily disable compiz on start of a game then re-enable it after?  alt shift F12 used to toggle compositing in the past, it seems as if its disabled now since compiz is required for unity to run.

---

### Post by ajgreeny on 2011-04-15
Use a shell script to start the game
```
#!/bin/bash
metacity --replace && game-command && compiz --replace
``` will do it, I think, though I have no experience of the unity desktop except in 10.10 UNE which was quickly replaced as unusable, in my opinion, and therefore don't know if you mean that the ```
metacity --replace
``` command is not possible any more.

---

### Post by cariboo on 2011-04-15
Log into the Classic desktop with no affects?

---

