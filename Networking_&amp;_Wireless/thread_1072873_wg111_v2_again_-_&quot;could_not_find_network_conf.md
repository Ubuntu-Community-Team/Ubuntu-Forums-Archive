---
title: "wg111 v2 again - &quot;could not find network configuration tool&quot;"
date: 2009-02-17
forum: Networking &amp; Wireless
---

### Post by Corniger on 2009-02-17
Hi guys, my first post, 2 days of Ubuntu and 50% less hair on my scalp :)

I tried to install my wg111v2, as many other seemed to have done. So I followed all the walkthroughs, installed the Windows WLan driver tool, my droiver is there, net11v2, hardware present, and when the magic should get to work and I click "configure network" I get, like manyy others, "could not find a network configuration tool".

I checked within add/remove applications where it says it's there. It's just not in the menu (gnome-network-admin). I downloaded the tarball but can't install it (no clue...).

What can I do? PLEASE somebody help. I wanted Ubuntu to work with Blender in 64 bits, but that only works if I have my 3d GPU driverinstalled which only works if I'm connected to the internet (because the proprietary nvidia linux driver won't run (*,.run file, needs to be run as root, no idea how to do that??? On my last Ubuntu 8.1 install I had a root terminal, on this one it disappeared, and when I got i to run, it told me I was running an XServer and I should exit the X server :P))

I've been through all possible posts, tried all sorts of stuff, tried to install the network admin tool, NOTHING. :(

---

### Post by Professor Bacon on 2009-02-17
Well that's a bit of a roundabout way of getting your graphics card working. I'm thinking it would be easier to just install the proprietary driver. And of course, since you need to log in as root, I will first tell you how to do that. I'll assume you're using the GNOME desktop environment.

First, you're going to want to set the root password to something you know (at least that's what I did first, honestly I didn't even check to see if root had a password by default). The first step is to click the "System" menu, then go to Administration -> Users and Groups. On this screen you will see a list of users on the computer, one of which should be 'root'. At first, root will be grayed out, so you're going to have to click the 'Unlock' button at the bottom of the window. Ubuntu will then prompt you for your password. Simply enter it, and you will now be able to edit the properties for the root account on your machine. Of course, setting the password by hand will lead to one that's easier to remember than auto-generating the password. After you do this, simply log out and log back in with the username root and the password you created, then try running the utility again. The instructions provided by NVIDIA worked perfectly for me. Of course, since this is a proprietary NVIDIA driver, you would have to contact their forum for support if it doesn't seem to be working properly. The Ubuntu community, as far as I understand, does not support proprietary software.

Oh, and one more thing: Although you are now able to log on as root, I would not recommend doing so unless you absolutely have to. The root account has unrestricted access to every aspect of your machine, and as such should be used for serious business only. For everything else, your normal user account would be a much better (and safer) choice.

---

### Post by Corniger on 2009-02-18
OK, thanks a lot for that :) Doesn't look too hard! I'll spend another night with this later on :popcorn:

**But still**: as Blender is also heavily community dependent (or better: I am :p) I would really, really like to get online! Should I reinstall? I installed with WUBI, then I was supposed to run a command to fix broken dependencies that removed practically all programs.
Then I formatted one whole hard drive and installed Ubuntu to it via CD. Only I couldn't boot to Ubuntu then (in my BIOS I can ONLY tell to boot from either CD, HD, Network etc, but not specifically from which device - I have 5 HDS and 2 DVD drives!).
So I formatted the disk again in Windows and reinstalled WUBI with exactly the same installation as before.
Only, this time there was no ROOT TERMINAL any more.
Maybe, if I install a few times, I can get the missing network configuration tool?

I also saw, that in the add/remove the "gnome-network-admin" was listed as something like "network-admin-gnome".

So without the Wireless the whole system is useless!
Should I install an older version that has been bugfixed properly? 

And please: if I had to use the ethernet wire, I'd have to un-register my WLan IP at my ISP, then use the wire, un-register that one again and re-register the WLan Mac, so PLEASE, there's got to be something to fix this!

