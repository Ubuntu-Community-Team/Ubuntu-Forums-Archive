---
title: "DSL connection"
date: 2010-08-23
forum: Networking &amp; Wireless
---

### Post by shamsuddin on 2010-08-23
I installed ubuntu 9.10 desktop edition. But I can not access  DSL. What to do? pls help me...................

---

### Post by julio_cortez on 2010-08-23
Usually to [COLOR=Gray]*[s]trigger[/s]*[/COLOR] configure my DSL ***the first time I access Ubuntu*** I fire up a terminal and do a **sudo pppoeconf**.
Then I can choose the MTU, username and password (if any is required), whether to trigger the DSL connection at startup or not.
If you decide to trigger the connection at startup, anytime you start Ubuntu you'll be already ready to go.
*Otherwise you should issue a **pon dsl-provider** (not really sure about the syntax as I trigger it at startup automatically) command when you start Ubuntu to be able to start your DSL.*

Does it work for you?

---

