---
title: "Can't connect to Bluetooth keyboard (Intrepid)"
date: 2008-12-20
forum: Networking &amp; Wireless
---

### Post by chrisinspace on 2008-12-20
I have searched this forum and others, but have not found a solution to my problem yet.  I was about to post this in a different thread, but realized it was probably off-topic.  In the other threads I found discussing bluetooth input devices, people can connect their device, but the connection drops after the machine goes to sleep or is reboot.  I can't even make my initial connection.

I have a bluetooth media keyboard with a built-in trackball and mouse buttons.  It's perfect for use in my living room with the Mythbuntu box hooked to the TV, but I can't get it to connect.  It worked under Edgy, Gutsy, and Hardy (all 32 bit), but will not work for me in 64 bit Intrepid. My Mythbuntu installation is running Gnome, not XFCE, though I have tried to pair in both desktop environments.  I can scan for devices using the Gnome GUI or hcitool in the terminal and detect it just fine, but it won't pair.  I got it to work by repeating the process over and over, but it only held on for a few minutes.  I have added its MAC in both the /etc/default/bluetooth and /etc/bluetooth/hcid.conf files, I have tried installing Blueman as suggested in another post, and I have tried using a different bluetooth adapter that I borrowed from work.  I don't know what else to do.  At this point, I'm considering a downgrade back to Hardy.  I really need my bluetooth keyboard to work because it's a pain running an HTPC with a corded keyboard/mouse.  

I also have a Dell Vostro 1310 laptop that dual-boots Intrepid 32 bit and Vista.  For testing purposes, I tried to pair the keyboard to both OS's on that machine.  I had the same problems in 32 bit Intrepid on the laptop, but it paired to my Windows installation in seconds.  I'm able to pair my Mythbuntu machine with other bluetooth devices (phone, laptop), just not the keyboard, so I don't think the problem is with my adapter.  I'm really confused.  Is it possible for a bluetooth *device* to not be Linux compatible?  I always took bluetooth to be a wireless standard.  If the adapter I'm using works and pairs to some devices, why not others?  In my mind, that's like having a wireless network adapter that works fine for pairing to one 802.11 device, but not another.

---

### Post by nkri on 2008-12-20
Many people are having this problem with Intrepid...I believe it's a kernel-related problem, since many people have upgraded and downgraded Bluez with little to no improvement:(

[_This_]("http://ubuntuforums.org/showthread.php?t=964139") is a thread dedicated to solving this problem, though we don't seem to be making much progress:mad:  A lot of people seem to be having the same problem as you: some of their Bluetooth hardware works, some doesn't, and there's not really any obvious pattern.

If you can't wait for this to be fixed in Intrepid, Hardy would probably be the best way to go, since Bluetooth worked fine in it:)

Oh, and just so you know, the problem is most likely not the device, but rather the software controlling the device.

Good luck!
-nkri

---

### Post by chrisinspace on 2008-12-20
Thanks, Nkri.  I actually read that thread from beginning to end, hoping to come across something.  I mainly saw people in that thread having the problem where their devices drop or their bluetooth adapters didn't work.  I was hoping maybe my problem was unrelated and fixable, but if it's a kernel issue, I guess I'm in the same boat.  

Did anyone ever have any luck with your version of Bluez?  You said you might have to fall back temporarily to a new distro.  Have you taken any steps yet?  The thing is, I really love the Mythbuntu distro for my living room PC.  Maybe I'll go back to 8.04, but I guess I could give KnoppMyth or Mythdora a try.

I'll keep an eye on the other thread.  Hopefully this is high on the Ubuntu radar.  It seems like a major issue for a lot of users.

---

### Post by nkri on 2008-12-20
> **chrisinspace said:**
> Thanks, Nkri.  I actually read that thread from beginning to end, hoping to come across something.  I mainly saw people in that thread having the problem where their devices drop or their bluetooth adapters didn't work.  I was hoping maybe my problem was unrelated and fixable, but if it's a kernel issue, I guess I'm in the same boat.  

Did anyone ever have any luck with your version of Bluez?  You said you might have to fall back temporarily to a new distro.  Have you taken any steps yet?  The thing is, I really love the Mythbuntu distro for my living room PC.  Maybe I'll go back to 8.04, but I guess I could give KnoppMyth or Mythdora a try.

I'll keep an eye on the other thread.  Hopefully this is high on the Ubuntu radar.  It seems like a major issue for a lot of users.

So far, no one has come back and said they've had any luck with the new Bluez:(

Yes, I have started to look into new distros.  I've tried LiveCD's of Gentoo, Debian, and Fedora so far; Gentoo was fun, though the LiveCD came with Xfce (I want GNOME, and am not prepared to install it until I know how it is with GNOME).  The stable version of Debain (called Etch) is pretty outdated, so I'm gonna try the testing version (Lenny).  Fedora was *very* nice; clean-looking desktop, much like Ubuntu, runs smoothly, and best of all, detects the bluetooth adapter right away; the package management system is not too great, though, and could be pretty tedious to get used to coming from Ubuntu.  I was also gonna try Slackware, openSUSE, Mandriva, and maybe Arch.

But if you like Ubuntu how it is now, I would just go back to 8.04 for the time being...it's just like 8.10, with a slightly different look;)

Good luck!
-nkri

PS: you might also want to keep your eye on [_this_]("https://bugs.launchpad.net/ubuntu/+source/bluez-utils/+bug/284982") bug report, since everyone there is having the same problems as we are here, and developers are likely to come up with a fix if more people confirm the problem.

---

