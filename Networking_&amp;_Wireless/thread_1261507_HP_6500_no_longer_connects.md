---
title: "HP 6500 no longer connects"
date: 2009-09-08
forum: Networking &amp; Wireless
---

### Post by ConfederateColonel on 2009-09-08
I was able to connect to my HP 6500 wireless just fine and everything worked - for a while. Something happened somewhere, and now I get a message that the printer may not be connected when I try to print a test page.

1) This is affecting all three of my systems running Ubuntu - two running 9.04 and one running 8.04.

2) The printer works fine from my Windows XP system, so I know the printer is capable of working.

3) I am not aware of any changes made to the printer or the network (not sure if there is even anything that can be changed on the printer).

Printer Settings now show:

[B]Device URI: socket://:9100
Make and Model: HP Officejet 6300 Series Foomatic/hpijs. hpijs 2.8.12[/B]

I didn't make any notes to see if any of that changed.

Is there anything in the software setup that could have changed? I know that the printer wireless software was not run since it stopped working.

What is so strange is that it all worked fine on all 3 systems until *something* changed. Any hints as to what to check?

Thanks for any help!

---

### Post by ConfederateColonel on 2009-09-09
It looks like the IP address somehow got changed. Here are the steps to fix it:

1) On the HP6500, press the Setup button (looks like a wrench).
2) On the panel, select Print Report, then Network Config Page.
3) The IP address is about half way down the report.
4) Enter the IP address in the Device URI field.

Everything goes smoothly after that.

Man, I sure love this forum! Even though I didn't get the specific answer, I was able to browse around in other somewhat related posts and figure out what to try.

---

### Post by smokindans on 2009-09-09
Hello,

I have the same exact problem with my HP1600 Color Laserjet. I have uninstalled, reinstalled, rebooted, etc....but the printer still will not connect.  The printer worked in the past, and still works on my Windows computers. This happened once before and I reinstalled it and it started working again. This time I cannot get it reconnected. I saw your post but was wondering if you could elaborate. I am not sure what setup menu and what icon of a wrench you are referring to.   Thanks in advance for any assistance. 

D

---

### Post by ConfederateColonel on 2009-09-09
> **smokindans said:**
> Hello,

I have the same exact problem with my HP1600 Color Laserjet. I have uninstalled, reinstalled, rebooted, etc....but the printer still will not connect.  The printer worked in the past, and still works on my Windows computers. This happened once before and I reinstalled it and it started working again. This time I cannot get it reconnected. I saw your post but was wondering if you could elaborate. I am not sure what setup menu and what icon of a wrench you are referring to.   Thanks in advance for any assistance. 

D
The setup button is on the control panel of the HP 6500 printer - not the Ubuntu system. When you install your printer software, is there any kind of diagnostics that might give you the IP it is using? Maybe some sort of test page that might have the IP address? Let me know if there is anything else I can add that might help!

---

