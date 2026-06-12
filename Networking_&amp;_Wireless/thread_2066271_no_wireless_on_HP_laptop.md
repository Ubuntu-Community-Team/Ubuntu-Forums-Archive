---
title: "no wireless on HP laptop"
date: 2012-10-04
forum: Networking &amp; Wireless
---

### Post by villageac on 2012-10-04
I am a newbie to this forum and to Ubuntu - if I should be posting to an existing thread, LMK and I'll repost.
I have a 4 year old HP DV2000 series laptop that I installed Ubuntu 12.04 on yesterday.  All seems well - I am able to get on the internet as long as I'm wired.  The laptop worked wirelessly as a Windows machine, but does not show the option of wireless on Ubuntu.  There is an on off wireless switch on the front of the laptop, I've switched it back and forth a number of times to no avail.  I've read through this forum as well as a number of sites I found on Google and have blundered my way through attempts at solving the problem but as yet have not.

I got this information.  Also, in additional drivers it says Broadcom STA drivers are activated

mike@mike-HP-Pavilion-dv2000-RP413UA-ABA:~$ lspci -vvnn | grep 14e4
01:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
mike@mike-HP-Pavilion-dv2000-RP413UA-ABA:~$

---

### Post by bart.a on 2012-10-10
Have you installed the correct windows driver with the ndiswrapper?

Please specify the wireless card. Who is the manufacturer and what is the type number?

---

### Post by bart.a on 2012-10-11
The broadcom chip is probably the culprit.

Go to terminal and type

[I]sudo apt-get remove bcmwl-kernel-source 
sudo apt-get install b43-fwcutter
sudo apt-get install firmware-b43-installer[/I]

Then restart the machine and enable wireless.

You can also check if the wireless is blocked by hardware or software:

*sudo rfkill list*
if it is blocked, use this to unblock.
*sudo rfkill unblock all*

---

### Post by villageac on 2012-10-11
thanks for your response.  I solved my problem a day after I posted - it's been a week or so, so I am not sure what I did - but I believe I uninstalled a driver - my answer came from someone on experts-exchange.com

---

### Post by bart.a on 2012-10-11
would you please place a link on this thread and change your post to solved..

Then others might be able to put it to use..

Thanks..

---

### Post by villageac on 2012-10-11
Done! But I don't know how to mark it as solved - can you either mark it as solved or please tell me where I do that - thanks!

[http://www.experts-exchange.com/OS/Linux/Q_27887611.html](http://www.experts-exchange.com/OS/Linux/Q_27887611.html)

the answer was:

First try disabling the additional drivers for the wireless card, then see if functions



I put a command in terminal post and got this:

mike@mike-HP-Pavilion-dv2000-RP413UA-ABA:~$ lspci -vvnn | grep 14e4
01:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
mike@mike-HP-Pavilion-dv2000-RP413UA-ABA:~$ 

In the area that says Windows Wireless Drivers it says Currenlty Installed Drivers and the box below it is blank.  There is an option to install new driver - if I click on that it says select inf file and asks for a location - if I look in the available locations in the dropdown, I can't find an inf file
ACCEPTED SOLUTION
by: rindiPosted on 2012-10-04 at 07:22:40ID: 38462665

First try disabling the additional drivers for the wireless card, then see if functions.

---

### Post by wildmanne39 on 2012-10-11
Hi, I marked it as solved for you, it can only be done by you or a mod.

Just click on thread tools in the future and then you will see the option to mark it as solved.
Thanks

---

