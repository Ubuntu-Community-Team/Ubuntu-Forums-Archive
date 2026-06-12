---
title: "Hard and soft blocked"
date: 2013-01-23
forum: Networking &amp; Wireless
---

### Post by Undertow92 on 2013-01-23
Hello, this is my first post in Ubuntu forums. I beg for your help - literally - because I am in absolute need of fixing it.

So, let me get to the point. I have a Presario CQ57 laptop in which I had Ubuntu 12.10. Everything seemed to work fine, until the wireless led of the laptop turned - irreversibly as it proved to be - orange. ( orange=off, blue=on)

When I tried to re-enable the wireless through the system settings, nothing happened. The ON status stayed as it was for less than a second and then OFF again. So, I tried some things, got desperate and thought it would be a problem of the specific Ubuntu 12.10. I decided to download Lubuntu 12.10 on another pc and installed it in my laptop, erasing Ubuntu completely. 

But, the problem persisted. I tried and tried lots of solutions that I found on threats marked as [SOLVED] but none worked. I am a true noob when it comes to fixing those things, so please, if someone can help, I would appreciate it so much.

---

### Post by cariboo on 2013-01-23
Could you open a terminal, and type the following command:

```
rfkill list
```

then paste the output in your next post. The output should look similar to this:

```
 rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
```

---

### Post by Undertow92 on 2013-01-23
Thank you for your reply. I did as you said. Here are the results:


0: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes
1: hp-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: no

---

