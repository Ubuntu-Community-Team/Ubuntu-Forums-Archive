---
title: "acpi and mythbakend problem"
date: 2007-10-03
forum: Mythbuntu
---

### Post by spoky99 on 2007-10-03
I'm trying to make work the script for automatic wake-up/shutdown of mythbutu. I follow the ubuntu mythtv howto [https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake](https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake) The acpi work (i tryed $ sudo sh -c 'echo "+00-00-00 00:05:00" > /proc/acpi/alarm' and after shutdown the computer they reboot after 5 minute) but when I set the script into mythtv-setup the computer don't estart for recording the tv.
Using one script I understand that the $time variable is write from mythtv only when the sistem goes down at the end of a programmed record, but if I manual shutdown the computer the $time variable isn't write. My local time is set to +1 hours.
I search other faq, but I don't found nothing about this problem
Someone could help me? or could suggest me one faq about this problem?

(excuse me for my bad english :)]
Smile )

---

### Post by superm1 on 2007-10-06
> **spoky99 said:**
> I'm trying to make work the script for automatic wake-up/shutdown of mythbutu. I follow the ubuntu mythtv howto [https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake](https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake) The acpi work (i tryed $ sudo sh -c 'echo "+00-00-00 00:05:00" > /proc/acpi/alarm' and after shutdown the computer they reboot after 5 minute) but when I set the script into mythtv-setup the computer don't estart for recording the tv.
Using one script I understand that the $time variable is write from mythtv only when the sistem goes down at the end of a programmed record, but if I manual shutdown the computer the $time variable isn't write. My local time is set to +1 hours.
I search other faq, but I don't found nothing about this problem
Someone could help me? or could suggest me one faq about this problem?

(excuse me for my bad english :)]
Smile )
I have a hunch that the mythtv user isn't able to execute this command due to a permissions issue.

Try this to log in as the mythtv user temporarily:

```
sudo -s
su mythtv

```

Now as the mythtv user try to issue your shutdown commands.  You'll get more verbose errors/warnings.

---

