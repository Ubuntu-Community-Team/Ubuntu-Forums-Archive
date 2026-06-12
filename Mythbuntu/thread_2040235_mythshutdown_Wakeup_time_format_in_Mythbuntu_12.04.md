---
title: "mythshutdown Wakeup time format in Mythbuntu 12.04?"
date: 2012-08-10
forum: Mythbuntu
---

### Post by samihs72 on 2012-08-10
Hi!

Is [COLOR=#000000][FONT=Verdana]Wakeup time format in mythshutdown same in Mythbuntu 12.04 as in Mythbuntu 10.04?[/FONT][/COLOR] I have this kind of [COLOR=#000000][FONT=Verdana]Wakeup time format setup currently in Mythbuntu 10.04:
[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]Set Wakeup time format: yyyy-MM-ddThh:mm:ss[/FONT][/COLOR]

I would be appreciated of your help.

---

### Post by Lester_Burnham on 2012-08-10
Hi,

I've used time_t since mythbuntu 8.10

Lester

---

### Post by samihs72 on 2012-08-11
> **Lester_Burnham said:**
> Hi,

I've used time_t since mythbuntu 8.10

Lester
Hi! I would like to verify, whether I have to modify mythshutdown parameters after 12.04 upgrade or not. So you mean Mythbuntu 12.04 uses time_t instead of my current setup?

[COLOR=#000000][FONT=Verdana]        Set Wakeup time format: yyyy-MM-ddThh:mm:ss[/FONT][/COLOR] (<-- is this time_t in 12.04?)
[COLOR=#000000][FONT=Verdana]        Set Command to set Wakeup Time: mythshutdown --setwakeup $time[/FONT][/COLOR]
 
Thanks in advance!

---

### Post by Lester_Burnham on 2012-08-11
> **samihs72 said:**
> Hi! I would like to verify, whether I have to modify mythshutdown parameters after 12.04 upgrade or not. So you mean Mythbuntu 12.04 uses time_t instead of my current setup?

[COLOR=#000000][FONT=Verdana]        Set Wakeup time format: yyyy-MM-ddThh:mm:ss[/FONT][/COLOR] (<-- is this time_t in 12.04?)
[COLOR=#000000][FONT=Verdana]        Set Command to set Wakeup Time: mythshutdown --setwakeup $time[/FONT][/COLOR]
 
Thanks in advance!

I'm sure I'm using time_t on a 12.04 install on a machine for a friend.
For set wakeup time: sudo sh -c "/usr/bin/setwakeup.sh $time"
I've been using my post [here]("http://www.pcmediacenter.com.au/forum/topic/35208-acpi-wake-mythbuntu-810-rtc/page__p__246206__hl__acpi+wake__fromsearch__1#entry246206") on another forum since 8.10 and it still works for me on newer releases.

I don't use mythwelcome, this is in the backend setup.

Lester

---

### Post by samihs72 on 2012-08-11
> **Lester_Burnham said:**
> I'm sure I'm using time_t on a 12.04 install on a machine for a friend.
For set wakeup time: sudo sh -c "/usr/bin/setwakeup.sh $time"
I've been using my post [here]("http://www.pcmediacenter.com.au/forum/topic/35208-acpi-wake-mythbuntu-810-rtc/page__p__246206__hl__acpi+wake__fromsearch__1#entry246206") on another forum since 8.10 and it still works for me on newer releases.

I don't use mythwelcome, this is in the backend setup.

Lester
Hi Lester! I am using mythwelcome and I have this line mythwelcome setup:
sudo sh -c "/usr/bin/setwakeup.sh $time"

Let's see, I have to upgrade and see what happens.. Thanks for your reply!

---

### Post by jksj on 2012-08-12
High I am finding that mythtv wakes from shutdown at the wrong time - an hour too late in 0.26, worked fine in previous versions. I am located in the UK which uses daylight saving, an hour ahead of GMT. Looks like an issue related to the conversion of all times to UTC in 0.26. I have raised the following ticket in trac.


[http://code.mythtv.org/trac/ticket/10995](http://code.mythtv.org/trac/ticket/10995)

---

### Post by samihs72 on 2012-08-13
Hi!

My current mythshutdown and mythwelcome setup in Mythbuntu 10.04 is as following:

[COLOR=#000000][FONT=Courier New]$ mythtv-setup[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]Proceed to general>Shutdown/Wakeup Options[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]        Block shutdown before client connected (Unchecked)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]        Set idle shutdown timeout (secs): 180[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]        Set Max. wait for recordings (min): 15[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]        Set Startup before rec (secs): 300[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]        Set Wakeup time format: yyyy-MM-ddThh:mm:ss[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]        Set Command to set Wakeup Time: mythshutdown --setwakeup $time[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]        Set Server Halt command: mythshutdown --shutdown[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]        Set pre shutdown check-command: mythshutdown --check[/FONT][/COLOR]



[COLOR=#000000][FONT=Courier New]$mythwelcome --setup[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]set nvram-wakeup Command: sudo sh -c "/usr/bin/setwakeup.sh $time"[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]set nvram-wakeup Restart Command:LEAVE EMPTY!![/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]set Command to reboot: /sbin/reboot[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]set Command to shutdown: sudo shutdown -h now[/FONT][/COLOR]

So in my Mythbuntu 10.04 box $time parameter format is this "[COLOR=#000000][FONT=Verdana]yyyy-MM-ddThh:mm:ss". I am using nvram-wakeup instead of ACPI wakeup (motherboard supports only nvram-wakeup) in setwakeup.sh script.

Interesting to see, whether these mythshutdown and[/FONT][/COLOR] mythwelcome parameter values still work in Mythbuntu 12.04 (?).

---

### Post by Lester_Burnham on 2012-08-13
Hi,

I have only ever used ACPI wake. I use the settings on that tutorial page without mythwelcome. I use irexec to start mythtv and exit the frontend when finished. That way suits me best, because I just leave the frontend open and alt+tab to another window to work on it when required, or via ssh. Other frontends wake it with WOL.

Lester

---

