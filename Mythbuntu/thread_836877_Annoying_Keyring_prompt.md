---
title: "Annoying Keyring prompt"
date: 2008-06-21
forum: Mythbuntu
---

### Post by Meph1st0 on 2008-06-21
I"ve got two problems.  I don't know if they're related.  First problem is my mythbox has to be on the wireless network.  it's just too far away from my router to run a cable and I'm just too lazy to run wires in my walls.  I've been able to get it on my network using ndiswrapper.  But whenever I reboot I get a prompt from the keyring manager for the password.  I have to type in the password before my box will connect to my wireless network.  Is there any way to get it to always allow my network manager program to access the keyring manager for the WEP key?

---

### Post by tonyr1988 on 2008-06-22
> **Meph1st0 said:**
> I"ve got two problems.  I don't know if they're related.  First problem is my mythbox has to be on the wireless network.  it's just too far away from my router to run a cable and I'm just too lazy to run wires in my walls.  I've been able to get it on my network using ndiswrapper.  But whenever I reboot I get a prompt from the keyring manager for the password.  I have to type in the password before my box will connect to my wireless network.  Is there any way to get it to always allow my network manager program to access the keyring manager for the WEP key?

I had this exact same problem. I looked at many different results, but wasn't satisfied.

First, click the network manager icon >> Manual Configuration. Double-click your wireless device, uncheck "Enable roaming mode," and type everything in manually. This worked perfectly on my laptop, but didn't work on my desktop (Mythbuntu box) for some reason (I think it was because I want a static IP address).

Try that and see if it works. If it doesn't, there's another solution that I ended up doing (which is actually insanely easy as well, and allows you to completely remove network manager from loading up every single time, but it easier to mess up than this method). Let me know if the manual configuration doesn't work.

---

### Post by Meph1st0 on 2008-06-23
OKay, I'm ready for your secondary solution.  I tried the steps you gave me and it didn't work.  I too want to statically assign my IP address and so I suppose that doesn't work. I don't understand why statically assigning the IP address wouldn't work though.  Kinda strange.

---

### Post by tonyr1988 on 2008-06-24
> **Meph1st0 said:**
> OKay, I'm ready for your secondary solution.  I tried the steps you gave me and it didn't work.  I too want to statically assign my IP address and so I suppose that doesn't work. I don't understand why statically assigning the IP address wouldn't work though.  Kinda strange.

Yeah, mine was a similar situation. I'm sure the "static IP" is a bug or something, but there's a simple/easy workaround.

First, I completely disabled Network Manager - it's worthless to me now. I used the following commands to do this:

> sudo /etc/dbus-1/event.d/26NetworkManagerDispatcher stop
sudo /etc/dbus-1/event.d/25NetworkManager stop

Then, create two files, at /etc/default/NetworkManager and /etc/default/NetworkManagerDispatcher

The files should simply say "exit" (no quotes) and that's it. (if you need help with this, ask me - I'm not sure how much experience you have in Linux terminals).

Then, now that we've gotten rid of the crappy Network Manager, we need to simply edit one file, /etc/network/interfaces (make sure you make a backup first!)

For me, it was this, for my WEP-protected static-IP address connection (yours should be similar) (the bold is the stuff I had to add to the file):

> auto lo
iface lo inet loopback