Edit: when I first install Ubuntu via Wubi, I can see networks in the WLan popup. I can click on them and input my WPA pwd, but it never connects. So maybe this is an entirely different issue?

I also checked for compatibility:

>  WG111v2 
Realtek 8187 
? 
? 
Yes (Feisty/Hardy) 
Yes
Works out of the box with Feisty(No WEP) and Hardy(with WEP)
2008-08-02

WG111v2
Realtek 8187
rtl8187
?
Yes (Feisty/Hardy)
Yes, with caveats
Using either ndiswrapper + netgw111 or native rtl8187 drive, performance was terrible as an interface or under Kismet. Saw 1-3 networks vs 15 using built-in atheros. Test run on two hw samples.
2008-08-19

WG111v2
rtl8187
?
Yes
Yes
Works out of the box with Feisty.
2007-06-07 

Why are there 3 different entries for the same POS? :)

At home I'll try to follow the "howto" a bit closer. But by 2 in the morning and after 2 wasted days I simply didn't have the nerve for intense forum study anymore...

---

### Post by Professor Bacon on 2009-02-18
I seem to have come across a solution to my own wireless troubles, and I do believe it may help you as well. I would recommend installing the compat-wireless package, which contains all the latest wireless drivers available for most modern distros. It should help you.

[http://wireless.kernel.org/en/users/Download](http://wireless.kernel.org/en/users/Download)

Simply download and unpack the archive, then run 'sudo make install' in the directory where you extracted the files (easy way to do this: open a terminal, type cd followed by a space, then drag the folder you wish to change to into your command prompt). Make sure you pay close attention to the terminal output, it will give you instructions after each step. Hope this helps!

---

### Post by Corniger on 2009-02-19
Thank you :)

I already downloaded this package. I found it marked on a forum, too. Never tried it, because I got lost in the flood of html pages I saved to my USB stick, and because the thread I found it in was never finished.

I haven't even touched my own computer yesterday, so I'll try all possible solutions and the new ones this afternoon.

I just never know when I change something within the command line, is that permanent or not? When I try out several solutions, is it possible that they're impossible to work because I have already blacklisted this and that and did something with the ndiswrapper and so on... Should I make a fresh install every time after a solution not working?

I often find referrals to a "Networking" menu item that doesn't exist. It simply isn't there, and no, I haven't removed it or deleted it, I actually have never seen it! Not even after a fresh install that I hadn't touched except for putting my name and pwd in.

I think I'll try once more and then ditch it. Maybe try 804. But why would something work in an older version, if I assume that the newer version is an updated version of the older one with more bugfixes... Why does the older version get longer support anyway? I don't get it. I need a break :)

---

### Post by Corniger on 2009-02-19
OK now: I tried the compat install. Installed fine, told me to make unload.
I typed "make unload" - a little pause, no further instructions. I Typed "sudo make unload" - same thing.
I was "unsure" and restarted. Nothing changed. After all I did no more wireless connections appear. You're supposed to load the driver for the needed device, but nothing tells you HOW.
I searched the website I downloaded the compat fromk, they explain every step except for the last one :P
So I'm really getting very, very tired and sick of this.
I'll do one more fresh install of 810, try to get it to work with compat et al., then I'll very probably delete that again and try 8.04. In case there's a Wubi installer available. And if it doesn't run this evening, I'll just re-embrace Windows.

---

### Post by Corniger on 2009-02-19
> **Professor Bacon said:**
> After you do this, simply log out and log back in with the username root and the password you created, then try running the utility again.

OK, I got bored with the network BS and tried to install the graphics driver. 

Outcome?
"The system administrator is not allowed to login from this screen"
I checked all privileges for the admin.
I'm really losing faith in this.

Edit: ok - compat worked and the make unload command worked, first with errors, then I retyped sudo make unload and rebooted.
Same as usual: "Disconnected", but wireless network appear. Trying to connect isn't taking me anywhere except to the grave :P

---

