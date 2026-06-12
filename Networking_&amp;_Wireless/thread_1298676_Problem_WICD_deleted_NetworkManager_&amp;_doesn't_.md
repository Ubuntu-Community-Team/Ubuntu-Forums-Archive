---
title: "Problem: WICD deleted NetworkManager &amp; doesn't work"
date: 2009-10-23
forum: Networking &amp; Wireless
---

### Post by NoCyberDom on 2009-10-23
System:
Jackalope
Netbook Reix on an HP 110
**System was fine until WICD messed it up**

I never thought I'd face this with a Linux system because all programs are supposed to be totally separate. However, I installed WICD to compare it to NM due to some things I read and imagine my surprise when my Network Manager failed before the install of WICD was even complete.

NM failed saying something about needed resources weren't available... I figured no big deal and it was a one or the other situation.

But then WICD hung until I manually canceled every single time I tried to connect to my wireless router. It would verify the WEP Key no problem but got hung trying to acquire an IP. I finally got tired of trying to make it work, shrugged with no idea why anyone would say it's so much better than NM and uninstalled WICD via Add/Remove.

Then it all got weird...

nm-applet is a no go, can't even find it but I already know that NM and the applet are different.

So I popped open a terminal and sudo'd NetworkManager to restart it manually... and was promptly informed that NetworkManager is NOT INSTALLED on my system, and that I can get it via "apt-get install network-manager".

Sounds easy... until you remember that you can't apt-get anything at all unless you have a working internet connection.

I checked the help and went to troubleshooting for wireless, which really needs to be rewritten. I mean, who writes a help file that tells the user to use apt-get to install things in order to fix a NETWORKING problem?????

No, I'm not kidding... check the troubleshooter under wireless connections... I was having flashbacks to reading help pages written by MickeySoft.

Sorry, just really frustrated and totally incensed that WICD has an install procedure that messed with another program... when WICD failed to work for me, I needed to roll back and due to the way it installed, I couldn't. AFAIK that should never be possible under Linux distros and I'm stunned.

What I need to do:

I need to install network-manager without the benefit of being able to use a network connection. I tried the failsafe boot and repairing broken packages already, it won't work because the package isn't broken, it's just plain gone.

Can I download the package(s) using Windoze and install from a flash card?

Remember, I am NOT talking about the little applet being broken. I'm talking about:

1) sudo NetworkManager

2) NetworkManager is not installed, you can install it by using sudo apt-get install network-manager

Pretty ironic considering that apt-get only works if you have a working internet connection, eh?

As Jar-Jar said: "Any help here would be hot"

Thanks

NCD

---

### Post by earthpigg on 2009-10-23
hi,> Can I download the package(s) using Windoze and install from a flash card?

you certainly can.

[http://packages.ubuntu.com/jaunty/network-manager](http://packages.ubuntu.com/jaunty/network-manager)

you will need to resolve dependencies manually. look at the packages on that page listed as 'depends' and 'recommends'. i suggest grabbing at least network-manager and network-manager-gnome.

for future reference: when you installed wicd, had you read carefully, it should have informed you that you could only have one or the other package installed at a time.

with userland applications, you can have multiple similar programs installed... but not always with [daemons]("http://en.wikipedia.org/wiki/Daemon_%28computer_software%29") that fulfill a very similar task.

---

### Post by t0mppa on 2009-10-23
Aye, installing WICD removes network manager, since the two aren't compatible. At least the first step worked for you, on a KUbuntu (which for some reason has a known buggy version of network manager installed by default) machine that I was setting up for a friend, the packet manager first uninstalled the network manager and only then tried to download the wicd packets, which obviously failed. ;)

I guess it was a good lesson on why not to use the "fancy" GUI programs, that only care about cool outlooks, and just rely on good old command line. Anyway, your options are pretty much the following:[LIST]
[*]get a connection [manually]("http://ubuntuforums.org/showthread.php?t=571188") and proceed with apt-get/Synaptic
[*]download the [.deb package]("http://packages.ubuntu.com/jaunty/network-manager") with the help of another computer (note that you might have to download quite a bit of other packages too, depending on if you have all the dependencies installed or not) and install from it
[*]temporarily remove the online repositories from the sources list and add your install CD there instead and proceed with apt-get/Synaptic
[/LIST]

---

### Post by jward3010 on 2009-10-23
I'm not a great hand on the interfaces file and iwconfig etc. but is there any chance he can just add IP info into interfaces and WEP and AP association stuff info into iwconfig. Save him having to get the stuff from another machine.

When he's connected he can just download nm through apt. Is that crazy?

---

### Post by swoody on 2009-10-23
As easy as it may sound, try connecting your computer with an ethernet cable to a router that doesn't require a passkey to connect, and startup your computer. I have done this several times from either a minimal install, or an install with no NM or wicd. Once booted, you can just run:
```
sudo apt-get install network-manager network-manager-gnome
```

---

### Post by NoCyberDom on 2009-10-23
Almost home...

I had to d/l both network-manager and network-manager-gnome. No other dependencies were needed.

Now nm-applet works and it still autoconnects, so the config files weren't harmed. However...

My Linux is VERY rusty... I've played with it since Red Hat 7 and Enlightenment DR14, but can't remember how to set nm-applet as a startup progrtam (hey I said I was rusty!!).

At the moment, I have to leave the terminal window open to keep nm running. Could someone please remind me how to set it to start on login?

Thanks, I'll write up a simple step by step to fix this andmark the thread as solved once that's finished.

NCD

---

### Post by swoody on 2009-10-23
NoCyberDom - Good to hear so far! To get NM to auto-start go to System>Preferences>Startup Applications and create a new entry in the new window that pops up. You can put in whatever you'd like for the name and description, and for the 'command' put in:
```
nm-applet --sm-disable
```
Then restart your computer and test it out :)

---

### Post by NoCyberDom on 2009-10-23
Actually it seems to have corrected itself once nm-applet was run once.

So, if WICD fails to work and you can't roll back to NetworkManager, it appears that you:

1) Need to download network-manager in the above link and save.

2) Change the end of the url above from network-manager to network-manager-gnome and download that package as well, save in the same place.

3) Start Gnome, double click network-manager and install, then do the same for nm-gnome while ignoring the suggestion to get the same thing elsewhere since you can't download it.

4) Open a terminal and type "nm-applet"

If that fails, try "sudo network-manager", then "nm-applet".

At this point, things went right back to the way they were before installing WICD for me.

Now I just need to figure out how to get nm-applet to display in my panels on E DR17, but I think that may be an issue for another forum ;)

Thanks again all!

NCD

---

### Post by jward3010 on 2009-10-24
How about using the "-d" (download only) switch with apt to just download the network program you want, if you ever have problems with one or the other it won't require an internet connection to install it. So:
```
sudo apt-get install -d wicd / network-manager
```

---