[B]auto ath0
iface ath0 inet static
     address [your static IP address you want, like 192.168.1.100]
     netmask 255.255.255.0
     gateway 192.168.1.1
     wireless-essid [your network's name]
     wireless-channel [your network's channel - might be optional, not sure]
     wireless-mode adhoc
     wireless-nick Ubuntu
     wireless-key [the hex key of your network][/B]

Some of your values might be different, though. Restart your computer and see if it works. If you have problems, give me as much information about your network that you know and I can try to help (of course, don't give passwords :D).

---

### Post by Meph1st0 on 2008-06-25
That didn't seem to do it either.  This time it didn't connect to a network at all.  Looking on the bright side the keyring prompt didn't come up either. :)  

Allow me to give you more info about my network, since that is what you'd requested in the case that your last suggestion didn't work.

I have a linksys wrt54g v5 router running the dd-wrt v24 firmware.  The router dhcp address pool is set to start at 192.168.1.100 and increment from there. The wireless card installed in my myth box is a netgear WG311 v3 nic.  This card requires that I use ndiswrapper to install the drivers.  I'm using 128 bit WEP.  I want to statically assign my myth box to 192.168.1.11.  My other home server is 192.168.1.10.

I followed your steps as exactly as I could.  I don't think I did anything wrong, but I may have.  When I created the two files in /etc/default/ I used gksudo gedit and saved them there with the name of NetworkManager and NetworkManagerDispatch.  Each file contained nothing more than the word "exit" (without the quotes, of course).

The interfaces file was nearly exactly as yours except for the essid, Channel (6, by the way), WEP key, and IP Address.  You were using ath0 as your interface I believe.  I don't know if that's the name of my device.  Isn't it usually wlan0?  

After rebooting, I had zero network ability.  Ifconfig only brought up details about the loopback address.  It didn't even show anything about my wired nic.  I just undid everything and rebooted again to be able to get back on the network to create this post.  When I am connected to the network, ifconfig shows wlan0 as my wireless card.

---

### Post by Streakist on 2008-06-25
I had the same problem. I was able to get the prompt to go away by completely removing the keyring password and leaving it blank. This is less safe but I didn't really care so long as it would stop bugging me.

---

### Post by Crusty Juggler on 2008-06-25
When I set my system up and ran on wireless the first time (after ndiswrapper), it asked for my WPA and after I entered it, it asked for a network manager password.  I didn't enter one and just hit enter.  I then got a warning about password storage being unsecure. Since then, it has never asked for a password or my WPA.

So if you can purge your password from network manager and not enter one when it prompts for one, you should be free of the annoying prompt.  Maybe.

---

### Post by Meph1st0 on 2008-06-26
I also read about how people just left their keyring password blank.  and I would like to try this, but i need help.  Because I'm running mythbuntu, I'm using the xfce desktop which didn't come with the keyring gui utility.  How do I get that installed?  or, is there a command I can type in a terminal to change the keyring password?

---

### Post by Meph1st0 on 2008-06-26
Okay, I've come up with a workaround.  I have a spare linksys wrt54g wireless router.  I loaded the dd-wrt firmware and configured it to work as a wireless bridge.  I've connected my mythbox via the network cable to the wireless bridge.  It's working well enough now.

---

### Post by volkswagner on 2008-06-28
> **Crusty Juggler said:**
> When I set my system up and ran on wireless the first time (after ndiswrapper), it asked for my WPA and after I entered it, it asked for a network manager password.  I didn't enter one and just hit enter.  I then got a warning about password storage being unsecure. Since then, it has never asked for a password or my WPA.

So if you can purge your password from network manager and not enter one when it prompts for one, you should be free of the annoying prompt.  Maybe.

I am not sure, maybe someone can confirm.  I think on my laptop at the keyring password prompt I used my login password (after install, first reboot).  I do not get the password pop up on reboot.  I believe I learned this from the forum using 7.04.

---

### Post by Meph1st0 on 2008-06-28
Strangly I've found the same to be true on my own laptop.  My laptop connects to the wireless network without a single request for the keyring password, which is also set to my login password.

Only on my mythbox does it ask for the keyring password.  I thought I'd read in other posts from other people reporting the same thing.  It works fine on their laptop but not on their desktop.

---

### Post by nitrofurano on 2009-02-17
from a webpage, i got to know 
exec echo -n <yourpasswordhere> | /usr/lib/libpam-keyring/pam-keyring-tool -u -s
must be executed before nm-applet

for running this you must install an old version of libpam-keyring (0.0.8-5 from feisty, this package, with /usr/lib/libpam-keyring/pam-keyring-tool file, completelly dissapeared from the more recent versions of this package)

but don't install it with dpkg or something alike - it's because you must fool the packager for not upgrading it, and removing pam-keyring-tool, since it doesn't exist since Ubuntu 7.10! - you must install it as a tarball or by hand - i installed as tarball

first, i extracted the .deb, and so the data.tar.gz - later, on nautilus, i selected the folders etc, lib and usr, and did right-click/create-archive to a package_version_platform.tar.gz file, and later, from terminal in this directory, i did
sudo tar -zxvf package_version_platform.tar.gz -C /

please get assured you're comfortable enough about making and using tarballs - since small mistakes may make you have to reinstall Ubuntu...

but, anyway, for me it's working now, perfectly!

---

