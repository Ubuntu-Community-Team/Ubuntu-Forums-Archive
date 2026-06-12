---
title: "MythTV Lirc"
date: 2008-07-03
forum: Multimedia Software
---

### Post by rxtx on 2008-07-03
Hi there, I have posted this question a few times, but with no reply.

I'm trying to get my Hauppauge remote working with lirc in Myth. If I bring up lircd with the following command BEFORE running Myth, then everything is well.

```
sudo /usr/sbin/lircd -H dev/input -d /dev/input/event4 -n
```

I am trying desperately to run this on boot so it stays active and Myth can hook onto it, just as above when it is run in a terminal window. Adding to .gnomerc isn't helping matters at all.

I'm really reaching the point of despair with this.

---

### Post by paulg on 2008-07-03
When you install lirc it should be launching at startup. What's more likely happening is that it is starting and either not loading kernel modules you need, or you have a conflict with another kernel module loading that is interfering with the lirc module, or perhaps isn't properly configured for your hardware. 

Sorry, I am not very familiar with your hardware. Have you checked the wiki at mythtv.org? There is a lot of information there on specific hardware. The Hauppauge cards are well documented there.

If lirc is configured properly you can start/stop/restart it from here (replace restart with whatever you're trying to do):

sudo /etc/init.d/lircd restart

---

### Post by rxtx on 2008-07-03
Thanks for the reply. I'm using a DVB Nova-T PCI card- it works flawlessly apart from this.

lirc seems to be running fine, and will stop start and restart without any problems, but Myth only seems to respond to the FULL set of keys after the above command is launched, just running the module at boot doesn't seem to do the trick. Running Myth without this command only gives cursor key and "OK" button functionality.

For the most part, I have been using [this]("http://parker1.co.uk/mythtv_ubuntu2.php") nifty guide to aid me, but am unable to find anything further which can help :(

I'll take a look at the lirc section of the wiki (which I seemed to have missed!) and will faff around some more tomorrow.

---

