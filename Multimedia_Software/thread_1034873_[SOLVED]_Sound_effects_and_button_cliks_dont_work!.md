---
title: "[SOLVED] Sound effects and button cliks dont work!"
date: 2009-01-09
forum: Multimedia Software
---

### Post by mwillams73 on 2009-01-09
I found 1 forum post about this problem unfortunately there was no step by step instruction on how to find the fix in the synaptic pakage manager, can anyone explain to me how to get this to work? I have sound i can play music and movies with no problems at all but theres no sounds scheme sounds you know, when you clik on something and your supposed to get a noise, nothing. When intrepid boots up i get the bongo music and all that but nothing else, so what do I do? 
Please dont just post a link that doesnt explain how to do it , I tried that earlier, I even downloaded the file but couldnt figure out how to install it. I need a step by step instruction for this. I know the solution exists just not how to implement it.

---

### Post by blazemore on 2009-01-09
Go to System -> Preferences -> Sounds -> Sounds
You can select the sounds there. I'm pretty sure there aren't any by default...

---

### Post by mwillams73 on 2009-01-09
thankz for the reply but that wasnt the problem, the problem was no one was explaining how to get the libcanberra file in the repositories, Soo, I went to launchpad where they said they had the fix and asked them to explain how to do it, this was the reply and after i rebooted im happy to say it worked, By the way this is a bug fix for those who arent getting the sound effects like they are supposed to, Enjoy!!!!


  If you are on Intrepid then you need to add the repository

"deb [http://ppa.launchpad.net/gkulyk/ubuntu](http://ppa.launchpad.net/gkulyk/ubuntu) intrepid main"

by going to System > Administration > Software Sources

Third Party Software tab.

Click on Add and give the above line without the quotes

Click Close .

It will ask to reload, let it do fetch.

In the updates you will get the new canberra 0.10

---

