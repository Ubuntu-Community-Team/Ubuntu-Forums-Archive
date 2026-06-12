---
title: "How to disable internet / networking capabilities"
date: 2010-01-10
forum: Networking &amp; Wireless
---

### Post by epictetus on 2010-01-10
(Note:  Long scenario description---skip to the end of this paragraph for reason for posting here.)  I suffer enormously from net addiction (as well as gaming addiction and related behavioural maladies).  I've had revelatory success in controlling my time online---and, in general, in front of a screen with unproductive applications---by locking my monitor's power cord into an Ems PowerCop (the key to which I keep at work).  Writing and journaling, I do on an AlphaSmart Neo.  However, I could really use a tool to allow me to edit and typeset my writing (and only those tasks).  I'm considering buying an ultra-low cost netbook (specifically, the Cherrypal Africa with Linux).  Despite the internet problem, I want a netbook because it's the cheapest way to keep the display power fully dependent and integrated with the machine---I can't have something that will allow a simple means of working around the Ems PowerCop.  Also, since it lacks an optical disk drive (and since I'll be keeping my usb drives at work) there will not be an easy way to reinstall the operating system.  However, before I buy anything, I need to know that, after installing/configuring all of my preferred settings for vim and La/Xetex, there is a way that I can cripple the netbook and all of its applications so that no internet access is possible.