### Post by LitilDivil on 2013-01-28
I had similar situation on a friend`s HP compaq lappy...Solution was to enter the BIOS and choose BIOS default settings, save and reboot. And wifi led turned blue (on) by itself and everything worked fine after that. Was very weird expirience for me...

---

### Post by Undertow92 on 2013-01-28
thank you for posting your reply, but the solution you suggested didn't work for me. I entered the BIOS as well, but when I rebooted the led was still off for me.  This problem has tortured me for many days now, so if someone has  a solution they can propose, I would be more than grateful.

---

### Post by zrdc28 on 2013-01-30
"hard blocked" (above) means that the _hardware_ is blocking the
use of wi-fi, which generally means there is an Fn plus another button
combo which allows the _hardware_ to turn on or off the wi-fi stuff
(sending radio signals from your laptop to the access point takes
battery power, and most manufacturers give you a switch to turn that off
when you don't want your battery running down while NOT needed wi-fi,
see?) so, check your user manual and be sure to unblock, then:

 "soft blocked" means your software is blocking this use of wi-fi,
here (and i hope there) i find a Network Manager icon in the "tray"
(but, i don't know if you have a 'tray' because you have not declared
your desktop environment (and not all DEs have a tray)...and, if i left
click on that icon i see a place to switch the wi-fi from enable to
disable to enable . . .

with the hardware unblocked, then enable wi-fi and it will probably do
that...

---

### Post by kurt18947 on 2013-01-30
> **zrdc28 said:**
> "hard blocked" (above) means that the _hardware_ is blocking the
use of wi-fi, which generally means there is an Fn plus another button
combo which allows the _hardware_ to turn on or off the wi-fi stuff
(sending radio signals from your laptop to the access point takes
battery power, and most manufacturers give you a switch to turn that off
when you don't want your battery running down while NOT needed wi-fi,
see?) so, check your user manual and be sure to unblock, then:

 "soft blocked" means your software is blocking this use of wi-fi,
here (and i hope there) i find a Network Manager icon in the "tray"
(but, i don't know if you have a 'tray' because you have not declared
your desktop environment (and not all DEs have a tray)...and, if i left
click on that icon i see a place to switch the wi-fi from enable to
disable to enable . . .

with the hardware unblocked, then enable wi-fi and it will probably do
that...

The above is good information.  To go one step further, from an account with SUDO privileges, type the following command:

```
sudo rfkill unblock all
``` 

then enter your password when prompted and let us know what happens.  I'm concerned about the phy0 hard block but simple things first.  After trying the above, check the network indicator.  Make sure that wireless is enabled.

---

### Post by Undertow92 on 2013-02-02
Thank you for your help.
So, I have tried all of those things but a strange thing happened. When I start my laptop, the lubuntu startup screen takes a minute or more to load and while it does so it says something like "configuring networks" and then "60 more seconds to configure networks". When it is actually on, there is no network icon on the panel nor can I turn on/off the wireless led. A couple of minutes after, though, the network icon appears out of the blue, turning the wireless led on and working just fine! What do you say?

---

### Post by varunendra on 2013-02-02
*Thread moved to **Networking & Wireless**.*

---

### Post by varunendra on 2013-02-03
As I can see you have got your main problem already solved somehow, just a few comments that you may find helpful in case something funny happens again.

> **Undertow92 said:**
> 
0: phy0: Wireless LAN
	Soft blocked: yes
	**Hard blocked: [COLOR="Red"]yes[/COLOR]**
Apart from what zrdc28 already suggested above, the WiFi on/off switch in many hp laptops has been reported many times to be too buggy, especially the 'touch-type' and 'press-type' ones. They become dodgy (sometimes work, sometimes not) even in some new laptops, and this kind of misbehaving (if starts) is not OS-specific, but is actually a hardware bug. I haven't yet seen any such reports with 'flip-type' switches yet (not sure if hp uses them in any models).

About the fourth type of on/off switch that uses **'Fn'+ <some key>** combination - That one may sometimes work with a different key combination other than what is indicated on the keyboard. For example, your F6 key may have the wireless symbol on it, while it may actually be F10 (with some other symbol or maybe none!) that may work as a switch for wifi. I have only once seen a user mentioning that and another one confirming the same behaviour in the same thread. I'm not sure, but believe it may be due to the 'wmi' driver inconsistency with some specific models.

Another common confusion is that sometimes the 'second' functions of the function keys actually become the 'first' functions. Which means - the hardware functions indicated on them (wifi, brightness, sound,...etc.) may work WITHOUT combination with 'Fn' key, and their normal functions (F1,F2,F3,...etc.) will work with the Fn key combo. Sounds odd, but I have confronted this behaviour myself many times. Not sure if it was intentional or a bug.

Regardless of the reason, you should be aware that none of the solutions will ever work unless the interface is '**Physically ON**', means, the "Hard blocked" value should be "No" in the **rfkill list** output.


> **LitilDivil said:**
> I had similar situation on a friend`s HP compaq lappy...Solution was to enter the BIOS and choose BIOS default settings, save and reboot. And wifi led turned blue (on) by itself and everything worked fine after that... A good thing to try if the switch doesn't seem to work. Alternatively, just make sure the wireless interface *(can be anywhere in the BIOS, with any name that suggests a network adapter)* is set to "**Enabled**" in the BIOS. Again, no solution will work if it is disabled in the BIOS, its just like physically turning it off.


Now about your current issue-
> **Undertow92 said:**
> When I start my laptop, the lubuntu startup screen takes a minute or more to load and while it does so it says something like "configuring networks" and then "60 more seconds to configure networks". When it is actually on, there is no network icon on the panel nor can I turn on/off the wireless led. A couple of minutes after, though, the network icon appears out of the blue, turning the wireless led on and working just fine! What do you say?
My first guess is that everything is normal, it is just taking long to detect wireless networks, and configure them if any found. Until the network becomes ready, the Network Manager will be absent. To stop this behaviour, you should try disabling the "Connect Automatically" option for your wireless interface(s) in Network Manager.

**Click NM-applet > Edit Connections > goto "Wireless" tab > double-click your wireless interface > clear the checkbox that says "Connect Automatically" > Save > close**

**[[COLOR="Red"]Correction :[/COLOR]** The above is for default Ubuntu. In lubuntu, the path to network settings is : **Lubuntu menu (bottom left corner) > Preferences > Network Connections > goto "Wireless" tab > (rest same as above)...]**

Reboot and see if it helps. Post back if not.

---

