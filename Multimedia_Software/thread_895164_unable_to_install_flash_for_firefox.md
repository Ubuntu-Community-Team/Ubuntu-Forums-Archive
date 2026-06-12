---
title: "unable to install flash for firefox"
date: 2008-08-19
forum: Multimedia Software
---

### Post by boyceb on 2008-08-19
Well- I just fired ubuntu (7.10) up and it recognized all my hardware- was on the internet immediately- never will i return to windowz.  However- there are some issues to work out: 
loading up a sight like say, youtube, i get the message "hello you either have java turned off or you dont have the latest flash" 
and so i click on the link, i download the installer, i choose "run in terminal" and am told that the instillation was a success. I return to youtube but it still says the above.  
Then I read somewhere that the browser should be closed.  I repeat process with browser closed. No dice. 
Than I read that one should go to System -> Administration -> Software Sources and enable all your repositories (i.e. main, universe, multiverse, restricted) and then try again to install.  
I did that and tried another couple of times with firefox both open and closed.  
No dice again...  so- now I'm wondering what the next thing I should try might be. . .  

thanks!

---

### Post by aysiu on 2008-08-19
Install of downloading the file from Adobe's website, try [this](http://www.psychocats.net/ubuntu/flash).

---

### Post by Nob on 2008-08-20
I have similar problem on Ubuntu 8.04. I installed flash,but on sites like youtube, video freezes after 2 sec, and there is no sound. Thing is, video clip continues to load, but image stays frozen.

How to solve this?

---

### Post by gandaran on 2008-08-20
> **boyceb said:**
> Well- I just fired ubuntu (7.10) up and it recognized all my hardware- was on the internet immediately- never will i return to windowz.  However- there are some issues to work out: 
loading up a sight like say, youtube, i get the message "hello you either have java turned off or you dont have the latest flash" 
and so i click on the link, i download the installer, i choose "run in terminal" and am told that the instillation was a success. I return to youtube but it still says the above.  
Then I read somewhere that the browser should be closed.  I repeat process with browser closed. No dice. 
Than I read that one should go to System -> Administration -> Software Sources and enable all your repositories (i.e. main, universe, multiverse, restricted) and then try again to install.  
I did that and tried another couple of times with firefox both open and closed.  
No dice again...  so- now I'm wondering what the next thing I should try might be. . .  

thanks!

your problem with flash is due to a broken flash package in synaptic, (only happens in ubuntu 7.10) to correct this, open your synaptic package manager,  scroll down to **flashplugin-nonfree** and mark for complete removal (choosing remove only, you'll be reinstalling the same broken package later) and click the apply button, next update synaptic by clicking the reload/refresh button, now you can reinstall the updated flashplugin-nonfree package, that's all.

if you followed aysiu's instructions in installing flash then just remove the broken flashplugin-nonfree package, it's no use having a broken package installed.

---

