---
title: "Shaky Wifi Connection with Xfinity Internet Ubuntu 12.0.4.1 lts"
date: 2013-02-16
forum: Networking &amp; Wireless
---

### Post by EvyBear on 2013-02-16
I just got Ubuntu Installed not too long ago, and for the first few days, Ubuntu was working fine with my internet. Now I have a shaky connection with my wifi, It goes from 4 bars to 2 bars and it'll be so slow that the webpage won't load and this happens randomly! I don't know anything about codes, I find that stuff really complicated and I don't know anything computer lingo really, Im a newbie, Im used to windows having everything for me. This shaky connection is really annoying and Im wondering if it's Ubuntu or Xfinity (Comcast Internet) because my internet worked great with windows. Help Please? :confused:[-(:-s

---

### Post by cariboo on 2013-02-16
This is just a thought, seeing as you really haven't provided any information about your system. Have you tried rebooting your router, by pulling the plug for about 10 seconds, then plugging it in again?

---

### Post by EvyBear on 2013-02-16
> **cariboo907 said:**
> This is just a thought, seeing as you really haven't provided any information about your system. Have you tried rebooting your router, by pulling the plug for about 10 seconds, then plugging it in again?
Thanks so much for replying :) and Yes, Ive called up comcast and everything. The customer service guy blamed Ubuntu, but I really don't think its the reason. What type of info do I need to provide for proper assistance? I'll take screenshots.

---

### Post by EvyBear on 2013-02-26
Hi Everyone, I am new to Ubuntu and I have problems connecting to my Xfinity Wireless Internet by Comcast.My connection is very hit and miss. 2 bars to 4 bars I've tried the disconnecting the router thing, and I'm assuming that the problem is deeper than that. I am not tech savvy so please explain step by step what I am supposed to do because I don't really understand computer vocabulary much. Here are some screenshots 
*<removed attachments showing ssid and mac address>*

---

### Post by varunendra on 2013-02-26
Duplicate threads ***merged and moved*** to correct section.
----------------------------------

@ EvyBear,
Please do not post multiple threads on same problem. Feel free to bump your thread after 24 hours if necessary.

