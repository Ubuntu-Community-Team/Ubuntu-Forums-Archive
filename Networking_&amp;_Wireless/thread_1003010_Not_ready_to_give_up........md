---
title: "Not ready to give up......."
date: 2008-12-05
forum: Networking &amp; Wireless
---

### Post by joshag1 on 2008-12-05
Hello, new to both linux and this forum.
I have worked with PC's for a good part of my life and made money in networking years ago (still young but don't do it anymore). Enough with the greetings and on to the problem.........

Fighting with Samba and my windows network. I have 3 PC's and one has recently been converted to Ubuntu 8.10 (dell dimension 8300). The others are a HP laptop (xp) and another dell w/xp. Only wired client is Ubuntu others are through linksys wrt54g's (3 total in the house). I have tried wiring laptop to same router as Ubuntu......nothing.

Once I got Ubuntu to see the other pc's and their shares but since then nothing. It even saw my iphone once??? I have tried to install/uninstall samba both through the program manager and w/line commands. Have tried editing config but still nothing.

On the other side, the windows pc's see the "Office-PC" but not it's shares.

Wouldn't bee such a problem but all printers are attached to new Ubuntu system.

I have spent 2 1/2 days (work is slow) working on this without a solution. I have read about every post on every forum and followed about a dozen "solutions" without any luck.

Any help would be appreciated..........

---

### Post by pastalavista on 2008-12-05
Just a noob to networking myself but do you have ntfs-3g and ntfprogs installed on the 'buntu machine? all the server apps? wireless networking is kinda difficult anyway as the routers all have to be setup too... overlapping signals maybe... kinda mind-boggling to me :) good luck.

---

### Post by ByteJuggler on 2008-12-05
I've seen trouble when Samba and Windows machines would fight over who the browse master is on the network, effectively splitting the workgroup/network into 2 groups so that one set wont see the other, depending on which browse master they end up using.  You might try disabling the computer browser service (iirc) on the windows machines (I'll try to confirm my recollection of this.) 

I'll also try to post a sanitized version of my Samba config, might be the simplest way to get you going. As for hidden shares -- home shares are hidden by default, and only visible to the user from the remote machine if the local username is the same as the home share on the ubuntu server.  There's a setting in the samba config to control this, IIRC.

In the meantime, I would say firstly get one machine set up so it will succesfully see your Ubuntu machine using an ethernet cable, and only then add in wireless into the mix.

---

### Post by joshag1 on 2008-12-05
Yeah, I'm trying the wired over wireless first. I am really comfortable with my wireless network. I am Frankenstien and it's my monster.
I am however having problems getting to the samba config. Seems it won't let me in without root access and that seems to be impossible in 8.10. Is this true? 

I will also double check to make sure I have all files installed.

In the mean time I have had another instance of now you see me, now you don't. Wirelessly I could see the other machines and browse their shares. Then just as quickly, they were gone. Haven't seen my iphone again. That was a first.

---

### Post by ByteJuggler on 2008-12-05
> **joshag1 said:**
> Yeah, I'm trying the wired over wireless first. I am really comfortable with my wireless network. I am Frankenstien and it's my monster.
I am however having problems getting to the samba config. Seems it won't let me in without root access and that seems to be impossible in 8.10. Is this true? 


Lol no.  :-)  Whenver you need to run something as root, just prepend "sudo" and type *your* password when asked.  The command will then run as root.  Ubuntu doesn't use the root account explicitly (by logging into root account as a seperate user) as is done in most/many other Unix/Linux flavours, but instead keeps the root account totally locked, using "sudo", which elevates the current user to root level when required.  This, amongst other things, close a common attack/hack vector, which increases system security.

The GUI version of the "sudo" command is "gksudo".  So try for example pressing alt-f2, then type/copy:

```
gksudo gedit /etc/samba/smb.conf
```

That's running gedit (the gnome text editor) on /etc/samba/smb.conf, the samba config file.  The gksudo in front runs it as root, so you have root/edit privileges.


> 
I will also double check to make sure I have all files installed.

