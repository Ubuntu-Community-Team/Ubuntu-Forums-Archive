---
title: "Wildmanne39 please HELP!"
date: 2011-12-30
forum: Networking &amp; Wireless
---

### Post by optima4 on 2011-12-30
**UPDATE below**


Hey, sorry to report but in this thread here [http://ubuntuforums.org/showthread.php?t=1877120&page=7](http://ubuntuforums.org/showthread.php?t=1877120&page=7)

I ran the commands instructed to fix my wireless problem. I thought the issue was resolved, but later as I was still using my internet I began showing issues again. 

I shut down earlier today and just restarted to my desktop being in shambles!!

Please someone help. I ran these commands

```
sudo apt-get install bcmwl-kernel-source 
```     ```
echo "blacklist bcma" | sudo tee -a /etc/modprobe.d/blacklist.conf 
```     ```
echo "blacklist brcmsmac" | sudo tee -a /etc/modprobe.d/blacklist.conf 
```     ```
echo "blacklist brcm80211" | sudo tee -a /etc/modprobe.d /blacklist.conf 
```Then rebooted.

and at first it seemed to work and now I am in pretty bad shape.

What is the right command to get it straight again? Can I undo this? I haven't ran anything else since this yesterday. 


_[SIZE=2][FONT=Arial Narrow]Issues[/FONT][/SIZE]_
My screen on the left is completely squished, the graphics are flattened and bulky, the screen on the right> all the icons are piled on top of each other. I also have to keep restarting to connect to the internet if my computer was off.

-----------------------------------------------------------------------------------------------------
***EDIT***

So here is something that has changed since I have played around with "Displays".

I went from 2D Ubuntu, to regular Ubuntu, and changed the setting around with the monitors.Then I had to reorganize all my files on the desktop, then I restarted, and switched back to 2D, and everything was back to normal except now my icons are all over the place. 

So I am going to re organize them in place, but I hope I dont have to do this every time. And I apologize Wildmanne39, I know you are busy, and like myself have only so much time to do extra for others. So I am not relying on only your efforts, I was just kind of worried I was losing my compatibility on this one.

Also the screen is still a little bloated and flat looking on my 19" monitor, so that is still happening, but at least I can see right.

---

### Post by wildmanne39 on 2011-12-30
Hi, I answered you in the other thread already.

I believe that will fix your problem and you should not try to undo what we have already done with the other commands, your wireless will work better if it stays the way it is, I believe you have more then one thing going on, let me know if the suggestion in the other thread fixes it.
Thanks

---

### Post by nothingspecial on 2011-12-31
Let's keep this in the other thread.

---