### Post by spoky99 on 2007-10-07
I already resolved this problem during the test (with the visudo I give the permission to mythtv and user to shutdown the computer and execute like a root the script and other thigs)
I try to shutdown the computer from user and mythtv but in each case the $time variable was not set
I try to use also mythshutdown... (I don't know what exatly they do) the computer goes down but... $time was not write

I also miss one information the $time is corectly set only if in the mythtv-setup the date format is started and ended with '' otherwise the $time it contains only the date

now I'm trying to reinstall all the sistem with the timezone set to +0 for don't use the script

---

### Post by chrisork on 2007-11-28
Hi there,

I've got similar problems. (bad english AND the correct writing of $time)

I used the same How-To. The Box starts when i write the RTC wakeup time manually, but mythbackend doesn't write it.

I use the standart Mythbuntu 7.10 - with Mythwelcome. I changed the MythWakeSet-Script as advised, but i think the $time variable isn't in the correct format. 
For testing i changed "Set wakeup time command" in mythtv-setup to "echo $time > my.log"

After the automated shutdown and the manual boot, my.log says: "yyy-11-28T21:57:00"

What to do?

Chris

---

### Post by roseway on 2007-11-29
I rather suspect that there's a mistake in the section near the end of the document headed "Configure MythBackend". Surely the wakeup time format should start 'yyyy-' not 'yyy-' ?

---

### Post by chrisork on 2007-11-29
I solved the problem. I think i messed up the hwclock.sh script. Now it works - without the proposed changes when using mythwelcome.

---

### Post by spoky99 on 2008-09-04
maybe I found the answer form my problem but I don't know how to solve it.
Searcing one linux-timer I read this inside this article for knoppmyth
(*[http://www.knoppmythwiki.org/index.php?page=WakeupToRecord](http://www.knoppmythwiki.org/index.php?page=WakeupToRecord)*)

[I]Problem Number 3:

If a normal shutdown -h is done, knoppmythbackend does not set the wakeup time. To fix this, you need to shutdown the frontend and set up the backend to shutdown when nothing is attached to it. This is how you must always shut down the computer for the wakeup to work. [/I]

when I make the test above I poweroff the computer using the xfce menu's button.
I read that is possible set the backend going down itself if isn't one frontend open but I don't know where is this setting-option.
Maybe that shutdown buttons in the logout menu of mythbuntu still make the correct shutdown first of the frontend and after of the backend, and this one, write-and-set the wake-up time in /proc/acpi/alarm
.

---

### Post by deadcyclo on 2008-09-04
> **spoky99 said:**
> 
I read that is possible set the backend going down itself if isn't one frontend open but I don't know where is this setting-option.

There is no specific setting for it. Just make sure you follow every single step in the guide properly. 
> **spoky99 said:**
> 
Maybe that shutdown buttons in the logout menu of mythbuntu still make the correct shutdown first of the frontend and after of the backend, and this one, write-and-set the wake-up time in /proc/acpi/alarm
.
Nope. you have to have mythbackend shut down for it to work.

---

### Post by spoky99 on 2008-09-07
[QUOTE=deadcyclo;5728468]There is no specific setting for it. Just make sure you follow every single step in the guide properly. 

I do it many time, the last time with a linux expert and... the problem was the same. ACPI work fine but the computer resume itself only if go-down itself after a planned record. If I shutdown the computer mythbackend don't write the wakeup time in /proc/acpi/alarm
(my friend test it using a pyton script)

I tried sutdown, poweroff and.. more different way for to "close" the computer. All work for shutdown the computer but no one make write the date & time of wakeup.
My be that I don't understand a banal thing, my english is not good but I read and translate every word in the how-to and I used different how-to for make it work, in the beginning I thunk was a problem of the script that was not good for ubuntu o mythbuntu.. but now I know this was not the problem.

---

### Post by bmwman on 2008-09-07
> **chrisork said:**
> I solved the problem. I think i messed up the hwclock.sh script. Now it works - without the proposed changes when using mythwelcome.

Hello, I'm using the same How To and of coarse I have the same issue. Everything works fine for the test but when the computer actually shuts down it never comes back on. Please post your settings if you figured it out. I spend days fiddling with this thing and still doesn't work. If anyone can help I would really appreciate it.

Here is what I wrote in another thread:
> This absolutely doesn't make sense to me. Here're my settings
Backend:
Code:

Wakeup time format:: yyyy-MM-ddThh:mm:ss
Set wakeuptime Command: sudo mythshutdown --setwakeup "$time"
Server halt Command: sudo -H mythshutdown --shutdown
Pre Shutdown check-command: mythshutdown --check

Mythwelcome:
Code:

nvram-wakeup Command: /usr/bin/MythWakeSet $time
nvram-wakeup Restart Command:
Command to reboot: sudo -H shutdown -h -r now
Command to shutdown: sudo -H shutdown -h -P now

For testing i put Command to shutdown: in Mythwelcome and I have a recordind scheduled at 4:30pm - an hour ahead.
The results:
Code:

backend@backend:~$ cat /proc/acpi/alarm
2008-09-06 19:43:41

Looks perfect, right? It sets the date and time correctly.

BUT!!! When I put in Mythwelcome instead of the machine shuts off and never comes back on. Of coarse I've tried that hundred times I know it won't turn back on so turn it on manually and check the alarm:
Code:

backend@backend:~$ cat /proc/acpi/alarm
2008-00-00 19:54:52

WTF!! I spent days and it keeps doing it. It works fine for the test but when it acutally shut down, it doesn't set the alarm time properly.

Please help me fix this!

---

### Post by Andrew U.K. on 2008-09-08
I'm in on this one. I have the same problem. 
I notice that you have a Gigabyte motherboard bmwman, I also have a gigabyte GA-MA78GM-S2H, what's yours spoky99? I'm sure this has nothing to do with it but I'm clutching at straws. 
I have also spent days now turning to weeks. In these times of austerity my wife is begining to think I've wasted £300 , so please help, someone,anyone.....

---

### Post by jb5 on 2008-09-08
I too had LOADS of problems getting ACPI to work properly.

I've got an ASUS board in my setup, but I eventually got it to work.

See [post 29 forwards](http://ubuntuforums.org/showthread.php?t=463478&page=3), maybe this approach might help.

I would make sure you know what settings you have now, so if this approach doesn't succeed at least you can get back to where you are now.

Best of luck!

---

### Post by spoky99 on 2008-09-09
[I][QUOTE=Andrew U.K.;5748005]I'm in on this one. I have the same problem. 
I notice that you have a Gigabyte motherboard bmwman, I also have a gigabyte GA-MA78GM-S2H, what's yours spoky99?[/I]

I'm testing and working with some LV-671 (Mini-ITX Motherboard) made by commell. I had two mobo whit the same bios (identical release of bios and identical configuration) in one acpi work in the other not work :D
I upgraded the bios in both the mobo and the mobo that dont' work now work.. the other... I could found one other bios cip because now don't work :D
I saw this mobo work also with nwram-wakeup but I prefer use the ACPI.

---

### Post by Andrew U.K. on 2008-09-10
Thanks.
I'm going to work through a fix on another thread, then I will try this one. After a month i'm not quite ready to give up....

Andrew

---