### Post by Professor Bacon on 2009-02-19
> **Corniger said:**
> OK, I got bored with the network BS and tried to install the graphics driver. 

Outcome?
"The system administrator is not allowed to login from this screen"
I checked all privileges for the admin.
I'm really losing faith in this.

Edit: ok - compat worked and the make unload command worked, first with errors, then I retyped sudo make unload and rebooted.
Same as usual: "Disconnected", but wireless network appear. Trying to connect isn't taking me anywhere except to the grave :P

Woops, I forgot a step with the instructions on how to log in as root. In your Login Window settings (System -> Administration -> Login Window), click on the Security tab and check off "Allow Local System Administrator Login". Sorry for the trouble, I completely forgot about that step.

When the compat-wireless installer tells you to unload and then reload the driver you want, it actually says "load correct driver- if unsure, reboot". It should have automatically selected the correct driver after you rebooted. Since that doesn't seem to be the case, I would try uninstalling the driver you installed in ndiswrapper. I'm not entirely sure, but I suspect there could be some interference.

---

### Post by Corniger on 2009-02-19
No worries, those are minor troubles compared to the WLan and missng stuff issue :) You're the only person helping me, so I owe you anyway :)

OK. I ran it and it cam up with that X Server thing again. I Should exit X Server. In root I looked up the security panel again with "X server settings" but no idea what I could mess up there... 

I'm really starting to find this humorous - in the very moment a resurrecting caffeine rush almost makes me wanna laugh :P

Edit: I performed all this within a fresh install. No ndiswrapper installed, nothing. Now I'll try the ndiswrapper again and then I hope I can still find a 8.04 version of Wubi. Otherwise: Ubuntu byebye.

---

### Post by Professor Bacon on 2009-02-19
You're actually supposed to run the NVIDIA installer in command-line mode. Log in as root and run the command init 2 (fairly certain that's it) in the terminal, then run the NVIDIA setup. When it's done, enter init 0 to shut down, power back up, and the NVIDIA utility should be installed. I forget if it goes through the configuration settings before or after you reboot, but either way it's going to be easy.

---

### Post by Corniger on 2009-02-19
> **Professor Bacon said:**
> You're actually supposed to run the NVIDIA installer in command-line mode. Log in as root and run the command init 2 (fairly certain that's it) in the terminal, then run the NVIDIA setup. When it's done, enter init 0 to shut down, power back up, and the NVIDIA utility should be installed. I forget if it goes through the configuration settings before or after you reboot, but either way it's going to be easy.

Ah, darn, that "sh" command, right? I'm so confused already, I keep forgetting stuff... sorry :(

---

### Post by Corniger on 2009-02-19
OK - I tried again in root. I ran it in the terminal, with the "sh" command and it came up with the X Server again. Dear coach? :) I'll go through the ndiswrapper thing once more.

As said: I see my and another wireless network But I can't login. Apparently, my device is being detected, but I can't connect. That was always the same. Also logging on to root. I never got a connection up. Maybe I'm on the wrong track after all??

---

### Post by Corniger on 2009-02-19
Back again on the wireless path I found another solution: [this looks great]("http://ubuntuforums.org/showthread.php?t=1010650")

I just have to access the "Networking" menu item that doesn't exist.
And I just have to access the "System Tools" in my applications, that aren't there.

Anyway, I managed to edit the file, but still no connection...

---

### Post by Professor Bacon on 2009-02-20
There's no need to use the sh command, you just need to put Ubuntu into text mode. Like I said, just log on as root and run init 2. Oh, and you might want to write down the directory where you keep your NVIDIA driver installer for when you go to install it.

As far as seeing the network but not being able to connect, unless you're selecting the wrong type of security, I've got nothing.

---

### Post by Corniger on 2009-02-20
Thanks again! :) 

I'll sure try that one of these months, or when I feel lucky and spend a few bucks on a different WLan adapter, not knowing if that's the issue after all, or in case I feel extremely bored/unchallenged, cause for now I've **most thoroughly** had it with Ubuntu. I'm sorry your efforts and caring ultimately were in vain :(

---

