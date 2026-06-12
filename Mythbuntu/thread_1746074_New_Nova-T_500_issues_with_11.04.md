---
title: "New Nova-T 500 issues with 11.04"
date: 2011-05-01
forum: Mythbuntu
---

### Post by bruk on 2011-05-01
I've just gone through a failed upgrade to 11.04, which prompted a backup and completely new install of mythbuntu. I've fixed up all the stuff to work that's supposed to work out of the box in the usual way. Unfortunately I'm now encountering a new issue with my Nova-T card that I haven't seen before.

Now ordinarily I'd use the 1.10 fw for the card (1.20 had never properly worked for me, at all), correct the input device being used so that all of the buttons are available, and then put my own preferences in the .mythtv/lircrc file. This would give me a fully working remote, that would repeat presses when you held buttons down.

For some reason though, 1.10 is now causing buffered input, i.e. when you press a button, it's the one you pressed before it that is reported (in irw, etc.). So I opted to try out 1.20 to see if there's been any improvements. It all seemed good, no buffered input, however, response time is now pretty bad. There appears to be between half and one second between a button press being reported.

Obviously, a slow non-repeating remote is better than a completely screwed one, but ideally, I'd like to have the full speed one back.

I've no idea what's actually changed regarding lirc or any kernel level stuff, which is where i'm assuming the problem is, as the card firmware has not changed in a couple of years.

Anyone?

---

### Post by rtrevor on 2011-05-04
Same issue here - the remote works fine but has a ~1.5 second delay after pressing each button. This is with lirc configured to use the Hauppauge remote through lirc (selecting the remote as the input device in dpkg-reconfigure lirc)

Apparently this is the legacy way to do things and the /dev/input/eventX input layer is the future, as per [http://wilsonet.com/?page_id=95]("http://wilsonet.com/?page_id=95").

So when I dpkg-reconfigure lirc to use the Linux input layer (/dev/input/eventX), and regenerate the lircrc file w/ mythbuntu lircrc regenerator as the key bindings are all different, it is now much quicker to respond but every button press is registered twice.

There is a workaround mentioned in this thread but it doesn't work for me: [http://ubuntuforums.org/showthread.php?t=1745463]("http://ubuntuforums.org/showthread.php?t=1745463") 

Worth trying as it should be much more responsive if you can find a solution to the double keypresses?

---

### Post by bruk on 2011-05-05
Thanks for pointing me in the right direction.

Firstly, wow, just wow, this is without a doubt the most shockingly poor system change I've ever seen. It's not just the fact that the myth wizard lets you choose a remote that has never worked out of the box, but now that you can't even get it working using the original tried and tested way. The working alternative is completely different from anything, and it isn't documented clearly anywhere, I mean even by typical linux standards it's bad, borderline Vogon earth destroying plans bad.

Anyway, rant over. Onto the solution.

There's two problems, well, one problem that'll cause another one if you do what common sense tells you to do.

The devinput/lircd.conf.devinput that is in your /etc/lirc/hardware.conf contains two remote setups, one normal, and one "legacy 32-bit". This is the first/main problem, because if you go ahead and generate the mythtv lircrc automatically, it parses this file and generates two duplicate sets of controls (the second problem). Which, tada, gives you two of every input.

So in short:

Delete the second remote in the devinput/lircd.conf.devinput file, and either auto generate the lircrc file, or edit it and find where KEY_0 appears again and delete it and everything after it.

My remote now works properly, I just need to go edit the specific function buttons, guide isn't mapped for example. What's most annoying is that I'd written off the remote as an ignored bit of hardware that was never going to get fixed, and ordered a swanky new MCE remote, but hey ho, at least I'll have more buttons.

---

### Post by rtrevor on 2011-05-09
Thanks, that fixed everything for me as well, all working now.

I created a bug report for the duplicate lircrc entries:

[https://bugs.launchpad.net/ubuntu/+source/mythbuntu-lirc-generator/+bug/779835](https://bugs.launchpad.net/ubuntu/+source/mythbuntu-lirc-generator/+bug/779835)

---

### Post by SteveCpl on 2011-09-18
> **bruk said:**
> Thanks for pointing me in the right direction.

Firstly, wow, just wow, this is without a doubt the most shockingly poor system change I've ever seen. It's not just the fact that the myth wizard lets you choose a remote that has never worked out of the box, but now that you can't even get it working using the original tried and tested way. The working alternative is completely different from anything, and it isn't documented clearly anywhere, I mean even by typical linux standards it's bad, borderline Vogon earth destroying plans bad.



I realise this post is a few months old now, but I have the exact problem initiallly described. using 1.10 of the firmware gives buffered response, and 1.20 gives the slow/delayed response.

Could you describe what you did to get from this to the repeated response? I've tried running dpkg-reconfigure lirc, selecting the options of:

Remote control configuration: Hauppauge Nova-T 500
IR transmitter, if present: None
Custom event interface for your dev/input device: /dev/input/by-path/pci-0000:04:02.2-event-ir 

but it makes no difference, I still have the very slow delayed single response.

Any help greatly appreciated!

---

