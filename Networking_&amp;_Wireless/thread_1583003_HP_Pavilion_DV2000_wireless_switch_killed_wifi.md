---
title: "HP Pavilion DV2000 wireless switch killed wifi"
date: 2010-09-27
forum: Networking &amp; Wireless
---

### Post by locoHost on 2010-09-27
The HP Pavilion series lappys have a switch on the front that disables wireless networking. I was plugged into the lan and I switched the wifi off the other day, now it's permanently switched off! :-( The wifi indicator light will no longer turn blue no matter how many restarts or ifconfig up/downs I do. Without reinstalling Ubuntu, how can I get this going again. It's using (was) the B43 Broadcom driver.

Thanks again everyone :-)

Mark

---

### Post by lukeiamyourfather on 2010-09-27
Try a live CD or another operating system to see if the card still works. Until you test the device in another environment don't rule out the possibility that the device failed between the last time it was disabled and now (or the switch could've failed).

---

### Post by locoHost on 2010-09-27
Man that would suck, but thanks, I'll definitely try with the Live CD :-)

---

### Post by slashwannabe94 on 2010-09-27
I totally agree with the above, could be hardware failure :P

---

### Post by bkratz on 2010-09-27
You might look at the very last entry on this page

[http://ubuntuforums.org/archive/index.php/t-832355.html](http://ubuntuforums.org/archive/index.php/t-832355.html)

---

### Post by locoHost on 2010-09-27
> **bkratz said:**
> You might look at the very last entry on this page

[http://ubuntuforums.org/archive/index.php/t-832355.html](http://ubuntuforums.org/archive/index.php/t-832355.html)

Wow, so power cycle it. Ok I'll try this and post the results.

Thank you!!! :-)

---

### Post by Shriner on 2010-09-27
Also be aware that HP has a problem with their motherboards in their laptops. They overheat (usually after the warranty has expired), the first thing that happens is that the wireless card will appear to die. You can replace it, but it still will not function. The next that will happen, usually within a month to a year, is your graphics will fail. 

It happened to me. While Google was my friend in diagnosing, the suggested repair shown on youtube, did me no good. HP will fix it, for a cost, if I remember correctly about $500 (plus shipping). 

My suggestion is to start looking for a new laptop, not an HP (or Compaq - same company). In the interim you can purchase a USB WiFi radio at WallyWorld to get you by.

Edit: Just noticed I still have the lappy listed in my sig...will have to change that....

---

### Post by locoHost on 2010-09-27
> **bkratz said:**
> You might look at the very last entry on this page

[http://ubuntuforums.org/archive/index.php/t-832355.html](http://ubuntuforums.org/archive/index.php/t-832355.html)

As expected, power cycle did nothing. I let it sit without the battery in for about 2 hours. My kind of luck normally precludes a far more complex solution than this :-/

I'll try the Live CD next. Assuming the Live CD works, can I uninstall the B43 Broadcom driver and reinstall without being a brain surgeon? Would that even do anything?

Thanks :-)

---

### Post by lukeiamyourfather on 2010-09-27
> **locoHost said:**
> I'll try the Live CD next. Assuming the Live CD works, can I uninstall the B43 Broadcom driver and reinstall without being a brain surgeon? Would that even do anything?

Cross that bridge when you get to it. Let us know what you find out when trying another operating system (or a live disc).

---

### Post by locoHost on 2010-09-27
> **lukeiamyourfather said:**
> Cross that bridge when you get to it. Let us know what you find out when trying another operating system (or a live disc).

Couldn't get wirless working with Live CD either. I could enable wireless, but this would never turn on the front blue light.

I tried installing the B43 driver from hardware drivers screen but got an error each time. The error was in /var/log/jockey.log...


```
2010-09-27 17:23:07,612 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-09-27 17:23:07,670 DEBUG: nvidia_current is not the alternative in use
2010-09-27 17:23:09,346 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-09-27 17:23:10,106 DEBUG: nvidia_current is not the alternative in use
2010-09-27 17:23:11,480 DEBUG: handler firmware:b43 previously unseen
2010-09-27 17:23:11,576 DEBUG: handler kmod:wl previously unseen
2010-09-27 17:23:11,577 DEBUG: handler xorg:nvidia_current previously unseen
2010-09-27 17:23:11,666 DEBUG: writing back check cache /var/cache/jockey/check
2010-09-27 17:23:11,753 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-09-27 17:23:11,774 DEBUG: nvidia_current is not the alternative in use
2010-09-27 17:23:12,036 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-09-27 17:23:26,964 DEBUG: Installing package: b43-fwcutter
2010-09-27 17:23:32,514 DEBUG: install progress statusChange dpkg-exec 0.000000
2010-09-27 17:23:41,204 DEBUG: install progress statusChange b43-fwcutter 0.000000
2010-09-27 17:23:41,204 DEBUG: install progress statusChange b43-fwcutter 20.000000
2010-09-27 17:23:41,737 DEBUG: install progress statusChange b43-fwcutter 40.000000
2010-09-27 17:23:41,741 DEBUG: install progress statusChange b43-fwcutter 60.000000
2010-09-27 17:23:41,751 DEBUG: install progress statusChange man-db 60.000000
2010-09-27 17:23:45,522 DEBUG: install progress statusChange dpkg-exec 60.000000
2010-09-27 17:23:45,610 DEBUG: install progress statusChange b43-fwcutter 60.000000
2010-09-27 17:23:45,611 DEBUG: install progress statusChange b43-fwcutter 80.000000
2010-09-27 17:23:45,611 DEBUG: install progress statusChange b43-fwcutter 100.000000
2010-09-27 17:23:45,813 DEBUG: Selecting previously deselected package b43-fwcutter.
(Reading database ... 127402 files and directories currently installed.)
Unpacking b43-fwcutter (from .../b43-fwcutter_013-2_amd64.deb) ...
Processing triggers for man-db ...
Setting up b43-fwcutter (1:013-2) ...

2010-09-27 17:23:46,069 DEBUG: unbind/rebind on driver /sys/module/b43/drivers/ssb:b43: device ssb0:0
ubuntu@ubuntu:/var/log$ 2010-09-27 17:23:07,612 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
bash: syntax error near unexpected token `('
ubuntu@ubuntu:/var/log$ 2010-09-27 17:23:07,670 DEBUG: nvidia_current is not the alternative in use
2010-09-27 17:23:07,612 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-09-27 17:23:07,670 DEBUG: nvidia_current is not the alternative in use
2010-09-27 17:23:09,346 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-09-27 17:23:10,106 DEBUG: nvidia_current is not the alternative in use
201010-09-27 17:23:07,670 DEBUG: nvidia_current is not the alternative in use
2010-09-27 17:23:09,346 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-09-27 17:23:10,106 DEBUG: nvidia_current is not the alternative in use
2012010-09-27: command not found
ubuntu@ubuntu:/var/log$ 2010-09-27 17:23:09,346 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
bash: syntax error near unexpected token `('
ubuntu@ubuntu:/var/log$ 2010-09-27 17:23:10,106 DEBUG: nvidia_current is not the alternative in use
2010-09-27: command not found
ubuntu@ubuntu:/var/log$ 2010-09-27 17:23:11,480 DEBUG: handler firmware:b43 previously unseen
2010-09-27: command not found
ubuntu@ubuntu:/var/log$ 2010-09-27 17:23:11,576 DEBUG: handler kmod:wl previously unseen
2010-09-27: command not found
ubuntu@ubuntu:/var/log$ 2010-09-27 17:23:11,577 DEBUG: handler xorg:nvidia_current previously unseen
2010-09-27: command not found
ubuntu@ubuntu:/var/log$ 2010-09-27 17:23:11,666 DEBUG: writing back check cache /var/cache/jockey/check
010-09-27 17:23:07,670 DEBUG: nvidia_current is not the alternative in use
2010-09-27 17:23:09,346 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-09-27 17:23:10,106 DEBUG: nvidia_current is not the alternative in use
2012010-09-27: command not found
ubuntu@ubuntu:/var/log$ 2010-09-27 17:23:11,753 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
bash: syntax error near unexpected token `('
ubuntu@ubuntu:/var/log$ 2010-09-27 17:23:11,774 DEBUG: nvidia_current is not the alternative in use
2010-09-27: command not found
ubuntu@ubuntu:/var/log$ 2010-09-27 17:23:12,036 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
bash: syntax error near unexpected token `('
ubuntu@ubuntu:/var/log$ 2010-09-27 17:23:26,964 DEBUG: Installing package: b43-fwcutter
2010-09-27: command not found
ubuntu@ubuntu:/var/log$ 2010-09-27 17:23:32,514 DEBUG: install progress statusChange dpkg-exec 0.000000
2010-09-27: command not found
ubuntu@ubuntu:/var/log$ 2010-09-27 17:23:41,204 DEBUG: install progress statusChange b43-fwcutter 0.000000
2010-09-27: command not found
ubuntu@ubuntu:/var/log$ 2010-09-27 17:23:41,204 DEBUG: install progress statusChange b43-fwcutter 20.000000
2010-09-27: command not found
ubuntu@ubuntu:/var/log$ 2010-09-27 17:23:41,737 DEBUG: install progress statusChange b43-fwcutter 40.000000
2010-09-27: command not found
ubuntu@ubuntu:/var/log$ 2010-09-27 17:23:41,741 DEBUG: install progress statusChange b43-fwcutter 60.000000
2010-09-27: command not found
ubuntu@ubuntu:/var/log$ 2010-02010-09-27 17:23:07,612 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
bash: syntax error near unexpected token `('
ubuntu@ubuntu:/var/log$ 2010-09-27 17:23:07,670 DEBUG: nvidia_current is not the alternative in use
2010-09-27: command not found
ubuntu@ubuntu:/var/log$ 2010-09-27 17:23:09,346 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
bash: syntax error near unexpected token `('
ubuntu@ubuntu:/var/log$ 2010-09-27 17:23:10,106 DEBUG: nvidia_current is not the alternative in use
2010-09-27 17:23:07,612 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-09-27 17:23:07,670 DEBUG: nvidia_current is not the alternative in use
2010-09-27 17:23:09,346 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-09-27 17:23:10,106 DEBUG: nvidia_current is not the alternative in use
2010-09-27 17:23:11,480 DEBUG: handler firmware:b43 previously unseen
2010-09-27 17:23:11,576 DEBUG: handler kmod:wl previously unseen
2010-09-27 17:23:11,577 DEBUG: handler xorg:nvidia_current previously unseen
2010-09-27 17:23:11,666 DEBUG: writing back check cache /var/cache/jockey/check
2010-09-27 17:23:11,753 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-09-27 17:23:11,774 DEBUG: nvidia_current is not the alternative in use
2010-09-27 17:23:12,036 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-09-27 17:23:26,964 DEBUG: Installing package: b43-fwcutter
2010-09-27 17:23:32,514 DEBUG: install progress statusChange dpkg-exec 0.000000
2010-09-27 17:23:41,204 DEBUG: install progress statusChange b43-fwcutter 0.000000
2010-09-27 17:23:41,204 DEBUG: install progress statusChange b43-fwcutter 20.000000
2010-09-27 17:23:41,737 DEBUG: install progress statusChange b43-fwcutter 40.000000
2010-09-27 17:23:41,741 DEBUG: install progress statusChange b43-fwcutter 60.000000
2010-02010-09-27: command not found
ubuntu@ubuntu:/var/log$ 201010-09-27 17:23:07,670 DEBUG: nvidia_current is not the alternative in use
201010-09-27: command not found
ubuntu@ubuntu:/var/log$ 2010-09-27 17:23:09,346 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
bash: syntax error near unexpected token `('
ubuntu@ubuntu:/var/log$ 2010-09-27 17:23:10,106 DEBUG: nvidia_current is not the alternative in use
2010-09-27: command not found
ubuntu@ubuntu:/var/log$ 201010-09-27 17:23:07,670 DEBUG: nvidia_current is not the alternative in use
201010-09-27: command not found
ubuntu@ubuntu:/var/log$ 2010-09-27 17:23:09,346 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
bash: syntax error near unexpected token `('
ubuntu@ubuntu:/var/log$ 2010-09-27 17:23:10,106 DEBUG: nvidia_current is not the alternative in use
2010-09-27: command not found
ubuntu@ubuntu:/var/log$ 2012010-09-27 17:23:07,612 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
bash: syntax error near unexpected token `('
ubuntu@ubuntu:/var/log$ 2010-09-27 17:23:07,670 DEBUG: nvidia_current is not the alternative in use
2010-09-27: command not found
ubuntu@ubuntu:/var/log$ 2010-09-27 17:23:09,346 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
bash: syntax error near unexpected token `('
ubuntu@ubuntu:/var/log$ 2010-09-27 17:23:10,106 DEBUG: nvidia_current is not the alternative in use
2010-09-27: command not found
ubuntu@ubuntu:/var/log$ 2010-09-27 17:23:11,480 DEBUG: handler firmware:b43 previously unseen
2010-09-27: command not found
ubuntu@ubuntu:/var/log$ 2010-09-27 17:23:11,576 DEBUG: handler kmod:wl previously unseen
2010-09-27: command not found
ubuntu@ubuntu:/var/log$ 2010-09-27 17:23:11,577 DEBUG: handler xorg:nvidia_current previously unseen
2010-09-27: command not found
ubuntu@ubuntu:/var/log$ 2010-09-27 17:23:11,666 DEBUG: writing back check cache /var/cache/jockey/check
2010-09-27: command not found
ubuntu@ubuntu:/var/log$ 2010-09-27 17:23:11,753 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
bash: syntax error near unexpected token `('
ubuntu@ubuntu:/var/log$ 2010-09-27 17:23:11,774 DEBUG: nvidia_current is not the alternative in use
2010-09-27: command not found
ubuntu@ubuntu:/var/log$ 2010-09-27 17:23:12,036 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
bash: syntax error near unexpected token `('
ubuntu@ubuntu:/var/log$ 2010-09-27 17:23:26,964 DEBUG: Installing package: b43-fwcutter
2010-09-27: command not found
ubuntu@ubuntu:/var/log$ 2010-09-27 17:23:32,514 DEBUG: install progress statusChange dpkg-exec 0.000000
2010-09-27: command not found
ubuntu@ubuntu:/var/log$ 2010-09-27 17:23:41,204 DEBUG: install progress statusChange b43-fwcutter 0.000000
2010-09-27: command not found
ubuntu@ubuntu:/var/log$ 2010-09-27 17:23:41,204 DEBUG: install progress statusChange b43-fwcutter 20.000000
2010-09-27: command not found
ubuntu@ubuntu:/var/log$ 2010-09-27 17:23:41,737 DEBUG: install progress statusChange b43-fwcutter 40.000000
2010-09-27: command not found
ubuntu@ubuntu:/var/log$ 2010-09-27 17:23:41,741 DEBUG: install progress statusChange b43-fwcutter 60.000000
2010-09-27: command not found
ubuntu@ubuntu:/var/log$ 2010-02010-09-27 17:23:07,612 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
bash: syntax error near unexpected token `('
ubuntu@ubuntu:/var/log$ 2010-09-27 17:23:07,670 DEBUG: nvidia_current is not the alternative in use
2010-09-27: command not found
ubuntu@ubuntu:/var/log$ 2010-09-27 17:23:09,346 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
bash: syntax error near unexpected token `('
ubuntu@ubuntu:/var/log$ 2010-09-27 17:23:10,106 DEBUG: nvidia_current is not the alternative in use
0-09-27 17:23:41,204 DEBUG: install progress statusChange b43-fwcutter 20.000000
2010-09-27 17:23:41,737 DEBUG: install progress statusChange b43-fwcutter 40.000000
20102010-09-27: command not found
ubuntu@ubuntu:/var/log$ 2010-09-27 17:23:11,480 DEBUG: handler firmware:b43 previously unseen
2010-09-27: command not found
ubuntu@ubuntu:/var/log$ 2010-09-27 17:23:11,576 DEBUG: handler kmod:wl previously unseen
2010-09-27: command not found
ubuntu@ubuntu:/var/log$ 2010-09-27 17:23:11,577 DEBUG: handler xorg:nvidia_current previously unseen
2010-09-27: command not found
ubuntu@ubuntu:/var/log$ 2010-09-27 17:23:11,666 DEBUG: writing back check cache /var/cache/jockey/check
2010-09-27: command not found
ubuntu@ubuntu:/var/log$ 2010-09-27 17:23:11,753 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
bash: syntax error near unexpected token `('
ubuntu@ubuntu:/var/log$ 2010-09-27 17:23:11,774 DEBUG: nvidia_current is not the alternative in use
2010-09-27: command not found
ubuntu@ubuntu:/var/log$ 2010-09-27 17:23:12,036 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
bash: syntax error near unexpected token `('https://help.ubuntu.com/
ubuntu@ubuntu:/var/log$ 2010-09-27 17:23:26,964 DEBUG: Installing package: b43-fwcutter
2010-09-27: command not found
ubuntu@ubuntu:/var/log$ 2010-09-27 17:23:32,514 DEBUG: install progress statusChange dpkg-exec 0.000000
2010-09-27: command not found
ubuhttps://help.ubuntu.com/ntu@ubuntu:/var/log$ 2010-09-27 17:23:41,204 DEBUG: install progress statusChange b43-fwcutter 0.000000
2010-09-27: command not found
ubuntu@ubuntu:/var/log$ 2010-09-27 17:23:41,204 DEBUG: install progress statusChange b43-fwcutter 20.000000
2010-09-27: command not found
ubuntu@ubuntu:/var/log$ 2010-09-27 17:23:41,737 DEBUG: install progress statusChange b43-fwcutter 40.000000
2010-09-27: command not found
ubuntu@ubuntu:/var/log$ 2010

```

I can't decipher why the B43 driver failed to install. Does this mean anything to you guys?

Thanks for all the help :)

---

### Post by locoHost on 2010-09-27
Also, in case it matters, this machine is running Maverick. I doubt that matters, but I thought I'd mention.

---

### Post by lukeiamyourfather on 2010-09-27
> **locoHost said:**
> Also, in case it matters, this machine is running Maverick. I doubt that matters, but I thought I'd mention.

Have you tried the Lucid live disc?

---

### Post by locoHost on 2010-09-30
> **lukeiamyourfather said:**
> Have you tried the Lucid live disc?

Just tried the Lucid 10.04 Live CD. In hardware drivers I enabled the Broadcom B43 driver, the front blue light still does not come on. Ifconfig shows no wlan0, just the wired connection and loopback.

Should the blue light come on immediately after installing the B43 driver or would I need to restart? Restarting won't really work with the Live CD.

---

### Post by gba3 on 2010-11-08
Have you solved the problem?

I have the same issue.

My problems started when I experimented with "suspend laptop" while going to the other place with wifi swiched off. At the other end laptop didn't wake up properly and I had to restart it. Since then I have tried both b43 anf STA drivers - no luck. And the most interesting is that with HW switch on it says "device not ready" and I can disable it by switching HW off but then again by switching it on it can't enable the device.

I don't know it matters but when I type in terminal:
rfkill list

It responds:
0: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
1: hp-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: no

---

### Post by wells24 on 2010-11-23
Same problem for me juste installing mavrick

kill switch stuck to off
I have tryed to reset with bios batery and did noting good

---

### Post by kobayashison on 2010-12-07
Same problem with a DV2000, maverick and last kernel (2.6.35-23-generic-pae).
It worked in the past but not anymore since a week, probably is the same problem with suspension that posted gba3.

Anyway it works with the older kernel 2.6.32-25-generic-pae and windows Vista. So is not an hardware failure.

---

### Post by kobayashison on 2010-12-07
probably this is the opened bug issue:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/616076]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/616076")

---

### Post by kobayashison on 2010-12-10
Now it works again without having to "rfkill unblock all" but I don't know if is for the kernel upgrade to 2.6.35-24-generic-pae or other reasons.

---

### Post by jw1949 on 2011-02-28
THX, the rfkill unblock wifi worked for me on 10.10 kernel 2.6.35-25-generic.

This board is wonderful !

---

### Post by kobayashison on 2011-03-01
Now with 2.6.35-27-generic-pae kernel works only if at the boot the switch was on. Booting with the switch off, is not possible to turn the wifi on even using ```
rfkill unblock all
```

---

### Post by HeWhoE on 2011-03-09
```
rfkill unblock all
```
Brilliant! Thank you! Not being able to get my wireless to work on my dv2000 was driving my nuts!

---

### Post by the_original_billq on 2011-05-21
Brilliant!  Thanks so much!  I've seen 100's of posts on the this topic on HP's site, the common answer there was to return the laptop for repair:-)

When I try to explain why Linux should be the OS of choice, folks just don't get it...

---