In the mean time I have had another instance of now you see me, now you don't. Wirelessly I could see the other machines and browse their shares. Then just as quickly, they were gone. Haven't seen my iphone again. That was a first.
That's typical behaviour when you have multiple network browse masters. One browse master has an empty list since most/all of the pc's are registered with the other browse master etc. Any PC that uses the "empty" browse master to get a listing of machines on the network will consequently not see the other machines on the network.  If the PC's are fighting, then the browse master can change every so often as the 2 browse masters make announcements on the network about who the browse master is, giving rise to the now-you-see-me-now-you-dont phenomenon.  (This problem BTW can happen even on Windows only networks, in case you were wondering.)  

Anyway, I'll try to get back to you with more concrete suggestions tomorrow (very late here, must go sleep now.)

---

### Post by joshag1 on 2008-12-05
Lesson learned!!!

I can now see all my shares on the xp pc's and that's all that matters now. Next step is to get printers working. They are visible but I get "connection error" when I try to print. This I am sure can be solved with access to samba config. Thanks allot. 

Getting late here too and I have an all day concert event tomorrow. Never too old to rock n roll.......

---

### Post by joshag1 on 2008-12-07
By the time I was home last night from the show, OS wouldn't boot up. Could be a hard drive issue. Windows w/ubuntu crashed a few days before and just chalked it up to hurt feelings by windows.

I have now reloaded this software 3 times and can say it appears to be more of a "hobby" than an OS???

---

### Post by ByteJuggler on 2008-12-08
> **joshag1 said:**
> By the time I was home last night from the show, OS wouldn't boot up. Could be a hard drive issue. Windows w/ubuntu crashed a few days before and just chalked it up to hurt feelings by windows.

I have now reloaded this software 3 times and can say it appears to be more of a "hobby" than an OS???

Well.  There are certain hardware that is problematic, and sometimes cause trouble, but usually not of the crashing variety.  I think you're getting the wrong impression if you're saying Linux/Ubuntu is more of a hobby than an OS.  Most of the machines in my house for example are Ubuntu and they are actually more stable than the Windows ones, and in any case have months of 24/7 uptime at a time, only to be interrupted by reboots due to kernel upgrades.  Another example: A friend of mine has recently upgraded his 7.04 (Gutsy) machine with an uptime of nearly 1 year to Hardy, which sadly broke his run of uninterrupted uptime.  

As I say, usually crashing behaviour can be traced buggy drivers (in the majority of cases video drivers) or otherwise other hardware problems (RAM problems, hard drive problems, overheating problems.)  Unfortunately what sometimes happens, is that people with flaky PC's running windows, get fed up of the flakiness of their PC's under windows, and then decide as a result to install Ubuntu.  Unfortunately, in cases where such flakiness is actually as a result of dodgy hardware, they then incorrectly get the impression that Linux/Ubuntu is less stable than Windows whereas the problem in such cases then isn't the software at all. 

You need to post *exactly* what is happening and exactly what messages you're getting.  Software problems tend to be repeatable (so things crash in the same place, predictably, every time.)  Hardware problems can sometimes be like this, but any randomness and variation in the behaviour/crashing can strengthen a diagnosis of hardware (as opposed to drivers/software) problems.  3 questions spring to mind: 1) Have you done a memory check (available from ubuntu boot menu)?  2) Have you done a hard drive diagnostic? (HDD manufacturers provide CD images on their websites that you can download and burn to do low level diagnostics on hard drives.  Highly recommended if you suspect HDD trouble for any reason.)  3) Did you verify your Ubuntu installation CD (also an option on the Ubuntu boot menu.)

Lastly, remember you're in a foreign country, so to speak..  Linux is not Windows, things are done differently and you're going to experience friction as a result of things being differently done in many cases than what you might be used to on Windows.  So there are going to be a learning curve and likely a number of reinstallations as you learn the ropes.  If you find that the learning curve is too steep and the land too alien, then by all means use Windows instead if it suits you better.  :)

BTW sorry for not having got back on the whole browse master thing yet -- it's an awkward problem when it happens and I've not had a chance to try to dig into/try to replicate it again to try to supply you a tested fix. (Assuming that indeed it is the problem on your network.)

---

### Post by joshag1 on 2008-12-09
I see that most of my problems were with a bad hard drive. 

I do believe, and I am not going to let it get the best of me, that there is a lot of work with Linux. No, I don't think that Linux/Ubuntu is windows. If I did, I never would have installed it. It is for me a huge!! learning curve. 

I will, with the support and knowledge of this forum and others, overcome.

---

