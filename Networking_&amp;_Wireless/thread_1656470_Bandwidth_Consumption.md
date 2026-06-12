---
title: "Bandwidth Consumption"
date: 2010-12-30
forum: Networking &amp; Wireless
---

### Post by Zeterai on 2010-12-30
This is an odd problem, and I haven't used Ubuntu personally for a few years so I'm a bit rusty with troubleshooting for it. 

There are three computers in our home. Two laptops running Windows 7 Home Premium x64, connecting to our Linksys WRT610N router, one on a wireless N band, and the other G. The third is a desktop running Ubuntu's latest version, and hooked into one of the router's ethernet ports.

Now, when the wired PC is shut off, or browsing online sparingly, the two laptops have absolutely no problems connecting to the internet and router. However, when the Ubuntu PC is running an online game, streaming video off YouTube, or even just using flash heavily, the laptop connections shut off immediately. They're able to connect to the router, but not able to access the configuration settings via the standard 192.168.1.1 method, nor are they able to connect to the internet. As soon as the wired PC stops intensively accessing the internet, the wireless signal resumes.

It's one of two problems. Either the router itself, or the ubuntu configuration. The very day that the problem arose some months ago, the one who owns the Ubuntu box was tinkering with his network settings trying to boost his speed. However, he does not know enough of the system to fully comprehend what he may have done. I'm nearly certain that something found online was entered into a terminal to cause this, but I do not know how it was done, or what could resolve it.

The short version I suppose, is the question of whether or not something can be done via terminal to let a ubuntu box take full ownership of a router's bandwidth. Our connection is 15Mbps high speed cable, split among three computers, there should be plenty of bandwidth to go around.

---

### Post by PatchesTheCaveman on 2010-12-31
Hi Zeterai!  It's very unlikely that someone could do anything in Ubuntu that could make it hog a 15 Mbps link.

However, someone could have changed the router settings such that the other machines have trouble accessing the network.  This seems especially likely since the other computers are also being prevented access to the router configuration.

I would strongly suggest you do a hard reset of your router, resetting it's configuration to a default state.  Locate a little reset button somewhere, usually on the back of it.  They're usually the kind you have to push with a pen or pencil.  Unplug your router.  Hold the reset button.  Plug it back in.  Keep holding the reset button for 30 seconds, then release it.

If your router reset successfully, it's name will have changed back to the default and any password on it will have cleared.  You can now access the router configuration to reset its name and password.  I also strongly suggest you password protect the router configuration to prevent anyone from tampering with it in the future.

If the name and password stay, you didn't reset the router.  If you have the manual, try and find instructions on how to "hard reset" it.  If you can't, let me know the model router you have and I can figure it out for you.

---

### Post by Zeterai on 2010-12-31
I did hard reset it, several times. It resets each time to full factory default, and I've set the network back up in each case. Power cycling did not help the issue either. I've attempted to set up static IPs for each of the laptops, as well as checked the port settings. There is absolutely no reason the router would be behaving this way, aside from a hardware fault. However, I don't have another router to test that with.

What makes me consider the Ubuntu config as the problem is that the very instant that the problems arose, the ubuntu user mentioned how he had just tried something on his computer. The timing is too close to be coincidental.

---

### Post by Zeterai on 2011-01-02
Bit more information. I connected one of the laptops to the router on the same ethernet port, with the same ethernet cable. It's able to browse the internet with no disruption to the other laptop, meaning it only occurs when the desktop running ubuntu is hooked up by a wired connection. It's definately something with how the net config for it was set up and not a router problem. I just don't know what he possibly could have done to cause it.

---

### Post by Boondoklife on 2011-01-02
Easy way to test it would be to try and boot from a livecd and browse. If it works, then it sounds like they pooched something.

Make sure the user browses the same sites as usual. You could also check the system monitor to see what the traffic looks like. If they have a p2p app running wideopen then it can and will bring a router to its knees.

---

### Post by Zeterai on 2011-02-23
It's been a bit of time, and I've attempted a number of fixes. Changing the subnet mask worked sporadically, but eventually ceased to be effective. Last night, however, I installed a brand new Linksys E2000N router. The problem appeared to cease, but began to occur again this morning, the instant the wired ubuntu box was turned on. Very occasionally, rebooting the router solves the issue for an hour or two, but the issue resumes soon after, and repeated reboots do nothing. I assigned static IP addresses to each work station, with no resolution.

Booting from a live CD seemed to stop the problem, but because Flash isn't installed in the live CD, I can't be 100% certain that's not what's causing it. It's definately a problem with the way ubuntu is configured on the wired box though, every other portion of the network has been removed or replaced. No P2P applications are active, and the network configuration panel seems normal. I'm at a complete loss for what's happening. Formatting and reinstalling the O/S isn't a viable option, unfortunately. Also of note is that plugging directly into the router doesn't result in a solution either; when the ubuntu box is online, absolutely nothing else is able to connect to the router or internet. Could it be manipulating the DHCP or DNS settings somehow?

---

### Post by Zeterai on 2011-02-24
Attempted to restrict the router's client lease time to just 30 minutes, no solution. It's becoming increasingly irritating just how resistant to fixing this problem is.

---

### Post by Zeterai on 2011-02-25
Any help at all? I really hate to post consecutively without any new information, but the thread keeps getting pushed down the list.

---

### Post by Boondoklife on 2011-02-25
Short of coming to your home and hacking it out with your computer, there is not a way to tell you what the issue is (No that was not an offer =P). I can tell you that your issue has got to be software related as the livecd shows your hardware is just fine. You could try to compare the modules that are loaded by the livecd and ubuntu; this would ensure it is not a driver issue.

I noticed you mentioned flash, what does that have to do with the topic at hand? If you are trying to test bandwidth then you might want to check this out [[Link]("http://webcache.googleusercontent.com/search?q=cache:siIaY_iL6E4J:www.linuxquestions.org/questions/linux-newbie-8/command-line-bandwidth-test-630270/+linux+test+bandwidth+commandline&cd=1&hl=en&ct=clnk&gl=us&client=ubuntu&source=www.google.com")]

My suggestion would be to just backup your data and wipe the box, then reinstall ubuntu and see if it works out of the box.

---

