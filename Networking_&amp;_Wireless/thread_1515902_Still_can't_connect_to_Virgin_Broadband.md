---
title: "Still can't connect to Virgin Broadband"
date: 2010-06-23
forum: Networking &amp; Wireless
---

### Post by Paul2795 on 2010-06-23
After googling "Virgin wireless broadband"+Ubuntu I got two posts on seperate websites that advised changing APN to VirginBroadband from Virgininternet whcih I did and also followed the advice of one of the aforementioned posts to disable all Authentication Methods except PAP, I still haven't been able to connect although the machine is obviously trying to. So should I try enableing other Authentication Methods, or could it be a hardware or some other problem?
Anyone out there got any ideas?

---

### Post by teejaybee on 2010-06-23
What error messages are you seeing in /var/log/syslog?

Does it connect in windows from the same location?

Which modem are you using?

---

### Post by Paul2795 on 2010-06-25
>  What error messages are you seeing in /var/log/syslog?
 
Does it connect in windows from the same location?
 
Which modem are you using?

I tried entering /var/log/syslog in Terminal and got 'Permission denied'
 
Yes it did connect in Windows from the same location, from different machine though that packed it in and was replaced by current one.
 
The modem is Virgin USB modem

---

### Post by oygle on 2010-06-25
> **Paul2795 said:**
> I tried entering /var/log/syslog in Terminal and got 'Permission denied'

You should be able to see syslog by System | Administration | Log File Viewer   |

If you can't do that, just go to a terminal window ..

```

sudo cat /var/log/syslog |more

```

> **Paul2795 said:**
> 
Yes it did connect in Windows from the same location, from different machine though that packed it in and was replaced by current one.

If it worked in Windooze, then it will work in Ubuntu. So, your connection from Virgin is working okay with windooze.

Do you have the DNS server settings correct ?

> **Paul2795 said:**
> 
The modem is Virgin USB modem

What brand/model is the USB modem. Is the light the right colour ?

I have all the authentication methods ticked on my mobile wireless. You are no doubt in Australia. Have you tried the Whirlpool forums, or does Virgin have a help centre ?

I'm not trying to discourage you from posting here. Just that I use Exetel mobile broadband, and the forums there had a few ubuntu users, and told me how to set it all up. But with the latest Ubuntu network manger, you just enter the correct APN, and it connects (as long as you have the dns server IP's correct that is).

Oygle

---

### Post by Paul2795 on 2010-06-26
> What brand/model is the USB modem. Is the light the right colour ?

I have all the authentication methods ticked on my mobile wireless. You are no doubt in Australia. Have you tried the Whirlpool forums, or does Virgin have a help centre ?

 
The modem is a Hauwei. It's been transfered into a receiver unit mounted on an outside wall, so I can't be certain what colour the light is.
 
I tried ringing Virgin Broadband Tech Support and was told they don't support Linux.

---

### Post by oygle on 2010-06-26
> **Paul2795 said:**
> The modem is a Hauwei.

Okay, same make as mine. I have the E169. What do your syslogs say?

> **Paul2795 said:**
> 
I tried ringing Virgin Broadband Tech Support and was told they don't support Linux.

Yes, a lot of ISP's in Australia are quite happy to take the dollars each month, but have no *nix people. Aren't there Virgin forums though ?

There is a [Virgin wireless forum on Whirlpool]("http://forums.whirlpool.net.au/forum/18?g=119") . Possibly have a look through [these posts]("http://forums.whirlpool.net.au/forum/?action=threads_search&f=18&g=119&q=ubuntu")

---

### Post by Paul2795 on 2010-06-27
Just something occured to me that I should have mentioned when I first started this thread. I don't know if this has any bearing on it, but I'm using *Mobile* Broadband.

---

### Post by oygle on 2010-06-27
> **Paul2795 said:**
> I don't know if this has any bearing on it, but I'm using *Mobile* Broadband.

Yes, assumed that you were. Paul, you need to supply more info if you want this problem solved.

What do your syslogs say. What version of Ubuntu are you running. Did you glean any info from the Whirlpool forums ?

Oygle

---

### Post by pdc on 2010-06-29
and if you are still out there Paul, 

this thread posts a solution to a Virgin problem in post #8

[http://ubuntuforums.org/showthread.php?t=1470505](http://ubuntuforums.org/showthread.php?t=1470505)

actions required are to copy and paste the commands below into a terminal

> sudo gedit /etc/udev/rules.d/temp-e169-modem.rules

enter your sudo password when asked; gedit (text editor) opens an empty page

then paste into that empty file

> ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="1001", RUN+="modem-modeswitch -v 0x%s{idVendor} -p 0x%s{idProduct} -t option-zerocd"


Save; Close; reboot

any joy?

---

### Post by oygle on 2010-06-29
Paul, you might be interested to look through [this Exetel thread]("https://forum.exetel.com.au/viewtopic.php?f=54&t=36438&start=0"). The [Wiki information on Australian wireless ]("https://wiki.ubuntu.com/AustralianTeam/Projects/WirelessBroadbandInformation") may be helpful ?

Oygle

---

### Post by Paul2795 on 2010-06-29
Thanks for the suggestions, but the problem's just been solved as I type this. My brother  who's the family computer expert and happens to be visiting, deleted the connection I set up and set up another from scratch, and then manually disabled CHAP authentication using Terminal. The moral of this saga is, learn to use Terminal, don't rely on the GUI.

---

### Post by scouser73 on 2010-06-29
I'm glad that you've got your connection sorted now, the best place to ask about problems connecting to the Internet on Virgin Media is here: [http://community.virginmedia.com/](http://community.virginmedia.com/)

---

