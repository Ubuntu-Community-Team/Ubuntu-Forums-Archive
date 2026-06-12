---
title: "wireless disabled by hardware switch 10.04"
date: 2012-05-27
forum: Networking &amp; Wireless
---

### Post by lmchristy on 2012-05-27
Hi there.  I am running 10.04 on a HP Pavilion dv1000, and I am trying to get my USB Wireless Adapter to work.  I know nothing about Linux, and I'm trying to help my husband out, who had his buddy install it on here and then he doesn't know how to help either.  I've installed the driver, but it's still saying Wireless is disabled through hardware switch.  I can follow directions really well, and really need some help.  We are at our wits end.  I've read other posts, but when it comes down to code, I have no idea how to read it.  I've finally just figured out how to get to the terminal, but I'm not sure what to do.  Please help!  Thank you for reading.

---

### Post by chili555 on 2012-05-27
Does your laptop have a hardware switch? Did you try to move it to ON? Is there an internal card that doesn't work?

In the terminal, please run and post:```
lsusb
rfkill list all
```Thanks.

---

### Post by lmchristy on 2012-05-27
Thank you!

There is a wireless button, but pushing it does nothing as far as I can tell.

Here is the result of lsub

rNo command 'lsub' found, did you mean:
 Command 'lsusb' from package 'usbutils' (main)
 Command 'qsub' from package 'torque-client' (universe)
 Command 'qsub' from package 'gridengine-client' (universe)
 Command 'qsub' from package 'torque-client-x11' (universe)
lsub: command not found

result of rfkill list all

r0: hp-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes
1: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: no

---

### Post by lmchristy on 2012-05-27
There is no wireless card, just a network card.

---

### Post by chili555 on 2012-05-27
> Here is the result of lsubI was asking for *lsu**s**b*. That is, list all the USB devices.

Please do:```
sudo modprobe -r hp-wmi
rfkill unblock all
rfkill list all
```Is there any improvement?

---

### Post by lmchristy on 2012-05-27
Oh Whops, here is the new stuff.


Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0bda:8176 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

I will try the new lines right now.

---

### Post by chili555 on 2012-05-27
> **lmchristy said:**
> There is no wireless card, just a network card.Do you mind if a cynical old doctor has a peek? Please post:```
lspci -nn | grep 0280
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by lmchristy on 2012-05-27
That worked!  I'm so happy.  Thank you so much!  WHEW!

---

### Post by lmchristy on 2012-05-27
If that hadn't worked, I certainly wouldn't have minded.  Again, sir, thank you so much.  I have been scouring the internet trying to figure it out.

---

### Post by chili555 on 2012-05-27
> **lmchristy said:**
> That worked!  I'm so happy.  Thank you so much!  WHEW!Any chance you'd like to write a quick configuration file and make it permanent?

May I just say:> 0bda:8176 Realtek Semiconductor Corp. > I've installed the driver,Pretty impressive! You can have a spot on Team Chili any time!

I'm still interested in the internal card; see my post above.

---

### Post by chili555 on 2012-05-27
> If that hadn't worked, I certainly wouldn't have minded.I would have minded; I hate to lose.

Any chance you'd like to write a quick configuration file and make it permanent?

---

### Post by lmchristy on 2012-05-27
Yes!  How would I do that?

---

### Post by chili555 on 2012-05-27
> **lmchristy said:**
> Yes!  How would I do that?LOL! I was pretty sure you'd come back eventually. We are going to blacklist hp-wmi so it doesn't ever load and block your wireless. Please open a terminal and we'll do it the kwik-n-EZ old-school command line way:```
sudo su
echo "blacklist hp-wmi" >> /etc/modprobe.d/blacklist.conf
exit
```You should be all set.

So you installed that driver? That's pretty complex stuff!

Please use thread tools at the top and mark Solved.

---

### Post by lmchristy on 2012-05-27
Well, when my husband rebooted his computer, and it lost the wireless again, I knew something was off.  

I had to do the driver myself because the install disk wouldn't run.  Plus, it wouldn't take the Linux driver, it would only work off the Windows XP driver.  I thought that was strange.  

I am a media specialist for a school district, so I am used to having to find my own answers to questions.  I put the code in, so I guess we'll know if it worked in a second!!

---

### Post by chili555 on 2012-05-27
> it would only work off the Windows XP driver. I thought that was strange. So you used ndiswrapper and the XP driver? ndiswrapper is designed and written to use the XP drivers and not otherwise. Still pretty advanced stuff.

So it's working OK now?

---

