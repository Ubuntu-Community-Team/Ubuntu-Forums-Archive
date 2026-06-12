---
title: "no network on ununtu 12.10 after upgrade"
date: 2012-10-21
forum: Networking &amp; Wireless
---

### Post by wazza75 on 2012-10-21
I have no networking on my machine after upgrading to 12.10. I can't even ping my router. ping localhost works however. I'm not sure where to even begin in fixing this. Any pointers on which log files I should check etc would be very helpful.

Thanks

Warwick

---

### Post by wazza75 on 2012-10-21
Also, restarting the network with /etc/init.d/networking restart kills unity.

---

### Post by varunendra on 2012-10-22
Please run the following command to download and run a script (courtesy dave, wildman & others) that will create a summary of your wireless settings (just copy-paste the command in a terminal):
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will create a file named "netinfo.txt" in your home directory. Copy-paste its contents here, or attach the file itself.

---

### Post by xenocide702 on 2012-11-16
I am having (by the sounds of it) exactly the same issue. Some time after running an update I lost all traces of my network card, restarting networking results in the desktop manager crashing. I ran the bootable installer (the one I just used to install) just to be sure it wasn't a hardware issue. Everything worked fine in the bootable instance.

I can run the script if you'd like, but this in my case I'm on a wired connection with no wireless device installed. Also, being that I have no working network connection, I'll have to download the file on another computer and copy it over.

Some searching turned up [<this link>](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/876495) which sounds like our issue, but there hasn't been any recent activity on that page.

I apologize if the proper educate here would be to start a new thread. I will happily do so if that's the case.

---

### Post by varunendra on 2012-11-16
> **xenocide702 said:**
> I apologize if the proper educate here would be to start a new thread. I will happily do so if that's the case.
Not such a big deal, but I'd recommend you to do so.
First - it being a fresh thread, you'll have more chance of getting quick and possibly better replies; Second - you'll be able to mark it as [Solved] if it becomes the case - it really helps us and others searching for solutions to specific problems.

Accordingly, please start a new thread of your own in Networking & Wireless section and besides a detailed description of the problem, post the outputs of following there -
```
lspci -nnk | grep -iA2 net
lsmod
nm-tool
```

You may then post a link to it here in your next post so that those of us who may be interested can follow it.

Good luck !

---

