---
title: "Have to leave terminals open on both machines for ssh tunne"
date: 2009-08-18
forum: Networking &amp; Wireless
---

### Post by manwithaplan on 2009-08-18
My problem is I'm trying to automate the my ssh reverse tunnels.

Currently I have to do this...

ROAMING NOTEBOOK -> ROUTER -> INTERNET -> ROUTER -> HOME-MACHINE


**First I run this on the notebook:**

```

#!/bin/bash
sleep 5
ssh mymachine.***.** -l username -R 25000:127.0.0.1:22 -X -Y >/dev/null

```

It opens a flashing terminal to my home machine with auto pass keys...

[B]
Then I have to run this command on my home machine to open the reverse tunnel:[/B]
```

ssh 127.0.0.1 -p 25000 -l username -X

```

This all works fine.... but...

I'd like to connect to the roaming notebook with this reverse tunnel from my home machine, so I need to run the tunnel script on the notebook at start up. 

I can successfully achieve all of this ... its just I need to automate the notebook side. The notebook OS is Juanty 9.04. So I have tried running the notebook script with the startup preferences, but it neither opens a terminal, or even the ssh tunnel. I have public keys, so password prompts aren't a problem.

My bash is novice at best, below average... and my experience is mostly with openrc and baselayout in Gentoo.

Also if my home machine isn't on, I'd like the script on the notebook to exit, if host isn't available.

Need some suggestions and maybe some sample code. I'm familiar with loops, and case statements... etc Just need idea's where to start on the notebook side.

EDIT: I dont always have to keep my terminal open on my home machine ... Its with the notebook. Tunnel only stays open if I leave the terminal open, with the above script.

---