The Cherrypal Africa can come with either Ubuntu, Debian, or its own Linux blend, Green Maraschino.  If it ends up being either Ubuntu or Debian, what can I do that will irreversibly (at least, from a software level---a hardware level would probably require damaging the usb ports, which I don't want to do) disable its ability to try to communicate with the internet (including the software repositories)?  I'm hoping for a particular system file that I can delete rather than the addition of a command somewhere that would be easy for me to undo when I'm bored out of my mind and want to see what Wikipedia has to say about the glycemic index.

I apologize for the length of this entry.  Any help/advice would be greatly appreciated.

---

### Post by MeKino on 2010-01-11
You can turn on or turn off Internet connectivity simply by right-clicking on the "connection" icon somewhere on the right of the top tool-bar.

---

### Post by epictetus on 2010-01-11
That won't do anything permanent.  I've tried uninstalling some of the packages I found by searching for `net' in Synaptic, but they didn't help, aside from removing an extra utility or two---still just as easy to get on Firefox or install new programs through Synaptic.  After more experimentation with removing various net-related packages but still being able to connect to the internet, I tried just marking everything for complete removal in the Networking section of Synaptic.  I hadn't realized it would do this, but it looked like it was basically uninstalling the entire operating system.

Bee tea duh bowl ewe, I'm testing all this on a Sun Virtualbox machine.  I'd think I'd still be able to disable networking capabilities on that in a similar manner to a full system, correct?  I'd do this with a system running off a usb stick if that weren't so much slower and still somewhat buggy (in my recent experience).

---

### Post by changingstate on 2010-01-11
I guess you erase the kernel modules ( drivers ) the machine uses to control the networking hardware from around /lib/modules/<kernel-version>/<path with whichever part of ./net they've been popped in>.

sudo lshw -C network will tell you which drivers are in use under the module option of the configuration line. 

You can easily repair this by reinstalling the kernel-image package, but with no networking and if you've erased all the cached .deb files in /var/cache/apt, that'd mean you'd need to physically transport the package to the machine on pendrive or CD or similar.

Unless anyone has a better idea.

P.S. By using this idea, you indemnify me against legal proceedings if you break your netbook OS. Thank you. :D

---

### Post by dbott67 on 2010-01-12
You could always edit the **/etc/network/interfaces** file and remove the gateway entry.  Without a gateway, there's no way to access the internet.

Then, set the file to be immutable:

```
chattr +i /etc/network/interfaces
```

Once the file is immutable, it cannot be changed (unless you remove the flag).

---

### Post by chili555 on 2010-01-12
> I guess you erase the kernel modules ( drivers ) the machine uses to control the networking hardware from around /lib/modules/<kernel-version>/<path with whichever part of ./net they've been popped in>.

sudo lshw -C network will tell you which drivers are in use under the module option of the configuration line.

You can easily repair this by reinstalling the kernel-image package, but with no networking and if you've erased all the cached .deb files in /var/cache/apt, that'd mean you'd need to physically transport the package to the machine on pendrive or CD or similar..ko-rrect! (Just a little linux joke, there; drivers are .ko files!) Just be sure you only remove the networking drivers, under *sudo lshw -C network*. Do NOT remove video drivers, sound drivers, etc. This would probably so it:```
sudo rm -rf /lib/modules/`uname -r`/kernel/drivers/net/*
```DISCLAIMER!!! Any and every 'rm -rf' command is very, very dangerous. If you are not sure, don't do it. I accept no responsibility for anyone's lack of judgement.

However, I will be very interested in the outcome!

---

### Post by epictetus on 2010-01-12
Thanks for some of the quite awesome-looking suggestions!  And of course, I'm more than willing to supply you with any water you require to wash your hands of what might result.

I'll test this stuff out on virtual machines over the next few days.  I've heard about a number of people having trouble with ordering the Cherrypal Africa, so I'm evaluating other options.  But my next pay day is this week, and I'm thinking my love of new gadgets might gang up on me with my lowered self-control and the convenience of online retail.

It might be awhile from now, but I'll post the results.

Thanks again for the help.

*Update* (*2011 02 12*): *Ended up getting a refurbished Asus Eee Pc netbook for $138 off of Amazon. Installed Linux Mint on it. Everything works great except for the webcam* (*which I wasn't planning to use*) *and possibly the mic* (*not sure...haven't tested it*). *Note*:* Be careful with the Asus Eee Pc system restore discs: Thinking that it would work similarly to a Linux LiveCD, I tried booting it on my main tower. It deleted my partition tables and wiped my external hard drive.* :(

---

### Post by hugmenot on 2010-01-18
Anything that is reversible is bound to be reverted by yourself, if you are really addicted.

I knew a friend who could not focus on his thesis. He took a wire cutter and cut the cat5 cable.

You can also open the netbook, remove the wireless mini-PCI card and give it to someone.

Or you remove yourself from sudoers and give root access to someone else. Your wife, mom, girfriend, etc.

---

### Post by epictetus on 2011-02-12
Sorry it's been so long since I initially requested assistance in crippling my new netbook. My justification is that I haven't been on the internet so much anymore. (Success! I've found myself spending a lot of time having fun in vim: poking around in Context, Ruby, and Python as well as modifying/setting up a general text typing shorthand system.)

I really appreciated all of the input but am not sure how much the suggestions worked. I initially tried one or two but still had network connectivity. It's possible that one of them might have worked but I got frustrated trying to kill the internet and started deleting network-looking drivers haphazardly.

What *consistently* works and is easy to do is to open the Network Connections manager (or whatever it's called---it's the icon that sits in the top panel and tells you when there are wireless networks available. I'm typing this on the crippled netbook and so cannot check what it's official name is at the moment.) and delete all of the network connections, and then open up Synaptic and delete network-manager and gnome-network-manager (if I remember correctly---again, I'm not positive on those names).

That really worked. When I need to install software, I do the whole package download script thing with wget. Fortunately, installing stuff this way is enough of a hassle that I'm really not tempted to do it to re-install network-manager. (The reason I wanted to cripple this netbook is adhd + internet addiction. With adhd making me bad at planning ahead or navigating through multi-step processes, it's good at detering me from generating the package download script for network-manager.)

There have been a few times that I've re-enabled network connectivity for travel or something like that. The result of doing that ends up being a good motivation for re-crippling and a reminder of how much more I am able to get done without constant distraction.

Anyway, thanks for all the help! Stuff like this is what really makes me love Linux.

---