If you think the thread is in wrong section, you can always use the "Report abuse" button *(below each poster's profile)* to request the mods/admins to move it to correct section of the forums.

I have removed your attachments for your security as they were showing your SSID and mac address, which may cause security issues.

Onto your problem -
Please follow the "Wireless Script" link in my signature and post back its result here. It will give us everything we need to know initially. We may ask for more info as and if required later.

Thanks!

---

### Post by EvyBear on 2013-02-26
> **varunendra said:**
> Duplicate threads ***merged and moved*** to correct section.
----------------------------------

@ EvyBear,
Please do not post multiple threads on same problem. Feel free to bump your thread after 24 hours if necessary.

If you think the thread is in wrong section, you can always use the "Report abuse" button *(below each poster's profile)* to request the mods/admins to move it to correct section of the forums.

I have removed your attachments for your security as they were showing your SSID and mac address, which may cause security issues.

Onto your problem -
Please follow the "Wireless Script" link in my signature and post back its result here. It will give us everything we need to know initially. We may ask for more info as and if required later.

Thanks!

Whoops! Im sorry. #-o

---

### Post by EvyBear on 2013-02-26
> **EvyBear said:**
> I just got Ubuntu Installed not too long ago, and for the first few days, Ubuntu was working fine with my internet. Now I have a shaky connection with my wifi, It goes from 4 bars to 2 bars and it'll be so slow that the webpage won't load and this happens randomly! I don't know anything about codes, I find that stuff really complicated and I don't know anything computer lingo really, Im a newbie, Im used to windows having everything for me. This shaky connection is really annoying and Im wondering if it's Ubuntu or Xfinity (Comcast Internet) because my internet worked great with windows. Help Please? :confused:[-(:-s

```

mytoy@mytoy-Aspire-one:~$ wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
--2013-02-26 18:36:14--  http://dl.dropbox.com/u/57264241/wireless_script
Resolving dl.dropbox.com (dl.dropbox.com)... 107.20.235.144, 107.20.182.97, 107.22.253.68, ...
Connecting to dl.dropbox.com (dl.dropbox.com)|107.20.235.144|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1555 (1.5K) [text/plain]
Saving to: `wireless_script'

100%[======================================>] 1,555       --.-K/s   in 0s      

Last-modified header missing -- time-stamps turned off.
2013-02-26 18:36:14 (16.5 MB/s) - `wireless_script' saved [1555/1555]

[sudo] password for mytoy: 
mytoy@mytoy-Aspire-one:~$ 
```

---

### Post by BarfBag on 2013-02-26
What kind of laptop do you have?

---

### Post by EvyBear on 2013-02-26
Acer One Aspire. My friend said its a really sucky laptop lol.

---

### Post by BarfBag on 2013-02-26
See this thread: [http://ubuntuforums.org/showthread.php?t=1054629](http://ubuntuforums.org/showthread.php?t=1054629)

I encountered a similar problem with my Toshiba, and this did the trick.  The rundown is: copy and paste each of these commands into your Terminal:

sudo aptitude update

sudo aptitude install install linux-backports-modules-$(uname -r)

sudo modprobe ath5k

Then, reboot your system.

I saw your other thread, and I realize you're not all that comfortable with the terminal. Just copy and paste these commands one by one, and report back with your results. :)

---

### Post by squigish on 2013-02-26
> **EvyBear said:**
> ```

mytoy@mytoy-Aspire-one:~$ wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
--2013-02-26 18:36:14--  http://dl.dropbox.com/u/57264241/wireless_script
Resolving dl.dropbox.com (dl.dropbox.com)... 107.20.235.144, 107.20.182.97, 107.22.253.68, ...
Connecting to dl.dropbox.com (dl.dropbox.com)|107.20.235.144|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1555 (1.5K) [text/plain]
Saving to: `wireless_script'

100%[======================================>] 1,555       --.-K/s   in 0s      

Last-modified header missing -- time-stamps turned off.
2013-02-26 18:36:14 (16.5 MB/s) - `wireless_script' saved [1555/1555]

[sudo] password for mytoy: 
mytoy@mytoy-Aspire-one:~$ 
```

The wireless script should have saved a file called netinfo.txt to your home directory.  That's the file that has the useful information.  Either attach it to a post, or copy/paste the contents into a post using [noparse][CODE][/noparse] tags.

---

### Post by EvyBear on 2013-02-26
> **BarfBag said:**
> See this thread: [http://ubuntuforums.org/showthread.php?t=1054629](http://ubuntuforums.org/showthread.php?t=1054629)

I encountered a similar problem with my Toshiba, and this did the trick.  The rundown is: copy and paste each of these commands into your Terminal:

sudo aptitude update

sudo aptitude install install linux-backports-modules-$(uname -r)

sudo modprobe ath5k

Then, reboot your system.

I saw your other thread, and I realize you're not all that comfortable with the terminal. Just copy and paste these commands one by one, and report back with your results. :)

Should I put spaces in between them? :)

---

### Post by EvyBear on 2013-02-26
Holy Fudge, I think it worked. My pages are loading faster and my Youtube videos are loading faster. I'll give it an hour and tell you if its consistent. I'm so thankful for your help :D

---

### Post by EvyBear on 2013-02-26
> **squigish said:**
> The wireless script should have saved a file called netinfo.txt to your home directory.  That's the file that has the useful information.  Either attach it to a post, or copy/paste the contents into a post using [noparse][CODE][/noparse] tags.

Okay, Ill try again.

---

### Post by EvyBear on 2013-02-26
Yeah, I am not getting anything different. I don't even know what a home directory is, is that the terminal?

---

### Post by BarfBag on 2013-02-26
As far as the commands I sent go, you'll want to enter them one at a time. In other words, paste the first one, then press enter, paste the second one, press enter again, and so on. Did it work?

---

### Post by varunendra on 2013-02-27
EvyBear,

Since your original problem was wireless stability, if you believe it is stable now, there is no need to post back the file or any more info, and I would request you mark the thread as [Solved] using "Thread Tools" link above the top post on this page.

However, if you think the problem is not solved yet, then you need to attach the "netinfo.txt" file (or copy-paste its contents) in your next post.

If you are using default Ubuntu, which has a vertical Application Launcher panel on the left side of screen, then 'Home' is the folder that will open up when you click the folder icon at the top of that panel.

That is where the file should be located.

---

