---
title: "Carbon X1 Wireless Internet Slow Ubuntu 12.10"
date: 2013-04-02
forum: Networking &amp; Wireless
---

### Post by metasoarous on 2013-04-02
> **Wild Man said:**
> Hi, please change your wireless settings to match the screenshots then reboot.

Also you have two network connections named the same thing I would remove one of them, it is probably causing the connection to jump from one to the other.
Thanks

@WildMan - I don't see the screenshots mentioned here, and have been having similar issues with my Carbon X1 Wireless on 12.10. Could you please clarify or repost the screenshots?

Thanks

Chris

---

### Post by wildmanne39 on 2013-04-02
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the netinfo.txt file.
Thanks

---

### Post by metasoarous on 2013-04-02
I was unable to upload that file (too big), so here is a dropbox link - 

[https://www.dropbox.com/s/1ccan0664to8kzo/netinfo.txt](https://www.dropbox.com/s/1ccan0664to8kzo/netinfo.txt)


Thanks for the rapid response!

---

### Post by wildmanne39 on 2013-04-02
Hi, please follow the directions in post 5 of this link.
[http://ubuntuforums.org/showthread.php?t=2131235&p=12583893#post12583893](http://ubuntuforums.org/showthread.php?t=2131235&p=12583893#post12583893)
Thanks

---

### Post by metasoarous on 2013-04-03
Awesome, thanks. Will have to try tomorrow as I'm working remotely today.

---

### Post by metasoarous on 2013-04-04
Okay, rebooted this morning after making those modifications and still no improvement.

---

### Post by wildmanne39 on 2013-04-04
Did you also go to this link and do what is in post 13?
[http://ubuntuforums.org/showthread.php?t=2079078&page=2](http://ubuntuforums.org/showthread.php?t=2079078&page=2)
Thanks

---

### Post by metasoarous on 2013-04-04
Yup, I did do that (well, modulo a gedit  -> vim substitution :-) )

So, to add a bit of detail here, the speed is not what I was expecting. However, as of yet the wild ping fluctuations correlated with my ssh tunnelling responsiveness have been much reduced so far. I actually tried a similar fix to the post 13 modification you posted about above (as suggested for a problem with another card at [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1011623](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1011623)), though without the `bt_coex_active=N`. It seemed to help things for a short while, but didn't last. I'll continue monitoring the behaviour and report back. I'll be largely happy if my ssh tunnel remains snappy enough to get work done, though it would be nice if I was able to take full advantage of the internet speed here.

In the meantime, if there are any other suggestions you might have for me, they would be greatly appreciated.


Thanks

---

### Post by metasoarous on 2013-04-04
Bummer... the sluggishness is back. That didn't take long. Wondering if it was just the reset than temporarily clears things up.

Any thoughts or suggestions?

Greatly indebted,
Chris

---

### Post by wildmanne39 on 2013-04-05
Change your wireless settings to match the screenshots please.

Also if you can change your router to just wpa2 AES and not enterprised that may help.
Thanks

---

### Post by metasoarous on 2013-04-08
Ya know, I thought that I had done those steps before, but looking back, I didn't set "Automatic addresses only", just the IPs. After trying that though, I couldn't ssh around (or even ping) the various servers on our network at all. And to clarify, this is a company network, so modifying router settings is not an option.

---

### Post by wildmanne39 on 2013-04-08
I did not realize you were tunneling into the computer through ssh, it probably stopped working because you changed the dns server like I asked.

Since you can not change the router settings the only other thing I can think of would be if you wanted to compile your own driver from compat, if you do you will have to recompile every time the kernel is upgraded.
Thanks

---

### Post by metasoarous on 2013-04-08
Yeah, I figured as much (regarding the DNS). Maintaining my own driver compilations doesn't sound like too much fun, but perhaps it's worth looking into.

Would you please help me conceptually understand what it is you think it going on? I just looked up compat, and understand that it is a utility for providing functionality in newer kernels to older ones, but I don't understand what specific compatability issues you think are at play in this situation. Presumably, if compat is useful in this situation, it would seem that there is some newer kernel funcitonality which is causing the issues I'm having. But why would compat be the ideal solution here, vs just waiting for an updated kernel in the next Ubuntu release? Any details which would help me understand the situation would be greatly appreciated.

Best

Chris

---

### Post by wildmanne39 on 2013-04-10
Hi, this driver has trouble with N speed and that parameter shoud have fixed that issue.
I rechecked the information that you posted and more then likely the issue is that you have several networks with the same name so network manager is continually jumping between them however you will stil need the parameters that you added earlier.

Compat drivers are just updated drivers, yes some are for older kernels but they have others that are for new kernel as well
Thanks

---

### Post by metasoarous on 2013-04-10
Okay, thanks for the explanation. I saw something to that effect on the original post I reponded to, and had a feeling that might be effecting things here as well. Unfortunately, I can't do anything about that. 

So from what you're telling me, it sounds like there is a newer driver in which this issue has been fixed. And either I can manually compile/install that driver with compat, and maintain that installation myself, or live with it until the newer version (presumably/eventually) finds it's way into my distro. Sound right? 

Would you remind me of the linux-next backports, or should linux-stable be fine?

Thanks

---

### Post by wildmanne39 on 2013-04-10
Compiling the driver could fix it but no guarantees, I really believe with others networks having the same name that it will not because it is most likely network manager switching from one network to another.

I will have to do some research and see how we can stop ir from switching.

As far as the fix being coming out in a new release of ubuntu that is not likely this issue has been around for quit awhile. 
I would try the stable first

---

