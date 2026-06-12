---
title: "Sound problem"
date: 2007-08-02
forum: Multimedia &amp; Video
---

### Post by Gobinu on 2007-08-02
Hello, i am writting this post becouse i've got problem with sound on my computer.My sound card is integrated (AC'97). Films and music works fine but any kind of system sounds or for exemple youtube films  
sounds horrible. I can general hear it but it skreech (is this good word?). I have found a solutin once but i am forced to reinstal ubuntu and i cant find it now, so i am asking you for help.
Thank you in advence.

---

### Post by AlexenderReez on 2007-08-04
hm...i suggest you to post question in absolute beginner place as there are many people over that are waiting for question :) ...ok then....hm...firstly....edit menu -->(right click on menu)---> go to sound and video then enable volume control ....make sure you have enable all sound in that volume control....if it still doesn't work...have a look to this threat :)

-->


> [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by Battal on 2007-08-04
Hi, I had a similar problem where sound was fine when playing music but unbearable when playing some games. Changing the contents of .asoundrc file in home directory to this:

```
pcm.!default {
	type hw
	card 0
	}

	ctl.!default {
	type hw           
	card 0
        }

```

fixed the problem for me to a good extent, still not perfect but much better. I have the same sound card so I thought it might help. good luck!

---

